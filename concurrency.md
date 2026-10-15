# Concurrency and Parallelism

## Distinguish the Concepts

- **Concurrency**: Structuring a program so multiple tasks can make progress (possibly interleaved). Possible even on one core.
- **Parallelism**: Actually executing multiple tasks at the same time (requires multiple cores or hardware).

Design for concurrency; parallelism is a runtime benefit when hardware allows.

## Core Principles

- Profile first. Introduce concurrency only when measurement shows a real bottleneck (I/O-bound or CPU-bound).
- Prefer the simplest model that solves the problem.
- Minimize shared mutable state—the root of most concurrency bugs. Prefer message passing, queues, or immutable data.
- Use high-level libraries and primitives rather than hand-rolled locks and threads when possible.
- Express parallelism at the highest practical level of abstraction.

## Choosing a Model

- **I/O-bound** (network, disk, many waiting operations): async/await or event-driven models often work well (high concurrency with low thread overhead).
- **CPU-bound**: threads, processes, or data-parallel libraries. In languages with a GIL (classic Python), processes or free-threaded builds may be needed for true parallelism.
- **Isolation needed**: processes or actors.

## Safety Practices

- Document any shared state and the synchronization strategy.
- Prefer thread-safe collections and high-level constructs (task groups, futures, channels).
- Avoid blocking inside async event loops.
- Be careful with cancellation and cleanup.
- Test concurrent code under load and with race-condition detectors when available.

## Common Pitfalls

- Adding threads/async without measuring.
- Shared mutable state without proper synchronization.
- Over-parallelizing small work (overhead exceeds gains).
- Blocking the event loop.
- Ignoring the cost of context switching or lock contention.

Concurrency increases complexity. Add it only when the benefit is clear and the design stays understandable.
