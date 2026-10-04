# Entivio

**One approved claim. Every recipient gets their share. Privately.**

Entivio privately coordinates multi-party claim payouts and settles them together
only when every required party has confirmed.

Built for **HackCanton Season 3** — RWA & Business Workflows track.

---

## Status: early build — nothing is proven yet

This repository is at the environment-setup stage. There is **no working flow**.
No contract, no settlement, no deployment, no evidence.

| Area | Status |
|---|---|
| Daml protocol (Claim / Entitlement) | Not started |
| Local canonical run | Not started |
| Privacy proof | Not started |
| Adversarial tests | Not started |
| DevNet access | **Blocked** — awaiting HackCanton/NODERS provisioning |
| Settlement asset | **Unverified** — not assumed available |
| Web application | Not started |
| Evidence layer | Not started |

Per-claim proof status is tracked honestly in [`docs/CLAIMS_STATUS.md`](docs/CLAIMS_STATUS.md).
Known gaps are listed in [`docs/LIMITATIONS.md`](docs/LIMITATIONS.md).

**Do not cite this repository as evidence of a working product. It is not one yet.**

---

## 30-second explanation

When an insurance claim is approved and needs to pay several parties at once,
each party should see their own share and nothing else — but the payout should
only happen when everyone is ready.

Entivio does exactly that. Each recipient confirms **only their own** entitlement.
The settlement gate stays blocked until every confirmation is in. Then the
allocation settles as one coordinated operation.

## What Entivio is not

Entivio starts **after** a claim is approved. It is a settlement workflow, not an
insurance product.

It does not decide whether an accident happened. It does not inspect anything. It
does not underwrite. It does not detect fraud. It does not replace an insurer. It
does not claim regulatory compliance. Claim approval is an **input**.

## Why Canton matters

Entivio needs several parties to coordinate around one financial workflow while
each seeing **different** information. Hiding amounts in the browser would not be
enough — a recipient could still query the ledger directly.

Canton enforces that boundary at the ledger level: participant-scoped privacy and
explicit authorization. That is why the project is on Canton rather than a
frontend pointed at a blockchain.

## The demo claim

Deterministic demonstration data — **not** a real insurance claim.

| | |
|---|---|
| Claim ID | `ENT-1042` |
| Description | Vehicle repair claim |
| Approved total | 10,000 units |

| Recipient | Entitlement |
|---|---|
| Policyholder | 6,000 |
| Repair Provider | 3,000 |
| Rental Provider | 1,000 |
| **Total** | **10,000** |

The allocation total must always equal the approved amount. The contract rejects
any other sum; frontend validation alone does not count.

## Planned architecture

```
Browser
  → Next.js / TypeScript application
    → Canton integration adapter
      → Canton JSON Ledger API
        → Daml contracts
```

The exact integration method will be validated against the real HackCanton
environment before it is claimed to work. Canton is the source of truth for claim
state. There is no database in the MVP.

## Repository layout

```
daml/          Daml contracts (Claim, Entitlement)
app/           Next.js application
lib/           Canton integration adapter
tests/         contract, integration, adversarial, privacy, e2e
docs/          architecture, decisions, status, limitations
evidence/      real run output only — never hand-written
```

## Reproduction

Not available yet. This section will contain real commands once the protocol
exists and has been run.

## License

MIT — see [`LICENSE`](LICENSE).
