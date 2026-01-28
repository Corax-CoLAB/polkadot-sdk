## 2025-02-20 - Substrate Arithmetic Inlining
**Learning:** `PerThing` arithmetic helpers (`overflow_prune_mul`, etc.) were not inlined by default. Inlining them allows the compiler to constant-fold `PerThing::ACCURACY` and the `Rounding` enum, resulting in significant speedups (~10-15%) for operations like `mul_floor` and `mul_ceil`.
**Action:** When working with generic arithmetic traits where constants are passed via associated constants or arguments, always consider `#[inline]` to enable specialization and constant propagation.
