# Hi, I'm Sofiane 👋

Python backend developer in Heilbronn, Germany. I build and operate production backend systems: real-time services, data pipelines, ML serving, and the infrastructure around them. Most recently I owned a CAD-to-rendering pipeline across 5+ Linux servers that fed YOLOv5 training.

📫 [LinkedIn](https://www.linkedin.com/in/sofiane-mallem-b87302170) · [Portfolio](https://sofiane-mallem.netlify.app/) · sofiane.mallem.07@gmail.com

🌍 Open to junior backend, platform and ML engineering roles (English, French, Arabic; learning German)

## Featured projects

| Project | What it is |
|---|---|
| [**Hang**](https://github.com/Melsso/hang) | Real-time dating/chat platform on FastAPI, Redis Pub/Sub and Nginx. Load-tested at 2,000 concurrent WebSockets with zero message loss across 190,000 messages. |
| [**LAD**](https://github.com/Melsso/lad) | Fully local ChatGPT-style assistant: MCP tool-calling agent, pgvector memory and a sandboxed shell, on Ollama with no external API. |
| [**Human Move**](https://github.com/Melsso/human-move) | Chess engine with three human-like strengths: Lichess pipeline, trained policy networks, a hand-written alpha-beta search, evaluated against Stockfish with confidence intervals ([live demo](https://human-move-945278219267.europe-west1.run.app/)). |
| [**Durden**](https://github.com/Melsso/durden) | YOLO object-detection API deployed on Google Cloud Run with keyless CI/CD ([live demo](https://durden-cnvhoj5qha-ew.a.run.app/)). |
| [**Sentinel**](https://github.com/Melsso/sentinel) | Auth service with session-bound tokens, refresh rotation with reuse detection, Lua-backed rate limiting and Argon2. |
| [**Queue Task Manager**](https://github.com/Melsso/queue-task-manager) | Async task queue with capability routing, retries, fencing tokens and at-least-once delivery on SQLite or Postgres. |

## Systems built from scratch

- Rate limiter (Redis + Lua, circuit breaker) · Redis-compatible cache server (AOF, replication, consistent hashing) 
- Vector database (HNSW, benchmarked against brute force)

## Stack

Python · FastAPI · PostgreSQL · Redis · Docker · Nginx · GitHub Actions · Google Cloud Run · PyTorch · TypeScript/React

