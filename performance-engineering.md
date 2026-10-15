# Performance Engineering

Performance work is systematic, not anecdotal. Define objectives, measure, change one thing, measure again.

## Methodology

1. **Set objectives**: Latency percentiles, throughput, resource budgets. Without a target, optimization has no stopping condition.
2. **Establish a baseline**: Measure the current system under realistic load.
3. **Profile**: Find the actual bottleneck (CPU, memory, I/O, network, lock contention, algorithmic). Tools vary by language and layer (system profiler → application profiler → micro-benchmark).
4. **Hypothesize and change**: Make one change aimed at the measured bottleneck.
5. **Re-measure**: Keep the change only if it moves the objective and the readability cost is acceptable.
6. **Repeat** until the objective is met or further gains are not worth the complexity.

## Levels of Analysis

- System (CPU, disk, network saturation).
- Application (hot functions, allocation rates, lock waits).
- Algorithmic (complexity, data structures, caching).
- Micro (instruction mix, cache misses)—only after higher levels are ruled out.

## Common Pitfalls

- Optimizing without a profile ("I think this is slow").
- Micro-optimizing code that is not on the critical path.
- Changing multiple things at once so the cause is unclear.
- Ignoring the cost of the optimization to future readers.
- Benchmarking in unrealistic conditions (cold cache, tiny data, no concurrency).

## Supporting Practices

- Continuous performance tests or budgets in CI for critical paths.
- Record non-obvious optimizations with the measurement that justified them.
- Prefer algorithmic and data-structure improvements over low-level tweaks.

Performance engineering is applied measurement. The practices in the profiling guide are the tactical layer; this is the process that keeps the work honest.
