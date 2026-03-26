---
layout: post
title: "The Architecture Discovery Tax"
subtitle: "Why Neural Networks Pay Double, and What That Means for Reinforcement Learning"
date: 2026-03-27
note: "A companion essay to <a href='/machine-consciousness/memory-scaffolding-during-reinforcement-learning/'>Memory Scaffolding During Reinforcement Learning</a>."
---

## The Observation

When an LLM is trained from scratch, it needs millions or billions of examples to reach competence. A human child learns the concept of "cup" from a handful of encounters. This disparity in sample efficiency is one of the oldest observations in AI research, and the standard explanation is some version of "brains are just better learners." That explanation is incomplete. Learning algorithms are part of the story — but there is a deeper factor that is often overlooked. The gap is not only about *how* networks learn. It is also about *what* they must learn.

A human infant arrives with a brain that already contains functional circuits shaped by hundreds of millions of years of evolutionary selection. The visual cortex is pre-wired for hierarchical feature extraction. The hippocampus is structured for episodic memory indexing. The cerebellum is built for timing and motor coordination. These are not blank computational substrates waiting to be trained. They are sophisticated information-processing architectures that evolution has already optimised for the kinds of problems the organism will encounter.

A neural network starts from random initialisation. Before it can learn anything useful about the world, it must first discover the computational motifs that make such learning possible. It must find that hierarchical feature extraction is a good strategy. It must develop attention-like circuits for relational reasoning. It must build internal structures for variable binding, compositionality, and abstraction. Only after these structures exist can gradient descent begin the work of filling them with knowledge.

**This is the architecture discovery tax:** the cost of simultaneously searching for both the right computational structures and the right knowledge to encode in them. Biological brains got the architecture part prepaid by evolution. Neural networks must pay for it out of the training budget.

## The Evidence

This observation is not new, though its implications may be underappreciated.

The most rigorous articulation comes from Anthony Zador at Cold Spring Harbor Laboratory. His 2019 paper in Nature Communications argued that most animal behaviour is not the product of clever learning algorithms but is encoded in the genome. Animals are born with highly structured brain connectivity that enables rapid learning. The neural network community, Zador argued, has aligned itself with "Team Nurture" by focusing on tabula rasa networks, and this is a fundamental mistake. He introduced the concept of the *genomic bottleneck*: the compression of wiring rules into the genome such that functional circuits can be assembled at birth from a compact developmental program. In follow-up experimental work (PNAS, 2024), his group demonstrated that standard architectures can be compressed by several orders of magnitude through such a bottleneck, yielding pre-training performance approaching that of the fully-trained network, and for complex problems, capturing essential circuit features that enhanced transfer learning to novel tasks.

Several independent lines of research converge on the same point from different directions. The lottery ticket hypothesis (Frankle & Carlin, 2018) showed that within overparameterised networks, sparse subnetworks exist that can match full performance if trained from the right initialisation, implying that a significant fraction of early training is spent simply identifying which subnetwork to use. Architecture search masquerading as gradient descent.

Inductive bias research (Bengio et al., 2022, Royal Society) approached the question from the other direction: rather than showing what networks must discover, it catalogued the priors that biological cognition already relies on (modularity, sparsity, causal reasoning, compositionality) and argued that deep learning needs to be extended in qualitative, not just quantitative, ways to incorporate these structural assumptions.

Mechanistic interpretability work at Anthropic revealed that transformers undergo phase transitions during training where they suddenly develop computational motifs: induction heads, copy-suppression circuits, indirect object identification circuits. These are not facts being memorised. They are functional structures emerging in weight space, and they need to exist before the model can efficiently learn certain categories of knowledge.

More recently, synergistic core research (2025) found that LLMs spontaneously develop information-integration structures in their middle layers that are remarkably similar to those found in the human brain. These structures are absent in randomly initialised networks, and when ablated, they cause disproportionate performance loss. The independent emergence of the same computational architecture in biological and artificial systems, despite vastly different substrates and learning rules, suggests a fundamental computational principle that both evolution and gradient descent converge on. But evolution gets there faster.

And evolutionary conditioning experiments (2025) demonstrated this directly: applying evolutionary pressure to artificial neural networks (using a genetic algorithm to optimise a network's *potential* to learn rather than directly optimising performance) produced significantly faster knowledge acquisition. Evolution, it appears, tunes neural systems to enable rapid learning by shaping their inductive landscape. Precisely the advantage that biological brains arrive with and neural networks must discover on their own.

## The Counterargument

There is a notable counterposition, articulated most directly in response to Zador's work. The argument runs: biological brains benefit from evolutionary priors, but this is because biological learning algorithms are — by the standards of modern optimisation — *weak*. Biological learning is constrained by locality (synapses can only use information available at their own junction), limited lifespans, and the absence of anything like backpropagation's ability to propagate error signals across an entire network. Evolution compensates for these suboptimal learning rules by pre-building intricate circuit structures.

Backpropagation, by contrast, is an enormously powerful optimiser. It is not constrained by locality or lifespan. Given enough data, it can discover any structure that evolution could provide, and it does so without the risk of baking in the *wrong* priors. From this perspective, the architecture discovery tax is real but acceptable: the cost of tabula rasa learning is high in data, but the result is a more flexible system unconstrained by potentially maladaptive innate assumptions.

The scaling laws community implicitly endorses this view. The empirical finding that model performance improves predictably with more data, compute, and parameters suggests that brute-force discovery of computational structure is not just feasible but efficient at scale. Why engineer in priors when gradient descent will find the right answer?

This counterargument deserves serious weight. It correctly identifies that biological evolution and artificial training exist in very different optimisation regimes, and that lessons from one do not transfer straightforwardly to the other. But it also, perhaps inadvertently, concedes the central observation: that LLMs *are* paying the architecture discovery tax. The disagreement is about whether the tax matters in practice, not about whether it exists.

## The Tripartite Gap

Framing the sample efficiency gap as purely an architecture discovery problem is itself incomplete. The missing evolutionary priors span at least three levels.

The first is *computational architecture*, Zador's primary focus. Biological brains arrive with modular, specialised circuits for specific problem types. Neural networks start with a uniform architecture and must discover internal specialisation through training. The transformer architecture encodes some useful biases (attention is inherently relational, the residual stream enables superposition), but these are far less rich than what evolution provides.

The second is *learning algorithms*. Biological learning uses highly non-uniform plasticity rules: Hebbian learning, spike-timing-dependent plasticity, neuromodulatory gating, sleep-phase consolidation. These are specialised learning rules for specialised circuits, themselves products of evolutionary selection. Backpropagation is a single uniform rule applied everywhere: powerful in aggregate but inefficient at the level of individual circuit formation, because it is doing architecture discovery with a tool that was not designed for architecture discovery.

The third is *input richness*. A child learning "cup" receives multimodal sensory grounding, motor interaction, social reinforcement, and temporal continuity from a single encounter. An LLM seeing the token "cup" in a sentence gets one thin slice of distributional co-occurrence. The information density per example is radically different. This is not strictly an evolutionary prior, but it is a consequence of the embodied substrate that evolution produced, and it dramatically inflates the number of examples an LLM needs to reach an equivalent internal representation.

Disentangling the relative contributions of these three factors is an open empirical question. Current LLMs are deficient at all three, and improving any one of them could reduce sample requirements. Crucially, different factors may dominate at different stages of training — architecture discovery weighs heaviest during pretraining, while learning process limitations become the binding constraint during reinforcement learning, where the architecture already exists but the training loop provides no memory, no reflection, and no structured credit assignment.

## Where This Meets Post-Training

Here is the observation that motivates this essay as a companion to the Memory Scaffolding theory: **the architecture discovery tax is primarily a pretraining cost, and the problem of learning from experience that remains afterward is at its worst during reinforcement learning.**

By the time a foundation model enters post-training, the circuit formation phase is largely complete. The model has already developed induction heads, attention patterns, internal feature hierarchies, and the synergistic cores that interpretability research has identified. The computational motifs exist. What post-training must do is develop and refine the knowledge and behaviours that flow through these existing structures.

Supervised fine-tuning handles this reasonably well. Its learning signal is dense (every token has a clear target), and the reference outputs implicitly demonstrate effective approaches. The teacher is showing the pattern. SFT does not face this problem because the training data already shows what the model needs to learn.

Reinforcement learning is different. Its learning signal is sparse (a single scalar per output), its exploration is blind (no record of what has been tried before), and its episodes are memoryless (each begins from zero). The architecture exists — the tax has been paid — but the model is navigating a vast space of possible behaviours with no compass and no map.

This is the specific gap that the Memory Scaffolding theory addresses. Not the architecture discovery problem, which belongs to pretraining, but the problem of learning from experience specific to RL: the structural absence of cross-episode continuity, structured credit assignment, and cumulative learning. The companion essay describes the mechanism in detail: a reflection-generated scratchpad that provides what the RL loop structurally lacks, with a mnemonic bridging phase that trains the model to activate internalised patterns once the scaffolding is removed.

## A Testable Prediction

This framing generates a specific, testable prediction about how Memory Scaffolding should affect a model's internal representations during RL training.

If the architecture discovery tax is real and largely paid during pretraining, then scaffolded RL should not dramatically change the model's computational architecture: the circuits should remain structurally similar to the unscaffolded baseline. What should change is the *efficiency with which knowledge flows through those circuits.*

Concretely, this predicts:

**Stable circuit structure.** Probing classifiers applied to intermediate representations should show similar computational motifs in scaffolded and unscaffolded models after RL. The same induction heads, the same attention patterns, the same synergistic cores. Scaffolding does not build new circuits; it makes better use of existing ones.

**Faster knowledge routing.** Activation patching experiments should show that scaffolded models develop cleaner information flow earlier in RL training. The right knowledge reaches the right circuits sooner, because the scratchpad guides the model toward high-quality outputs that give gradient descent a cleaner reward signal for refining knowledge pathways.

**Reduced representational interference.** RL without scaffolding risks the model learning contradictory or redundant representations across episodes, since it cannot remember what it tried before. Scaffolded RL, by providing cross-episode context, should produce representations with less internal conflict, measurable as lower interference in multitask probing experiments.

**Mnemonic bridging as knowledge-access training.** The mnemonic bridging phase, where the model learns to invoke self-generated reasoning cues, should be understood not as architecture modification but as *access pattern training*: teaching the model's existing circuits a reliable way to locate and activate the knowledge that was organised during the scaffolded phase. The cues are addresses, not structures.

## Positioning the Theory

The existing literature offers clear diagnoses of the sample efficiency gap and strong opinions about what to do at the pretraining level.

Zador and the nativist camp argue for building more innate structure into networks: better architectures, genomic bottleneck initialisation, meta-learned priors. This addresses the architecture discovery tax directly but requires knowing what priors to install, and risks installing the wrong ones.

The scaling camp argues that more data and compute will overcome the tax through brute force. This has been empirically validated at enormous scale, but is silent on what to do during RL, where the data budget is smaller, the learning signal is sparser, and the cost of inefficient exploration is proportionally higher.

The world model camp, most vocally Yann LeCun, would reject the premise of improving RL altogether. LeCun has argued that RL is inherently too sample-inefficient to be worth fixing, and that the correct response is to replace trial-and-error exploration with planning over learned world models: if you can simulate outcomes internally, you do not need the reward-and-exploration loop at all. This is the strongest structural objection to Memory Scaffolding: not that the diagnosis is wrong, but that the patient is terminal and the effort is better spent elsewhere. The pragmatic response is twofold. First, LeCun's world model architectures (JEPA and its successors) remain research-stage, while RL is how frontier models are actually trained today and will be for the foreseeable future; scaffolding is an intervention for the paradigm that exists, not the one that might replace it. Second, even world models will need to be trained, and if any part of that training involves reward-based learning (which LeCun himself concedes may sometimes be necessary), the learning-from-experience problem resurfaces, and the core scaffolding insight is not architecture-specific.

Memory Scaffolding occupies a different niche entirely. It does not try to reduce the architecture discovery tax at pretraining; it accepts that cost as already paid by the time RL begins. It does not compete with SFT, which has its own dense supervision mechanism. Instead, it addresses the *learning-from-experience problem specific to reinforcement learning*: the combination of sparse reward signals, blind exploration, and memoryless episodes that makes RL the least sample-efficient phase of the training pipeline. The scratchpad provides what the RL loop structurally lacks: cross-episode continuity, structured credit assignment, and cumulative learning.

## Open Questions

**How much architecture discovery happens during RL?** The claim that circuit formation is "largely complete" after pretraining is an assumption, not an established fact. Some RL tasks may require novel computational motifs that did not emerge during pretraining. If so, Memory Scaffolding might also accelerate circuit formation by providing cleaner gradient signals, but this would be an indirect effect, not the primary mechanism.

**Does the learning-from-experience bottleneck scale with model size?** Larger models may pay a proportionally smaller architecture discovery tax at pretraining. If so, the learning-from-experience problem during RL becomes an increasingly dominant bottleneck at scale, which would make scaffolding *more* valuable, not less, as models grow.

**Can the tax be measured directly?** A clean experiment would compare pretraining convergence curves between randomly initialised models and models initialised via Zador's genomic bottleneck, then apply identical RL (with and without scaffolding) to both. This would disentangle the contribution of pretraining architecture priors from RL-phase learning from experience.

---

*The architectural priors debate asks what a student should know at birth. The scaling debate asks how much homework is enough. Supervised fine-tuning gives the student an answer key. Memory Scaffolding asks: what if we gave the student a notebook?*
