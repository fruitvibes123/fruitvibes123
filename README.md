# Fruit Basket — an immutable appliance OS, built end to end by an LLM

A single-purpose, integrity-enforcing Linux appliance OS for one self-hosted web application,
with its build factory and reusable security crates.

> [!WARNING]
> Every line of code and documentation in these repositories is LLM output, written end to end
> by Claude (Anthropic) under the direction and review of a human operator. Read and reuse it
> with that provenance in mind.

**Start with the [engineering whitepaper](https://fruitvibes123.github.io/fruit-basket/)** —
threat model, boot chain, integrity architecture, init and supervision, the reproducible build
pipeline, and the accepted limitations. The companion loader has its own paper:
[Rambutan — the UEFI Secure Boot loader](https://fruitvibes123.github.io/fruit-basket/rambutan-whitepaper.html).

| Repository | What it is |
|---|---|
| [fruit-basket](https://github.com/fruitvibes123/fruit-basket) | the OS: dm-verity + IMA/EVM sealed rootfs, Rust PID-1, A/B updates, no shell, no package manager |
| [orchard](https://github.com/fruitvibes123/orchard) | the build/deploy factory: pinned-input image bakes, QEMU boot gates, install/update/backup ceremonies — its [guide](https://github.com/fruitvibes123/orchard/blob/main/orchard_guide.md) is the end-to-end walkthrough |
| [seed-vault](https://github.com/fruitvibes123/seed-vault) | the reusable security crates: six MIT/Apache verification cores + the GPL signer family |

Six of the seed-vault crates are on crates.io:
[dragonfruit](https://crates.io/crates/dragonfruit) (the no_std ed25519 delegation/verify core),
[pomelo-guard](https://crates.io/crates/pomelo-guard) (compile-time IDOR-safe resource loading),
[coconut-fs](https://crates.io/crates/coconut-fs),
[pomegranate](https://crates.io/crates/pomegranate),
[durian-throttle](https://crates.io/crates/durian-throttle), and
[grape-hostkey](https://crates.io/crates/grape-hostkey).

The repositories are published exports of private canonical repositories, produced by an
equivalence-gated release tool; each release commit carries its gate-witness list. The payload
application and the signing pipeline remain private — the box hosts any application that speaks
its service-manifest schema.
