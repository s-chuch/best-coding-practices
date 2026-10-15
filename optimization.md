# Optimization Guide

## The Right Order

1. **Correctness and clarity first** — Get it working and readable.
2. **Profile with realistic data** — Identify the actual bottlenecks (usually ~10% of the code accounts for ~90% of runtime).
3. **Algorithm and data structure improvements** — These give the biggest gains.
4. **Micro-optimizations last** — Only on proven hot paths, and only if the benefit outweighs the readability cost.
5. **Measure before and after** — Keep the change only if it meaningfully improves the metric that matters (latency, throughput, memory, etc.).

## Knuth’s Full Guidance

> We should forget about small efficiencies, say about 97% of the time: premature optimization is the root of all evil. Yet we should not pass up our opportunities in that critical 3%.
>
> A good programmer will not be lulled into complacency by such reasoning, he will be wise to look carefully at the critical code; but only after that code has been identified.

## Common High-Impact Techniques

- **Right data structure**: Hash map/set instead of linear scan in a list. Heap for top-k. Sorted array + binary search when appropriate.
- **Avoid repeated work**: Cache results, hoist invariants out of loops, use memoization for pure functions.
- **Early exits / short-circuiting**: Stop as soon as you have the answer.
- **Bulk operations**: Vectorized operations, batch I/O, bulk database inserts instead of one-by-one.
- **Reduce allocations and copies**: Especially in hot loops.
- **Leverage the compiler/runtime**: Write clear code so optimizers can do their job (constant folding, inlining, strength reduction, etc.).
- **Parallelism and concurrency**: Only when the problem is parallelizable and the overhead is worth it. Prefer higher-level constructs (thread pools, async, data-parallel libraries) over manual threading when possible.

## What to Avoid

- Optimizing before measuring.
- Sacrificing readability on non-critical paths.
- Clever micro-optimizations that the compiler already does better.
- Premature parallelization that adds complexity and bugs.

## Checklist Before Committing an Optimization

- [ ] Baseline measurement recorded
- [ ] Bottleneck confirmed by profiler
- [ ] Algorithm/data structure considered first
- [ ] Change is as small as possible
- [ ] Correctness tests still pass
- [ ] New measurement shows meaningful improvement
- [ ] Readability impact is acceptable or documented
- [ ] Non-obvious trade-offs are commented
