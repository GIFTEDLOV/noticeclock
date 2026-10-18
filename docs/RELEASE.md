# Release qualification — NoticeClock `v4.0.0-rc.1`

- Source SHA-256: `b968431218e2b8e1e24264a13a81c9cadde7a2d321e661df50e907dbed545e13`; deployed address: `0x99D41333f28913BA45Fc36C64eb0A88D1600F350`; ABI SHA-256: `cef0fd7d95e3e616bc62644966e692e28ec805bf1fa738043a0e75e71dc043a4`.
- Lifecycle case `NCQUAL-39142055216` is `FINALIZED` with verdict `INCONCLUSIVE`; all three transactions are recorded in `evidence/noticeclock-live.json`. Its source reference is synthetic and labeled.
- Run 39138804500 overall failed at NoticeClock majority disagreement; the three artifacts for other projects individually recorded PASS. NoticeClock’s later run 39142055216 passed its lifecycle and ended INCONCLUSIVE.
- Original deployment run 39138161003 concluded failure in live qualification after deployment and byte verification passed.

This standalone contract has no browser signing acceptance criterion.

**Status:** source and contract provenance are verified; this release candidate is not yet fully submission-ready. Do not enable `RELEASE_QUALIFIED` or submit a full-application readiness claim until the app acceptance criteria pass.
