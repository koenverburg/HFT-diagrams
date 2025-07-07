# Project / Codebase Diagram
> **Disclaimer** this document is a living document and is subject to change. Use this as reference for your own project or as inspiration for your own project.
> I use this to help me visualize the project structure and how the different components interact with each other.

## Rules
- Computation of indicators are written in Rust and exposed to Node via the n-api
-

## Decisions
- Main Language: Typescript
- Main Runtime: Bun (NodeJs)
- Second Language: Rust (n-api)

## High Level folder structure
```bash
/
/crates/internals
/crates/rsi
/crates/ma
/crates/ema
/crates/bollinger-bands
/crates/average-directional-index # ADX
/crates/macd

/packages/trader # trader
/packages/signals # signals bots
/packages/internals
/packages/types
/packages/abstracts
```

### Build/deploy sequence
- build the rust bindings
- bundler the Typescript
- Create either bytecode from the typescript bundle or bundle bun + the typescript inside a single binary.
- Create docker image
- deploy to k3s cluster
- monitor
- profit

### Mindset
The application runs on the given context via the environment variables, which dictate on which exchange the trader/signal bot is running on, but also which pair is should trade/send signals from, trade volume, settings for the indicators, and other settings.
