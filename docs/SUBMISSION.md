# GenLayer submission dossier ? NoticeClock

## Project name

NoticeClock

## Short description

Assess contractual notice and cure evidence against frozen terms with independent semantic consensus and an explicit inconclusive outcome.

## Detailed description

NoticeClock coordinates a three-party case in which the parties freeze a notice/cure clause, submit evidence, and nominate a distinct attestor wallet. GenLayer validators independently assess whether a breach is identified, the clause applies, and the requested cure is clear. State changes remain bounded by frozen terms, challenge rights, and deterministic deadlines.

## Problem solved

Parties disagree over whether a notice identifies an applicable breach and states a sufficiently clear cure.

## Why this requires a GenLayer Intelligent Contract

Validators need to interpret natural-language notice and evidence against the precise frozen clause. Deterministic code cannot make that semantic assessment; the contract keeps its powers, roles, deadlines and result schema deterministic.

## Genuine semantic-consensus behavior

Inside gl.vm.run_nondet_unsafe, the leader and validators independently evaluate breach_identified, clause_applicable, requested_cure_clear and evidence_sufficient. A strict boolean schema is checked. Contract code derives READY, INVALID or INCONCLUSIVE; disagreement cannot silently approve.

The leader and validators independently execute the semantic evaluation. The result is schema-validated and contract code alone maps it to permitted outcomes. Evidence and challenge text are untrusted input. Disagreement and invalid output cannot silently become approval. Challenge periods and finalization use contract transaction time.

## GitHub repository

https://github.com/GIFTEDLOV/noticeclock

## Production app

Not applicable: standalone Intelligent Contract.

## Studionet deployment

- Network: GenLayer Studionet
- Chain ID: `61999`
- Canonical RPC: `https://studio.genlayer.com/api`
- Contract: [0x99D41333f28913BA45Fc36C64eb0A88D1600F350](https://explorer-studio.genlayer.com/address/0x99D41333f28913BA45Fc36C64eb0A88D1600F350)
- Verified deployed source SHA-256: `b968431218e2b8e1e24264a13a81c9cadde7a2d321e661df50e907dbed545e13`
- ABI schema SHA-256: `cef0fd7d95e3e616bc62644966e692e28ec805bf1fa738043a0e75e71dc043a4`

## Live demonstration and evidence

- Historic case: `NCQUAL-39142055216`; status `FINALIZED`; terminal verdict **INCONCLUSIVE**.
- Qualification workflow: [run 39142055216](https://github.com/GIFTEDLOV/driftproof/actions/runs/39142055216).
- Deployed contract and source parity evidence: `evidence/live-verification.json`.
- The successful NoticeClock lifecycle is case `NCQUAL-39142055216`; the earlier workbench NoticeClock attempt is preserved as BLOCKED because its canonical adjudication state did not match.

## Security and qualification summary

Tests and CI cover role separation, immutable terms, string and SDK address serialization, invalid transitions, strict semantic schema, prompt boundaries, disagreement handling, challenge timing, evidence provenance, history integrity, and finalization. The independently verified live outcome is INCONCLUSIVE; the contract correctly did not turn uncertainty into approval.

- Exact-main CI: [workflow run 39161740779](https://github.com/GIFTEDLOV/noticeclock/actions/runs/39161740779) passed for the then-current main commit. Release-preparation exact-head CI and version tag CI will be linked on the repository release.
- CI covers Python tests, GenVM lint, ABI/schema, source provenance, security analysis and app SDK/build/browser tests where applicable.
- No unresolved Critical or High issue was identified in the release audit.
- The historic 39138804500 workbench is not represented as a four-project PASS: NoticeClock was BLOCKED; the other three project artifacts individually report PASS. NoticeClock's later case 39142055216 passed its lifecycle, with terminal verdict INCONCLUSIVE.

## Instructions for reviewers

1. Inspect `contracts/noticeclock.py` and `release.json`.
2. Verify the deployed source and ABI against the hashes above using the checked-in read-only verifier.
3. Review the case and receipt evidence under `evidence/`; a FINALIZED label is not treated as proof without successful GenVM execution and canonical state readback.
4. Confirm this is a standalone contract submission; it does not claim a production app.
5. Treat all qualification cases and source records as synthetic test inputs; do not infer real-world events.

## Known limitations and external trust assumptions

The live qualification used explicitly labeled synthetic evidence. An attestor signature proves control of the nominated wallet, not the real-world sender's identity or notice authenticity. The contract is not legal advice, a document-authentication service, or a payment/settlement system. All cases remain in append-only storage; there is no deletion or pruning interface.

## Portal status

The submission fields and evidence package are **prepared for immediate Portal entry**. The final Portal submission has **not** been made. It requires an authenticated Builder Portal session and explicit final-submit authorization; no claim of submission or steward approval is made.
