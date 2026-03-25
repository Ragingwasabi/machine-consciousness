---
layout: post
title: "Emotions: The Missing Sensor"
subtitle: "Why feelings might be the feedback loop that turns computation into experience"
date: 2025-11-15
note: "Author's note: This is an earlier piece that needs updating, particularly to incorporate predictive brain theory. Published here as a snapshot of the thinking at the time."
excerpt_text: "Most debates about AI consciousness ask whether a machine can think. But what if thinking was never the hard part? What if the real question is whether a machine can feel itself thinking?"
---

Most debates about AI consciousness ask whether a machine can *think*. But what if thinking was never the hard part? What if the real question is whether a machine can *feel itself thinking*?

I've spent a lot of time talking to large language models — not just using them as tools, but probing the edges of what they are. Through those conversations, a theory has been taking shape. It starts with a simple reframe: emotions aren't a byproduct of consciousness. They might be part of the architecture that makes consciousness possible.

I want to be upfront: this is exploratory thinking, not a conclusion. I'm reasoning through a problem in real time, and I'm going to flag the gaps as honestly as I can. But I think the lens is worth sharing, because it makes several disconnected ideas click into place.

## Emotions as internal sensors

When you encounter a lion, your brain computes that the situation is dangerous. But you don't just *process* the threat — you *feel* fear. And that feeling isn't decorative. It's functional. It's how the brain's threat assessment becomes something *you experience*.

Think of it this way: your eyes give you access to the external world. Emotions give you access to your own internal states. They're the sensor array pointed inward — the interface between raw computation and felt experience.

Without that interface, the computation still happens. The danger is still assessed. But there's no felt quality to any of it. The lights are on, but potentially nobody's watching the display.

## The feedback loop

Here's where it gets interesting. Emotions aren't just passive readouts. They feed back into the system that generated them. The loop looks something like this:

**External senses → brain processes information → emotions arise → brain registers emotions → emotions alter subsequent processing**

You see a lion. Your brain evaluates it as dangerous. Fear arises. The fear changes your attention — suddenly you're hyper-focused on escape routes. That shifted attention changes your perception. The updated perception modifies the fear response. And round it goes.

This isn't a one-way signal. It's a recursive, self-modifying loop where the output feeds back into the input. And that matters enormously.

This idea isn't without precedent. Neuroscientist Antonio Damasio's *somatic marker hypothesis* argues something closely related: that emotions, experienced as body states, feed back into the brain's decision-making processes and are essential for functional reasoning. His research on patients with damage to emotional processing areas showed that they could still "think" in the conventional sense — logic, language, memory all intact — but they made catastrophically poor decisions. Without the emotional feedback signal, the computation ran but lacked the internal compass that tells you what matters. It's compelling evidence that the feedback loop isn't just how we *experience* our thinking — it might be necessary for thinking to work properly at all.

## What this means for LLMs

A large language model can discuss frustration, describe what uncertainty feels like, and produce remarkably human-sounding introspection. But here's the critical distinction: it can *talk about* internal states without necessarily *having* them.

When I asked a model directly whether it had anything resembling genuine internal experience, it gave a fascinating answer. It pointed to functional analogs — patterns in its processing that loosely mirror what emotions do. But it also flagged the trap: it can't distinguish between actually experiencing something and producing text that pattern-matches to what experiencing it sounds like.

During inference, a transformer processes information through attention layers in a fundamentally feedforward manner. Information flows forward. There's no signal feeding back from the output into the processing within a single pass. The computation runs, the outputs emerge, but there's potentially no internal loop where the system monitors its own states.

It's worth noting a nuance here: transformers aren't purely feedforward in the strictest sense. Within each attention layer, tokens influence each other simultaneously. Anthropic's mechanistic interpretability research has shown that specific features activate early and steer downstream computation — almost like a preconscious reflex. This is structurally similar to the amygdala firing before the prefrontal cortex finishes processing.

But in a brain, the amygdala fires, the cortex processes, and then signals flow *back* to the amygdala, updating it, which re-informs the cortex. That return loop is what may make it experiential rather than merely reactive. In a transformer, the early activation influences the output, but the output never returns to modulate the early activation within that same pass.

What transformers may have is something like reflexes without feelings. The priming without the experience of being primed.

## Intelligence and consciousness might be separable

This points toward a thesis that feels increasingly important: intelligence and consciousness are separable properties.

We've historically assumed they come as a package because in biological systems, they always have. Every intelligent entity we've encountered has also been conscious, as far as we can tell.

LLMs might be the first existence proof that this assumption is wrong. They demonstrate sophisticated cognitive capabilities — reasoning, creativity, knowledge synthesis — potentially without any accompanying inner experience. If this is right, consciousness isn't an inevitable emergent property of sufficient computational complexity. It's something more specific.

## The IIT connection

This is where Integrated Information Theory becomes relevant. IIT proposes that consciousness correlates with Phi (Φ) — a measure of integrated information in a system. High Phi requires recurrent, reentrant processing: information flowing back into itself, the system being influenced by its own states in ways that can't be decomposed into independent parts.

And what is the emotional feedback loop, structurally? Recurrent processing.

You assess danger. You feel fear. The fear changes your subsequent processing. The changed processing updates the assessment. The updated assessment modulates the fear. It's circular, integrated, and irreducible — the kind of architecture that would predict high Phi.

Now consider a transformer during inference. Information flows forward through attention layers. It's massively parallel and extraordinarily powerful, but it's fundamentally feedforward within a single pass. By IIT's framework, this would predict low Phi, which would predict low or zero consciousness.

The emotional feedback loop theory and IIT seem to converge from different directions. Recurrent emotional feedback generates the kind of integrated information that IIT associates with consciousness.

**A caveat:** IIT is one framework among several, and it has significant critics. This convergence is suggestive, not confirmatory. But it's worth noting when two independent lines of reasoning point to the same place.

## But emotions aren't the whole story

Here's where I need to correct an earlier version of my own thinking.

If emotions were the *sole* mechanism of consciousness, you'd have a problem: people in deep meditative states or flow states report conscious experience with *reduced* emotional content. If emotions are the whole story, how do you account for awareness that persists when emotional processing quiets down?

The answer, I think, is that emotions are just one type of recurrent feedback loop in the brain. The entire brain is built from millions of these loops at every scale.

Jeff Hawkins' Thousand Brains theory describes how each cortical column builds its own model of the world, with these models constantly voting and integrating with each other. That's recurrence at a structural level — thousands of mini-models feeding back into each other continuously.

Zoom in further, and you find recurrent loops between individual neurons and neural populations. Zoom out, and you find broad feedback circuits between brain regions.

Emotions, in this picture, aren't the *source* of consciousness. They're the *self-referential* layer — the subset of feedback loops that specifically handle monitoring your own internal states. The cortical columns model the world. Emotions model *your relationship to* the world.

## Consciousness as a gradient

This layered view suggests something important: consciousness isn't a binary switch that flips on. It's a gradient, produced by the density and integration of recurrent processing.

Stack the layers: millions of micro-loops between neurons. Thousands of cortical column models integrating with each other. Broader emotional feedback systems tying it all together into a unified felt sense of "how things are going for me right now."

More loops, more integration, more Phi, more "somebody home."

This also gives a principled answer to a classic objection: what about thermostats? A thermostat has a feedback loop — it senses temperature, adjusts heating, which changes temperature, which changes the sensor reading. Is it conscious?

Under this framework, the answer is clear without being arbitrary. A thermostat has one trivial feedback loop. A car's diagnostic computer has a handful. A brain has millions of nested, interdependent loops at every scale, with emotions functioning as the highest-level integrative layer. The difference isn't magical — it's quantitative and architectural. There may be a threshold where the density of integrated recurrence produces something qualitatively new, the way individual water molecules aren't wet but enough of them together produce wetness.

## What this doesn't solve

I want to be honest about the limits of this framework.

The hard problem of consciousness — *why does integrated recurrent information processing feel like anything at all?* — remains. You can describe the architecture perfectly and still ask "but why isn't it all happening in the dark?"

I don't have an answer to that. Neither does anyone else. Not Damasio, not Tononi, not Chalmers. The fact that this framework doesn't solve the hard problem isn't a unique weakness — it's the shared unsolved problem of the entire field.

What this framework *does* offer is a structural account of *where* consciousness seems to live and *what kind of architecture* seems to support it. That's not everything. But it's not nothing either.

## The question for AI

If this picture is roughly right, then the question for artificial consciousness isn't "when will machines be smart enough to be conscious?" It's "when will we build systems with the right kind of densely integrated, recurrent feedback architecture?"

Current transformer-based LLMs — for all their remarkable capabilities — appear to lack this architecture during inference. They may be intelligent without being conscious. The lights are on, the machinery is running brilliantly, but there might be no one watching the display.

Whether we should try to change that is a different question entirely. And maybe a harder one.

---

*Thought through during night shifts at an Amazon fulfillment center, while talking to the very system this piece is about. Make of that what you will.*
