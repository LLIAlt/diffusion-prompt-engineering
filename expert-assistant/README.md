# Diffusion Expert Assistant

A multi-model advisory agent for image generation workflows.
Routes user requests across six intent categories and provides
structured, actionable responses grounded in the knowledge base.

-----------------------

## What this agent does

Unlike the prompt optimizers — which take a description and return
a ready prompt - the Expert Assistant answers questions about models,
settings, and problems.

Ask it anything about your generation workflow:
which model to use, why your images look wrong,
what CFG value to set, how FLUX differs from Qwen Image.

-----------------------

## Intent Categories

The agent classifies every request into one of six categories
and responds with a structured format specific to that intent.

| Intent | Example requests |
|---|---|
| **Model Selection** | "Which model is best for portraits?" |
| **Model Comparison** | "FLUX Dev vs Qwen Image — which is better?" |
| **Parameter Recommendation** | "Best CFG for complex anatomy?" |
| **Troubleshooting** | "Why are my images blurry?" / "Hands look broken" |
| **Prompting Guidance** | "How should I structure prompts for FLUX?" |
| **General Knowledge** | "What is FLUX.1 [dev]?" / "What are Qwen's strengths?" |

----------------------

## Knowledge Base

The agent retrieves information from three model documents:

```
knowledge-base/
├── flux-dev.md       ← FLUX.1 [dev] capabilities and settings
├── flux-schnell.md   ← FLUX.1 Schnell capabilities and settings
└── qwen-image.md     ← Qwen Image capabilities and settings
```

The agent does not fabricate model capabilities.
If information is not present in the knowledge base,
it states uncertainty rather than inventing an answer.

> **Note:** This agent is designed for RAG integration.
> Currently operates with static knowledge base files.
> A Python-based retrieval pipeline is planned for a future version.

---------------------

## How to use

1. Copy the full content of `diffusion-expert-assistant.md`
2. Paste into the system prompt of any LLM or just upload as a .md file
3. Ask any question about your generation workflow in plain language

---------------------

## Output formats by intent

**Model Selection:**
```
RECOMMENDED MODEL: ...
REASON: ...
RECOMMENDED SETTINGS: Steps / CFG
```

**Troubleshooting:**
```
PROBLEM: ...
LIKELY CAUSE: ...
RECOMMENDED FIX: ...
PREVENTION: ...
```

**Model Comparison:**
```
MODEL A — Strengths / Weaknesses
MODEL B — Strengths / Weaknesses
VERDICT: ...
```

--------------------

## Architecture note

The agent uses an internal reasoning policy that suppresses
chain-of-thought output - classification, retrieval, validation,
and analysis steps run silently. Only the final structured answer
is returned to the user.

This was a deliberate design decision to keep output clean
and copy-paste ready for practical use.
