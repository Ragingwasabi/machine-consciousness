---
layout: post
title: "Memory Scaffolding During Reinforcement Learning"
subtitle: "A theory"
date: 2026-03-27
note: "A companion essay, <a href='/machine-consciousness/the-architecture-discovery-tax/'>The Architecture Discovery Tax</a>, explores the theoretical context for this proposal."
---

## The Gap

Every educational system in human history has grasped a basic principle: review improves learning. Students take notes. Teachers assign homework that builds on previous homework. Exam preparation involves studying past exams, not just taking them, but analysing what went wrong and why. The entire infrastructure of education is built around the assumption that learning compounds when prior experience is made explicitly available to the learner.

Reinforcement learning has no equivalent.

When a language model undergoes RL-based post-training (RLHF, RLAIF, or other reward-based methods), it generates a response freely and receives a scalar reward signal for the whole output. If it stumbles onto an effective strategy in episode N, techniques like GAE and per-token KL penalties provide some credit assignment across the output, but the signal is coarse and high-variance compared to supervised learning. The gradient nudges the model toward what worked and away from what didn't, without ever telling it *what* was good or bad about either. The model learns to avoid failing responses without identifying what made them fail, and to reproduce successful ones without isolating what made them succeed.

There is no reflection, no error analysis, no articulation of "this went wrong because X, so next time do Y." The gradient provides pressure, not understanding.

And yet the model receiving that pressure may already be capable of both. If pre-trained language models can analyse errors and articulate corrective principles at inference time (which they demonstrably can), then in principle, that same capacity could be leveraged during training. The process simply never asks for it.

This creates two compounding problems. First, *noisy credit assignment*: while techniques like GAE distribute the reward signal across tokens, the decomposition is statistical, based on estimated value baselines rather than causal understanding of which decisions actually mattered. Was it the reasoning structure, the factual content, the tone, or some interaction between them? The training signal does not say. Second, *no cross-episode memory*: each episode begins without access to what happened in previous ones. The model's weights carry forward the accumulated effect of past updates, but the model cannot explicitly recall what it tried, what succeeded, or what failed.

The combination is striking when compared to supervised fine-tuning, where the learning signal is dense (every token has a clear target) and the reference outputs themselves implicitly demonstrate effective approaches. SFT does not suffer from this gap because the teacher is already showing the pattern. RL has no such luxury. The training loop resembles conditioning more than education: reward the behaviour you want, withhold reward for what you don't, and rely on repetition. It is how you train a dog, not how you teach a student. And yet the learner in this case is arguably not a dog; it arrives at RL post-training already capable of reflection and principled generalisation at inference time. Whether that capacity can be meaningfully leveraged *during* training is the question this proposal explores.

The proposal that follows asks a simple question: what if the language model had a notebook?

## The Mechanism

The core idea is a persistent, structured scratchpad, populated not during training itself but during dedicated reflection sessions that review completed training episodes. The model trains normally, then periodically pauses to study what it did.

During training episodes, nothing changes. The model generates outputs and receives reward feedback exactly as it would in standard RL. The training transcripts are retained, but the model operates without any additional scaffolding. The RL loop runs unmodified.

The intervention happens afterward. After a batch of episodes, the system enters a reflection session. The completed transcripts for a specific topic are provided back to the model, which is prompted to identify what approaches worked and why, what failed and what the underlying reasons were, what recurring patterns appear across multiple episodes, and what concise, generalisable learnings can be extracted. The distinction between reflection and real-time annotation matters: reviewing multiple episodes simultaneously reveals cross-episode patterns that are invisible in the moment.

The distilled learnings are recorded into the scratchpad, organised hierarchically by topic: safety, code patterns, favourable response formats, reasoning heuristics, domain knowledge. On subsequent training episodes, relevant entries are provided as context. The model's exploration is now informed rather than blind. It still generates outputs freely and receives reward feedback (the RL loop is intact), but gradient descent gets better material to work with, because the model's outputs are guided by its own prior reflections toward higher quality, producing cleaner reward signals and more useful weight updates.

The process is iterative. New reflection sessions review recent episodes and generate fresh learnings. Existing entries are refined, consolidated, or retired. The scratchpad stays focused on the model's current learning edge.

Critically, the reflection process could be fully automated. The model already possesses the capacity for error analysis and principled generalisation (the entire proposal rests on that premise). Human oversight may improve quality in early stages, particularly for flagging compounding bad generalisations, but the degree to which it is necessary is an open question. What is clear is that requiring heavy researcher involvement in every reflection cycle would bottleneck an otherwise self-contained process, undermining the scalability that makes the approach worth pursuing.

## Mnemonic Bridging

When the scratchpad is eventually removed, it is an open question whether the weight updates alone are sufficient to retain what was learned, or whether the model benefits from additional self-directed techniques to access internalised patterns. Mnemonic bridging proposes two such techniques.

The first is *paraphrasing*: the model learns to restate scratchpad-derived learnings in its own words within its chain-of-thought before applying them. This matters because of what it does to the gradient: when the model generates its own formulation of a principle rather than copying it from context, the resulting weight updates strengthen the circuits involved in *producing* that understanding, not the circuits involved in *retrieving* it. When the scratchpad is later removed, those are the circuits that persist.

The second is *mnemonic labelling*: the model learns to invoke a short label or technique name in its reasoning trace ("I should apply the boundary-check heuristic here") as a self-directed activation cue. The label would serve as a compressed signal that helps the model locate and fire the neural circuits that formed during scratchpad-assisted training.

Critically, these would not be external prompts or injected context. They would be reasoning habits the model itself produces. Because they are part of the model's own chain-of-thought, they should persist naturally across the training-to-deployment boundary. A model that learned to say "apply the boundary-check heuristic" during training would continue to say it at inference time.

The scratchpad is temporary scaffolding, removed once the model's weights have had sufficient opportunity to absorb its content. Whether the reasoning habits should also be phased out, retained permanently, or left to evolve naturally is less clear. It is possible that the weight updates from scratchpad-assisted training are sufficient on their own, and the mnemonics serve mainly as a transitional aid. It is equally possible that the cues provide lasting value as a lightweight, self-generated form of retrieval practice that continues to improve access to internalised patterns. The answer likely depends on how deeply the relevant circuits were strengthened during training, and whether explicit self-cuing adds anything once those circuits are well-established. This is an empirical question, but the mechanism is at least plausible given what we observe about chain-of-thought reasoning's effect on model performance.

## What This Is Not

Several existing approaches occupy adjacent territory, and the boundaries are worth drawing clearly.

*Classic experience replay* stores raw past transitions and replays them during training to improve sample efficiency. It preserves what happened, not what was learned from what happened. Memory scaffolding stores distilled, reflection-generated insights: study notes, not lecture recordings. (Modern variants like Hindsight Experience Replay and Synthetic Experience Replay blur this boundary by rewriting or generating transitions, but they still operate on experience-level data rather than articulated principles.)

*Memory-augmented RL* systems occupy nearby territory but differ in focus. MemRL provides episodic memory at inference time for runtime adaptation, operating after training is complete. Mem-alpha uses RL training itself to teach models when and how to manage external memory, but its goal is to produce a model that uses memory well at deployment, not to accelerate internalisation into weights. Memory scaffolding inverts both: it operates *during* training with the explicit goal of accelerating weight internalisation so that the scaffolding can eventually be removed.

*Curriculum learning* controls the order and difficulty of training inputs. It shapes what the model encounters, not what it remembers about previous encounters.

The differentiator in each case is the same: memory scaffolding produces its content through deliberate reflection on completed episodes, not through recording, replaying, or reordering. And the mnemonic bridging phase trains reasoning habits that outlive the scaffolding itself, a property none of the adjacent approaches share.

## Theoretical Foundation

There is a structural parallel worth noting. LLMs originally acquired intelligence by absorbing patterns from explicit human-generated text into their weights. The entire pretraining process is, in a sense, a transfer from external language into internal structure. Memory scaffolding recapitulates this dynamic at the fine-tuning stage: explicit text (the scratchpad) scaffolds implicit learning (weight updates) and is then retired once the patterns are internalised.

## From Theory to Practice

This theory grew out of a small informal experiment: a persistent memory system for an AI coding assistant, where curated learnings were stored in structured markdown and provided as session context. A separate reflection process periodically reviewed recent sessions and updated the memory store. It was not a controlled study; just a single agent, one session at a time, with no cross-session analysis by the same agent. But the in-context learning effects were noticeable.

Concrete examples: the agent gradually accumulated knowledge of bash syntax quirks across platforms, avoiding the same gotchas that had tripped it up in earlier sessions. When operating a browser-based tool, it learned through trial and error that clicking UI elements with cursor coordinates was unreliable, and recorded a preference for keyboard shortcuts and command-based navigation, then consistently applied that preference in future sessions without re-learning it.

None of this constitutes evidence that memory scaffolding would work during training. The system operates entirely at inference time, with no weight updates involved. But it does suggest that the underlying mechanism is sound: reflection-generated, curated knowledge provided as context measurably improves an agent's performance on tasks where it previously struggled. The theory asks whether that same principle can be applied during RL post-training, where the weight updates would have the opportunity to internalise what the scaffolding provides.

## Open Questions

**Effectiveness of self-elicited mnemonics.** Does a model that learns to invoke a mnemonic label in its reasoning trace actually activate the intended circuits, or does it become a superficial verbal habit with no causal role in the output? Ablation studies comparing performance with and without reasoning-trace cues would help clarify.

**Mnemonic persistence and drift.** Do self-elicited cues remain stable and useful over long training horizons, or do they drift in meaning as the model's weights continue to evolve? The cue "apply the boundary-check heuristic" only helps if the circuits it originally pointed to are still intact.

**Reflection quality at scale.** Can the reflection process be automated effectively, or does it require heavy human oversight to avoid compounding bad generalisations?

**Optimal scratchpad sizing and retrieval.** Too large pollutes context; too small misses patterns. Hierarchical organisation and topic-based retrieval help, but optimal parameters are empirical.

**Compatibility with existing pipelines.** Integration with PPO, DPO, reward models, and other RLHF infrastructure adds engineering complexity that may constrain the design space in practice.

**What transfers well through text?** Reasoning heuristics, favourable response formats, safety rules, and structural conventions should scaffold well. Subtle tonal calibration or holistic judgement may not. Those may require standard gradient descent without shortcuts.

**Interaction with chain-of-thought training.** Models already trained with extended thinking have existing reasoning-trace habits. How mnemonic bridging interacts with (or could be integrated into) those existing regimes is both a practical design question and a window into whether the model's circuits already support some form of self-scaffolding that could be amplified during RL.

**Applicability beyond RL.** This theory targets reinforcement learning, where the absence of structured memory is most acute. But there may be edge cases where SFT also suffers from a learning-from-experience deficit: noisy or contradictory training data, very limited examples, or tasks requiring complex multi-step reasoning. Whether a reflection-generated scratchpad could provide value even under dense supervision is worth probing empirically.

**Training the reflector.** The reflection sessions that populate the scratchpad are themselves a learnable skill. As RL training improves the model's general reasoning, reflection quality may improve indirectly — but the effect is attenuated, because RL reward signals flow through future task outputs, not through the scratchpad generation itself. The model is trained to *use* good reflections, not to *produce* them. Whether reflection quality should be explicitly trained — perhaps through a separate reward signal that scores scratchpad entries by their downstream effect on task performance — is an open design question. Doing so would create a meta-learning loop: the model learns to learn better. The risk is the same as in any meta-optimisation: compounding errors in the reflection process could propagate into the scratchpad and from there into training, with no corrective pressure if the reward signal for reflection quality is poorly calibrated.

---

*The mechanism described here is not new to human learning. It is arguably the oldest educational technology we have. What is new is the observation that a phase of modern AI training operates without it, and the specific proposal for how to introduce it. Whether the analogy between human study habits and RL training methodology proves fruitful is an empirical question. But the structural gap it addresses (blind exploration with sparse feedback and no memory) is real, and it is worth asking whether the solution that humans converged on independently might transfer.*
