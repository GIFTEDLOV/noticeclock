# Deployment and source provenance

Existing deployment: [0x99D41333f28913BA45Fc36C64eb0A88D1600F350](https://explorer-studio.genlayer.com/address/0x99D41333f28913BA45Fc36C64eb0A88D1600F350), GenLayer Studionet chain 61999, RPC `https://studio.genlayer.com/api`. GenLayerJS 1.1.8 `getContractCode` bytes match `contracts/noticeclock.py` at SHA-256 `b968431218e2b8e1e24264a13a81c9cadde7a2d321e661df50e907dbed545e13`; the deployed ABI equals the schema generated from that file at SHA-256 `cef0fd7d95e3e616bc62644966e692e28ec805bf1fa738043a0e75e71dc043a4`. No contract replacement was required.

The original workflow [39138161003](https://github.com/GIFTEDLOV/driftproof/actions/runs/39138161003) failed in its later live qualification step after deployment and actual-byte verification succeeded. Do not call that workflow fully passed. The recorded live case and sanitized transaction/state evidence are in `evidence/noticeclock-live.json`.

Not applicable: this standalone contract has no production app.

`npm run verify:live` is read-only: it hashes deployed bytes, compares ABI schemas, inspects recorded semantic/finalization receipts, reads canonical state and verifies history. It does not broadcast. Any replacement deployment requires a documented blocker, new address, byte/ABI verification, fresh lifecycle qualification, frontend binding update and exact-release CI.
