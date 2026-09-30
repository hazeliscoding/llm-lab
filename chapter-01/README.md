# Chapter 1 — Understanding Large Language Models

> 📖 Official code to compare against, after I've tried it myself:  
> [LLMs-from-scratch by Sebastian Raschka](https://github.com/rasbt/LLMs-from-scratch)

## 🧠 What this chapter is about

This chapter is basically the **"okay but what even *is* an LLM?"** chapter.

No coding yet. Just building the mental model before I start assembling the cursed math machine myself.

The big picture:

- LLMs are neural networks trained to predict the next token.
- Somehow, doing that at a ridiculous scale produces models that can write, summarize, translate, answer questions, generate code, and occasionally lie to me with incredible confidence.
- Modern LLMs are mostly based on the **Transformer** architecture.
- The same basic architecture can be adapted to a bunch of different tasks instead of building a completely separate model for everything.
- Training happens in stages rather than "feed it the internet and suddenly ChatGPT pops out."

The chapter also gives a nice overview of the road ahead:

```text
raw text
   ↓
tokenization
   ↓
embeddings
   ↓
attention
   ↓
transformer blocks
   ↓
GPT-style model
   ↓
pretraining
   ↓
fine-tuning
   ↓
tiny language creature acquired
```

Which makes the rest of the book feel a lot less mysterious.

## ✅ What I implemented

Nothing!

And for once that is intentional. 😌

Chapter 1 is conceptual, so the goal here was just to understand the map before wandering into the forest.

- [x] Understand the general idea behind an LLM
- [x] Understand why Transformers matter
- [x] Understand the difference between pretraining and fine-tuning
- [x] Get a rough idea of what I'm eventually going to build
- [x] Resist the urge to skip directly to "make GPT go brrrr"

## 💡 Concepts I understand now

### Language models are prediction machines

At the core, a language model is predicting what token is likely to come next.

That sounds almost suspiciously simple considering what modern models can do.

Something like:

```text
"The cat sat on the"
```

might give high probability to:

```text
mat
floor
chair
bed
```

and very low probability to:

```text
postgresql
chainsaw
taxes
```

The interesting part is that getting extremely good at next-token prediction requires learning a huge amount of structure about language and the world represented by that language.

So the model never gets a magical `understand_everything()` function.

It learns useful internal representations because they help it predict better.

### Tokens are not the same thing as words

LLMs don't directly read text the way I do.

Text gets converted into **tokens**, which are eventually represented as numbers.

A token might be:

- an entire word
- part of a word
- punctuation
- whitespace-ish stuff
- some weird fragment that makes perfect sense to the tokenizer and absolutely nobody else

So the rough pipeline starts more like:

```text
text
 ↓
tokens
 ↓
token IDs
 ↓
vectors
 ↓
model
```

Chapter 2 is apparently where I get to actually poke at this.

### Transformers are the important bit

The architecture underlying GPT-style models is the **Transformer**.

The major idea I'll be digging into later is **attention**.

Attention lets the model decide which earlier parts of the input are important while processing the current token.

Very rough brain version:

```text
"The animal didn't cross the street because it was tired."
                                          ↑
                                    what is "it"?
```

The model needs some way to connect related information across the sequence.

That's where attention enters the chat.

### Pretraining vs fine-tuning

This distinction finally feels clean in my head.

**Pretraining**

```text
giant pile of text
      ↓
learn general language patterns
      ↓
base model
```

The model learns by predicting tokens across enormous amounts of unlabeled text.

Then:

**Fine-tuning**

```text
base model
   ↓
smaller specialized dataset
   ↓
model becomes better at a specific behavior/task
```

So you don't normally train an entire huge model from zero every time you want it to do something new.

You start from something that already learned language patterns and specialize it.

### Building an LLM is a pipeline

This was probably the biggest useful takeaway.

"Build an LLM" sounds like one gigantic impossible task.

But the book breaks it down into smaller pieces:

```text
1. Process text
2. Turn text into tokens
3. Turn tokens into vectors
4. Implement attention
5. Build Transformer blocks
6. Assemble GPT
7. Train it
8. Fine-tune it
```

Suddenly:

> "build GPT"

becomes:

> "build a bunch of smaller understandable systems that eventually stack into GPT"

Much less terrifying.

## 😵 Things that confused me

A few things are still very much in the **"I recognize these words but do not yet possess them spiritually"** category:

- How exactly attention learns which tokens should care about which other tokens.
- What embeddings actually look like once they're being trained.
- How next-token prediction alone leads to surprisingly general behavior.
- Where knowledge is actually "stored" inside a neural network.
- How much behavior comes from the architecture versus the training data versus fine-tuning.
- Why Transformers scale so absurdly well compared to older language-model architectures.

I'm deliberately not trying to solve all of those yet.

Future chapters exist for a reason.

## 🔬 Experiments I tried

None yet.

Chapter 1 is the lore episode.

The science crimes begin in Chapter 2.

## 📝 Notes to future me

Don't rush through the early chapters just because modern frameworks can already do all of this for me.

The entire point of doing this book is to get below:

```python
model.generate(...)
```

and understand what is actually happening underneath it.

Also:

**do not turn this into a race to finish the book.**

If attention takes me three evenings to properly understand, then attention takes me three evenings.

The goal isn't:

> "I completed an LLM book."

The goal is:

> "When somebody talks about tokenization, embeddings, attention, Transformer blocks, logits, loss, or fine-tuning, I actually know what machinery they're talking about."

And ideally, by the end:

```text
LLMs before this book:
✨ mysterious oracle ✨

LLMs after this book:
large matrix multiplication creature
that I have personally assembled
```

Onward to Chapter 2. 🫡