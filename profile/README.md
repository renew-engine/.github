<div align="center">

<picture>
  <source media="(prefers-color-scheme: dark)" srcset="assets/renew-banner-wide.svg">
  <source media="(prefers-color-scheme: light)" srcset="assets/renew-banner-wide-light.svg">
  <img src="assets/renew-banner-wide.svg" alt="renew — an AI-first game engine in Rust" width="820">
</picture>

<br>
<br>

### A game engine in Rust, built to be *operated*

Deterministic simulation&nbsp; · &nbsp;Vulkan rendering&nbsp; · &nbsp;every capability driven from the command line

<br>

[![CI](https://github.com/renew-engine/renew/actions/workflows/ci.yml/badge.svg)](https://github.com/renew-engine/renew/actions/workflows/ci.yml)
[![Nightly checks](https://github.com/renew-engine/renew/actions/workflows/nightly-checks.yml/badge.svg)](https://github.com/renew-engine/renew/actions/workflows/nightly-checks.yml)

[![License](https://img.shields.io/badge/license-Apache--2.0-blue)](https://github.com/renew-engine/renew/blob/main/LICENSE)
[![Rust](https://img.shields.io/badge/rust-1.97%2B-orange)](https://github.com/renew-engine/renew/blob/main/rust-toolchain.toml)
[![Edition](https://img.shields.io/badge/edition-2024-blueviolet)](https://github.com/renew-engine/renew/blob/main/Cargo.toml)
[![Platforms](https://img.shields.io/badge/platforms-Windows%20%7C%20Linux%20%7C%20macOS-lightgrey)](https://github.com/renew-engine/renew/actions/workflows/ci.yml)
[![Unsafe](https://img.shields.io/badge/unsafe-denied%20by%20default-success)](https://github.com/renew-engine/renew#quality-gates)

**[Start here → github.com/renew-engine/renew](https://github.com/renew-engine/renew)**

</div>

---

Every capability in the engine is a library with a command-line face and machine-readable
output, so a person, a script, or an agent drives it through exactly the same surface. The
simulation core is deterministic by construction: same build, same seed, same inputs, same
result, bit for bit.

> [!NOTE]
> **"AI-first" on the banner is about the surface, not the feature list.** Everything is
> headless, scriptable, and emits schema-versioned JSON beside its human-readable output, so
> nothing about the engine requires a person in front of a screen. It does not mean the
> engine ships AI features.

> [!IMPORTANT]
> **Early development.** Pre-0.1. Every module declares where it sits on the `bootstrap` →
> `internal` → `stable` ladder, and nothing has reached `stable` yet — so nothing here is
> ready to build a game on. What exists is real, tested, and honest about what it is.

## Four commitments

| | What that means in practice |
|---|---|
| **Deterministic** | Fixed timestep over integer nanoseconds, fixed-point arithmetic in the simulation, no wall-clock reads and no unseeded randomness. Replay and lockstep are a foundation, not a retrofit. |
| **Code-first** | One binary builds, tests, benchmarks, packs assets, records and replays runs, and starts samples — each command with a `--json` face. A GUI, when it arrives, will be a client of those same APIs and never a privileged one. |
| **Modular** | A small required core; everything else optional and removable behind an explicit interface. CI proves it one crate at a time — each optional crate excluded along with its dependents, then built **and** tested. |
| **Measured** | Performance claims arrive with numbers and the configuration that produced them. The steady-state frame loop is held to zero heap allocations through the engine's allocators, counted in dev builds. |

## Start here

Stable [Rust](https://rustup.rs) 1.97 or newer, and nothing else.

```sh
git clone https://github.com/renew-engine/renew
cd renew
cargo build --workspace
cargo run --bin hello-engine
```

That last command is the proof of life — a fixed-timestep accumulator driven through 60
frames of deliberately uneven frame times, reading no clocks at all:

```console
$ cargo run --bin hello-engine
hello-engine 0.1.0
fixed timestep: 16666667 ns
frames simulated: 60
time submitted: 1245000015 ns
ticks executed: 74
time pending: 11666657 ns
```

Run it twice. Run it on another machine, or another operating system. Every byte is
identical — and that property is what the rest of the engine is built to preserve.

## What's in the tree

Twenty-one engine crates, five of them core: diagnostics, the event vocabulary, math,
memory, and the platform layer. Around them sit fixed-point arithmetic, the frame loop, an
ECS, a job system, seeded RNG, input, replay and trace digests, 2D and 3D physics, a Vulkan
RHI behind an interface that names no Vulkan type, 2D and 3D renderers, audio, asset packs,
and a dependency-free PNG encoder. Six samples and two tools sit beside them.

```sh
cargo run --bin renew -- modules   # the live list, each crate's maturity read from its manifest
```

Every commit on `main` clears formatting and a strict clippy deny-set, the full test suite in
debug and release on Windows, Linux and macOS, a line-coverage gate that fails in *both*
directions, a module-graph DAG check, the removability configurations above, and
`cargo-deny` over the whole dependency tree — with sanitizers and Miri on a nightly schedule.

## Contributing

Issues are the most useful thing you can send: bug reports, questions about why something is
the way it is, and cases where the documentation and the code disagree — the last of those
especially, since a document that misdescribes the code is treated here as a defect rather
than as tidying owed later.

See [CONTRIBUTING](https://github.com/renew-engine/renew/blob/main/CONTRIBUTING.md) for the
bar a change is held to. The short version: a change arrives with its tests, its
documentation, and evidence that it works.

<div align="center">
<br>

<sub>Licensed under <a href="https://github.com/renew-engine/renew/blob/main/LICENSE">Apache-2.0</a>&nbsp; · &nbsp;Brand assets in <a href="https://github.com/renew-engine/renew/tree/main/assets/brand"><code>assets/brand/</code></a></sub>

</div>
