# NoticeClock

Assess contractual notice and cure evidence against frozen terms with independent semantic consensus and an explicit inconclusive outcome.

**Release:** v4.0.0 ? **Network:** GenLayer Studionet (chain `61999`) ? **Contract:** [`0x99D41333f28913BA45Fc36C64eb0A88D1600F350`](https://explorer-studio.genlayer.com/address/0x99D41333f28913BA45Fc36C64eb0A88D1600F350)

## What it does

NoticeClock coordinates a three-party case in which the parties freeze a notice/cure clause, submit evidence, and nominate a distinct attestor wallet. GenLayer validators independently assess whether a breach is identified, the clause applies, and the requested cure is clear. State changes remain bounded by frozen terms, challenge rights, and deterministic deadlines.

## Why GenLayer

Validators need to interpret natural-language notice and evidence against the precise frozen clause. Deterministic code cannot make that semantic assessment; the contract keeps its powers, roles, deadlines and result schema deterministic.

Inside gl.vm.run_nondet_unsafe, the leader and validators independently evaluate breach_identified, clause_applicable, requested_cure_clear and evidence_sufficient. A strict boolean schema is checked. Contract code derives READY, INVALID or INCONCLUSIVE; disagreement cannot silently approve.

## Deployment provenance

- Canonical RPC: `https://studio.genlayer.com/api`
- Exact deployed source SHA-256: `b968431218e2b8e1e24264a13a81c9cadde7a2d321e661df50e907dbed545e13`
- ABI schema SHA-256: `cef0fd7d95e3e616bc62644966e692e28ec805bf1fa738043a0e75e71dc043a4`
- `getContractCode` source-byte parity: exact match with `contracts/noticeclock.py`.
- Explorer: https://explorer-studio.genlayer.com/address/0x99D41333f28913BA45Fc36C64eb0A88D1600F350

## Live qualification

- Historic case: `NCQUAL-39142055216`, terminal `INCONCLUSIVE`; source data is synthetic and explicitly labeled.
- Historic qualification: [GitHub Actions run 39142055216](https://github.com/GIFTEDLOV/driftproof/actions/runs/39142055216).
- Project exact-head CI: [run 39161740779](https://github.com/GIFTEDLOV/noticeclock/actions/runs/39161740779).
- This is a standalone contract; no frontend app is claimed.

## Release and submission status

The v4.0.0 package source and submission materials are prepared in this independent repository. GitHub release publication follows exact-head CI. Submission fields and review instructions are in [docs/SUBMISSION.md](docs/SUBMISSION.md) and [docs/SUBMISSION_FIELDS.json](docs/SUBMISSION_FIELDS.json). The Portal entry is **prepared, not submitted**; a final Portal submission is an authenticated action.

## Checks

Requirements: Python 3.12+, Node.js 22+, npm.

```powershell
python -m pip install -r requirements-dev.txt
python -m pytest -q
python -m genvm_linter.cli lint contracts/noticeclock.py
npm ci
npm run verify:live
```

Python tests and live verifier run in this repository. Unit and mocked integration tests are not a substitute for the live consensus evidence linked above.

See [security audit](docs/SECURITY.md), [deployment](docs/DEPLOYMENT.md), [rejection-prevention matrix](docs/REJECTION_PREVENTION.md), and [release qualification](docs/RELEASE.md). MIT License.
