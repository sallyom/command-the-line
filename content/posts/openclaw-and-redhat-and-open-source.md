---
title: "Calling All Claws: My Take on Open Source"
date: 2026-04-11T15:32:00+01:00
draft: false
---

As I wrote about in my previous post, I think the big opportunity in the agentic AI space isn't to build
the next OpenClaw, but to build around the one that already exists. This piece is about what that looks like, and
what Red Hat's history with open source can teach us.

Red Hat was founded in 1995 by Bob Young and Marc Ewing, two guys running on credit card debt, selling
Linux on CDs in Ziploc bags. They became one of the first open source companies to hit a billion dollars in annual
revenue. The model they built is simple to describe and takes real discipline to follow.

I've seen a few ways companies try to build a product around an open source project such as OpenClaw.
The first is to fork it, add secret sauce, and ship the fork. The second is to study how OpenClaw works,
rebuild the idea from scratch in a different way, and sell that version.
By forking, you control the code and you can
differentiate, but you also need to maintain the project by yourself, forever. Every upstream
improvement now has to be manually ported or ignored. Every security issue becomes yours to fix. Every new contributor who
shows up to help OpenClaw is strengthening the shared vision instead of your fork. The fork starts as freedom and quickly becomes a tax.
Copying the idea and selling it also has its problems. You're starting from zero with none of the community, none of the
ecosystem, and none of the trust.

Over the last decade I've been at Red Hat, I've learned how it became one of the earliest and most successful companies built entirely on open source.

## Contribute back

When Red Hat acquires a company, a first priority is to open source it.
They bought Ansible and open sourced Ansible Tower. They bought Qumranet and kept
KVM fully open in the Linux kernel. They bought Sistina and released GFS and LVM2 as free software.
They bought Netscape Directory Server and open sourced it. 3scale was pushed further into the open.
They take the proprietary bits, push them upstream, then build a product
on top of the same open foundation everyone else can use. And for acquisitions of, or investments in, already open source projects,
Red Hat invests in the community, to ensure it's maintained and fairly governed so it continues to thrive.

Red Hat is among the largest corporate contributors to the Linux kernel, GNOME,
Kubernetes, Ceph, and Xorg. Red Hat engineers helped create and steward systemd, Podman, Buildah,
CRI-O, and Fedora. It helped shape organizations like the Open Container Initiative, the CNCF,
and the Ceph Foundation. They do it because it works, not for charity.

Bob Young, Red Hat's co-founder, used to explain the model with ketchup. Heinz dominates the ketchup market with
roughly 80% share. You can make something that tastes like Heinz in your
kitchen sink, it's just flavored tomato paste. People buy Heinz because Heinz defined what ketchup should
be. They buy Heinz for convenience, consistency, brand, trust. The same applies to open source.
Anyone can take the code and run it. The question is whether they want to, or whether they'd rather have
someone who lives and breathes that software handle it for them.

## This takes confidence

This takes confidence, swagger even. You have to celebrate that everyone can run your project for free. You have to
genuinely want that to be true. The confidence comes from understanding what your customers actually want.
Large enterprises don't want to
run critical software off the shelf of GitHub. They want guarantees, verification, convenience, and support. They want a
phone number to call at 2 AM when something breaks.

Red Hat's model is an example. Fedora is the free, bleeding-edge upstream. RHEL is the enterprise product.
It's hardened, certified, tested, backed by up to ten years of support.
The code is substantially the same. The difference is the packaging, the testing, the SLAs, the expertise,
and the long-term commitment. That's what customers pay for.

Another example is OpenShift. It's a CNCF Certified Kubernetes distribution. Red Hat didn't fork Kubernetes.
They pushed enterprise lessons about access control, security, networking, and operations back upstream. Then they built a carefully
curated, opinionated experience on top. Security, architecture, and operations improvements make Kubernetes better for everyone, including their competitors.
A stronger upstream Kubernetes doesn't diminish what Red Hat offers. It strengthens and validates the foundation that OpenShift is built on.

There is a fine line between contributing back and adding something differentiating, but I don't think it's as
blurry as it seems. If a change would benefit the whole ecosystem, push it upstream. If it's a specific opinion about how
to assemble, configure, or operate the software for a particular audience, that can be your product.

Bug fixes should generally go upstream. Security patches should go upstream. Performance improvements and core
features that make the foundation stronger should go upstream. Your opinions about defaults, your integration testing,
your compliance certifications, your support infrastructure, and your curated plugin ecosystem can be your product.

Now back to OpenClaw. OpenClaw isn't a product and it isn't a company. It's an open foundation inviting everyone to join in
and see what's possible. I think there will be room for many people and companies to make money with OpenClaw if that's what they want to do.
One strong way to do that is to help make OpenClaw as good as it can be. Help make it a solid foundation for your company and many others.
Work together on the core, then fan out and pursue the ideas that become possible with that shared foundation.

Only when a community proves hostile to reasonable contributions and your customers have a dire, specific need would I consider
shipping a fork rather than a dependency on a pinned version of upstream project. And even then, I would hope the long-term goal is to make the fork unnecessary.

If you copy the idea and repackage it, you could be leaving the bigger opportunity on the table. I think the companies best positioned around
OpenClaw will be the ones that contribute meaningfully to it. That's not just my idealism, and I do have a lot of that.
It's one thing I've learned working at Red Hat and a lesson from thirty years of open source.
Contribute upstream where it makes sense, build your expertise, package your opinions, and have the confidence to believe customers will choose you
for what you bring to the table, not because you locked them out of alternatives.

This is the open source way.
