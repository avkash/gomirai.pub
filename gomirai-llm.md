# GOmirai LLM — the local AI model

GOmirai's intelligence does not come from a cloud API. It comes from a language
model that GOmirai downloads onto your computer and runs there. This document
describes what that model is, how big it is, what it does, and how it fits into
the application.

---

## At a glance

| | Language model | Embedding model |
|---|---|---|
| **Name** | GOmirai LLM | GOmirai Embed |
| **Current version** | 2.1 | 1.0 |
| **Tag** | `gomirai-llm:2.1` | `gomirai-embed:1.0` |
| **Download size** | **≈ 4.7 GB** (5,048,350,848 bytes) | **≈ 139 MB** (146,146,432 bytes) |
| **Format** | GGUF, 8-bit quantised (Q8_0) | GGUF |
| **Runs on** | Your machine, via Ollama | Your machine, via Ollama |
| **Job** | Reads, judges and summarises your mail | Turns text into vectors for semantic search |

Both are served from 650 AI Lab's distribution bucket over a CDN, verified by
SHA-256 after download.

### What it is built on

GOmirai LLM 2.x is built from **Google's Gemma 4 E2B instruction-tuned model**,
packaged at 8-bit precision for desktop use. Gemma is Google's open family of
on-device models; "E2B" means roughly two billion effective parameters — small
enough to run on a laptop, capable enough to read and reason about email.

*Use of Gemma is subject to Google's Gemma Terms of Use.*

---

## Why a small local model instead of a large cloud one

A frontier cloud model would be more capable in the abstract. It would also mean
uploading your complete private correspondence to a third party. That trade is
the entire reason GOmirai exists, so it is not on the table.

The choice that makes a local model viable is **scope**. GOmirai does not ask the
model to be a general assistant. It asks it to do a small number of narrow,
well-defined jobs — classify this message, does it need a reply, summarise this
thread, extract the action items — each with a tight prompt and a required output
shape. A 2B-parameter model does that reliably. It would not write you a novel.

---

## What it actually does in the application

### Triage — the core job

Every incoming message is read by the model, which decides:

- **Does this need a reply?** Someone is waiting on you.
- **Does this need attention?** You should know about it, even if no reply is owed.

These are deliberately two independent judgements, surfaced as two tabs in AIBox.
A shipping notification needs attention and no reply; a direct question needs
both.

It also assigns a category, extracts action items, and notes what has already
been handled.

### Summaries

Per-message and per-thread summaries, and a daily briefing aggregated across
every connected account.

### Ask GOmirai

Ask a question in plain language and get an answer drawn from your own mail,
notes and documents. This is where the **embedding model** does its work: it
converts your content into vectors so the app can find the passages relevant to
your question, then the language model answers using them.

### Scheduling

The model reads a scheduling request in an email, checks your calendar, and
proposes times. Nothing is written to your calendar without you confirming it.

### Document and note intelligence

Files added to the Vault are summarised and made searchable; notes in the
Obsidian vault are embedded so semantic search finds them by meaning, not just
by keyword.

### Translation

Handled by a separate translation engine rather than this model.

---

## How it runs — the architecture

GOmirai does not implement model inference itself. It uses **[Ollama](https://ollama.com)**,
a widely used local model runtime, and manages its whole lifecycle for you:
starting it when the app launches, restarting it if it stops, and reporting the
server log when something fails.

```
   Your mail  ──►  GOmirai  ──►  Ollama on 127.0.0.1  ──►  GOmirai LLM
                      ▲                                     (on your disk)
                      └──────────  results  ◄───────────────────┘
```

Everything in that loop is on your machine. `127.0.0.1` is your own computer
talking to itself — the traffic never touches a network.

### Setup is one flow

**AI → LLM Setup** runs three steps with a red/green light on each:

1. **Download** — fetch the model, with live progress.
2. **Instance** — register it with Ollama.
3. **Verify** — send a test prompt and confirm a real answer comes back.

Until all three pass, the app reports **Not Ready** and AI features stay
switched off rather than failing quietly. When a newer model version is
published, the same panel offers **Update Model**.

### Processing happens in the background

Mail is analysed as it arrives, independently of what you are looking at. You
can navigate away, and the work continues. The queue is durable — it survives
quitting the app, and resumes where it left off.

AIBox analyses a rolling recent window of mail plus everything new, rather than
your entire archive, so a large mailbox does not mean an enormous first run. The
window length depends on your plan.

---

## What you need to run it

| | Minimum | Comfortable |
|---|---|---|
| **RAM** | 16 GB | 24 GB+ |
| **Free disk** | ~10 GB | 20 GB+ |
| **CPU/GPU** | Apple Silicon or Intel Mac · x64 Windows | Apple Silicon (Metal GPU acceleration) |

The model file alone is 4.7 GB, and it must be held in memory while running.
On Apple Silicon, Ollama uses the Metal GPU automatically.

**GOmirai runs without the AI.** If you do not download the model, every email
and calendar feature still works — you simply do not get AIBox. The AI is a
layer on top, not a dependency.

---

## Can I use a different model?

Yes. GOmirai's model management can install other open models — Qwen3 4B and 8B,
other Gemma builds — from the catalog in the AI panel. The email pipeline is
tuned and validated against GOmirai LLM, so that is the supported path and the
default everyone gets; other models are available for experimentation.

---

## Privacy summary

- The model file lives on **your disk**.
- Inference happens on **your CPU/GPU**, over `127.0.0.1`.
- Your email content is **never** sent to a third-party AI service, and never
  used to train any model — ours or anyone else's.
- The only network calls involved are downloading the model itself and, if you
  enable it, backing up your own data to your own cloud storage.

See [privacy-and-data.md](privacy-and-data.md) for the complete picture.
