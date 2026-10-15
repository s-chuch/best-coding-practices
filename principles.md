# Detailed Principles

## KISS – Keep It Simple, Stupid

Write the simplest code that solves the problem. Complexity increases cognitive load and maintenance cost. Prefer standard library features and clear logic over clever constructs.

## DRY – Don't Repeat Yourself

Every piece of knowledge should have a single, unambiguous representation. Extract duplicated logic. The "rule of three" is a practical heuristic: after the third repetition, consider abstracting.

## YAGNI – You Aren't Gonna Need It

Do not implement functionality until it is required. Over-engineering for imagined future needs creates dead weight.

## Single Responsibility Principle (SRP)

A function or class should have only one reason to change. If you need the word "and" to describe what it does, it is probably doing too much.

## Open/Closed Principle

Software entities should be open for extension but closed for modification. Prefer composition and interfaces over modifying existing code.

## Guard Clauses and Early Returns

Handle error cases and edge conditions first and return early. This keeps the main "happy path" unindented and easier to follow.

## Meaningful Names

Names should reveal intent. Prefer `userAccountBalance` over `bal`. Avoid abbreviations unless they are universally understood in the domain.

## Avoid Magic Numbers

Use named constants or configuration. `MAX_RETRIES = 3` is clearer than a bare `3`.

## Measure Before Optimizing

Profile first. The 90/10 (or 80/20) rule: most of the runtime is spent in a small portion of the code. Optimize only the critical path after measurement.

## Prefer Readability

Unless a section is proven to be a bottleneck, favor clear code over micro-optimized code. Document any intentional complexity.
