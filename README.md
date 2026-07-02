# NucleScript Playground

The [Nuclescript organization](https://github.com/Nuclescript)'s interactive
playground for **NucleScript**, the declarative DNA storage operations
language. This repo is a self-contained mirror of the
[VyomKulshrestha/Nucle-OS](https://github.com/VyomKulshrestha/Nucle-OS)
workspace — the engine's source of truth — plus the playground crates, so
it builds and runs standalone from here.

## 🧪 Try it live

**[nuclescript.github.io/playground](https://nuclescript.github.io/playground/)**
— no install, no download. `nucle_wasm` compiles the compiler/codec/ECC
engine to WebAssembly and runs it entirely in your browser tab. A GitHub
Actions workflow (`.github/workflows/pages.yml`) rebuilds and redeploys it
on every push to `main`, so it's always current.

The playground has three tabs, each backed by the real engine (no
reimplemented math, no mocked data):

- **Write & Run** — paste a `.nsl` program and get compiler diagnostics,
  simulation steps, and optimizer notes.
- **Benchmark Explorer** — pick a codec/profile, drag the redundancy
  slider, and density/GC%/cost/recovery-probability update live, computed
  by the real codec benchmark plus a Reed-Solomon-aware Monte-Carlo
  recovery estimate.
- **Pipeline Visualizer** — encodes real input through the actual
  codec/ECC/noise engine and animates each strand through
  encode → synthesize/sequence (noise) → recover, including honest
  failures when redundancy/profile can't reconstruct the data.

## Run it locally

Prefer a native binary over the browser build? `nucle_playground` is the
same three tabs as a self-contained `tiny_http` server:

```bash
cargo run -p nucle_playground
# then open http://127.0.0.1:8080
```

No `cargo` or cloning needed at all? Grab a prebuilt binary from the
[**Releases**](https://github.com/Nuclescript/playground/releases) page —
Linux, Windows, and macOS builds with the frontend embedded, so running the
single downloaded file is enough.

## Packages

Official NucleScript packages (`@nuclescript/presets`, `@nuclescript/profiles`,
`@nuclescript/benchmarks`, `@nuclescript/recovery`) are published separately
to [this org's package registry](https://github.com/orgs/Nuclescript/packages).

## Everything else

This repo exists to run the playground standalone. For the full engine —
architecture, the NucleScript language reference, CLI usage, and test
coverage — see [VyomKulshrestha/Nucle-OS](https://github.com/VyomKulshrestha/Nucle-OS).

---

MIT — see [LICENSE](LICENSE) for details.
