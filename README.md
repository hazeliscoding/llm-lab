# llm-lab 🧪

My hands-on lab for building a GPT-style language model from scratch, one typed line at a time.

## Purpose

This repo is my companion while I study
[*Build a Large Language Model (From Scratch)*](https://www.manning.com/books/build-a-large-language-model-from-scratch)
by Sebastian Raschka.

- The [official repository](https://github.com/rasbt/LLMs-from-scratch) is my reference and answer key.
- This repository holds **my own typed implementations, notes and experiments**.
- I deliberately don't copy finished implementations. Typing the code, getting it wrong, and fixing it is how the material actually sticks.

So expect bugs, detours, and code that's worse than the book's. That's the point.

## Learning philosophy

For every section, I follow the same loop:

```text
Read
→ Implement it myself
→ Run it
→ Break it
→ Debug it
→ Compare with the official implementation
→ Write down what I learned
```

A few house rules:

- **Type it, don't paste it.** Copy-paste skips the part where learning happens.
- **Try first, peek later.** The official code is for comparing, not for starting.
- **Notes in my own words.** If I can't explain it simply, I don't understand it yet.

## Environment

- [Python](https://www.python.org/) 3.13
- [uv](https://docs.astral.sh/uv/) for the Python version, virtual environment and dependencies
- [PyTorch](https://pytorch.org/)
- [Jupyter](https://jupyter.org/)
- [tiktoken](https://github.com/openai/tiktoken)
- [matplotlib](https://matplotlib.org/)

Set up and launch:

```powershell
uv sync
uv run jupyter lab
```

`uv sync` downloads Python 3.13 if needed, creates `.venv/`, and installs everything from `uv.lock`.

Later chapters need a few extra packages (for example `tqdm`, `pandas` and `tensorflow`). I'll add them with `uv add <package>` when I get there instead of installing everything up front.

On Windows, the PyTorch wheel from PyPI is CPU-only. That's enough for most of the book.

## Progress

Chapter 1 is conceptual (no code), so the hands-on part starts at Chapter 2.

- [ ] Chapter 2 — Working with Text Data
- [ ] Chapter 3 — Coding Attention Mechanisms
- [ ] Chapter 4 — Implementing a GPT Model from Scratch to Generate Text
- [ ] Chapter 5 — Pretraining on Unlabeled Data
- [ ] Chapter 6 — Fine-Tuning for Classification
- [ ] Chapter 7 — Fine-Tuning to Follow Instructions

## Repository structure

```text
llm-lab/
├── chapter-02/ … chapter-07/   my code and notebooks for each chapter, plus a notes README
├── experiments/                 code that deliberately deviates from the book
├── notes/                       cross-chapter notes: concepts, open questions, glossary
├── pyproject.toml               project metadata and dependencies (uv)
└── uv.lock                      pinned dependency versions
```

- **`chapter-XX/`**: where I implement each chapter myself. Each `README.md` is a template I fill in as I go: what I built, what clicked, what confused me.
- **`experiments/`**: my playground. Changed hyperparameters, visualizations, debugging snippets, side-by-side comparisons. See [experiments/README.md](experiments/README.md).
- **`notes/`**: things that span chapters.
  - [concepts.md](notes/concepts.md): concepts I want to remember, in my own words
  - [questions.md](notes/questions.md): what I don't understand yet, and the answers once I find them
  - [glossary.md](notes/glossary.md): terms I keep running into

## Credit

All the material, and all the credit for it, belongs to Sebastian Raschka and
[*Build a Large Language Model (From Scratch)*](https://www.manning.com/books/build-a-large-language-model-from-scratch).
If this repo makes you curious, get the book and type it out yourself.
