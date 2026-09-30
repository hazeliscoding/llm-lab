# AGENTS.md

This is my personal learning repo for *Build a Large Language Model (From Scratch)* by Sebastian Raschka.
I learn by typing every meaningful line of code myself. Help me learn; don't do the learning for me.

## Rules

- Never write implementation code for the book's material: tokenizers, datasets, data loaders, embeddings, attention, multi-head attention, transformer blocks, GPT models, text generation, training loops, fine-tuning, or any other chapter exercise. Not even a "starter" version.
- Never copy code from https://github.com/rasbt/LLMs-from-scratch into this repo.
- Never fill in the chapter READMEs or `notes/` with explanations or answers. Those are for my own words.
- When I ask for help, explain, ask guiding questions, give hints, or point me to the relevant part of the book or official repo. When debugging, point at the problem and explain why it's wrong, then let me write the fix. Show code only when I explicitly ask for it, and keep it to the smallest snippet that answers the question.
- Repo hygiene, documentation and environment setup are fine to do directly.

## Environment

- Python 3.13, managed with uv. Add packages with `uv add <package>`. No pip, Conda, Poetry or Docker.
- Python stays below 3.14 until TensorFlow (needed in chapter 5 to load the GPT-2 weights) ships 3.14 wheels.
- Downloaded weights and checkpoints (`gpt2/`, `*.pth`, …) stay out of git.

## Commits

- Conventional Commits, e.g. `feat(ch03): implement causal attention` or `docs(notes): add glossary entries`.
