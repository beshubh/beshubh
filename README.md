# Shubham Kumar

### Software Engineer | Distributed Systems | Performance Engineering | Rust

I build high-throughput systems, remove performance bottlenecks, and turn hard
infrastructure problems into measurable business outcomes.

At [LimeChat AI](https://www.limechat.ai/), I grew from SDE I to Principal
Software Engineer through three promotions. My work has contributed to **$1.6M
in additional annual revenue**, eliminated peak-traffic downtime from systems
handling **~1 billion requests per day**, and reduced CPU usage by as much as
**80%** in latency-sensitive production workloads.

[![Email](https://img.shields.io/badge/Email-bshubh%40proton.me-6D4AFF?style=flat-square&logo=protonmail&logoColor=white)](mailto:bshubh@proton.me)
[![Writing](https://img.shields.io/badge/Writing-zerocpy.substack.com-FF6719?style=flat-square&logo=substack&logoColor=white)](https://zerocpy.substack.com/)
[![GitHub](https://img.shields.io/badge/GitHub-beshubh-181717?style=flat-square&logo=github)](https://github.com/beshubh)

## Production impact

- **Generated revenue:** Led the engineering of a unified messaging service and
  an AI Voice Agents platform that contributed to **$1.6M in additional annual
  revenue**.
- **Rebuilt a critical real-time path in Rust:** Developed a low-latency audio
  bridge between WhatsApp and LiveKit that reduced **CPU usage by 80%** and
  **memory consumption by 50%** compared with the previous Python service.
- **Engineered for billion-request scale:** Eliminated peak-traffic downtime
  across three high-volume projects handling **~1B daily requests** by replacing
  Redis queues with Kafka and adding circuit breakers around queues, databases,
  and caches.
- **Cut user-facing latency by 66%:** Reduced chat-agent peak latency from
  **15 seconds to 5 seconds** through semantic caching and the removal of read
  query fanout.
- **Removed a major PostgreSQL bottleneck:** Introduced centralized connection
  pooling with PgBouncer, reduced application contention from **5,000 to fewer
  than 3,000 connections**, and lowered database CPU usage by **60%**.
- **Made revenue attributable:** Architected a TypeScript link-shortening and
  tracking service that processes **1M+ unique links per day** and attributes
  **50% of annual broadcast revenue**.
- **Delivered through leadership:** Led a three-engineer team that shipped three
  revenue-critical systems in under three months. I also raised backend test
  coverage above **80%** and established stronger testing and code-review
  practices.

Earlier in my career, I designed and implemented the complete backend for a
course-hosting platform used by **100K+ students** across India.

## Systems projects

I build foundational systems to understand their algorithms, data structures,
protocols, and failure modes from first principles.

### [Harvest: full-text search engine](https://github.com/beshubh/harvest)

A full-text search engine built in Rust. Harvest combines a concurrent web
crawler, a composable text-analysis pipeline, and a positional inverted index.
It uses memory-bounded **SPIMI indexing**, durable index blocks, and a **k-way
merge** to index datasets that cannot fit in memory. It also supports
incremental indexing and phrase queries.

`Rust` `Tokio` `Axum` `MongoDB` `Inverted Indexes` `External-Memory Algorithms`

### [Kafka implementation in Rust](https://github.com/beshubh/codecrafters-kafka-rust)

A Kafka-compatible broker implementation that works at the binary protocol
level. It implements request routing, Kafka wire encoding and decoding,
KRaft metadata parsing, log storage, and APIs for producing, fetching,
describing topic partitions, and negotiating API versions.

`Rust` `Kafka Protocol` `KRaft` `Binary Encoding` `Storage`

### [rslox: Lox interpreter](https://github.com/beshubh/rslox)

A tree-walk interpreter written in Rust to understand language implementation
end to end. It includes lexical scanning, parsing, abstract syntax trees,
environments, functions, callable values, and runtime evaluation.

`Rust` `Interpreters` `Parsing` `ASTs` `Language Runtimes`

### [LeetCode GitHub Sync](https://github.com/beshubh/leetcode-gh-sync)

A Firefox extension that detects accepted LeetCode submissions and commits them
directly to a configured GitHub repository. The browser integration is written
in JavaScript. Deterministic sync planning is written in Rust and compiled to
WebAssembly.

`Firefox WebExtensions` `Rust` `WebAssembly` `JavaScript` `GitHub API`

### More systems work

- [kvs-rust](https://github.com/beshubh/kvs-rust): A key-value database based
  on the Bitcask storage model.
- [rust-redis](https://github.com/beshubh/rust-redis): A Redis-compatible server
  built to study event loops and the RESP wire protocol.
- [distsys-rust](https://github.com/beshubh/distsys-rust): Implementations of
  Raft consensus, a fault-tolerant key-value service, Percolator-style
  transactions, RPC infrastructure, and linearizability checking.

## Tools I reach for

`Rust` `TypeScript` `Node.js` `Go` `Python` `Kafka` `PostgreSQL` `RabbitMQ`
`Redis` `Kubernetes` `Docker` `gRPC` `REST`

## Let's talk

I am interested in Senior and Staff engineering opportunities involving
performance-critical systems, distributed infrastructure, developer platforms,
databases, search, or technically demanding product engineering.

Contact me at **[bshubh@proton.me](mailto:bshubh@proton.me)**.
