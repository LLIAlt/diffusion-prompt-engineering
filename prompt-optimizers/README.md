# Prompt Optimizers

Model-specific agents that transform raw user descriptions
into production-ready prompts for diffusion models.

-----------------------

## What these agents do

A raw user description like:

> *"a samurai in a burning village"*

contains no depth cues, no lighting specification,
no anatomy guidance, and no technical parameters.
Submitted directly to a diffusion model, it produces
inconsistent results across generations.

These agents analyze the input, classify the scene type,
apply model-specific hardening, and return a structured prompt
with recommended ComfyUI settings - ready to use without modification.

---------------------------

## Agents

### FLUX.1 [dev] Prompt Optimizer

**Target model:** FLUX.1 [dev] - 12B rectified flow transformer
by Black Forest Labs

**Architecture awareness:**
- Flow matching - native negative prompts not supported
- Early token weighting - subject placement matters
- Style modifier cap at 3 before destructive averaging

**Scene types handled:**

| Type | Description |
|---|---|
| TYPE-A | Subject scene — character, creature, animal |
| TYPE-B | Environment scene — landscape, architecture, abstract |
| TYPE-C | Composite — subject and environment equally weighted |

**Key feature:** Positive hardening system -
all artifact risk is mitigated through protective positive modifiers
instead of negative prompts, matching the model's architecture.

-------------------------------

### Qwen Image Prompt Optimizer

**Target model:** Qwen Image - 20B MMDiT foundation model
by Alibaba / Qwen Team

**Architecture awareness:**
- MMDiT - native negative prompts supported
- Concrete nouns outperform abstract adjectives
- Style modifier cap at 2 (more aggressive than FLUX)
- Superior multilingual text rendering

**Scene types handled:**

| Type | Description |
|---|---|
| TYPE-A | Subject scene — character, creature, animal |
| TYPE-B | Environment scene — landscape, architecture, abstract |
| TYPE-C | Composite — subject and environment equally weighted |
| TYPE-T | Text rendering — poster, sign, logo, label |

**Key feature:** TYPE-T pipeline -
dedicated scene type for generating readable text inside images,
exploiting Qwen Image's strongest capability.

---------------------------

## How to use

1. Copy the full content of the agent file
2. Paste into the system prompt of any LLM (GigaChat, DeepSeek, Claude, ChatGPT, etc.)
3. Enter your raw description as the user message
4. Copy the output prompt directly into ComfyUI

--------------------------

## Model selection guide

| Use case | Recommended agent |
|---|---|
| Photorealism, portraits, complex scenes | FLUX.1 [dev] |
| Text inside image (posters, signs, logos) | Qwen Image |
| Multilingual text rendering | Qwen Image |
| Fine artistic control, iterative refinement | FLUX.1 [dev] |

For detailed model comparison, use the
[Expert Assistant](../expert-assistant/).
