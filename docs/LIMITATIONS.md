# Limitations

Known limitations, stated plainly. This file is not a list of things we hope
nobody notices — it is the list we would want a judge to read.

**Last updated:** 2026-10-04

---

## LIMITATION 1 — DevNet access not yet obtained

**WHY**
DevNet requires an allowlisted egress IP and credentials issued by a Super
Validator sponsor. Access is provisioned through the HackCanton/NODERS
onboarding path, not self-serve.

**IMPACT**
No real-network deployment, no real parties, no real settlement can be shown
until this is resolved. Gates 5 and above are blocked.

**CURRENT STATUS**
Requested / in progress. Blocks deployment only — **not** contract development,
local flow, privacy proof, or adversarial testing.

**SAFE DESCRIPTION**
"Entivio's contract and settlement logic run and are tested locally. DevNet
deployment is pending environment access."

**FUTURE PATH**
Obtain DevNet credentials via HackCanton onboarding, then run the DevNet
canonical run and record real transaction evidence.

---

## LIMITATION 2 — Settlement asset is unverified

**WHY**
The MVP requires one settlement asset that is free, actually available, and
transferable by the required parties. CC and USDCx are **candidates**, not
confirmed.

**IMPACT**
If no verified free asset can be transferred between the required parties,
atomic value settlement cannot be demonstrated.

**CURRENT STATUS**
Unverified. No asset has been assumed or hard-coded.

**SAFE DESCRIPTION**
"Settlement is demonstrated against the asset made available by the environment.
The asset is not assumed."

**FUTURE PATH**
Verify actual asset availability with the provisioned parties. If none is
available, the capability is marked UNPROVEN and the product claim narrowed —
never faked.

---

## LIMITATION 3 — Claim approval is an input, not verified

**WHY**
Verifying real-world accidents would require a trusted external oracle, which is
outside the MVP and would add another dependency.

**IMPACT**
Entivio does not establish that a claim is legitimate. It coordinates settlement
of a claim that has already been approved elsewhere.

**CURRENT STATUS**
Permanent by design. See ADR-002.

**SAFE DESCRIPTION**
"Entivio settles an already-approved claim. It does not adjudicate claims."

**FUTURE PATH**
None planned. This is a scope boundary, not a defect.

---

## LIMITATION 4 — No database in the MVP

**WHY**
Canton is the source of truth for claim state. A second store would create two
sources of truth and a synchronisation problem.

**IMPACT**
All claim and entitlement state must be read from the ledger. No off-ledger
querying, search, or analytics.

**CURRENT STATUS**
By design. See ADR-004.

**SAFE DESCRIPTION**
"Claim state is read from the Canton ledger. There is no separate database."

**FUTURE PATH**
If a verified requirement appears, any added database must document its reason,
free status, Vercel compatibility, data model, and source-of-truth rules.

---

## LIMITATION 5 — No KYC, compliance, or fraud detection

**WHY**
These are regulated activities outside the MVP and outside the builder's ability
to implement truthfully.

**IMPACT**
Entivio must not be represented as a compliant or fraud-resistant financial
product. It is a settlement workflow.

**CURRENT STATUS**
Out of scope. Never claimed.

**SAFE DESCRIPTION**
"Entivio is a settlement coordination workflow. It does not perform KYC,
compliance checks, or fraud detection."

**FUTURE PATH**
None in this MVP.

---

## LIMITATION 6 — Nothing is proven yet

**WHY**
The project is at environment-setup stage. No contracts, no runs, no evidence.

**IMPACT**
Every capability in `docs/CLAIMS_STATUS.md` is `UNPROVEN`, `UNAVAILABLE`, or
`OUT OF SCOPE`.

**CURRENT STATUS**
Temporary, and the reason this file exists.

**SAFE DESCRIPTION**
"This repository describes intended behaviour. Verified results will be recorded
in `evidence/` as they are produced."

**FUTURE PATH**
Build the protocol, run the local canonical run, record real evidence, then
update `docs/CLAIMS_STATUS.md` per capability.
