<h1 align="center">
  <a href="https://wave-rf.com/?utm_source=github&amp;utm_medium=referral&amp;utm_campaign=org-profile&amp;utm_content=header-logo">
    <picture>
      <source media="(prefers-color-scheme: dark)" srcset="https://wave-rf.com/images/CombinedWhiteLarge.svg">
      <img src="https://wave-rf.com/images/CombinedBlackLarge.svg" alt="Wave RF" height="72">
    </picture>
  </a>
</h1>

<p align="center">
  <strong>Connectivity and real-time data infrastructure.</strong>
</p>

<p align="center">
  We build both ends of the hard part: resilient multi-modal connectivity that gets data off remote devices,<br>
  and the open-source data layer that makes it queryable the moment it lands.
</p>

<p align="center">
  <a href="https://wave-rf.com/?utm_source=github&amp;utm_medium=referral&amp;utm_campaign=org-profile&amp;utm_content=header"><strong>🌐 wave-rf.com</strong></a> ·
  <a href="https://wave-rf.com/about?utm_source=github&amp;utm_medium=referral&amp;utm_campaign=org-profile&amp;utm_content=header-about"><strong>About us</strong></a>
</p>

Wave RF started at the University of Michigan and was incorporated in 2024 to solve one problem: getting telemetry off devices in places where networks fail. Building that stack surfaced a second one. Storing and querying that data live, at volume, was just as hard, so we built the data layer we wanted and open-sourced it. Today that is two lines of infrastructure under one roof:

- **Data infrastructure** *(live today)*: [**WaveHouse**](https://github.com/Wave-RF/WaveHouse), the open-source real-time API gateway for ClickHouse®, and [**WaveHouse Cloud**](https://wavehouse.cloud/?utm_source=github&utm_medium=referral&utm_campaign=org-profile&utm_content=intro), the managed service built on it.
- **Connectivity** *(in development)*: hardware, firmware, and routing that move data across LoRa®, Wi-Fi, satellite, and cellular, failing over between links so a packet always has a path home. [Learn more →](https://wave-rf.com/connectivity?utm_source=github&utm_medium=referral&utm_campaign=org-profile&utm_content=intro)

We build in the open: WaveHouse, chtypes, and most of the smaller tools we needed along the way are public below.

---

<h2 align="center">
  <a href="https://github.com/Wave-RF/WaveHouse">
    <picture>
      <source media="(prefers-color-scheme: dark)" srcset="https://raw.githubusercontent.com/Wave-RF/WaveHouse/main/docs/public/branding/lockup-dark.svg">
      <img src="https://raw.githubusercontent.com/Wave-RF/WaveHouse/main/docs/public/branding/lockup-light.svg" alt="WaveHouse" height="56">
    </picture>
  </a>
</h2>

<p align="center">
  <strong>ClickHouse® is a great database with a subpar API. WaveHouse fixes that.</strong>
</p>

<p align="center">
  <a href="https://github.com/Wave-RF/WaveHouse/releases"><img alt="Release" src="https://img.shields.io/github/v/release/Wave-RF/WaveHouse?filter=v*&amp;label=release&amp;color=%2306B0BF"></a>
  <a href="https://github.com/Wave-RF/WaveHouse/blob/main/LICENSE"><img alt="License: Apache 2.0" src="https://img.shields.io/badge/License-Apache_2.0-%23086D77"></a>
  <a href="https://github.com/Wave-RF/WaveHouse"><img alt="GitHub stars" src="https://img.shields.io/github/stars/Wave-RF/WaveHouse?style=flat&amp;logo=github&amp;color=%2306B0BF"></a>
</p>

Pointing a frontend straight at ClickHouse means one-row inserts that trigger `Too many parts`, no backpressure or edge validation, no real-time push, and no row or column security. The usual fix is a custom API, a Kafka queue, a batch consumer, a cache tier, and an auth service. **WaveHouse is that whole stack as one binary**, and its only external dependency is ClickHouse. Think *Supabase for ClickHouse*, or an *open-source Tinybird* that pushes data to the frontend in real time.

- **Ingest:** a durable write-ahead log (embedded NATS JetStream) returns `200 OK` instantly and batch-flushes in the background. Rows are schema-validated against ClickHouse, with optional idempotent dedup and a dead-letter queue for rows ClickHouse rejects.
- **Query:** a result cache (in-process, or Redis shared across instances) with `singleflight` coalescing, a type-safe query AST, and Tinybird-style named pipes (parameterized SQL endpoints).
- **Real-time:** native SSE push, broadcast *before* the ClickHouse flush, with gap-fill for late or reconnecting clients.
- **Security:** Hasura-style per-table, per-role column and row policies with JWT claim templating, all hot-reloadable.
- **Client:** [`@wavehouse/sdk`](https://www.npmjs.com/package/@wavehouse/sdk), a TypeScript client with a query builder, live queries, streaming, and schema codegen.

WaveHouse is in **alpha**: it runs in production, but APIs and configuration can still change before 1.0.

<p align="center">
  <a href="https://wavehouse.dev/?utm_source=github&amp;utm_medium=referral&amp;utm_campaign=org-profile&amp;utm_content=wavehouse-docs"><strong>📖 Docs</strong></a> ·
  <a href="https://wavehouse.dev/getting-started?utm_source=github&amp;utm_medium=referral&amp;utm_campaign=org-profile&amp;utm_content=wavehouse-quickstart"><strong>🚀 Quick start</strong></a> ·
  <a href="https://wavehouse.dev/why-wavehouse?utm_source=github&amp;utm_medium=referral&amp;utm_campaign=org-profile&amp;utm_content=wavehouse-why"><strong>🧠 Why WaveHouse</strong></a> ·
  <a href="https://github.com/Wave-RF/WaveHouse"><strong>⭐ Source</strong></a> ·
  <a href="https://github.com/Wave-RF/WaveHouse/discussions"><strong>💬 Discussions</strong></a>
</p>

> [!TIP]
> **See it running:** [**stats.wavehouse.dev**](https://stats.wavehouse.dev/?utm_source=github&utm_medium=referral&utm_campaign=org-profile&utm_content=wavehouse-stats) is a live dashboard of the WaveHouse repo's own GitHub activity. Every number, chart, and event on it is served by WaveHouse through `@wavehouse/sdk` in the browser, with no backend of its own.

> [!NOTE]
> **Rather not run it yourself?** [**WaveHouse Cloud**](https://wavehouse.cloud/?utm_source=github&utm_medium=referral&utm_campaign=org-profile&utm_content=cloud-cta) is managed WaveHouse + ClickHouse with zero ops: stream events in and publish secure, cached REST and SSE APIs without operating anything in between. **[Get started on WaveHouse Cloud →](https://wavehouse.cloud/?utm_source=github&utm_medium=referral&utm_campaign=org-profile&utm_content=cloud-cta-button)**

---

## 🧬 chtypes

**[ClickHouse's own type system, as a library you can call.](https://github.com/Wave-RF/chtypes)** Validate, coerce, and preview rows *before* they reach a server, with every answer coming from ClickHouse's real C++ rather than a model of it.

ClickHouse will accept `256` into a `UInt8`, store `0`, and never mention it. chtypes compiles ClickHouse's own C++ for each release into a native library behind a small, frozen C ABI. For any row, schema, and ClickHouse version, it tells you whether the row is **accepted, rejected, or poisoned**, the exact value that would be stored, and every silent change along the way.

| Language | Install | Package |
| --- | --- | --- |
| Go | `go get github.com/wave-rf/chtypes/go` | [![Go](https://img.shields.io/badge/Go-pkg.go.dev-%2306B0BF?logo=go&logoColor=white)](https://pkg.go.dev/github.com/wave-rf/chtypes/go) |
| Python | `uv add chtypes` | [![PyPI](https://img.shields.io/pypi/v/chtypes?label=PyPI&color=%2306B0BF&logo=pypi&logoColor=white)](https://pypi.org/project/chtypes/) |
| TypeScript | `pnpm add @wavehouse/chtypes` | [![npm](https://img.shields.io/npm/v/%40wavehouse%2Fchtypes?label=npm&color=%2306B0BF&logo=npm&logoColor=white)](https://www.npmjs.com/package/@wavehouse/chtypes) |
| Rust | `cargo add chtypes` | [![crates.io](https://img.shields.io/crates/v/chtypes?label=crates.io&color=%2306B0BF&logo=rust&logoColor=white)](https://crates.io/crates/chtypes) |

<p align="center">
  <a href="https://github.com/Wave-RF/chtypes/blob/main/docs/quickstart.md"><strong>🚀 Quickstart</strong></a> ·
  <a href="https://github.com/Wave-RF/chtypes/tree/main/docs"><strong>📖 Docs</strong></a> ·
  <a href="https://github.com/Wave-RF/chtypes/tree/main/examples"><strong>🧪 Examples</strong></a> ·
  <a href="https://github.com/Wave-RF/chtypes"><strong>⭐ Source</strong></a>
</p>

---

## 🧰 Also open source

Smaller tools we built for our own sites and CI, and shared along the way.

**For [Astro](https://astro.build/) and [Starlight](https://starlight.astro.build/) sites**

| Project | What it does |
| --- | --- |
| [**starlight-glossary**](https://github.com/Wave-RF/starlight-glossary) | Interactive glossary with hover tooltips for Starlight docs |
| [**starlight-llm-tools**](https://github.com/Wave-RF/starlight-llm-tools) | Per-page `.md` twins, `llms.txt`, and Copy-Markdown / Open-with-AI buttons |
| [**astro-themed-mermaid**](https://github.com/Wave-RF/astro-themed-mermaid) | Build-time, theme-aware Mermaid diagrams for Astro / Starlight |
| [**astro-trademarks**](https://github.com/Wave-RF/astro-trademarks) | Marks the first mention of each trademark on a page with ® or ™, and renders that page's trademark notices |

**For [Cloudflare Workers](https://workers.cloudflare.com/)**

| Project | What it does |
| --- | --- |
| [**cloudflare-md-router**](https://github.com/Wave-RF/cloudflare-md-router) | Worker that serves Markdown twins to LLM crawlers and HTML to everyone else |
| [**cloudflare-preview**](https://github.com/Wave-RF/cloudflare-preview) | GitHub Actions for Worker preview deploys when the build has to run in CI: per-PR preview URLs, a sticky PR comment, and GitHub Deployments |

---

<p align="center">
  🌐 <a href="https://wave-rf.com/?utm_source=github&amp;utm_medium=referral&amp;utm_campaign=org-profile&amp;utm_content=footer">wave-rf.com</a> &nbsp;·&nbsp;
  📡 <a href="https://wavehouse.dev/?utm_source=github&amp;utm_medium=referral&amp;utm_campaign=org-profile&amp;utm_content=footer">wavehouse.dev</a> &nbsp;·&nbsp;
  ☁️ <a href="https://wavehouse.cloud/?utm_source=github&amp;utm_medium=referral&amp;utm_campaign=org-profile&amp;utm_content=footer">wavehouse.cloud</a> &nbsp;·&nbsp;
  📊 <a href="https://stats.wavehouse.dev/?utm_source=github&amp;utm_medium=referral&amp;utm_campaign=org-profile&amp;utm_content=footer">stats.wavehouse.dev</a>
</p>

<p align="center">
  <a href="https://linkedin.com/company/WaveRF/">LinkedIn</a> &nbsp;·&nbsp; <a href="https://x.com/waveRFcorp">X</a>
</p>

<p align="center">
  <sub>ClickHouse® is a registered trademark of ClickHouse, Inc. LoRa® is a registered trademark of Semtech Corporation or its affiliates. Wi-Fi® is a registered trademark of Wi-Fi Alliance.</sub>
</p>
