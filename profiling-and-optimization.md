# Profiling and Optimization Guide

## Core Rule

Donald Knuth: *"We should forget about small efficiencies, say about 97% of the time: premature optimization is the root of all evil. Yet we should not pass up our opportunities in that critical 3%."*

**Process**:
1. Make it correct and clear.
2. Profile with realistic data and workloads.
3. Identify the true hotspots (often a small fraction of the code).
4. Optimize algorithms and data structures first.
5. Measure before and after. Keep only changes whose benefit outweighs the cost in readability and maintenance.
6. Document non-obvious optimizations.

## What to Measure

- Latency (p50, p95, p99).
- Throughput.
- Memory (peak, allocations, leaks).
- CPU time and hotspots.
- I/O or database time when relevant.

Establish a baseline before changes.

## Tools by Language / Environment

### Python
- cProfile / profile (function-level).
- line_profiler (line-level).
- Scalene, Pyinstrument (sampling, lower overhead).
- memory_profiler.
- Linux `perf` (with Python 3.12+ support).

### JVM / Java
- JVisualVM (bundled).
- async-profiler.
- YourKit, JProfiler (commercial).

### Native / C / C++
- `perf` (low-overhead sampling, production-friendly).
- Valgrind (Memcheck, Massif, Callgrind) — high overhead, use in development.
- gprof.
- Intel VTune.

### General / Continuous
- Flame graphs.
- Pyroscope, Grafana Cloud Profiler, Google Cloud Profiler, Amazon CodeGuru.
- eBPF-based tools for production Linux.

## Best Practices

- Profile optimized builds (`-O2` / `-O3`), not debug builds.
- Prefer sampling profilers in production (low overhead).
- Use instrumentation profilers in development when you need precise call counts.
- Compare profiles before and after (differential flame graphs).
- Top-down analysis: system metrics → process → functions → lines.
- Remember the 80/20 or 90/10 rule: most time is spent in a small part of the code.
- Algorithmic improvements usually beat micro-optimizations.
- Help the compiler: clear code, fewer unnecessary abstractions in hot paths, appropriate data layouts.

## Common Wins

- Right data structure (hash set vs linear search, etc.).
- Avoid repeated work (cache, hoist invariants).
- Reduce allocations in hot loops.
- Batch I/O or database calls.
- Parallelism only after confirming the workload is CPU-bound and safe to parallelize.

Optimization is a cost/benefit decision. Clarity usually wins unless measurement proves otherwise.
