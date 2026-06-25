# Diffusion Prompt Engineering Portfolio
### Production-grade prompt agents for modern image generation models

----------------

A curated library of prompt engineering agents built for practical use
with FLUX.1 [dev], Qwen Image, and related diffusion models.

Each agent in this library was developed through iterative real-world
testing in ComfyUI and is designed to solve specific, documented failure
modes of its target model — not to generate generic prompts.

------------------

## Library Structure

```
prompt-engineering-portfolio/
│
├── prompt-optimizers/          ← model-specific prompt agents
│   ├── flux-optimizer.md
│   └── qwen-image-optimizer.md
│
├── knowledge-base/             ← model documentation used by the assistant
│   ├── flux-dev.md
│   ├── flux-schnell.md
│   └── qwen-image.md
│
└── expert-assistant/           ← multi-model routing and advisory agent
    └── diffusion-expert-assistant.md
```

------------------

## Agents Overview

### Prompt Optimizers

Model-specific agents that transform raw user descriptions into
production-ready prompts. Each optimizer is aware of its model's
architecture, token weighting behavior, known failure modes,
and optimal generation parameters.

| Agent | Target Model | Architecture | Key Feature |
|---|---|---|---|
| flux-optimizer | FLUX.1 [dev] | Flow Matching | Positive hardening, no negative prompts |
| qwen-image-optimizer | Qwen Image | MMDiT | Native negative prompts, TYPE-T text rendering |

→ [View prompt-optimizers](./prompt-optimizers/)

-----------------------------------------------

### Expert Assistant

A multi-model advisory agent that helps users select the right model,
compare model behaviors, troubleshoot generation problems,
and improve prompting strategy.

Routes requests across six intent categories:
Model Selection · Model Comparison · Parameter Recommendation ·
Troubleshooting · Prompting Guidance · General Knowledge

→ [View expert-assistant](./expert-assistant/)

-------------------------------------------------------

### Knowledge Base

Structured model documentation used internally by the Expert Assistant
as its retrieval source. Contains capabilities, recommended settings,
known limitations, and prompting techniques for each supported model.

→ [View knowledge-base](./knowledge-base/)

-------------------------------------------------------

## How to Use

All agents are plain `.md` files - no installation required.

**Option 1 — Paste into system prompt**
Copy the agent's full content into the system prompt field
of any LLM interface (Claude, ChatGPT, etc.).
Enter your raw description as the user message.

**Option 2 — API integration**
Use the agent file content as the `system` parameter in any
Anthropic or OpenAI API call. Replace `{user_description}`
with the actual user input at runtime.

-----------------------------------

## Stack

FLUX.1 [dev] · Qwen Image · ComfyUI · RunPod

----------------------------------

## Author

**Danil Okhrimenko** · Prompt Engineer

