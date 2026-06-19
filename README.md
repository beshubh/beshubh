# Shubham Kumar

Working on distributed systems and performance.

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
