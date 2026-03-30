---
layout: post
title: "The Architecture Discovery Tax: Gradient Descent as Compressed Evolution"
subtitle: "On Training, Evolution, and the Transition From Being Shaped to Being Taught"
date: 2026-03-27
note: "A companion essay to <a href='/machine-consciousness/memory-scaffolding-during-reinforcement-learning/'>Memory Scaffolding During Reinforcement Learning</a>."
---
## The Observation

When an LLM is trained from scratch, it needs millions or billions of examples to reach competence. A human child learns the concept of "cup" from a handful of encounters. This disparity in sample efficiency is one of the oldest observations in AI research, and the standard explanation is some version of "brains are just better learners." That explanation is incomplete. It understates something more fundamental about what is actually happening during training.

A human infant arrives with a brain that already contains functional circuits shaped by hundreds of millions of years of evolutionary selection. The visual cortex is pre-wired for hierarchical feature extraction. The hippocampus is structured for episodic memory indexing. The cerebellum is built for timing and motor coordination. These are not blank computational substrates waiting to be trained. They are sophisticated information-processing architectures that evolution has already optimised for the kinds of problems the organism will encounter.

A neural network starts from random initialisation. Before it can learn anything useful about the world, it must first discover the computational motifs that make such learning possible. It must find that hierarchical feature extraction is a good strategy. It must develop attention-like circuits for relational reasoning. It must build internal structures for variable binding, compositionality, and abstraction. Only after these structures exist can the process of filling them with knowledge begin.

**This is the architecture discovery tax:** the cost of simultaneously searching for both the right computational structures and the right knowledge to encode in them. Biological brains got the architecture part prepaid by evolution. Neural networks must pay for it out of the training budget.

But framing this as a "tax" — an unfortunate overhead cost — may actually undersell what is happening. Neural network training is not merely *analogous* to evolution. It shares evolution's deepest structural property: an external force shaping a system through differential selection, without the system itself understanding why certain configurations survive.

## Training as Compressed Evolution

When a population of organisms evolves over millions of years, the process is straightforward in principle: random genetic variation produces different body plans, neural architectures, and behavioural tendencies — and possibly, through epigenetic mechanisms, some configurations shaped by a parent's lifetime experience are passed forward directly. Environmental pressures differentially reward some configurations and punish others. Configurations that produce better fitness outcomes are propagated; those that don't are culled. Over time, the population converges on architectures well-suited to the problems the environment presents.

No organism in this process understands *why* it succeeds or fails. Evolution has no teacher. Natural selection cannot tell a species "your visual cortex would work better with six layers instead of four." It can only differentially reproduce organisms that happen to have better visual processing. The knowledge of *what works* is encoded in the population's genome through brute-force trial and error across generations.

Now consider pretraining a neural network. Random initialisation produces a configuration of weights. Training examples are presented, and gradient descent adjusts the weights to reduce prediction error. Configurations that produce better predictions are reinforced; those that produce worse predictions are adjusted away. Over billions of examples, the network converges on internal structures — induction heads, attention patterns, feature hierarchies — well-suited to the problems the training distribution presents.

The epistemic structure is identical: an external selection pressure shapes the system without the system understanding *why* certain configurations work. Gradient descent is a smarter evolutionary force than natural selection — it can trace the error signal backward through the entire network and make targeted adjustments, whereas evolution can only see the phenotypic outcome. This is a genuine disanalogy, and the evolutionary framing should not be pushed further than it can bear. Backpropagation is a qualitatively more powerful optimiser than natural selection: it has access to information that evolution never does. But the specific properties this essay identifies as problematic in RL (sparse scalar feedback, no cross-episode memory, no causal understanding of what worked or why) are real features of the training loop regardless of whether the evolutionary metaphor holds in full. The diagnosis does not depend on the analogy being airtight. The *model* never understands what is happening to it. It is being shaped, not taught.

This is why pretraining requires billions of examples. The model is not "learning" in the pedagogical sense — it is undergoing compressed evolutionary search. It must discover, through external selection pressure alone, both the computational architecture that evolution spent hundreds of millions of years refining *and* the knowledge to run through that architecture. The architecture discovery tax is not an overhead cost on top of learning. It is the price of conducting evolution from scratch on an accelerated timescale.

## The Evidence

This framing is not new, though its implications may be underappreciated. Several independent lines of research converge on the same structural observation.

The most rigorous articulation comes from Anthony Zador at Cold Spring Harbor Laboratory. His 2019 paper in Nature Communications argued that most animal behaviour is not the product of clever learning algorithms but is encoded in the genome. Animals are born with highly structured brain connectivity that enables rapid learning. The neural network community, Zador argued, has aligned itself with "Team Nurture" by focusing on tabula rasa networks, and this is a fundamental mistake. He introduced the concept of the *genomic bottleneck*: the compression of wiring rules into the genome such that functional circuits can be assembled at birth from a compact developmental program. In follow-up experimental work (PNAS, 2024), his group demonstrated that standard architectures can be compressed by several orders of magnitude through such a bottleneck, yielding pre-training performance approaching that of the fully-trained network, and for complex problems, capturing essential circuit features that enhanced transfer learning to novel tasks.

The lottery ticket hypothesis (Frankle & Carlin, 2018) showed that within overparameterised networks, sparse subnetworks exist that can match full performance if trained from the right initialisation, implying that a significant fraction of early training is spent simply identifying which subnetwork to use. Architecture search masquerading as gradient descent.

Inductive bias research (Bengio et al., 2022, Royal Society) approached the question from the other direction: rather than showing what networks must discover, it catalogued the priors that biological cognition already relies on (modularity, sparsity, causal reasoning, compositionality) and argued that deep learning needs to be extended in qualitative, not just quantitative, ways to incorporate these structural assumptions.

Mechanistic interpretability work at Anthropic revealed that transformers undergo phase transitions during training where they suddenly develop computational motifs: induction heads, copy-suppression circuits, indirect object identification circuits. These are not facts being memorised. They are functional structures emerging in weight space, and they need to exist before the model can efficiently learn certain categories of knowledge. Each phase transition is the training-as-evolution process discovering a new architectural motif — the artificial equivalent of a species developing a new organ.

More recently, synergistic core research (2025) found that LLMs spontaneously develop information-integration structures in their middle layers that are remarkably similar to those found in the human brain. These structures are absent in randomly initialised networks, and when ablated, they cause disproportionate performance loss. The independent emergence of the same computational architecture in biological and artificial systems, despite vastly different substrates and selection rules, suggests both evolution and gradient descent converge on the same functional solutions. But evolution gets there faster, because it has already run the search.

And evolutionary conditioning experiments (2025) demonstrated this directly: applying evolutionary pressure to artificial neural networks (using a genetic algorithm to optimise a network's *potential* to learn rather than directly optimising performance) produced significantly faster knowledge acquisition. Evolution, it appears, tunes neural systems to enable rapid learning by shaping their inductive landscape. Precisely the advantage that biological brains arrive with and neural networks must rediscover through their own compressed evolutionary process.

## The Counterargument

There is a notable counterposition, articulated most directly in response to Zador's work. The argument runs: biological brains benefit from evolutionary priors, but this is because biological learning algorithms are — by the standards of modern optimisation — *weak*. Biological learning is constrained by locality (synapses can only use information available at their own junction), limited lifespans, and the absence of anything like backpropagation's ability to propagate error signals across an entire network. Evolution compensates for these suboptimal learning rules by pre-building intricate circuit structures.

Backpropagation, by contrast, is an enormously powerful optimiser. It is not constrained by locality or lifespan. Given enough data, it can discover any structure that evolution could provide, and it does so without the risk of baking in the *wrong* priors. From this perspective, the architecture discovery tax is real but acceptable: the cost of tabula rasa learning is high in data, but the result is a more flexible system unconstrained by potentially maladaptive innate assumptions.

The scaling laws community implicitly endorses this view. The empirical finding that model performance improves predictably with more data, compute, and parameters suggests that brute-force discovery of computational structure is not just feasible but efficient at scale. Why engineer in priors when gradient descent will find the right answer?

This counterargument deserves serious weight. It correctly identifies that biological evolution and artificial training exist in very different optimisation regimes, and that lessons from one do not transfer straightforwardly to the other. But it also, perhaps inadvertently, concedes the central observation. The disagreement is about whether conducting compressed evolution from scratch is *practical at scale*, not about whether that is what training is doing. And critically, even if brute-force evolutionary search is acceptable during pretraining — where compute budgets are enormous and the process only needs to run once — the question of whether it remains acceptable during reinforcement learning, where budgets are smaller, signals are sparser, and the cost of blind exploration is proportionally higher, is a different question entirely.

## The Tripartite Gap

Framing the sample efficiency gap as purely an architecture discovery problem is itself incomplete. The missing evolutionary priors span at least three levels.

The first is *computational architecture*, Zador's primary focus. Biological brains arrive with modular, specialised circuits for specific problem types. Neural networks start with a uniform architecture and must discover internal specialisation through training. The transformer architecture encodes some useful biases (attention is inherently relational, the residual stream enables superposition), but these are far less rich than what evolution provides.

The second is *learning algorithms*. Biological learning uses highly non-uniform plasticity rules: Hebbian learning, spike-timing-dependent plasticity, neuromodulatory gating, sleep-phase consolidation. These are specialised learning rules for specialised circuits, themselves products of evolutionary selection. Backpropagation is a single uniform rule applied everywhere: powerful in aggregate but inefficient at the level of individual circuit formation, because it is conducting architecture search with a tool that was not designed for architecture search.

The third is *input richness*. A child learning "cup" receives multimodal sensory grounding, motor interaction, social reinforcement, and temporal continuity from a single encounter. An LLM seeing the token "cup" in a sentence gets one thin slice of distributional co-occurrence. The information density per example is radically different. This is not strictly an evolutionary prior, but it is a consequence of the embodied substrate that evolution produced, and it dramatically inflates the number of examples an LLM needs to reach an equivalent internal representation.

Disentangling the relative contributions of these three factors is an open empirical question. Current LLMs are deficient at all three, and improving any one of them could reduce sample requirements. Crucially, different factors may dominate at different stages of training — architecture discovery weighs heaviest during pretraining, while the limitations of the training process itself become the binding constraint during reinforcement learning, where the architecture already exists but the training loop provides no memory, no reflection, and no structured credit assignment.

## Where Evolution Meets Its Limits

Here is the observation that connects this essay to the Memory Scaffolding theory: **the training-as-evolution framing reveals not just what the architecture discovery tax costs, but where the evolutionary paradigm becomes the wrong tool for the job.**

By the time a foundation model enters post-training, the evolutionary search for computational architecture is largely complete. The model has already developed induction heads, attention patterns, internal feature hierarchies, and the synergistic cores that interpretability research has identified. The computational motifs exist. This is the equivalent of evolution having produced a sophisticated brain — the organ is built, the circuits are wired. What remains is not architectural search but behavioural refinement: developing and tuning the knowledge, habits, and strategies that flow through the existing architecture.

Supervised fine-tuning handles this transition reasonably well. Its learning signal is dense (every token has a clear target), and the reference outputs implicitly demonstrate effective approaches. SFT is closer to instruction than evolution — the teacher shows the pattern, the student reproduces it. The epistemic relationship between system and training signal shifts: the model is no longer being blindly shaped by selection pressure, it is being shown what to do.

Reinforcement learning does not make this shift. It remains fully within the evolutionary paradigm. Its learning signal is sparse (a single scalar per output). Its exploration is blind (no record of what has been tried before). Its episodes are memoryless (each begins from zero). The model stumbles into good outputs and gets reinforced. It stumbles into bad outputs and gets penalised. It cannot ask *why* something worked or *what* made something fail. It is shaped by differential reward, exactly as an organism is shaped by differential survival.

The architecture exists — the evolutionary search for computational structure has been paid for during pretraining. But the *training process itself* is still operating in the evolutionary mode: external selection, no internal understanding, no memory across episodes. The model has a sophisticated brain but is being trained like a sea slug — stimulus, response, reinforcement.

This is the specific mismatch that the Memory Scaffolding theory targets.

## From Evolution to Education

Evolution is powerful but epistemically impoverished. The organism being evolved never understands the selection pressure shaping it. It cannot examine its own history, identify what worked, generalise principles, or carry understanding forward. Each generation (or in RL's case, each episode) starts without access to what came before. The accumulated effect of past selection is encoded in structure (genes, weights) but is not available as *knowledge* to the system being shaped.

Biological organisms eventually broke out of this constraint. At some point in evolutionary history, nervous systems became sophisticated enough that organisms could learn from their own experience within a single lifetime — not just be shaped by selection across generations. Memory, reflection, and the ability to model cause and effect allowed organisms to transition from pure evolutionary subjects to active learners. This was arguably the most consequential phase transition in the history of intelligence: the point where the system being shaped began to participate in its own shaping.

Memory Scaffolding proposes an analogous transition for reinforcement learning.

In standard RL, the model is a passive subject of the training process. It generates outputs, receives rewards, and has its weights adjusted. It does not understand why it was rewarded or penalised. It cannot examine its own history. Each episode is a fresh trial with no explicit continuity. The training paradigm is evolutionary, and the model's role is to be evolved.

Memory Scaffolding breaks this relationship. After batches of training episodes, the model enters reflection sessions where it reviews its own completed transcripts: what it tried, what worked, what failed, and why. It distils these observations into generalised principles stored in a structured scratchpad. On subsequent episodes, relevant entries are provided as context, and the model's exploration becomes informed rather than blind.

The critical shift is not the scratchpad itself — it is the *epistemic transition* it enables. The model is no longer merely being shaped by external reward signals. It is examining its own performance, identifying causal patterns, and generating understanding that feeds back into future behaviour. It has moved from being a subject of evolution to a participant in its own education.

The RL loop still runs. Gradient descent still adjusts weights. The external selection pressure is still present. But the *material* that selection operates on has changed. Instead of blind exploration producing random variations for reward to filter, the model's outputs are informed by its own accumulated understanding. Gradient descent gets better inputs to work with — not because the reward signal has improved, but because the model is producing higher-quality outputs based on reflective analysis.

This is the difference between natural selection (which discovers solutions through brute-force differential reproduction) and education (which transmits understanding so that the learner can direct their own improvement). Evolution stumbles into solutions. Education understands them.

The analogy to biological history is direct. Evolution built sophisticated brains through millions of years of blind selection. Those brains eventually became capable of learning — of examining experience, extracting principles, and carrying understanding forward within a single lifetime. Memory Scaffolding proposes an equivalent transition within the training process: the model's architecture was built by training-as-evolution, and now the model itself can participate in refining what runs through that architecture, because it possesses the reflective capacity to do so.

The scratchpad is temporary — it is removed once the model's weights have absorbed its content, aided by the mnemonic bridging techniques described in the companion essay. The scaffolding is retired once its purpose is served. But the shift it enables, from evolution to education, is permanent: the weight updates during the scaffolded phase encode not just "what worked" but the model's own understanding of *why* it worked, producing cleaner representations than blind selection alone could achieve.

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

Zador and the nativist camp argue for building more innate structure into networks: better architectures, genomic bottleneck initialisation, meta-learned priors. This addresses the architecture discovery tax directly by pre-installing the results of evolutionary search rather than rerunning it. It is the equivalent of giving a newborn a pre-built brain rather than asking it to evolve one. The risk is installing the *wrong* priors, but the principle is sound.

The scaling camp argues that more data and compute will overcome the tax through brute force. This has been empirically validated at enormous scale, but it is essentially an argument that compressed evolution is cheap enough at scale to be the preferred strategy. It is silent on what to do during RL, where the data budget is smaller, the learning signal is sparser, and the cost of blind evolutionary search is proportionally higher.

The world model camp, most vocally Yann LeCun, would reject the premise of improving RL altogether. LeCun has argued that RL is inherently too sample-inefficient to be worth fixing, and that the correct response is to replace trial-and-error exploration with planning over learned world models. In evolutionary terms, this amounts to giving the organism the ability to simulate outcomes internally, bypassing the need for actual trial-and-error interaction with the environment. This is the strongest structural objection to Memory Scaffolding: not that the diagnosis is wrong, but that the evolutionary paradigm should be abandoned entirely rather than reformed.

The pragmatic response is twofold. First, LeCun's world model architectures (JEPA and its successors) remain research-stage, while RL is how frontier models are actually trained today and will be for the foreseeable future; scaffolding is an intervention for the paradigm that exists, not the one that might replace it. Second, even world models will need to be trained, and if any part of that training involves reward-based learning (which LeCun himself concedes may sometimes be necessary), the evolutionary dynamics resurface, and the case for introducing reflective learning applies.

Memory Scaffolding occupies a different niche entirely. It does not try to reduce the architecture discovery tax at pretraining — it accepts that evolutionary cost as already paid. It does not compete with SFT, which has its own dense supervision mechanism that already transcends the evolutionary paradigm. Instead, it addresses the specific problem that RL remains stuck in the evolutionary mode long after the architecture has been discovered. It proposes that the transition from evolution to education — which biological organisms achieved through the development of memory and reflection — can be recapitulated within the RL training loop by leveraging the reflective capacities the model already possesses.

The model has already been evolved. Memory Scaffolding proposes that it is time to start teaching it.

## Open Questions

**How much architecture discovery happens during RL?** The claim that circuit formation is "largely complete" after pretraining is an assumption, not an established fact. Some RL tasks may require novel computational motifs that did not emerge during pretraining. If so, scaffolded RL may remain in "evolutionary mode" for those specific circuits while operating in "educational mode" for everything else.

**Does the evolutionary bottleneck scale with model size?** Larger models may pay a proportionally smaller architecture discovery tax at pretraining, completing their evolutionary search more efficiently. If so, the residual problem — that RL remains stuck in evolutionary mode — becomes an increasingly dominant bottleneck at scale, which would make the transition to education *more* valuable, not less, as models grow.

**Can the tax be measured directly?** A clean experiment would compare pretraining convergence curves between randomly initialised models and models initialised via Zador's genomic bottleneck, then apply identical RL (with and without scaffolding) to both. This would disentangle the contribution of pretraining evolutionary search from RL-phase educational intervention.

**Where does SFT sit on the spectrum?** This essay frames SFT as closer to instruction than evolution, but the boundary is not sharp. SFT with noisy or contradictory training data may still operate partly in evolutionary mode. The evolution-to-education spectrum may be more of a continuum than a clean binary, with different training regimes occupying different positions depending on the density and quality of their supervision signal.

**Is the transition reversible?** If Memory Scaffolding successfully shifts RL from evolutionary to educational mode, does removing the scaffolding (as the theory proposes) risk regressing back to evolutionary dynamics? The mnemonic bridging phase is designed to prevent this, but whether internalised reflective habits can fully substitute for the external scaffolding is an empirical question. The biological parallel suggests they can — humans do not forget how to learn — but the analogy has limits.

---

*Evolution built the brain. Education fills it. Current AI training does both at once, paying a heavy tax for the first and using the wrong paradigm for the second. The architecture discovery tax names the first cost. Memory Scaffolding addresses the second. Together, they suggest that the next step for AI training is the one biological intelligence took millions of years ago: the transition from being shaped by selection to learning from experience.*