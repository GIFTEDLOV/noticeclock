# Deployment and verification

## Contract

- Network: GenLayer Studionet, chain ID `61999`
- RPC: `https://studio.genlayer.com/api`
- Contract: [0x99D41333f28913BA45Fc36C64eb0A88D1600F350](https://explorer-studio.genlayer.com/address/0x99D41333f28913BA45Fc36C64eb0A88D1600F350)
- Deployed-source SHA-256: `b968431218e2b8e1e24264a13a81c9cadde7a2d321e661df50e907dbed545e13`
- ABI schema SHA-256: `cef0fd7d95e3e616bc62644966e692e28ec805bf1fa738043a0e75e71dc043a4`
- Source parity: exact `getContractCode` byte match with `contracts/noticeclock.py`, verified using GenLayerJS 1.1.8.
- The existing verified V4 deployment is preserved. No replacement deployment was made.

## Live evidence

- Historic qualification case `NCQUAL-39142055216` finalized `INCONCLUSIVE`; details and transaction hashes are in the checked-in evidence.
- Qualification Actions: [run 39142055216](https://github.com/GIFTEDLOV/driftproof/actions/runs/39142055216).
- Latest exact-main qualification CI before release preparation: [run 39161740779](https://github.com/GIFTEDLOV/noticeclock/actions/runs/39161740779).

This repository has no production app URL; it is intentionally a standalone contract submission.

## Verifier

`npm run verify:live` is read-only: it retrieves deployed bytes, checks the expected hash and ABI schema, checks receipt execution details, and reads canonical case state and history. It does not broadcast transactions. The signed browser lifecycle scripts perform writes only when explicitly guarded and never retry an uncertain broadcast.

## Reproduction

```powershell
python -m pip install -r requirements-dev.txt
python -m pytest -q
python -m genvm_linter.cli lint contracts/noticeclock.py
npm ci
npm run verify:live
```
