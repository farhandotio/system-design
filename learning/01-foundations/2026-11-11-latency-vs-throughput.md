# 2026-11-11: Latency vs Throughput

**Lesson:** [Latency vs Throughput](https://freesystemdesign.com/#/latency/learn)

## The Idea

“Make it faster” can mean two different things:

- **Latency** is how long one request takes from start to finish.
- **Throughput** is how many requests or how much data the system handles over time.

Think of a water pipe. Latency is how long one drop takes to travel through it. Throughput is how much water comes out each second. A long pipe can have high latency and still carry lots of water if it is wide enough.

## Why They Matter

Network distance, extra network stops, connection setup, waiting in a queue, and server work can all add latency. Throughput depends on how much work the system can handle at once. Adding servers can raise total throughput, but it does not automatically make one request finish sooner.

Some choices affect both metrics. Batching can move more work together, but each item may wait longer. Pipelining can keep more requests moving at once. Parallel work can finish one task sooner, but uses more CPU and memory.

```text
One request takes 800 ms: its latency is 800 ms.
More servers can handle more requests at once,
but that request may still take 800 ms.
```

Video streaming needs enough throughput to send lots of data. Online games care a lot about low latency because players notice a slow response.

## Takeaway

Before trying to make a system “faster,” ask: do we need each request to finish sooner, or do we need to handle more requests at once? The answer points to different fixes.
