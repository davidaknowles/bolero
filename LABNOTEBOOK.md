# Lab notebook

## 2026-07-23 — Conditioned-LoRA model note

Added `docs/main.tex` and its compiled PDF. The note documents the implementation of
Bolero as a frozen Borzoi/Flashzoi backbone with per-layer conditional LoRA, including:

- generation of low-rank factors from cell-state embeddings;
- single- and multi-dataset conditioning encoders;
- paired pseudobulk and background-signal training;
- count and delta prediction losses; and
- collapsing adapters into a fixed model for inference and attribution.

The source was checked against `BorzoiLoRA`, `module_lora_cond`, `module_embedding`, the
LoRA configuration presets, and the Borzoi training/data paths.

Follow-up clarification: the note now gives the explicit grouped-convolution LoRA
parameterization and identifies the current cell-state embeddings as 30-dimensional joint
RNA--ATAC MULTIVI latents, rather than expression PCs.

Removed the generic Conv2d equations from the note after checking the architecture: Bolero's
Borzoi backbone uses only Conv1d layers over genomic position; Conv2d support in the adapter
module is unused here.
