<div align="center">

# Shubham Kumar

### Backend · Infrastructure · Platform Engineer

**Distributed systems, reliability engineering and database internals.**<br>
Former Principal Engineer at LimeChat (YC W21): systems serving **1B+ requests a day**.

<br>

[![Email](https://img.shields.io/badge/bshubh@proton.me-6D4AFF?style=for-the-badge&logo=protonmail&logoColor=white)](mailto:bshubh@proton.me)
[![LinkedIn](https://img.shields.io/badge/LinkedIn-0A66C2?style=for-the-badge&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/shubham--sk/)
[![Website](https://img.shields.io/badge/beshubh.github.io-111111?style=for-the-badge&logo=githubpages&logoColor=white)](https://beshubh.github.io)
![Open to work](https://img.shields.io/badge/Open_to_work-2EA44F?style=for-the-badge)

<sub><i>Coding is dead, long live coding!</i></sub>

</div>

---

Hey, I'm Shubh 👋

I build the parts of a product that have to stay up at 3 a.m.: messaging pipelines, queues, databases, real-time media and the reliability layer around them. In ~5 years at **LimeChat (YC W21)** I went from **SDE-I to Principal Engineer** with three promotions. Along the way I designed the messaging backbone every product runs on and took a voice-AI product from zero to **$600K+ ARR**.

In August 2026 I took time off to go deep on **systems programming and databases**. Since then I've finished **CMU 15-445 Database Systems with 100/100 on every project** and built an **LSM-tree storage engine in Rust**. I spent years scaling Postgres, Redis and Kafka; now I've built the internals myself.

> **Looking for:** Senior Backend, Infrastructure, Platform, Distributed Systems or Database / Storage engineering roles, plus backend-leaning full-stack roles. I want hard systems problems where reliability and performance actually matter. Based in India.

<br>

<table>
  <tr>
    <td align="center" width="25%"><h2>1B+</h2>requests / day<br><sub>through systems I designed</sub></td>
    <td align="center" width="25%"><h2>100M+</h2>messages / day<br><sub>Unified Messaging System</sub></td>
    <td align="center" width="25%"><h2>$600K+</h2>ARR in &lt; 6 months<br><sub>voice product I started</sub></td>
    <td align="center" width="25%"><h2>100/100</h2>on every CMU 15-445 project<br><sub>database built in C++</sub></td>
  </tr>
</table>

---

## 🛠️ Selected work at LimeChat (YC W21)

<sub>LimeChat builds AI customer-support and sales agents for large enterprises in India.</sub>

### 📞 WhatsApp ↔ LiveKit real-time audio bridge · `Rust` `WebRTC` `LiveKit`

**Problem.** Meta opened WhatsApp Calling, and we had an AI voice agent on LiveKit. Nothing existed to connect the two: WhatsApp speaks peer-to-peer WebRTC, while LiveKit is a room-based SFU. Nobody on the team had worked with WebRTC before.

**What I did.** I reverse-engineered the media flow and built a bridge that acts as a WebRTC peer to the caller. It terminates the media, transcodes Opus to PCM, and joins the LiveKit room as a virtual participant. First I shipped a Python + aiortc prototype to validate the product. Once real traffic showed it was CPU-bound, I benchmarked Python against Rust at 50–300 concurrent calls per core and rewrote the media path in **Rust** with Tokio, reusing buffers to avoid per-frame allocations.

**Result.** It was the **first system in India** to let AI agents take WhatsApp calls, and we shipped it **before LiveKit did**. The Rust rewrite cut **CPU by 80% and memory by 50%**. Pods went from 1 GB / 2 vCPU × 4–10 replicas to ~200 MB / 0.5 vCPU × ~2. The platform around it, which I architected, reached **$600K+ ARR in under 6 months** and closed **~10 enterprise deals**.

→ [Deep dive: how we built WhatsApp voice agents](https://beshubh.github.io/?post=story-of-how-we-built-voice-agents-at-limechat)

### 📨 Unified Messaging System · `Python` `Kafka` `RabbitMQ` `PostgreSQL` `Redis`

**Problem.** Every product had its own path for sending and receiving messages on WhatsApp, Instagram, email and other channels. That meant duplicated logic and inconsistent delivery guarantees.

**What I did.** I designed one system boundary for all of them, covering delivery state, retries and **idempotent recovery under partial failure**. I then scaled it into the backbone the whole company runs on.

**Result.** It handles **100M+ messages a day** and **~1B requests a day**, and it carries revenue worth **millions of dollars a year**. Separately, I removed a multi-year CRM bottleneck so broadcast campaigns scaled from **60K to 1M messages**.

### 🛡️ Company-wide reliability: making overload a non-event · `Kafka` `RabbitMQ` `Redis` `Circuit breakers`

**Problem.** Traffic spikes repeatedly overwhelmed queues, caches and databases. A single slow dependency could cascade into a company-wide outage.

**What I did.** I led a cross-team initiative:
- **Circuit breakers** on every critical dependency, so callers fail fast instead of hammering a struggling system.
- **Tiered fallback queues**: critical messages escalate from weaker to stronger systems (RabbitMQ → Kafka → durable store) instead of being dropped.
- Migrating hot Redis queues to **Kafka**.
- Archiving cold transactional data to S3, plus resource alerting.

**Result.** **Peak-traffic downtime from queue overload went to zero.**

→ [Deep dive: improving resilience at LimeChat](https://beshubh.github.io/?post=improving-resilience-at-limechat)

### ⚡ Performance and production debugging

| What | How | Impact |
|---|---|---|
| AI chat-agent latency | Semantic caching on decision steps, removing high-fanout DB reads | **−66% peak latency** (15 s → 5 s) |
| PostgreSQL saturation | Centralized connection pooling with PgBouncer | **−60% DB CPU** (90% → 40%), 5k → 3k connections |
| Workers hanging at peak, for years | Traced it to how Celery prefetches countdown/ETA tasks and starves workers ([write-up](https://beshubh.github.io/?post=you-might-be-unaware-of-celerys-delayed-semantics)) | A multi-year incident class eliminated |
| Workflow engine (like n8n or Zapier) | Built and scaled the execution engine | Tens of millions of events, **1M+ messages a day** |

**Leadership:** I led 3 engineers to ship **3 revenue-critical systems in under 3 months**: User Segments, Workflow Builder and Unified Messaging. I also started the weekly internal tech talks and pushed backend test coverage until testing became standard practice across the company.

---

## 🗄️ Database internals: what I've been doing since August 2026

### CMU 15-445/645 Database Systems: **100/100 on every project** · `C++17`

I built the core of **BusTub**, CMU's teaching relational database, from scratch:

| Project | What I built |
|---|---|
| **Buffer pool** | ARC page replacement, an async disk scheduler, RAII page guards with read/write latching |
| **B+ tree index** | A concurrent B+ tree with latch crabbing and optimistic inserts; insert, delete, search and iterators |
| **Query execution** | Volcano-style executors: scans, DML, aggregation, nested-loop, index and **hash joins with recursive partitioning**, **external merge sort**, window functions (including `RANK`), plus optimizer rules (NLJ → hash join, seq scan → index scan) |
| **Concurrency control** | **MVCC**: timestamps and watermarks, undo logs and tuple reconstruction, transactional DML and index updates, aborts, garbage collection |

<sub>The code is private under CMU's academic-integrity policy. I'm happy to walk through it in an interview.</sub>

### [LSM-tree storage engine in Rust](https://github.com/beshubh/lsm-engine-course) · `Rust`

I finished all three weeks of [mini-lsm](https://skyzh.github.io/mini-lsm/): memtables, SSTables with block encoding and bloom filters, merge iterators, **leveled and tiered compaction**, WAL and manifest recovery, and **MVCC with serializable snapshot isolation** using optimistic conflict detection, watermarks and compaction filters. I also wrote notes on RocksDB's evolution covering write and space amplification, tombstones and rate-limited deletes.

---

## 🔬 Other systems I've built from first principles

| Project | What it is | Stack |
|---|---|---|
| [**Harvest**](https://github.com/beshubh/harvest) ⭐ | A full-text search engine with a concurrent crawler, positional inverted index, SPIMI indexing with **k-way external merge**, and phrase queries. [Write-up →](https://beshubh.github.io/?post=building-search-engine-from-scratch-using-rust) | `Rust` `Tokio` `Axum` `MongoDB` |
| [**Kafka in Rust**](https://github.com/beshubh/kafka-rust) | Kafka wire protocol and broker basics: Produce, Fetch, topic and partition metadata, KRaft log | `Rust` |
| [**Distributed systems**](https://github.com/beshubh/distsys-rust) | **Raft**, a fault-tolerant KV store, transactions, linearizability | `Rust` |
| [**Gossip Glomers**](https://github.com/beshubh/flyio-dist-challenges) | Fly.io's distributed-systems challenges: broadcast, gossip, counters | `Rust` |
| [**Bitcask KV store**](https://github.com/beshubh/kvs-rust) | A log-structured key-value store based on the Bitcask paper | `Rust` |
| [**rslox**](https://github.com/beshubh/rslox) | A tree-walk interpreter with a scanner, parser, AST, closures and runtime | `Rust` |
| [**LeetCode GitHub Sync**](https://github.com/beshubh/leetcode-gh-sync) | A Firefox extension with a Rust → WebAssembly sync planner | `Rust` `Wasm` `JS` |

---

## 🧰 Stack

| | |
|---|---|
| **Languages** | Rust · Python · Go · TypeScript · C++ |
| **Data & storage** | PostgreSQL · Redis · MongoDB · Elasticsearch · PgBouncer |
| **Messaging & streaming** | Kafka · RabbitMQ · Celery |
| **Infrastructure** | Kubernetes · Docker · AWS · GCP |
| **Real-time** | WebRTC · LiveKit · WebSockets |
| **Frameworks** | Tokio · Axum · Django · Node.js · gRPC |

---

## 🤝 How I work

- **Prototype to learn, rewrite to scale.** I ship the simplest version that proves the idea, measure it under real load, and only then reach for the heavy tools. The Python → Rust bridge followed exactly that path.
- **Find the root cause.** If an incident needs a manual restart every week, it hasn't been fixed. The Celery and PgBouncer fixes both ended problems that had been "normal" for years.
- **I learn whatever the problem needs.** I hadn't touched WebRTC before the voice bridge or C++ before CMU 15-445. Both shipped anyway.
- **High agency, low ceremony.** I like owning a problem end to end, from design doc to production to on-call. I don't do well with micro-management.

## ✍️ Writing

- [Story of how we built Voice Agents at LimeChat](https://beshubh.github.io/?post=story-of-how-we-built-voice-agents-at-limechat): WebRTC, LiveKit and why we rewrote in Rust
- [Improving resilience at LimeChat](https://beshubh.github.io/?post=improving-resilience-at-limechat): circuit breakers and fallbacks for everything
- [You might be unaware of Celery's delayed semantics](https://beshubh.github.io/?post=you-might-be-unaware-of-celerys-delayed-semantics): a bug that hid for years
- [Building a search engine from scratch using Rust](https://beshubh.github.io/?post=building-search-engine-from-scratch-using-rust)

<details>
<summary><b>📜 Career timeline</b></summary>
<br>

| | Role | |
|---|---|---|
| **Aug 2026 to now** | Systems programming and database internals, full time | CMU 15-445, mini-lsm, C++ |
| **2021 to Aug 2026** | SDE-I → **Principal Engineer**, LimeChat (YC W21) | Messaging, voice AI, reliability, performance |
| **2020 to 2021** | Backend Engineer, ClassCast | Rebuilt the course platform for 100K+ students; real-time chat on Node.js and Redis Pub/Sub |
| **2020** | Backend Intern, The Tarzan Way | Django, Elasticsearch, an AWS SNS pub/sub broker |

</details>

---

<div align="center">

**Building something hard in backend, infra or databases? Let's talk.**<br>
📫 [bshubh@proton.me](mailto:bshubh@proton.me) · 💼 [LinkedIn](https://www.linkedin.com/in/shubham--sk/) · 🌐 [beshubh.github.io](https://beshubh.github.io)

<sub>Off the keyboard, I lift heavy weights. 🏋️</sub>

</div>
