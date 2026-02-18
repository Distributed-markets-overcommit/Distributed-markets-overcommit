# CGK — Provably Non-Overcommitting Distributed Capacity Layer

**A distributed primitive that enforces hard capacity bounds — even under network partitions and adversarial behavior — by mathematical construction.**

Live interactive demo: https://[your-username].github.io/cgk (replace with your actual GitHub Pages URL once deployed)

## What is CGK?

CGK is a **provably safe** distributed capacity allocation layer. It prevents overcommitment in any system where total capacity must be strictly conserved — even when nodes are partitioned, lie, or act adversarially.

Core guarantees (by construction, not policy):
- **Conservation invariant**: Σ allocations ≤ CAP at all times, across all network conditions
- **Partition tolerance**: Isolated shards cannot inflate beyond safe local bounds
- **Non-additive reconciliation**: Uses lattice join (⊔) semantics — never blind additive merge
- **Contractive dynamics**: Banach fixed-point convergence ensures fast stabilization
- **Hard rejection at injection**: No tokens are consumed if the injection would violate the global cap

Real-world failures this prevents:
- FTX-style balance sheet illusions from additive reconciliation
- Celsius-style double-counting of future capacity
- AWS-style cascading overcommit during reconnect storms

CGK is designed as a substrate for:
- Cloud compute clearing & quota systems
- AI inference marketplaces (e.g. GPU/TPU slot allocation)
- Decentralized energy/microgrid balancing
- Any distributed market with hard resource bounds

## Interactive Demo

Open the demo in your browser to see the invariants hold live:

1. Normal operation → energy contracts to equilibrium
2. Max injection → hard cap enforced, rejections logged
3. Partition + adversarial attack on isolated shard
4. Reconnect → merge fires, total stays ≤ CAP, no double-spend

Watch the "reconnect moment" — this is where most distributed quota systems fail. CGK survives it structurally.

(Embed screenshot or GIF here if you want — e.g. the final convergence screen)

## Key Mathematical Ideas

- **Contractive map** with c < 1 → unique stable equilibrium (Banach)
- **Tarski lattice** with join-semilattice merge (not sum)
- **CRDT-style** height-monotonic updates + safe local caps during partitions
- **Token-gated injection** prevents unbounded adversarial pressure

Full proofs and formal model coming in a short paper / technical report.

## Quick Start (Demo Only)

Just open `index.html` in a modern browser — no build step needed.

For development:
```bash
# Optional: serve locally with live reload
npx serve .
# or python -m http.server
