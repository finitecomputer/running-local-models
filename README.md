# Running Local Models

The official slideshow for:

**Running Local Models: From Desktop to Data Center**

## The deck

`machine.html` is the official deck ("The Expanding Machine"). It opens with a
title and speaker intro, then walks through the local inference stack in twenty-six slides, with
intermediate resource slides that point the audience at the tools for each level:

- Slide 01 — Title (Running Local Models: From Desktop to Data Center)
- Slide 02 — Speaker (bio + links)
- Slide 03 — Definitions (model · weights · parameters · quantization · tokens · inference · agent · concurrency)
- Slide 04 — One box (Ollama)
- Slide 05 — Model names
- Slide 06 — Pull it apart
- Slide 07 — Dense versus MoE
- Slide 08 — Choose your app (omlx.ai · jan.ai)
- Slide 09 — Choose your model (Hugging Face · Artificial Analysis)
- Slide 10 — Local stack
- Slide 11 — Hardware (GPU bros vs. unified memory bros)
- Slide 12 — Mac mini
- Slide 13 — Single GPU (RTX 3090)
- Slide 14 — Runtimes (llama.cpp · MLX-LM · vLLM · SGLang)
- Slide 15 — Agent contract
- Slide 16 — OpenAI-compatible endpoints (responses · chat · models · embeddings · images · audio)
- Slide 17 — Agents (Hermes Agent · OpenCode · Pi · goose)
- Slide 18 — Tool adapter
- Slide 19 — Shared service
- Slide 20 — DGX Spark
- Slide 21 — Our DGX Spark cluster
- Slide 22 — Dynamo (NVIDIA Dynamo)
- Slide 23 — Swap slots (static API + Dynamo, swappable agent · tool adapter · runtime · model · OS/drivers · hardware)
- Slide 24 — Multi-GPU server
- Slide 25 — Complete machine
- Slide 26 — Thank you + talk resources (including inference.finite.computer/v1)

## Open the deck

Live deck: https://finitecomputer.github.io/running-local-models/

Open `machine.html` directly in a modern browser, or serve this directory
locally:

```sh
python3 -m http.server 4173
```

Then visit `http://127.0.0.1:4173/machine.html`.

## Controls

- Right arrow, Down arrow, Page Down, Space, or click: next stage
- Left arrow, Up arrow, or Page Up: previous stage
- Number keys 1 through 9 and 0 jump to stages 1 through 10
- Home returns to the title slide
- End jumps to the thank-you and resources slide
- Clicking a link on a resource stage opens it without advancing

The deck uses inline CSS and JavaScript, system fonts, and local hardware images
under `assets/hardware/`. It has no external runtime dependencies.

## Image sources

- Mac mini — Apple Newsroom: https://www.apple.com/newsroom/2024/10/apples-new-mac-mini-is-more-mighty-more-mini-and-built-for-apple-intelligence/

## Visual system

The deck uses a warm paper background, near-black type, and a single orange
signal color. Stages use large typography, generous margins, short copy, and
flat compositions — designed to move from a first local model to a shared
inference cluster without turning the presentation into a dashboard.
