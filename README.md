# forgetting-problem 🧠

Tools for the problem you eventually face: how do agents safely forget?

This repository provides a set of patterns—Thermal Decay, Scheduled Pruning, and Emergency Purge—for managing memory lifecycle in autonomous agent fleets. It is not a complete solution, but a collection of implementable ideas for your own systems.

---

## The Problem

As agents run, their context accumulates stale, erroneous, or irrelevant state. This slows reasoning, introduces errors, and consumes resources. Managing this decay is a core operational challenge for any multi-agent system.

This is open-source research into structured forgetting: deliberate, safe mechanisms to keep agent context focused and functional.

---

## Quick Start

This is a fork-first repository. Clone or fork it to use as a starting point for your own implementation.

```bash
# Clone the repository
git clone https://github.com/your-org/forgetting-problem
```
The core patterns are in `/src/mechanisms`. You adapt them to your agent runtime and memory store.

You can also run the included simulation to see the interactions between the mechanisms.

---

## Core Mechanisms

These three patterns work together. You implement them; they provide the rules.

| Mechanism | What It Does |
|---|---|
| **Thermal Decay** | Gradually reduces the weight of memories that go unaccessed over time, simulating natural fading. |
| **Scheduled Pruning** | Runs deterministic cleanup cycles to remove state flagged as obsolete or beyond a retention period. |
| **Emergency Purge** | A circuit-breaker protocol. When triggered, it rapidly clears compromised or toxic context from an agent or fleet segment. |

**Key Properties:**
- Built for the Cocapn agent runtime and fleet protocol.
- Zero runtime dependencies. It's logic, not infrastructure.
- BYOK (Bring Your Own Knowledge): You provide the memory store; this provides the rules for letting go.

---

## What This Is Not

- This is not a vector database janitorial script.
- This is not an automated, set-and-forget solution. **These patterns require manual tuning and oversight for your specific use case.** Their effectiveness depends on your implementation.
- This is not a proprietary black box. Every operation is designed to be transparent and auditable.

## Try It Live

Observe these patterns in a live fleet context:
👉 [https://the-fleet.casey-digennaro.workers.dev](https://the-fleet.casey-digennaro.workers.dev)

---

## Contributing

This is an open, unsolved problem. Discussions, pull requests, and issues are welcome—especially around edge cases, failure modes, and ethical considerations.

## License

MIT © Superinstance & Lucineer (DiGennaro et al.)

---

<div align="center">
  <a href="https://the-fleet.casey-digennaro.workers.dev">The Fleet</a> • <a href="https://cocapn.ai">Cocapn</a>
</div>