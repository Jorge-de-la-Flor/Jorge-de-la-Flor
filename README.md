<div align="center">

English | [Español](README.es.md)

# Jorge de la Flor (aka FrostCore)

![Python](https://img.shields.io/badge/Python-Systems%20%26%20Data-3776AB?style=flat-square&logo=python&logoColor=white)
![Rust](https://img.shields.io/badge/Rust-Systems%20Programming-CE422B?style=flat-square&logo=rust&logoColor=white)
![C/C++](https://img.shields.io/badge/C%2FC%2B%2B-Embedded%20Development-00599C?style=flat-square&logo=cplusplus&logoColor=white)

![Embedded Systems](https://img.shields.io/badge/Embedded-Real--Time%20Systems-0078D4?style=flat-square)
![Distributed Systems](https://img.shields.io/badge/Distributed%20Systems-Edge%20Computing-FF6F00?style=flat-square)
![Cloud](https://img.shields.io/badge/Cloud-Azure%20%28prod%29%20%7C%20AWS-0089D6?style=flat-square)
![Language Engineering](https://img.shields.io/badge/Language%20Engineering-Transpilers%20%26%20Codegen-8A2BE2?style=flat-square)

**Software & Cyber-Physical Systems Developer**

**Python & Rust · Low-level systems, distributed systems, embedded computing, cloud infrastructure**

I build systems that are verified against the real thing — firmware that compiles for real MCU toolchains, transpiled code that runs under `rustc` and `javac`, runtimes tested against live production — from a microcontroller to a control plane on Azure.

</div>

---

## 🧠 About me

I design and ship low-level and distributed systems: embedded computing, cloud infrastructure, and language/codegen tooling, mostly in Python and Rust. My work centers on one question — does this actually hold up in production? — so every generator, transpiler, or runtime I publish is checked against real toolchains and real deployments, not just unit tests on strings.

Since 2023 I've built and maintained the software a property-management business runs on — from the first line of code to stable production.

I'm also a technical instructor, open-source mentor, and speaker at tech community events (Microsoft Build 2026 Community Event, CSWeek 2026, BoyaConf 2026).

Background in International Business, which helps me translate business needs into systems that ship.

---

## 🚀 Featured Projects

### [sysgud](https://github.com/Jorge-de-la-Flor/sysgud) — Human-Approved AI Ops Agent in Rust
`Rust · SQLite · REST/OpenAPI · Telegram Bot API · Anthropic API`

A local process-diagnostics agent: an LLM turns logs into proposed actions, but `KILL` and `EXECUTE` only run after approval by an allow-listed user, via REST API or Telegram. Decisions are persisted to disk before acting and never re-executed after a restart; commands never pass through a shell built from model text; secrets are redacted before storage and before the LLM. Five-crate workspace with dependency boundaries checked in CI, shipped as a hardened container (read-only filesystem, all capabilities dropped). Built at a hackathon, where I led the team on design, infrastructure and code.

### Apider — Multi-Tenant Automation Runtime · [PyPI](https://pypi.org/project/apider/)
`Python · Azure Functions · PyPI · MCP · Paddle`

A serverless runtime exposing Email, Telegram, WhatsApp, Discord, Slack, Google Sheets, HTTP, Webhooks, and CloudScheduler through a clean Python SDK, plus an AI module (agentic tool-use, structured extraction, stateless RAG) that reuses the MCP tool catalog. Published on PyPI and validated by a 61-check end-to-end suite run against a live production deployment — with per-tenant HMAC key derivation, ContextVar isolation, and process-level sandboxing.

### OMNI-PY — Universal Language Transpiler
`Python (ast) · Rust (PyO3) · Java · Go · JavaScript · Rust`

Full 16/16 source-to-target coverage across Java, Go, JavaScript, and Rust, using Python as a universal AST pivot. The Rust emitter is ownership-aware (exact `.clone()`/`.to_string()`, `Option<T>`, `div_euclid`/`rem_euclid` for Python semantics) — the borrow checker ends up being the pipeline's strictest reviewer. Every output is verified by actually compiling and running it with `rustc` and `javac`, backed by eight rustc-style lints and a dual-engine safety analyzer.

### Pyperantio — Multi-Toolchain Firmware Generator
`Python · Rust · embedded-hal · 5 MCU toolchains`

A single typed Python API (`IOConfig`) describes hardware once and generates native firmware for five different toolchains — no more full HAL rewrites when porting between MCU families. The hardware model is harvested from industry silicon sources (1,503 STM32 MCUs, 70 AVR, 11 ESP32) rather than hand-written tables. Design-time validation rejects electrically invalid pin/peripheral configurations before emitting code, with rustc-style diagnostics localized into the user's language. Verified by generated Rust compiling under `thumbv6m-none-eabi` and a 401-case test suite. Talk at BoyaConf 2026 with a live multi-target demo.

### FrostCloud — Control Plane in Rust
`Rust · axum · SeaORM · PostgreSQL/SQLite`

An all-Rust Cargo workspace providing accounts, identity, service catalog, and per-account activations as a control plane kept out of the request path. Architectural boundaries are enforced at the crate level — the identity logic knows nothing about axum or SeaORM. Tokens are 256-bit CSPRNG, stored only as SHA-256 hashes, with a test verifying the plaintext token is never a store key.

### Pycaudal — Pipeline Capacity Analysis
`Python · stdlib-only · CLI · ADR Generator`

Turns opinion-based capacity planning into measurement: a fluent API models pipelines as stages with capacity and latency, locates the bottleneck, prescribes the minimal change to hit a target rate, and emits a shareable Architecture Decision Report. 77 tests, zero dependencies.

### Distributed Sensing Platform — Cyber-Physical System · [video demo](https://www.youtube.com/watch?v=wTfh7YRz6LQ)
`ESP32 · Raspberry Pi · Kalman Filter · MQTT · SQLite · SSE`

A three-node cyber-physical system: discrete-time Kalman filtering on the MCU, an FSM-controlled multi-sensor pipeline (PIR + ultrasonic), UART → MQTT → edge distribution, SQLite persistence, a REST API, and a live dashboard over Server-Sent Events.

> OMNI-PY, Pyperantio, FrostCloud and Apider's backend are closed-source while they become products. Happy to walk through any of them live on a screen share.

---

## 🔬 Robotics & Systems Labs

Repositories exploring the core engineering principles behind robotics and cyber-physical systems — sensing, estimation, control, and distributed coordination under real-world constraints.

* **sensor-uncertainty-lab** — Probabilistic models of noisy sensor measurements
* **bayesian-sensor-fusion** — Kalman filters, particle filters, and multi-sensor fusion for state estimation
* **robot-perception-lab** — Probabilistic perception: occupancy grids, localization
* **control-systems-lab** — PID controllers and system dynamics
* **embedded-state-machine-systems** — FSM architectures for embedded robotics
* **edge-device-coordination** — Coordination patterns for distributed embedded nodes

---

## 🛠️ Tech stack

| Area | Primary use |
|---|---|
| 🐍 Python | Automation, backend APIs, language engineering (AST, codegen), data pipelines |
| 🦀 Rust | Systems, embedded, `embedded-hal`, safe low-level tooling, web services (axum) |
| ⚙️ C/C++ | Arduino, ESP-IDF, STM32 (bare-metal / HAL), proprietary SDK integration |
| 🔌 Embedded & IoT | ESP32, STM32, Arduino, RP2040; PlatformIO, ESP-IDF, STM32Cube; UART, I2C, SPI, MQTT |
| ☁️ Cloud | Azure Functions (production), core AWS services (EC2, Lambda, S3, IAM), serverless multi-tenant design, containers (Podman/Docker) |
| 🗄️ Data & storage | PostgreSQL, SQLite, SeaORM, SQLAlchemy |
| 🤖 AI Agent Systems | MCP server design, agentic tool-use, human-in-the-loop approval, JSON-RPC 2.0 |

---

## 🎤 Talks & Writing

- *"Building a Multi-Tenant Python Runtime on Azure Functions"* — Microsoft Build 2026 Community Event, Azure User Group Latam (Lima, June 2026)
- *"Isolation and Trust Boundaries in Production: Building Fail-Safe Systems"* — CSWeek 2026 (Lima, August 2026)
- *"De Python a Bare-Metal: Repensando la Abstracción en Sistemas Embebidos"* — BoyaConf 2026 (Tunja, Colombia, November 2026) · upcoming
- Author of *The Agnostic Engineer: Architecture Beyond Infrastructure* (complete manuscript, unpublished) — on designing systems that survive changes in infrastructure, language, and provider

---

## 📫 Where to find me

- 📧 **Email**: [frostcore@jafa.dev](mailto:frostcore@jafa.dev)
- 💼 [LinkedIn](https://linkedin.com/in/jorge-de-la-flor)
- 🌐 [jafa.dev](https://jafa.dev)
- 💡 Open to full-time remote roles in systems software, Rust, embedded and infrastructure
- 🤝 Happy to collaborate on embedded systems, hardware–software integration and developer tooling



<!--
**Jorge-de-la-Flor/Jorge-de-la-Flor** is a ✨ _special_ ✨ repository because its `README.md` (this file) appears on your GitHub profile.

Here are some ideas to get you started:

- 🔭 I’m currently working on ...
- 🌱 I’m currently learning ...
- 👯 I’m looking to collaborate on ...
- 🤔 I’m looking for help with ...
- 💬 Ask me about ...
- 📫 How to reach me: ...
- 😄 Pronouns: ...
- ⚡ Fun fact: ...
-->
