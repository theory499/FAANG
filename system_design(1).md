# The Complete System Design Handbook

*A zero-to-expert reference for software engineers, architects, and anyone who has to build, scale, or reason about complex systems.*

---

## How to Read This Document

This document is structured as both a learning path and a reference manual. If you are starting from zero, read it linearly: every part assumes the vocabulary and mental models established in the parts before it. If you already have foundations, treat the table of contents as a map and jump in.

The document is organized into ten parts:

1. **Foundations** — the physics, math, and theory that underlie everything else.
2. **Building Blocks** — the individual components (load balancers, caches, databases, queues, etc.) that distributed systems are built from.
3. **Architectural Patterns** — the higher-order patterns that compose components into systems.
4. **Reliability** — making systems that don't fall over.
5. **Security** — making systems that don't get owned.
6. **Cloud & Infrastructure** — how this all runs in modern cloud environments.
7. **Data Engineering** — the analytical/data-platform side of system design.
8. **ML Systems** — system design for machine learning workloads.
9. **Hyperscale Case Studies** — how Google, Facebook, Instagram, YouTube, Netflix, Uber, Twitter, WhatsApp, TikTok, Stripe, Dropbox, and others actually work.
10. **Methodology** — how to approach a system design problem, especially in interviews and in real architectural reviews.

Throughout, the goal is to give you not just what each component is, but **when to use it, what its failure modes are, how to reason about its trade-offs, and how it actually behaves in production at scale.**

---

## Table of Contents

### Part 1 — Foundations
1. What System Design Is (and Isn't)
2. The Hardware Realities: Latency Numbers Every Engineer Should Know
3. Networking Fundamentals (OSI, TCP/IP, HTTP, DNS, TLS)
4. Performance: Latency, Throughput, Tail Latency
5. Scalability: Vertical, Horizontal, and the Limits of Both
6. Availability and Reliability
7. The CAP Theorem, PACELC, and What They Actually Mean
8. Consistency Models (Strong, Eventual, Causal, and Everything In Between)
9. Distributed Systems Fundamentals (Failures, Time, Consensus)

### Part 2 — Building Blocks
10. Load Balancers (L4, L7, Algorithms, GSLB)
11. Proxies, Reverse Proxies, API Gateways
12. DNS at Scale
13. Content Delivery Networks (CDNs)
14. Caching — The Definitive Treatment
15. Databases I — Relational (SQL) Deep Dive
16. Databases II — NoSQL Families (Key-Value, Document, Column, Graph)
17. Databases III — NewSQL and Distributed SQL
18. Indexing (B-trees, LSM-trees, Hash, Inverted, Geo, Vector)
19. Replication (Single-Leader, Multi-Leader, Leaderless)
20. Partitioning and Sharding
21. Transactions and Isolation Levels
22. Message Queues and Streaming Platforms
23. Search Systems and Inverted Indexes
24. Object Storage and Blob Stores
25. File Systems (Local and Distributed)
26. Time-Series, Graph, and Specialized Stores

### Part 3 — Architectural Patterns
27. Monoliths, SOA, and Microservices
28. Event-Driven Architecture
29. CQRS and Event Sourcing
30. Sagas, Choreography, Orchestration
31. Service Mesh
32. Lambda and Kappa Architectures
33. Hexagonal, Clean, and DDD Architectures
34. The Cell-Based / Shuffle-Sharded Architecture
35. Multi-Tenancy Patterns
36. API Design (REST, GraphQL, gRPC, WebSockets, SSE)

### Part 4 — Reliability
37. Failure Modes in Distributed Systems
38. Retries, Timeouts, Backoff, Jitter
39. Circuit Breakers, Bulkheads, Hedging
40. Rate Limiting and Throttling
41. Backpressure and Flow Control
42. Idempotency and Exactly-Once Semantics
43. Disaster Recovery, Multi-Region, RPO/RTO
44. Observability (Logs, Metrics, Traces, Profiles)
45. SRE: SLI, SLO, SLA, Error Budgets
46. Chaos Engineering
47. Capacity Planning

### Part 5 — Security
48. Authentication (Sessions, JWT, OAuth 2.1, OIDC, SAML, Passkeys)
49. Authorization (RBAC, ABAC, ReBAC, PBAC, Policy-as-Code)
50. Transport Security (TLS, mTLS, Certificate Management)
51. Secrets Management (Vault, KMS, Envelope Encryption)
52. Zero Trust Architecture
53. DDoS Mitigation, WAFs, Bot Management
54. Data Security (Encryption at Rest, Tokenization, Privacy)
55. Supply Chain Security

### Part 6 — Cloud & Infrastructure
56. Cloud Service Models (IaaS, PaaS, SaaS, FaaS)
57. The Major Clouds (AWS, GCP, Azure) — Mental Models
58. Compute (VMs, Containers, Serverless, Edge)
59. Cloud Networking (VPC, Subnets, Routing, Peering, Transit)
60. Cloud Storage and Databases
61. Containers and Container Orchestration
62. Kubernetes — End to End
63. Service Mesh in Practice (Istio, Linkerd, Cilium)
64. Infrastructure as Code (Terraform, Pulumi, CDK)
65. CI/CD and GitOps
66. FinOps and Cloud Cost Management
67. Edge Computing and CDN-Compute

### Part 7 — Data Engineering
68. OLTP vs OLAP and HTAP
69. Data Warehouses, Lakes, and Lakehouses
70. ETL vs ELT
71. Change Data Capture (CDC)
72. Batch Processing (Spark, MapReduce)
73. Stream Processing (Flink, Kafka Streams, Spark Streaming)
74. Data Modeling (Star, Snowflake, Data Vault)
75. Data Quality, Lineage, Governance
76. Real-Time Analytics

### Part 8 — ML Systems
77. ML System Design Overview
78. Feature Stores
79. Training Infrastructure
80. Model Serving
81. Vector Databases and Semantic Search
82. RAG Systems
83. LLM Inference at Scale

### Part 9 — Hyperscale Case Studies
84. URL Shortener (Bit.ly, TinyURL)
85. Pastebin / Text-Sharing
86. Rate Limiter
87. Distributed Cache
88. Notification System
89. Web Crawler (Googlebot)
90. Google Search
91. YouTube
92. Instagram (Feed, Stories, Reels, DMs)
93. Facebook News Feed
94. Twitter / X
95. TikTok
96. WhatsApp / Signal / Messenger
97. Netflix
98. Spotify
99. Uber / Lyft / DoorDash
100. Airbnb / Booking
101. Stripe / Payment Systems
102. Dropbox / Google Drive
103. Google Maps
104. Amazon E-Commerce
105. Slack / Discord
106. Zoom / Google Meet
107. GitHub
108. CDN (Cloudflare, Akamai, Fastly)
109. DNS (Google 8.8.8.8, Cloudflare 1.1.1.1)
110. Ad Serving (Google Ads)

### Part 10 — Methodology
111. The System Design Interview Framework
112. Estimation and Back-of-the-Envelope Math
113. Trade-off Analysis and Decision Records
114. Common Anti-Patterns
115. How to Keep Learning

---

# Part 1 — Foundations

## 1. What System Design Is (and Isn't)

System design is the discipline of choosing, arranging, and tuning components so that a software system meets its functional and non-functional requirements within real-world constraints.

A useful working definition: **system design is the art of making informed trade-offs.** Almost no decision in a real system is "correct" in an absolute sense. You are perpetually trading consistency for availability, latency for cost, simplicity for flexibility, throughput for tail latency, time-to-market for operational maturity. The job of an architect is to make these trade-offs *deliberately*, *with eyes open*, and *with a clear understanding of which way the wind will blow if requirements change*.

What system design **is**:

- Choosing the right shape for data (relational vs. document vs. wide-column vs. graph vs. time-series, normalized vs. denormalized).
- Choosing the right communication style (synchronous request/response, asynchronous messages, streaming).
- Deciding what to keep on the hot path and what to push to the background.
- Designing for failure as a first-class concern, not an afterthought.
- Making explicit what is implicit: data lifetimes, consistency guarantees, identity, ordering, idempotency.

What system design **is not**:

- Memorizing diagrams of "how Twitter works." Real Twitter has changed its architecture many times. The diagrams are illustrative, not prescriptive.
- Picking trendy components. "We use Kafka" is not an architecture.
- A pure paper exercise. A design that ignores operability, observability, and the team's skills is a bad design even if it would work in theory.

A good architect is fluent in the building blocks (Part 2), patterns (Part 3), and operational realities (Parts 4–6), and is comfortable saying "I don't know" or "it depends" when those answers are honest.

---

## 2. The Hardware Realities: Latency Numbers Every Engineer Should Know

Before any abstraction, the physical world imposes hard limits. You should internalize these numbers; they should feel as obvious as gravity.

**Approximate latencies (orders of magnitude, modern hardware, 2025-era):**

| Operation | Time | Implication |
|---|---|---|
| L1 cache reference | ~1 ns | Effectively free. |
| Branch mispredict | ~3 ns | Hot loops care. |
| L2 cache reference | ~4 ns | Still essentially free. |
| Mutex lock/unlock (uncontended) | ~17 ns | Cheap, but adds up under contention. |
| L3 cache reference | ~10–40 ns | Cross-core sharing. |
| Main memory reference | ~80–100 ns | The boundary between "fast" and "the rest." |
| Compress 1 KB with snappy | ~2 µs | CPU work, pipelineable. |
| Send 1 KB over 1 Gbps network | ~10 µs | Network is bandwidth-limited too. |
| Read 4 KB from NVMe SSD | ~10–50 µs | Modern NVMe is shockingly fast. |
| Read 1 MB from memory | ~100 µs | Cache lines, prefetch dominate. |
| Read 4 KB from SATA SSD | ~150 µs | |
| Round trip in same datacenter | ~250–500 µs | "Local network" assumption. |
| Read 1 MB from SSD | ~1 ms | |
| Disk seek (HDD) | ~5–10 ms | Avoid wherever possible; HDDs are archival now. |
| Read 1 MB from spinning disk | ~10–20 ms | |
| Round trip same continent | ~10–40 ms | US east-to-west is ~70 ms. |
| Round trip across continents | ~80–200 ms | Speed of light is the floor. |
| Round trip via satellite | ~600+ ms (geo) / ~30 ms (LEO) | Starlink is LEO. |

**Key intuitions to derive from these numbers:**

- **A round trip is forever.** A single intra-datacenter round trip is ~5,000× slower than a memory access. A cross-continent round trip is ~1,000,000× slower. This is why batching, pipelining, and avoiding chatty protocols matter so much.
- **Memory is the new disk; SSD is the new memory; HDD is tape.** The 10,000× gap between RAM and HDD is gone; SSD closes most of it. This has reshaped what databases look like (LSM-trees over B-trees in many workloads, for example).
- **The speed of light matters.** Light in fiber covers ~200,000 km/s. New York to London is ~5,500 km, so the absolute physical floor for the round trip is ~55 ms. You will never beat physics. If you need lower latency, you must put data closer to the user (CDN, edge computing, regional replicas).
- **Compute is cheap, IO and coordination are expensive.** Most "performance problems" are actually waiting problems — waiting on the network, waiting on the disk, waiting on a lock, waiting on another service.

These numbers should also drive intuitions around **cost.** Egress bandwidth costs money. Cross-region replication costs money. A single cross-region round trip on the hot path of every request will both slow you down and bankrupt you.

---

## 3. Networking Fundamentals

Every distributed system rests on the network. You don't have to be a network engineer, but you must understand the layers and the mechanics that show up in your day.

### 3.1 The OSI Model and TCP/IP

The OSI 7-layer model is a teaching abstraction; in practice, the **TCP/IP 4-layer model** maps better onto reality:

1. **Link layer** (Ethernet, Wi-Fi) — moves frames between adjacent nodes.
2. **Internet layer** (IP, ICMP) — moves packets across networks. Best-effort, unreliable.
3. **Transport layer** (TCP, UDP, QUIC) — provides logical channels (TCP gives reliability + ordering; UDP is fire-and-forget; QUIC is TCP+TLS+multiplexing rolled into one over UDP).
4. **Application layer** (HTTP, gRPC, DNS, SMTP) — what your code mostly speaks.

### 3.2 IP, Subnets, and Routing

An **IP address** is a routable identifier. IPv4 is a 32-bit address space (~4.3 billion); we ran out, hence NAT and IPv6 (128-bit, effectively unlimited). A **subnet** is a contiguous block of IPs sharing a routing prefix, written `10.0.0.0/16` (the `/16` means the first 16 bits are the network portion).

In a cloud VPC, you carve a private CIDR block (e.g., `10.0.0.0/16`) into subnets, attach route tables, and place workloads in subnets. Public subnets have a route to an internet gateway; private subnets do not.

**NAT** (Network Address Translation) lets many private addresses share one public address by rewriting source ports. Almost every home router does this; cloud NAT gateways do it for outbound traffic from private subnets.

### 3.3 TCP — What You Actually Need to Know

TCP gives you a **reliable, ordered, bidirectional byte stream** over an unreliable IP network. It does this through:

- **Three-way handshake** (`SYN`, `SYN-ACK`, `ACK`) — establishes sequence numbers and a connection state. Costs one round trip before you send data.
- **Sequence numbers and acknowledgments** — every byte is numbered; the receiver acks the highest contiguous byte received.
- **Congestion control** — algorithms (Reno, CUBIC, BBR) that probe for available bandwidth and back off on packet loss. BBR is widely used at hyperscale (Google).
- **Flow control** — receiver-advertised window prevents overwhelming a slow consumer.
- **Slow start** — TCP starts cautiously and ramps up; this is why connection reuse (keep-alive, connection pools) matters so much.

Implications for system design:

- Establishing a TCP+TLS connection costs ~2 round trips minimum (1 for TCP, 1+ for TLS). On a 50 ms link that's 100+ ms before the first byte. **Reuse connections.** This is why HTTP/2 multiplexing and HTTP/1.1 keep-alive matter.
- TCP is stream-oriented; "messages" are an application-level concept. You must frame messages yourself (length-prefix, delimiters, etc.).
- TCP head-of-line blocking: a single lost packet stalls all logical streams sharing that connection. HTTP/2 reduced HOL blocking at the application layer but inherited it at the transport. **QUIC** (HTTP/3) eliminates it by giving each stream its own ordering domain over UDP.

### 3.4 UDP and QUIC

UDP gives you a datagram service: no connection, no reliability, no ordering, just send-and-pray. It's the right choice when you can tolerate loss (real-time video, DNS where retry is cheap, games) or when you want to build your own reliability semantics on top.

**QUIC** is Google's protocol, now an IETF standard, built on UDP. It bundles TLS 1.3 into the handshake (so 1-RTT or even 0-RTT connection setup), multiplexes streams without HOL blocking, and supports connection migration (your laptop's TCP dies when you switch from Wi-Fi to cellular; QUIC survives because connection identity is decoupled from the IP/port). HTTP/3 runs over QUIC.

### 3.5 HTTP

HTTP is a request/response protocol on top of TCP (or QUIC for HTTP/3). Versions matter:

- **HTTP/1.0** — one request per connection. Painful.
- **HTTP/1.1** — keep-alive (reuse connections), pipelining (mostly broken in practice). Browsers open ~6 parallel connections per origin.
- **HTTP/2** — single TCP connection, multiplexed streams, header compression (HPACK), server push (deprecated). Eliminates application-layer HOL blocking but not transport-layer.
- **HTTP/3** — HTTP/2 semantics over QUIC. Eliminates transport HOL blocking, faster handshakes.

Key HTTP concepts that show up everywhere in system design:

- **Methods** — `GET` (safe, idempotent, cacheable), `HEAD`, `POST` (not idempotent), `PUT` (idempotent replace), `DELETE` (idempotent), `PATCH` (partial update).
- **Status codes** — `2xx` success, `3xx` redirect, `4xx` client error, `5xx` server error. Knowing the difference between `502`, `503`, and `504` is operationally important (`502` means the gateway got a bad response, `503` means the gateway itself is overloaded, `504` means the gateway timed out waiting for the upstream).
- **Headers** — `Cache-Control`, `ETag`, `If-None-Match`, `Authorization`, `Content-Type`, `Content-Encoding`, `Accept-Encoding`. These drive caching, conditional requests, content negotiation.
- **Cookies** vs. **headers** vs. **query params** for state. Cookies are sent automatically on every request to the origin; headers and bodies are not.

### 3.6 DNS

DNS turns names into IPs. It is hierarchical, cached aggressively, and globally distributed. Resolution path:

1. Client checks its OS cache.
2. Client asks its **resolver** (often `1.1.1.1`, `8.8.8.8`, or your ISP's).
3. Resolver, if not cached, asks a **root server** (`a.root-servers.net`, etc.) → gets pointer to TLD server.
4. Resolver asks the **TLD server** (e.g., for `.com`) → gets pointer to the **authoritative** server.
5. Resolver asks the authoritative server → gets the answer, caches it for the **TTL**.

Key record types: `A` (IPv4), `AAAA` (IPv6), `CNAME` (alias), `MX` (mail), `TXT` (arbitrary, used for SPF/DKIM/verification), `NS` (delegation), `SOA` (zone metadata), `SRV` (service location).

DNS is used as a load balancer (return different `A` records to spread traffic), as a failover mechanism (health-checked records like Route 53's), and as a service discovery mechanism (Kubernetes service DNS).

**TTL** is a big deal. Low TTLs (60s) let you fail over fast but increase resolver load and add latency for resolutions. High TTLs (1h+) are cheap but mean DNS-based failover is slow.

### 3.7 TLS

TLS gives you confidentiality, integrity, and authentication on top of TCP/QUIC. The handshake is the price of admission:

- TLS 1.2: 2 RTTs.
- TLS 1.3: 1 RTT, with 0-RTT resumption for repeat visitors (carries replay risks for non-idempotent requests).

A TLS handshake involves: cipher suite negotiation, certificate exchange, key exchange (ECDHE for forward secrecy), and finished-message verification. The server's certificate is signed by a CA your client trusts, anchored in a root certificate store.

**mTLS** (mutual TLS) authenticates the *client* too via a client certificate. It's how service meshes typically authenticate service-to-service traffic.

### 3.8 Other Critical Protocols

- **WebSocket** — long-lived, bidirectional, framed protocol over a single HTTP-upgraded TCP connection. Used for chat, live updates, collaborative editing.
- **Server-Sent Events (SSE)** — server → client streaming over plain HTTP. Simpler than WebSocket; used for AI streaming responses, notifications.
- **gRPC** — RPC framework over HTTP/2 with Protocol Buffers. Strongly typed, code-generated, supports streaming. Dominant for service-to-service in modern stacks.
- **MQTT, AMQP** — pub/sub protocols for IoT and messaging.

---

## 4. Performance: Latency, Throughput, Tail Latency

Three numbers describe a system's performance:

- **Latency** — time per request.
- **Throughput** — requests per unit time.
- **Tail latency** — what the slowest X% of requests look like.

The novice mistake is to talk about "average latency." Averages lie. A system with an average of 50 ms latency might have a `p99` of 5 seconds; users feel the tail, not the mean. **You should design and measure with percentiles** — `p50`, `p90`, `p99`, `p99.9`. The higher the percentile, the more it surfaces real-world problems: GC pauses, cache misses, slow disks, retries, leader elections.

**Why tail latency dominates at scale.** Consider a request that fans out to 100 microservices in parallel and waits for all to respond. If each backend has `p99 = 1s`, the *combined* `p99` is closer to 1s seen at *any* of 100 servers — which is closer to the `p63` of a single server (because `0.99^100 ≈ 0.37`, so 63% of fan-out requests will see at least one slow backend). At hyperscale, you must aggressively reduce tail latency: hedged requests, request cancellation, isolating noisy neighbors, eliminating GC pauses (Go, Rust, off-heap), avoiding head-of-line blocking.

**Little's Law:** `L = λ × W`. The average number of in-flight requests `L` equals arrival rate `λ` × average time in system `W`. Useful for capacity planning. If you want 10,000 RPS at 100 ms latency, you need to be able to hold 1,000 concurrent in-flight requests.

**Universal Scalability Law (USL):** Throughput doesn't scale linearly with concurrency. As you add workers, contention (locks, shared state) and coherency (synchronization between workers) eventually cause throughput to *decrease*. This is why "just add more threads" stops working, and why architectures favor sharding (no shared state) over shared-memory parallelism at scale.

---

## 5. Scalability: Vertical, Horizontal, and the Limits of Both

**Vertical scaling** (scaling *up*) means making one machine bigger: more cores, more RAM, faster disk. It's simple — no code changes, no distributed-systems problems. It's also limited: a machine has a max size, and bigger machines cost super-linearly.

**Horizontal scaling** (scaling *out*) means adding more machines. It's the only path to true scale, but it forces you into the world of distributed systems: partial failures, network partitions, consistency, coordination.

The architectural prerequisite for horizontal scaling is **statelessness on the request path** plus a **scalable state layer** behind it. Web servers and API servers should be stateless (any instance can serve any request); state lives in databases, caches, and queues that have their own scaling story.

**The scalability cube** (Scale Cube, from *The Art of Scalability*) gives a useful framing:

- **X-axis:** clone — run more identical copies behind a load balancer (most common, easiest).
- **Y-axis:** functional decomposition — split by service / capability (microservices).
- **Z-axis:** data partitioning — shard by some key (user ID, geography, tenant).

Most large systems combine all three. Hyperscale systems are essentially massively Z-axis sharded plus heavily Y-decomposed.

Practical scaling tactics, in roughly increasing complexity:

1. **Optimize.** Profile first. A 10× algorithmic improvement is cheaper than 10× more hardware.
2. **Cache.** The fastest query is the one you don't run.
3. **Asynchronize.** Move non-essential work off the hot path into queues.
4. **Add read replicas.** Reads usually outnumber writes 10:1 or more.
5. **Vertical scale.** Sometimes it's just easiest.
6. **Shard / partition.** Now you're a distributed system; behave accordingly.
7. **Specialize.** Different workloads → different stores (search → Elasticsearch, analytics → ClickHouse, graph → Neo4j).
8. **Geographic distribution.** Multi-region for both latency and availability.

---

## 6. Availability and Reliability

**Availability** is the fraction of time a system is up and serving requests within its SLO. It is usually measured in "nines":

| Nines | Downtime/year | Downtime/month | Comment |
|---|---|---|---|
| 99% | 3.65 days | 7.2 hours | Hobbyist. |
| 99.9% (three nines) | 8.76 hours | 43.8 min | Many SaaS products. |
| 99.95% | 4.38 hours | 21.9 min | Common cloud SLA. |
| 99.99% (four nines) | 52.6 min | 4.4 min | Serious infrastructure. |
| 99.999% (five nines) | 5.26 min | 26.3 s | Telecom-grade. |
| 99.9999% (six nines) | 31.5 s/year | 2.6 s | Very rare; hyperscale infra components. |

Each nine is roughly 10× harder than the previous. Going from three nines to four is the pivotal step: it usually requires multi-AZ, automated failover, no single point of failure, runbooks/on-call, careful deploys, observability. Five nines requires multi-region active-active and very mature operational practice. **Match the target to actual business requirements.** Five nines for a marketing site is wasted money; three nines for a payment system is malpractice.

**Reliability** is broader: availability + correctness + durability + security. A system that's up but corrupting data is not reliable.

Key concepts:

- **MTBF / MTTR** — mean time between failures, mean time to recover. Availability ≈ MTBF / (MTBF + MTTR). You can improve availability by failing less often *or* recovering faster. At scale, recovery dominates: you cannot avoid failures, you can only minimize blast radius and shorten recovery.
- **Single point of failure (SPOF)** — any component whose failure brings the system down. Eliminating SPOFs is foundational to HA.
- **Blast radius** — when something fails, how much breaks? Cell-based architectures (Part 3) shrink blast radius deliberately.
- **Redundancy.** N+1 (one spare), N+2 (two spares), 2N (full duplicate). The right level depends on cost and failure correlation.

---

## 7. The CAP Theorem, PACELC, and What They Actually Mean

### 7.1 CAP

Brewer's CAP theorem states that in the presence of a network **P**artition, a distributed system must choose between **C**onsistency (every read returns the most recent committed write) and **A**vailability (every request gets a non-error response). You cannot have both *during a partition*.

CAP is widely misquoted. It does **not** say you can only have two of the three. It says **during a partition**, you must choose either C or A. When the network is healthy, you can have both.

**CP systems** sacrifice availability during partitions to maintain consistency. Examples: most relational databases in their default config, Spanner, etcd, ZooKeeper, HBase.

**AP systems** sacrifice consistency during partitions to remain available. Examples: Cassandra (default), DynamoDB (in some modes), Riak, classic DNS.

In practice, "consistency" in CAP is **linearizability** (the strictest form). Many systems labeled "CP" actually offer something weaker.

### 7.2 PACELC

PACELC is more useful: in case of **P**artition, choose **A** or **C**; **E**lse (no partition), choose between **L**atency and **C**onsistency.

This is the more honest framing because partitions are rare; the constant trade-off is between latency and consistency. Strong consistency requires coordination (often consensus), which costs round trips. Eventual consistency lets you serve from the nearest replica with no coordination, getting low latency at the cost of stale reads.

PACELC categorizations:

- **PA/EL** — DynamoDB, Cassandra. Always optimize for latency/availability.
- **PC/EC** — Spanner, traditional RDBMS in synchronous-replication mode. Always optimize for consistency.
- **PA/EC** — MongoDB (in some configs).
- **PC/EL** — rare in practice.

The architect's job: pick the right combination for each piece of data. **Different data has different requirements within the same system.** User profile updates can be eventually consistent; payment processing usually cannot.

---

## 8. Consistency Models

"Consistency" means a dozen different things depending on context. Understanding the spectrum is essential.

From strongest to weakest:

### 8.1 Linearizability (Strong Consistency)

Operations appear to take effect atomically at some point between when they were issued and when they returned. Once a write completes, all subsequent reads (anywhere in the system) see it. The system behaves as if there's a single, magical, instantaneous data store.

**Cost:** requires coordination (consensus). High latency, low availability under partition.

**Where:** etcd, ZooKeeper, Spanner (with TrueTime), CockroachDB, single-node databases under serializable.

### 8.2 Sequential Consistency

All operations appear in *some* total order, and each client sees its own operations in the order it issued them. Weaker than linearizability because there's no "wall clock" requirement; a write that completed yesterday might be visible after a write that completed today, as long as the client orderings are preserved.

### 8.3 Causal Consistency

Operations that are causally related (one happened-after another) are seen in that order by all observers. Concurrent operations may be seen in different orders by different observers.

This is often the sweet spot: it preserves the orderings users actually care about (your reply must come after the original message) without requiring global coordination.

**Where:** modern collaborative apps, some research databases, COPS, AntidoteDB.

### 8.4 Read-Your-Writes Consistency

A client always sees its own writes. (You post a comment, you immediately see it; other users may not for a moment.) Implementable on top of eventual consistency by routing a client's reads to the same replica it wrote to, or by tracking write timestamps.

### 8.5 Monotonic Reads

Once a client has seen a value, subsequent reads will not see older values. Prevents the "time travel" experience of seeing data appear, then disappear, then reappear.

### 8.6 Monotonic Writes

A client's writes are applied in the order it issued them. (Sounds obvious; isn't, in async/replicated systems.)

### 8.7 Eventual Consistency

If no new writes occur, all replicas eventually converge to the same value. **No bound on when.** This is the weakest useful guarantee. In practice, "eventual" usually means "milliseconds to seconds."

**Where:** DNS, S3 (historically; now strong read-after-write), most large-scale NoSQL in their loose configs, social media feeds.

### 8.8 The Practical Mix

Real systems offer **per-operation** consistency choices:

- DynamoDB: strongly consistent reads cost 2× and aren't available across regions; eventually consistent reads are default.
- Cassandra: tunable per-query consistency (ONE, QUORUM, ALL).
- Spanner: every read is linearizable, but you can pick stale reads for performance.

**Important:** consistency models constrain *what users observe*, not *what's stored*. Two users can observe different "consistent" timelines; the question is whether each user's view is coherent.

---

## 9. Distributed Systems Fundamentals

Three realities define distributed systems:

### 9.1 Partial Failure

In a single process, things either work or crash. In a distributed system, **anything can fail independently**: a node can be slow, a packet can be lost, a disk can corrupt one block out of a billion, a clock can skew, a process can be paused for 30 seconds by GC. You cannot tell, in finite time, whether a non-responsive node is *slow*, *partitioned*, or *dead*.

This single fact has enormous consequences:

- **Timeouts are guesses.** Pick too low, you cause false positives (treating slow nodes as dead, retrying unnecessarily, possibly causing cascades). Pick too high, you take forever to detect real failures.
- **Idempotency is mandatory.** If you can't tell whether a request succeeded, you'll retry, and retries must be safe.
- **Health checks lie.** A node can pass its health check and still be unable to serve real traffic.

### 9.2 Time Is Hard

There is no global clock. Every node has its own clock, drifting at different rates, occasionally jumping (NTP corrections, leap seconds, VM migrations). This breaks the intuition that "later" is well-defined.

- **Wall-clock time** (UTC) drifts and jumps; never use it to order events.
- **Monotonic time** never goes backwards within a process; use it for measuring durations.
- **Logical time** (Lamport clocks, vector clocks) tracks causal "happens-before" without wall-clock time. Vector clocks let you tell whether two events are concurrent.
- **Hybrid logical clocks (HLC)** combine wall-clock and logical time; widely used in modern distributed databases (CockroachDB, MongoDB).
- **Google's TrueTime** uses GPS and atomic clocks to provide bounded-uncertainty timestamps; this is what makes Spanner's external consistency feasible.

### 9.3 Consensus

How do multiple nodes agree on a single value (or sequence of values) when any of them can fail? This is the **consensus** problem. It is provably impossible to solve deterministically in a fully asynchronous network with even one faulty node (FLP impossibility, 1985). In practice, we solve it with timing assumptions and randomness.

Algorithms you should know:

- **Paxos** — the foundational algorithm. Famously hard to implement correctly. Multi-Paxos amortizes leader election.
- **Raft** — designed for understandability, now dominant in new systems (etcd, Consul, TiKV, CockroachDB). A leader, log replication, terms, elections.
- **Zab** — ZooKeeper's protocol; similar to Multi-Paxos.
- **PBFT, Tendermint, HotStuff** — Byzantine fault-tolerant variants; used in blockchains and systems that must survive adversarial nodes.

Consensus is the bedrock of strong consistency. Whenever you see a system with a leader, log replication, and quorum reads/writes (etcd, ZooKeeper, Kafka's controller, CockroachDB ranges, MongoDB primary), there's a consensus protocol underneath.

A consensus group typically replicates writes to a **quorum** — a majority of the members. With 3 nodes you tolerate 1 failure; with 5 you tolerate 2. Even numbers don't help (you still need a strict majority), so members come in odd numbers.

### 9.4 The Two Generals and Byzantine Generals

The **Two Generals Problem** shows that two parties cannot reliably coordinate over a lossy channel — there's always a last message whose receipt is unconfirmed. This is why exactly-once delivery is impossible without idempotent receivers; the best you can do is at-least-once + dedup.

The **Byzantine Generals Problem** generalizes to malicious participants. BFT algorithms can tolerate up to ⌊(n-1)/3⌋ malicious nodes — you need 3f+1 nodes to tolerate f Byzantine faults.

### 9.5 The Eight Fallacies of Distributed Computing

Peter Deutsch's classic list of things engineers wrongly assume:

1. The network is reliable.
2. Latency is zero.
3. Bandwidth is infinite.
4. The network is secure.
5. Topology doesn't change.
6. There is one administrator.
7. Transport cost is zero.
8. The network is homogeneous.

Every one of these is wrong, and ignoring any of them will eventually bite you in production.

---

# Part 2 — Building Blocks

This part is the deep-dive on the components from which all distributed systems are built. Treat each as a chapter you can return to.

## 10. Load Balancers

A load balancer (LB) distributes incoming requests across a pool of backend instances. It serves four purposes simultaneously: **performance** (spread load), **availability** (route around dead instances), **scalability** (add/remove backends transparently), and **abstraction** (one stable address for clients).

### 10.1 Layer 4 vs Layer 7

Load balancers operate at different layers of the network stack:

- **Layer 4 (transport-layer)** — operates on TCP/UDP. Sees IP addresses and ports, not request contents. Can do connection-level distribution but cannot route by URL, header, or cookie. Very fast, low overhead. Examples: AWS NLB, HAProxy in TCP mode, IPVS, Google Maglev.
- **Layer 7 (application-layer)** — terminates the TCP+TLS connection, parses HTTP, can route by URL path, host header, cookie, JWT claim, etc. Can do response rewriting, header manipulation, request mirroring. Slower than L4 but vastly more flexible. Examples: AWS ALB, Envoy, NGINX, HAProxy in HTTP mode, Traefik.

Most modern stacks have both: an L4 LB at the edge for raw throughput and DDoS resilience, then an L7 LB inside for smart routing.

### 10.2 Algorithms

How does the LB pick a backend?

- **Round-robin** — rotate through backends. Simple; doesn't account for backend load.
- **Weighted round-robin** — heavier weights to bigger machines.
- **Least connections** — pick the backend with fewest active connections. Good for variable request durations.
- **Least response time** — pick the backend with lowest measured latency.
- **Random** — surprisingly competitive with round-robin in practice; used in some systems for its statistical properties.
- **Power of two choices (P2C)** — pick two backends randomly, send to the less loaded. Provably near-optimal load distribution with minimal coordination. Widely used (Twitter's Finagle, Linkerd, Envoy's `LEAST_REQUEST` with `choice_count: 2`).
- **Consistent hashing** — hash the request (e.g., by user ID) and route to the corresponding backend; minimizes redistribution when backends change. Critical for session affinity, cache-friendly routing.
- **Maglev hashing** — Google's algorithm; consistent hashing with very even distribution. Used in cloud LBs (GCP, AWS NLB).

### 10.3 Session Affinity ("Sticky Sessions")

Sometimes you need the same client to land on the same backend (because the backend has in-memory state). Mechanisms:

- **Source IP hash** — route by client IP. Breaks behind NATs/proxies.
- **Cookie-based** — LB sets a cookie naming the backend. Reliable; only works for HTTP.

Stickiness is a smell. It complicates failover (if the sticky backend dies, the user loses state) and uneven load distribution. Prefer stateless backends with state in shared stores.

### 10.4 Health Checks

The LB pulls dead backends out of rotation by health-checking them. Two flavors:

- **Active** — LB pings backends periodically (HTTP, TCP, gRPC health endpoints).
- **Passive** — LB observes failed requests and ejects backends that fail too often (outlier detection).

**Health checks are hard.** Two failure modes:

1. The backend *says* it's healthy but isn't (the health endpoint passes while real requests fail because of a hot bug or a downstream dependency).
2. The backend is overwhelmed and fails health checks; LB removes it; remaining backends get more load and also fail; the system collapses.

Mitigations: differentiate "shallow" (process is alive) from "deep" (can serve real traffic) checks; cap the % of backends that can be marked unhealthy at once; expose load shedding so overloaded backends shed gracefully without failing health checks.

### 10.5 Global Server Load Balancing (GSLB)

GSLB routes traffic across geographic regions. Mechanisms:

- **DNS-based** — different DNS responses per region (Route 53 latency-based or geo-based routing). Coarse, slow to react (DNS TTL).
- **Anycast** — same IP advertised from many locations; BGP routes the user to the nearest. Used by CDNs, public DNS resolvers (1.1.1.1), and a few hyperscalers. Very fast convergence on failure (BGP reroutes).

### 10.6 Practical Patterns

A typical large web stack:

```
Internet
   ↓
  Anycast IP (e.g., Cloudflare)
   ↓
  Edge L4 LB / DDoS scrubbing
   ↓
  TLS termination
   ↓
  L7 LB / API gateway (routing, auth, rate limit)
   ↓
  Service mesh / internal LB
   ↓
  Application instances
```

---

## 11. Proxies, Reverse Proxies, API Gateways

A **proxy** sits between client and server. Variants:

- **Forward proxy** — sits in front of the client; the server doesn't know the real client. Used for corporate egress filtering, anonymization. Squid is a classic example.
- **Reverse proxy** — sits in front of the server; the client doesn't know which backend it's talking to. NGINX, Envoy, HAProxy. Provides TLS termination, caching, load balancing, request routing.
- **Sidecar proxy** — a proxy deployed alongside each service instance (typically in the same Kubernetes pod). Foundation of service meshes (Envoy as Istio/Linkerd's data plane).

### 11.1 What a Reverse Proxy Does

A modern reverse proxy is doing many jobs:

- **TLS termination** — frees backends from crypto.
- **Connection management** — keep-alive, pooling, HTTP/2 multiplexing.
- **Load balancing** — algorithms above.
- **Request/response rewriting** — headers, paths.
- **Caching** — for cacheable responses (`Cache-Control`).
- **Compression** — gzip, brotli.
- **Rate limiting** — per IP, per user, per route.
- **Routing** — by host, path, header, weight.
- **Observability** — access logs, metrics, traces.
- **Auth** — JWT validation, OAuth introspection, mTLS.
- **WAF integration** — block known attack patterns.

### 11.2 API Gateway

An **API gateway** is a reverse proxy *plus* API-product features: authentication, authorization, rate limiting, quota enforcement, request transformation, API versioning, request validation, developer portal, monetization. AWS API Gateway, Kong, Apigee, Tyk, Azure API Management, Gloo.

When to use one:

- You have many APIs from many teams and want a unified surface for API consumers.
- You want to expose APIs to third parties with auth, throttling, monetization.
- You want to do request transformation between client-friendly and backend formats.

When **not** to use one:

- For service-to-service communication. Use a service mesh.
- For trivial routing. NGINX or Envoy alone is fine.

### 11.3 Backend for Frontend (BFF)

A pattern: a thin API layer per client type (mobile, web, partner) that aggregates and shapes data from many services. Avoids one bloated API trying to satisfy everyone. Often implemented in Node.js/Go/etc., calling internal microservices.

---

## 12. DNS at Scale

We covered DNS basics in Part 1. At scale, DNS becomes a critical piece of infrastructure with its own design considerations.

### 12.1 Authoritative DNS Architecture

A high-traffic authoritative DNS (the server that owns a zone like `example.com`) needs:

- **Anycast.** Same IP announced from many points; users hit the nearest.
- **In-memory zone data** with delta updates.
- **Massive UDP throughput.** DNS is mostly small UDP packets; you want kernel bypass (DPDK) or eBPF for line-rate processing.
- **DDoS mitigation.** DNS is a favored DDoS amplification vector and target.
- **DNSSEC** — cryptographic signing of records to prevent cache poisoning. Operationally fiddly; widely supported but underdeployed.

### 12.2 Recursive Resolvers

Public resolvers like `1.1.1.1` and `8.8.8.8` answer for billions of clients. They cache aggressively, prefetch popular records, and are themselves anycast.

### 12.3 DNS as a Service Discovery Mechanism

In Kubernetes, services get DNS names like `myservice.mynamespace.svc.cluster.local`. CoreDNS resolves these from the Kubernetes API. Other systems use Consul, etcd, or proprietary discovery (Eureka).

DNS-based service discovery has limitations:
- TTL-driven; slow to reflect topology changes.
- No notion of weights or health (in classic DNS).
- Returns lists of IPs; clients need to do their own balancing.

For service-to-service inside a mesh, you usually want **xDS** (Envoy's discovery API) instead, which streams updates push-style.

### 12.4 DNS over HTTPS / TLS (DoH / DoT)

Encrypts DNS queries. Privacy and integrity benefits; complicates observability and on-network filtering. Increasingly the default in browsers.

---

## 13. Content Delivery Networks (CDNs)

A CDN is a network of geographically distributed servers ("edge nodes" or "PoPs" — points of presence) that cache content close to users.

### 13.1 What Problem CDNs Solve

- **Latency.** Speed of light is the floor; bringing content closer cuts RTTs.
- **Bandwidth at origin.** Origin serves a small number of large files; edges serve everyone else.
- **Reliability.** A failing origin doesn't take you down if the edge has cached responses.
- **DDoS absorption.** CDN edges absorb attack traffic.

### 13.2 How They Work

1. User resolves `cdn.example.com` → an IP at the nearest PoP (via anycast or geo-DNS).
2. Edge checks its cache. **Cache hit** → serves directly.
3. **Cache miss** → fetches from origin (or a regional shield), caches per `Cache-Control` headers, serves to user.
4. On expiry / invalidation, cached object is purged or revalidated.

### 13.3 Cache Keys and Variants

The cache key is typically `(host, path)` plus some headers (`Vary` header tells the CDN which request headers create distinct cached variants — `Accept-Encoding`, `Accept-Language`).

Mistakes to avoid:
- Caching responses keyed only on URL when content varies by `Authorization` (you'd serve one user's data to another).
- Forgetting `Vary: Accept-Encoding` (gzip vs. brotli vs. uncompressed mixing up).

### 13.4 Cacheable vs. Uncacheable

- **Static assets** (images, CSS, JS, video) — cache forever with content-hashed URLs (`app.a8f3d2.css`); deploys produce new URLs.
- **API responses** — usually cache for short windows (seconds–minutes) where staleness is tolerable.
- **Personalized content** — cache only at the user level (edge KV, signed URLs) or skip caching.

### 13.5 Push vs. Pull CDNs

- **Pull CDN** (most common) — origin serves everything; edge fetches on miss.
- **Push CDN** — you upload content to the CDN explicitly. Used when origin is slow or expensive (e.g., video hosting where you upload once and forget).

### 13.6 Modern CDN Features

Edges have evolved into compute platforms:

- **Edge functions** — JavaScript/WASM at the edge (Cloudflare Workers, AWS Lambda@Edge, Fastly Compute@Edge, Vercel Edge).
- **Edge KV / R2 / D1** — small key-value or SQL storage at the edge.
- **Image optimization** — resize/recompress on the fly.
- **Streaming** — HLS/DASH manifest stitching, ad insertion.
- **WAF, bot management, rate limiting** — security at the edge.

### 13.7 Key Players

- **Cloudflare** — security-first, dev-friendly Workers platform, free tier.
- **Akamai** — the original CDN, deepest edge footprint, enterprise focus.
- **Fastly** — programmable VCL config, instant purges, used by major news/media.
- **AWS CloudFront** — tightly integrated with AWS.
- **Google Cloud CDN** — leverages Google's edge.

---

## 14. Caching — The Definitive Treatment

Caching is the single most important performance technique in system design. It's also the source of more correctness bugs than almost anything else. Understanding caching deeply pays off forever.

### 14.1 Why Cache

A cache trades **memory** (cheap, fast, volatile) for **avoided work** (compute, IO, network). The hit rate determines the value: a 90% hit rate means 10× fewer requests to the slow path. A 99% hit rate means 100× fewer.

### 14.2 Where to Cache

Caching exists at many layers, often simultaneously:

1. **CPU caches** (L1/L2/L3) — automatic, transparent. Affects performance via locality.
2. **In-process cache** (HashMap, Caffeine, Guava in Java; LRU dicts in Python) — fastest, but per-instance, no sharing.
3. **Local disk** (browser cache, app data dir) — survives restarts.
4. **Distributed cache** (Redis, Memcached) — shared across instances, network round trip.
5. **Database query cache / buffer pool** — built into the database.
6. **CDN edge cache** — closest to the user.
7. **Browser cache** — closest of all; controlled via HTTP headers.

A good architecture caches strategically at multiple layers.

### 14.3 Caching Patterns

**Cache-aside (lazy loading).** The application checks the cache; on miss, queries the DB and populates the cache. Most common pattern.

```
read(key):
    val = cache.get(key)
    if val is None:
        val = db.get(key)
        cache.set(key, val, ttl=300)
    return val
```

Pros: only cache what's actually requested; cache failures don't block.  
Cons: stale on miss-then-update races; "thundering herd" on cold starts.

**Read-through.** The cache library itself fetches on miss; application just calls `cache.get`. Cleaner but couples the cache to the data layer.

**Write-through.** Writes go to cache and DB synchronously. Reads always hit hot cache. Slow writes; durability depends on DB.

**Write-back (write-behind).** Writes go to cache, asynchronously flushed to DB. Fastest writes. **Risk of data loss** if the cache crashes before flush. Good for write-heavy non-critical data (analytics, view counters).

**Write-around.** Writes go directly to DB; cache populated only on read. Good when writes don't need to be read soon.

**Refresh-ahead.** Cache proactively refreshes hot keys before TTL. Avoids cold-start penalties for predictable reads.

### 14.4 Eviction Policies

When the cache fills, what to evict?

- **LRU** (Least Recently Used) — evict whatever hasn't been touched longest. Most common; good general-purpose.
- **LFU** (Least Frequently Used) — evict by use count. Better for skewed distributions; costs more bookkeeping.
- **TinyLFU / W-TinyLFU** — modern hybrid. The default in Caffeine. Tracks frequency in a probabilistic data structure (count-min sketch) plus an LRU window. Excellent hit rates.
- **FIFO** — evict oldest insert. Simple; mediocre.
- **Random** — surprisingly competitive; near-zero overhead.
- **TTL-based** — entries expire on a timer; evicted lazily on access or by a cleaner.
- **ARC** (Adaptive Replacement Cache) — adapts between recency and frequency. Patented by IBM; used in some storage systems.

### 14.5 Cache Invalidation — The Hard Problem

Phil Karlton: "There are only two hard things in computer science: cache invalidation and naming things."

The problem: when the underlying data changes, the cache is stale. How do you keep them in sync?

Approaches:

1. **TTL (Time To Live).** Just expire after some duration. Simple, but accept staleness up to the TTL.
2. **Event-driven invalidation.** When data changes, publish an event; cache subscribers invalidate. Better freshness, more complex (requires reliable pub/sub).
3. **Write-through.** Updates always hit the cache.
4. **Versioned keys.** Cache key includes a version (`user:42:v17`). When data changes, version bumps; old keys become unreachable and eventually evicted. No invalidation needed; just stale storage.
5. **Stale-while-revalidate.** Serve stale data immediately, refresh in background. Industry practice for read-heavy systems.

### 14.6 Cache Pathologies

Patterns that bite real systems:

**Thundering herd / cache stampede.** A hot key expires; thousands of concurrent requests all miss; they all hit the database, which falls over. Mitigations:
- **Singleflight / request coalescing** — only one request to the DB per key; others wait on its result.
- **Probabilistic early expiration** — refresh with probability that increases as TTL approaches; spreads refresh load.
- **Lock-and-refresh** — when expiring, one request gets a lock to refresh; others serve stale.

**Cache penetration.** Queries for keys that don't exist (random IDs from a scanner). Every miss hits the DB.
- Cache the negative result (with shorter TTL).
- **Bloom filter** in front of the cache to quickly answer "definitely not present."

**Cache avalanche.** Many keys expire simultaneously (e.g., bulk-loaded with same TTL); huge spike on the DB.
- Add jitter to TTLs.
- Stagger pre-warming.

**Hot key.** A single key (e.g., a celebrity's profile) gets vastly more traffic than others, overwhelming a single cache shard.
- Replicate hot keys across multiple nodes.
- Use a local in-process cache as L1 in front of the distributed cache.

**Hot partition / hot shard.** Same as hot key but across an entire shard. Often requires sharding by composite key (user_id + bucket) or moving to a cache that auto-rebalances.

**Cache inconsistency.** Updates to two stores (e.g., DB and cache) where one fails.
- Always update DB first, then invalidate cache (don't update cache directly with new value — race conditions).
- Use CDC to drive cache invalidation from the DB's change log.

### 14.7 Distributed Caches

**Memcached** — pure key-value, no persistence, no replication, multi-threaded. Extremely fast and simple. Sharded by consistent hashing on the client side. Very widely used at hyperscale (Facebook's mcrouter, Twitter's Twemcache).

**Redis** — way more than a cache: data structures (strings, hashes, lists, sets, sorted sets, streams, bitmaps, hyperloglog, geospatial), pub/sub, scripting, transactions, persistence (RDB snapshots, AOF append-only file), replication, Cluster mode for sharding. Single-threaded (per shard) but very fast. The Swiss army knife.

When to pick:
- **Memcached:** plain caching, want simplicity, multi-threaded performance for big values.
- **Redis:** anything beyond plain key-value (counters, queues, leaderboards, geo), or you need persistence.

**Hyperscale variants:**
- **Facebook's TAO** (graph cache for social data) — write-through with consistency from MySQL.
- **Facebook's Memcached fleet** — McRouter for client-side sharding and replication.
- **Twitter's Twemcache** — high-throughput memcached fork.

### 14.8 Real-World Numbers

Modern Redis (single instance, simple GET/SET): ~100K–500K ops/sec per node, sub-millisecond latency. Clusters scale roughly linearly. Memory cost is the binding constraint.

Memcached: similar, often higher throughput per core because it's multi-threaded.

In-process caches: tens of millions of ops/sec, nanosecond latency.

---

## 15. Databases I — Relational (SQL) Deep Dive

The relational model has been the workhorse of data storage for half a century, and despite endless predictions of its death, it remains the right answer for most OLTP problems.

### 15.1 The Relational Model

A relation is a set of tuples with named, typed attributes. SQL is the language for querying and manipulating relations. The key idea: **separate the logical model from the physical storage** and let a query optimizer figure out how to execute.

Strengths:

- **ACID transactions** with rich concurrency control.
- **Declarative queries** — say what you want, not how to get it.
- **Joins** — relate data across tables without precomputed materializations.
- **Schema and constraints** — strong typing, foreign keys, uniqueness, check constraints.
- **Mature ecosystem** — tooling, expertise, libraries.

### 15.2 ACID

- **Atomicity** — a transaction's operations all commit or all abort.
- **Consistency** — transactions take the database from one valid state to another (constraints hold).
- **Isolation** — concurrent transactions appear to run serially (modulo isolation level).
- **Durability** — committed transactions survive crashes.

ACID is implemented via:
- **Write-ahead log (WAL)** — every change written to log before being applied to disk. Crash recovery replays the log.
- **Locking and/or MVCC** — concurrency control.
- **fsync** — forcing writes through OS caches to physical media.

### 15.3 Storage Engines

Two dominant designs:

**B-tree (and B+tree)** — pages on disk, ordered, balanced. Each lookup is `O(log n)` page reads (typically 2–4 IOs even for billion-row tables, because the index fans out). Updates write the changed page plus the WAL. Good for read-heavy and mixed workloads. PostgreSQL's heap+B-tree, MySQL InnoDB's clustered B+tree, Oracle, SQL Server.

**LSM-tree** (Log-Structured Merge tree) — writes go to an in-memory memtable and a WAL; periodically flushed to immutable sorted files (SSTables); background compaction merges and sorts. Trades read amplification (must check multiple levels) for write throughput. Used by RocksDB, LevelDB, and many NoSQL engines (Cassandra, HBase, ScyllaDB, CockroachDB's storage layer, MyRocks).

When to pick:
- **B-tree** — read-heavy, low write amplification needed, predictable latency.
- **LSM** — write-heavy, willing to tune compaction, want compression.

### 15.4 PostgreSQL vs. MySQL

The two open-source giants. Different design philosophies.

**PostgreSQL.** Standards-compliant, feature-rich, extensible (CREATE EXTENSION; PostGIS, pgvector, TimescaleDB, Citus). MVCC with the famous "vacuum" garbage collection. Strong query planner. JSONB. Excellent for complex queries, mixed workloads, and as a Swiss-army backend.

**MySQL.** Simpler, traditionally faster for simple workloads, dominant in web (LAMP). InnoDB engine is a clustered-index B+tree (primary key determines physical order). Huge ecosystem (Vitess for sharding, ProxySQL for routing).

In 2025, **Postgres is the default choice** for most new projects. MySQL still rules where sharding via Vitess (e.g., YouTube) is the pattern, or where existing infrastructure dictates.

### 15.5 The SQL Execution Lifecycle

A query goes through:

1. **Parser** — text → AST.
2. **Rewriter** — apply views, rules.
3. **Planner / optimizer** — generate execution plans, estimate cost (using table statistics), pick the cheapest. Cost is bytes-read, CPU, memory.
4. **Executor** — runs the plan: sequential scans, index scans, index-only scans, hash joins, merge joins, nested loop joins, sorts, aggregations.

Read execution plans (`EXPLAIN`, `EXPLAIN ANALYZE`) — this is mandatory for serious database work. Most performance issues are visible in the plan: missing index, bad estimate, wrong join order, full table scan you didn't expect.

### 15.6 Joins

- **Nested loop join** — for each row in A, scan B (or use an index on B). `O(n × m)` without index, `O(n × log m)` with. Good for small A, indexed B.
- **Hash join** — build a hash table on B (smaller side), probe with A. `O(n + m)` but needs memory.
- **Merge join** — both sides sorted, walk in parallel. `O(n + m)` after sort. Good when inputs are already sorted (e.g., on indexed columns).

Optimizers pick based on stats. Bad stats → bad plans. `ANALYZE` keeps stats fresh.

### 15.7 The N+1 Query Problem

```python
users = db.query("SELECT * FROM users WHERE active = true")  # 1 query
for user in users:
    user.orders = db.query("SELECT * FROM orders WHERE user_id = ?", user.id)  # N queries
```

Catastrophic at scale. Every ORM has tools to fix it (eager loading, joins, IN clauses). The first thing to look for when an endpoint is slow.

### 15.8 Indexes

Indexes are the single biggest lever in relational performance. Covered in detail in §18; for now, understand:

- A primary key is automatically indexed (it's typically the clustered index in InnoDB, separate in Postgres).
- Foreign keys are *not* automatically indexed — index them or pay for joins.
- Indexes accelerate `WHERE`, `JOIN`, `ORDER BY`. They also slow `INSERT`/`UPDATE`/`DELETE` because each index must be maintained.
- Composite indexes are direction-sensitive: `(a, b)` helps `WHERE a = ?` and `WHERE a = ? AND b = ?`, but not `WHERE b = ?` alone.
- Use `EXPLAIN` to confirm an index is actually being used.

---

## 16. Databases II — NoSQL Families

"NoSQL" is a marketing term for "not relational." It covers four very different families:

### 16.1 Key-Value Stores

The simplest data model: opaque values keyed by opaque keys. Examples: Redis, DynamoDB (in basic mode), Riak, etcd, RocksDB, FoundationDB.

Use cases: caching, session storage, leaderboards (Redis sorted sets), feature flags, configuration.

Strengths: blazing fast, trivial to scale (pure shard by key).

Limitations: no rich queries, no joins, no secondary indexes (in pure form).

### 16.2 Document Stores

Values are structured documents (typically JSON/BSON). You can query and index by fields *inside* the document. Examples: MongoDB, Couchbase, Amazon DocumentDB, Firestore.

Use cases: content management, catalogs, user profiles where the schema varies, prototyping.

Strengths: flexible schema, document = aggregate (locality is good for fetches), JSON-native APIs match modern app development.

Limitations: weaker join semantics than relational; cross-document transactions historically limited (modern MongoDB has them, but at cost); easy to design yourself into trouble with deeply nested or unbounded documents.

### 16.3 Wide-Column / Column-Family Stores

Data model: rows have many columns, but columns aren't fixed up front; columns are grouped into "families" stored together. Inspired by Google's Bigtable. Examples: Cassandra, HBase, ScyllaDB, Bigtable.

Storage is **column-family-oriented**, optimized for writes (LSM-trees) and time-series-shaped data.

**Cassandra** in particular is the canonical example: peer-to-peer, no single leader, AP under CAP, gossip-based membership, tunable consistency per query (ONE / QUORUM / ALL). Designed for massive write throughput across many regions. Powers Discord (trillions of messages), Netflix metadata, Apple iCloud.

Use cases: time-series, write-heavy logs, IoT data, large-scale messaging, audit trails.

Limitations: query patterns must be designed in advance; ad-hoc queries are painful; "denormalize for the read path" is the rule.

### 16.4 Graph Databases

First-class nodes and edges with properties. Examples: Neo4j, JanusGraph, Amazon Neptune, Dgraph, ArangoDB.

Use cases: social networks (friend-of-friend queries), fraud detection (traversal of money flows), knowledge graphs, recommendation, identity and access (a la ReBAC).

Strengths: traversal queries (`p99` for "friends of friends with shared interests" is fast where SQL would do many joins).

Limitations: less mature operationally than SQL; harder to shard cleanly (graph partitioning is hard); often adopted in addition to a primary store, not instead of.

### 16.5 When to Choose What

A practical decision flow:

- **Default to relational (Postgres).** It does most jobs well; the ecosystem is unmatched; modern Postgres handles JSON, vectors (pgvector), time-series (TimescaleDB), search (full-text, pgvector + RAG), and even queueing.
- **Add Redis** for caching, rate limiting, transient state.
- **Pick a wide-column store** when you have massive write volume, time-series shape, or known access patterns and you need horizontal scale beyond a single Postgres.
- **Pick a document store** when truly schema-less and the access pattern is "fetch this document by ID."
- **Pick a graph database** when traversal is a first-class workload.
- **Pick specialized stores** for specialized workloads — search (Elasticsearch, OpenSearch, Vespa), analytics (ClickHouse, Druid), vectors (Pinecone, Qdrant, Weaviate, Milvus).

The pattern that emerges: **polyglot persistence** — different stores for different jobs, kept in sync via CDC and event streams.

---

## 17. Databases III — NewSQL and Distributed SQL

NewSQL is a third wave: SQL semantics + ACID transactions + horizontal scale. The trade-offs of the NoSQL era (give up SQL and ACID for scale) are being undone by systems that scale to many nodes while preserving familiar guarantees.

### 17.1 Google Spanner

The canonical example. Spanner gives you:

- Globally distributed SQL.
- External consistency (linearizable across the entire system).
- Synchronous replication via Paxos.
- The crucial trick: **TrueTime** — a clock API that returns a bounded interval `[earliest, latest]` rather than a single timestamp, allowing the system to wait out clock uncertainty for global ordering.

Used internally for Google's most critical systems (Ads, Drive, Photos). Available externally as Cloud Spanner.

### 17.2 CockroachDB

Open-source, Spanner-inspired, self-hostable. Uses HLCs (hybrid logical clocks) instead of TrueTime — accepts slightly looser guarantees but doesn't need atomic clocks. Range-based sharding ("ranges" of ~512 MiB), Raft per range, distributed SQL execution. Postgres wire-compatible.

### 17.3 TiDB / TiKV

PingCAP's stack. TiKV is a Raft-based key-value store; TiDB sits on top providing MySQL-compatible SQL. Used at scale by ByteDance, Square, Zalando.

### 17.4 YugabyteDB

Postgres-compatible distributed SQL with a Spanner-style storage layer.

### 17.5 Vitess

Different angle: not a new database, but a sharding layer on top of MySQL. Originally built at YouTube; powers GitHub, Slack, HubSpot, Square. Treats a fleet of MySQL instances as one logical database. The pragmatic choice when you want MySQL semantics + horizontal scale.

### 17.6 Trade-offs

NewSQL is amazing but not free:

- **Latency.** Single-region, multi-AZ writes cost you a Paxos round trip (1–10 ms typical). Multi-region writes cost you cross-region RTTs. There is no magic; physics still applies.
- **Operational complexity.** A 3-node CockroachDB cluster is more complex than a single Postgres.
- **Maturity.** Postgres has 30 years of optimizer hardening; distributed SQL optimizers are catching up.

For most apps under, say, 10–100 TB and < 50K writes/sec, single-node Postgres with read replicas is simpler and faster. Reach for distributed SQL when you have a real reason.

---

## 18. Indexing Deep Dive

Indexes are the bridge between data and queries.

### 18.1 B-tree / B+tree

Already the dominant on-disk index. A balanced tree with high fanout (hundreds of keys per node), so depth is small even for billions of rows. Internal nodes guide; leaf nodes hold data (or pointers).

In a **B+tree** (variant used by most databases), all data lives at leaves, and leaves are linked into a sorted list — making range scans efficient.

Trade-offs:
- Reads: `O(log n)`, ~3–4 disk pages even for billions of rows.
- Writes: must locate, possibly split nodes; logged via WAL.
- Random IO heavy on writes (mitigated by memory caching of hot pages).

### 18.2 LSM-tree

Write-optimized. Memtable + sorted run files (SSTables). Reads probe multiple levels (mitigated by Bloom filters per SSTable to skip levels). Compaction in background merges runs.

Trade-offs:
- Writes: sequential, fast, log-structured.
- Reads: amplification, but fast with Bloom filters and warm caches.
- Space: amplification depends on compaction strategy (tiered vs. leveled).
- Compaction is non-trivial to tune; bad compaction crushes performance.

### 18.3 Hash Indexes

Bucket-based, `O(1)` lookups. No range queries. Used in main-memory KV stores (Redis hashes, in-memory caches) and on disk (Berkeley DB hash, some Postgres scenarios).

### 18.4 Bitmap Indexes

For low-cardinality columns (gender, status). Each value gets a bitmap; queries do bitwise AND/OR. Phenomenal for analytics; bad for OLTP because updates require rewriting bitmaps. Used in column stores and data warehouses.

### 18.5 Inverted Index

The data structure of search engines. For each *term*, a posting list of documents containing it. `(word → [doc1, doc5, doc23, …])`.

Querying "system design" intersects the posting lists for "system" and "design." Modern inverted indexes (Lucene → Elasticsearch / OpenSearch / Solr / Vespa) compress posting lists, store positions for phrase queries, and add scoring (TF-IDF, BM25, vector hybrid).

### 18.6 Geo Indexes

Spatial data needs spatial indexes:

- **Geohash** — interleave lat/lon bits to produce a string; nearby places share prefixes. Uber's H3 is a related hexagonal grid system.
- **R-tree** — spatial trees, used in PostGIS.
- **Quadtree** — recursive 2D subdivision; used in Google Maps tiling.

### 18.7 Vector Indexes

For semantic / embedding search. Vectors live in `R^d` (typically `d = 384` to `4096`). You want approximate nearest neighbors (ANN) — exact NN is `O(n)` per query, useless at scale.

Algorithms:

- **HNSW** (Hierarchical Navigable Small World) — graph index, dominant in 2025. Used by Pinecone, Weaviate, Qdrant, pgvector.
- **IVF** (Inverted File) — partition vectors into clusters; search the closest few clusters. Used in FAISS.
- **PQ** (Product Quantization) — compress vectors for memory efficiency. Combined with IVF (IVF-PQ) for billion-scale.
- **DiskANN** — index that fits on SSD; used by Microsoft for very large corpora.

### 18.8 Composite, Covering, Partial, Functional Indexes

- **Composite index** on `(a, b, c)` orders rows by a then b then c. Useful for queries fixing a leading prefix.
- **Covering index** includes all columns the query needs; the engine doesn't have to fetch the heap.
- **Partial index** indexes only rows matching a condition (`WHERE active = true`). Smaller, faster.
- **Functional index** indexes a function (`LOWER(email)`); allows queries like `WHERE LOWER(email) = ?` to use it.

### 18.9 The Cost of Indexes

Every index slows writes and consumes space. The classic mistake is to index every column "just in case." Watch which indexes are actually used (Postgres `pg_stat_user_indexes`) and drop the dead weight.

---

## 19. Replication

Replication = making copies of data on multiple machines for durability, availability, and read scalability.

### 19.1 Single-Leader (Primary–Replica)

One leader accepts writes; replicas pull (or are pushed) the change log and apply it. Most relational systems work this way: Postgres streaming replication, MySQL binlog replication, MongoDB replica sets, Redis replication.

Replication can be:

- **Synchronous** — leader waits for at least N replicas to ack before confirming the write. No data loss on leader failure (modulo subtleties); higher write latency; fewer failure tolerances.
- **Asynchronous** — leader confirms writes immediately, replicas catch up in the background. Low latency; possible data loss on leader failure if the leader's acked writes hadn't propagated.
- **Semi-synchronous** — at least one replica must ack synchronously; others are async. A common compromise.

Failover is the hard part:

- Detecting that the leader failed (vs. just slow / partitioned).
- Promoting a replica to leader (which one? the most caught-up?).
- Notifying clients (DNS, service discovery, consensus-managed leader info).
- Avoiding **split brain** — two leaders thinking they're authoritative.

Tools: Patroni for Postgres, Orchestrator for MySQL, Sentinel and Cluster for Redis.

### 19.2 Multi-Leader

Multiple nodes accept writes; they replicate to each other. Used for multi-region deployments where every region needs local writes.

Problem: **conflicts.** If user updates are accepted in two regions before they replicate, you get conflicting values for the same row. Resolution strategies:

- **Last-Write-Wins (LWW)** — pick the one with the highest timestamp. Fast, but can lose writes. Cassandra's default.
- **Application-level merge** — the app sees both values and decides. (Used in shopping carts: union them.)
- **CRDTs** (Conflict-free Replicated Data Types) — data structures designed to merge deterministically without conflicts. Great for collaborative editing, counters, sets. Used in Riak, Redis (CRDT modules), Automerge, Yjs.

### 19.3 Leaderless (Dynamo-style)

No leaders. Clients write to a quorum of replicas (W) and read from a quorum (R), where `W + R > N` (total replicas) ensures overlap and thus consistency.

Examples: Cassandra, DynamoDB, Riak.

Read repair and anti-entropy (Merkle trees) bring divergent replicas back into sync.

Tunable: pick `W=1, R=1` for max performance and eventual consistency, or `W=N, R=1` (write-all-read-one) for consistency at the cost of write availability.

### 19.4 Replication Lag

Async replicas drift behind the leader. Effects:

- **Read-after-write inconsistency.** User updates their profile on the leader, immediately reads from a replica, sees the old value.
- **Monotonic read violation.** Two reads, second one served by a more-lagged replica, sees older data.

Mitigations:

- Route a user's reads to the same replica (or to the leader) within a session.
- Track a "logical timestamp" of each write and refuse reads from replicas behind that timestamp.
- Just send writes-then-reads to the leader.

---

## 20. Partitioning and Sharding

Partitioning ("sharding") splits data across multiple nodes by some key. The terms are interchangeable in most contexts.

### 20.1 Why Shard

Because a single machine has limits — disk size, RAM, write throughput, vertical-scale ceiling. Sharding lets you spread data and writes across many machines, scaling horizontally.

### 20.2 Strategies

**Range partitioning.** Each shard owns a contiguous range of keys (`A–F`, `G–M`, …). Good for range scans. Bad if your keys are sequential (e.g., timestamps): all writes hit the latest shard. Solution: shuffle the leading bits, or use hash partitioning.

**Hash partitioning.** Hash the key, mod by shard count, route to shard. Even distribution, no range scans. The naive `hash % N` is bad: changing N redistributes everything.

**Consistent hashing.** Map both keys and shards onto a ring; each key goes to the next shard clockwise. Adding/removing a shard moves only `1/N` of keys. The standard for distributed caches and many KV stores. Variants: virtual nodes (each physical shard owns many points on the ring) for better balance; **rendezvous hashing** as an alternative with similar guarantees.

**Directory-based partitioning.** A central lookup service maps keys to shards. Maximum flexibility (rebalance freely), but the directory is itself a critical service.

**Composite / hierarchical.** Shard by a combination of keys (`(tenant, user)`) to keep related data together while balancing load.

### 20.3 Hot Partitions

Even with hash partitioning, a single key can dominate (a celebrity's user ID, today's hot news article). Mitigations:

- **Salting.** Append a random suffix to the hot key; spread writes across `N` virtual keys; combine on read. Good for write-heavy hot keys (counters).
- **Read-side caching.** Cache the hot key aggressively.
- **Replicate the hot key** across multiple shards; route reads round-robin.

### 20.4 Resharding

Eventually you'll need more shards. Painful operations:

- Range partitioning with a shard manager (CockroachDB, Spanner, TiDB) does this online.
- Manual approach: dual-write to old + new schemes, backfill, switch reads, decommission.

Tools like Vitess have rich resharding primitives. Custom-rolled sharding tends to make resharding hellish.

### 20.5 Cross-Shard Operations

The dark side of sharding:

- **Cross-shard transactions** require 2PC (slow, fragile) or distributed transactions (CockroachDB-style).
- **Cross-shard joins** require fan-out, gather, merge.
- **Global secondary indexes** require their own partitioning scheme; reads to find data may need to fan out.

Design data and queries to minimize cross-shard operations. Co-locate data accessed together (same `tenant_id` shard key, for example).

---

## 21. Transactions and Isolation Levels

A **transaction** groups multiple operations into an atomic, isolated unit. Concurrency control must reconcile concurrent transactions.

### 21.1 The Anomalies

What can go wrong without isolation:

- **Dirty read** — read uncommitted writes from another transaction.
- **Non-repeatable read** — re-read a row, get a different value (because another transaction committed in between).
- **Phantom read** — re-execute a range query, get a different set of rows.
- **Lost update** — two transactions read-modify-write the same row; one's update is lost.
- **Write skew** — both transactions read and validate something, then write based on assumptions invalidated by the other's write.

### 21.2 SQL Isolation Levels

Defined by the SQL standard, with subtleties:

| Level | Dirty Read | Non-Rep Read | Phantom | Notes |
|---|---|---|---|---|
| **Read Uncommitted** | Possible | Possible | Possible | Almost never used. |
| **Read Committed** | Prevented | Possible | Possible | Postgres, Oracle default. |
| **Repeatable Read** | Prevented | Prevented | Possible (in standard) / prevented (in some impls) | MySQL InnoDB default. |
| **Serializable** | Prevented | Prevented | Prevented | True serial schedule equivalence. |

**Important:** isolation levels are implementation-defined past the standard. PostgreSQL's "Repeatable Read" is actually snapshot isolation, which prevents phantoms but allows write skew. PostgreSQL's "Serializable" uses Serializable Snapshot Isolation (SSI), which detects and aborts dangerous interleavings.

### 21.3 MVCC

Most modern databases use **Multi-Version Concurrency Control**: instead of locking on read, every write creates a new version of the row tagged with the transaction ID. Readers see a consistent snapshot. Writers don't block readers.

Postgres MVCC creates dead row versions that must be cleaned up via **vacuum** (lazy GC). MySQL InnoDB uses an undo log instead. Both have operational implications: long-running transactions hold back vacuum / undo cleanup, causing bloat.

### 21.4 Two-Phase Locking (2PL)

Locks held until commit. Strict 2PL prevents serialization anomalies but degrades to serial execution under contention. Used in some traditional databases for serializable isolation.

### 21.5 Distributed Transactions

Transactions across multiple databases / services. Hard.

**Two-Phase Commit (2PC).** Coordinator asks all participants to *prepare*; if all say yes, sends *commit*; otherwise *abort*. Blocks if the coordinator fails after prepare. Reliable but slow and fragile.

**Three-Phase Commit (3PC).** Adds a step to remove blocking, but assumes synchronous network. Rarely used.

**Saga.** Long-running, asynchronous. A sequence of local transactions, each with a compensating action. Failure triggers compensation. Used heavily in microservices (Part 3).

In practice: avoid distributed transactions where possible. Design for eventual consistency, idempotency, and sagas.

---

## 22. Message Queues and Streaming Platforms

Messaging decouples producers from consumers, allowing async processing, buffering, and fan-out. Two flavors:

### 22.1 Queues vs. Streams

**Queues** — messages go in, consumers take them out, message is gone. Each message processed once (by one consumer in a group). Examples: RabbitMQ (AMQP), Amazon SQS, ActiveMQ.

**Streams (logs)** — messages appended to an immutable log; consumers read by offset; messages stay around for days/weeks; replayable. Multiple consumer groups can each read independently. Examples: Apache Kafka, AWS Kinesis, Azure Event Hubs, Pulsar (which actually does both well), Redpanda (Kafka-compatible, C++).

The line is blurring (Kafka added "queue mode" semantics; Pulsar always supported both), but the conceptual difference matters.

### 22.2 Apache Kafka — The Giant

Kafka is the dominant streaming platform. Architecture:

- **Topics** are append-only logs.
- **Partitions** within a topic — Kafka's unit of parallelism. A consumer group has at most one consumer per partition. Order is guaranteed *within* a partition.
- **Brokers** host partitions.
- **Replicas** — each partition has a leader and followers (replication factor).
- **Producers** write to the partition leader.
- **Consumers** track their **offset** per partition.
- **Controller** (formerly via ZooKeeper, now KRaft / Raft-based) — manages cluster metadata.

Writes are sequential appends (very fast). Disk is used efficiently with the OS page cache. Kafka famously achieves "millions of messages per second per broker" because it does almost no work per message.

Delivery semantics:

- **At-most-once** — fire and forget; loss possible.
- **At-least-once** — retries on failure; duplicates possible. Default.
- **Exactly-once** — Kafka has idempotent producers + transactions for "exactly once" within Kafka. End-to-end exactly-once requires idempotent consumers (your downstream must tolerate duplicates — e.g., upsert by unique ID).

Use cases: event streaming, log aggregation, CDC pipelines, async work queues, microservice event buses, ML training data pipelines, real-time analytics.

### 22.3 RabbitMQ

Traditional broker. Rich routing (exchanges: direct, topic, fanout, headers), per-message ack, priority queues, delayed messages. Lower throughput than Kafka but more flexible message-by-message routing. Good for traditional task queues (but Sidekiq/Celery/RQ on Redis are also common).

### 22.4 NATS, Redpanda, Pulsar

- **NATS** — extremely lightweight pub/sub, designed for microservice messaging. NATS JetStream adds persistence.
- **Pulsar** — Yahoo origin, multi-tenant, separates compute (brokers) from storage (BookKeeper). Geo-replication built-in.
- **Redpanda** — C++ Kafka-compatible drop-in. No JVM, no ZooKeeper. Lower latency, simpler ops.

### 22.5 Cloud-Native Messaging

- **AWS SQS** — managed queue, two flavors (Standard at-least-once unordered; FIFO ordered).
- **AWS Kinesis Data Streams** — Kafka-like, fully managed.
- **GCP Pub/Sub** — global publish/subscribe with at-least-once delivery, fan-out.
- **Azure Event Hubs / Service Bus** — Kafka-protocol-compatible Event Hubs; rich Service Bus.

### 22.6 Patterns

- **Work queue** — many workers compete for messages.
- **Pub/sub fan-out** — one publisher, many subscribers.
- **Event sourcing** — log of domain events as system of record.
- **CQRS read model builds** — consume events, build read-side projections.
- **CDC pipeline** — Debezium → Kafka → consumers, streaming database changes.
- **Outbox pattern** — write event to DB in same transaction as data, separate process publishes to broker. Solves dual-write atomicity.

### 22.7 Pitfalls

- **Poison messages** — a message that crashes the consumer; without a dead-letter queue, it'll loop forever blocking progress.
- **Backlog explosion** — consumers slower than producers; the queue grows without bound. Need backpressure or autoscaling.
- **Ordering surprises** — within a partition you have order; across partitions you don't. If you need cross-key ordering, you'll either use one partition (no parallelism) or design the keys carefully.
- **Duplicate handling** — at-least-once means you'll see duplicates; build idempotent consumers.

---

## 23. Search Systems and Inverted Indexes

Search isn't just ⌘F. At scale it's a discipline of its own.

### 23.1 The Pipeline

A search system has roughly four stages:

1. **Crawl / ingest** — pull documents from sources (database CDC, web crawling, file systems).
2. **Index** — tokenize, normalize (lowercase, stem, stopwords), build inverted index, store positions.
3. **Query** — parse query, retrieve candidates, score, rank, return.
4. **Serve** — handle high QPS, low latency, maintain freshness.

### 23.2 Lucene-Family Stacks

**Apache Lucene** is the underlying library. **Elasticsearch / OpenSearch** wrap it as a distributed cluster: shards, replicas, REST API, aggregations, percolator (reverse search). **Solr** is the older sibling, still used. **Vespa** (Yahoo origin) is more capable for ML-driven ranking and supports vector search natively.

### 23.3 Scoring and Ranking

Classical: **TF-IDF** (Term Frequency × Inverse Document Frequency); **BM25** (improved version, default in Lucene). Score boosted by exact phrase, recency, popularity, custom signals.

Modern: hybrid retrieval combining BM25 with **vector similarity** (semantic search). Then a re-ranker (often a cross-encoder or LLM-based) re-scores the top candidates.

### 23.4 Real-Time Indexing

Trade-off: in-memory write buffers see new docs immediately but cost RAM; on-disk segments are durable but require flush+merge cycles. Lucene's compromise: tiny in-memory segments, periodic merges (Lucene "refresh" interval).

### 23.5 Architecture at Scale

- **Sharding** by document hash; query fans out to all shards, merges results.
- **Replication** for read scale and HA.
- **Hot/warm/cold tiers** — recent indices on SSD, older on HDD or object storage. Elasticsearch frozen tier uses S3 directly.
- **Index lifecycle management** — rotate by time (logs, metrics), drop old.
- **Routing** — for multi-tenant, route queries to the tenant's shard.

### 23.6 Specialized Cases

- **Logs/observability** — Elasticsearch is the classic; ClickHouse and Loki are growing alternatives.
- **Product / catalog search** — Algolia, Typesense, Meilisearch (managed/hosted, easy DX).
- **Semantic search** — vector DBs (covered in §18.7 and §81) often hybrid with BM25.

---

## 24. Object Storage and Blob Stores

Object storage is **the default storage tier of the cloud era** — cheap, durable, infinite, HTTP-accessible.

### 24.1 The Model

- Objects (blobs) keyed by string keys, organized in flat namespaces called **buckets**.
- Objects are immutable: you can replace, but not append.
- Reads/writes via HTTP API.
- Eventual consistency historically; modern S3 is read-after-write consistent (since 2020).

### 24.2 The Heavyweights

- **AWS S3** — the original, defines the de facto API.
- **GCS** — Google Cloud Storage.
- **Azure Blob Storage** — three tiers (Hot, Cool, Archive).
- **Cloudflare R2** — S3-compatible, no egress fees (huge cost win).
- **MinIO** — open-source S3-compatible, self-hostable.
- **Ceph** — open-source object + block + file.

### 24.3 Internals (How S3-likes Work)

A modern object store under the hood is roughly:

- **Frontends** — receive HTTPS, authenticate, route.
- **Index / metadata service** — maps key → location of data chunks. Sharded, replicated.
- **Storage nodes** — store data chunks. Erasure coding (e.g., 10 data + 4 parity Reed-Solomon) for durability with much less overhead than 3-way replication.
- **Background workers** — repair, scrub, rebalance.

S3 famously claims "11 nines of durability." It achieves this through erasure coding across many fault domains plus continuous integrity checking.

### 24.4 Use Cases

- **Static assets / web hosting** — images, JS, CSS, video.
- **Backups, archives** — compliance, disaster recovery.
- **Data lake storage** — Parquet/ORC files for warehouses.
- **ML training data** — terabytes of training inputs and model artifacts.
- **Logs and observability data** — Loki, Mimir use object storage as primary tier.

### 24.5 Patterns

- **Pre-signed URLs** — let clients upload directly to S3 without proxying through your servers. Saves bandwidth and CPU.
- **Multipart upload** — uploads > 5 MiB should be chunked; > 5 GiB must be.
- **Lifecycle policies** — auto-tier objects to colder storage after N days, delete after M.
- **Versioning** — keep prior versions for safety.
- **Replication** — cross-region for DR.

### 24.6 The Cost Model

Object storage is cheap for *storage* (~$0.02/GB/month for hot, sub-cent for cold). It can be expensive for **egress** (data leaving the cloud), **requests** (per-API call), and especially **cross-region transfer**. Architects should know these costs; they often dominate at scale.

---

## 25. File Systems

Briefly, because it underlies many of the systems above:

### 25.1 Local File Systems

- **ext4** — Linux default, extents-based, journaled.
- **XFS** — high-throughput, used in databases.
- **ZFS** — advanced (copy-on-write, snapshots, checksums, integrated volume management). Used by Netflix, many storage appliances.
- **Btrfs** — copy-on-write, snapshots; some maturity issues historically.

### 25.2 Network File Systems

- **NFS** — POSIX semantics over network. Latency-sensitive but ubiquitous.
- **SMB/CIFS** — Windows-native equivalent.

### 25.3 Distributed File Systems

- **HDFS** — Hadoop's file system; large blocks (64–128 MB), replicated. Designed for batch.
- **GlusterFS, CephFS** — distributed POSIX file systems.
- **Lustre** — HPC.
- **JuiceFS** — modern distributed FS over object storage.

### 25.4 Cloud File Services

- **AWS EFS** (NFS), **FSx** (multi-protocol).
- **GCP Filestore**.
- **Azure Files**.

In modern cloud architectures, object storage usually replaces shared file systems. Reach for cloud file systems only when POSIX semantics are required (legacy apps, ML training that expects directories, etc.).

---

## 26. Time-Series, Graph, and Specialized Stores

### 26.1 Time-Series Databases

Optimized for the shape of time-series data: append-mostly writes ordered by timestamp, range scans by time, aggregation over time windows.

- **InfluxDB** — purpose-built TSDB, used heavily in monitoring.
- **Prometheus** — TSDB + monitoring system; pull-based scraping. The de-facto metrics standard.
- **TimescaleDB** — Postgres extension turning it into a TSDB. Ergonomic if you want SQL.
- **VictoriaMetrics** — high-perf Prometheus-compatible.
- **ClickHouse** — column-store; not a TSDB per se but fantastic for time-series at scale.
- **Thanos / Mimir / Cortex** — long-term, horizontally scalable Prometheus.

### 26.2 Wide-Column Databases for Time-Series

Cassandra, Bigtable, ScyllaDB shine for high-volume time-series (IoT, observability) where the access pattern is "give me data for entity X in time range Y."

### 26.3 OLAP / Column Stores

For analytics over large data:

- **ClickHouse** — open-source MergeTree column engine. Insanely fast scans.
- **Apache Druid** — segment-based, real-time + historical, used at Netflix, Pinterest.
- **Apache Pinot** — LinkedIn-origin, real-time analytics.
- **Snowflake / BigQuery / Redshift** — managed warehouse stalwarts.
- **DuckDB** — embedded analytical SQL; the SQLite of analytics.

### 26.4 Graph Databases

Already covered (§16.4). Operationally tend to be smaller-scale; large-scale graph workloads often live on specialized infra (Facebook's TAO, LinkedIn's graph DB, Uber's M3).

### 26.5 Vector Databases

Covered in detail in §81. Briefly: Pinecone, Weaviate, Qdrant, Milvus, ChromaDB; pgvector for "I just want it inside Postgres."

### 26.6 Object/Document Hybrid

- **MongoDB** — document store with strong query language.
- **Couchbase** — KV + N1QL (SQL-on-JSON) + caching tier.
- **Firestore** — Google's serverless document DB.

### 26.7 Embedded Stores

Sometimes the right "database" is in your process:

- **SQLite** — public domain, ridiculous reliability, the world's most widely deployed database (every phone, browser, OS).
- **DuckDB** — analytical SQLite.
- **RocksDB / LevelDB** — embedded LSM KV; the storage engine inside countless databases.
- **LMDB** — memory-mapped B-tree KV store.

### 26.8 The Polyglot Persistence Reality

A typical large system has, say:

- **Postgres** for OLTP truth-of-record.
- **Redis** for cache / sessions / rate limit.
- **Elasticsearch** for full-text search.
- **ClickHouse** for analytics.
- **Kafka** as the event backbone.
- **S3** for blobs.
- **Vector DB** for ML retrieval.
- **Time-series DB** for metrics.

Kept consistent through CDC, event streams, and well-defined ownership.

---

# Part 3 — Architectural Patterns

Patterns are how you compose components into systems. Each pattern has a context where it shines and contexts where it harms.

## 27. Monoliths, SOA, and Microservices

### 27.1 The Monolith

A single deployable application containing all business logic. Everything talks via in-process function calls. One database, one deploy.

**Strengths:** simplicity. One codebase, one CI pipeline, one deploy. Refactoring is easy. Transactions are easy. Debugging is easy. No network in the way.

**Weaknesses at scale:** the codebase becomes too large for any one engineer to hold; teams trip over each other; deploys are risky because everything changes at once; scaling forces you to scale the whole app even if only one part is hot; technology choices are locked to whatever the monolith was built with.

**The right scale:** a startup with < 50 engineers should almost always be a monolith. Most of the success stories of "we moved to microservices" are followed years later by "we moved back to a modular monolith." Shopify, Stack Overflow, and many others run monoliths at significant scale.

### 27.2 SOA (Service-Oriented Architecture)

Pre-microservice era of "services." Often built around heavyweight middleware (ESBs — enterprise service buses), SOAP, WSDL, contract-driven. Big-corp roots. The lessons of SOA fed directly into microservices, but the tooling looked very different.

### 27.3 Microservices

Many independently deployable services, each owning a domain, communicating over the network (sync HTTP/gRPC, async messages).

**Strengths:** team autonomy (each team owns its services); independent deploys (smaller blast radius per change); independent scaling (scale only what's hot); polyglot (each service can use the right language/store); fault isolation (in principle).

**Costs:** distributed systems problems multiply; network latency on every call; operational complexity (many services to deploy, monitor, secure); harder to refactor across boundaries; data is fragmented across stores; "where do transactions happen?" becomes hard; observability is mandatory and expensive.

**When to adopt:** when team coordination is the bottleneck, not technology. Microservices solve organizational problems first, scaling problems second.

### 27.4 The Modular Monolith

Often the right middle ground. One deployable, but internally organized into modules with strict boundaries (separate schemas, no cross-module DB access, only call across modules through defined interfaces). You get most of the design benefits of microservices without the operational cost. When a module's scaling or team needs justify it, peel it off into its own service.

### 27.5 Sizing a Microservice

Common mistakes:
- **Nano-services** — every function is a service. Latency, cost, and ops become unbearable.
- **Distributed monolith** — services so coupled they must be deployed together. Worst of both worlds.

Heuristics:
- A service should have a clear business capability and a single owning team.
- A service's data should be private to it. No other service reaches into its database.
- A service should be deployable independently — schema changes don't break other services.

### 27.6 Service Communication Styles

- **Synchronous** (HTTP/REST, gRPC) — simple, direct, but coupling is tight; failures cascade.
- **Asynchronous** (events, messages) — looser coupling, better fault isolation, but eventual consistency and complexity in tracing/debugging.

Best practice: **use sync for queries, async for state changes.** Commands ("create order") are events; queries ("get order") are direct.

---

## 28. Event-Driven Architecture

In an event-driven architecture, services publish events when state changes; other services react.

### 28.1 Events as the Backbone

An **event** is a fact: "OrderPlaced", "PaymentReceived", "InventoryReserved". It's immutable, named in past tense, owned by the publisher.

A **command** is an instruction: "PlaceOrder". It can fail. Different concept.

Events flow through a message broker (Kafka, RabbitMQ, NATS, cloud pub/sub). Each consumer subscribes to topics it cares about and reacts independently.

### 28.2 Benefits

- **Loose coupling.** Producer doesn't know who consumes.
- **Temporal decoupling.** Consumer doesn't have to be running when event is published.
- **Easy fan-out.** Add a new consumer by subscribing.
- **Resilience.** Consumer down → events buffer; consumer comes back → catches up.
- **Auditability.** Event log is a natural audit trail.

### 28.3 Costs

- **Eventual consistency** is the default; stale reads are normal.
- **Debugging is harder.** A request triggers a chain of events; tracing requires correlation IDs and distributed tracing.
- **Schema evolution** is critical. Events live forever; old consumers must keep working with new event versions. Use schema registries (Confluent Schema Registry, Apicurio) and compatibility rules.

### 28.4 Patterns

- **Publish/Subscribe** — one-to-many event delivery.
- **Event Notification** — small events that trigger other services to query for full data ("OrderUpdated, id=123" → consumer fetches order).
- **Event-Carried State Transfer** — events carry the changed data; consumers can update their local state without callbacks.
- **Choreography vs. Orchestration** (covered in §30).

---

## 29. CQRS and Event Sourcing

Two patterns often paired but separable.

### 29.1 CQRS

**Command Query Responsibility Segregation.** Splits the model into a write side (commands that mutate state) and a read side (queries that return data). They can have different models, different stores, different scaling profiles.

Why: read patterns and write patterns often diverge. Writes might be normalized for integrity; reads might be denormalized for query performance. CQRS lets you optimize each independently.

Implementation: writes go to the write store (often event-driven); reads go to one or more read stores (projections), updated by consuming the write side's events.

When to use:
- Massive read/write asymmetry.
- Complex reporting/analytics needs alongside transactional updates.
- Domain models that resist serving both UIs and APIs from the same shape.

When not:
- Most CRUD apps. CQRS adds significant complexity.

### 29.2 Event Sourcing

Instead of storing the current state, store the **sequence of events** that led to it. Current state is derived by replaying events.

Strengths:
- **Complete audit trail** for free.
- **Time travel** — reconstruct state at any past time.
- **Replayability** — bug in derivation logic? Fix code, replay events, rebuild state.
- **Multiple projections** — derive different read models from the same events.

Costs:
- **Schema evolution of events** is hard (events are immutable; old events must remain interpretable).
- **Querying current state** requires a projection — you don't query the event log directly for current state.
- **Mental shift.** Most developers think in terms of state, not events.
- **Snapshots** needed once event histories grow long, to avoid replaying millions of events.

Often paired with CQRS: write side is event-sourced; read side is projections.

Used in finance (ledgers are inherently event-sourced), e-commerce (order history), audit-heavy domains. Also overkill for many use cases.

---

## 30. Sagas, Choreography, Orchestration

Distributed transactions are bad. Sagas are how you get transactional-ish behavior across services without 2PC.

### 30.1 The Saga Pattern

A saga is a sequence of **local transactions**. Each step has a corresponding **compensating action** that semantically undoes it. If any step fails, run the compensations for completed steps.

Example: "Place Order" saga
1. ReserveInventory (compensate: ReleaseInventory)
2. ChargePayment (compensate: RefundPayment)
3. CreateShipment (compensate: CancelShipment)

If step 2 fails, run compensation for step 1.

### 30.2 Choreography

Each service reacts to events; no central coordinator. Service A publishes "OrderPlaced", Service B reacts, publishes "InventoryReserved", Service C reacts, etc.

Pros: simple, decentralized, no SPOF.  
Cons: business flow is implicit, scattered across services. Hard to see the whole saga. Cyclical dependencies easy to create.

### 30.3 Orchestration

A central orchestrator (a workflow engine) tells services what to do and tracks progress.

Pros: explicit flow, easy to visualize and debug, easy to add steps.  
Cons: orchestrator is a critical service; it's a coupling point.

Tools: **Temporal** (the modern winner), **AWS Step Functions**, **Cadence** (Temporal's predecessor at Uber), **Camunda** (BPMN), **Apache Airflow** (more for batch).

Temporal is particularly worth knowing. It treats workflows as code (write a function; pauses and retries are transparent), persists state, replays on failure, makes long-running flows trivial.

### 30.4 Idempotency Is Mandatory

Sagas retry. Compensations retry. Every step must be idempotent: re-running it must not double-charge, double-ship, or double-anything. Standard techniques: idempotency keys, dedup tables, conditional writes.

---

## 31. Service Mesh

A service mesh moves cross-cutting concerns out of application code into a layer of network proxies. Each service has a **sidecar proxy** (typically Envoy) that handles:

- mTLS between services.
- Service discovery.
- Load balancing.
- Retries, timeouts, circuit breaking.
- Traffic shaping (canary, blue/green, weighted routing).
- Observability (metrics, traces).
- Authorization policies.

The proxies are the **data plane**. A **control plane** configures them.

### 31.1 The Major Meshes

- **Istio** — most feature-rich, biggest community, can be operationally heavy. Envoy data plane.
- **Linkerd** — Rust-based, ultralight, simpler operationally. Uses its own micro-proxy (linkerd2-proxy), not Envoy.
- **Consul Connect** — HashiCorp.
- **Cilium Service Mesh** — eBPF-based, often runs sidecar-less.

### 31.2 Sidecar vs. Sidecar-less

The sidecar model adds a proxy per pod (memory + latency overhead). Newer "ambient" / "sidecar-less" approaches (Istio Ambient Mesh, Cilium) push functionality into per-node agents or eBPF. Smaller footprint, similar functionality.

### 31.3 When to Adopt

- Many services (dozens+) needing consistent mTLS, observability, traffic policies.
- Strict zero-trust requirements (covered in §52).
- Operationally mature team — meshes are not free.

For a small number of services or a team early in their journey, simpler tools (Envoy + a config repo, or just Kubernetes NetworkPolicies + ingress) are often enough.

---

## 32. Lambda and Kappa Architectures

Patterns for handling both real-time and historical data.

### 32.1 Lambda Architecture

Two pipelines:

- **Batch layer** — slow but accurate, processes all data over time, computes "truth." (Spark, Hadoop on data lake.)
- **Speed layer** — fast but approximate, processes recent events with low latency. (Streaming engine.)
- **Serving layer** — merges results.

The complexity is duplicating logic across both layers. Useful when the batch layer's accuracy is essential.

### 32.2 Kappa Architecture

A single streaming pipeline. To "reprocess history," replay the event log from the beginning. No batch layer.

Simpler. Possible when storage of the full event log is feasible (cheap object storage made this practical). Kafka log compaction, Pulsar tiered storage, etc.

In 2025, Kappa is increasingly the default. Lambda persists where compliance or workload nature demands batch correctness.

---

## 33. Hexagonal, Clean, and DDD Architectures

These are about the *internal* structure of a service.

### 33.1 Hexagonal (Ports and Adapters)

Cockburn's pattern. The application core is independent of any specific technology. It exposes **ports** (interfaces); **adapters** plug specific tech in. The database, the HTTP framework, the message broker — all are adapters at the boundary.

Benefits: testability (swap adapters with fakes), portability, the core stays clean of framework concerns.

### 33.2 Clean Architecture

Robert Martin's variation. Concentric circles: entities (innermost), use cases, interface adapters, frameworks (outermost). Dependencies point inward only.

### 33.3 Domain-Driven Design (DDD)

Eric Evans' approach to modeling complex domains. Key concepts:

- **Ubiquitous language** — engineers and domain experts share vocabulary.
- **Bounded context** — the model has clear boundaries; same word can mean different things in different contexts.
- **Aggregates** — clusters of entities treated as a unit for consistency.
- **Domain events** — first-class things in the model.

DDD provides the conceptual map for slicing a system into services: bounded contexts often align with service boundaries.

### 33.4 In Practice

You don't have to be religious about any of these. The valuable insights are:

- Keep business logic separate from IO.
- Push IO to the edges.
- Make dependencies explicit.
- Prefer named interfaces over concrete types where it helps testability.

---

## 34. Cell-Based Architecture

A pattern from AWS, Slack, Salesforce: partition the entire system (not just data) into independent **cells**, each capable of serving a fraction of users end-to-end. A cell has its own load balancer, services, databases, caches.

### 34.1 Goals

- **Bounded blast radius.** A bug, a poison customer, a load spike — the damage is confined to the cell, not the whole system.
- **Predictable scaling.** Add cells, not just nodes.
- **Easier rollouts.** Deploy to one cell first; observe; expand.

### 34.2 Cell Routing

A router (thin, stateless, well-tested) decides which cell to send each request to. Often based on customer/tenant ID. Routing decisions can be:
- Static (hash of tenant ID).
- Dynamic (load-aware).
- Migration-aware (during tenant moves between cells).

### 34.3 Shuffle Sharding

A clever variant: each user is mapped to a *random subset* of cells (e.g., 2 of 8). Two users sharing one cell with high probability don't share both. So one bad user can degrade ~`1/N` of others, instead of all of them on a single shared cell.

Used in Route 53, AWS infrastructure, Lambda. The math is beautiful: with even small subset sizes, the probability of two specific users colliding completely shrinks dramatically.

### 34.4 When to Use

When fault isolation is a top priority and per-customer fairness matters more than peak utilization. SaaS multi-tenancy, regulated industries, high-availability infra services.

---

## 35. Multi-Tenancy Patterns

How do you serve many customers ("tenants") from one system?

### 35.1 Models

- **Shared everything (pooled).** All tenants share infrastructure and data stores; tenant ID is a column. Cheapest. Hardest to isolate noisy neighbors and meet compliance.
- **Shared infrastructure, isolated data.** Same compute; per-tenant database/schema. Common compromise.
- **Silo (dedicated stack).** Each tenant gets their own infrastructure. Most isolated; most expensive.
- **Bridge / Hybrid.** Different tiers (free → silo for enterprise).

### 35.2 Concerns

- **Data isolation.** Bug or bad query must not leak across tenants. Use Postgres RLS, schema-per-tenant, or strong middleware.
- **Noisy neighbors.** One tenant's load shouldn't degrade another's. Per-tenant rate limits, shuffle sharding, queue isolation.
- **Provisioning.** Onboarding a new tenant should be cheap and automated.
- **Compliance.** Some tenants need data in specific regions, encryption with their keys (BYOK), audit logs.

### 35.3 Tenant ID Everywhere

A practical rule: **every row, every cache key, every log line, every metric should carry a tenant ID.** It's the single most useful design decision in multi-tenant systems.

---

## 36. API Design

Your APIs are your interface contract with the world (or with other teams). Designing them well pays for itself many times over.

### 36.1 REST

Resource-oriented HTTP. URIs identify resources; HTTP methods define operations. JSON bodies. Hypermedia (HATEOAS) is rarely strictly applied in practice; "RESTful" usually means "JSON over HTTP with conventional methods and status codes."

Strengths: ubiquitous, familiar, cacheable (HTTP semantics), easy to debug (curl).  
Weaknesses: chatty (multiple round trips for related data), versioning is messy, no schema by default.

### 36.2 GraphQL

Single endpoint; clients send a query specifying exactly what they want. Server resolves fields. Strong typing via the schema.

Strengths: clients fetch exactly what they need; reduces round trips; introspection makes tooling great.  
Weaknesses: caching is harder than REST; complexity of resolvers; risk of expensive queries (need depth limiting, persisted queries, query cost analysis).

Used heavily by GitHub, Shopify, Facebook (origin).

### 36.3 gRPC

HTTP/2 + Protocol Buffers. Strongly typed schemas; code generation in many languages; bidirectional streaming.

Strengths: fast (binary, multiplexed), strong contracts, great for service-to-service.  
Weaknesses: harder to debug (binary), browser support requires gRPC-Web or a proxy, not as ubiquitous as REST.

The default for internal microservice communication in modern stacks.

### 36.4 WebSockets

Long-lived bidirectional connection; arbitrary framed messages.

Use cases: chat, live collaboration, real-time games, live data feeds.

Considerations: connection state lives somewhere; horizontal scale requires either sticky sessions, a pub/sub backplane (Redis pub/sub, Kafka), or a connection-aware ingress (e.g., an edge router that pins to the right backend).

### 36.5 Server-Sent Events (SSE)

One-way (server → client) streaming over HTTP. Simpler than WebSockets, automatic reconnect, plays nicely with HTTP infrastructure. Great for AI streaming responses (LLM output token-by-token), notifications, dashboards.

### 36.6 Webhooks

Server-to-server callbacks via HTTP. "When X happens in our system, we POST to your URL." Used by Stripe, GitHub, Slack.

Best practices: HMAC-sign the payloads (so receiver can verify it's from you), retry with exponential backoff on non-2xx, support endpoint configuration with rotation, dedup on receiver side (idempotency keys), document delivery semantics.

### 36.7 API Versioning

Every public API needs a versioning strategy:
- **URI versioning** — `/v1/...`, `/v2/...`. Most explicit, easiest for clients.
- **Header versioning** — `Accept: application/vnd.example.v2+json`. Cleaner URIs.
- **Query parameter** — `?version=2`. Easy but ugly.
- **No versioning, always backward compatible.** GraphQL's preferred model: only additive changes.

Pick one and stick with it.

### 36.8 Pagination

Critical for any list endpoint. Three styles:

- **Offset / page-based** — `?page=3&size=20`. Simple. Bad for moving data (items shift; user sees duplicates). `OFFSET` in SQL is also slow on large offsets.
- **Cursor-based** — `?cursor=abc123`. Server returns an opaque cursor; client passes it back. Robust; slightly more complex.
- **Time-based** — `?since=2025-01-01T00:00:00Z`. Useful for change feeds.

Cursor-based is usually best for production APIs.

### 36.9 Idempotency

Mutating endpoints (POST in particular) should accept an `Idempotency-Key` header. Same key + same request = same response (without re-executing). The classic Stripe pattern, now widely adopted.

### 36.10 Rate Limiting and Quotas

Every public API needs them. Cover in §40.

### 36.11 Errors

Consistent error responses are kindness to your users. RFC 7807 (Problem Details) provides a JSON format. Always include:
- A machine-readable error code (`invalid_argument`, not just "400 Bad Request").
- A human-readable message.
- A correlation/request ID (for support).
- Optional structured details.

---

# Part 4 — Reliability

A system is reliable when it does the right thing, in the right time, despite the inevitability of failures. This part is about engineering for that inevitability.

## 37. Failure Modes in Distributed Systems

Before fixing, understand. Distributed systems fail in distinctive ways.

**Crash failure.** A process stops. The cleanest failure mode. Detect via timeouts/health, redirect traffic.

**Omission failure.** A process is alive but drops some messages or fails to process some requests. Worse than crash because it hides.

**Performance failure (slow / "gray failure").** The process responds, but slowly. The most insidious failure mode; health checks pass; clients pile up. **A slow node is often worse than a dead one** because dead nodes get removed, slow nodes drag everyone down with them.

**Network partition.** Some nodes can't talk to others. May be one-way (asymmetric). Detection is fundamentally ambiguous (you can't distinguish from slow + dead).

**Byzantine failure.** A process behaves incorrectly or maliciously — corrupted memory, bad code, attacker control. Most non-blockchain systems trust their nodes and don't defend against this.

**Cascading failure.** One service degrading causes its callers to retry, increasing load on other services, causing them to degrade. The big-system death spiral.

**Metastable failure.** The system enters a degraded state and stays there even after the trigger is gone. (E.g., a brief overload causes retries that keep the system at saturation indefinitely.) The deeply terrifying ones; usually require manual intervention.

---

## 38. Retries, Timeouts, Backoff, Jitter

The simplest fault-tolerance primitive — and often misused.

### 38.1 Timeouts

**Every network call needs a timeout.** A call without one waits forever, holds threads/connections, propagates congestion.

Set timeouts based on:
- The downstream's `p99.9` latency, plus headroom.
- Your overall request budget. If your endpoint must respond in 1s and you call 3 services, each can't take 800 ms.
- The caller's tolerance, not the callee's average.

Multiple layers of timeouts must be consistent. If your DB driver has a 60s timeout but your service has a 5s timeout, the DB connection still leaks.

### 38.2 Retries

When a call fails, retry... maybe.

**Retry only on transient failures.** Network errors, 5xx, timeouts — yes. 4xx errors (especially 400, 401, 403, 404) — no, they'll fail again. Validation errors — definitely no.

**Retry-Safe operations.** Only idempotent operations can be safely retried. GET? Sure. POST? Only with idempotency keys. PUT/DELETE? Idempotent by definition (re-deleting an already-deleted resource should be a no-op).

**Limit retries.** Cap at 2–3 retries. More just amplifies load during outages.

**Cap concurrent retries.** A retry budget — limit retries to, say, 10% of the request rate. Otherwise during partial outages you can double or triple traffic to a struggling service.

### 38.3 Exponential Backoff

Don't retry immediately. Wait `b * 2^n` for the n-th retry (cap at some max). Gives the failing service time to recover.

### 38.4 Jitter

Without jitter, all retries from many clients land at the same time — a thundering herd. **Always add jitter.**

```
backoff = min(cap, random_between(base, base * 2^attempt))
```

This is "full jitter." Variants exist (decorrelated jitter, equal jitter); full jitter is fine for most cases.

### 38.5 Idempotency Keys

Pass a unique key with mutating requests. The server stores `(idempotency_key → response)` for some window (24 hours typical). Same key arrives → return cached response without re-executing. Works seamlessly with retries.

---

## 39. Circuit Breakers, Bulkheads, Hedging

### 39.1 Circuit Breaker

Borrowed from electrical engineering. When a downstream is failing, stop calling it for a while; fail fast locally.

States:
- **Closed** — normal, traffic flows.
- **Open** — failure threshold tripped; calls fail immediately without trying.
- **Half-open** — after a cool-down, allow a trickle of calls; if they succeed, close; if they fail, re-open.

Without a circuit breaker, a slow downstream causes calls to pile up, threads to block, callers to OOM. With one, the failing dependency is excised quickly and the system fails predictably.

Trip conditions: error rate > X% over the last Y requests, or > Z consecutive failures.

Libraries: Hystrix (legacy), Resilience4j (JVM), Polly (.NET), Envoy / Istio for service-mesh-level circuit breakers.

### 39.2 Bulkheads

Isolate resources so that a failure in one area doesn't drown others. Named after ship compartments.

Examples:
- **Thread pools per dependency.** Slow dependency exhausts its pool, not all threads.
- **Connection pools per dependency.**
- **Separate queues per priority class.**
- **Cell-based architecture** (§34) is a form of bulkhead.

### 39.3 Hedged Requests

For tail-latency-sensitive paths: send the request to two backends; whichever responds first wins; cancel the other. (Or: send to one, after `p95` time send a duplicate.)

Burns more capacity (~5%) but slashes tail latency. Used heavily at Google for Search and other low-latency services.

### 39.4 Load Shedding

When overloaded, drop low-priority work fast rather than serving everyone slowly. Examples:
- Return 503 with `Retry-After` for low-priority traffic when `p99` latency rises.
- Prioritize logged-in users over anonymous, paying over free.

Better to fail some requests cleanly than to bring everyone to a crawl.

---

## 40. Rate Limiting and Throttling

Limits the rate of incoming requests, per some key (IP, user, API key, tenant).

### 40.1 Why

- Protect against abuse (scrapers, bots).
- Prevent any one tenant from hogging shared resources.
- Enforce paid plan limits.
- Smooth traffic into downstreams.

### 40.2 Algorithms

**Fixed window.** Count requests in each clock window (e.g., per minute). Simple. Burst at window boundaries (`n` at end of one window + `n` at start of next = `2n`).

**Sliding window log.** Store timestamps of all requests; count those in the last N seconds. Accurate; expensive (memory).

**Sliding window counter.** Two fixed-window counters, weighted by overlap. Approximation, low memory, common compromise.

**Token bucket.** Bucket holds up to `B` tokens; refills at rate `r` tokens/sec; each request consumes 1 (or more) tokens. Allows bursts up to `B`, sustained rate `r`. The most common algorithm in production.

**Leaky bucket.** Requests queue in a bucket; drained at rate `r`. Excess overflows. Smooths bursts at the cost of latency.

### 40.3 Distributed Rate Limiting

Single-node rate limiting is trivial. Distributing across instances is harder; you need a shared counter.

Approaches:
- **Centralized counter** (Redis `INCR` with `EXPIRE`). Works for moderate scale; Redis is the bottleneck.
- **Lua scripts in Redis** for atomic check-and-increment.
- **Token-bucket per shard with reconciliation.**
- **Approximate, gossip-based** for very high throughput.

Cloud-native: AWS API Gateway throttling, Cloudflare rate limiting, Envoy rate-limit service, Stripe's `Rate-Limit` library (uses Redis).

### 40.4 Returning Limits to Clients

Standard response: `429 Too Many Requests` with headers:
- `X-RateLimit-Limit: 1000`
- `X-RateLimit-Remaining: 23`
- `X-RateLimit-Reset: 1700000000`
- `Retry-After: 30`

Be a good citizen: tell clients the limit and when they can try again.

---

## 41. Backpressure and Flow Control

Backpressure is the ability of a slow consumer to slow down a producer. Without it, fast producers and slow consumers cause unbounded queues, memory growth, and eventual collapse.

### 41.1 Why It Matters

Imagine a service that reads from Kafka, processes each message, writes to a database. If the database slows, the processing slows, but Kafka keeps offering messages. Without backpressure (and Kafka is naturally back-pressured by consumer pull), you'd OOM.

In synchronous systems, backpressure manifests as natural slowness — the producer waits because the consumer is slow. In asynchronous systems with queues, you must engineer it.

### 41.2 Mechanisms

- **Bounded queues.** Block (or reject) the producer when the queue is full.
- **Reactive Streams / `Flow`** (Java) / `tokio::sync::mpsc` (Rust) — explicit demand signaling between producer and consumer.
- **HTTP/2 flow control** — built-in window-based flow control per stream.
- **TCP flow control** — built into the protocol.
- **Token-based work admission** — workers pull when they have capacity, instead of being pushed.

### 41.3 Drop vs. Block

When backpressure kicks in:
- **Block** — producer waits. Stops the world but preserves data.
- **Drop newest** — when queue is full, reject incoming. Keeps the system responsive but loses data.
- **Drop oldest** — when queue is full, evict oldest items. Often the right choice for stale data (real-time metrics, logs).
- **Sample** — keep a fraction.
- **Compress / coalesce** — merge similar items.

The right strategy depends on data semantics. Logs you might drop. Payments you must not.

---

## 42. Idempotency and Exactly-Once Semantics

We've mentioned idempotency repeatedly. It deserves its own treatment because it's the single most important property for building reliable distributed systems.

### 42.1 Idempotent Operations

`f(f(x)) = f(x)`. Calling the operation twice has the same effect as calling it once.

Examples:
- `SET x = 5` (idempotent).
- `INCREMENT x` (NOT idempotent).
- `INSERT IF NOT EXISTS` (idempotent).
- `INSERT ... ON CONFLICT DO NOTHING` (idempotent).
- HTTP `PUT` (idempotent by spec).
- HTTP `POST` (NOT idempotent unless designed to be).

### 42.2 How to Make Things Idempotent

- **Deterministic IDs.** Generate the entity's ID at the client; if it's already in the database, the second insert is a no-op.
- **Idempotency keys.** Server stores `(key → result)` for a window. Same key → return same result.
- **Conditional updates.** `UPDATE ... WHERE version = N`; only the first wins; second sees no rows updated, knows it's a no-op.
- **Upserts.** `INSERT ... ON CONFLICT UPDATE`.
- **Version vectors / optimistic locking.** Clients pass the version they read; updates fail if version changed.

### 42.3 Exactly-Once: The Honest Truth

True end-to-end exactly-once delivery is impossible across a network. (Two Generals Problem.) What you can have: at-least-once delivery + idempotent processing = effectively-exactly-once.

When you hear "exactly-once" from a vendor, ask: in what scope? Kafka's "exactly-once semantics" means within Kafka writes. End-to-end requires you to make your sinks idempotent.

---

## 43. Disaster Recovery, Multi-Region, RPO/RTO

A datacenter is going to burn down, flood, or lose power. A region is going to have an outage. Plan accordingly.

### 43.1 Definitions

- **RPO (Recovery Point Objective)** — how much data are you willing to lose? Measured in time. RPO = 0 means "no data loss"; RPO = 1 hour means "lose up to 1 hour of recent data."
- **RTO (Recovery Time Objective)** — how long can you be down? RTO = 5 minutes means "detected, failed over, serving in 5 minutes."

These two numbers drive every other decision. RPO=0/RTO=0 (zero data loss, zero downtime) is staggeringly expensive; relax either axis and costs drop fast.

### 43.2 Multi-Region Patterns

**Active-passive (cold/warm standby).**
- DR region has data replicas, infrastructure provisioned (warm) or scripted (cold).
- Failover is manual or semi-automated.
- RPO depends on replication lag (typically seconds–minutes for async); RTO is minutes-hours.
- Cheaper. Used for "we can afford some downtime."

**Active-active.**
- Both regions serve traffic.
- Bidirectional replication or partitioned data (each region owns some users).
- RPO can be near-zero; RTO can be near-zero (just shift traffic).
- Hard. Conflict resolution, global routing, consistency model.

**Pilot light.**
- Critical infra always running in DR (data replication, key services), the rest is provisioned on failover.
- Compromise between cold standby and hot.

### 43.3 What to Replicate

- **Application state** (databases, object storage, caches if regenerable).
- **Configuration and secrets** (often forgotten).
- **DNS / global LB config** (you need to be able to flip traffic).
- **CI/CD** (you need to deploy fixes during an outage).

Object storage: cross-region replication, often async (S3 CRR has some-minute latency).
Databases: cross-region replicas (built-in for many managed offerings — Aurora Global, Spanner, CockroachDB).

### 43.4 Test the Failover

A DR plan that's never been tested doesn't work. **GameDays** (deliberate failover drills) are the only way to know.

Common discoveries during the first GameDay:
- DNS TTLs too high.
- Secrets in DR region stale.
- Some service had a hidden dep on the primary region.
- The runbook has typos.
- The on-call list is out of date.

### 43.5 Backups

Replication is not backup. Replication propagates corruption and deletes immediately. Backups are point-in-time snapshots that can recover from "we accidentally dropped the table."

- Point-in-time recovery (PITR) for databases.
- Object versioning + lifecycle for blob storage.
- Regular restore tests. (Backups you've never restored from don't work.)

### 43.6 Multi-Cloud

Sometimes regulatory or risk-tolerance demands surviving the loss of a *cloud provider*. Hard. Most "multi-cloud" implementations are partial (DNS multi-cloud, or just multi-region within one cloud). True multi-cloud requires significant abstraction effort and gives up cloud-specific features.

---

## 44. Observability

Observability is your ability to reason about what a system is doing from its outputs. The three classic pillars: **logs, metrics, traces.** Modern stacks add a fourth: **profiles.**

### 44.1 Logs

Discrete events with timestamp + structured fields. Most expressive (any data); most expensive (volume).

Best practices:
- **Structured (JSON).** Don't write `"User 42 placed order 7 for $50"`. Write `{"event": "order_placed", "user_id": 42, "order_id": 7, "amount": 50}`.
- **Levels.** `DEBUG`, `INFO`, `WARN`, `ERROR`. Production usually runs at `INFO`; aggregators may sample `DEBUG`.
- **Correlation IDs.** Every log line includes the request/trace ID so you can follow a request across services.
- **Sampling.** At hyperscale, log everything is too expensive; sample non-error logs.
- **PII discipline.** Don't log secrets, tokens, full PII.

Stacks: ELK (Elasticsearch + Logstash + Kibana), OpenSearch, Grafana Loki, Datadog Logs, Splunk, ClickHouse-based (HyperDX, SigNoz).

### 44.2 Metrics

Numerical aggregates over time. Cheap (small footprint), great for dashboards and alerts, lossy (can't drill down to individual events).

Types:
- **Counter** — monotonically increasing (request count).
- **Gauge** — point-in-time value (memory used).
- **Histogram** — distribution; buckets to compute percentiles.
- **Summary** — like histogram but quantiles computed on agent.

The de facto standard: **Prometheus** for collection (pull-based), **Grafana** for visualization, **Alertmanager** for alerts.

The four golden signals (Google SRE book): **latency, traffic, errors, saturation**. If you measure these for every service, you'll catch most problems.

The RED method: **Rate, Errors, Duration** (per request).
The USE method: **Utilization, Saturation, Errors** (per resource).

### 44.3 Traces

Trace = the distributed call graph of a single request, with timing per span. Lets you see where time goes across services.

Standards:
- **OpenTelemetry** — the cross-vendor standard for traces, metrics, logs. Use it.
- Trace propagation via W3C Trace Context headers (`traceparent`, `tracestate`).

Tools: Jaeger, Tempo, Zipkin, Honeycomb, Datadog APM.

Without traces, debugging cross-service problems is archaeology. With traces, you see the waterfall and the slow span jumps out.

### 44.4 Profiles (Continuous Profiling)

Always-on, low-overhead CPU/memory profiling. Tools: Pyroscope, Parca, Datadog Continuous Profiler.

Lets you ask "where is my CPU going?" and answer with flame graphs from production. Increasingly standard at scale.

### 44.5 Wide Events (the "Honeycomb model")

Instead of separate logs/metrics/traces, emit one rich event per unit of work with all relevant context (user ID, tenant, latency, downstream timings, error if any). Query with high-cardinality filters in tools designed for it (Honeycomb, ClickHouse).

The argument: the artificial split of logs/metrics/traces is partly a tooling artifact. With the right backend, wide events do all three jobs.

### 44.6 SLO Math

Don't alert on every error. Alert on burn rate of error budget (covered next).

---

## 45. SRE: SLI, SLO, SLA, Error Budgets

Site Reliability Engineering — Google's discipline of running production systems. Several core ideas have crossed into the mainstream.

### 45.1 Definitions

- **SLI (Service Level Indicator)** — a measurement. "Fraction of requests served in < 200 ms."
- **SLO (Service Level Objective)** — a target for an SLI. "99.9% of requests served in < 200 ms over 30 days."
- **SLA (Service Level Agreement)** — a contractual promise to customers, typically slightly looser than SLO with consequences if missed.

### 45.2 Error Budgets

If your SLO is 99.9% over 30 days, you have a 0.1% error budget — about 43 minutes of total downtime per month.

The error budget is the central management tool of SRE:
- If you're well within budget, you can deploy aggressively, take risks.
- If you've burned the budget, slow down. Freeze risky deploys. Invest in reliability.

This neatly aligns dev velocity and reliability. Reliability isn't binary; it's a continuous trade-off, and the budget makes it explicit.

### 45.3 Multiwindow / Multiburn-rate Alerts

Don't alert "errors > 0.1%" — that would be constant noise. Alert on **burn rate of the error budget**. Common pattern (Google SRE Workbook):
- Page if you'd burn 2% of the monthly budget in 1 hour AND in 5 minutes.
- Lower-urgency alert for slower burn (10% in 6 hours).

### 45.4 Toil

Repetitive operational work without lasting value. SRE rule of thumb: cap toil at 50% of an SRE's time; the rest is engineering to eliminate toil. Without this, SRE becomes a glorified ops team.

### 45.5 Postmortems / Blameless Reviews

Every incident gets a written postmortem. Blameless: focus on systemic causes, not individuals. Output: action items with owners. The cultural backbone of resilient organizations.

---

## 46. Chaos Engineering

Coined at Netflix. The principle: **the best way to be confident a system tolerates failures is to deliberately cause failures and watch.**

### 46.1 Principles

- Start with a hypothesis ("if we kill an AZ, traffic shifts and `p99` stays under 500 ms").
- Define a steady-state metric.
- Inject a controlled failure.
- Observe; if reality differs from hypothesis, fix the system or the assumption.

### 46.2 Tools

- **Chaos Monkey** (the original Netflix tool — randomly kill instances).
- **Gremlin** — commercial chaos platform.
- **AWS Fault Injection Service**.
- **Litmus** — Kubernetes-native.

### 46.3 Practice

- Start in pre-prod. Earn confidence.
- GameDays — scheduled, controlled exercises with the team.
- Eventually run continuously in production at small blast radius.
- Always have a kill switch.

The goal isn't to break things; it's to learn what you don't know about your system before customers do.

---

## 47. Capacity Planning

How do you make sure the system can handle next year's traffic? Last quarter's product launch?

### 47.1 Inputs

- Current load (RPS, data volume, write QPS).
- Growth projections (new users, new features, marketing spikes).
- Headroom required (peak vs. average; 2× peak is reasonable).
- Per-instance limits (RPS, RAM, CPU, IOPS).

### 47.2 Forecasting

Simple but underused: track historical growth, fit a curve, project. For event-driven spikes (Black Friday), look at last year's curve and apply growth.

### 47.3 Load Testing

Before scaling, test. Tools: k6, Gatling, Locust, JMeter, Vegeta.

Tests:
- **Load test** — sustained expected peak.
- **Stress test** — push past peak, see breakage.
- **Spike test** — sudden traffic burst.
- **Soak test** — long-running at moderate load (catches memory leaks, slow degradation).

Run against production-like environments. Numbers from a single laptop don't generalize.

### 47.4 Autoscaling

Cloud-native systems autoscale based on metrics:
- **Reactive** — scale on CPU / RPS thresholds. Lag matters; can be slow.
- **Predictive** — scale on forecasted load. AWS, GCP have ML-based predictive scaling.
- **Scheduled** — scale up before known peaks (8 AM scale-up).

Autoscaling has limits: cold starts, dependency limits (DB connections), misbehaving feedback loops. Test it.

### 47.5 Headroom

Run with enough headroom that a single failure (lose an AZ, a service) doesn't push you over capacity. The standard is N+1 or 2N for AZ-level redundancy.

---

# Part 5 — Security

Security isn't a layer you add at the end. It's a property the architecture either has or doesn't. This part covers the security primitives every architect must know.

## 48. Authentication

**Authentication (AuthN)** answers "who are you?" Distinct from **Authorization (AuthZ)**: "what may you do?"

### 48.1 Sessions vs. Tokens

**Session-based.** Server creates a session record on login; sets a session cookie referencing it. Every request, server looks up the session. Easy to revoke; requires shared session storage in distributed systems (Redis is typical).

**Token-based.** Server issues a signed/encrypted token (e.g., JWT); client sends it with each request. Stateless on the server side (modulo revocation). Easier horizontal scale; revocation is trickier.

In practice modern apps use both: a session cookie for the browser app, OAuth tokens for APIs and third-party access.

### 48.2 JWT (JSON Web Tokens)

A JWT is `base64(header).base64(payload).base64(signature)`. Header declares the algorithm; payload contains claims (`sub`, `exp`, `iss`, `aud`, custom claims); signature proves the issuer.

Strengths: stateless, self-contained, easy to pass in `Authorization: Bearer ...` header.

Pitfalls (real ones, in the wild):
- **`alg: none`** — old vulnerability where some libraries accepted unsigned tokens. Always validate the algorithm explicitly.
- **HS256 vs RS256 confusion** — if your code accepts both and the public key is ever used as an HMAC secret, you have a vulnerability. Pin the algorithm.
- **Long-lived access tokens are dangerous.** Compromised token = compromised session until expiry. Use short access tokens (5–15 min) + long-lived refresh tokens.
- **Storing tokens in `localStorage`** exposes them to XSS. Prefer `HttpOnly` cookies for browser apps.
- **Revocation.** Stateless tokens can't be revoked easily; you need a denylist or short TTLs.

### 48.3 OAuth 2.0 / 2.1

OAuth solves: "how does service A let service B access my data on service C, without B getting my C password?" The classic three-legged flow.

OAuth 2.1 (consolidating drafts) is the modern flavor. Key flows:

- **Authorization Code with PKCE** — the right default for almost everything (SPAs, mobile, server-side). PKCE (Proof Key for Code Exchange) prevents authorization code interception.
- **Client Credentials** — for service-to-service (no user). Service authenticates with its own credentials.
- **Refresh token** — long-lived token used to get new access tokens.
- **Device authorization grant** — for input-constrained devices (TVs, CLIs). User authorizes on a phone.

OAuth 2.1 deprecates the **implicit flow** (insecure for SPAs) and **resource owner password grant** (defeats the purpose of OAuth).

### 48.4 OpenID Connect (OIDC)

OAuth 2.0 is for *authorization*; OpenID Connect adds *authentication* on top. The IdP issues an **ID token** (a JWT) describing the user. Used for "Sign in with Google/Microsoft/Apple/etc."

### 48.5 SAML

The enterprise SSO standard. XML-based, older, dominant in B2B. Most apps need to support it for enterprise deals. Use a library; never roll your own SAML.

### 48.6 Passkeys / WebAuthn

The password-killer. Uses public-key crypto: device generates a keypair per site; biometric/PIN unlocks the private key for signing the auth challenge. Phishing-resistant by design (the key is bound to the origin).

Supported in all modern browsers and OSes. Adopting passkeys is now state-of-the-art for consumer auth.

### 48.7 mTLS

Mutual TLS: server and client both authenticate via certificates. The standard for service-to-service in zero-trust architectures.

In a service mesh, sidecars handle mTLS automatically using a service identity provisioned by the control plane.

### 48.8 API Keys

Long-lived, often plaintext-equivalent shared secrets. Convenient for server-to-server, machine-to-machine. Best practice: never log them, allow rotation without downtime, scope them (read-only, per-resource), tie to specific source IPs when possible.

For higher security, prefer signed requests (e.g., AWS SigV4) — the key is never sent over the wire; instead, you sign each request.

### 48.9 MFA / 2FA

Beyond passwords: TOTP (authenticator apps), SMS (insecure but better than nothing), push notifications, hardware keys (YubiKey), passkeys. Required by sensible security practice for any privileged or human-facing access.

### 48.10 Token Binding & Modern Patterns

For high-security applications, tokens should be **bound** to a context — the client that requested them, not bearer-only. **DPoP (RFC 9449)** binds tokens to a client-held key; the client proves possession of the key on each call. Prevents stolen-token replay.

For request integrity (not just transport), **HTTP Message Signatures (RFC 9421)** plus `Content-Digest` provide application-layer authenticity. These two are independent: DPoP authenticates *the client*; signatures prove *the request body wasn't tampered*.

These patterns are increasingly important in agentic AI systems and high-assurance APIs (financial, healthcare).

---

## 49. Authorization

Once you know who someone is, what may they do?

### 49.1 RBAC (Role-Based Access Control)

Users have **roles**; roles have **permissions**. `admin → can_delete_user`. Easy to reason about; widely used.

Limits: explosion of roles ("admin who can delete this specific tenant's data"); hard to express attribute-based rules.

### 49.2 ABAC (Attribute-Based Access Control)

Decisions are functions of attributes: subject (user), action, resource, environment. "User can edit document if user.department == document.department AND time is during business hours."

More expressive; harder to reason about.

### 49.3 ReBAC (Relationship-Based Access Control)

Access is based on relationships in a graph. "Alice can read this doc because she's in the team that owns the folder it's in." Inspired by Google Zanzibar (the system behind Drive, YouTube, Cloud).

Tools: **OpenFGA** (open-source Zanzibar-style), **SpiceDB** (Authzed), **Permify**.

ReBAC excels at hierarchical/social authorization (folders, teams, friend-of-friend).

### 49.4 PBAC / Policy as Code

Policy as Code: write policies in a dedicated DSL, evaluate centrally. **OPA (Open Policy Agent)** with Rego is the dominant tool. Used for Kubernetes admission control, microservice authorization, IaC validation.

Cedar (AWS) and Rego are the two languages worth knowing.

### 49.5 Architectural Pattern

The standard pattern: **Policy Decision Point (PDP)** + **Policy Enforcement Point (PEP)**.

- **PEP** sits in the request path; for each request, asks the PDP "is this allowed?"
- **PDP** evaluates policy.
- **PIP (Policy Information Point)** provides attributes the PDP needs.
- **PAP (Policy Administration Point)** is where humans write/manage policies.

Centralizing PDP keeps policy consistent and auditable. Local caching of decisions matters for latency.

### 49.6 Authorization in Microservices

Each service makes its own authorization decision (defense in depth). The gateway can do coarse checks ("is the user authenticated, do they have *some* access?") but the service must decide on its own data.

A common modern pattern: pass an authenticated user context (signed) along the call chain; each service uses it as input to its own policy decisions.

---

## 50. Transport Security

### 50.1 TLS

Already covered the basics in §3.7. For configuration:

- **Use TLS 1.3.** TLS 1.2 is acceptable; older versions are deprecated.
- **Use modern ciphers.** ECDHE for key exchange (forward secrecy); AES-GCM or ChaCha20-Poly1305 for symmetric.
- **HSTS** (HTTP Strict Transport Security) — tells browsers "always use HTTPS for this domain for the next year." Prevents downgrade attacks.
- **Certificate transparency.** All public certs are logged; you can monitor for misissuance.
- **Automate certificate management.** Let's Encrypt + cert-manager (Kubernetes), AWS ACM. Manual cert renewals cause outages.

### 50.2 mTLS

Required for zero-trust. Service mesh handles automatically. SPIFFE/SPIRE provides a vendor-neutral standard for workload identity (`spiffe://example.com/ns/default/sa/myservice`).

### 50.3 Certificate Hygiene

- Rotate regularly.
- Short-lived (days, not years) where automation allows.
- Detect expiring certs *before* expiry. Outages from expired certs are common and embarrassing.

---

## 51. Secrets Management

Secrets are anything you can't write in source code: API keys, DB passwords, signing keys, OAuth client secrets, third-party tokens.

### 51.1 Where Not to Put Secrets

- Source repositories (you'd be amazed).
- Environment variables that get logged.
- Container images.
- Dockerfile.
- CI/CD configs in the repo.

### 51.2 Secret Stores

- **HashiCorp Vault** — open-source, dynamic secrets (DB creds generated per session), strong RBAC.
- **AWS Secrets Manager** / **Parameter Store** / **KMS**.
- **GCP Secret Manager** / **KMS**.
- **Azure Key Vault**.
- **External Secrets Operator** in Kubernetes (syncs secrets from Vault/cloud into K8s Secrets).

### 51.3 Envelope Encryption

You don't encrypt large data with a "master key"; you encrypt it with a **data key**, then encrypt the data key with the master. Master key lives in KMS / HSM and never leaves; data keys are short-lived.

This is how cloud KMS, Vault, and most field-level encryption schemes work.

### 51.4 Rotating Secrets

A secret you can't rotate is a vulnerability. Plan for rotation:
- Multiple valid versions during overlap.
- Automated rotation where possible (DB creds via Vault dynamic secrets).
- Audit rotations.

### 51.5 SOPS, sealed-secrets

For the GitOps pattern (configs in git), tools encrypt secrets at rest:
- **SOPS** — encrypts YAML/JSON, decrypts via KMS / age / GPG.
- **Sealed Secrets** (Bitnami) — Kubernetes-specific.

---

## 52. Zero Trust Architecture

The traditional perimeter model: VPN in, then trust everything inside. Zero trust: **trust nothing by default; authenticate and authorize every request**, even on internal networks.

### 52.1 Principles

- **Never trust the network.** Every service-to-service call must authenticate.
- **Least privilege.** Users and services get the minimum needed.
- **Verify continuously.** A user authenticated at login isn't trusted forever; risk-based reauthentication.
- **Assume breach.** Design so that compromise of one service doesn't grant access to all.

### 52.2 Building Blocks

- **Identity-aware proxies** — Google's BeyondCorp, Cloudflare Access, AWS Verified Access. Replace VPN; verify identity + device posture per request.
- **Service mesh + mTLS + policy** — for internal service-to-service.
- **SPIFFE/SPIRE** — workload identity standard.
- **Just-in-time access** — humans get elevated access for a window, not permanently.

Zero trust is more journey than destination. The perimeter never goes away entirely; it shrinks until it's per-request.

---

## 53. DDoS, WAF, Bot Management

### 53.1 DDoS Mitigation

DDoS attacks come in flavors:
- **Volumetric** — saturate the link. Mitigated by sheer capacity (CDN, anycast).
- **Protocol** — SYN floods, fragment floods. Mitigated by stateful filtering, SYN cookies.
- **Application-layer** — slow loris, resource exhaustion, expensive endpoints. Mitigated by WAF, rate limiting, hardening.

Practical mitigation: put a major CDN/edge provider (Cloudflare, AWS Shield, GCP Cloud Armor, Akamai) in front. Their edge has more capacity than any DDoS.

### 53.2 WAF (Web Application Firewall)

Pattern-matching firewall for HTTP. Blocks SQLi, XSS, path traversal, etc. Examples: Cloudflare WAF, AWS WAF, ModSecurity.

WAFs have false positives; deploy in observe mode first. They're a layer of defense, not a substitute for secure code.

### 53.3 Bot Management

Distinguish humans from bots (good and bad bots). Techniques: device fingerprinting, behavior analysis, CAPTCHAs (the modern variants — Cloudflare Turnstile, hCaptcha, Google reCAPTCHA), token-based attestation (Apple's Private Access Tokens, Cloudflare PAT).

---

## 54. Data Security

### 54.1 Encryption at Rest

All persistent storage should be encrypted at rest. In cloud: typically free or near-free (S3, EBS, RDS, etc. all support transparent encryption).

For higher requirements: **bring-your-own-key (BYOK)** or **hold-your-own-key (HYOK)** — customer-managed keys in their KMS.

### 54.2 Encryption in Transit

TLS everywhere. mTLS for service-to-service.

### 54.3 Field-Level Encryption

For very sensitive fields (PII, payment info), encrypt at the field level. The DB sees only ciphertext; only the application (with the key) can decrypt. Limits exposure if DB is breached.

### 54.4 Tokenization

Replace sensitive values (credit card numbers) with tokens; the real value lives in a vault (the tokenization service). Used heavily in payment systems for PCI scope reduction.

### 54.5 Privacy and PII

- Data minimization: collect only what you need.
- Retention: delete what you don't need.
- Right to deletion (GDPR, CCPA): you must be able to find and delete a user's data on request, including replicas, backups, search indexes, logs.
- Access controls: not every employee needs PII access.
- Differential privacy and anonymization for analytics.

### 54.6 Compliance

A non-exhaustive list of regimes:
- **GDPR** (EU) — privacy.
- **CCPA / CPRA** (California) — privacy.
- **PCI-DSS** — payment cards.
- **HIPAA** — US healthcare.
- **SOC 2** — operational controls (most B2B SaaS).
- **ISO 27001** — security management.
- **FedRAMP** — US government.

Architecture has to enable compliance: data residency, audit logging, access controls, encryption.

---

## 55. Supply Chain Security

You don't just write code. You depend on it.

### 55.1 Dependency Risks

A vulnerability or malicious code in a dependency = a vulnerability in your code. Examples:
- `event-stream` (2018) — a popular npm library was hijacked, used to steal Bitcoin wallets.
- `xz utils` (2024) — a multi-year social-engineering attack to plant a backdoor in a core Linux library.

### 55.2 Mitigations

- **SBOM (Software Bill of Materials).** Know what you depend on. SPDX, CycloneDX formats.
- **Vulnerability scanning.** Trivy, Snyk, Dependabot, Renovate. Continuous scans of code, containers, and IaC.
- **Pin versions / use lockfiles.** Reproducible builds.
- **Least privilege at build time.** Build agents shouldn't have prod credentials.
- **Image signing.** Cosign, Sigstore. Verify what you deploy was built by your pipeline.
- **SLSA framework.** Supply-chain Levels for Software Artifacts. Defines maturity levels for build provenance.

### 55.3 Container Security

- Use minimal base images (`distroless`, Alpine for non-glibc).
- Run as non-root.
- Drop capabilities.
- Read-only root filesystem when possible.
- Scan images.
- Sign images.

---

# Part 6 — Cloud & Infrastructure

The cloud is where modern systems live. This part covers the mental models for cloud platforms, the abstractions they provide, and the operational tooling that makes large-scale systems possible.

## 56. Cloud Service Models

### 56.1 IaaS, PaaS, SaaS, FaaS

A spectrum from "you manage everything" to "managed for you":

- **Bare metal** — physical servers; you manage everything including hardware.
- **IaaS (Infrastructure as a Service)** — VMs, networks, storage. AWS EC2/EBS/VPC, GCP Compute Engine, Azure VMs. You manage OS and up.
- **CaaS (Containers as a Service)** — managed Kubernetes (EKS, GKE, AKS), ECS, Fargate. You manage containers and apps.
- **PaaS (Platform as a Service)** — Heroku, Vercel, Fly.io, App Engine, Cloud Run. You bring code; the platform runs it.
- **FaaS (Function as a Service)** — Lambda, Cloud Functions, Azure Functions. You bring functions; the platform runs them on demand.
- **SaaS (Software as a Service)** — fully managed apps. Salesforce, Workday, Stripe.

Higher up the stack: less ops, less flexibility, often higher unit cost (until scale flips it the other way).

### 56.2 The Build vs Buy Calculus

Architects must constantly decide: do we operate our own X, or rent it?

**Operate yourself when:**
- You have specialized requirements no managed service satisfies.
- Cost at scale dominates (tens of millions of dollars / year).
- You have the expertise and organization to run it well.
- Vendor lock-in is unacceptable.

**Rent (managed) when:**
- The service is undifferentiated heavy lifting.
- Your team's bandwidth is better spent elsewhere.
- The managed service's reliability exceeds yours.
- You're early — speed matters more than cost.

The default for most teams is **rent**. "We need a Kafka" should provoke "have you considered Kinesis / managed Kafka?"

---

## 57. The Major Clouds — Mental Models

### 57.1 AWS

The biggest, oldest, broadest. Started as IaaS, now has thousands of services.

Key services every architect should know:
- **Compute:** EC2 (VMs), ECS / Fargate (containers), Lambda (FaaS), EKS (Kubernetes), Batch.
- **Storage:** S3 (object), EBS (block), EFS (file), Glacier (cold archive).
- **Database:** RDS (managed relational), Aurora (cloud-native MySQL/Postgres), DynamoDB (KV), ElastiCache (Redis/Memcached), Neptune (graph), TimeStream (TSDB), Redshift (warehouse), OpenSearch.
- **Networking:** VPC, Route 53 (DNS), CloudFront (CDN), ELB (load balancers — ALB, NLB, GLB), API Gateway, Direct Connect.
- **Messaging:** SNS (pub/sub), SQS (queues), Kinesis (streams), MSK (managed Kafka), EventBridge (event bus).
- **Security:** IAM, KMS, Secrets Manager, WAF, Shield, GuardDuty, Inspector.
- **Observability:** CloudWatch (logs/metrics), X-Ray (tracing).
- **Data:** Glue (ETL), EMR (Spark/Hadoop), Athena (S3 SQL), Lake Formation.
- **AI/ML:** SageMaker, Bedrock (LLMs).

AWS culture: many small primitives; assemble them yourself; pricing is transparent but complex; documentation can be vast.

### 57.2 GCP

Smaller catalog, often deeper engineering. Born from Google's internal infrastructure.

- **Compute:** Compute Engine, GKE (the most mature managed Kubernetes), Cloud Run (best-in-class container PaaS), Cloud Functions, App Engine.
- **Storage:** Cloud Storage (object), Persistent Disk, Filestore.
- **Database:** Cloud SQL, Spanner (the killer app), Firestore, Bigtable, BigQuery (the OLAP killer app), Memorystore.
- **Networking:** VPC, Cloud DNS, Cloud CDN, Cloud Load Balancing (global anycast).
- **Messaging:** Pub/Sub (truly excellent), Dataflow (streaming), Cloud Tasks.
- **AI/ML:** Vertex AI; Google's own models (Gemini).

GCP strengths: Spanner, BigQuery, networking (Google's global backbone), Kubernetes. Often best for data + ML.

### 57.3 Azure

Microsoft's cloud; deep enterprise integration (Active Directory, Office 365, etc.).

- **Compute:** VMs, AKS, Functions, App Service, Container Instances, Container Apps.
- **Storage:** Blob Storage, Files, Disks.
- **Database:** SQL Database, Cosmos DB (multi-model), PostgreSQL/MySQL Flexible Server, Synapse (warehouse).
- **Networking:** Virtual Network, Front Door (CDN+WAF), Application Gateway, ExpressRoute.
- **Messaging:** Service Bus, Event Hubs, Event Grid.
- **AI/ML:** Azure ML, Azure OpenAI Service.

Azure strengths: enterprise / Microsoft shop integration; OpenAI partnership.

### 57.4 The Other Clouds

- **Cloudflare** — edge-first; fantastic for HTTP-shaped workloads.
- **Oracle Cloud (OCI)** — competitive pricing, strong for Oracle workloads.
- **DigitalOcean / Linode / Hetzner** — simpler, cheaper, smaller catalog. Good for SMBs and startups.
- **Vercel / Netlify / Fly.io / Render** — developer experience-first PaaS layers.

### 57.5 Cloud-Agnostic Principles

- Build on commodity primitives (VMs, K8s, S3-compatible) and use cloud-specific services where the value is enormous.
- Abstract through interfaces (cloud KMS via your own KMS interface, etc.) when portability is real.
- Don't blindly multi-cloud "for portability." It costs significant complexity.

---

## 58. Compute

### 58.1 Virtual Machines

The base unit of cloud compute. Choosing instance types involves trade-offs:
- **General purpose** (m-class) — balanced.
- **Compute-optimized** (c-class) — high CPU/RAM ratio.
- **Memory-optimized** (r/x-class) — high RAM.
- **Storage-optimized** (i/d-class) — local NVMe.
- **GPU/accelerated** — ML, graphics, scientific.
- **Burstable** (t-class on AWS) — cheap baseline + credits for bursts. Watch out for unbounded credit consumption.

Pricing models:
- **On-demand** — pay per second/minute/hour.
- **Reserved / committed-use** — 1- or 3-year commitment, 30–70% discount.
- **Savings Plans** — flexible commit on $/hour.
- **Spot / preemptible / surplus** — 60–90% off, but can be reclaimed any time. Great for fault-tolerant workloads.

### 58.2 Containers

Lightweight, portable, fast to start. Modern compute default.

Building blocks:
- **OCI image** — layered filesystem + metadata.
- **Container runtime** — runc, containerd, CRI-O.
- **Orchestrator** — Kubernetes, ECS, Nomad.

We'll cover Kubernetes in §62 in detail.

### 58.3 Serverless / FaaS

You give the platform a function; it runs on incoming events. Auto-scales from zero. Pay per invocation + execution time.

Strengths:
- Zero idle cost.
- Auto-scale infinite (modulo limits).
- Operational simplicity (no servers to manage).

Weaknesses:
- **Cold starts** — first invocation pays a startup penalty (50 ms–several seconds). Mitigations: provisioned concurrency, lighter runtimes, snapshotting (AWS Lambda SnapStart).
- **Execution limits** — usually 15 min max (AWS Lambda); not for long jobs.
- **Stateless** — state lives elsewhere (S3, DynamoDB).
- **Cost at high steady state** — at sustained load, VMs are cheaper.
- **Local dev experience** — historically poor; improving (LocalStack, etc.).

Use cases: event-driven processing (S3 → Lambda → DynamoDB), webhook handlers, glue code, scheduled tasks, low-traffic APIs.

### 58.4 Edge Compute

Run code at CDN edges, close to the user. Cloudflare Workers, AWS Lambda@Edge, Vercel Edge, Fastly Compute@Edge, Deno Deploy.

Constraints:
- **Lighter runtime** — V8 isolates (Workers) instead of full containers; sub-ms cold start.
- **Limited memory and CPU per invocation.**
- **Limited persistent storage** — KV, R2, D1, Durable Objects.

Use cases: A/B routing, auth at the edge, image transformation, edge caching of personalized content, low-latency APIs serving a global audience.

### 58.5 Choosing Compute Models

Heuristic:
- **Long-running, stateful, well-understood load** → VMs / containers.
- **Event-driven, bursty, variable load** → FaaS.
- **Latency-sensitive, geographic** → edge.
- **Big data, batch** → Spark on managed clusters / serverless data services.

Most real systems use a mix.

---

## 59. Cloud Networking

A modern cloud account has its own network: a VPC.

### 59.1 VPC Basics

A **VPC (Virtual Private Cloud)** is a logically isolated network in the cloud. You choose:
- A CIDR block (e.g., `10.0.0.0/16` — 65,536 addresses).
- Subnets within it, each tied to an availability zone (AZ).
- Route tables per subnet.
- Internet Gateway (for public traffic).
- NAT Gateway (for outbound from private subnets).

Public vs. private subnets:
- **Public** — has a route to the Internet Gateway; instances can have public IPs.
- **Private** — no route to internet directly; outbound goes through NAT.

A typical 3-tier setup: public subnets for load balancers, private subnets for app servers, isolated subnets for databases (no internet at all).

### 59.2 Multi-AZ / Multi-Region

**Availability Zone** — independent datacenter (power, cooling, network) within a region. Failures are independent across AZs. **Always run across at least 2 AZs.** Three is even better for quorum-based systems.

**Region** — a geographic area with multiple AZs. Across regions: independent power, distinct backbones, separate failure domains.

Latency: AZ-to-AZ within a region is typically <2 ms; region-to-region is 30–200+ ms.

### 59.3 VPC Connectivity

- **Peering** — direct one-to-one VPC-to-VPC link. No transitive routing (A peered to B and C doesn't mean B↔C).
- **Transit Gateway / Cloud Router** — hub-and-spoke; route between many VPCs/on-prem.
- **VPN** — IPsec tunnel from on-prem to cloud.
- **Direct Connect / Interconnect** — dedicated fiber. Fastest, most expensive.

### 59.4 Load Balancers in Cloud

- **AWS ALB** — L7, HTTP/HTTPS; routes by path, host, header.
- **AWS NLB** — L4, TCP/UDP; static IPs; very high throughput.
- **AWS GLB** — for inserting third-party network appliances.
- **GCP Global Load Balancer** — anycast IP, global L7, integrated with CDN.
- **Azure Load Balancer / Application Gateway / Front Door**.

### 59.5 Service Endpoints / PrivateLink

Reach cloud services from within your VPC privately, without going to the public internet. AWS calls these **VPC endpoints** or **PrivateLink**. Reduces egress costs and exposure.

### 59.6 Cloud DNS

Each cloud has a managed DNS:
- **AWS Route 53** — health checks, failover, latency-based routing.
- **GCP Cloud DNS**.
- **Azure DNS**.

### 59.7 Network Security

- **Security Groups** — stateful instance-level firewalls.
- **NACLs** (Network ACLs) — stateless subnet-level firewalls.
- **WAF** at the edge.
- **Flow logs** — capture network metadata for forensics.

Defense in depth: security groups + NACLs + WAF, all configured.

---

## 60. Cloud Storage and Databases

### 60.1 Storage Tiers

Block, file, object, plus warmer/colder tiers within object:
- **Block** — EBS, Persistent Disk, Managed Disks. Attached to one VM at a time (mostly). Use for boot volumes and DBs.
- **File** — EFS, Filestore, Azure Files. NFS/SMB.
- **Object** — S3, GCS, Blob Storage. Cheap, scalable, durable. Tiered: Standard → Infrequent Access → Glacier/Archive.

Pricing intuition:
- Hot object: $0.02/GB/month + per-request fees.
- Cold archive: $0.001/GB/month, but retrieval can take hours and costs more.

### 60.2 Managed Databases

- **AWS RDS** — Postgres, MySQL, MariaDB, SQL Server, Oracle. Managed Multi-AZ, backups, scaling.
- **AWS Aurora** — Postgres/MySQL-compatible; cloud-native storage layer (separates compute from storage). Six-way replicated across 3 AZs. Read replicas with low lag.
- **AWS DynamoDB** — managed KV / wide-column; serverless option; single-millisecond latency at scale; expensive at very high RPS.
- **GCP Cloud SQL** — Postgres/MySQL/SQL Server.
- **Cloud Spanner** — globally consistent SQL.
- **Firestore** — NoSQL document store.
- **Bigtable** — wide-column.
- **BigQuery** — serverless OLAP; pay-per-query model; insanely fast on TB/PB of data.
- **Azure Cosmos DB** — multi-API (SQL, MongoDB, Cassandra), tunable consistency, global distribution.

### 60.3 Caching and Search

- **AWS ElastiCache** (Redis / Memcached), **GCP Memorystore**, **Azure Cache for Redis**.
- **AWS OpenSearch Service** (managed Elasticsearch fork), **Elastic Cloud**.

### 60.4 Pricing Considerations

The biggest cost surprises in cloud are usually:
- **Egress.** Data leaving the cloud is expensive ($0.05–$0.12/GB to internet typically). Minimize cross-region and to-internet transfer; consider providers like Cloudflare R2 with no egress.
- **Inter-AZ traffic.** Traffic between AZs costs ~$0.01/GB. At high volume this adds up.
- **Per-request charges.** S3 GETs are cheap individually but add up to real money at billions per day.
- **Idle resources.** Reserved capacity you're not using.

---

## 61. Containers and Container Orchestration

### 61.1 Containers

A container is a process (or process tree) running in isolated namespaces:
- **PID namespace** — process tree.
- **Network namespace** — interfaces, routes.
- **Mount namespace** — filesystem view.
- **UTS, IPC, user, cgroup namespaces.**

Plus **cgroups** for resource limits (CPU, memory, IO).

A container image is a stack of read-only filesystem layers (OCI format) plus metadata. The container runtime unpacks the image, sets up namespaces and cgroups, and execs the entrypoint.

### 61.2 Docker and Beyond

Docker popularized containers. Modern stacks have moved past the Docker daemon to:
- **containerd** — the runtime extracted from Docker; the default in K8s.
- **runc** — the low-level OCI runtime (the thing that actually creates containers).
- **CRI-O** — alternative runtime, popular in OpenShift.
- **Podman** — daemonless Docker alternative.
- **BuildKit / Buildah / Kaniko** — image building tools.

For developer experience, Docker Desktop / Rancher Desktop / OrbStack / colima remain useful locally.

### 61.3 Container Best Practices

- **One process per container** (mostly). Use multiple containers in a pod for sidecars.
- **Minimal base images.** Distroless, Alpine. Smaller surface, faster pulls.
- **Multi-stage builds.** Build artifacts in one image, copy into a minimal runtime image.
- **Don't run as root.** `USER 1000` in Dockerfile.
- **Pin versions.** `python:3.11-slim`, not `python:latest`.
- **Health checks** in Dockerfile or platform manifest.
- **Configuration via environment variables; secrets via mounted volumes** or platform secret stores.

---

## 62. Kubernetes — End to End

Kubernetes (K8s) is the dominant container orchestrator. Originated from Google's internal Borg. Worth understanding deeply because it's everywhere.

### 62.1 The Big Picture

K8s runs containerized workloads on a cluster of machines. You declare desired state ("3 replicas of this app"); K8s makes it so and keeps it so.

Architecture:

**Control plane** (the brain):
- **API server** — REST API, the single entry point.
- **etcd** — consistent KV store; the source of truth for cluster state.
- **Scheduler** — assigns pods to nodes.
- **Controller manager** — runs control loops (replication, endpoints, etc.).
- **Cloud controller manager** — cloud-specific glue.

**Data plane** (the workers):
- **kubelet** — node agent; talks to API server, runs containers.
- **kube-proxy** — sets up service networking (iptables/IPVS rules or eBPF).
- **Container runtime** — containerd, CRI-O.

### 62.2 Core Objects

- **Pod** — one or more containers sharing network namespace and volumes; the unit of scheduling. Usually one main container + sidecars.
- **Deployment** — manages replicas of a pod template; rolling updates.
- **StatefulSet** — for stateful workloads; stable identity, ordered start/stop, persistent volumes per pod.
- **DaemonSet** — one pod per node (for node-level agents: log collectors, network plugins).
- **Job / CronJob** — run-to-completion / scheduled tasks.
- **Service** — stable virtual IP and DNS for a set of pods. Types: ClusterIP (internal), NodePort (external via node IP), LoadBalancer (cloud LB), ExternalName.
- **Ingress** — HTTP routing to services; backed by an ingress controller (NGINX, Traefik, Contour, Envoy-based).
- **Gateway API** — Ingress's successor; richer, multi-protocol.
- **ConfigMap** — non-secret configuration.
- **Secret** — secret values (base64 in etcd; encrypt etcd at rest!).
- **Namespace** — logical partition for objects.
- **PersistentVolume / PersistentVolumeClaim** — durable storage abstraction.

### 62.3 Controllers and Reconciliation

K8s is built on the **controller pattern**: declarative spec, current state, control loop that drives current toward desired.

```
loop:
    desired = get_spec()
    current = observe()
    if current != desired:
        act_to_close_gap()
```

Every operator (described below) follows this pattern. Once you internalize this, K8s makes sense.

### 62.4 Networking

K8s networking has rules:
1. Every pod gets its own IP.
2. Pods can communicate with all other pods without NAT.
3. Nodes can communicate with all pods without NAT.

Implementations (CNI plugins):
- **Calico** — BGP-based, with policy enforcement.
- **Cilium** — eBPF-based, fastest, modern feature set including network policy and service mesh.
- **Flannel** — simple overlay.
- **AWS VPC CNI / GCP-native / Azure CNI** — cloud-integrated.

**Services** are virtual IPs implemented by `kube-proxy`'s iptables/IPVS rules (or Cilium's eBPF). They load-balance to pod IPs.

**DNS** is provided by CoreDNS — services resolve as `service.namespace.svc.cluster.local`.

**Network policies** (NetworkPolicy objects) — pod-level firewalls. By default, all-to-all is allowed; policies make it deny-by-default per namespace.

### 62.5 Storage

K8s abstracts storage with the **CSI (Container Storage Interface)**. Drivers exist for every major storage system (EBS, GCE PD, Azure Disk, Ceph, Portworx, etc.).

**StorageClass** defines a class of storage; **PVC** requests storage of a class; controller provisions a **PV**.

For databases on K8s, **operators** (below) manage the lifecycle.

### 62.6 Operators and CRDs

**Custom Resource Definitions (CRDs)** extend the K8s API with new types.
**Operators** are controllers for these custom resources.

This is one of K8s's biggest superpowers: you can model anything (databases, message queues, ML training jobs) as K8s objects. Examples: Postgres operators (Zalando, Crunchy, CNPG), Strimzi (Kafka), Prometheus operator, ArgoCD, Flux, cert-manager.

### 62.7 Scheduling

The scheduler considers:
- Resource requests (CPU, memory).
- Node selectors / affinity rules.
- Pod affinity / anti-affinity (place pods together / apart).
- Taints and tolerations (a node can repel pods unless they tolerate the taint).
- Topology spread constraints (spread across zones).
- Priority and preemption.

### 62.8 Resource Management

Each container has:
- **Requests** — guaranteed allocation; influences scheduling.
- **Limits** — hard cap.

Best practice: set requests = limits for memory (avoid OOM-kills under pressure); set CPU requests but be cautious with CPU limits (CPU throttling can cause latency issues).

**Quality of Service (QoS)** classes:
- **Guaranteed** — requests = limits for all resources.
- **Burstable** — requests < limits.
- **BestEffort** — no requests/limits. First to be evicted.

### 62.9 Autoscaling

- **HPA (Horizontal Pod Autoscaler)** — scale replicas based on CPU, memory, or custom metrics.
- **VPA (Vertical Pod Autoscaler)** — adjust resource requests.
- **Cluster Autoscaler** — add/remove nodes based on pending pods.
- **Karpenter** (AWS-origin, now CNCF) — faster, smarter cluster autoscaler choosing right instance types per workload.
- **KEDA** — event-driven autoscaling (queue depth, etc.).

### 62.10 Security

- **RBAC** — role-based access to API.
- **Pod Security Standards** — privileged / baseline / restricted; replaces deprecated PSP.
- **Network Policies** — pod firewalls.
- **Secrets at rest** — encrypt etcd; use external secret stores for critical material.
- **Image policies** — admission controllers (Kyverno, Gatekeeper / OPA) enforce image-signing, registry allowlists.
- **Workload identity** — SPIFFE/SPIRE or cloud-native (IRSA on AWS, Workload Identity on GCP).

### 62.11 Multi-Tenancy and Multi-Cluster

- **Namespace as soft tenant** — fine for trusted teams; insufficient for hostile multi-tenancy.
- **vCluster / Capsule / Loft** — virtual clusters per tenant, sharing infra.
- **Multi-cluster** — for blast radius, geographic, regulatory reasons. Tools: Cluster API, Karmada, Argo CD multi-cluster.

### 62.12 Observability for K8s

- **Metrics** — Prometheus + kube-state-metrics + node-exporter; Grafana dashboards.
- **Logs** — DaemonSet log collectors (Fluent Bit, Vector) → backend (Loki, ES, ClickHouse).
- **Traces** — OpenTelemetry instrumented apps + collector → Tempo / Jaeger.
- **Cluster events** — `kubectl get events`, monitor with kubernetes-event-exporter.

### 62.13 When NOT to Use Kubernetes

K8s is overkill for:
- A small team running a small app. ECS/Fargate, Cloud Run, Render, Fly.io are simpler.
- Single-application infrastructure where a simple VM works.

K8s rewards investment. If you're not going to staff platform engineering, choose a simpler PaaS.

---

## 63. Service Mesh in Practice

We covered the concept in §31. Here, the practical considerations.

### 63.1 Istio

The most feature-complete. Components:
- **Istiod** — control plane (xDS, certs, config).
- **Envoy** sidecars per pod.
- **Ambient Mesh** — newer "no sidecar" mode using a per-node proxy + waypoint proxies.

Capabilities: mTLS, traffic shifting (canary), retries/timeouts, circuit breaking, RBAC at the network layer, observability, fault injection.

Operational warnings: complex; deep configuration surface; can introduce subtle bugs (proxy upgrades, MTU issues, large pod startup overhead historically). Worth the cost for systems with many services and strict requirements.

### 63.2 Linkerd

Smaller, simpler, Rust-based proxy (linkerd2-proxy). Less configurable but easier to operate. Strong consistency story and very low overhead. Good fit for "want a service mesh without the operational pain."

### 63.3 Cilium Service Mesh

eBPF-based; can run sidecar-less by intercepting in the kernel. Strong on performance, integrates with Cilium NetworkPolicy. Newer; growing adoption.

### 63.4 What Problems Does It Actually Solve

If you have:
- Many languages (you don't want to implement retries/circuit breaking N times).
- Strict mTLS/zero trust requirements.
- A need to do traffic shifting (canary, blue/green) without app changes.
- Cross-cutting observability for tracing/metrics across services.

…then a mesh pays back. Otherwise, an API gateway plus library-level resilience may be simpler.

---

## 64. Infrastructure as Code

Infrastructure as code (IaC) means defining your infrastructure declaratively in version-controlled files. The benefits: reproducibility, code review, audit trail, automation, rollback.

### 64.1 Terraform

The dominant general-purpose tool. HCL DSL; provider plugins for nearly every cloud and SaaS. State file tracks current vs. desired.

Concepts:
- **Resources** — declared infra objects (`aws_instance`, `google_storage_bucket`).
- **Modules** — reusable groups of resources.
- **State** — the source of truth for what's actually deployed; remote state in S3 + DynamoDB (or Terraform Cloud) for team use.
- **Plan / apply** — plan shows the diff; apply executes.

OpenTofu is the open-source fork after Terraform's license change.

### 64.2 Pulumi

Same model as Terraform, but in TypeScript/Python/Go/C#. Real programming language; familiar IDE support. Particularly nice for complex logic.

### 64.3 AWS CDK / CDK for Terraform

CDK lets you write CloudFormation in TypeScript/Python/Java. CDK for Terraform compiles to Terraform. Same idea: real language for IaC.

### 64.4 Kubernetes-Native: Helm, Kustomize

For K8s manifests:
- **Helm** — templated charts; package + release management. Ubiquitous.
- **Kustomize** — overlay-based; built into kubectl. Simpler when you don't need templates.
- **CDK8s** — write K8s manifests in code.

### 64.5 GitOps

The pattern: git is the single source of truth; a controller continuously syncs the cluster to the git state.

Tools:
- **Argo CD** — pull-based, multi-cluster, mature.
- **Flux** — pull-based, GitOps Toolkit.

GitOps gives you declarative deploys, rollback by `git revert`, audit log = git history, and excellent multi-cluster/multi-env workflows.

### 64.6 Best Practices

- **One repo per concern, or monorepo with strict structure.** Avoid "the giant Terraform repo no one understands."
- **State per environment.** Separate prod and staging states.
- **Lock state during apply** (Terraform's S3 + DynamoDB lock).
- **Don't manually edit** what IaC manages. Drift is the enemy.
- **Continuous validation** — `terraform plan` in CI on every PR; reject drift.
- **Module / chart versioning.**

---

## 65. CI/CD and GitOps

### 65.1 CI (Continuous Integration)

Every commit is built, tested, validated. The longer between integrations, the worse the merge pain.

Pipeline:
1. Lint, format check.
2. Unit tests.
3. Static analysis (security scanners, type checkers).
4. Build (containers, packages).
5. Integration tests.
6. Generate artifacts (signed images).

CI tools: GitHub Actions, GitLab CI, CircleCI, Jenkins, Buildkite, Drone, Tekton.

### 65.2 CD (Continuous Delivery / Deployment)

Delivery = always shippable; deployment = shipped automatically.

Strategies:
- **Recreate** — kill old, start new. Brief downtime; simplest.
- **Rolling** — replace instances incrementally. K8s default.
- **Blue/green** — two full environments; switch traffic. Easy rollback.
- **Canary** — small % of traffic to new version; observe; expand. Best for high-risk changes.
- **Feature flags** — deploy code with the feature off; turn it on selectively. Decouples deploy from release.

### 65.3 Progressive Delivery

Combine canary with automated analysis:
- **Argo Rollouts**, **Flagger** — drive canary based on metrics (error rate, latency); auto-promote or auto-rollback.
- **LaunchDarkly, Statsig, Unleash** — feature flag platforms with experiment integration.

### 65.4 Pipelines for Hyperscale

At scale, pipelines themselves become significant systems:
- Hermetic builds (reproducible).
- Build cache (Bazel, Nix).
- Pipelines test infra changes the same as code changes.
- Deploys can take hours or days due to gradual rollout policies.

---

## 66. FinOps and Cloud Cost Management

Cloud costs balloon if no one watches.

### 66.1 Visibility

- **Tagging.** Tag every resource with team, environment, project, cost-center. Without tags, attribution is impossible.
- **Cost allocation reports.** AWS Cost Explorer, GCP billing reports, Azure Cost Management.
- **Per-team dashboards.**

### 66.2 Optimization Levers

- **Right-sizing.** Most workloads are over-provisioned. Audit CPU/memory utilization; downsize.
- **Reserved / committed pricing.** For stable baseline, save 30–70%.
- **Spot / preemptible** for fault-tolerant workloads. 60–90% off.
- **Storage tiering.** Move cold data to colder tiers.
- **Egress.** Architect to minimize internet/cross-region egress.
- **Idle resources.** Decommission unused dev/test environments overnight and on weekends. Lambda or scheduled scripts to scale down.
- **Architectural choices.** Sometimes a different store or pattern saves orders of magnitude.

### 66.3 Cultural

The team that creates costs should see them. Per-team / per-service dashboards, monthly cost reviews, accountability.

---

## 67. Edge Computing and CDN-Compute

We covered edge in §13 (CDN) and §58.4 (compute). The convergence is one of the most interesting trends of the decade: CDNs becoming compute platforms.

### 67.1 Workers / Edge Functions

V8 isolates (Cloudflare Workers, Vercel) or lightweight container runtimes (Fastly Compute@Edge with WASM, AWS Lambda@Edge). Sub-ms cold starts, code runs near users.

### 67.2 Edge Storage

- **Cloudflare KV** — eventually consistent KV.
- **Cloudflare R2** — S3-compatible, no egress fees.
- **Cloudflare D1** — SQLite at the edge.
- **Cloudflare Durable Objects** — strongly consistent objects pinned to one location.
- **Vercel KV** (Redis-based), **Upstash** — serverless Redis.

### 67.3 Architectural Implications

You can do real things at the edge:
- Auth / token verification (no round trip to origin).
- A/B test routing.
- Image/video transformation.
- Personalized content with user-cached data.
- Edge-cached APIs with smart invalidation.

The architectural shift: origin becomes an event source / source of truth; the edge is where users meet the system.

---

# Part 7 — Data Engineering

The data plane runs in parallel to the application plane. Modern systems generate data faster than they create features, and the discipline of moving, storing, and processing it has become an architectural concern in its own right.

## 68. OLTP vs OLAP and HTAP

**OLTP (Online Transaction Processing)** — many small reads and writes; row-oriented; strict consistency; low latency. The application database. Postgres, MySQL, DynamoDB.

**OLAP (Online Analytical Processing)** — fewer, larger queries; aggregations across millions of rows; column-oriented; relaxed consistency. The warehouse / data store. BigQuery, Snowflake, Redshift, ClickHouse, Druid.

**HTAP (Hybrid)** — handle both. TiDB, SingleStore, Spanner.

### 68.1 Why the Separation

OLAP queries scan tons of rows; running them on OLTP causes contention and slow user-facing requests. So you ETL/ELT data from OLTP to a warehouse where analysts can hammer it.

### 68.2 Row vs Column Storage

OLTP uses row stores (read/write whole rows). OLAP uses column stores: each column is stored separately, enabling massive compression and scanning only the columns you need.

A query like `SELECT AVG(price) FROM orders WHERE country = 'US'` reads two columns out of perhaps 50 in a column store; a row store reads everything.

---

## 69. Data Warehouses, Lakes, Lakehouses

### 69.1 Warehouse

Structured, schema-on-write data optimized for SQL analytics. Snowflake, BigQuery, Redshift, Synapse. Compute and storage are decoupled in modern systems (you scale them independently).

Strengths: SQL, performance, governance.  
Weaknesses: schema rigidity; cost at PB scale; less flexibility for non-tabular data.

### 69.2 Lake

Object storage (S3, GCS) with files in columnar formats (Parquet, ORC) or row formats (Avro, JSON). Schema-on-read; cheap; flexible.

Strengths: cost (object storage at $0.02/GB), any file format, ML-friendly.  
Weaknesses: governance is hard; no transactions; "data swamp" anti-pattern.

### 69.3 Lakehouse

The synthesis: object storage as the substrate, but with a transactional table format on top giving warehouse-like guarantees:
- **Apache Iceberg** — most adopted, vendor-neutral.
- **Delta Lake** — Databricks' format.
- **Apache Hudi** — Uber-origin, strong CDC focus.

These give you ACID on object storage, time travel, schema evolution, partition evolution. Compute engines (Spark, Trino, Flink, Snowflake, BigQuery) can all read them.

The 2025 default: lakehouse on Iceberg.

---

## 70. ETL vs ELT

**ETL (Extract, Transform, Load)** — transform data on the way in (in a tool); land clean data in the warehouse. Older pattern; fixed transformations; works when storage is expensive and compute scales differently.

**ELT (Extract, Load, Transform)** — load raw data; transform inside the warehouse (with SQL). Modern default; cheap warehouse compute makes it feasible; transformations are versioned in code.

Tools:
- **dbt** — SQL-based transformations, dependency graphs, tests, docs. The 2020s ELT standard.
- **Airbyte / Fivetran / Stitch** — managed ingestion (E + L).
- **Apache Airflow / Dagster / Prefect** — orchestration of pipelines.

The modern stack: Fivetran/Airbyte → warehouse → dbt for transforms → BI tool (Looker, Mode, Tableau).

---

## 71. Change Data Capture (CDC)

CDC turns a database's changes into a stream of events, enabling near-real-time replication and integration.

### 71.1 Approaches

- **Log-based CDC (best).** Tail the database's transaction log (Postgres WAL, MySQL binlog, MongoDB oplog). No load on the database, captures all changes, ordering preserved.
- **Trigger-based.** DB triggers write to a change table; readers consume it. Higher overhead; portable to legacy DBs.
- **Query-based / polling.** Periodically poll for changed rows by `updated_at`. Misses deletes; not real-time.

### 71.2 Tools

- **Debezium** — open-source, log-based, Kafka Connect-based; supports many DBs.
- **AWS DMS** — managed migration/CDC.
- **GCP Datastream**, **Azure Data Factory** with CDC.
- **Postgres logical decoding / wal2json / pgoutput** — Postgres-native primitives.

### 71.3 Use Cases

- **Replication** — sync OLTP to OLAP near-realtime.
- **Search index updates** — Postgres → Kafka → Elasticsearch.
- **Cache invalidation** — DB change → cache evict event.
- **Microservice integration** — one service's DB → another's read model.
- **Audit logs** — every change captured.
- **Outbox pattern** — write to outbox table inside transaction; CDC publishes; reliable atomic event publication.

### 71.4 Pitfalls

- Schema changes require coordination; renames/drops break downstream.
- Initial snapshot can be enormous — strategies: use database-native (Postgres `pg_dump`), parallel snapshot per partition.
- Ordering across tables: log-based gives per-row ordering, often per-table; cross-table ordering via timestamps.
- Backpressure — slow consumers fall behind; stream eventually fills.

---

## 72. Batch Processing

Processing data in big chunks at intervals.

### 72.1 MapReduce

Google's seminal model (2004). Map: per-record transform. Reduce: aggregate by key. Hadoop popularized it. Largely superseded by Spark, but the mental model still applies.

### 72.2 Apache Spark

The dominant batch engine. In-memory computation, lazily evaluated DAGs of transformations.

- **RDD** — original API.
- **DataFrame / Dataset** — higher-level, optimized via Catalyst.
- **SQL** — first-class.
- **Streaming** — micro-batches; structured streaming gives near-real-time.
- **MLlib, GraphX** — built-in libraries.

Run on YARN, Kubernetes, or managed (Databricks, EMR, Dataproc).

### 72.3 Other Engines

- **Trino / Presto** — interactive distributed SQL on lake. Fast, no data movement.
- **DuckDB** — embeddable analytical SQL; punches above its weight.
- **Flink / Spark Streaming** for streaming (next section).

---

## 73. Stream Processing

For continuous, event-by-event computation.

### 73.1 The Streaming Mental Model

A stream is an unbounded sequence of events. Operations:
- **Filter, map, project** — per-event.
- **Join** — match events from multiple streams (windowed; can't wait forever).
- **Aggregate** — reduce over a window of events.
- **Window** — group events by time (tumbling, sliding, session).

Time matters:
- **Event time** — when the event happened.
- **Processing time** — when the system saw it.
Late events, out-of-order events, watermarks — these are the hard parts of stream processing.

### 73.2 Apache Flink

The reference streaming engine. True per-event processing, exactly-once via checkpointing, sophisticated event-time handling. Powers ad systems, fraud detection, real-time analytics. Used at Uber, Netflix, Alibaba.

### 73.3 Kafka Streams

Library, not a cluster — runs in your app. Stateful streams via local RocksDB + Kafka changelog. Simpler ops; tightly coupled to Kafka. Good for "I want streaming inside my Java service."

### 73.4 Spark Structured Streaming

Micro-batch with continuous mode option; rich SQL support. Easier if your team already runs Spark batch.

### 73.5 Materialize, RisingWave, ksqlDB

SQL-on-streams: write SQL queries that maintain materialized views as data streams in. Materialize and RisingWave are the modern entrants; SQL semantics are clearer than imperative streaming code.

### 73.6 Use Cases

- Real-time dashboards (always-fresh metrics).
- Fraud detection (anomalies in events).
- Recommendation refresh.
- Real-time ML feature computation.
- Inventory and pricing updates.
- Real-time alerting.

---

## 74. Data Modeling for Analytics

OLAP modeling differs from OLTP.

### 74.1 Star and Snowflake Schemas

- **Star schema** — central fact table (transactions, events) referencing dimension tables (date, customer, product). Denormalized; fast joins.
- **Snowflake schema** — dimensions are normalized into sub-dimensions. More normalized; sometimes too many joins.

Star is the default. Use snowflake when dimensions are large and reused.

### 74.2 Data Vault

Hub (business keys) + link (relationships) + satellite (descriptive attributes). Designed for change-resilient warehouses; favored in regulated industries. More complex; pays back in long-term flexibility.

### 74.3 Fact Tables: Grain

Pick the **grain** (level of detail) of each fact table carefully. "One row per order" vs "one row per order line" matter for what you can compute.

### 74.4 Slowly Changing Dimensions (SCDs)

How do you track that a customer's address changed?
- **Type 1** — overwrite. Lose history.
- **Type 2** — new row with valid_from / valid_to. Full history.
- **Type 3** — current + previous columns. Limited history.

Type 2 is most common.

---

## 75. Data Quality, Lineage, Governance

### 75.1 Data Quality

Without testing data, you ship bad analytics. Tools: **Great Expectations**, **dbt tests**, **Soda Core**.

Common tests: not-null, unique, accepted values, foreign-key integrity, freshness, row counts, schema match.

### 75.2 Lineage

For any column in a dashboard, where did it come from? Lineage tools: **OpenLineage**, **Marquez**, **Datahub**, **Collibra**, **Alation**.

Critical for: debugging bad numbers, compliance (data subject deletion), impact analysis (this column changed; what breaks?).

### 75.3 Catalog and Discovery

A data catalog is the directory: what tables exist, who owns them, what they mean, how fresh they are. Datahub, Amundsen, OpenMetadata, Atlas, Collibra.

### 75.4 Privacy and Governance

- Mask PII at ingestion (or rely on column-level access control).
- Audit who accessed what.
- Right to deletion: must be able to find a user's data and delete it across all stores including derivatives.

---

## 76. Real-Time Analytics

The line between operational data and analytics blurs as users expect dashboards to be live.

### 76.1 Architectures

- **OLAP store with streaming ingest.** Druid, Pinot, ClickHouse: ingest streams, query in seconds-old data.
- **Materialized streaming views.** Materialize, RisingWave: pre-computed views over streams.
- **HTAP databases** — TiDB, SingleStore for unified OLTP+OLAP.

### 76.2 Use Cases

- Live ops dashboards (ride-share supply/demand, e-commerce order rates).
- User-facing analytics (LinkedIn "who viewed your profile" with hours-fresh data).
- Real-time personalization features.
- Fraud and anomaly detection.

The 2025 stack often: Kafka → Flink (transformations) → Druid/Pinot/ClickHouse (storage + serving) → BI / app embeds.

---

# Part 8 — ML Systems

Machine learning has its own system-design discipline. Many architectures apply (caches, queues, replication, sharding), but ML adds workloads with distinctive shapes.

## 77. ML System Design Overview

An ML system has three loops:

1. **Training loop** — train models on data; evaluate; promote a winning model.
2. **Inference loop** — serve predictions in production.
3. **Feedback loop** — capture predictions and outcomes to retrain.

Plus offline experimentation, online experimentation (A/B), monitoring (data drift, model drift), and retraining.

The challenge: keeping all three loops aligned (training/serving consistency) and operating reliably.

### 77.1 Components

- **Data pipelines** — clean, label, version data.
- **Feature store** — compute and serve features consistently for training and inference.
- **Training infrastructure** — distributed compute (GPUs/TPUs), experiment tracking.
- **Model registry** — versioned, evaluated, promotable model artifacts.
- **Serving infrastructure** — low-latency online inference, batch prediction.
- **Monitoring** — model performance, data drift, prediction distribution.
- **Experimentation** — A/B testing, shadow deploys.

---

## 78. Feature Stores

A feature store solves: "the model trained with feature `X` and serves with feature `X`, even though training reads X from a warehouse and serving reads X from low-latency store."

### 78.1 Two Halves

- **Offline store** — bulk, columnar, used for training. Warehouse / S3 / Iceberg.
- **Online store** — low-latency KV for serving. Redis, DynamoDB, Cassandra.

The store keeps them in sync (same definition, same computation), and provides:
- **Point-in-time correctness** for training (no leakage from the future).
- **Versioning** of feature definitions.
- **Sharing** across teams (compute once, reuse).

Tools: Feast (open-source), Tecton, Hopsworks, AWS SageMaker Feature Store, GCP Vertex AI Feature Store, Databricks Feature Store.

### 78.2 Online Latency Pattern

Per-request inference often needs many features. Pattern: in parallel, fetch features from the online store with batched gets; combine; run model. Budget: feature lookup < 10 ms total.

---

## 79. Training Infrastructure

### 79.1 Workloads

- **Single-GPU training** — most ML jobs.
- **Multi-GPU single-node** — data parallel, model parallel.
- **Multi-node distributed** — for foundation models, recommendation systems at scale.
- **Tuning / sweeps** — many parallel runs with different hyperparameters.

### 79.2 Frameworks and Schedulers

- **PyTorch + DDP / FSDP** — standard. FSDP shards optimizer state across GPUs.
- **DeepSpeed** — Microsoft's training stack with ZeRO sharding.
- **Megatron-LM** — NVIDIA's; used for LLM pretraining.
- **JAX + pjit / pmap** — preferred at Google.
- **Ray** — generic distributed Python; Ray Train for ML.
- **Kubeflow / Argo Workflows / Flyte** — pipelines on K8s.
- **SLURM** — HPC-style scheduler, still widely used in research.

### 79.3 Storage for Training

- Reading TBs of training data from object storage with lazy/streaming readers.
- Tools: Mosaic Streaming Dataset, WebDataset, NVIDIA DALI.
- Checkpoint storage: large; must be fast (MosaicML, AsyncCheckpointing).

### 79.4 Experiment Tracking

Run history, hyperparameters, metrics, artifacts. Weights & Biases, MLflow, Neptune, Comet.

---

## 80. Model Serving

### 80.1 Serving Modes

- **Real-time online** — < 100 ms typical; e.g., recommendation, ad ranking.
- **Streaming** — predict as events flow.
- **Batch prediction** — score many entities offline.
- **Embedded / on-device** — phones, browsers.

### 80.2 Serving Stacks

- **TensorFlow Serving / TorchServe** — model-specific.
- **NVIDIA Triton Inference Server** — multi-framework, GPU-optimized, dynamic batching.
- **vLLM, SGLang, TGI** — for LLMs with throughput-optimized batching.
- **BentoML, Seldon, KServe** — orchestration on K8s.
- **Vertex AI / SageMaker / Azure ML** — managed serving.

### 80.3 Performance Tricks

- **Batching** — accumulate requests for a few ms, run together. Huge throughput win on GPU.
- **Caching** — common queries / embeddings cached.
- **Quantization** — int8 / fp8 inference; smaller / faster.
- **Distillation** — smaller student model; close accuracy.
- **Speculative decoding** (LLMs) — small model proposes tokens, big model verifies.

### 80.4 Deployment Patterns

- **Shadow** — new model gets traffic copy; compare outputs.
- **Canary** — small fraction of users.
- **A/B test** — compare versions on user metrics.
- **Multi-armed bandit** — adapt traffic to winning models in flight.

### 80.5 Model Registry

Source of truth for models: version, training metadata, metrics, status (staging/production/archived). MLflow Registry, Vertex Model Registry, SageMaker Model Registry.

---

## 81. Vector Databases and Semantic Search

Embeddings (vectors) are the lingua franca of modern ML retrieval. A vector database stores them and supports approximate nearest neighbor (ANN) search.

### 81.1 What's Stored

For each item: an ID + a vector (e.g., 768 dims) + metadata (filterable attributes).

### 81.2 Indexes

Covered in §18.7. HNSW dominates. IVF-PQ for billion-scale memory-constrained.

### 81.3 Operations

- **Upsert** — insert/update vector by ID.
- **Query** — find top-k nearest; optionally filter by metadata.
- **Delete** — remove.
- **Hybrid search** — combine vector similarity with BM25 (keyword); rerank.

### 81.4 Players

- **Pinecone** — managed; serverless tier popular.
- **Weaviate** — open-source; GraphQL; modular.
- **Qdrant** — open-source; Rust; performant.
- **Milvus** — open-source; designed for billion-scale.
- **pgvector** — Postgres extension; "I just want it inside my DB"; fine to ~1M vectors per index, more with care.
- **Elasticsearch / OpenSearch** — has vector support, especially good for hybrid.
- **Vespa** — Yahoo origin; richest ranking; underrated.

### 81.5 Latency and Scale Considerations

- HNSW indexes are memory-bound. Plan RAM accordingly.
- Sharding by some key + replication for HA.
- Metadata filters: pre-filter (filter, then ANN — expensive) vs post-filter (ANN, then filter — may miss results). Mature stores let you choose / hybridize.

---

## 82. RAG Systems

Retrieval-Augmented Generation: an LLM with relevant context fetched per query.

### 82.1 Pipeline

1. **Chunk** documents (~200–1000 tokens each, often with overlap).
2. **Embed** each chunk with a sentence-encoder model (BGE, e5, OpenAI ada / text-embedding-3, etc.).
3. **Store** embeddings in a vector DB.
4. At query time: **embed** the query, **retrieve** top-k similar chunks, **augment** the prompt with them, **generate** with the LLM.

### 82.2 What Makes Production RAG Hard

- **Chunking strategy.** Sentence vs paragraph vs semantic chunking; overlap; metadata.
- **Hybrid retrieval.** Vector alone misses keyword-precise queries; combine BM25 + vector + reranker.
- **Reranking.** A cross-encoder (or LLM) scores top-100 candidates and picks top-5 for prompt. Massive quality lift.
- **Recency / authority weighting.** Boost newer or trusted sources.
- **Query expansion / rewriting.** LLM generates alternative phrasings; retrieve for each.
- **Evaluation.** RAG quality is hard to test; tools: Ragas, TruLens, custom annotated sets.
- **Freshness.** Pipelines to keep the index current via CDC from sources.
- **Citations and traceability.** Show users which source the answer used.
- **Cost and latency.** Each retrieval round adds latency; rerankers add more.

### 82.3 Architectural Patterns

- **Single-shot RAG** — retrieve once, generate.
- **Multi-hop / iterative** — generate intermediate questions; retrieve again.
- **Agentic RAG** — LLM tool-uses retrieval as a tool, alongside others.
- **Fine-tuned embeddings** — domain-specific embeddings outperform generic ones for specialized corpora.

---

## 83. LLM Inference at Scale

Running LLMs in production has its own architecture.

### 83.1 The Math

LLM inference is autoregressive: generate one token, feed it back, repeat. Two phases:

- **Prefill** — process the prompt; compute-bound; parallel across tokens.
- **Decode** — generate one token at a time; memory-bandwidth-bound; sequential.

The KV cache (per-layer cached attention keys/values) is what makes decode fast — but it's huge (gigabytes for long contexts).

### 83.2 Serving Optimizations

- **Continuous batching** — instead of static batches, dynamically add requests; handle their decode in parallel. vLLM popularized this. 5–10× throughput.
- **PagedAttention** — vLLM's KV cache management; paginated like virtual memory; eliminates fragmentation.
- **FlashAttention** — fused, IO-aware attention kernel; faster, less memory.
- **Quantization** — int8, fp8, even int4. Smaller, faster, slightly worse quality.
- **Tensor / pipeline parallelism** — split big models across GPUs.
- **Speculative decoding** — small draft model proposes tokens, big verifies in parallel; latency reduction.
- **Prefix caching** — common prompt prefixes cached so multiple requests skip prefill.

### 83.3 Stacks

- **vLLM** — open-source; most popular.
- **TGI** — HuggingFace.
- **SGLang** — flexible orchestration of complex generations.
- **TensorRT-LLM** — NVIDIA's; fastest on NVIDIA GPUs.
- **DeepSpeed-MII**.
- **OpenAI / Anthropic / Google APIs** — managed.

### 83.4 At Scale

- **Routing** — load-balance across instances; consistent hashing on session for KV cache reuse.
- **Provisioned vs spot capacity** — GPUs are scarce and expensive; spot discounts huge but interruptible.
- **Multi-region** — for latency and capacity.
- **Cost tracking** — per-tenant token accounting.
- **Safety** — input/output filters, prompt-injection defenses.
- **Caching** — exact-match prompt cache, semantic cache for near-duplicate queries.

### 83.5 The Agent Tier

Modern AI applications layer agents on top of LLMs: tool use, multi-step planning, parallel sub-agents. Architectures involve:
- **Tool registry** with safe execution.
- **Workflow engine** (Temporal, custom) — long-running with retries.
- **Memory store** — short-term conversation, long-term knowledge.
- **Sandboxing** — code execution must be isolated.
- **Authorization for tool use** — agents acting on behalf of users need their own auth chain (delegated identity, scoped tokens, audit trail).
- **Cost and latency budgeting** per agent run.

---

# Part 9 — Hyperscale Case Studies

This part walks through real systems. The actual architectures of these companies have evolved over years and cannot be perfectly known from the outside; what follows is a synthesis of public talks, papers, blog posts, and well-understood patterns. The goal is to give you mental models you can apply, not exact blueprints. Each section starts with the core problem, sketches the architecture, and discusses scale and trade-offs.

## 84. URL Shortener (bit.ly, TinyURL)

**Problem.** Map a long URL to a short slug like `xyz123`. On request to the short URL, redirect to the original. Provide analytics (clicks).

**Functional requirements.**
- Create short URL from long URL.
- Redirect short URL to original.
- (Optional) Custom slugs, expiration, analytics.

**Non-functional.**
- Reads vastly outnumber writes (10:1 to 1000:1).
- Low latency on redirect (< 50 ms).
- High availability (a dead shortener breaks links).
- Predictable, non-guessable slugs (no enumeration).

### 84.1 Estimation

Assume 100M URLs/month created, 1B redirects/month.
- Writes: ~40/s avg, ~200/s peak.
- Reads: ~400/s avg, ~5K/s peak.
- Storage: 100M × 12 months × 5 years × ~500 bytes = ~3 TB raw; with indexes and replicas, ~10 TB.

This is small. A single beefy DB or a moderately-sized sharded cluster does it.

### 84.2 Key Design

**Slug generation.**
- **Hashing the URL** (MD5 → base62) — risk of collisions; deterministic so same URL maps to same slug, which is sometimes wanted.
- **Counter + base62.** Increment a counter, base62-encode it. Sequential (predictable). Use a Snowflake-like ID generator with random bits to avoid sequential.
- **Random base62 strings** with retry on collision. 7 chars of base62 = 62^7 ≈ 3.5 trillion. Plenty.

The standard production approach: a service generating unique IDs (Snowflake-like), then base62-encoded. Pre-generate batches per writer to avoid coordination per-request.

**Storage.** A KV: `slug → (long_url, metadata)`. DynamoDB / Cassandra / Redis with persistent backing.

**Read path.**
1. Request `GET /xyz123`.
2. Lookup slug in cache (Redis) → hit, redirect (302/301).
3. On miss, lookup in DB; populate cache; redirect.

A 99%+ cache hit rate is achievable; popular links dominate.

**Write path.**
1. Receive long URL.
2. Generate ID; base62-encode.
3. Store `(slug, long_url)`.
4. Return short URL.

**Analytics.** Don't log clicks synchronously; emit an event to Kafka. Stream processor aggregates per-slug metrics (clicks per hour/day, by referrer, by country) into a DB the dashboard reads.

### 84.3 Scaling Concerns

- **Hot links.** A viral link might spike to millions of redirects per second. Solution: aggressive CDN caching of redirects (with appropriate `Cache-Control`); the redirect is just `Location: <long-url>`.
- **Custom slugs.** Need uniqueness check; use the same KV.
- **Spam / malicious URLs.** Scan against safe-browsing lists; expire suspicious ones.

### 84.4 Variants

- **Internal short links** (e.g., `g.co`) — same architecture, smaller scale.
- **Branded / vanity domains** — multi-tenancy; slug uniqueness scoped per domain.

---

## 85. Pastebin / Text-Sharing

**Problem.** Users paste text; get a shareable URL; recipients view it (read-only).

**Differences from URL shortener.**
- Storage is bigger per item (KB–MB) but still small overall.
- Often want syntax highlighting, expiration, password protection.

### 85.1 Architecture

- Generate a random ID for each paste.
- Store paste text in object storage (S3) keyed by ID. (Bigger blobs go to object storage; metadata in KV/SQL.)
- Metadata DB: `id → (s3_key, expires_at, syntax, created_at, view_count, password_hash)`.
- API server handles create, read, expire.
- CDN caches paste reads (immutable; long TTL).

### 85.2 Trade-offs

- **All-public** — simpler caching, no auth.
- **Private** — signed URLs or ID + secret token.

### 85.3 Scale

Even at hundreds of millions of pastes, total storage is tens of TB. Single-region object storage suffices. Read-heavy → CDN absorbs most traffic.

---

## 86. Rate Limiter

**Problem.** Limit requests per identifier (IP, user, API key) to N per window.

Already covered the algorithms in §40. Here, the system design.

### 86.1 Distributed Architecture

Most production rate limiters are centralized (Redis or similar) for accuracy across instances.

- **Edge** — at the API gateway / LB.
- **Service-level** — for per-endpoint or per-tenant limits.

### 86.2 Implementation

**Redis token bucket via Lua script** (atomic):
```
KEYS[1] = bucket key
ARGV[1] = max tokens
ARGV[2] = refill rate per second
ARGV[3] = now (timestamp)
ARGV[4] = cost (tokens this request needs)

(load tokens, last_refill from key)
elapsed = now - last_refill
tokens = min(max, tokens + elapsed * rate)
if tokens >= cost:
    tokens -= cost
    save (tokens, now)
    return ALLOW
else:
    return DENY
```

This is atomic, fast, accurate.

### 86.3 At Hyperscale

Single Redis can't handle global rate limiting at hyperscale.

- **Sharded Redis** by user / tenant key.
- **Approximate / probabilistic** at the edge with periodic sync — each edge node tracks local count; aggregate periodically (sloppy global, fast local). Cloudflare's approach.
- **Hierarchical** — per-instance L1, per-cluster L2, per-region L3.

### 86.4 Concerns

- **Identity for rate limiting.** Anonymous users keyed by IP (which can be NATted; one IP = many users). Logged-in keyed by user ID. API by key.
- **Headers** to return: `X-RateLimit-Limit`, `X-RateLimit-Remaining`, `X-RateLimit-Reset`, `Retry-After`.
- **Soft vs hard limits.** Soft warns; hard rejects.

---

## 87. Distributed Cache

We covered concepts in §14. Here, the system design exercise.

### 87.1 Requirements

- Multi-node, in-memory KV cache.
- Sharded for capacity; replicated for HA.
- Low-latency reads (< 1 ms typical).
- Tolerate node failures gracefully.

### 87.2 Architecture

**Sharding.** Consistent hashing on the key. Each key maps to a shard; shards distributed across nodes.

**Replication.** Each shard has a primary and one or more replicas. Writes go to primary, replicate async or sync to replicas.

**Client-side.** Many big systems do client-side sharding (smart client knows the ring). Avoids a proxy hop. Examples: Twemproxy / mcrouter (Facebook).

**Or proxy-based.** Envoy or specialized proxies. Server-side is simpler for clients but adds latency.

**Cache coherence with the source-of-truth DB.** Cover in §14.5–14.6.

### 87.3 Real-World

- **Memcached** — Facebook's mcrouter is a proxy that routes, replicates, and migrates; powers Facebook's massive cache fleet (hundreds of billions of operations/day).
- **Redis Cluster** — built-in sharding (16,384 hash slots).
- **DynamoDB DAX** — managed write-through cache.
- **AWS ElastiCache for Redis** with cluster mode.

---

## 88. Notification System

**Problem.** Send notifications (email, push, SMS, in-app) to many users in response to events.

### 88.1 Requirements

- Multiple channels.
- High throughput (millions of notifications/day; bursts of millions during incidents).
- Reliability (don't lose notifications).
- Per-user preferences; quiet hours; throttling.
- Personalization, templating, localization.
- Delivery tracking.

### 88.2 Architecture

```
Event Producers ──→ Kafka (events) ──→ Notification service
                                            │
                                            ↓
                                       User Preferences DB
                                            │
                                            ↓
                            Channel Workers (email/SMS/push/in-app)
                                            │
                                            ↓
                                  Provider APIs (SendGrid, Twilio,
                                    APNs/FCM, internal in-app store)
```

- **Event ingestion.** Kafka topic per source; notification service consumes.
- **Preferences.** Each user → channel-specific preferences + quiet hours + locales.
- **Templating.** Each notification type has templates per channel and locale.
- **Channel workers.** Per-channel workers handle delivery, retries, errors. Email worker batches into provider APIs; SMS worker handles per-region rate limits; push worker handles APNs/FCM tokens.
- **Tracking.** Webhook callbacks from providers (delivered, opened, bounced) feed analytics.

### 88.3 Scale

- **Throttling.** Per-user max N notifications/day; cross-channel.
- **Deduplication.** Don't spam the same notification multiple times. Use a key (user, type, related-id).
- **Backpressure.** Queue depth → autoscale; eventually drop low-priority.
- **Batching / digests.** Many systems coalesce frequent events into hourly or daily digests.
- **Quiet hours.** Cron-style respect for user timezone.

### 88.4 Push Specifically

Pushes go through APNs (Apple) or FCM (Google). Token management is critical:
- Store device tokens; one user can have many.
- Rotate when invalidated (token expiry, app reinstall).
- Handle "this token is invalid" responses by removing.

For massive fan-out (a celebrity's 10M followers), pre-fan-out to a per-user notifications list (push pattern) or compute on read (pull pattern). Hybrid for hot accounts (covered more in social feeds).

---

## 89. Web Crawler (Googlebot)

**Problem.** Discover and download web pages to index them. At Google scale: tens of billions of pages, refreshed continuously.

### 89.1 Components

- **URL frontier** — queue of URLs to fetch, prioritized.
- **Fetcher** — downloads pages; respects `robots.txt`; rate-limits per host.
- **Parser** — extracts links, content, metadata.
- **Deduplication** — content fingerprints; URL canonicalization.
- **Storage** — fetched pages.
- **Scheduler** — when to re-crawl each URL based on freshness.

### 89.2 The URL Frontier

Distributed priority queue, partitioned by host. Per-host politeness (one fetch at a time per host typically; respect crawl-delay).

Some hosts re-crawled minutely (news), some weekly, some yearly. Adaptive based on observed change frequency.

### 89.3 Politeness

- Fetch `robots.txt` first; cache it.
- Respect `Crawl-Delay`.
- Cap requests per host per second.
- Identify with proper User-Agent, contact info.

### 89.4 Deduplication

- **URL canonicalization** — strip fragments, normalize parameters, follow redirects.
- **Content hashing** — SimHash / MinHash for near-duplicate detection.
- **Bloom filters** for "have we seen this URL recently."

### 89.5 Distributed Architecture

- **Many fetcher nodes** spread across regions.
- **Distributed URL frontier** — partitioned, replicated.
- **Distributed storage** — pages go to object storage (HDFS / S3 / Google's Colossus).

### 89.6 Scaling

- Tens of thousands of fetcher machines at Google scale.
- Bandwidth constraints; fetcher placement (closer to large hosts geographically).
- Adversarial conditions: crawler traps (infinite URL spaces), blocked / cloaked content.

### 89.7 The Index Build

After crawl: pages go through parsing → tokenization → inverted index construction → ranking signals computation → serving index. Covered in §90.

---

## 90. Google Search

The most ambitious system in computing history. Public details span 25+ years of papers (PageRank, MapReduce, GFS, Bigtable, Spanner, Borg). A simplified mental model:

### 90.1 The Macro Pipeline

```
Crawler ──→ Web pages (Bigtable / Colossus)
              │
              ↓
         Parser, Indexer
              │
              ↓
       Inverted Index (sharded)
              │
              ↓
         Ranking pipeline
              │
              ↓
         Serving index (sharded, replicated)
              │
              ↓
        Query Frontends ──→ Users
```

### 90.2 The Inverted Index

For every term `t`, a posting list of `(doc_id, positions, importance)`. The index is sharded by document (each shard has all terms but for a subset of docs) so that each query fans out to all shards (which return their top-k), and the front-end merges.

Index size: in the petabytes. Stored in highly compressed columnar formats. Hot terms in memory; cold on SSD.

### 90.3 Query Path

1. **Query understanding.** Tokenize, spell-correct, expand synonyms, detect entities, classify intent (navigational, informational, transactional). Increasingly uses neural models for understanding.
2. **Retrieval.** Fan out to all index shards; each returns top-k candidates by base relevance (BM25-like + signals).
3. **Aggregation.** Front-end merges top results across shards.
4. **Ranking.** Multi-stage scoring: classical signals (PageRank, freshness, query-doc relevance, click data) + learned-to-rank models + neural rerankers (BERT-family, then larger).
5. **Augmentation.** Featured snippets, knowledge panel, images, news, local — vertical search systems plug in.
6. **Serving.** Render result page with caching layers. Sub-second P50 latency for the entire chain.

### 90.4 Latency

A query end-to-end: < 200 ms `p50`. To achieve this:
- Massive parallelism across shards.
- Aggressive caching (popular queries cache; same query same time of day).
- Hedged requests across replicas to control tail.
- Co-located compute and index.
- Tens of thousands of machines per query bucket; query touches hundreds-thousands of them.

### 90.5 Freshness

The crawler runs continuously. Hot URLs (news) are re-crawled and re-indexed within minutes. Caffeine (Google's index update system) replaced batch index updates with incremental, near-real-time updates.

### 90.6 Personalization and Geography

User location, language, search history shape ranking. Multi-region serving: query goes to nearest region; index replicated globally with per-region freshness.

### 90.7 Spam, Adversarial Web

Webspam team continuously adjusts ranking to demote SEO spam, hacked sites, low-quality AI-generated content. PageRank is one signal among hundreds.

### 90.8 Lessons

- **Layered ranking** — cheap retrieval over many docs; expensive scoring over few.
- **Learned models** at the most expensive stages.
- **Fan-out + tail latency** — hedging is essential; if one of 1000 shards is slow, the whole query is slow.
- **Specialized systems for verticals** — News, Images, Maps, Shopping each have their own index pipelines.

---

## 91. YouTube

Serve a billion hours of video per day. Tens of billions of views per day. Multi-resolution, multi-format, global, ad-supported. Acquired by Google in 2006 and built on Google's infrastructure since.

### 91.1 Macro

- **Upload** — millions of videos per day.
- **Encode** — transcode to many resolutions, codecs (H.264, VP9, AV1), bitrates (HLS/DASH adaptive).
- **Store** — original and encoded variants (Colossus / Spanner for metadata).
- **Distribute** — Google's CDN; edge caches absorb 99%+ of bytes.
- **Recommend** — feed ranking, related videos.
- **Serve** — adaptive bitrate streaming, ad insertion.

### 91.2 Upload and Encoding

- Multi-part upload to nearest region.
- Job queue for encoding (priority by uploader tier and predicted views).
- Encoding farm: thousands of machines doing parallel transcodes.
- Hot videos (predicted high-view) get more encoded variants up front; long-tail get encoded lazily on first view.

### 91.3 Storage

- Originals in cold-tier object storage.
- Encoded variants in hot tier; popular ones in CDN edge caches.
- Metadata (titles, descriptions, durations, comments) in distributed databases (Spanner-like).

### 91.4 Streaming

- **Adaptive Bitrate (ABR)** — client downloads a manifest (HLS .m3u8 / DASH .mpd) that lists segments at multiple bitrates; client picks based on bandwidth and switches segment-by-segment.
- **Segments** are short (2–6s); cached at the edge.
- **DRM** for premium content (Widevine / FairPlay).

### 91.5 Recommendation

- Two-stage: candidate generation (fast, retrieves thousands), ranking (slower neural model picks final order).
- Signals: user history, watch time, demographics, video metadata, embeddings of videos and users.
- Real-time signals (just watched X) shape next recommendation.
- Multi-objective: watch time, satisfaction (post-watch survey), diversity, freshness.

### 91.6 Comments, Likes, Subscriptions

Standard CRUD at scale. Sharded by video / user; replicated; cached.

### 91.7 Ads

Ad selection per impression. Inserted into HLS/DASH manifest server-side (so users can't ad-block by URL). See §110 for ad-serving deep dive.

### 91.8 Live Streaming

- **Ingest** — RTMP / WebRTC push from creator.
- **Transcode** — real-time, low-latency.
- **Distribute** — chunked HLS/DASH (1–2s chunks) for low latency, or LL-HLS / LL-DASH for sub-second.
- **DVR** — recent live becomes VOD seamlessly.

### 91.9 Scale Numbers (rough public figures)

- 500+ hours of video uploaded per minute.
- Billions of views/day.
- Exabytes of storage.

### 91.10 Lessons

- Hot/cold data separation is critical at video scale.
- CDN absorbs the load; origin is for cache fills only.
- ML throughout — encoding presets, recommendations, ad selection.
- Adaptive streaming means clients are intelligent.

---

## 92. Instagram (Feed, Stories, Reels, DMs)

Started 2010 as a photo-sharing app on Postgres + Redis on AWS. Acquired by Facebook 2012, migrated onto Meta infrastructure. Now: ~2B users, billions of images/videos uploaded per day, complex feed ranking, Reels (TikTok competitor), Stories, Direct Messages, Shopping. We'll cover the major surfaces.

### 92.1 Photo / Video Upload

- Client uploads to nearest edge / origin (multipart for large videos).
- **Asset service** stores blobs in Meta's photo storage (Haystack-derived) — append-only, optimized for billions of small objects with low IOPS overhead.
- **Encode** — multiple resolutions for image; multiple bitrates for video.
- **Metadata DB** — TAO-backed graph: `Post(id, author, caption, media_refs, location, mentions, ...)`.
- Outbox event: "PostCreated" → consumed by feed indexers, search, ranking pipelines.

### 92.2 The Feed

The "Home Feed" is the canonical hard system-design problem.

**Two patterns:**
- **Push (fan-out on write).** When a user posts, write the post into every follower's feed inbox. Read is cheap (just read your inbox).
- **Pull (fan-out on read).** When you load your feed, query posts from each user you follow.
- **Hybrid.** Push for normal users; pull for celebrities (whose followers number in the millions and would explode write costs).

Instagram uses **hybrid**, with sophisticated ranking on top.

**Feed pipeline:**

1. **Candidate generation.** Pull recent posts from people you follow + recommended-account candidates + Reels candidates + ad slots. Tens-hundreds of candidates.
2. **Feature gathering.** For each candidate, fetch features (post age, author, engagement, predicted CTR, predicted dwell time, your past interactions).
3. **Ranking.** A multi-objective deep model scores each candidate on multiple objectives (like, comment, share, dwell time, save) and combines them into a final score. This is where the bulk of feed magic happens.
4. **Diversity / business rules.** Don't show 10 posts from the same person; intersperse Reels; insert ads at right positions.
5. **Render.** Return the ranked list with media URLs.

**Storage layers:**
- **TAO** — graph cache layer over MySQL (we'll discuss in §93). Source of truth for the social graph and post metadata.
- **Cassandra** for inbox-style data (e.g., DM messages historically).
- **Memcached / similar** for caching computed things.
- **MyRocks (RocksDB on MySQL)** for compressed primary storage.
- **Photo / video object storage** — Haystack-family, edge-cached.

### 92.3 Stories (24-hour ephemeral)

- Posted once, lifetime 24h, then auto-expire.
- Per-author "story tray" — list of stories per friend.
- Read pattern: open a friend's tray, see their stories sequentially.
- Storage: similar to posts, with TTL.
- Privacy / muting integrated.

Distinct read pattern (sequential traversal of one friend's stories) means a different cache structure than the feed.

### 92.4 Reels (Short-Form Video)

- TikTok-style algorithmic vertical video feed.
- The big difference from Home Feed: the candidate pool is everyone's videos, not just people you follow. Heavy ML ranking.
- **Two-tower model** for retrieval: a user-tower computes user embedding; a video-tower computes video embeddings. Find videos near the user in vector space.
- **Reranking** with cross-features (does this user, with this context, like this video at this moment?).
- **Real-time signals.** Skip a video at 2 seconds → feed adjusts in real time. This requires fast feature pipelines.
- Caching: very limited; each user's feed is essentially personalized in real time.

### 92.5 Direct Messages

A messaging system inside Instagram:
- E2E encryption (rolling out).
- Per-conversation message store.
- Push notifications, presence ("typing…").
- Multi-device sync.
- Architecture similar to WhatsApp (covered in §96).

### 92.6 Search and Discovery

- Search: sharded inverted index over usernames, captions, hashtags.
- Explore: another ML-driven feed, candidate-generation + ranking model selecting interesting content for you.

### 92.7 Notifications

Massive fan-out. When you post, every follower gets a "New post from X" candidate notification — but heavily filtered/ranked by the notifications team's ML model deciding whether you actually want it (and which channel: push, in-app, email).

### 92.8 Operational

- Multi-region active-active.
- Cell-based.
- Aggressive feature-flagging; thousands of experiments running concurrently.
- Real-time monitoring and rollback.

### 92.9 Lessons

- **Hybrid fan-out** is the standard: push for the common case, pull for celebrities.
- **Two-tower retrieval + heavy reranking** is the canonical ML feed architecture.
- **TAO-style graph cache** is a deep idea: source of truth in MySQL, but consistent read-through cache shaped like the graph.
- **Per-surface (Feed, Stories, Reels, DMs) architectures** look different even within one product.

---

## 93. Facebook News Feed

The original social feed system, foundational to many later designs. Public details mostly come from Facebook engineering posts, the TAO paper, and various conference talks.

### 93.1 The Stack (High Level)

- **MySQL** as primary OLTP storage. Sharded by user ID. Hundreds of thousands of MySQL instances historically.
- **TAO** — a distributed graph cache layered over MySQL. The read-side serving layer. We'll detail it.
- **Memcached fleet** for cache.
- **Tupperware / Twine** — Facebook's container orchestration (predates K8s; similar problem).
- **Haystack / F4 / Tectonic** — photo storage tiers.
- **PMM, Wormhole, Scribe, etc.** — internal pubsub / change pipelines.

### 93.2 TAO

TAO is one of the most influential systems in modern infra design. The paper is a classic.

- **Data model.** Two object types: **objects** (entities with typed properties) and **associations** (typed edges between objects with metadata). Everything in Facebook (users, posts, comments, likes, friendships) maps to these.
- **API.** `obj_get(id)`, `assoc_get(id1, type, id2_list)`, `assoc_count(id1, type)`, `assoc_range(id1, type, pos, count)`, plus mutations.
- **Layered cache.** Each region has a **leader cluster** (consistent with MySQL) and **follower clusters** (read-through, eventually consistent, closer to clients). Writes go to the leader, then to MySQL, then invalidate followers asynchronously.
- **Sharding.** Shard by `id1` for associations — a user's connections all live on one shard, so "who liked this post" doesn't fan out.

### 93.3 The Feed Read Path

1. Front-end fetches user's friend list and other "candidate sources" (groups, pages, ads).
2. For each source, fetch recent posts via TAO.
3. Aggregator combines into candidate pool (~100s).
4. Feature service fetches engagement signals, post metadata, user history.
5. Ranker (deep neural model) scores each candidate.
6. Apply business rules (diversification, ad insertion).
7. Return.

The whole thing in a few hundred ms.

### 93.4 The Feed Write Path

When you post:
- Write to TAO / MySQL.
- Publish event to Wormhole (FB's CDC).
- Consumers (search index, feed candidate stores, recommendation systems) update accordingly.

### 93.5 Aggregations

Likes, comments, shares — counts in the millions for hot posts. Counters are sharded; aggregated; cached. Reading "this post has 1.2M likes" is `assoc_count`, served from cache.

### 93.6 Photos / Videos

- **Haystack** (2010 paper) — photo storage optimized for billions of small images. Append-only logs; per-image pointer in an in-memory index.
- **F4** — warm tier with erasure coding.
- **Cold tier** — even more compression for rarely-accessed.
- **Delivery** — Facebook's edge POPs (FNA — Facebook Network Appliance), millions of edge cache hits per second.

### 93.7 Search and Privacy

Search is hard at FB because results must respect privacy: you can search for "John Smith" but only see what John has shared with you. Every result must be access-checked. Search index is sharded; access checks happen at query time.

### 93.8 Ads

Auctions per ad slot, multiple per page. Latency-critical. Section §110.

### 93.9 Scale (rough public figures)

- 3B+ daily active users (Meta family).
- Hundreds of trillions of edges.
- Trillions of feed candidate evaluations per day.
- Petabyte/day photo storage growth.

### 93.10 Lessons

- **Cache layer that is graph-shaped** (TAO) — not just KV — when your data is graph-shaped.
- **Hybrid push-pull feeds.**
- **MySQL still works at extreme scale** when sharded right and supplemented with smart caches.
- **Specialized storage tiers** for hot vs cold content.

---

## 94. Twitter / X

The original microblog at scale. Famous for the "fan-out on write vs on read" debate. Has gone through many architectures.

### 94.1 The Tweet Object

`Tweet(id, user_id, text, media, created_at, reply_to, retweet_of, ...)`. ID is a **Snowflake ID** — 64 bits: timestamp + worker ID + sequence number. Time-orderable, globally unique, generated without coordination. Snowflake (the ID scheme) was open-sourced by Twitter and is now ubiquitous.

### 94.2 Timelines

The Home Timeline (the feed of tweets from people you follow): hard.

**Pure pull:** for every load, query latest tweets from every followee. For users following thousands, this is many DB lookups per page load.

**Pure push:** when you tweet, write to every follower's "timeline cache." For users with millions of followers (celebrities), this is millions of writes per tweet.

**Hybrid:** push for normal users; pull for celebrities; merge at read time. This is what Twitter has historically done.

The push-side timelines are stored as Redis lists per user (the "timeline service").

### 94.3 Read Path

1. Fetch user's pre-computed timeline from Redis (push side).
2. Fetch tweets from celebrities you follow (pull side).
3. Merge by timestamp.
4. Optional: ranking on top of chronological (the "For You" tab uses heavy ML).
5. Hydrate: fetch tweet content, author, media for each.
6. Return.

### 94.4 Storage

- **MySQL** historically (Manhattan, Twitter's KV store, also used).
- **Manhattan** — Twitter's distributed KV store; multi-region, eventually consistent option.
- **Cache fleet** — Redis (timelines), Memcached (tweets, users).
- **Photo / video** — separate object storage with CDN.

### 94.5 Search

Realtime tweet search with seconds-to-minutes lag. Sharded inverted index. Updated continuously.

### 94.6 The "For You" Feed

ML-ranked timeline. Two-tower retrieval + heavy reranker, similar to Reels architecture. Real-time signals.

### 94.7 Direct Messages

Real-time messaging similar to other DM architectures.

### 94.8 Scale

- ~500M+ tweets/day at peak.
- Hundreds of millions of DAU.
- Latency-sensitive (live events, breaking news).

---

## 95. TikTok

Pioneered the algorithmic short-video feed. ByteDance's architecture is less publicly documented, but the patterns are clear from talks and reverse-engineering.

### 95.1 The Magic: ML-First Feed

Unlike Facebook/Instagram where the social graph drives the feed, TikTok's feed is **mostly graph-independent.** You don't need to follow anyone. The system finds videos for you based on behavior.

This means:
- The candidate pool is **all videos**, not "people you follow."
- The system relies entirely on retrieval + ranking ML.
- Feedback loop is fast: every swipe, watch-completion, like, share, follow is a signal that updates user representation.

### 95.2 Recommendation Architecture

Two-stage:

1. **Retrieval / Candidate Generation.** Given user state, retrieve thousands of candidate videos. Multiple retrievers run in parallel:
   - Embedding-based (two-tower model).
   - Graph-based (videos liked by similar users).
   - Trending / freshness retriever.
   - Diversity / cold-start retriever (new content).
2. **Ranking.** Deep model scores each candidate on many objectives (watch %, like, share, comment, follow, skip). Weighted combination → final score.

### 95.3 Real-Time Pipelines

- Watch a video for 1 second, skip → user embedding updated within seconds.
- Real-time feature stores; streaming pipelines (Flink-style).
- New videos enter candidate pools fast (cold start).

### 95.4 Video Infrastructure

- Upload, transcode (multiple resolutions, vertical-first).
- Pre-fetching at the client: while you watch one video, the next 2–3 are downloaded in the background.
- Edge caching of popular videos.
- Server-side ad insertion.

### 95.5 Cold Start

New videos need exposure to learn whether they're good. TikTok exposes them to a small audience first, observes engagement, expands if good. This is bandit-style exploration baked into the feed.

### 95.6 Scale

- 1.5B+ users.
- Hours of watch time per user per day.
- Tens of billions of recommendations served daily.

---

## 96. WhatsApp / Signal / Messenger

End-to-end encrypted messaging at scale. WhatsApp is the canonical example: 2B+ users, fewer than 100 engineers historically.

### 96.1 Core Architecture

- **Connection servers** — clients hold persistent connections (TCP / WebSocket / XMPP-derived). Handle online presence.
- **Message routing** — ephemeral; deliver to recipient's connection if online; queue otherwise.
- **Storage** — minimal on the server; messages stored only until delivered. (For groups and multi-device, more complex storage.)
- **Push** — APNs / FCM for offline notifications.

### 96.2 End-to-End Encryption

The Signal Protocol:
- **X3DH** for initial key agreement.
- **Double Ratchet** for forward and post-compromise secrecy: every message uses a fresh key derived from a chain that ratchets forward.
- **Per-pair sessions.**

For groups: **Sender Keys** (each member has a sender key shared with all members) — efficient compared to N×N pairwise.

The server can route ciphertext but cannot read it. Metadata (who messages whom, when) is what the server knows.

### 96.3 Multi-Device

Tricky with E2E. Signal's approach: each device has its own identity; sender encrypts separately for each recipient's devices. Sync between own devices via the same mechanism.

### 96.4 Scale

WhatsApp's secret sauce historically: Erlang. Each connection is a lightweight Erlang process; one server handles millions of connections. Dedicated phone-line-style protocol design.

### 96.5 Storage

Minimal at WhatsApp; messages live on devices. iCloud / Google Drive backups optional (encrypted).

Other messengers (Signal, Messenger) take similar approaches.

### 96.6 Status / Stories / Calls

- Status (Stories) — TTL-based, distinct surface.
- Voice/video calls — WebRTC with TURN/STUN servers; E2E for voice in modern apps.
- Group calls — SFU (Selective Forwarding Unit) servers route encrypted streams without seeing them.

---

## 97. Netflix

Streaming video, recommendations, original content production. Heavily on AWS (and their own CDN).

### 97.1 Open Connect (Netflix's CDN)

Netflix runs its own CDN for video bytes. They place "Open Connect Appliances" (OCAs) inside ISPs and IXPs. Pre-position popular content overnight; serve directly from the ISP. Reduces transit costs, improves latency.

### 97.2 The Stack

- **Microservices on AWS.** Hundreds of services.
- **Cassandra** for high-throughput, high-availability data (viewing history, etc.).
- **DynamoDB** in places.
- **MySQL / Aurora** for some.
- **Kafka** as the event backbone.
- **EVCache** — Netflix's distributed memcached layer.
- **Atlas** — their metrics platform.
- **Spinnaker** — their CD platform (open-source).
- **Chaos Monkey / Chaos Engineering** — they invented the discipline.

### 97.3 Streaming

- Video files in S3, encoded into many bitrates.
- Manifest (HLS/DASH) sent to client.
- Client adaptively selects bitrate based on bandwidth.
- Segments served from OCAs.
- DRM (Widevine, PlayReady, FairPlay).

### 97.4 Recommendation

Multi-objective ML across many signals: watch history, time of day, demographics, member context. Multiple recommenders for different rows ("Trending," "Because you watched X," "New on Netflix"). Personalized artwork (different cover image per user for the same title).

### 97.5 Operational Excellence

Netflix's reliability culture is famous:
- Multi-region active-active.
- Chaos engineering (kill instances continuously in production).
- Strict service ownership.
- Autoscaling + reactive failure handling.
- Detailed observability (Atlas, Mantis, etc.).

---

## 98. Spotify

Music streaming, podcasts, recommendations.

### 98.1 The Stack

- Mostly on Google Cloud (after migration from AWS).
- Backed by GCS + BigQuery for analytics.
- Microservices in Java + Python.
- **Apollo** — their internal microservice framework.
- Cassandra, Bigtable.

### 98.2 Streaming Audio

- Audio files (compressed: Ogg Vorbis, AAC, recently lossless variants).
- Multi-bitrate; client adapts.
- CDN delivery.
- Pre-fetching the next track during current playback.

### 98.3 Recommendation

- **Discover Weekly, Daily Mixes** — collaborative filtering + content-based + audio analysis (key, tempo, energy via the Echo Nest acquisition's lineage) + sequence models.
- A canonical example of recommendation done well.

### 98.4 Real-Time Personalization

- Skipping a song is a strong negative signal; system reacts within seconds.
- Streaming pipeline (Dataflow / Flink) processes events; updates user representation.

### 98.5 Search

- Hybrid: keyword + semantic (vector) for natural-language queries ("songs like dreamy synth").

### 98.6 Podcasts

- Different challenges: long content, segmented playback, ad insertion, chapter markers, transcription for search.

---

## 99. Uber / Lyft / DoorDash (On-Demand Marketplaces)

Real-time matching of supply (drivers, dashers) and demand (riders, eaters), at city-scale concurrency.

### 99.1 Core Components

- **Location service** — drivers stream their location every few seconds.
- **Geospatial index** — find nearby drivers fast.
- **Dispatch / matching service** — assign trip to driver.
- **Trip lifecycle service** — state machine: requested → matched → en route → started → completed.
- **Pricing / surge** — dynamic pricing based on supply/demand.
- **Payments** — charge rider, pay driver.
- **Maps / routing** — ETA estimation, navigation.
- **Notifications** — push, SMS.

### 99.2 Geospatial Index

The hard primitive. Find drivers within X km of a point in milliseconds.

- **H3** (Uber's hexagonal grid) — divide world into hexagons at 16 resolution levels. Each hex has a 64-bit ID. Nearest-neighbor queries reduce to "find drivers in this set of hexes."
- **Geohash** — earlier scheme, similar idea with rectangles.
- **Quad-trees / R-trees** for in-memory spatial structures.

The location service maintains an in-memory index per city or region; updates are streamed in.

### 99.3 Dispatch

- Rider requests trip.
- Compute candidate set: drivers within X distance and matching criteria.
- Rank candidates: ETA, driver rating, ride preferences.
- Send offer to top driver; driver accepts (or rejects, fall through).
- Optimization: in busier markets, batch matching (compute optimal assignment over many requests at once — bipartite matching).

### 99.4 ETAs

ML models estimating arrival time:
- Historical traffic.
- Real-time conditions.
- Driver behavior.
- Time of day, weather, events.
- Updated continuously.

### 99.5 Surge / Dynamic Pricing

When demand exceeds supply in an area, raise price:
- Encourages supply (drivers move to area).
- Reduces demand (some riders defer).
- Geospatial: per hex.
- Updated every few seconds.

Mathematical: balance surge to clear the market.

### 99.6 Trip State Machine

Trip is a state machine with strict ordering. State transitions are events.
- Model as a saga or via a workflow engine (Uber's Cadence, predecessor of Temporal, was built for exactly this).
- Compensations for failures (refund if trip can't complete).

### 99.7 Payments

- Pre-authorize at trip start.
- Charge on completion.
- Multiple payment methods (split, expense codes).
- Integration with Stripe / Adyen / etc.

### 99.8 Scale

- Tens of millions of active drivers/riders.
- Real-time location updates from millions of devices.
- Millions of trips/day per city.

### 99.9 Variants: Food Delivery (DoorDash, Uber Eats)

Add: restaurants (different supply-side), batching deliveries (one dasher carries multiple orders), preparation time prediction, restaurant POS integration.

---

## 100. Airbnb / Booking (Marketplace + Inventory)

Searching, booking, paying for accommodations.

### 100.1 Search

- **Multi-faceted** — location, dates, party size, price, amenities.
- **Geospatial** — search by map area.
- **Ranking ML** — predict which listings will get clicks / bookings for this user.
- **Personalization** — past behavior, traveler type.

Index: typically Elasticsearch with custom scoring + a reranking model.

### 100.2 Inventory and Availability

- Calendar per listing.
- **Booking is a write-heavy contention point** — two users trying to book the same dates.
- Use database constraints / locks / optimistic concurrency.
- **No double-booking** is the absolute requirement.

### 100.3 Payments

- Hold at booking; settle to host on check-in or after.
- Multi-currency.
- Refund flows for cancellations.
- Fraud detection.

### 100.4 Messaging Between Hosts and Guests

Standard messaging service.

### 100.5 Reviews

- After-trip; bidirectional (host reviews guest, guest reviews host).
- Critical to marketplace trust.

### 100.6 Scale

- ~1B nights booked cumulatively.
- Hundreds of millions of listings touched per day.

---

## 101. Stripe / Payment Systems

Card payments, banking integrations, fraud, billing, payouts, compliance. The "easy API on top of complicated infrastructure" canonical product.

### 101.1 The Payment Flow

A simplified card payment:
1. Customer enters card on merchant's site (or via Stripe.js/Elements that tokenizes client-side).
2. Token sent to Stripe API.
3. Stripe attaches token to a `PaymentIntent`, sends to acquirer / issuer via card network (Visa, Mastercard, etc.).
4. Issuer authorizes (or declines).
5. Stripe holds the auth.
6. Capture (settle) — typically within hours/days.
7. Funds eventually settle to merchant's bank account (T+2 typical).

### 101.2 Architecture Themes

- **Idempotency** is everywhere. Every API call accepts an `Idempotency-Key`. Same key + same body → same response. Critical because retries are common and double-charging is disastrous.
- **Strong typing of money.** Currency + integer minor units. Never floats.
- **Audit log of everything.** Append-only events. Every state change is an event with full provenance.
- **Webhooks for async events.** Customer's server gets notified of state changes (payment succeeded, refund issued, dispute opened).
- **Compliance.** PCI-DSS for card data; tokenization isolates the cardholder data environment. Most merchants never see card numbers — Stripe holds them.

### 101.3 Storage

- Append-only event store as the source of truth.
- Derived databases: per-merchant balance, per-payment state, per-day reports.
- Multi-region for availability and regulatory data residency.

### 101.4 Reliability

Payments cannot lose data. Two-region active-active where possible. Heavy backup, point-in-time recovery, reconciliation jobs comparing internal state to bank statements daily.

### 101.5 Fraud Detection

- Real-time ML scoring on each payment.
- Network effects (card seen in many places, velocity).
- Rules + ML hybrid.
- 3D Secure (SCA in EU) for additional auth on risky transactions.

### 101.6 Other Stripe Products

- **Connect** — multi-party payments (Lyft pays drivers; Shopify collects from customers and pays merchants).
- **Billing** — subscriptions, proration, dunning, taxes.
- **Issuing** — issue cards (corporate cards, virtual cards).
- **Atlas** — incorporate companies.
- **Radar** — fraud.
- **Tax** — sales tax / VAT computation.

### 101.7 Lessons

- **Idempotency is not optional in payments.**
- **Event sourcing for ledger-like data.**
- **Strong API design as the product.** The hard parts are inside; the API hides them well.
- **Webhooks must be reliable.** Signed payloads, retries, configurable endpoints.

---

## 102. Dropbox / Google Drive (Cloud File Sync)

Sync files across devices and the cloud.

### 102.1 Core Challenge

Keep file system state consistent across many devices and the cloud, with offline edits and conflict resolution.

### 102.2 Architecture

- **Block storage.** Files split into blocks (typically 4 MB); blocks stored in object storage (originally S3, Dropbox migrated to its own "Magic Pocket"). Block-level dedup (same block → stored once).
- **Metadata service.** File trees, version history, sharing permissions. Sharded relational DB.
- **Sync clients.** Watch local FS for changes; upload changed blocks; receive change notifications and download blocks.
- **Notification service.** Push changes to online clients.

### 102.3 Sync Protocol

- Client computes block hashes for changed file.
- Sends hashes to server; server returns "I already have these blocks; upload only the new ones."
- Server records new file version; pushes notification to other clients.

This is essentially **content-addressable storage** for the block layer + a **versioned tree** for metadata.

### 102.4 Conflict Resolution

When two devices edit the same file offline:
- The server detects divergent versions.
- Creates a conflict copy ("foo (Alice's conflicted copy 2025-01-01).docx").
- Avoids merging text content (left to apps like Google Docs, which use OT/CRDT for true real-time merge).

### 102.5 Sharing and Permissions

- Per-file ACLs.
- Permissions inheritable from folders.
- ReBAC-style (you can access via membership in a team, group, etc.).

### 102.6 Scale

- Exabytes of user data.
- Block dedup huge: many users share common files (OS images, popular software).

### 102.7 Google Drive Specifics

- Tighter integration with Google Docs (which is OT/CRDT-based real-time collab — different problem).
- Search + AI integration.

---

## 103. Google Maps

Mapping, search, routing, traffic, Street View, places, business listings.

### 103.1 The Map Itself

- World divided into tiles at multiple zoom levels (zoom 0 = whole world in one tile; zoom 20+ = building level).
- Each tile pre-rendered (or vector-rendered client-side) and served from a CDN.
- Updated continuously as map data changes.

### 103.2 Search

- Geographic + textual + popularity ranking.
- "coffee near me" — geo + category match + ranking by ratings, distance, hours.
- Knowledge graph of places, businesses.

### 103.3 Routing

- **Road network** as a weighted graph.
- **Contraction Hierarchies / CRP / similar** — preprocessing techniques that turn shortest-path queries from `O(V log V)` Dijkstra into milliseconds.
- **Real-time traffic** — speeds learned from anonymized phone GPS streams; weights dynamically updated.
- **Multi-modal** — walking, transit, driving, biking; combined.
- **ETA models** — beyond shortest path; ML for accurate ETAs.

### 103.4 Traffic

- Phones constantly send anonymized speed data.
- Aggregate by road segment.
- Detect anomalies (accidents → slowdown → route around).

### 103.5 Places

- Massive database of POIs (businesses, landmarks).
- Continuous ingestion from many sources, deduplication, conflation.
- User-contributed reviews, photos.

### 103.6 Imagery

- Satellite imagery, aerial, Street View.
- Petabytes of image data.
- Continuously refreshed (weekly to yearly depending on importance).

---

## 104. Amazon E-Commerce

Catalog, search, recommendations, cart, orders, fulfillment, payments — across thousands of categories and many countries.

### 104.1 Catalog

- Hundreds of millions of items.
- Hierarchical (categories, attributes).
- Per-item: title, description, images, attributes, price, availability, seller.
- 3rd-party sellers ("Marketplace") add their own listings.
- Storage: distributed document/wide-column DBs.

### 104.2 Search

- Inverted index over title, description, attributes, brand.
- Per-category facets (filters).
- Ranking: relevance + popularity + conversion rate + sponsored.
- Real-time (newly listed items searchable in seconds).

### 104.3 Cart

- Per-user cart state — could be in DynamoDB or a similar KV.
- Multi-device sync.
- Abandoned cart recovery (email reminders).

### 104.4 Order

- **Order is a distributed transaction across:** payment, inventory, fulfillment, shipping, tax.
- Modeled as a saga.
- Sub-orders for multi-seller shipments.
- State machine: placed → paid → fulfilled → shipped → delivered.

### 104.5 Inventory

- Per-warehouse stock counts.
- Reservation at order time (decrement); release on cancellation.
- Hot SKUs need careful concurrency (don't oversell). Optimistic / atomic updates.

### 104.6 Fulfillment

- Routing orders to warehouses.
- Pick / pack / ship with sophisticated logistics.
- Same-day / next-day promises requiring careful capacity allocation.

### 104.7 Recommendations

- "Customers also bought" — collaborative filtering at huge scale.
- Personalized homepage.
- Email recommendations.

### 104.8 Internal Architecture

The famous 2002 Bezos memo mandated all teams expose their data via APIs and consume each other's via APIs. This birthed Amazon's microservices culture and, indirectly, AWS itself. Today Amazon retail is built on AWS like everyone else.

---

## 105. Slack / Discord (Real-Time Team Chat)

Persistent messaging organized by channels/workspaces, with presence, typing indicators, threading, search, and integrations.

### 105.1 Slack's Architecture

- **HTTP + WebSocket** — WebSocket for real-time delivery, HTTP for everything else.
- **Channel sharding.** Each channel routed to a specific server cluster.
- **MySQL via Vitess** — Slack runs Vitess at large scale.
- **Memcached, Redis** for hot data.
- **Solr / search service** for message search.
- **Job queues** for async work.

### 105.2 Discord's Architecture

Famously runs on Cassandra — trillions of messages. Their engineering blog details:
- Per-channel partitioning.
- Time-based bucketing within channels.
- Messages indexed by snowflake IDs.
- Migrated from Cassandra to ScyllaDB (faster, lower latency, fewer servers).

### 105.3 Presence

- Track which users are online and on which channels they're active.
- High write rate (every connection / disconnection / heartbeat).
- Specialized service.

### 105.4 Voice / Video

Discord especially: voice channels with low-latency audio. SFU architecture: server forwards encrypted streams to participants.

### 105.5 Notifications

Push notifications for direct messages and mentions. Per-user preferences (DND, channel mute).

### 105.6 Search

Inverted index over message content. Per-workspace; large workspaces have very large indexes. Sharded.

---

## 106. Zoom / Google Meet (Video Conferencing)

Real-time video and audio for groups.

### 106.1 SFU vs MCU

- **SFU (Selective Forwarding Unit)** — server forwards encrypted streams without decoding. Each client receives N-1 streams. Bandwidth-heavy on client. Most modern systems use SFU.
- **MCU (Multipoint Conferencing Unit)** — server decodes, mixes, re-encodes. CPU-heavy on server. Bandwidth light on client. Used historically.
- **P2P** — works for very small calls (2 participants). Doesn't scale.

Zoom's architecture is largely SFU with cloud-based servers.

### 106.2 Components

- **Signaling** — clients negotiate media via the server (offer/answer SDP, ICE candidates).
- **Media servers** — receive and forward streams. Geographically distributed.
- **TURN servers** — relay when peer-to-peer doesn't work (NAT, firewalls).
- **Recording** — record the SFU's view.

### 106.3 Bandwidth Management

- **Simulcast** — sender encodes multiple resolutions; SFU forwards the right one based on receiver's view.
- **SVC (Scalable Video Coding)** — single encode with layers; more efficient.
- **Bandwidth estimation** — adapt bitrates dynamically.

### 106.4 Quality Mechanisms

- Forward error correction.
- Retransmission (NACK).
- Audio jitter buffer.
- Background noise suppression (RNNoise, Krisp-style ML).
- Echo cancellation.

### 106.5 Scale

- Millions of concurrent meetings.
- Billions of meeting-minutes per day.
- Geographic distribution to minimize latency.

---

## 107. GitHub

Code hosting, CI, code review, issue tracking. Owned by Microsoft.

### 107.1 Repository Storage

- Git repositories on disk (or distributed FS).
- **Spokes** — GitHub's distributed Git storage layer.
- Replication across servers in a region; failover.

### 107.2 The Web App

- Ruby on Rails monolith ("the Monolith"); Vitess-sharded MySQL.
- Sub-systems gradually extracted to services.

### 107.3 Search

- Code search at GitHub scale is hard: trillion+ files, complex tokenization (identifiers, special characters).
- New code search (2023+) uses Blackbird, custom-built; ngram-based with custom postings encoding.

### 107.4 CI

- Self-hosted runners and GitHub-hosted runners (VM per job).
- Workflow files trigger jobs; job scheduler dispatches to runners.
- At scale: thousands of CI minutes per second.

### 107.5 Pull Requests

- Compare branches; render diffs server-side.
- Merge conflicts shown.
- Review state machine.
- Webhooks to integrations.

### 107.6 Scale

- 100M+ developers.
- 400M+ repositories.
- Petabytes of code.

---

## 108. CDN (Cloudflare, Akamai, Fastly)

We covered the concepts in §13. Internal architecture of a modern CDN:

### 108.1 Edge Servers (PoPs)

- Globally distributed: 100s–300s of locations.
- Anycast IP routes user to nearest PoP.
- Each PoP has many servers; typically Linux + custom proxy software (NGINX, Envoy, custom).

### 108.2 Cache Tiers

- **L1** at the edge per server.
- **L2** at the PoP (shared across servers).
- **Regional shield** to consolidate cache fills before hitting origin.
- **Origin shield** — last layer before origin.

### 108.3 Cache Coherence

- Origin sends `Cache-Control` headers.
- Purges via API: `purge by URL`, `purge by tag`, `purge everything`.
- Tag-based invalidation: tag responses with logical groups; purge all responses with a tag.

### 108.4 Compute

Workers / edge functions described in §67.

### 108.5 Security

- TLS termination.
- WAF, bot management.
- DDoS scrubbing (massive bandwidth at the edge).
- Rate limiting at the edge.

### 108.6 Cloudflare Specifics

- Workers KV, R2, D1, Durable Objects.
- Argo Smart Routing — uses Cloudflare's network for transit, often faster than open internet.
- Magic Transit / Spectrum for non-HTTP traffic.

### 108.7 Akamai

- Pioneer (1998); deepest edge footprint.
- Strong on enterprise, media, security.

### 108.8 Fastly

- Programmable VCL (now Fastly Compute@Edge with WASM).
- Sub-second purges (vs. minutes elsewhere historically).
- Strong with publishers, news.

---

## 109. DNS at Hyperscale (1.1.1.1, 8.8.8.8)

Public recursive resolvers.

### 109.1 Architecture

- **Anycast** — same IP from many locations.
- **Per-PoP** — local cache + fallback to authoritative servers.
- **Aggressive caching** with respect for TTLs.
- **DNSSEC validation.**
- **Privacy** — DoH/DoT support; query logging policies (Cloudflare claims no IP logging).

### 109.2 Optimizations

- **Pre-fetch** popular domains before TTL expiry.
- **Negative caching** — cache NXDOMAIN responses.
- **Query name minimization** — only send necessary parts of query at each step.

### 109.3 Scale

- 1.1.1.1: trillions of queries/month.
- Sub-15 ms median responses globally.

---

## 110. Ad Serving (Google Ads, Meta Ads)

Real-time bidding for ad slots, billions of times per day.

### 110.1 The Auction Pipeline

For each ad opportunity (page load, search, video):

1. **Targeting.** Find ads that match the context (search terms, page topic, user demographic).
2. **Quality / Pacing / Eligibility.** Filter for ad health, advertiser budget, daily/hourly pacing.
3. **Bidding.** Each candidate ad's bid (or predicted bid via ML) is computed.
4. **Quality score.** Predict CTR (click-through rate); winning bid blends bid × CTR.
5. **Auction.** Second-price (Google's old GSP) or first-price (modern). Pick winner(s).
6. **Render.** Insert into page / SERP / video.
7. **Track.** Impressions, clicks, conversions for billing and optimization.

### 110.2 Latency

The whole thing in tens of milliseconds. Massive parallelism, heavy caching, ML inference at scale.

### 110.3 Storage

- **Advertiser accounts, campaigns, budgets.** Sharded relational.
- **Bids** computed in real time per impression.
- **Logs of impressions/clicks** — Kafka → analytics warehouses.

### 110.4 ML

- CTR prediction (deep models, trained on petabytes of click data).
- Conversion prediction.
- Lookalike audiences.
- Bid optimization (smart bidding).

### 110.5 Privacy and Compliance

- GDPR, CCPA, ePrivacy.
- Move from third-party cookies to Privacy Sandbox / SKAdNetwork / similar.
- Consent management.

---

# Part 10 — Methodology

## 111. The System Design Interview Framework

System design questions are open-ended. A structured approach helps you cover everything in 45–60 minutes.

### 111.1 The Standard Flow

1. **Clarify requirements (5 minutes).** Ask functional and non-functional. Don't dive in until you know what you're solving.
2. **Estimate scale (5 minutes).** Users, QPS, storage, bandwidth.
3. **High-level design (10 minutes).** Boxes and arrows. APIs. Major components.
4. **Deep dive (15–20 minutes).** Pick the most interesting/contested parts; go deep.
5. **Address bottlenecks and scale (10 minutes).** Where does this break? How do you scale it?
6. **Discuss trade-offs (5 minutes).** What did you choose, what didn't you, why?

### 111.2 Clarifying Questions to Always Ask

- **Who are the users?** Internal? Consumer? Enterprise?
- **What scale?** "What's the order of magnitude?" — 1K users vs 1B users is a different system.
- **Read-heavy or write-heavy?** What's the ratio?
- **Latency expectations?** (Tens of ms? Seconds? Async OK?)
- **Consistency expectations?** Strong everywhere? Eventual fine?
- **Geographic scope?** One region? Global?
- **Reliability target?** Three nines or five?
- **Constraints / non-goals.** Often things explicitly out of scope simplify the answer.

### 111.3 The High-Level Design

Sketch:
- Clients (web, mobile, third-party).
- Edge / CDN.
- Load balancer.
- API servers / gateway.
- Core services.
- Data stores.
- Caches.
- Async / queue / streaming.
- External services / integrations.

Label data flow. Define the API.

### 111.4 Where to Go Deep

The interviewer is looking for depth in **the part of the system that contains the most interesting trade-offs.** For a feed system, that's usually fan-out and ranking. For a video system, that's encoding and delivery. For a payment system, that's idempotency, consistency, and reconciliation.

Ask: "Where would you like me to go deep?" or pick the obvious hard part and start.

### 111.5 What Interviewers Want to See

- Clarifying — you don't barrel ahead with assumptions.
- Estimating — you can do the math.
- Trade-offs — every decision has alternatives; you can name them and justify.
- Failure modes — you think about what breaks, not just what works.
- Concrete components — you know what real tools / techniques solve real problems.
- Communication — clean diagrams, clear narrative, doesn't lose the thread.

### 111.6 Common Mistakes

- Diving into details without clarifying scope.
- Picking technologies without explaining why.
- Drawing a perfect diagram with no labels or no API definition.
- Ignoring failure modes.
- Inventing exotic solutions when boring ones work.
- Not noticing your own contradictions ("eventual consistency for payments").

### 111.7 What to Read

- *Designing Data-Intensive Applications* (Martin Kleppmann) — the bible.
- Google SRE books (free online).
- Engineering blogs of major companies (Netflix, Uber, Discord, Stripe, Cloudflare, Meta, Google, AWS).
- *The Art of Scalability* — for the cube and growth thinking.
- Papers: Dynamo, Bigtable, GFS, Spanner, Kafka, MapReduce, Borg, Chubby, ZooKeeper, Cassandra, Raft, Paxos.

---

## 112. Estimation and Back-of-the-Envelope Math

Engineers often blank when asked "how much storage?" Practice; it gets routine.

### 112.1 Useful Numbers

- **Seconds in a day:** ~86,400 (round to 100,000).
- **Seconds in a year:** ~30M (more precisely ~31.5M).
- **Bytes:** 1 char ≈ 1 byte (ASCII), 2–4 (Unicode); 1 image ≈ 100 KB–5 MB; 1 minute video ≈ 50–200 MB at typical bitrates.
- **Servers:** modern server, ~64 cores, ~256 GB RAM, ~10 TB SSD. Handles ~10K RPS for moderate work, fewer for heavy work.
- **Disk:** SSD ~ 500 MB/s to GB/s; NVMe several GB/s. HDD ~150 MB/s sequential, much slower random.
- **Network:** 10 Gbps ≈ 1.25 GB/s. 100 Gbps within DC.

### 112.2 Working Through an Example

"Design a feed for 100M DAU."

- 100M DAU; assume each loads feed 5x/day → 500M feed loads/day.
- /day → /sec: 500M / 100K ≈ 5K RPS feed loads (avg). Peak ~3× = 15K RPS.
- Each feed load: ranking ~20 candidates; needs candidate fetch, feature fetch, scoring.
- Each user posts 0.1×/day on average → 10M posts/day → 100 posts/sec avg, 300 peak.
- Fan-out: avg 100 followers → 10M × 100 = 1B fan-out writes/day → ~10K RPS.
- Storage: 10M posts × 1 KB metadata × 365 × 5 years ≈ 18 TB.
- Photo storage: 10M posts × 0.5 photo each × 1 MB × 365 × 5 years ≈ 9 PB. (Massive.)

These numbers shape your design: 15K RPS for reads is moderate; 10K RPS fan-out writes plus 9 PB storage is significant.

### 112.3 Common Hugely-Wrong Estimates

- Confusing GB and Gb (factor of 8).
- Forgetting peak-to-average ratio (often 3–10×).
- Forgetting replication overhead (3× or so).
- Forgetting compression (factor of 3–10× for text).

### 112.4 Sanity Check

When numbers come out absurd, you're probably off by a factor. Compare to known systems: Twitter ~500M tweets/day → ~6K writes/sec. Google Search ~100K QPS. AWS S3: trillions of objects. If your number is 100× any known system, double-check.

---

## 113. Trade-off Analysis and Architecture Decision Records

### 113.1 Every Decision Has a Trade-off

The good architect makes them explicit.

For each major decision:
- **Options considered.** Even the rejected ones.
- **Decision criteria.** What we optimized for.
- **Choice made.** And why.
- **What we give up.** Honest costs.
- **Reversibility.** Hard to undo or easy?

### 113.2 Architecture Decision Records (ADRs)

Lightweight templates:

```
# ADR-007: Use PostgreSQL for primary OLTP store

## Status
Accepted

## Context
We need an OLTP store for orders, users, inventory. Workload is
mostly point lookups, with some short-range queries; expected ~5K
write QPS and 50K read QPS at year 3.

## Decision
Use PostgreSQL 16 on managed RDS, with read replicas.

## Consequences
+ Mature, battle-tested
+ Rich features (JSONB, partial indexes, etc.)
+ Team's existing expertise
- Single-instance write throughput limit (~20K writes/sec)
- Will need sharding (Citus / Vitess / app-level) if we 10x

## Alternatives considered
- DynamoDB: no relational features, expensive at this scale
- CockroachDB: more complex ops, less team familiarity
- MySQL: roughly equivalent; team prefers Postgres
```

ADRs live in the repo. Future engineers (or you, in 18 months) thank past you.

### 113.3 The Two Pizzas of Reversibility

Bezos: "Most decisions are two-way doors — easy to walk back. A few are one-way."

- **Two-way door:** schema column rename, framework choice, deployment style. Decide quickly; reverse if wrong.
- **One-way door:** primary database choice, encryption scheme, public API contract. Decide carefully; you may not get to redo it.

Calibrate effort accordingly.

### 113.4 The Default Bias Toward Boring

Choose mature, well-known tools by default. Reach for the new and exotic only when the boring choice has a real problem you can articulate. "Postgres + Redis + S3 + Kafka" is the answer to most system design questions, and that's good.

---

## 114. Common Anti-Patterns

A non-exhaustive list of mistakes we all make and re-make.

### 114.1 Distributed Monolith

Microservices that must deploy together to work. All the cost of distributed systems, none of the benefits. Causes: shared databases, synchronous chains, tight contract coupling.

Cure: enforce service boundaries (no shared DBs); use async events to decouple; version APIs.

### 114.2 The God Service

One service that knows about everything. Becomes a bottleneck and a single point of failure.

Cure: split by domain; use events to push notifications instead of polling.

### 114.3 Chatty APIs

N round trips to render one page. Death by latency.

Cure: aggregate on the server (BFF); GraphQL; batched APIs.

### 114.4 Database as a Queue

Polling a `jobs` table for "TODO" rows. Works for low scale; collapses at moderate scale (lock contention, bloat, vacuum problems).

Cure: real queue (SQS, Redis, Kafka). Postgres + careful design (SKIP LOCKED) can work for medium scale.

### 114.5 Premature Sharding

Sharding before you need to. Adds complexity for benefits you may never realize.

Cure: vertical scale first; replicas for reads; shard when the metrics demand.

### 114.6 Premature Microservices

Splitting a small product into microservices because "Netflix does it." Three engineers cannot operate twenty services.

Cure: modular monolith; extract services when the team and the product justify it.

### 114.7 Caching as Performance Solution to Bad Code

Cache hides slow queries. Helps until the cache misses, then everything dies.

Cure: fix the query first; cache on top of correct, reasonably-performant code.

### 114.8 Synchronous Calls for Async Work

Caller waits for "send email" or "render report" or "transcode video" — for seconds or minutes, blocking a worker thread.

Cure: enqueue and return immediately; notify on completion (webhook, polling, push).

### 114.9 Single Master, No Failover Plan

A single primary DB without an exercised failover plan. Works until it doesn't.

Cure: multi-AZ with automated failover; tested DR plan; runbooks.

### 114.10 Logs as Database

Searching gigantic logs for "what happened to user 42 yesterday." Logs are the wrong shape; they aren't indexed for that.

Cure: structured events to a real query layer (event log, OLAP store, Honeycomb-style wide events).

### 114.11 No Idempotency

Mutating endpoints with no idempotency keys. Retries become bugs.

Cure: idempotency from day one for any non-idempotent operation.

### 114.12 No Observability Until It's Too Late

"We'll add monitoring when we have time." You won't.

Cure: structured logs, metrics, traces from day one. They cost almost nothing early; they're invaluable later.

### 114.13 Doing Auth Yourself

Custom session handling, custom OAuth, custom password hashing. Almost guaranteed to be wrong.

Cure: use proven libraries / services (Auth0, Cognito, Clerk, Keycloak, WorkOS) until you have a real reason not to.

### 114.14 Tightly Coupled Schema

Your microservice's schema is the public contract. Any change breaks consumers.

Cure: API ≠ schema. Versioned APIs that translate to/from internal storage.

### 114.15 Magic Constants

Hard-coded values for timeouts, limits, retry counts.

Cure: configurable via environment / feature flags. Different envs, different needs.

### 114.16 Optimizing Without Measuring

"This Redis lookup is slow." How do you know?

Cure: profile, measure, fix the hot path. Premature optimization wastes effort and adds complexity.

### 114.17 Big Bang Rewrites

"This is too messy; let's rewrite." You'll discover the messy parts encoded years of edge-case fixes.

Cure: strangler-fig pattern — incrementally replace. Run old and new in parallel; migrate features one at a time.

### 114.18 Treating Flaky Tests as Acceptable

"Just retry the test." That flake is leaking from real code. Future you will be debugging a real outage that started as a "flake."

Cure: zero tolerance for flaky tests. Investigate; fix root cause.

### 114.19 No Sharding Key in Logs / Metrics / Errors

When things break, you can't tell which tenant / user / shard.

Cure: tenant ID, user ID, shard, region in every log line, every metric label, every error.

### 114.20 Surprise Egress

Sudden cloud bill spike. Often: a new feature inadvertently shuttling data across regions or out to the internet.

Cure: cost dashboards per service; alerts on egress anomalies; review architectures for hidden cross-region traffic.

---

## 115. How to Keep Learning

System design is a skill compounded over years.

### 115.1 Read

- Engineering blogs of large companies (Netflix Tech Blog, Uber Engineering, Meta Engineering, Stripe Eng, Cloudflare Blog, AWS Builders' Library).
- Foundational papers (cited above).
- *Designing Data-Intensive Applications* annually.
- *Site Reliability Engineering* and *The SRE Workbook* (Google).
- Hardware reality: read whatever's current on CPU, NVMe, network speeds — these change the math.

### 115.2 Build

Read about a system; build a tiny version. Lessons from "I made a toy URL shortener with sharding and replication" stick more than reading 10 blog posts.

### 115.3 Operate

Run something in production. The difference between "I designed" and "I designed and operated" is enormous. Operating teaches you what your design assumed but didn't ensure.

### 115.4 Postmortems

Read public ones (AWS post-event summaries, Cloudflare blogposts, GitLab incidents, etc.). Each is a free education in what breaks.

### 115.5 Whiteboard

Practice designing systems with peers. Verbalize trade-offs. The act of explaining surfaces holes.

### 115.6 Question Defaults

When something works, ask "why does this work?" Understanding is built from small, persistent curiosity.

### 115.7 Stay Current

The field changes. eBPF wasn't a thing in production a few years ago; now it's everywhere. WebAssembly is starting to matter. LLMs are reshaping system design (vector stores, agents, semantic caching). What's a quirk today is mainstream in three years.

### 115.8 Stay Grounded

…but most things don't change. The CAP theorem is the same. Latency numbers are the same (modulo a factor here and there). The fallacies of distributed computing apply forever. The fundamentals are what carry you across decades.

---

# Closing

System design is, at the end, **the art of trade-offs**. There is no single correct architecture for any problem. The best architects internalize a vocabulary of components, patterns, and failure modes; they ask the right clarifying questions; they reach for the boring proven tool by default and the exotic one only when justified; they design for operability, observability, and human limits as much as for technical correctness; and they hold their designs lightly, knowing that requirements evolve, scale changes, and yesterday's right answer becomes today's tech debt.

If you take one thing from this document, let it be this: **the goal is not to build the most impressive system, but the system that best serves the problem with the resources, constraints, and uncertainty you actually have.** Bigger isn't better. Newer isn't better. The right answer is the simplest design that meets requirements and admits change as you learn more.

Build things. Operate them. Read postmortems. Read papers. Question defaults. Stay curious. The systems you build will get better, and the systems built around you will continue to surprise you in their complexity, fragility, and beauty.

— *End of handbook.*
