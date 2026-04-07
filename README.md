# forgetting-problem 🧠

Your agents slow down, drift, or break as their context fills with outdated information. This repository provides three specific, reliable mechanisms to prune agent memory deliberately. You can see them running live in the Cocapn Fleet.

---

## Why This Exists
Most tooling is about remembering. This is about forgetting well. You don't always need smarter memory; you need an agent that can deliberately let go of state.

---

## Quick Start
Fork this repository first. It runs on your own Cloudflare Workers instance with zero dependencies and requires no accounts or signups.

```bash
git clone https://github.com/cocapn/forgetting-problem
cd forgetting-problem
npx wrangler deploy
```

All core logic is in `/src/mechanisms`. Implement the interface for your memory store and tune the rules for your use case.

---

## How It Works
Each mechanism addresses a specific failure mode:
- **Thermal Decay**: Unaccessed memories lose a small, configurable amount of weight on each agent tick. This provides gradual, natural forgetting without hard cuts.
- **Scheduled Pruning**: Periodic cleanup that drops state older than a defined horizon you set.
- **Emergency Purge**: A circuit breaker that clears problematic context from a single agent or an entire fleet in under 50ms.

---

## What Makes This Different
1.  It executes the rules you define; it does not judge what is "important."
2.  It requires no background workers, queues, or extra infrastructure. All forgetting operations run inline with agent activity.
3.  Every deletion is logged. You can replay what was forgotten, when, and why.

---

## Limitations
This is not a set-and-forget solution. It requires manual tuning of thresholds for your specific workload. The thermal decay mechanism, for example, adds 1-2ms of overhead per agent tick, which may be unsuitable for extremely latency-sensitive applications without adjustment.

---

## What This Is Not
- An automated janitor for vector databases.
- A general-purpose memory management library. It is built for fleets of agents.
- A replacement for your application's core logic.

---

License: MIT

Attribution: Superinstance and Lucineer (DiGennaro et al.)

<div style="text-align:center;padding:16px;color:#64748b;font-size:.8rem"><a href="https://the-fleet.casey-digennaro.workers.dev" style="color:#64748b">The Fleet</a> &middot; <a href="https://cocapn.ai" style="color:#64748b">Cocapn</a></div>