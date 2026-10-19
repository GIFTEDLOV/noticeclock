# Release qualification ? NoticeClock v4.0.0

**Release dossier date:** 2026-10-19
**Release state:** Source, contract, and existing live qualification evidence are preserved. Portal dossier is prepared; final Portal submission is not made.

- Contract address: [0x99D41333f28913BA45Fc36C64eb0A88D1600F350](https://explorer-studio.genlayer.com/address/0x99D41333f28913BA45Fc36C64eb0A88D1600F350).
- Deployed V4 source SHA-256: `b968431218e2b8e1e24264a13a81c9cadde7a2d321e661df50e907dbed545e13`; ABI schema SHA-256: `cef0fd7d95e3e616bc62644966e692e28ec805bf1fa738043a0e75e71dc043a4`.
- Historic case `NCQUAL-39142055216`: `FINALIZED / INCONCLUSIVE`; its source inputs are synthetic and labeled.
- Qualification workflow: [39142055216](https://github.com/GIFTEDLOV/driftproof/actions/runs/39142055216).
- Exact-main CI on the release preparation baseline: [39175259896](https://github.com/GIFTEDLOV/noticeclock/actions/runs/39175259896) passed.
- This is a standalone contract release; no production app is claimed.

The original V4 contract deployment is preserved. No contract redeployment or source-hash substitution occurred. The release-verification artifact distinguishes successful transaction finality from successful GenVM execution and canonical state.

**Submission:** prepared in [docs/SUBMISSION.md](SUBMISSION.md) and [docs/SUBMISSION_FIELDS.json](SUBMISSION_FIELDS.json); **not submitted to the Builder Portal**. No steward acceptance is claimed.

See [deployment evidence](DEPLOYMENT.md), [security review](SECURITY.md), [rejection-prevention matrix](REJECTION_PREVENTION.md), and [reviewer instructions](SUBMISSION.md).
