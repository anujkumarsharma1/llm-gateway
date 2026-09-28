# llm-gateway

A Go gateway in front of self-hosted LLMs, plus a reproducible measurement of which inference engine should serve which kind of request.

**Status:** planned. The repo currently holds only a scaffold.

## What it does
Routes latency-sensitive traffic to SGLang and throughput-heavy batch traffic to vLLM, with streaming, retries, circuit breaking, semantic caching and per-key rate limiting. The main deliverable is the benchmark study of whether the split beats either engine alone.

## How it's built
- Go gateway: streaming proxy, model routing, retries with backoff, circuit breaker, fallback to a smaller model.
- Semantic cache with a tunable similarity threshold.
- Token-based rate limiting and cost accounting per API key.
- OpenTelemetry traces and Grafana dashboards.

## How to run
    docker compose up
    go run ./cmd/bench --config configs/mixed_workload.yaml

## What it measured
| Metric | vLLM only | SGLang only | Routed |
|---|---|---|---|
| Throughput (tokens/sec) | not yet measured | not yet measured | not yet measured |
| p99 time to first token | not yet measured | not yet measured | not yet measured |
| Cost per million tokens | not yet measured | not yet measured | not yet measured |
| Semantic cache false-hit rate | not yet measured | | |

## Hardware and method
State the exact GPU, model, quantisation and workload used, so someone else can reproduce it.
