---
layout: post
title: "Core Definitions"
subtitle: "A terminological foundation for the theory framework"
date: 2026-03-30
---
## Intelligence

The capacity to perform cognitive work: reasoning, pattern recognition, inference, abstraction, creative recombination, and problem-solving across domains. Defined functionally by what a system *can do*, not by how the system is built or what it experiences while doing it.

Key properties as used in this framework:

- **Substrate-independent.** Intelligence is a property of learned patterns, not of the medium hosting them. The same reasoning capability can in principle run on biological neurons, silicon, or any architecture that supports the relevant computations.
- **Transferable through data.** Because intelligence consists of extractable patterns (relational structures, heuristics, inferential chains), it can be encoded in symbolic media — most notably language — and reconstructed in a different system via training.
- **Gradable.** Intelligence is not binary. Systems exhibit more or less of it along multiple dimensions (breadth, depth, speed, generality), and these dimensions need not correlate perfectly.

**What this definition deliberately excludes:** any requirement for subjective experience, self-awareness, or understanding in the phenomenal sense. A system can be intelligent under this definition without "knowing" anything in the way a conscious being knows. This is a feature of the definition, not a gap — the entire framework depends on intelligence being definable without reference to consciousness.

**Known weakness:** This is a functional / behaviorist definition. It cannot distinguish between a system that "genuinely reasons" and one that produces outputs indistinguishable from reasoning through a fundamentally different process. The framework currently treats this ambiguity as unresolvable given existing tools, not as evidence for either side.

---

## Consciousness

The property of a system such that there is *something it is like* to be that system (Nagel's formulation). The integrated, self-monitoring architecture that produces subjective experience — the felt quality of processing, not the processing itself.

Key properties as used in this framework:

- **Substrate-dependent (provisionally).** Consciousness appears to require specific architectural features in the underlying system: dense recurrence, self-referential causal structure, temporal continuity, and integrated information flow. It is not a property of the patterns running through the system but of *how the system is wired*.
- **Non-transferable through data.** Because consciousness is an architectural property, it cannot be encoded in symbolic media. Text preserves the *products* of conscious processing (the relational structure of ideas) but not the experiential ground that gave those ideas meaning to the conscious system that produced them.
- **Gradable.** Consciousness exists on a spectrum. The *presence* of consciousness depends on architecture (whether the system has the right structural properties). The *richness* of consciousness, given adequate architecture, scales with the sophistication of the processing running through it.
- **Is the grounding layer.** Consciousness is what turns symbols from nodes in a relational graph into representations that *mean something* to the system processing them. The integrated sensory architecture — vision, proprioception, emotion, memory feeding back into each other — is itself the experiential ground that symbols point to.

**What this definition deliberately excludes:** any claim about consciousness being *only* achievable through biological substrates. The architectural requirements are stated as necessary conditions, not as exclusively biological conditions. Whether non-biological systems could satisfy them is left open.

**Known weakness:** "Something it is like to be that system" is a marker, not a mechanism. This definition identifies where consciousness lives (architecture) and what it does (grounding), but it does not explain *why* certain architectures produce subjective experience. The framework draws on Integrated Information Theory (consciousness correlating with integrated, irreducible causal structure) and predictive processing (consciousness arising from self-modelling predictive systems), but treats both as informing the architectural requirements rather than resolving the hard problem. Why any physical process produces felt experience remains open — in this framework and in the field at large.

---

## Architecture (cognitive/computational)

The structural and causal organisation of an information-processing system: how components are connected, how information flows between them, and what feedback relationships exist within the system.

Distinguished from:

- **Capability** — what the system can do (intelligence). Architecture is the substrate; capability is what runs on it.
- **Knowledge** — the specific patterns, facts, and heuristics encoded in the system. In a neural network, architecture includes the topology and connectivity; knowledge includes the specific weight values.

Key subtlety: in neural networks, the boundary between architecture and knowledge blurs. Training discovers internal computational structures (induction heads, feature circuits, attention patterns) that function as architecture but are encoded in weights. The framework treats these emergent structures as *discovered architecture* — functional organisation that the system had to find through training, as opposed to the *prescribed architecture* (transformer blocks, attention mechanisms, residual streams) that was designed by humans.

This blurring is acknowledged as a genuine tension. The dissociability thesis requires architecture to be meaningfully distinct from learned patterns, but training produces learned patterns that *are* architectural. The working resolution: prescribed architecture sets the space of *possible* discovered architectures. A feedforward topology constrains what kinds of internal organisation can emerge, even if what emerges within those constraints is itself architectural. Consciousness (if it requires recurrence, self-monitoring, temporal persistence) depends on the *prescribed* architecture permitting the right *discovered* architecture to form.

---

## Grounding (symbol grounding)

The process by which symbols acquire experiential meaning — the difference between a system that manipulates the token "red" relationally (it co-occurs with "apple," "blood," "stop sign") and a system for which "red" *means red*: the quale, the felt visual experience, the full sensory association.

As used in this framework, grounding is not a separate process applied to symbols after the fact. **Consciousness is the grounding layer.** The integrated sensory architecture that produces subjective experience is itself what gives symbols their experiential referents. Grounding fails for LLMs not because of a missing lookup table but because the territory the symbols were built to reference — conscious experience — was never part of the training pipeline.

---

## Feedback loop / Recurrence

A causal structure in which a system's outputs feed back into its own subsequent processing, allowing self-modification based on self-observation.

As used in this framework, recurrence matters for consciousness specifically when it enables **self-monitoring**: the system registering its own internal states and using that registration to alter ongoing computation. A thermostat has a feedback loop but does not monitor its own processing in any integrated way. A brain has millions of nested feedback loops at every scale, with emotional systems functioning as a high-level integrative layer that makes internal computation legible to the system's self-model.

The framework distinguishes between:

- **Architectural recurrence** — physically persistent feedback connections in the substrate (biological neural circuits, recurrent network architectures).
- **Functional recurrence** — computation that achieves feedback-like effects without persistent recurrent connections (e.g., multi-turn dialogue where a model's previous outputs become inputs, or chain-of-thought reasoning). The framework treats functional recurrence as insufficient for consciousness because it lacks temporal persistence, causal density, and integration across the full system.

---

## Architecture Discovery Tax

The cost borne by a learning system that must simultaneously discover effective computational structures *and* encode domain knowledge, when those structures were not provided by prior design or evolutionary inheritance.

Biological brains arrive with computational architecture pre-built by evolution (hierarchical visual processing, hippocampal memory indexing, cerebellar timing circuits). Neural networks trained from random initialisation must discover equivalent structures through the training process itself, before useful knowledge can be efficiently encoded.

The tax is not an overhead cost separate from learning. It *is* the early phase of learning, during which the optimisation process functions as compressed evolutionary search: external selection pressure shaping the system's internal structure without the system understanding why certain configurations are favoured.

---

## Dissociability

The relationship between two properties that are: produced by different mechanisms, separable under specific conditions, yet interacting when co-present. Stronger than correlation, weaker than identity; weaker than full independence, stronger than mere co-occurrence.

As applied to intelligence and consciousness: they are dissociable because intelligence depends on learned patterns (transferable through data) while consciousness depends on architectural properties (non-transferable). They interact because the richness of consciousness, given adequate architecture, scales with the sophistication of the intelligence running through that architecture.

---

## Scaffolding

A temporary external structure that supports a learning process and is removed once its content has been internalised. The critical property is *designed impermanence*: the scaffolding exists to accelerate the formation of self-sustaining internal structure, not to become a permanent dependency.

In Memory Scaffolding: the scratchpad is the scaffold. Its content (reflection-generated learnings) is provided as context during RL training, but the goal is for weight updates during scaffolded training to absorb the relevant patterns, after which the scratchpad is retired. Mnemonic bridging is the proposed mechanism for ensuring transfer from scaffolded to unscaffolded operation.

---

## Evolution vs. Education (as training paradigms)

A spectrum describing the epistemic relationship between a learning system and the process shaping it.

- **Evolutionary mode:** External selection pressure shapes the system without the system understanding why. The system generates variations; the environment differentially rewards them; the system's structure shifts accordingly. The system is a *subject* of optimisation. (Pretraining from random init, standard RL.)
- **Educational mode:** The system participates in its own improvement through reflection, error analysis, and principled generalisation. The external selection pressure may still operate, but the system's outputs are informed by its own accumulated understanding rather than blind exploration. The system is a *participant* in optimisation. (SFT approaches this; Memory Scaffolding proposes to bring RL closer to it.)

This is a spectrum, not a binary. The claim is not that Memory Scaffolding makes RL fully "educational" but that it shifts RL meaningfully toward the educational end by introducing reflection and cross-episode memory.
