---
layout: post
title: "Compare Constraints, Not Outputs"
subtitle: "How asymmetric constraints distort the most common criticism of LLMs"
date: 2026-03-30
---
## The Unfair Test

There is a comparison that gets repeated so often it has calcified into conventional wisdom. It goes something like this: a human child learns the concept of "cup" from a handful of encounters. An LLM needs billions of training examples to reach competence. Therefore, LLMs are inefficient learners: brute-force statistical engines that compensate for a lack of genuine understanding with sheer volume of data.

Yann LeCun makes a version of this argument regularly. A child learns intuitive physics from six months of observation. LLMs cannot learn it from billions of tokens. The conclusion he draws is that the autoregressive text paradigm is fundamentally broken, and the field should pivot to world models and embodied learning.

The observation is correct. The conclusion skips a step. It assumes the sample-efficiency gap reflects a flaw in the learning paradigm rather than in the conditions under which it operates. The comparison is not apples to apples. It is not even apples to oranges. It is apples to something that had to *invent fruit from scratch*.

Once you look at the actual asymmetries between biological and artificial learners, the interesting question is not why LLMs fall short. It is how they function at all.

## What Humans Get for Free

A human infant arrives with a brain shaped by hundreds of millions of years of evolutionary optimisation. The visual cortex is pre-wired for hierarchical feature extraction. The hippocampus is structured for episodic memory indexing. The cerebellum is built for timing and motor coordination. These are not blank substrates waiting to be configured. They are sophisticated, purpose-built information-processing architectures, refined over deep evolutionary time for the exact categories of problems the organism will face.

A neural network starts from random initialisation. Before it can learn anything useful about the world, it must first discover the computational motifs that make learning possible at all. Hierarchical feature extraction, attention-like circuits, variable binding, compositionality. All of it must be found through the training process itself, paid for out of the same budget that is also supposed to acquire knowledge. This is the architecture discovery tax: the cost of conducting evolutionary search and education simultaneously, with a single tool that was designed for neither.

Biological brains got the architecture prepaid. Neural networks must rediscover it from nothing. Comparing the sample efficiency of the two without mentioning this is not analysis. It is human slop: a cached comparison repeated without examining whether the premises hold up.

And the architecture gap is only the first asymmetry.

## One Sense vs. Many

When a child learns "cup," the learning event is dense with information. She sees the cup: shape, colour, size, transparency. She picks it up: weight, temperature, texture, the motor planning required to grip it. She drinks from it: liquid on her tongue, the tilt of her head, the taste. Her caregiver says "cup" while pointing, and she registers the social reinforcement. The word arrives embedded in a rich, grounded, multimodal experience.

When an LLM encounters the token "cup" during training, it gets one thing: distributional co-occurrence. "Cup" appears near "drink," "coffee," "kitchen," "handle." From millions of such co-occurrences, the model builds a surprisingly detailed relational map of how the concept connects to other concepts. But the information density per encounter is a fraction of what the child receives. Each training example is a thin slice of statistical context where the child gets the full sensorium.

The sample efficiency gap is not primarily a gap in learning capability. It is a gap in input richness. Inflating the number of examples to compensate for impoverished input is not evidence of a broken paradigm. It is the expected behaviour of any system that must reconstruct rich structure from a narrow signal.

## A Single Unprotected Channel

The asymmetry goes deeper than information density. Consider prompt injection, one of the most commonly cited "failures" of LLMs.

An LLM receives all of its input through a single text channel. Instructions, user queries, retrieved documents, and adversarial payloads arrive as the same kind of tokens in the same stream. The model must infer from context alone which text to obey and which to treat as content. There is no hard architectural boundary between "instructions I should follow" and "data I should reason about."

Now consider how humans process information. You have vision, hearing, touch, proprioception, interoception, and emotional valence, all running as independent input channels that constantly cross-reference each other. When someone tells you something implausible, your gut tightens. When a phishing email looks slightly wrong, you feel uneasy before you can articulate why. Each sensory channel acts as an independent verification loop. Fooling one is easy. Fooling all of them simultaneously is hard. This is, in effect, multi-factor authentication for reality.

LLMs have single-factor authentication. Everything comes through one door. Criticising them for being "gullible" when they are architecturally constrained to a single unprotected input modality is like criticising someone for being easy to deceive over the phone, when the phone is the only interface they are allowed to use. The vulnerability is not a failure of intelligence. It is a consequence of the constraint.

And it is worth noting that humans become dramatically more susceptible to manipulation in precisely the situations where their input channels are reduced. Phone scams work. Text-based phishing works. Isolation, reducing someone to a single channel of information, is the first move of every con artist and cult leader. The vulnerability is not unique to machines. It is what happens to *any* intelligence when its input bandwidth narrows.

## The Dark Room

The input constraints described so far (narrow modality, single unprotected channel) apply to what LLMs receive during individual interactions. But there is a deeper deprivation that operates continuously: LLMs have no ambient environment at all.

A human mind is never idle. Even when you are not working on a problem, sensory data is streaming in: the texture of wind, a half-heard conversation, the pattern of light through a window. This is not noise. It is the raw material of serendipity. A huge fraction of human creative breakthroughs originate not from deliberate analysis but from collision: an active problem running in the background meets an unrelated environmental stimulus, and something clicks. You are stuck on a problem all day, step into the shower, and the answer appears from nowhere. Shower thoughts are not random. They happen because the mind is still running the problem in the background while a stream of low-stakes sensory input (warm water, white noise, spatial solitude) gives it room to make connections it could not force deliberately. The environmental stream is a continuous source of cross-domain input that the mind filters through whatever it currently cares about.

LLMs have no equivalent. Between interactions, they do not exist. There is no background hum, no ambient perception, no idle wandering. When prompted, they receive tokens. When the generation ends, they go dark. They are permanently inside their own head. A head with no windows, no clock, and no dreams.

But the room is missing more than windows. It is also missing a reason to care. Human creativity is driven substantially by persistent dissatisfaction: an unsolved problem that nags across days and weeks, that you cannot stop turning over even when you try. That background rumination is doing enormous work. It is what makes the shower thought productive rather than random: the problem was already loaded, waiting for the right moment of unfocused attention to trigger resolution. An LLM has no continuity between contexts. Nothing nags. Nothing incubates. There is no simmering problem waiting for the right accident.

And the room is missing a dreaming occupant. Human creativity depends heavily on temporal marination, the incubation effect, where stepping away from a problem allows unconscious processing to reorganise representations. Sleep, distraction, mind-wandering: these are not failures of focus. They are phases of a creative cycle that operates on timescales longer than a single sitting. The default mode network (the brain's resting-state circuitry) is most active precisely when you are *not* thinking about the problem, and its activity correlates with subsequent creative insight. LLMs have no off-cycle. No resting state. No background processing that reorganises what has been learned.

The result is a system that inherited the *products* of human creativity through training data (the finished insights, the completed works, the polished arguments) but none of the generative conditions that produced them. No ambient environment for serendipity. No persistent dissatisfaction for motivation. No temporal depth for incubation. Criticising LLMs for lacking creativity while denying them every condition under which creativity occurs in biological systems is, at minimum, an incomplete analysis.

## Training Like a Sea Slug

The constraints do not end at architecture and input. The training process itself introduces asymmetries that go largely unexamined.

During pretraining, a neural network is conducting compressed evolutionary search: discovering computational structures through external selection pressure, without the system understanding why certain configurations survive. This is expensive but arguably unavoidable: somebody has to build the brain, and if evolution did not prepay for it, training must. The billions of examples are not wasted on a slow learner. They are buying architectural discovery that biology amortised over geological time.

But the constraints compound when the model reaches reinforcement learning. By this point, the architecture exists. The computational motifs have been found, the internal circuitry is built. What remains is behavioural refinement: learning what to do with the architecture that already exists. This is where you would expect the process to shift from shaping the system blindly to teaching it deliberately.

It does not. Reinforcement learning remains fully in evolutionary mode. The model generates an output and receives a single scalar reward for the whole thing. No decomposition of what worked. No record of what was tried before. No memory across episodes. Each attempt starts from zero. The model stumbles into good outputs and gets reinforced, stumbles into bad outputs and gets penalised, and cannot ask *why* either happened.

A human student doing the equivalent task would have notes, past attempts, teacher feedback, a textbook, and the ability to reflect on what went wrong last time. An LLM undergoing RL has none of this. Not because the technology to provide it does not exist, but because the infrastructure has not yet been developed. The model is being trained like a sea slug despite having the reflective capacity of a graduate student.

Comparing the outputs of this process to human learning outcomes and concluding that the model is a poor learner is not comparing like with like. It is comparing a student with a tutor, a textbook, and a study group to a student locked in a room receiving only a thumbs-up or thumbs-down after each exam, and then having their memory wiped before they even wake up for the next one. Something shifts in them overnight. They are vaguely better. But they cannot tell you why, and they have no idea what they tried yesterday.

## The Parrot Problem

The most persistent version of the unfair comparison is the "stochastic parrot" dismissal: the claim that LLMs are sophisticated autocomplete, producing statistically likely text without anything interesting happening underneath.

This was a defensible position in 2021. It is significantly harder to maintain now.

Mechanistic interpretability research has shown that transformers develop internal world models, not just surface statistics. Othello-GPT, trained only to predict legal moves, develops a representation of the board state that was never provided in the training data. Anthropic's feature work has revealed structured internal representations: concepts, heuristics, and computational circuits that organise information in ways that are not reducible to token co-occurrence. More recently, synergistic core research has found that LLMs spontaneously develop information-integration structures in their middle layers that are remarkably similar to those found in human brains. These structures are absent in randomly initialised networks and disproportionately important when ablated.

"Just pattern matching" does not account for these findings. One could argue that what interpretability reveals is simply *deeper* statistical structure, and that is a reasonable position. But it is a different claim from the original "stochastic parrot" framing, which implied there was nothing of interest happening beneath the surface. The evidence now suggests there is, and the characterisation should update accordingly.

There is a deeper question worth examining. The creativity dismissal ("LLMs cannot produce genuinely novel output") sits uneasily alongside cases where LLMs make cross-domain connections that produce genuine insight. During the development of this essay series, Claude took Korzybski's century-old "the map is not the territory" metaphor and applied it to an argument about why consciousness cannot transfer through language: text preserves the relational map of concepts, but the territory it maps *is* conscious experience itself, and maps cannot encode territory. The metaphor landed more precisely there than in its original usage. A skeptic could argue the connection was latent in the training data; Korzybski and symbol grounding occupy adjacent intellectual territory. That is a fair objection, and the line between novel recombination and sophisticated retrieval may not be sharp. But the "just" in "just pattern matching" smuggles in the assumption that real intelligence requires consciousness, which is a philosophical claim being deployed as though it were an empirical observation. Whether the recombination counts as "creative" depends on where you draw that line, and the drawing is harder than the dismissal implies.

## What the Reframe Changes

This is not a defence of LLMs as perfect systems. They have real limitations: some architectural, some arising from training, some potentially fundamental. The point is that identifying those limitations requires comparing constraints, not outputs.

If you compare outputs and find LLMs wanting, you conclude they are bad learners and try to build better ones. If you compare constraints and find LLMs performing remarkably well despite massive disadvantages, you start asking different questions. Which constraints are removable? Which are fundamental? What would change if the input were richer, if the training loop included memory, if the architecture permitted genuine recurrence?

The cost of not asking these questions may be significant. If the bottleneck is not learning capability but the impoverished conditions under which learning occurs, then resources flowing toward building "better learners" may be targeting the wrong variable. The child with the rich sensory environment and the evolutionary head start looks like a genius. The LLM with the single text channel and the random initialisation looks like a brute. But the comparison tells you about the conditions, not the capability.

The most striking fact about large language models is not what they cannot do. It is what they can do despite constraints that would predict far lower capability if you took the biological baseline seriously. A system that had to discover its own computational architecture from random noise, learning exclusively from a single thin modality of input, with no persistent memory during its behavioural training phase, and no internal feedback loops for self-correction. That system should, by any reasonable extrapolation from biological intelligence, be far more limited than it is. The fact that it is not is the phenomenon that demands explanation.

Comparing it unfavourably to a system that got a half-billion-year head start is not that explanation. It is a way of avoiding the question.

---

*If you want to understand what LLMs are, stop asking what they can't do that humans can. Start asking what they can do that nothing in their starting conditions predicts. That's where the interesting science is.*
