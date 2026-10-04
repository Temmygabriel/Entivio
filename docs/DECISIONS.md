# Architecture Decisions

Decisions that shape Entivio, and why. When a decision changes, it gets recorded
here rather than silently edited — see the change-control rule in
`ENTIVIO_BUILD_SPEC.md` §126.

---

## ADR-001 — No AI in the core settlement mechanism

**Date:** 2026-10-04
**Status:** Accepted

**Context**
The core problem is deterministic: split an amount, collect confirmations, settle
when conditions are met. There is no judgement call to make.

**Decision**
AI is not part of the core. No LLM, no ML model, no AI assistant.

**Reason**
AI would not materially improve allocation, authorization, confirmation, or
settlement — it would only add a dependency, cost, and a new failure mode. Adding
it to justify the label "AI-powered" would be dishonest.

**Consequences**
The settlement path stays deterministic and auditable, which is what a financial
workflow needs.

---

## ADR-002 — An approved claim is an input

**Date:** 2026-10-04
**Status:** Accepted

**Context**
Entivio could try to verify that an accident happened. That would require a
trustworthy physical-world oracle.

**Decision**
Claim approval is an input. Entivio begins after approval.

**Reason**
A real oracle is outside the MVP and would introduce another dependency plus a
false impression of verification. Scope is better spent on the settlement
workflow itself.

**Consequences**
Entivio must never be described as validating claims. See LIMITATION 3.

---

## ADR-003 — The ledger is the source of truth

**Date:** 2026-10-04
**Status:** Accepted

**Context**
Claim state could be cached or mirrored off-ledger for convenience.

**Decision**
Canton ledger state is authoritative. The verifier reads deployed state, not a
cache.

**Reason**
If the UI and the ledger can disagree, the privacy and gating guarantees are
meaningless. The whole product claim rests on ledger-enforced state.

**Consequences**
Reads must handle ledger latency. Receipt of a transaction does not mean state is
immediately readable — the verifier waits, queries, then asserts.

---

## ADR-004 — No database in the MVP

**Date:** 2026-10-04
**Status:** Accepted

**Context**
A database is the default reflex for a web app.

**Decision**
No PostgreSQL, MongoDB, Firebase, Supabase, Redis, or equivalent.

**Reason**
It would create a second source of truth and a synchronisation problem, for no
verified benefit. Zero-budget and Vercel-friendliness also favour fewer moving
parts.

**Consequences**
Any future database must document reason, free status, Vercel compatibility, CI
compatibility, data model, and source-of-truth rules before being added.

---

## ADR-005 — Grofty is optional

**Date:** 2026-10-04
**Status:** Accepted

**Context**
Grofty offers a Canton wallet, Party ID support, CC/USDCx, and signing.

**Decision**
The core product must not depend on Grofty onboarding.

**Reason**
If Grofty onboarding breaks or is unavailable, the product must still work. A
core dependency on a third-party flow is an unnecessary risk.

**Consequences**
Grofty work begins only after the core Canton flow passes, and only if verified
available. Recovery phrases and private keys never enter the repository under any
circumstance.

---

## ADR-006 — Settlement asset selected only after verified availability

**Date:** 2026-10-04
**Status:** Accepted

**Context**
The obvious move is to hard-code CC or USDCx and build around it.

**Decision**
The asset stays unset until availability is verified in the real environment.

**Reason**
Assuming an asset exists is exactly the kind of guess that produces a demo which
cannot be reproduced. Availability, transferability, and party access must all be
confirmed first.

**Consequences**
No package ID, asset identifier, or balance is hard-coded. If no free asset is
available, the atomicity claim is marked UNPROVEN and the product claim narrowed
rather than faked.

---

## ADR-007 — TypeScript over JavaScript

**Date:** 2026-10-04
**Status:** Accepted

**Context**
The frontend and the Canton integration adapter could be written in either.

**Decision**
TypeScript throughout.

**Reason**
The Canton JSON Ledger API exchanges structured JSON whose shapes matter for
correctness. Types catch contract-mismatch errors at build time, and the CI
typecheck gate depends on it.

**Consequences**
`npm run typecheck` is a required CI step. Slightly heavier build, which is
delegated to GitHub Actions rather than the 8 GB local machine.
