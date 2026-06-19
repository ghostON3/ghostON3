<!--
  This is the repo `ghostON3/ghostON3` — GitHub renders this README on the
  profile page. Create the repo with the exact name `ghostON3`, push this file.
-->

# Michal — `ghostON3`

I build systems end to end and I don't stop at the part most people call "done."
Event-sourced backends, a Rust voice + window-manager substrate, a browser
extension, a desktop app, a mobile app and a TV app — frequently the *same*
product across all of them, from one codebase. Polyglot by necessity, not for
the résumé line.

I run an autonomous "dark factory" of AI agents against my own monorepo: a
queue, leases, heartbeats, hash-chained event logs, and lint rules that fail the
build instead of nagging in review. Thousands of PRs have shipped through it.
The interesting engineering isn't any one feature — it's the machine that keeps
a fleet of agents honest without a human as the router.

```
Daily driver:  Arch Linux · Hyprland (Wayland) · tmux · neovim-adjacent · kitty
Languages:     TypeScript · Rust · Python · SQL · Bash
Surfaces:      web · desktop (Tauri/Electron) · mobile (React Native/Expo)
               TV (React Native tvOS) · browser extension (MV3) · CLI daemons
Backbone:      event sourcing · hash-chain integrity · CQRS-ish reducers
               Postgres/Drizzle · BullMQ/Redis · NestJS/Fastify · k3s/Helm/GitOps
Infra:         self-hosted first — k3s homelab, sealed-secrets, Grafana +
               VictoriaMetrics, Pino + prom-client, OpenTelemetry
```

## What I actually do, with proof

- **Architecture that's enforced, not documented.** I encode decisions as
  static-analysis rules so they can't rot: no wall-clock reads in domain logic,
  no `process.env` reaching into a method, never lose the original error in a
  re-throw. → [`eslint-plugin-ghost`](https://github.com/ghostON3/eslint-plugin-ghost)
  (11 rules, 94 tests).
- **Event sourcing done properly.** Append-only log, deterministic replay,
  tamper detection via a per-record hash chain — a "truthkeeper" canary runs in
  CI from line zero. → `elo-evolution-showcase`.
- **Systems software in Rust.** A long-running per-app focus tracker that reads
  Hyprland IPC and writes SQLite; a local voice substrate (STT/TTS over a UNIX
  socket). Low-overhead daemons where a GC'd runtime would be the wrong tool.
  → `elo-time-tracker`, `voice-hub`.
- **One product, every surface.** A single TypeScript monorepo with thin
  platform shells — `apps/{web,desktop,mobile,extension,vscode-extension}` plus
  Rust `hyprland-bridge` and a scraper pool — sharing one core package so
  schema drift between front and back is structurally impossible.
- **My workstation is code.** Months-tuned Arch + Hyprland: monitor-aware
  workspaces, a scratchpad that remembers where windows came from, audible
  feedback on every commit. → [`ghost-dotfiles`](https://github.com/ghostON3/ghost-dotfiles).

## How I work

- **Done = proven + consumed, not merely produced.** A feature is done when a
  user can exercise it end to end and it's live — not when `tsc` is green.
- **Local-first / sovereign.** The device is the source of truth. Self-host
  before reaching for someone else's cloud.
- **Composition over invention.** HTTP, JSON, SQLite, SSE already work — I don't
  invent a protocol to feel clever.
- **Honesty over theatre.** If a test fails, I say so with the output. If a
  thing isn't wired through, it isn't shipped.

## Reach me

Open to senior / staff roles where the bar is real systems work across the
stack. The fastest way to read me is the code, not this page — start with
[`eslint-plugin-ghost`](https://github.com/ghostON3/eslint-plugin-ghost) and
[`ghost-dotfiles`](https://github.com/ghostON3/ghost-dotfiles).
