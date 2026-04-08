<div align="center">

![Sam — sovereign multi-node local AI cluster](./assets/hero.svg)

</div>

```text
operator   ▸ Al  ·  github.com/66sith
project    ▸ Sam — a sovereign, multi-node local AI cluster
status     ▸ online · 5 nodes · zero cloud dependence
```

---

I run **Sam** — a multi-node local AI cluster I designed and operate on private
infrastructure. Everything runs on hardware I own. No cloud inference. No telemetry
leaving the network. The cluster is built and maintained by coordinated coding agents
under my direction; I'm the architect and the operator, not the typist.

I started this because I wanted an assistant that was actually mine — that could
remember things across sessions, run my pipelines, watch my infrastructure, talk to me
out loud, and never depend on a third party staying up or staying friendly. Sam is the
result.

---

## Architecture

```text
                              ┌─────────────────────────┐
                              │   AGENT GATEWAY         │
                              │   ─ Claude · Cursor     │
                              │   ─ session handoffs    │
                              └────────────┬────────────┘
                                           │
                                  ┌────────▼────────┐
                                  │  ORCHESTRATOR   │
                                  │  ─ Nemotron-8B  │
                                  │  ─ routing      │
                                  │  ─ memory mux   │
                                  └────┬────────┬───┘
                ┌──────────────────────┘        └──────────────────────┐
                │                                                       │
       ┌────────▼────────┐  ┌─────────────────┐  ┌───────────────────┐  │
       │  INFERENCE 01   │  │  INFERENCE 02   │  │  INFERENCE 03/04  │◄─┘
       │  ─ llama.cpp    │  │  ─ llama.cpp    │  │  ─ specialised    │
       │  ─ GGUF models  │  │  ─ GGUF models  │  │    workers        │
       └────────┬────────┘  └────────┬────────┘  └─────────┬─────────┘
                │                    │                     │
                └────────────────────┴─────────────────────┘
                                     │
       ┌─────────────────────┬───────┴────────┬─────────────────────┐
       │                     │                │                     │
┌──────▼──────┐      ┌───────▼──────┐  ┌──────▼──────┐      ┌───────▼──────┐
│  COGNITIVE  │      │   NERVOUS    │  │    OPS &    │      │  VOICE I/O   │
│   MEMORY    │      │    SYSTEM    │  │   METRICS   │      │   ─ wake     │
│ ─ long-term │      │ ─ event bus  │  │ ─ Grafana   │      │   ─ TTS/STT  │
│ ─ vector    │      │ ─ heartbeats │  │ ─ audits    │      │   ─ persona  │
└─────────────┘      └──────────────┘  └─────────────┘      └──────────────┘

                           ─────────  on-prem  ─────────
```

The cluster is split across discrete responsibilities so any single node can fail
without taking the whole assistant down. The orchestrator routes requests to the
right inference node based on context, history, and load. Memory is persistent and
queryable. Voice runs on its own pipeline so the assistant can be talked to like a
person, not a chatbox.

---

## Components

| component                 | role                                                           |
| ------------------------- | -------------------------------------------------------------- |
| **sam-os**                | cluster operating system, boot orchestration, service registry |
| **sam-nervous-system**    | inter-node event bus, Nemotron-8B routing layer                |
| **sam-cognitive-memory**  | long-term episodic + semantic memory store                     |
| **sam-infrastructure**    | networking, storage, deployment, hardware management           |
| **sam-ops**               | operational documents, audits, incident reports                |
| **sam-trading**           | algorithmic trading pipeline                                   |
| **sam-income-pipeline**   | passive income — FLUX image generation → distribution          |
| **sam-voice-operations**  | wake-word, TTS/STT, multi-channel voice routing                |
| **sam-metrics**           | observability, dashboards, alerts                              |

The repos themselves are private — sovereignty includes not posting your floor plan
on the front door.

---

## Stack

```text
  inference   ▸ llama.cpp · GGUF quantization · Nemotron-8B orchestrator
  hardware    ▸ Mac Studio M3 Ultra (512 GB unified) + supporting nodes
  monitoring  ▸ Grafana stack
  voice       ▸ OpenClaw framework
  agents      ▸ Anthropic Claude · Cursor · custom session handoff layer
  language    ▸ Python · TypeScript · Shell · whatever fits the job
```

---

## Current focus

```text
  ▸ hardening the orchestrator routing layer
  ▸ collapsing tech debt across the cluster
  ▸ wiring tighter feedback loops between agents and ops
  ▸ shipping the income pipeline to steady-state
```

---

## Philosophy

```text
  sovereignty       — my hardware, my data, my keys, my rules
  legibility        — every repo explains itself to the next agent that opens it
  agent-driven      — humans architect, agents implement, both review
  no fragile glue   — if it breaks when one service goes down, it's wrong
```

---

<div align="center">

`66sith` ·  operator  ·  Sam local AI cluster

</div>
