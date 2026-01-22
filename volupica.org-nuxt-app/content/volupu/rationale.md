# Volupu rationale










## Why NativeTrace must remain OS-Specific

In the context of the Volupu architecture we just designed, Swift traces inside `NativeTrace` are **OS-specific (Raw)**, not normalized.

Here is why this distinction is crucial for your design:

### 1. The Two-Layer Architecture

Volupu effectively creates a "Normalized Layer" and a "Raw Layer."

* **Layer 1: Normalized (Volupu `Trace`)**
This is the clean, normalized view. The Volupu transpiler (written in Rust) guarantees that every `Trace` record has a standard `file`, `line`, and `functionName`. This is the "Universal" trace.
* **Layer 2: OS-Specific (Volupu `NativeTrace`)**
This is the raw, chaotic reality of the underlying platform. For `case apple(trace)`, this string contains the exact output from Swift's `Thread.callStackSymbols`.

### Why `NativeTrace` must remain OS-Specific

1. **Performance:** "Normalizing" a raw Swift stack trace at runtime requires heavy string parsing (regex) to strip out hex addresses and demangle symbols. Doing this on a mobile device during a crash risks an Out-Of-Memory (OOM) error, violating Volupu's design principle.
2. **Fidelity:** A raw Swift trace contains platform-specific clues that normalization might destroy.
* *Example:* Identifying if a crash happened in `UIKit` (iOS) vs `AppKit` (macOS).
* *Example:* Seeing `libsystem_kernel.dylib` hints at a low-level OS resource exhaustion.


3. **AI Capability:** Since Volupu is designed for General AI, we don't need to simplify this text. The AI can read a raw Mach-O stack trace just as easily as a normalized one.

### What the AI sees (The Raw Reality)

When you access `case apple(trace)`, the string will look like this (OS-specific):

```text
0   VolupuApp          0x00000001000040d0 $s9VolupuApp14ProcessData... + 40
1   SwiftUI            0x0000000189f30204 $s7SwiftUI6ButtonV4body... + 20
2   libdyld.dylib      0x0000000180230214 start + 4

```

The AI uses this raw data to debug the *implementation*, while it uses the normalized `Trace` record to debug your *logic*.

---






