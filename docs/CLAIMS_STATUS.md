# Claim Status

Every major technical statement about Entivio, with its honest proof status.

**Allowed statuses:** `PROVEN` · `PARTIALLY PROVEN` · `UNPROVEN` · `UNAVAILABLE` · `OUT OF SCOPE`

**Last full review:** 2026-10-04

> Nothing in Entivio is currently proven. This file exists so that the gap between
> what we intend to build and what actually works stays visible. A status only
> moves to `PROVEN` when real evidence exists in `evidence/`.

| Claim | Status | Evidence | Last checked | Notes |
|---|---|---|---|---|
| Canton privacy used by Entivio | `UNPROVEN` | none | 2026-10-04 | Contracts do not exist yet |
| Recipient sees only own entitlement | `UNPROVEN` | none | 2026-10-04 | Requires real multi-party privacy test |
| Allocation total equals approved amount | `UNPROVEN` | none | 2026-10-04 | Invariant must be enforced in contract |
| Settlement gated on all confirmations | `UNPROVEN` | none | 2026-10-04 | No contract yet |
| Atomic coordinated settlement | `UNPROVEN` | none | 2026-10-04 | Must be verified against the real asset implementation |
| Local canonical run | `UNPROVEN` | none | 2026-10-04 | Not attempted |
| DevNet deployment | `UNAVAILABLE` | none | 2026-10-04 | No DevNet access yet — awaiting HackCanton/NODERS |
| Settlement asset availability (CC) | `UNAVAILABLE` | none | 2026-10-04 | Candidate only. Not assumed available |
| Settlement asset availability (USDCx) | `UNAVAILABLE` | none | 2026-10-04 | Candidate only. Not assumed available |
| Vercel deployment | `UNPROVEN` | none | 2026-10-04 | No app yet |
| Verifier reports real ledger state | `UNPROVEN` | none | 2026-10-04 | Not built |
| Grofty wallet integration | `OUT OF SCOPE` | n/a | 2026-10-04 | Optional; core must not depend on it |
| BitSafe integration | `OUT OF SCOPE` | n/a | 2026-10-04 | Optional; only if it materially helps |
| Hacken audit result | `OUT OF SCOPE` | n/a | 2026-10-04 | Optional; evidence only, never proof of security |
| AI in core settlement | `OUT OF SCOPE` | n/a | 2026-10-04 | Deliberate decision — see ADR-001 |
| Real accident verification | `OUT OF SCOPE` | n/a | 2026-10-04 | Claim approval is an input — see ADR-002 |
| MainNet settlement | `OUT OF SCOPE` | n/a | 2026-10-04 | Not an MVP goal |
| KYC / regulatory compliance | `OUT OF SCOPE` | n/a | 2026-10-04 | Not claimed anywhere |
