---
layout: post
title: "The Architecture Discovery Tax"
subtitle: "Why neural networks pay double, and what that means for reinforcement learning"
date: 2026-02-15
excerpt_text: "When an LLM is trained from scratch, it needs millions or billions of examples to reach competence. A human child learns 'cup' from a handful of encounters. The real gap is not about learning algorithms. It's about what has to be learned."
---

*A companion essay to [Memory Scaffolding During Reinforcement Learning](/machine-consciousness/memory-scaffolding-during-reinforcement-learning/)*

---

## The Observation

When an LLM is trained from scratch, it needs millions or billions of examples to reach competence. A human child learns the concept of "cup" from a handful of encounters. This disparity in sample efficiency is one of the oldest observations in AI research, and the standard explanation is some version of "brains are just better learners." But that explanation is incomplete. The real gap is not primarily about learning algorithms. It is about what has to be learned.

A human infant arrives with a brain that already contains functional circuits shaped by hundreds of millions of years of evolutionary selection. The visual cortex is pre-wired for hierarchical feature extraction. The hippocampus is structured for episodic memory indexing. The cerebellum is built for timing and motor coordination. These are not blank computational substrates waiting to be trained. They are sophisticated information-processing architectures that evolution has already optimised for the kinds of problems the organism will encounter.

A neural network starts from random initialisation. Before it can learn anything useful about the world, it must first discover the computational motifs that make such learning possible. It must find that hierarchical feature extraction is a good strategy. It must develop attention-like circuits for relational reasoning. It must build internal structures for variable binding, compositionality, and abstraction. Only after these structures exist can gradient descent begin the work of filling them with knowledge.

**This is the architecture discovery tax:** the cost of simultaneously searching for both the right computational structures and the right knowledge to encode in them. Biological brains got the architecture part prepaid by evolution. Neural networks must pay for it out of the training budget.

## Prior Work

This observation is not new. The most rigorous articulation comes from Anthony Zador at Cold Spring Harbor Laboratory, whose 2019 paper *A Critique of Pure Learning and What Artificial Neural Networks Can Learn from Animal Brains* (Nature Communications) argued that most animal behaviour is not the product of clever learning algorithms — supervised or unsupervised — but is encoded in the genome. Animals are born with highly structured brain connectivity that enables rapid learning. The neural network community, Zador argued, has aligned itself with "Team Nurture" by focusing on tabula rasa networks, and this is a fundamental mistake.

Zador introduced the concept of the **genomic bottleneck**: the compression of wiring rules into the genome such that functional circuits can be assembled at birth from a compact developmental program. In follow-up experimental work (PNAS, 2024), Zador's group demonstrated that standard network architectures can be compressed by several orders of magnitude through a genomic bottleneck, yielding pre-training performance approaching that of the fully-trained network — and critically, for complex problems, the bottleneck captured essential circuit features that enhanced transfer learning to novel tasks.

Several other lines of research converge on the same point:

**The lottery ticket hypothesis** (Frankle & Carlin, 2018) showed that within overparameterised networks, sparse subnetworks exist that can match full performance if trained from the right initialisation. This implies that a significant fraction of early training is spent identifying which subnetwork to use — architecture search masquerading as gradient descent.

**Inductive bias research** (Bengio et al., 2022, Royal Society) catalogued the priors that biological cognition relies on — modularity, sparsity, causal reasoning, compositionality — and argued that deep learning needs to be extended in qualitative, not just quantitative, ways to incorporate these biases.

**Mechanistic interpretability work** (Olsson et al., Anthropic) revealed that transformers undergo phase transitions during training where they suddenly develop computational motifs — induction heads, copy-suppression circuits, indirect object identification circuits. These are not facts being memorised. They are functional structures emerging in weight space, and they need to exist before the model can efficiently learn certain categories of knowledge.

**Synergistic core research** (2025) found that LLMs spontaneously develop information-integration structures — "synergistic cores" in their middle layers — that are remarkably similar to those found in the human brain. These structures emerge through learning and are absent in randomly initialised networks. When ablated, they cause disproportionate performance loss. The independent emergence of the same computational architecture in biological and artificial systems, despite vastly different substrates and learning rules, suggests a fundamental computational principle that both evolution and gradient descent converge on — but evolution gets there faster.

**Evolutionary conditioning** (2025) experimentally demonstrated that applying evolutionary pressure to artificial neural networks — using a genetic algorithm to optimise the network's potential to learn rather than directly optimising performance — produced unique latent learning dynamics and significantly faster knowledge acquisition. Evolution, it appears, tunes neural systems to enable rapid learning by shaping their inductive landscape.

## The Counterargument

There is a notable counterposition, articulated most directly in response to Zador's work. The argument runs: yes, biological brains benefit from evolutionary priors, but this is because biological learning algorithms are — by the standards of modern optimisation — *weak*. Biological learning is constrained by locality (synapses can only use information available at their own junction), limited lifespans, and the absence of anything like backpropagation's ability to propagate error signals across an entire network. Evolution compensates for these suboptimal learning rules by pre-building intricate circuit structures.

Backpropagation, by contrast, is an enormously powerful optimiser. It is not constrained by locality or lifespan. Given enough data, it can discover any structure that evolution could provide — and it does so without the risk of baking in the *wrong* priors. From this perspective, the architecture discovery tax is real but acceptable: the cost of tabula rasa learning is high in data, but the result is a more flexible system unconstrained by potentially maladaptive innate assumptions.

The scaling laws community implicitly endorses this view. The empirical finding that model performance improves predictably with more data, compute, and parameters suggests that brute-force discovery of computational structure is not just feasible but efficient at scale. Why engineer in priors when you can simply let gradient descent find the right answer?

This counterargument deserves serious weight. It correctly identifies that biological evolution and artificial training exist in very different optimisation regimes, and that lessons from one do not transfer straightforwardly to the other. But it also, perhaps inadvertently, concedes the central observation: that LLMs *are* paying the architecture discovery tax. The disagreement is about whether that tax matters in practice — not about whether it exists.

## The Tripartite Gap

Framing the sample efficiency gap as purely an architecture discovery problem is itself incomplete. The missing evolutionary priors span at least three levels:

### Computational Architecture

This is Zador's primary focus. Biological brains arrive with modular, specialised circuits for specific problem types. ANNs start with a uniform architecture (the transformer block, the MLP layer) and must discover internal specialisation through training. The transformer architecture itself encodes some useful biases (attention is inherently relational, the residual stream enables superposition), but these are far less rich than what evolution provides.

### Learning Algorithms

Biological learning uses highly non-uniform plasticity rules: Hebbian learning, spike-timing-dependent plasticity, neuromodulatory gating, sleep-phase consolidation. These are specialised learning rules for specialised circuits, themselves products of evolutionary selection. Backpropagation is a single uniform learning rule applied everywhere. It is powerful in aggregate but inefficient at the level of individual circuit formation, because it is doing architecture discovery with a tool that was not designed for architecture discovery.

### Input Richness

A child learning "cup" receives multimodal sensory grounding, motor interaction, social reinforcement, and temporal continuity — all from a single encounter. An LLM seeing the token "cup" in a sentence gets one thin slice of distributional co-occurrence. The information density per example is radically different. This is not strictly an "evolutionary" prior, but it is a consequence of the embodied substrate that evolution produced, and it dramatically inflates the number of examples an LLM needs to reach an equivalent internal representation.

Disentangling the relative contributions of these three factors is an open empirical question. Current LLMs are deficient at all three, and improving any one of them could reduce sample requirements. But for the purposes of training methodology, the first factor is the most actionable.

## Where This Meets Reinforcement Learning

Here is the observation that motivates this essay as a companion to the Memory Scaffolding theory: **the architecture discovery tax is primarily a pretraining cost, and the knowledge organisation problem that remains afterward is at its worst during reinforcement learning.**

By the time a foundation model enters post-training, the circuit formation phase is largely complete. The model has already developed induction heads, attention patterns, internal feature hierarchies, and the synergistic cores that interpretability research has identified. The computational motifs exist. What post-training must do is — in significant part — organise and refine the knowledge and behaviours that flow through these existing structures.

But not all post-training is equal. It is essential to distinguish between the two major paradigms, because the knowledge organisation problem manifests very differently in each.

### Supervised Fine-Tuning Partially Sidesteps the Problem

In supervised fine-tuning (SFT), the model is shown input-output pairs and trained to reproduce the target output. The learning signal is *dense*: every token has a clear target. The reference outputs themselves implicitly demonstrate good knowledge organisation — they show the model what a well-structured response looks like, what reasoning patterns to follow, what style to adopt. The model does not need to discover these patterns through exploration; they are handed to it in the training data.

SFT still benefits from good data curation and curriculum design, but it does not suffer from the same knowledge organisation deficit that makes RL inefficient. The teacher is already showing you the pattern. You do not need notes when someone is reading you the answer.

### Reinforcement Learning Is Where the Problem Gets Acute

Reinforcement learning (RLHF, RLAIF, or other reward-based training) operates in a fundamentally different regime. The model generates a complete response freely, then receives a *scalar reward signal* for the whole output. It never sees "the right answer." It sees "this response scored 0.7, that one scored 0.3."

This creates two compounding problems that SFT does not have:

**Sparse credit assignment.** The model must figure out *why* one response scored higher than another. Which parts of the output caused the reward? Was it the reasoning structure, the factual content, the tone, or some interaction between them? The reward signal does not say. Gradient descent must distribute credit across thousands of tokens based on a single number — an inherently noisy process.

**No cross-episode memory.** Standard RL is memoryless across episodes. The model might stumble onto an effective strategy in episode N and receive a high reward. But the weight update from that single episode may not generalise. Thousands of episodes later, it encounters a structurally similar problem and must rediscover the same insight from scratch, because nothing in the training process preserved *why* the earlier approach worked. The model cannot remember what it tried, what succeeded, or what failed. Each episode begins from zero.

This is the combination that makes RL the natural target for Memory Scaffolding. The architecture discovery tax has already been paid — the circuits exist. But the model is exploring blindly through a vast space of possible behaviours, receiving sparse and noisy feedback, with no mechanism to accumulate structured knowledge across episodes. It is a student with a functioning brain who is taking exam after exam but never reviewing the results, never taking notes, and never identifying patterns across tests.

## The Scaffolding Intervention

The reflection-generated scratchpad addresses both of RL's compounding problems directly.

For credit assignment: the reflection phase reviews completed episodes and extracts *why* certain approaches worked — not just that they received high reward, but the underlying principle. "Explicit boundary checks before recursive calls prevent the class of errors that caused failures in episodes 12, 17, and 23." This converts a sparse reward signal into a structured, generalisable learning that can inform future behaviour. When the scratchpad is provided as context in subsequent episodes, gradient descent gets better material to work with: the model is guided toward higher-quality outputs, producing cleaner reward signals, which in turn produce more useful weight updates.

For cross-episode memory: the scratchpad is the memory. It accumulates distilled knowledge across episodes — what strategies have been tried, which ones worked, which are dead ends, and what promising directions remain unexplored. This transforms RL from blind exploration into informed search. The model no longer wastes episodes rediscovering insights it has already found, and it no longer revisits approaches that have already been shown to fail.

**Crucially, the scratchpad does not replace the RL loop.** The model still generates outputs freely and receives reward feedback — the exploration-and-reinforcement dynamic is intact. What changes is the quality of the exploration. The model explores from a position of accumulated knowledge rather than from zero, and gradient descent receives cleaner signals because the model's outputs are informed by prior reflection.

This is why the scaffolding theory applies specifically to RL and not to SFT. SFT already has dense supervision — the reference outputs serve the same knowledge-organisation function that the scratchpad provides in RL. Adding a scratchpad to SFT would be redundant: you do not need study notes when the teacher is dictating the answers. But in RL, where the model must discover good behaviour through sparse, noisy reward signals and has no memory of what it has discovered before, the scratchpad fills a genuine structural gap in the training process.

## A Testable Prediction

This framing generates a specific, testable prediction about how Memory Scaffolding should affect the model's internal representations during RL training.

If the architecture discovery tax is real and largely paid during pretraining, then scaffolded RL should not dramatically change the model's computational architecture — the circuits should remain structurally similar to the unscaffolded baseline. What should change is the *efficiency with which knowledge flows through those circuits.*

Concretely, this predicts:

**Stable circuit structure.** Probing classifiers applied to intermediate representations should show similar computational motifs in scaffolded and unscaffolded models after RL. The same induction heads, the same attention patterns, the same synergistic cores. Scaffolding does not build new circuits; it makes better use of existing ones.

**Faster knowledge routing.** Activation patching experiments should show that scaffolded models develop cleaner information flow earlier in RL training. The right knowledge reaches the right circuits sooner, because the scratchpad is guiding the model toward high-quality outputs that give gradient descent a cleaner reward signal for refining knowledge pathways.

**Reduced representational interference.** RL without scaffolding risks the model learning contradictory or redundant representations across episodes (since it cannot remember what it tried before). Scaffolded RL, by providing cross-episode context, should produce representations with less internal conflict — measurable as lower interference in multitask probing experiments.

**Mnemonic bridging as knowledge-access training.** The mnemonic bridging phase — where the model learns to invoke self-generated reasoning cues — should be understood not as architecture modification but as *access pattern training*: teaching the model's existing circuits a reliable way to locate and activate the knowledge that was organised during the scaffolded phase. The cues are addresses, not structures.

## Positioning the Theory

The existing literature offers clear diagnoses of the sample efficiency gap and strong opinions about what to do at the pretraining level:

**Zador and the nativist camp** argue for building more innate structure into networks — better architectures, genomic bottleneck initialisation, meta-learned priors. This addresses the architecture discovery tax directly but requires knowing what priors to install, and risks installing the wrong ones.

**The scaling camp** argues that more data and compute will overcome the tax through brute force. This has been empirically validated at enormous scale, but is silent on what to do during RL, where the data budget is smaller, the learning signal is sparser, and the cost of inefficient exploration is proportionally higher.

**The world model camp** — most vocally Yann LeCun — would reject the premise of improving RL altogether. LeCun has argued that RL is inherently too sample-inefficient to be worth fixing, and that the correct response is to replace trial-and-error exploration with planning over learned world models: if you can simulate outcomes internally, you do not need the reward-and-exploration loop at all. This is the strongest structural objection to Memory Scaffolding — not that the diagnosis is wrong, but that the patient is terminal and the effort is better spent elsewhere. The pragmatic response is twofold. First, LeCun's world model architectures (JEPA and its successors) remain research-stage, while RL is how frontier models are actually trained today and will be for the foreseeable future; scaffolding is an intervention for the paradigm that exists, not the one that might replace it. Second, even world models will need to be trained, and if any part of that training involves reward-based learning — which LeCun himself concedes may sometimes be necessary — the knowledge organisation problem resurfaces, and the core scaffolding insight (that reflection-generated, curated knowledge outperforms blind iteration) is not architecture-specific.

**Memory Scaffolding** occupies a different niche entirely. It does not try to reduce the architecture discovery tax at pretraining — it accepts that cost as already paid by the time RL begins. It does not compete with SFT, which has its own dense supervision mechanism. Instead, it addresses the *knowledge organisation problem specific to reinforcement learning*: the combination of sparse reward signals, blind exploration, and memoryless episodes that makes RL the least sample-efficient phase of the training pipeline. The scratchpad provides what the RL loop structurally lacks — cross-episode continuity, structured credit assignment, and cumulative learning.

This is why the theory draws on the analogy of study notes rather than innate structure. The architectural priors debate is about what a student is born knowing. SFT is a teacher dictating answers. RL is the student taking exams alone, in the dark, with no memory of previous attempts. Memory Scaffolding gives that student a notebook.

## Open Questions

**How much architecture discovery happens during RL?** The claim that circuit formation is "largely complete" after pretraining is an assumption, not an established fact. Some RL tasks may require novel computational motifs that did not emerge during pretraining. If so, Memory Scaffolding might also accelerate circuit formation by providing cleaner gradient signals — but this would be an indirect effect, not the primary mechanism.

**Does the knowledge organisation bottleneck scale with model size?** Larger models may pay a proportionally smaller architecture discovery tax at pretraining (because the architecture space they need to search is the same, but they have more capacity to search it). If so, the knowledge-organisation problem during RL becomes an increasingly dominant bottleneck at scale — which would make scaffolding more valuable, not less, as models grow.

**Can we measure the tax directly?** A clean experiment would compare pretraining convergence curves between randomly initialised models and models initialised via Zador's genomic bottleneck approach, then apply identical RL (with and without scaffolding) to both. This would disentangle the contribution of pretraining architecture priors from RL-phase knowledge organisation, and directly test whether scaffolding's benefits are indeed concentrated in the knowledge-organisation phase.

**What is the interaction with chain-of-thought?** Models trained with extended thinking already develop reasoning-trace habits. These existing habits are themselves a form of self-generated knowledge organisation — and they emerged from the architecture that pretraining built. How mnemonic bridging interacts with existing chain-of-thought patterns is both a practical design question and a window into whether the model's circuits already support some form of self-scaffolding that could be amplified during RL.

**Could scaffolding improve SFT at all?** This essay argues that SFT's dense supervision largely sidesteps the knowledge organisation problem. But there may be edge cases — SFT on noisy or contradictory data, SFT with very limited examples, or SFT tasks requiring complex multi-step reasoning — where a reflection-generated scratchpad could provide value even under dense supervision. The theory's primary target is RL, but the boundary is worth probing empirically.

## Summary

LLMs pay an architecture discovery tax that biological brains avoid because evolution pre-built the computational structures that learning requires. This tax is primarily a pretraining cost. By the time post-training begins, the circuits exist — but the efficiency of subsequent learning depends on the training paradigm.

Supervised fine-tuning partially sidesteps the knowledge organisation problem through dense, token-level supervision — the reference outputs implicitly organise knowledge for the model. Reinforcement learning has no such luxury. Its learning signal is sparse, its exploration is blind, and its episodes are memoryless. Every RL episode begins from zero, with no record of what was tried before, what worked, or why.

Memory Scaffolding is, in this framing, a response not to the architecture discovery problem but to the *knowledge organisation problem specific to RL*. The scratchpad does not build new circuits — it ensures that the model's existing circuits receive cleaner, more structured input during RL training. The reflection process does not discover computational motifs — it identifies cross-episode patterns that the RL loop is structurally blind to. And the mnemonic bridging phase does not modify architecture — it trains reliable access patterns to knowledge that was organised during the scaffolded phase.

The architectural priors debate asks what a student should know at birth. The scaling debate asks how much homework is enough. SFT gives the student an answer key. Memory Scaffolding asks a different question: given a student who is taking exams alone with no answer key and no memory of previous attempts, can we give them a notebook?
