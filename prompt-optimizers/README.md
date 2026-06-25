# Prompt Optimizers
This repository provides two optimization modules:

- Flux.1 [dev] Optimizer --> improves prompt structure and generation consistency for FLUX-based image generation models.
- Qwen-Images Optimizer --> enhances prompt clarity, reasoning structure, and output quality for Qwen LLMs.

The goal is to standardize and improve model outputs with minimal setup.
------------------------------------------------------------------------

## Features:
- Flux.1 [dev] optimizer takes into account common critical generation errors in FLUX outputs (such as issues with hands and fingers). For example, to improve quality, when the “hands” trigger is activated, it automatically adds the necessary prompt enhancements to correct and refine the result. It improves the quality of a raw prompt by preserving its original intent while enhancing its clarity and making it more interpretable for FLUX.1 [dev].

- Qwen-Images optimizer improves the interpretability of raw prompts for diffusion models. Its main feature is enhanced performance in text generation tasks. Maintains proper color balance when constructing the prompt for image generation. Automatically generates a negative prompt when necessary.

- BOTH:
  Multi-step decomposition of complex queries.
  Ability to identify subjects, objects, scenes, and landscapes. Improves requirements, performs self-analysis, and ensures adherence to the characteristics of diffusion models.
------------------------------

## How to use?
- Just put them with your prompt in ChatGPT / Gigachat / Claude / Deepseek / Gemini and others.
-------------------------------
## You can see the examples at the end of .md files.
