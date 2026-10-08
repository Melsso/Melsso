# Sofiane Mallem

**Python backend developer** · Heilbronn, Germany · Open to new roles

I build and operate production backend systems: async APIs, real-time services, data pipelines, and the infrastructure around them. Most recently, I owned a CAD-to-rendering pipeline running across 5+ Linux servers and feeding YOLOv5 model training. My side projects tend to be the kind of infrastructure most people import rather than write: a cache server, a task queue, a rate limiter, a vector database, an auth service.

[LinkedIn](https://www.linkedin.com/in/sofiane-mallem-b87302170/) · [Portfolio](https://sofiane-mallem.netlify.app/) · [Email](mailto:sofiane.mallem.07@gmail.com)

## Projects

- **[Lad](https://github.com/Melsso/lad)** - A personal, locally hosted ChatGPT/Claude-style chat app built with FastAPI, React, Postgres/pgvector, and Ollama, with no external LLM API. Chats run in a lighter chat mode or a larger agent mode. Both use an MCP-based tool-calling loop (each tool is its own stdio MCP server) with web search and cross-chat semantic memory recall over rolling conversation summaries. Agent mode adds a sandboxed shell and file uploads. The sandbox is an offline, credential-free container on an internal Docker network, running as non-root with dropped capabilities and CPU, memory and process limits, and the API only accepts requests from nginx. Replies stream over SSE. Dockerized behind nginx with a single startup script, and tested with pytest (including real Postgres via testcontainers), Vitest and MSW, with GitHub Actions CI running ruff, mypy, oxlint and tsc.

- **[Hang](https://github.com/Melsso/hang)** - A social dating platform where users register with email/password or Google OAuth, edit profiles with images stored in S3-compatible storage, swipe on other users, and chat after a mutual match. Real-time messaging runs on WebSockets with typing indicators, read receipts and cursor-based pagination. Redis Pub/Sub propagates events across multiple stateless FastAPI instances behind Nginx, with per-user rate limiting, Prometheus metrics and Grafana dashboards. Load tested end to end through Nginx with zero dropped messages at up to 2,000 concurrent WebSocket connections, a test that also exposed and led to a fix for a database-session leak. Built with FastAPI, PostgreSQL, React and TypeScript, Dockerized, with GitHub Actions CI running ruff, mypy and tests against real Postgres and Redis containers.

- **[Durden](https://github.com/Melsso/durden)** - An object detection API built with FastAPI and Ultralytics YOLO. Clients upload an image and get back labels, confidence scores, bounding boxes and inference time, with optional per-request model selection across multiple loaded YOLO models. Models load in a background task at startup, so the service reports readiness through `/health` and `/status` and returns 503 on `/predict` until they are ready. Ships with a dependency-free web UI (HTML/CSS/JS with canvas overlays and a confidence slider). CPU-only PyTorch Docker image, with GitHub Actions CI running ruff and pytest, publishing to GHCR and deploying to Google Cloud Run via workload identity federation.

- **[Sentinel](https://github.com/Melsso/sentinel)** - A self-contained authentication service built with FastAPI, Postgres, and Redis. Covers registration, email verification, login, password reset and change, and account deletion with Argon2 hashing. Access tokens are tied to sessions and die the moment a session is revoked, while atomic refresh-token rotation with reuse detection revokes the whole session if a token is replayed. Abuse protection includes Lua-backed rate limiting, per-IP account lockout, enumeration-resistant responses, and trusted-proxy handling. Adds session management, hashed-email audit logs, and background email delivery with retries. Dockerized, with CI running ruff, mypy, pytest against real Redis, pip-audit, and an end-to-end smoke test on the Compose stack.

- **[Queue Task Manager](https://github.com/Melsso/queue-task-manager)** - An asynchronous task queue built with FastAPI and SQLAlchemy: a broker plus workers that register capabilities, long-poll for tasks, and report results. Features priorities with optional aging, named queues, capability-based routing, retries with exponential backoff, timeouts, idempotency keys, and fencing tokens so a stale worker can never overwrite a newer attempt. Heartbeats and recovery loops handle dead workers and lost assignments with at-least-once delivery. Runs on SQLite or PostgreSQL (`FOR UPDATE SKIP LOCKED`), with async and sync Python clients, a Prometheus `/metrics` endpoint, and separate client and worker credentials. Dockerized, with CI running the suite on both databases, including a multi-process claim test.

- **[Rate Limiter](https://github.com/Melsso/rate-limiter)** - An asynchronous rate limiting library for FastAPI backed by Redis, supporting Fixed Window, Sliding Window, and Token Bucket algorithms. Atomic Lua scripts keep limits exact under concurrency, and it plugs in as a route decorator, dependency, or pure ASGI middleware. Supports weighted request costs, per-tier limits, IPv6-aware client identification, and custom 429 responses. Handles Redis outages with a circuit breaker and an in-memory fallback limiter, and works with Redis, Valkey, and Redis Cluster. Fully typed and tested with pytest against real Redis containers, with GitHub Actions CI running ruff, mypy, and a version matrix across Redis 5 to 8, Valkey, and a 3-master cluster.

- **[Mini Cache](https://github.com/Melsso/mini_cache)** - A Redis-wire-compatible (RESP2) cache server built from scratch in Python/asyncio with no runtime dependencies, usable with `redis-cli` and standard Redis clients. Supports TTL expiry, `maxmemory` with LRU eviction, password auth, and client limits, plus AOF persistence with group-committed fsync, crash-safe torn-tail repair, and background log rewrite. Primary/replica replication uses per-replica queues so a slow replica never stalls the primary, with heartbeat-based failure detection and auto-reconnect. A client-side consistent-hashing router adds connection pooling, pipelining, and timeouts across shards. Deployable as a multi-shard cluster with Docker Compose and tested over real sockets in CI with pytest, ruff, and mypy.

- **[Search Engine](https://github.com/Melsso/search-engine)** - A vector database built from scratch in Python: exact brute-force search as a correctness baseline, a multi-layer HNSW index implementing the paper's diversity-preserving neighbor-selection heuristic, named collections with their own dimension, metric and index backend, exact-match metadata filtering, and atomic JSON snapshot persistence. Exposed through a FastAPI HTTP layer and deployable with Docker Compose. Benchmarked honestly: a first fixed-`ef_search` run looked like an 81x speedup but hid recall collapsing to 59%, so the real comparison tunes `ef_search` to hold about 95% recall, where HNSW is 1.7x faster at 1,000 vectors and 10.6x faster at 80,000, with a steep build-time cost (144s vs 0.08s). Tested with pytest (HNSW recall measured against brute force, the API through real HTTP requests), with ruff and mypy in CI.

## Background

- **Education:**
  - Software Engineering Course at 42 Heilbronn;
  - B.Sc. Computer Science, University of S.T. Houari Boumediene, Algiers
- **Languages:**
  - English (fluent)
  - French (native)
  - Arabic (native)
  - German (A1)

## Tech

| | |
|---|---|
| **Languages** | Python, SQL, TypeScript, JavaScript, Bash, C/C++ |
| **Backend** | FastAPI, async Python, REST, WebSockets, OAuth, SQLAlchemy |
| **Data** | PostgreSQL (pgvector), Redis, Pandas |
| **Infrastructure** | Docker, Nginx, Ansible, GitHub Actions, Google Cloud Run, Prometheus, Grafana |
| **ML / AI** | YOLO object detection and training pipelines, Ollama, MCP, AI-assisted development (Claude Code, Cursor) |
| **Testing** | pytest, Testcontainers, Vitest, ruff, mypy |

## How I work

- **Test against the real thing.** Real Postgres, Redis and sockets in CI rather than mocks wherever possible.
- **Measure before claiming.** Load tests, recall-vs-speed benchmarks and failure injection over assumptions.
- **Own it end to end.** From design and implementation to deployment, monitoring and incident response.

## Get in touch

I'm looking for my next role as a Python / backend developer. The quickest way to reach me is [email](mailto:sofiane.mallem.07@gmail.com) or [LinkedIn](https://www.linkedin.com/in/sofiane-mallem-b87302170/).
