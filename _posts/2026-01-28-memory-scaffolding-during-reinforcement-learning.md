---
layout: post
title: "Memory Scaffolding During Reinforcement Learning"
subtitle: "A theory"
date: 2026-01-28
excerpt_text: "Standard RLHF is memoryless across episodes. Humans scaffold their learning with notes, mnemonics, and deliberate review. Current RL training has no equivalent. What if we gave the model a notebook?"
---

## The Problem

Standard RLHF is memoryless across episodes. When a model makes a mistake in episode N and encounters a structurally similar problem thousands of steps later, it has no explicit record of what it learned — only whatever signal propagated through weight updates, which may or may not generalise. Humans scaffold their learning with notes, mnemonics, and deliberate review. Current RL training has no equivalent.

## The Proposal: Reflection-Driven Scratchpad

The core mechanism is a persistent, structured scratchpad populated not during training itself, but during dedicated reflection sessions that review completed training episodes. The model trains normally, then periodically pauses to study what it did.

### Phase 1: Train Normally

The model runs through several training episodes on a given topic, generating outputs and receiving feedback (reward signals, corrections). No notes are taken during these episodes — the model operates exactly as it would in standard RLHF. The training transcripts are retained for later review.

### Phase 2: Structured Self-Reflection

After a batch of training episodes, the system enters a reflection session. The completed training transcripts for a specific topic are provided back to the model (or a reflection agent), which is prompted to:

- Identify what approaches worked and why
- Identify what failed and extract the underlying reason
- Spot recurring patterns across multiple episodes
- Propose concise, generalisable learnings
- Refine or consolidate any existing scratchpad entries in light of new evidence

This is the only phase where scratchpad entries are generated. The distinction matters: reflection produces higher-quality, more generalisable notes than real-time annotation would, because the model has access to multiple episodes simultaneously and can identify cross-episode patterns that aren't visible in the moment.

### Phase 3: Scratchpad Integration

The distilled learnings from reflection are recorded concisely into the scratchpad, organised hierarchically by topic (safety, code patterns, reasoning heuristics, domain knowledge, etc.). On subsequent training episodes, relevant scratchpad entries are provided as context.

The model's exploration is now informed rather than blind. It still generates outputs and receives feedback — the RL loop is intact — but gradient descent gets better material to work with because the model is guided toward higher-quality outputs by its own prior reflections.

### Phase 4: Internalisation via Mnemonic Bridging

This phase addresses the dependency risk — the concern that the model learns to lean on the scratchpad rather than internalising patterns into its weights.

Rather than abruptly removing the scratchpad, the system transitions through an intermediate stage designed to help the model activate its own internalised circuits once the full scaffolding is gone. The key mechanism is that the model is trained to reproduce scratchpad-derived patterns within its own reasoning trace, using two self-elicitation techniques:

- **Paraphrasing**: The model learns to restate the relevant learning in its own words within its chain-of-thought before applying it. This forces active reconstruction from the model's own weights rather than passive retrieval from context, strengthening the association between the reasoning pattern and the model's internal representations.
- **Mnemonic labelling**: The model learns to invoke a short label or technique name in its reasoning trace (e.g., "I should apply the boundary-check heuristic here") as a self-directed activation cue. The label serves as a compressed signal that helps the model locate and fire the neural circuits that formed during scratchpad-assisted training.

Critically, these are not external prompts or injected context — they are reasoning habits the model itself produces. Because they are part of the model's own chain-of-thought, they persist naturally across the training-to-deployment boundary. The model that learned to say "apply the boundary-check heuristic" in its reasoning during training will continue to say it at inference time, providing a permanent lightweight bridge to the patterns that were internalised during scratchpad-assisted learning.

This creates a three-stage fade-out for the scratchpad itself, while the self-elicitation techniques endure:

1. **Full scratchpad** → model references detailed external guidance and begins learning to paraphrase and label patterns in its reasoning trace
2. **Scratchpad removed** → model activates internalised patterns via self-generated mnemonics and paraphrasing in its chain-of-thought
3. **Mature reasoning** → over time, the model may compress or drop explicit mnemonic labels as the underlying circuits become reliably activated through normal reasoning flow

The hypothesis is not that mnemonic bridging *tests* whether internalisation occurred, but that it *facilitates access* to whatever was internalised. The compressed self-generated cues help the model reach the right circuits. If the circuits did not form adequately during scratchpad-assisted training, the triggers will not compensate — and that will be visible in performance metrics. But their purpose is activation, not diagnosis.

### Phase 5: Ongoing Reflection Cycles

The process is iterative. As training continues:

- New reflection sessions review recent episodes and generate fresh learnings
- Existing entries are refined, consolidated, or promoted toward scratchpad removal
- The model is progressively trained to rely on its own reasoning-trace techniques rather than external context
- The scratchpad stays focused on the model's current learning edge

Human oversight during reflection improves quality — researchers can flag incorrect generalisations, guide what gets retained, and validate proposed entries before they enter the scratchpad.

## Why This Is Distinct

| Approach | What it stores | When it operates | Purpose |
|---|---|---|---|
| **Memory Scaffolding** | Distilled, reflection-generated learnings | During RL training | Accelerate weight internalisation |
| Memory-augmented RL (MemRL, Mem-α) | Episodic experience | Post-training / inference | Runtime adaptation |
| Experience replay | Raw past experiences | During training | Sample efficiency |
| Curriculum learning | (Controls input order) | During training | Structured difficulty progression |

The key differentiator is that notes are products of deliberate reflection on training episodes, not real-time recordings or raw replays. Study notes, not lecture recordings. And the mnemonic bridging phase trains reasoning habits that outlive the scaffolding itself.

## Theoretical Foundation

LLMs originally acquired intelligence by absorbing patterns from explicit human-generated text into weights. Memory scaffolding recapitulates this at the fine-tuning stage: explicit text (the scratchpad) scaffolds implicit learning (weight updates), then is retired once patterns are internalised.

The mnemonic bridging phase adds a further parallel to human learning: students move from detailed notes → summary cues → unaided recall. In this framework, the "summary cues" are not provided externally but generated by the model in its own reasoning — analogous to a student who has learned to silently name a technique before applying it, a self-directed retrieval practice that strengthens and maintains access to learned patterns.

## Practical Precedent

This theory was informed by building a deployed memory system for an AI coding assistant:

- Curated learnings stored in structured markdown, provided as session context
- Periodic reflection cycles (every 12 hours) review recent sessions and update memory
- Observed effects: mistakes stop repeating, reflection beats real-time notes, curation beats raw logs, compounding returns over time

The deployed system demonstrates the mechanism works at inference time. The theory asks whether the same mechanism — reflection-generated, curated, structured knowledge — can accelerate the training process itself, and whether mnemonic bridging can provide a durable path from external scaffolding to self-sufficient reasoning.

## Open Questions

- **Effectiveness of self-elicited mnemonics.** Does a model that learns to invoke a mnemonic label in its reasoning trace actually activate the intended circuits, or does it become a superficial verbal habit with no causal role in the output? Ablation studies comparing performance with and without reasoning-trace cues would help clarify.
- **Mnemonic persistence and drift.** Do self-elicited cues remain stable and useful over long training horizons, or do they drift in meaning as the model's weights continue to evolve? The cue "apply the boundary-check heuristic" only helps if the circuits it originally pointed to are still intact.
- **Reflection quality at scale.** Can the reflection process be automated effectively, or does it require heavy human oversight to avoid compounding bad generalisations?
- **Optimal scratchpad sizing and retrieval.** Too large pollutes context; too small misses patterns. Hierarchical organisation and topic-based retrieval help, but optimal parameters are empirical.
- **Compatibility with existing pipelines.** Integration with PPO/DPO, reward models, and other RLHF infrastructure adds engineering complexity.
- **What transfers well through text?** Reasoning heuristics, safety rules, and structural conventions should scaffold well. Subtle tonal calibration or holistic judgment may not — those may need standard gradient descent without shortcuts.
- **Interaction with chain-of-thought training.** Models already trained with extended thinking may have existing reasoning-trace habits. How mnemonic bridging interacts with — or could be integrated into — existing chain-of-thought training regimes is an open design question.
