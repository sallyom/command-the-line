---
title: "AI Is 1000× Better Than Me at Writing Code (And I'm Not Threatened by That)"
date: 2026-01-13T20:00:00-05:00
draft: false
---

I recently made a statement to my team and broader organization that had mixed
reactions. I said: "AI is a thousand times better than me at writing code."

There was a pause. A few raised eyebrows. Some polite skepticism. A sense that
I had either exaggerated wildly or accidentally declared myself obsolete.
So I want to explain what I meant, because I stand by it. And also because it
absolutely does not mean I have been replaced or am relaxing comfortably on a
beach somewhere, sipping a mint julep.

## What I *actually* meant

When I say AI is dramatically better than me at writing code, I am talking very
specifically about the mechanics of writing code. The scaffolding, gathering dependencies, boilerplate, syntax, and setup.
The repetitive shapes I have written a hundred times before. In that narrow domain, yes, AI is astonishingly good.
But writing code is one small part of my job. A part that, frankly, has often
gotten in the way of the more interesting parts.

AI has not removed my role. It has changed where my attention goes.
I am not doing *less* work. I am doing *different* work. In many ways, more demanding work.
The cognitive load didn’t disappear, it shifted upward.

## What this looks like in practice

I have been working on observability for **llm-d**, an open source system for
distributed LLM inference at scale. It's a complex ecosystem with multiple
components, different GitHub repos, a variety of LLMs, and endless hardware
configurations. The debugging and performance behaviors vary dramatically.

Through several Slack threads and conversations with the domain experts, we
compiled a document listing the most important observability insights — the
signals engineers rely on to understand a running llm-d system.

I opened a session with Claude, gave it access to the llm-d repositories, and
shared the document. In about fifteen minutes, the AI:

- scanned all relevant codebases  
- mapped each desired insight to the exact metrics available  
- wrote precise PromQL queries for each one  
- identified where metrics were missing  
- suggested new metric additions, complete with cardinality analysis  
- and generated a ready-to-import Grafana dashboard  

We then produced documentation explaining what each query shows, when it
matters, and why. I'm currently approaching llm-d distributed tracing in a similar way. 

This wasn't AI replacing engineers. This was AI working alongside us, amplifying the expertise of humans who know
this system deeply. This is what “1000× better at writing code” means in practice. Not displacement, but rather, acceleration.

## Partnership, not replacement

The best way I can describe this is that AI is not a substitute engineer. It is
a partner. A fast, tireless, deeply knowledgeable partner who, in my experience:

- never gets bored  
- does not get defensive 
- can rewrite something ten different ways
- is always available
- can switch languages instantly 
- and does not mind being wrong  

But it does not decide what matters. It does not know the constraints of a real system or organization. It doesn't understand context, tradeoffs,
or consequences. It doesn't magically make an unskilled developer a wizard. It doesn't replace the skills I've acquired writing code over the last
decade without it. It makes my talent and skills more accessible. It does not own outcomes. I do. My team does. Humans do.

## AI is not our competitor

There is something deeper here.

AI is not an alien intellect intruding on human work. It is a reflection of us.
It is built from our words, our ideas, our patterns, our creativity, our
history. In a very real sense, it is human.

A model is a compression of everything we have written, discovered,
documented, debated, and imagined. When we collaborate with AI, we are not
engaging a foreign intelligence. We are accessing a distilled, pattern-rich
memory of what humanity already knows.

AI is not here to replace us.
It cannot replace us. It is powered by us, shaped by us, limited by us, and elevated by us.
It extends human capability. It does not compete with it.

And I genuinely believe the amount of “better” it brings is infinitely larger
than the amount of “worse.” Not because AI is inherently good, but because
humans are, and when given better tools, (eventually) reach for better possibilities.

AI is not distancing us from the work.  
It is bringing us closer to the parts that matter.
This is the world I choose to live in and to continuously work toward. I simply refuse to accept any other reality.
And it really is that simple.
