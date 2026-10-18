# NoticeClock

Assess contractual notice and cure evidence against frozen terms with independent semantic consensus and an explicit inconclusive outcome.

**Package:** v4.0.0-rc.1 · **Network:** Studionet `61999` · **Contract:** [`0x99D41333f28913BA45Fc36C64eb0A88D1600F350`](https://explorer-studio.genlayer.com/address/0x99D41333f28913BA45Fc36C64eb0A88D1600F350)

## Description

NoticeClock coordinates a three-party case in which the parties freeze a notice/cure clause, submit evidence, and nominate a distinct attestor wallet. GenLayer validators independently assess whether a breach is identified, the clause applies, and the requested cure is clear. State changes remain bounded by the frozen terms, challenge rights, and deterministic deadlines.

## Deployment provenance

- RPC: `https://studio.genlayer.com/api`
- Exact deployed-source SHA-256: `b968431218e2b8e1e24264a13a81c9cadde7a2d321e661df50e907dbed545e13`
- Independently recomputed ABI schema SHA-256: `cef0fd7d95e3e616bc62644966e692e28ec805bf1fa738043a0e75e71dc043a4`
- `getContractCode` parity: exact match with `contracts/noticeclock.py`.

## Existing live case

Case `NCQUAL-39142055216` reached `FINALIZED`, round 2, with terminal verdict **INCONCLUSIVE**. Evidence is in `evidence/noticeclock-live.json`; the recorded run is [39142055216](https://github.com/GIFTEDLOV/driftproof/actions/runs/39142055216) for NoticeClock and [39138804500](https://github.com/GIFTEDLOV/driftproof/actions/runs/39138804500) for the other projects. Run 39138804500 as a whole failed because NoticeClock disagreed; the three case artifacts preserved here individually report `PASS`. Source evidence is synthetic and labeled.

## Release status

The existing deployed V4 contract is preserved and byte-verified. **This package is not submission-qualified as a complete release yet.** ParcelCourt and ShiftFair production URLs still serve older read-only bundles. Their updated source in `web/` is not deployed, and signing remains disabled (`RELEASE_QUALIFIED=false`) until a funded ephemeral-signer browser transaction passes actual GenVM receipt and canonical-state checks. No live positive verdict is claimed.

## Run checks

Requirements: Python 3.12+, Node.js 22+, npm.

```powershell
python -m pip install -r requirements-dev.txt
python -m pytest -q
python -m genvm_linter.cli lint contracts/noticeclock.py
npm ci
npm run verify:live
```

For the two frontend repos: `cd web; npm ci; npm run check; npm test; npm run build; npm audit --audit-level=high`. Python tests use an explicit local API fixture; they are regression tests, not live consensus proof. The read-only verifier independently checks code bytes, ABI, receipt summaries, canonical state and history through GenLayerJS 1.1.8.

See [Security](docs/SECURITY.md), [Deployment](docs/DEPLOYMENT.md), [Rejection prevention](docs/REJECTION_PREVENTION.md), [Submission dossier](docs/SUBMISSION.md) and [Release status](docs/RELEASE.md). MIT license in `LICENSE`.
