# ENTIVIO BUILD SPECIFICATION

Version: 1.0
Date: 4 October 2026
Project: Entivio
Hackathon: HackCanton Season 3
Primary track: RWA & Business Workflows
Deployment target: Vercel
Repository target: GitHub
Build constraint: Zero budget
Coding workflow: Claude Code CLI + DeepSeek coding assistant
Local machine constraint: Windows PC with 8 GB RAM
Cloud build preference: GitHub Actions / GitHub cloud resources for heavy work

---

# 0. READ THIS FIRST

This document is the project contract.

Do not treat it as a suggestion list.

The product is:

Entivio is a private multi-party claim settlement application.

Core flow:

Approved claim
→ allocation
→ recipient confirmation
→ settlement gate
→ settlement
→ proof

The product must be real.

Do not create fake transaction success screens.
Do not create fake Canton activity.
Do not invent APIs.
Do not invent contract addresses.
Do not invent token balances.
Do not invent sponsor capabilities.
Do not invent DevNet access.
Do not invent wallet behavior.
Do not invent deployment details.

When something is unknown, stop at the exact boundary where the unknown matters and report the blocker.

Do not quietly choose an assumption and continue.

This project is being built by a solo builder with a zero-dollar budget and a Windows PC with 8 GB RAM.

The local PC should not be used for heavy builds when cloud execution is practical.

The web application will be deployed through Vercel.

The public GitHub repository must contain only files that are appropriate for a public hackathon repository.

Secrets, private credentials, personal data, machine-specific files, local environment files, recovery phrases, tokens, and temporary private notes must remain local and must never be pushed.

The coding assistant must communicate with the builder using simple language that a 15-year-old can understand.

The implementation itself may be technically advanced.

The communication must stay simple.

---

# 1. PROJECT OUTCOME

## 1.1 Product

Name:

Entivio

Product category:

Private multi-party settlement

First use case:

Approved insurance claim payout

Core promise:

When one approved claim needs to pay several parties, Entivio lets each participant see and confirm their own entitlement while keeping unrelated payout information private, then settles the approved distribution only when the required conditions are satisfied.

## 1.2 What Entivio does

Entivio starts after a claim has already been approved.

It does not decide whether an accident happened.

It does not perform physical inspection.

It does not perform insurance underwriting.

It does not claim to replace an insurer.

It does not claim to perform fraud detection.

It does not claim to provide regulatory compliance.

The MVP is a settlement workflow.

## 1.3 Concrete demo

Use one deterministic demo claim.

Claim ID:

ENT-1042

Example:

Vehicle repair claim

Approved total:

10,000 units of the verified Canton settlement asset used for the canonical run.

Recipients:

Policyholder
6,000

Repair Provider
3,000

Rental Provider
1,000

Total:
10,000

This is demonstration data. Do not present it as a real insurance claim.

---

# 2. SOURCE OF TRUTH

Use this hierarchy.

1. Actual deployed Canton ledger state and verified transaction evidence
2. Current official Canton / Digital Asset documentation
3. Current official HackCanton / AppsFactory documentation
4. Approved Entivio product specification
5. Accepted architecture decisions in this repository
6. Source code and tests
7. README and marketing material

When two sources conflict:

Stop.

Write down the conflict.

Identify which source has higher priority.

Resolve it explicitly.

Do not silently pick the easier answer.

This rule applies especially to:

Canton version
DPM commands
DevNet access
Party provisioning
Ledger API endpoints
wallet behavior
asset availability
HackCanton submission rules
sponsor challenge rules
Vercel runtime limits

---

# 3. CURRENT HACKCANTON CONTEXT

Current event facts available while writing this specification:

HackCanton Season 3 is an online build program operated through AppsFactory by NODERS.

Current public reporting:

Submission deadline:
9 October 2026 at 23:59 UTC

Judging:
10 October through 18 October 2026

Finalists:
19 October 2026

Grand Final:
21 October 2026 at 14:00 UTC

Current public update on 2 October 2026:

85 teams
44 projects
6 completed submissions

Tracks:

1. RWA & Business Workflows
2. Financial Applications
3. Investment Infrastructure
4. Data, Analytics & Ecosystem Dashboards
5. Open Track

Projects can select up to two tracks.

The event provides guided Canton onboarding, technical resources, mentoring and DevNet support.

Verify all submission requirements again before final submission.

Useful references:

HackCanton current reporting:
https://cantonnews.org/hackcanton-season-3-reaches-85-teams-as-submissions-begin

Canton event calendar:
https://cantonnews.org/events

AppsFactory:
https://appsfactory.cc/hackathons

HackCanton S3:
https://hackathon.appsfactory.cc/season-3

NODERS infrastructure workshop:
https://natokhd.com/video/how-to-spin-up-your-project-on-canton-noders/5K1oe9i1MEQ

The official event source has higher priority than secondary reporting.

---

# 4. CURRENT CANTON TECHNICAL CONTEXT

Current reference material confirms:

DPM is part of the current Canton/Daml development workflow.

The JSON Ledger API provides HTTP/JSON access to a Canton ledger.

Current reference material:

JSON Ledger API:
https://archived.docs.digitalasset.com/build/3.5/reference/json-api/openapi.html

JSON Ledger API tutorial:
https://archived.docs.digitalasset.com/build/3.5/tutorials/json-api/canton_and_the_json_ledger_api.html

Daml package management:
https://archived.docs.digitalasset.com/build/3.5/sdlc-howtos/applications/develop/manage-daml-packages.html

Canton Developer Hub:
https://github.com/canton-network-devs/Canton-Developer-Hub

Important:

These references are not permission to guess commands.

Check the current installed version and current official documentation before implementation.

Record actual versions.

---

# 5. GROFTY CONTEXT

Grofty is optional for the core product.

Current Grofty documentation indicates:

Canton Party ID support
Canton wallet
CC support
USDCx support
transaction signing
controlled onboarding

Reference:
https://grofty.cc/docs/quick-start

Do not make core Entivio depend on Grofty onboarding.

If Grofty is added, verify the current onboarding and signing flow first.

Never store recovery phrases or private keys in the repository.

---

# 6. ZERO-BUDGET RULE

Budget is zero dollars.

This is hard.

Do not require payment for:

RPC
hosting
database
LLM API
security audit
wallet
test assets
cloud compute
analytics
email
domain

unless the hackathon supplies the service free of charge.

If a required dependency costs money:

Status is BLOCKED.

Do not invent a paid workaround.

Look for a verified free path supplied by HackCanton.

If none exists, narrow the scope or remove the dependency.

---

# 7. LOCAL MACHINE RULE

The builder has a Windows PC with 8 GB RAM.

Use local resources for:

Claude Code CLI
light editing
small commands
git
light debugging

Prefer GitHub cloud for:

large npm installs
production builds
large TypeScript builds
full test suites
Playwright runs when practical
repeatable CI
heavy lint/build workflows

Do not require the builder to upgrade hardware.

Do not install heavy dependencies without a reason.

Before adding a large dependency, explain:

what it does
why it is needed
why a smaller option is not enough
whether it works in GitHub Actions
whether it works in Vercel

---

# 8. PUBLIC REPOSITORY SAFETY

Public repository may contain:

application source
Daml source
tests
safe configuration
package manifests
README
architecture
public screenshots
safe evidence
public transaction references when safe
CI configuration

Local-only:

.env.local
private credentials
API keys
JWT secrets
wallet files
recovery phrases
private keys
browser profile data
personal notes
temporary private exports
machine-specific settings
private HackCanton credentials

Never commit private credentials.

---

# 9. GIT SAFETY

Before every push:

Run git status.

Inspect changed files.

Inspect staged files.

Search changed text for likely secrets.

Confirm no .env.local.

Confirm no wallet secrets.

Confirm no private keys.

Confirm no personal machine paths.

Then push.

If a secret is ever committed:

Stop.

Do not merely delete it in a later commit.

Rotate the secret if applicable.

Clean history if necessary.

Report the incident clearly.

---

# 10. COMMUNICATION RULE

Communicate with the builder like they are 15 years old.

Use simple labels:

PHASE COMPLETE

What was done

Tests

Evidence

Problem

Next step

Avoid jargon unless necessary.

Explain jargon when needed.

Do not flood the builder with decorative symbols.

Do not use fake enthusiasm.

Do not hide warnings.

Example:

PHASE BLOCKED

Problem

The app cannot reach the Canton ledger.

Why this matters

We cannot prove the real settlement until the ledger is reachable.

What you need to do

Get the DevNet access details from the HackCanton onboarding flow.

What happens next

After the connection works, continue deployment testing.

---

# 11. NO-GUESSING RULE

Never invent:

Canton APIs
Daml syntax
wallet behavior
contract addresses
network endpoints
Party IDs
token contracts
settlement assets
package IDs
Vercel environment variables
DPM commands
sponsor capabilities
deployment steps

If unknown:

Stop.

Report exactly what is unknown.

Explain why it matters.

Tell the builder exactly what action is needed.

Do not build around an invented assumption.

---

# 12. IMPLEMENTATION ORDER

Use these gates:

Gate 0
Environment discovery

Gate 1
Protocol skeleton

Gate 2
Smallest local real flow

Gate 3
Privacy proof

Gate 4
Failure and adversarial tests

Gate 5
DevNet deployment

Gate 6
Evidence layer

Gate 7
Application UI

Gate 8
Polish and accessibility

Gate 9
Production integration

Gate 10
Final submission audit

Do not skip required gates.

Do not call a gate PASS without evidence.

---

# 13. PRODUCT THESIS

Name:

Entivio

One-line proposition:

Entivio privately coordinates multi-party claim payouts and settles them together only when every required party has confirmed.

Human explanation:

When one approved claim needs to pay several people, Entivio lets each person see their own share, confirm it privately, and settle everyone together.

Core Canton mechanisms:

privacy
authorization
coordinated settlement

Primary visible state transition:

2 of 3 confirmed
→ blocked
→ 3 of 3 confirmed
→ ready
→ settled

---

# 14. USER ROLES

## Administrator

Creates the approved claim.

Creates the allocation.

Can see the complete settlement.

Can execute settlement only when protocol conditions allow.

## Recipient

Examples:

Policyholder
Repair Provider
Rental Provider

Can see their own entitlement.

Can confirm only their own entitlement.

Cannot change another recipient's entitlement.

Cannot settle incomplete claims.

---

# 15. MVP SCOPE

Required:

One claim
Three recipients
One administrator
Three recipient parties
One settlement asset
One allocation
Recipient confirmations
Settlement gating
Successful settlement
Early settlement failure
Role-specific visibility
Proof receipt
Canonical run
Verifier

Optional:

Grofty wallet integration
BitSafe authority integration
Hacken Daml audit result

Not in MVP:

AI
OCR
fraud AI
physical accident verification
real insurer API
KYC
real-world claims adjudication
cross-chain bridge
DEX
DAO
token launch
marketplace
complex analytics
email service
mobile application
extra chains
large admin reporting suite


# 16. STATE MACHINE

Primary states:

APPROVED
ALLOCATED
PENDING_CONFIRMATION
READY_TO_SETTLE
SETTLED

Exceptional states:

EXPIRED
CANCELLED

BLOCKED is an operational result shown when an action cannot currently execute. It does not have to be a permanent ledger state.

Transitions:

APPROVED
→ ALLOCATED

ALLOCATED
→ PENDING_CONFIRMATION

PENDING_CONFIRMATION
→ READY_TO_SETTLE

READY_TO_SETTLE
→ SETTLED

Active state before expiry
→ EXPIRED

Eligible active state
→ CANCELLED

SETTLED
→ no further settlement

---

# 17. CLAIM MODEL

Use only fields required by the actual product.

Conceptual fields:

claimId
administrator
totalAmount
settlementAsset
deadline
description
status

The exact Daml type layout must be chosen after checking the current compiler and project format.

Do not copy an old Canton contract structure without verifying it.

---

# 18. ENTITLEMENT MODEL

Conceptual fields:

claim reference
recipient party
amount
role
confirmation state

The entitlement must remain bound to the correct recipient.

A recipient must not be able to act on another recipient's entitlement.

---

# 19. CONTRACT CHOICES

Required:

CreateClaim
Allocate
Confirm
Settle

Optional:

Expire
Cancel

Do not create extra choices unless a real requirement is documented.

---

# 20. ALLOCATION INVARIANT

The sum of all recipient entitlements must equal the approved claim amount.

Example:

6,000
+
3,000
+
1,000
=
10,000

Invalid:

6,000
+
3,000
+
900
=
9,900

Invalid:

6,000
+
3,000
+
2,000
=
11,000

The contract must reject invalid allocations.

Frontend validation is not enough.

---

# 21. CONFIRMATION RULE

A recipient may confirm only their own entitlement.

The confirmation must be authorized by that recipient party.

Confirmation does not change the entitlement amount.

For MVP, allocation amounts should become fixed once allocated.

---

# 22. SETTLEMENT RULE

Settlement must require:

claim exists
allocation exists
claim is active
claim has not expired
claim is not cancelled
all required recipients have confirmed
approved amount is valid
settlement asset is available
settlement has not already occurred

The exact settlement-asset mechanism must be proven in the actual Canton environment.

Do not substitute fake balances.

---

# 23. ATOMICITY REQUIREMENT

Do not design the product as three unrelated frontend payments and label them one settlement.

The target behavior is one coordinated settlement operation producing the valid final state.

The exact technical representation must be verified against the selected Canton asset implementation.

If true atomic value movement cannot be proven:

Stop.

Mark the capability UNPROVEN.

Narrow the product claim.

Do not advertise atomic value settlement until evidence exists.

---

# 24. PRIVACY MODEL

Administrator sees:

full claim
full allocation
confirmation states
settlement status
proof

Recipient sees:

claim reference
their entitlement
their confirmation status
authorized shared state
settlement status

Recipient should not automatically receive unrelated entitlement amounts.

Frontend hiding is not enough.

The underlying ledger visibility must support the privacy claim.

---

# 25. PRIVACY TEST

Create four real parties:

Administrator
Policyholder
Repair Provider
Rental Provider

Create one claim.

Create three entitlements.

Read state from each party's authorized view.

Expected:

Administrator sees full relevant settlement data.

Policyholder sees only their authorized data.

Repair Provider sees only their authorized data.

Rental Provider sees only their authorized data.

If a recipient can query unrelated entitlement information merely because the frontend hides it:

FAIL.

---

# 26. CORE INVARIANTS

INV-01

Allocation total equals approved claim amount.

INV-02

Only administrator can allocate.

INV-03

Recipient can confirm only own entitlement.

INV-04

Recipient cannot modify another entitlement.

INV-05

Settlement cannot execute before all confirmations.

INV-06

Expired claim cannot settle.

INV-07

Cancelled claim cannot settle.

INV-08

Settled claim cannot settle again.

INV-09

Final settlement amount equals approved amount.

INV-10

No valid application state represents a falsely completed partial settlement.

INV-11

Invalid allocation cannot be created.

INV-12

Unauthorized actors cannot perform privileged actions.

INV-13

Participant visibility follows the intended privacy model.

---

# 27. TEST PLAN

## Contract tests

Test:

valid creation
invalid allocation
wrong administrator
wrong recipient
valid confirmation
duplicate confirmation
early settlement
ready settlement
expired settlement
cancelled settlement
duplicate settlement

## Integration tests

Test:

full local flow
multi-party flow
state readback
final state

## Adversarial tests

Test:

recipient A attempts recipient B action
random party attempts admin action
settlement before all confirmations
settlement after deadline
settlement twice
allocation mismatch
invalid amount
missing recipient
invalid asset
wrong network when applicable

## Privacy tests

Test real party visibility.

## E2E tests

Test:

open app
select claim
review
confirm
switch recipient
confirm
observe gate
settle
view proof

---

# 28. TEST REPORTING

Every test report must state:

TEST RUN

Environment

Command

Result

Passed

Failed

Skipped

Important notes

Never say all tests passed unless the tests actually ran and passed.

A skipped test must be reported as skipped.

---

# 29. LOCAL CANONICAL RUN

First canonical run is local.

Steps:

Create Claim
→ Allocate
→ Confirm Policyholder
→ Confirm Repair Provider
→ Confirm Rental Provider
→ Settle
→ Read final state
→ Verify invariants

Record:

date
time
commit
Canton version
DPM version
network
party IDs
claim ID
asset
transactions
expected result
actual result

---

# 30. DEVNET DISCOVERY

Before deploying:

Verify exact DevNet URL.

Verify authentication.

Verify party provisioning.

Verify ledger API access.

Verify DAR deployment method.

Verify available settlement assets.

Verify asset transfer method.

Verify user permissions.

Do not guess.

NODERS' current infrastructure workshop describes DevNet access, party provisioning, API access, DAR deployment, logs and debugging as part of its HackCanton support.

---

# 31. DEVNET CANONICAL RUN

Required flow:

Deploy package
→ create real claim
→ create real allocation
→ confirm real recipients
→ execute real settlement
→ query final state
→ save evidence

PASS requires actual transaction evidence.

No screenshots alone.

---

# 32. RECEIPT IS NOT ENOUGH

After a transaction succeeds:

wait for the relevant state to be readable
→ query
→ assert expected state
→ continue

Do not assume receipt inclusion means the state read is already caught up.

---

# 33. OBSERVABILITY

Record for every important run:

timestamp
step
transaction ID
result
safe error details
final state

Do not log:

private keys
recovery phrases
JWT secrets
API tokens
unnecessary sensitive personal data

---

# 34. EVIDENCE FILES

Final evidence folder:

evidence/
canonical-run.md
canonical-run.json
transactions.json
verification-output.txt
privacy-test.md
adversarial-tests.md
deployment.md
limitations.md

All values must be real.

Never put secrets into evidence.

---

# 35. VERIFIER

Create a repeatable verification command.

Preferred conceptual interface:

npm run verify

The verifier must read actual deployed state.

Report:

Claim
Allocation total
Recipient count
Confirmations
Status
Settlement amount
Transaction identifiers
Invariant checks

Possible outputs:

PASS
FAIL
UNAVAILABLE

Network errors are not PASS.

---

# 36. CLAIM STATUS FILE

Create:

docs/CLAIMS_STATUS.md

For every major technical statement record:

Claim
Status
Evidence
Last checked
Notes

Allowed statuses:

PROVEN
PARTIALLY PROVEN
UNPROVEN
UNAVAILABLE
OUT OF SCOPE

Example:

Canton privacy used by Entivio
PROVEN
Evidence: actual party visibility test

MainNet settlement
UNPROVEN
Evidence: none

Real accident verification
OUT OF SCOPE

---

# 37. LIMITATIONS FILE

Create:

docs/LIMITATIONS.md

For each limitation:

LIMITATION
WHY
IMPACT
CURRENT STATUS
SAFE DESCRIPTION
FUTURE PATH

Do not hide limitations.

---

# 38. UI PRODUCT WORLD

Product world:

The Settlement Room

Adjectives:

calm
precise
private
consequential
trustworthy

Primary visual object:

Settlement Sheet

Signature interaction:

2/3 confirmed
→ blocked
→ 3/3 confirmed
→ ready
→ settled

The product should feel like a controlled operational room, not a crypto trading dashboard.

---

# 39. BRAND

Name:

Entivio

Character:

quiet confidence

Prefer language such as:

Ready to settle
2 of 3 confirmed
Your entitlement
Settlement blocked
Nothing has been transferred
Settlement completed
View proof

Avoid hype:

revolutionary
next generation
AI powered
trustless revolution
Web3 transformation

---

# 40. TYPOGRAPHY

Preferred:

Source Serif 4 for display
IBM Plex Sans for interface
IBM Plex Mono for IDs, amounts, timestamps and technical references

If these exact fonts cannot be used safely or without unnecessary dependency:

Stop and report before changing the visual direction.

Do not silently replace them with a generic dashboard font system.

---

# 41. COLOR TOKENS

Canvas:
#F5F3ED

Primary surface:
#FFFEFA

Primary text:
#151817

Secondary text:
#5E625F

Border:
#D8D8D0

Primary signal:
#245C4A

Positive:
#2E7D5B

Negative:
#B74B42

Warning:
#B17A32

Private state:
#6B6D68

Use restrained color.

No gradients unless a product-specific reason is documented.

---

# 42. DESIGN ANTI-PATTERNS

Do not use:

purple AI gradients
blue crypto glow
glassmorphism
giant bento grids
fake 3D coins
floating token art
decorative crypto charts
giant rounded cards
gradient typography
meaningless badges
generic dashboard sidebars
excessive pills
fake metrics
generic hero illustrations
Powered by blockchain decoration

---

# 43. PRODUCT COMPONENT VOCABULARY

Use:

SettlementSheet
RecipientLane
ConfirmationRail
PrivacyBoundary
SettlementGate
SettlementReceipt
ClaimTimeline
TransactionReference

Generic internal primitives are allowed.

Visible product components should describe actual Entivio concepts.

---

# 44. PRODUCT JOURNEY

Landing
→ Understand
→ Open claim
→ Review allocation
→ Recipient view
→ Confirm
→ Wait
→ All confirmed
→ Ready
→ Settle
→ Verify
→ Receipt

Do not add extra steps without a real requirement.

---

# 45. LANDING PAGE

Headline:

One approved claim.
Every recipient gets their share.
Privately.

Supporting copy:

Entivio coordinates multi-party claim payouts so each participant sees only what they need, while settlement completes only when every required party is ready.

Primary:

Open Demo Claim

Secondary:

View Proof

The Settlement Sheet should appear early.

Do not lead with an abstract blockchain illustration.

---

# 46. CLAIMS INBOX

Show:

claim ID
description
approved amount
recipient count
confirmation count
status

Keep the page focused.

Do not add fake analytics.

---

# 47. CLAIM ROOM

Main components:

Settlement Sheet
Claim Timeline
Recipient Lanes
Settlement Gate
Proof link

This is the central application.

---

# 48. RECIPIENT VIEW

Show:

Your Settlement
Your Amount
Your Confirmation
Overall State

Also show the privacy boundary:

Other recipient amounts
PRIVATE

The underlying ledger must enforce the same boundary.

---

# 49. BLOCKED STATE

Display:

SETTLEMENT BLOCKED

2 of 3 confirmations received.

Rental Provider
Awaiting confirmation

Nothing has been transferred.

This is a core demo state.

---

# 50. READY STATE

Display:

ALL RECIPIENTS CONFIRMED

3 of 3

10,000 units ready

No allocation changes are permitted.

Settle 10,000

This is the pre-settlement climax.

# 51. SETTLED STATE

Display:

SETTLED

Claim ID
Total amount
Recipient count
Final authorized amounts
Transaction reference
Verification state

Provide:

View transaction
View proof
Run verifier

Do not show a fake transaction reference.

---

# 52. PRIVATE STATE

When another recipient's information is not visible, use a clear private-state treatment.

Example:

OTHER RECIPIENT DETAILS
PRIVATE

Do not simply remove the section with no explanation.

The privacy boundary is part of the product story.

---

# 53. CONFIRMATION RAIL

Show:

1 / 3
2 / 3
3 / 3

Each completed confirmation should have a clear visual state.

Do not use decorative progress bars that claim a percentage unrelated to real confirmations.

---

# 54. SETTLEMENT GATE

The gate explains why settlement is unavailable or available.

Pending:

2 of 3 confirmations

One recipient is still required.

Ready:

3 of 3 confirmed

Settlement can execute.

Blocked must be a truthful state derived from the actual backend/ledger state.

---

# 55. CLAIM TIMELINE

Show:

Approved
Allocated
Confirming
Ready
Settled

If a state has not actually happened, do not mark it completed.

The timeline is not decoration.

It is a representation of protocol state.

---

# 56. TRANSACTION REFERENCE

Show a shortened safe transaction identifier in the UI.

Provide the full identifier on the proof screen if safe.

Never fabricate identifiers.

If no transaction exists:

show:

Transaction not available

not a placeholder.

---

# 57. LOADING STATES

Examples:

Loading claim state

Checking settlement status

Submitting confirmation

Verifying final state

Do not use fake progress percentages.

Do not show "87% complete" unless that value has a real meaning.

---

# 58. ERROR STATES

Example:

SETTLEMENT FAILED

The ledger rejected the request.

Show safe error details.

Do not leak credentials.

Do not replace a real backend failure with a generic fake success.

---

# 59. EMPTY STATE

Example:

NO OPEN CLAIMS

There are no claims waiting for your action.

Do not show fake sample metrics in production mode.

---

# 60. PROOF ERROR STATE

If verification cannot run:

VERIFICATION UNAVAILABLE

We could not check the ledger state right now.

Do not show:

VERIFIED

---

# 61. RESPONSIVE DESIGN

Desktop is not the only target.

Mobile must be intentionally designed.

Main task on mobile:

open claim
review
confirm
see state
settle if authorized
view proof

No horizontal scrolling for the primary flow.

---

# 62. ACCESSIBILITY

Required:

keyboard navigation
visible focus
button labels
form labels
clear error messages
logical reading order
sensible contrast
reduced motion support

Do not sacrifice accessibility to visual style.

---

# 63. BACKEND ARCHITECTURE

Preferred conceptual architecture:

Browser
→ Next.js / TypeScript application
→ Canton integration adapter
→ Canton JSON Ledger API or exact currently supported application API
→ Daml contracts

The final integration method must be validated against the real HackCanton environment.

Do not assume a private endpoint can be reached from Vercel.

---

# 64. DATABASE POLICY

MVP default:

No database.

Canton is the source of truth for claim state.

Do not add PostgreSQL, MongoDB, Firebase, Supabase, Redis, or another database unless a verified requirement appears.

Any added database must have:

reason
free status
Vercel compatibility
cloud CI compatibility
data model
source-of-truth rules

---

# 65. API POLICY

Create only the endpoints actually required.

Possible conceptual routes:

GET claim
GET claims
GET recipient view
POST create claim
POST allocation
POST confirmation
POST settlement
GET proof

Actual names are implementation details.

Do not duplicate ledger logic across many application layers.

---

# 66. AUTHORIZATION POLICY

Do not trust a browser role value.

For example:

role=administrator

is not proof of administrator authority.

The ledger or trusted authentication layer must enforce privileged actions.

Frontend role information is presentation only.

---

# 67. ENVIRONMENT VARIABLES

Public template:

.env.example

Private local values:

.env.local

Production secrets:

Vercel environment variables

Never store real values in:

source
README
public evidence
screenshots
GitHub Actions logs

Before each push, confirm .env.local is not staged.

---

# 68. VERCEL

Deployment target:

Vercel

Before implementation:

check current Next.js support
check runtime constraints
check request duration
check outbound network behavior
check environment variable handling
check whether Canton integration can safely run in Vercel
check whether any persistent connection is required

If Vercel cannot safely support the required Canton integration:

stop

report

select only a verified zero-cost architecture

Do not create a hidden paid backend.

---

# 69. GITHUB

Repository should be the public source of truth for safe project files.

Recommended:

GitHub repository
GitHub Actions
Vercel connected to repository

Do not push personal credentials.

Do not push local secrets.

Do not push irrelevant private notes.

---

# 70. CI

Minimum CI checks:

dependency install
lint
typecheck
unit tests
integration tests where environment allows
production build

Canton-specific tests that require a supplied environment may be separated.

The report must distinguish:

Passed
Failed
Skipped
Blocked

A skipped test is not a passed test.

---

# 71. HEAVY BUILD

When local build is too heavy:

push a small coherent commit

run GitHub Actions

inspect output

fix

rerun

Do not repeatedly force the 8 GB PC through large builds.

---

# 72. DEPENDENCY RULE

Before installing a package, record:

name
version
purpose
license
free status
reason
Vercel compatibility
GitHub Actions compatibility

Avoid package sprawl.

---

# 73. DPM DISCOVERY

Before writing Daml project files:

check actual DPM installation
record version
verify project creation command
verify build command
verify test command
verify DAR output path

Do not use obsolete commands just because an old tutorial contains them.

---

# 74. DAML DISCOVERY

Verify:

Daml language version
compiler version
daml.yaml structure
package dependencies
test syntax
template identifiers
choice syntax

Do not invent package names.

---

# 75. JSON LEDGER API DISCOVERY

Verify:

base URL
authentication
command endpoint
query endpoint
active-contract query behavior
party service
package deployment endpoint if used
expected JSON shapes

The current Digital Asset JSON Ledger API reference provides OpenAPI and AsyncAPI specifications.

Use the actual endpoint exposed by the current environment.

---

# 76. PACKAGE / DAR DEPLOYMENT

Build the DAR.

Record actual path.

Deploy using the verified current method.

Record:

package identifier
version
deployment time
network

Do not hard-code package IDs before deployment.

---

# 77. PARTY MANAGEMENT

Use real parties from the selected environment.

Do not use Party IDs copied from examples.

Record public Party IDs only if safe.

Store private credentials locally.

---

# 78. SETTLEMENT ASSET GATE

The exact settlement asset is intentionally not hard-coded in this specification.

The chosen asset must be:

free to use
actually available
supported by the current Canton environment
usable by the required parties
transferable through the chosen mechanism
verifiable in the canonical run

Potential assets such as CC or USDCx must be treated as candidates until verified.

Do not assume availability.

---

# 79. IF ASSET ACCESS FAILS

Do not create fake balances.

Do not call an internal database transfer a blockchain settlement.

Do not display a successful payment without actual evidence.

Report:

BLOCKED

Reason:
No verified free settlement asset is available for the required live flow.

Then evaluate the supported options.

---

# 80. GROFTY OPTIONAL GATE

Only begin Grofty work after core Canton flow passes.

Verify:

wallet installation
current onboarding
Party ID
signing
asset availability
network
transaction behavior

If Grofty onboarding is unavailable:

continue Entivio without it.

---

# 81. BITSafe OPTIONAL GATE

Only use BitSafe if it materially improves the product.

Verify exact current integration.

Do not add it just for sponsor count.

The core product must remain useful without the optional layer.

---

# 82. HACKEN OPTIONAL GATE

Run security audit tooling only after core tests exist.

Security tooling is evidence.

It does not prove absolute security.

Record:

tool
version
date
scope
findings
severity
remediation
rerun result

---

# 83. NO AI IN CORE

Decision:

AI is not part of Entivio's core settlement mechanism.

Reason:

The core problem is deterministic.

AI does not materially improve:

allocation
authorization
confirmation
settlement

Do not add an AI assistant just to call the application AI-powered.

---

# 84. NO INSURANCE ORACLE

Decision:

Claim approval is an input.

Entivio does not verify physical-world accidents.

Reason:

A trustworthy external event oracle is outside the MVP and would introduce another dependency.

Safe claim:

Entivio settles an already-approved claim.

---

# 85. NO FAKE BLOCKCHAIN

Do not build:

mock transaction after button click
fake hash
fake block height
fake wallet balance
fake Canton status
fake explorer
fake settlement receipt

Demo data may be used before the real environment is ready, but the UI must clearly identify demo data.

---

# 86. REAL-FIRST RULE

If a feature cannot be made real:

Identify blocker.

Determine whether feature is core.

Document limitation.

Remove false claim.

Either replace dependency with a verified option or reduce scope.

Do not fake the feature.

---

# 87. PHASE 0 ACCEPTANCE

Environment discovery complete.

Required outputs:

actual OS
Node version
npm version
Git version
DPM status
Canton status
Java status if required
GitHub status
Vercel status
DevNet access status
asset status

PASS:

No unknown mandatory tool blocks protocol work.

---

# 88. PHASE 1 ACCEPTANCE

Daml protocol skeleton exists.

Required:

Claim
Entitlement
authorization
state machine
invariants
tests

PASS:

project builds

tests execute

authorization is represented in code

---

# 89. PHASE 2 ACCEPTANCE

One complete local real flow.

Create
→ allocate
→ confirm 1
→ confirm 2
→ confirm 3
→ settle

PASS:

final state is correct

state can be read

verifier can confirm it

---

# 90. PHASE 3 ACCEPTANCE

Privacy proof.

PASS:

actual participant visibility behavior matches design.

Frontend masking alone does not pass this gate.

---

# 91. PHASE 4 ACCEPTANCE

Adversarial tests.

PASS:

invalid actions are rejected.

Examples:

early settlement
wrong recipient
wrong administrator
expired claim
duplicate settlement
invalid allocation

---

# 92. PHASE 5 ACCEPTANCE

DevNet deployment.

PASS:

real deployment
real parties
real claim
real allocation
real confirmations
real settlement
real state verification

---

# 93. PHASE 6 ACCEPTANCE

Evidence.

Required:

canonical run
transactions
verifier
privacy evidence
adversarial evidence
claims status
limitations

PASS:

external reviewer can follow the proof.

---

# 94. PHASE 7 ACCEPTANCE

UI.

Required:

landing
claims
claim room
recipient view
blocked
ready
settled
proof

PASS:

main journey works.

---

# 95. PHASE 8 ACCEPTANCE

Visual and accessibility polish.

PASS target:

20/24 or higher on final visual gate.

Any zero on:

product clarity
visual identity
technical mechanism
technical honesty

means redesign.

---

# 96. PHASE 9 ACCEPTANCE

Full deployed E2E.

PASS:

production web application
→ real ledger action
→ real state change
→ proof

If production action is not real:

label it accurately.

---

# 97. PHASE 10 ACCEPTANCE

Submission.

PASS:

all submission artifacts complete
all links work
repo safe
claims truthful
canonical evidence exists
demo works

---

# 98. PRODUCT ACCEPTANCE TESTS

AT-01

Visitor understands product in 5 seconds.

AT-02

Visitor understands product in 30 seconds.

AT-03

Administrator can create claim.

AT-04

Administrator can create valid allocation.

AT-05

Invalid allocation fails.

AT-06

Recipient sees own entitlement.

AT-07

Recipient cannot act for another recipient.

AT-08

Early settlement is blocked.

AT-09

Three confirmations unlock settlement.

AT-10

Settlement succeeds.

AT-11

Final state is readable.

AT-12

Proof page contains real evidence.

AT-13

Verifier reports correct result.

AT-14

Expired claim fails.

AT-15

Duplicate settlement fails.

AT-16

Unauthorized privileged action fails.

AT-17

Public repository contains no secret files.

AT-18

Vercel deployment works.

---

# 99. STRANGER TEST

Give the app to someone who has not seen the project.

Do not explain it first.

After 5 seconds ask:

What is this?

After 30 seconds ask:

What does it do?

After 60 seconds ask:

Why does Canton matter?

Record the answers.

If unclear:

FAIL UX test.

---

# 100. FINAL DEMO

Canonical demo:

0 to 5 seconds

Product name and proposition.

5 to 15 seconds

Approved claim and three recipients.

15 to 25 seconds

Recipient-specific private view.

25 to 35 seconds

Early settlement attempt blocked.

35 to 45 seconds

Final confirmation.

45 to 52 seconds

Settlement.

52 to 60 seconds

Real Canton transaction proof.

End.

---

# 101. DEMO SCRIPT

Entivio privately coordinates multi-party claim settlements.

This approved claim is worth 10,000 units and needs to pay three parties.

Each participant sees their own entitlement.

We try to settle before everyone is ready and the system blocks it.

The last participant confirms.

Now the settlement is ready.

We settle it.

Here is the real Canton transaction and resulting ledger state.

That is the product:

private participant coordination with enforced settlement conditions.

---

# 102. TECHNICAL EXPLANATION

After the product demo, say:

The claim and entitlements are represented as Canton/Daml state.

Each role has explicit authorization.

Recipients can confirm only their own entitlement.

Settlement is gated by the required conditions.

The ledger is the source of truth.

The final state is verified from the ledger.

The repository contains tests for invalid actions and privacy behavior.

Do not add unsupported claims.

---

# 103. WHY CANTON

Answer:

Entivio needs several parties to coordinate around one financial workflow while seeing different information.

Canton provides participant-scoped privacy and authorization capabilities that make this possible at the ledger level.

The project therefore uses Canton for a behavior that matters to the product rather than merely deploying a frontend on Canton.

---

# 104. NOVELTY ANSWER

Safe version:

The novelty is not simply putting claims on a blockchain.

Entivio turns a multi-recipient claim into a role-scoped settlement workflow where participants confirm their own entitlements and the final settlement is coordinated through the ledger.

Do not claim first-ever status unless independently verified.

---

# 105. DOES IT WORK ANSWER

Show:

canonical run

real transaction

final state

verifier

Do not answer only with:

Yes.

---

# 106. VIDEO STRUCTURE

Opening:

product immediately

Middle:

blocked state

then final confirmation

then settlement

Ending:

transaction proof and one-sentence Canton explanation

Do not spend the opening on architecture diagrams.

---

# 107. SCREENSHOT SET

Use approximately five screenshots:

1. Product landing
2. Private recipient view
3. Blocked settlement
4. Ready / settled state
5. Proof receipt

Avoid weak screenshots.

Avoid random development screenshots.

---

# 108. PUBLIC README STRUCTURE

Recommended:

# Entivio

One-line proposition

## 30-second explanation

## Demo

## Live deployment

## What is novel

## Why Canton matters

## How it works

## Verified end-to-end

## Architecture

## Security and invariants

## Known limitations

## Reproduction

## Contract / package information

## License

Put proof near the top.

---

# 109. README TRUTH RULE

Do not write:

Fully decentralized insurance.

Trustless insurance.

Fully secure.

Production ready.

Guaranteed compliance.

Zero counterparty risk.

Oracle verified.

MainNet live.

unless the actual evidence proves the exact statement.

---

# 110. SUBMISSION PACKAGE

Required final artifacts:

live URL
GitHub repository
deployed package / contract information
canonical run
verifier command
demo video
pitch copy
screenshots
technical description
limitations / evidence notes

Before submission, compare this list with the current HackCanton form.

---

# 111. FINAL VISUAL QUALITY GATE

Score 0 to 2:

product clarity
product-specific identity
technical mechanism visualized
information hierarchy
typography
spacing
signature interaction
state coverage
motion
mobile
technical honesty
judge proof

Target:

20/24 minimum.

Zero on key identity or honesty categories triggers redesign.

---

# 112. ANTI-AI UI TEST

Ask:

Could an AI have made this as a generic premium Web3 dashboard?

If yes:

FAIL.

Remove the logo.

Can the reviewer still identify:

Settlement Sheet
privacy boundary
confirmation rail
settlement gate
state transition

If no:

FAIL.

---

# 113. PUBLIC/LOCAL FILE MAP

Public:

src
app
components
lib
daml
tests
safe docs
safe evidence
README
package files
CI files
public assets

Local:

.env.local
private credentials
wallet files
recovery phrases
private keys
personal notes
temporary secrets
temporary exports

The final public repository must be manually reviewed before submission.

---

# 114. ENVIRONMENT FILE POLICY

Create:

.env.example

with names only and safe examples.

Actual values go in:

.env.local

and Vercel environment settings.

Never commit actual production secret values.

---

# 115. GITHUB ACTIONS SECRETS

If CI needs secrets:

Use GitHub repository secrets or environment secrets.

Never write secrets directly into workflow YAML.

Do not echo secret values into logs.

Use least privilege.

Delete unnecessary secrets after the hackathon if appropriate.

---

# 116. VERCEL SECRETS

Use Vercel environment configuration.

Separate:

Preview
Development
Production

only where actually needed.

Do not place secret values in source.

After deployment:

inspect Vercel logs for accidental secret output.

---

# 117. DEPLOYMENT LOG

Create:

docs/DEPLOYMENT.md

Record:

deployment date
commit
Vercel project
production URL
Canton network
package identifier
asset
important environment notes
known limitations

Never put secret values in this file.

---

# 118. CANONICAL RUN FILE

Create:

docs/CANONICAL_RUN.md

Record:

run ID
commit
network
Canton version
DPM version
administrator party
recipient parties
claim ID
asset
steps
transactions
expected state
actual state
verification result

Use real data.

---

# 119. TRANSACTION ARTIFACT

Create:

evidence/transactions.json

Suggested fields:

runId
step
timestamp
transactionId
network
safe description

Do not include private credentials.

---

# 120. VERIFICATION OUTPUT

Create:

evidence/verification-output.txt

This must be real output from the verifier.

Do not manually type a fake PASS.

---

# 121. PRIVACY EVIDENCE

Create:

evidence/privacy-test.md

Include:

party tested
expected visibility
actual visibility
result
date
environment

Do not include secrets.

---

# 122. ADVERSARIAL EVIDENCE

Create:

evidence/adversarial-tests.md

For each test:

test ID
attempt
expected
actual
result

---

# 123. SECURITY DOCUMENT

Create:

docs/SECURITY.md

Explain:

authorization
recipient binding
allocation invariant
settlement gate
expiry
double-settlement protection
privacy
limitations

Use evidence references.

---

# 124. ARCHITECTURE DOCUMENT

Create:

docs/ARCHITECTURE.md

Include:

system diagram
frontend
Canton integration
Daml contracts
ledger state
proof system
deployment
trust boundaries
data flow

Do not create a diagram with components that do not exist in the final system.

---

# 125. ARCHITECTURE DECISIONS

Important decisions should be recorded.

Examples:

ADR-001
No AI in core settlement

ADR-002
Approved claim is an input

ADR-003
Ledger is source of truth

ADR-004
No database in MVP

ADR-005
Grofty optional

ADR-006
Settlement asset selected only after verified availability

Add more only when a real decision requires them.

---

# 126. CHANGE CONTROL

For architectural changes record:

date
decision
old approach
new approach
reason
impact
tests affected
docs affected

Do not silently change architecture.

---

# 127. USER ACTION RULE

If builder must obtain:

wallet
Party ID
DevNet access
whitelist access
GitHub permission
Vercel permission
test asset
DApp
browser extension

provide exact steps.

Use:

USER ACTION REQUIRED

What you need to do

Step 1
...

Step 2
...

Step 3
...

What should happen

...

What to tell me afterward

...

Do not assume builder knows the platform.

---

# 128. BLOCKER RULE

When blocked:

PHASE BLOCKED

What is missing

Why it matters

What was checked

Exact action needed

What happens afterward

Do not continue with a fake substitute.

---

# 129. PHASE REPORT

After every phase:

PHASE

Status

Completed

Tests

Evidence

Security findings

Known limitations

Files changed

Public files added

Local-only files

Next phase

Keep the language simple.

---

# 130. EXAMPLE PHASE REPORT

PHASE 2

Status

PASS

Completed

Created the claim and entitlement contracts.

Added authorization.

Added settlement gating.

Tests

Contract tests: PASS

Early settlement test: PASS

Unauthorized recipient test: PASS

Evidence

Local canonical run: PASS

Security findings

No known critical issue.

Known limitations

DevNet settlement has not been tested yet.

Files changed

daml/...
tests/...

Next phase

Privacy testing.

---

# 131. EXAMPLE BLOCKER REPORT

PHASE 5

Status

BLOCKED

What is missing

The required free settlement asset is not available to the DevNet parties.

Why it matters

Without the asset we cannot prove real value settlement.

What was checked

Party provisioning works.

Contracts deploy.

Claim creation works.

Allocation works.

Settlement asset access fails.

What you need to do

Use the HackCanton-provided asset onboarding path.

What happens afterward

Run the settlement test again.

---

# 132. STOP CONDITIONS

Stop immediately if:

required environment cannot be accessed
settlement asset unavailable
privacy mechanism cannot be verified
Canton integration differs from assumed design
Vercel cannot reach required service
dependency becomes paid
secret was exposed
contract behavior conflicts with specification
current event rules conflict with this document
technical claim cannot be proven

Do not improvise a solution without reporting it.

---

# 133. SCOPE CUT RULE

When time becomes short, keep:

Claim
Allocation
Recipient confirmation
Settlement gate
Settlement
Privacy proof
Transaction proof

Remove first:

Grofty enhancement
BitSafe enhancement
Hacken enhancement
extra dashboards
analytics
secondary use cases
non-essential animations

Do not cut the evidence layer before cutting optional features.

---

# 134. FINAL CANONICAL CLAIM

The product should be able to truthfully say:

Entivio coordinates settlement for an already-approved multi-party claim.

Each participant sees authorized information.

Required confirmations are enforced.

Settlement is gated by actual protocol state.

The final state can be verified.

That is the core product.

---

# 135. FINAL DEMO FALLBACK

Primary:

live deployed application

Secondary:

recorded canonical run

Tertiary:

static proof artifacts

Never pass off a recorded transaction as newly executed.

Never present static proof as live execution.

Label fallbacks clearly.

---

# 136. FINAL REPOSITORY CHECK

Before final submission:

git status

inspect changed files

inspect staged files

search for likely secrets

check .gitignore

check environment files

check wallet files

check private documentation

check machine-specific paths

review latest pushed commit

review GitHub repository itself

---

# 137. FINAL DEPLOYMENT CHECK

Verify:

production URL works
claim loads
recipient view works
confirmation works
settlement gate works
real settlement works if claimed
proof works
transaction link works
verifier works

If any claimed live function does not work:

remove or correct the claim before submission.

---

# 138. FINAL CLAIM CHECK

Review every important statement in:

README
landing page
submission form
demo script
video
technical docs

Ask:

Can this be proven?

If yes:

PROVEN

If partly:

PARTIALLY PROVEN

If no:

UNPROVEN

If outside MVP:

OUT OF SCOPE

Remove unsupported claims.

---

# 139. FINAL SUBMISSION CHECKLIST

Product

One-sentence proposition is clear.

User is specific.

Core capability is concrete.

Canton requirement is explicit.

Sponsor

Canton is native.

Canton is load-bearing.

Counterfactual is documented.

Live capability is tested.

Limits are documented.

UX

Five-second comprehension passes.

Thirty-second comprehension passes.

Main journey is obvious.

Signature interaction exists.

State machine appears in UI.

Errors exist.

Loading exists.

Empty state exists.

Visual

Product-specific world exists.

Tokens exist.

Anti-patterns are banned.

Technical mechanism is visible.

Mobile is intentional.

Asset provenance exists.

Engineering

Real deployment exists.

Unit tests exist.

Integration tests exist.

Adversarial tests exist.

Privacy test exists.

E2E exists.

Invariants are documented.

No fake production success paths.

Proof

Canonical run exists.

Transaction identifiers exist.

Verifier exists.

Evidence exists.

Claim status exists.

Limitations exist.

Demo

Before state exists.

Action exists.

Visible state change exists.

Proof exists.

Closing message is clear.

Submission

Live URL works.

Repository works.

Screenshots are strong.

Demo works.

Sponsor selections are accurate.

Package / contract information is correct.

Description is truthful.

No unsupported claims.

Stranger review completed.

---

# 140. FINAL COMPLETION STANDARD

The project is complete only when:

core protocol is real
core flow works
privacy is tested
authorization is tested
settlement gating works
settlement is proven
final state is verified
deployed app reflects real state
canonical run exists
verifier exists
public repository is safe
README is truthful
demo works
submission package is complete

Anything missing means:

NOT COMPLETE

---

# 141. FINAL AGENT INSTRUCTION

Before changing code:

Read this entire file.

Inspect current repository.

Inspect environment.

Check current official Canton documentation.

Check current HackCanton instructions.

Check current sponsor instructions if used.

Report what is known.

Report what is unknown.

Report blockers.

Only then implement the current gate.

---

# 142. DO NOT SKIP VERIFICATION

Do not say:

It should work.

It looks correct.

The deployment is probably fine.

The transaction should be valid.

The wallet likely supports this.

Canton probably exposes this endpoint.

Use actual tests or clearly mark the statement as unverified.

---

# 143. DO NOT BUILD FROM MEMORY

For current Canton tooling:

verify docs

verify installed versions

verify commands

verify API

verify environment

For HackCanton:

verify current event requirements

verify current sponsor requirements

verify current submission form

For Vercel:

verify current runtime behavior

verify environment

Do not rely on stale knowledge.

---

# 144. KEEP THE CORE SMALL

The winning product is not the product with the most screens.

The winning product is the clearest complete proof.

Prioritize:

real workflow
privacy
authorization
settlement
proof

over:

number of features
number of pages
number of integrations
number of sponsors

---

# 145. DO NOT TURN THIS INTO A GENERIC DASHBOARD

The main screen must revolve around:

Settlement Sheet

Recipient Lanes

Confirmation Rail

Settlement Gate

Claim Timeline

Proof

If the page starts becoming:

sidebar
cards
charts
metrics
widgets
AI panel

stop and redesign.

---

# 146. FINAL PRODUCT LANGUAGE

Entivio

One approved claim.

Every recipient gets their share.

Privately.

Core transition:

WAITING
→ READY
→ SETTLED

Core technical mechanism:

Canton privacy
+
authorization
+
coordinated settlement

Core proof:

real ledger state
+
real transaction evidence
+
repeatable verifier

---

# 147. FINAL HANDOFF RULE

This specification is the baseline for the coding assistant.

The coding assistant may improve implementation details when evidence supports the change.

It must not weaken:

privacy
authorization
settlement correctness
zero-budget constraint
public-repository safety
Vercel deployment target
GitHub cloud build preference
evidence-first engineering
product-specific design
technical honesty

When a conflict occurs:

stop

document

ask for clarification only when necessary

otherwise follow the higher-priority source-of-truth rule.

---

# 148. END

End condition:

Entivio is a real, verifiable, judge-readable multi-party settlement product built on Canton, with a public-safe repository and a Vercel-deployed application.

The project is not considered finished because the interface looks finished.

It is finished when the core behavior, deployment, evidence and communication all agree with each other.
