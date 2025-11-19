---
title: "I Didn't Change Jobs - AI Changed the Job I Have"
date: 2025-11-18T20:00:00-05:00
draft: false
---

# I Didn't Change Jobs - AI Changed the Job I Have

### *How the last three months quietly transformed my role as a software engineer*

Over the last three months, something happened to me as a software developer that I didn't consciously choose,
negotiate, or plan for. It wasn't a new language, a new framework, or a new tool that I decided to adopt. It was
quieter than that and more profound. At some point this fall, I realized that the way I work had completely changed.

## I didn't decide to work differently. AI became too good to ignore.

Until a few months ago, if I needed a Kubernetes controller with reconcilers, watchers, status updates, CRDs, RBAC,
I sat down and wrote it myself. That was normal. That was my job. And then, without any big announcement or event,
that normal quietly disappeared.

Today, if I describe that same controller to Claude, what it should watch, what events it reacts to, what state
transitions it handles, the model generates the entire codebase: the scaffolding, the reconcilers, the RBAC, the
manifests, even the tests. And more often than not, the result is cleaner and more complete than what I would have
written.

What's more than that, much of the code I used to write - or have already written in past projects - already exists
within the model's latent knowledge. The patterns, the idioms, the API interactions, the structure of a well-formed
controller, it's all baked in.

Instead of hunting through old repos or copying code from projects we've built before, I can access years of
accumulated patterns through a conversation. The things I used to re-implement or re-discover are compressed inside
the model, waiting to be unpacked. A compressed universe of patterns we used to manually write. And it doesn't only work
for some things or sometimes. I wasn't prepared for its consistency, AI's quiet, reliable power.

And here's what's even more surprising: in many cases, the code isn't needed at all. When the model already
understands the workflow, and I can give it a runner or tool access, writing a full service becomes redundant. Instead
of generating software artifacts to execute later, I can describe the workflow in plain language, and the AI carries
it out directly.

For many things, we're not just accessing compressed patterns of code, we're bypassing code entirely and delegating
behavior.

## The shift didn't happen in theory. It happened in my hands, in my actual work.

This wasn't an abstract idea or something I picked up from a conference talk. It upended how I do the real tasks of
my real job. Every project. Every script. Every refactor. Every debugging session.

Every single thing I do now I start with my AI partner. Not as an experiment or an isolated spike, not as a quarterly
goal of demonstrating how I'm adopting AI, but as my actual daily workflow. Configurations, manifests, bash loops,
vLLM arguments, telemetry analysis, architectural diagrams, documentation. All of these are
now collaborations with AI.

Here's another place this shift hit me most: **observability.**
Some of the systems I work with span multiple repos and components, each exposing their own metrics. Before, building
a Grafana dashboard meant digging through codebases, scraping metric names, and manually assembling panels. Now I ask
Claude to scan all the repos, extract every metric, group them, identify where there should be ones that don't exist,
and generate a full dashboard that satisfies a collection of desired insights from stakeholders. It does this in
minutes. It suggests visualizations, metrics, or spans I hadn't considered, based on the patterns of the system's
current behavior.

Without ceremony or fanfare, my starting point changed. My habits changed before my beliefs did. That's how I know
this moment is real.

## My role shifted: from coder to orchestrator, from implementer to architect.

I still write code, but it's no longer the center of what I do, which is probably for the best, because it was never
the thing I was best at anyway.

And I think about the people who were the best, the ones whose coding skill felt superhuman. I wonder whether this
shift hits them the hardest. Not because the AI outperforms them, but because it forces a quiet realization: the real
craft they've mastered was never just the code. It was everything around it. Instead of manually implementing
everything, I now describe what I want, let the AI produce a strong first version, and then spend my time shaping it,
challenging it, and putting guardrails around it.

The "coding" part of my work moved up a level. I spend more time thinking about whether something should even be a
traditional codebase or whether a conversational interface with a tool-runner is enough. I think about where I need
determinism and where flexibility is acceptable; what deserves to be a strict function and what can be an AI-guided
workflow; what constraints the system needs and what architecture will keep it safe, predictable, and adaptable.

My job didn't get easier, it got different. It got bigger. It has become more conceptual and more supervisory. I've
stopped thinking of myself as someone who writes all the code and started thinking of myself as someone who designs
environments for AI to work inside. It's a subtle shift, but a massive one.

## Here's where a blur of change snapped into focus:

I co-teach a course within Boston University's Faculty of Computing and  Data Sciences, *Software Engineering
Career Prep*. I have the honor of sharing with aspiring data and computer scientists what I do every day. This
semester, something shook me:

**I can't prepare students for the profession the way I used to.**

Not because they don't need fundamentals - they absolutely do - but because the profession they're entering is already
vastly different from what it was even a semester ago.

The old rhythm of the job, sketching ideas into code over a few days of learning new APIs, creating tests and documentation,
wrestling with git - that world is fading. It's not gone, but it's no longer the center. Now
the center is something else entirely: clarity, specification, architecture, constraint-setting, and collaborating with
AI. Even the most junior engineers will spend more time orchestrating code than typing it.

Their success won't hinge on how fast they can write, but on how well they can think, how clearly they can define a
problem, evaluate a solution, and adapt as the tools evolve. Realizing this as a mentor and teacher is what made the
shift undeniable.

## I didn't set out to change how I work. AI just crossed a threshold.

This isn't hype or speculation. This isn't "AI might change software engineering someday."

**The job has changed.**
**It changed in the last three months. It changed in the last two weeks.**
**And it changed because AI is becoming capable in a way that makes the old workflow obsolete.**

Avoiding or refusing to use AI stopped making sense. The ground moved beneath me.

## And strangely enough, the human part of my job got stronger.

As AI takes on more of the mechanical labor, the rogue parentheses and unwanted whitespace, the nil-pointer and race condition hunts,
the repetitive boilerplate, my teammates and I spend more time actually talking. More time imagining. More time designing.

We're less hunched over keyboards and more engaged with each other. And because the tedious parts aren't draining our
energy, we all have more space to explore ideas that once felt too ambitious or too time-consuming. Wild ideas feel
more doable. Innovative solutions feel closer. The ceiling feels higher.

Which is fitting, because even this post was written the same way I now build software: in conversation with my AI
partner, shaping the ideas together, clarifying them like I would with a colleague or a very patient friend. The
process even feels a little like therapy for the engineering mind: a space to think out loud, challenge assumptions,
and imagine what could be possible.

## This post is simply a marker in time.

I'm going to write more about this, especially what it means for students, for teams, and for the parts of engineering
that become more important (not less) in this new world.

But this first piece is just to say:

**This is the moment I realized software engineering is being rewritten.**

Everything that follows starts here.
