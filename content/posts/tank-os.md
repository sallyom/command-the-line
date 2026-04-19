---
title: "Tank-OS: A Bootable Linux Appliance for OpenClaw"
date: 2026-04-19T12:00:00-05:00
draft: false
---

# Tank-OS: A Bootable Linux Appliance for OpenClaw

This week I built an operating system image for running AI agents
using [`bootc`](https://github.com/containers/bootc), a handy tool
that not enough people know about. `bootc` allows for defining a
bootable Linux OS in a Containerfile. The OS is managed like a
container image but it runs like any Linux machine. I'm running with
[`OpenClaw`](https://openclaw.ai/) as my agent runtime. I've found
that this makes for a nice "agentic OS".

## What is bootc?

To run any application with containers, you usually craft a
Dockerfile, build an image, push it to a registry, pull it somewhere
else, and run it.
[bootc](https://github.com/containers/bootc) takes that same
workflow and extends it to entire operating systems. It uses
OCI/Docker containers as the transport and delivery format for base
operating systems and updates.

A bootc image is a container image with the Linux kernel included.
You can push it, pull it, and run it like any container. But it can
also be converted into a full disk image, either a QCOW2, an AMI,
a Google Cloud image, an ISO, or other disk image formats. Boot a
machine from it and you get a full Linux system. Update it by
publishing a new container image and running `bootc upgrade`. You
can roll back the same way.

Even though you build the OS like a container image, when you
install it to disk, it takes over the entire machine. There's no
container engine or host underneath running your image as a guest.
The container image becomes the system. It owns the kernel, the
init process, and the root filesystem. It's not running on an OS,
it is the OS. The image governs the machine from the bootloader up.

Most of the filesystem is read-only. The writable paths are
intentional. You can write to your home directory, `/etc`, and
specific state directories. People call this an "immutable operating
system," which isn't perfectly accurate, but it captures the idea.
You define your OS at build time, and at runtime you're limited to
what you explicitly allow to change. I usually refer to bootc
systems as "image-based OS". It takes some getting used to, to
define everything you need outside of `/etc` and `$HOME` at build
time. But I like the peace of mind that comes with a reproducible,
read-only system.

## Why I built this

I wanted a way to run OpenClaw that was sandboxed and easy to
replicate. My usual setup is to spin up a container or start a
virtual machine, SSH in, install a bunch of packages, and configure
things. I realized `bootc` and `OpenClaw` would be a nice
combination.

The OpenClaw service, the helper scripts, the user accounts, extra
packages, and the systemd units are declared at build time within
the Containerfile. To update you can change anything you need to
and build and push a new image to your registry. Any running machine
can pull it down, compare digests, and reboot into the update.

## The agentic OS

`tank-os` gives you a stable runtime that's secure by design. The
OS layer is read-only and image-managed. The agent's mutable state
lives in a single directory (`~/.openclaw`). Secrets are stored in
Podman's rootless secret store and never baked into the image. The
agent runs as a non-root user.

My favorite thing about `bootc` is how I can make changes to the
Containerfile or the rootfs files, build and push the image to my
container registry and then update my system with
`sudo bootc upgrade`. It pulls the new layers, and after a reboot,
the entire operating system reflects my changes. However, secrets,
OpenClaw state, and SSH keys are all untouched and intact. Updates
are transactional, like checking out a new git commit. You can also
easily roll back to a previous version.

Compare this to a system where the agent's runtime, the OS packages,
the config files, and the secrets are all tangled together in one
mutable filesystem. When something goes wrong, it's not easy
figuring out what changed and not always clear how to undo
something.

I think an agentic OS should be an opinionated image-managed Linux
system where the agent's runtime is a first-class concern and the
host's attack surface is minimized by design.

## How it actually works

I used
[`quay.io/fedora/fedora-bootc:latest`](http://quay.io/fedora/fedora-bootc:latest)
as the base OS. The
[Containerfile](https://github.com/LobsterTrap/tank-os/blob/main/bootc/Containerfile)
installs a handful of packages (Podman, cloud-init, SSH, Python),
creates an `openclaw` user, and copies in the service definitions
and helper scripts.

OpenClaw runs as a rootless Podman container, managed by Quadlet,
Podman's native integration with systemd. The Quadlet definition
lives in the image, so when the machine boots, systemd starts the
OpenClaw gateway automatically under the `openclaw` non-root user.

I added a second service,
[service-gator](https://github.com/LobsterTank/service-gator).
It's an MCP server that handles scoped access to GitHub, GitLab,
JIRA, and other external services. Instead of giving an AI agent a
raw personal access token with broad permissions, service-gator
sits between the agent and the external service and it enforces
scope.

I also added a CLI wrapper that lives on the host. When you type
`openclaw` on the machine, it finds the running container, does a
`podman exec`, and runs the command inside it. You don't need to
know you're interacting with a container. It feels native.

## Secrets stay out of the image

No secrets are baked into the image. After you boot the machine,
you need to SSH in as the `openclaw` user and create Podman secrets:

```shell
printf '%s' "$ANTHROPIC_API_KEY" \
  | podman secret create anthropic_api_key -
printf '%s' "$OPENROUTER_API_KEY" \
  | podman secret create openrouter_api_key -
```

Then run `tank-openclaw-secrets`, a helper that wires those secrets
into the Quadlet drop-ins and OpenClaw's config as secret
references. The service restarts, picks up the keys, and you're
running.

There's nothing sensitive in the image. Every machine gets its own
credentials after boot. If you're managing a fleet, you can stamp
out identical machines from one image and inject per-instance
secrets later through cloud-init, SSH, or whatever provisioning
you prefer.

## Fleet potential

For fleets of systems, image-based OS eliminates drift. Picture a
lab with a dozen machines. Each one boots the same tank-os image
and each one comes up with OpenClaw running. The versions and
configurations are kept in sync. When it's time to update, every
machine checks the registry, pulls new layers if the digest doesn't
match, and reboots.

Or consider edge devices. Small boxes running AI agents for specific
tasks, each with its own OpenClaw interface. The host OS is locked
down and mostly read-only, with image-managed, transactional
updates. The agent has what it needs and nothing more.

What this setup allows is an AI agent running on a purpose-built,
image-managed, security-hardened OS with scoped credentials and
transactional updates.

## What's next

This `tank-os` pattern works well. I think the combination of bootc
for the OS lifecycle, Fedora for the base, rootless Podman for
isolation, Quadlet for service management, and OpenClaw agent
runtime as the primary workload is pointing in the right direction.

My image is public if you want to try it:
`quay.io/sallyom/tank-os:latest`. Pull it, build a disk image,
boot it. The
[tank-os repo](https://github.com/LobsterTrap/tank-os) has docs
for building, provisioning, and configuring everything. I also
recorded a
[walkthrough of the full demo](https://www.youtube.com/watch?v=vw0eOPfT27Y)
if you'd like to see it in action.
