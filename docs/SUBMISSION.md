# GenLayer submission dossier — NoticeClock

## Project name

NoticeClock

## Short description

Assess contractual notice and cure evidence against frozen terms with independent semantic consensus and an explicit inconclusive outcome.

## Detailed description

NoticeClock coordinates a three-party case in which the parties freeze a notice/cure clause, submit evidence, and nominate a distinct attestor wallet. GenLayer validators independently assess whether a breach is identified, the clause applies, and the requested cure is clear. State changes remain bounded by the frozen terms, challenge rights, and deterministic deadlines.

## Problem solved

Parties disagree whether a notice identifies an applicable breach and states a sufficiently clear cure.

## Why this requires a GenLayer Intelligent Contract

This requires semantic evaluation of natural-language clauses and evidence under independent validator execution. A deterministic workflow cannot decide whether notice text substantively satisfies a frozen contractual standard.

## Genuine semantic-consensus behavior

Inside gl.vm.run_nondet_unsafe, the leader and validators independently evaluate breach_identified, clause_applicable, requested_cure_clear, and evidence_sufficient. The response has the precise boolean schema. The contract derives READY, INVALID, or INCONCLUSIVE deterministically; disagreement cannot become approval.

## GitHub repository URL

[https://github.com/GIFTEDLOV/noticeclock](https://github.com/GIFTEDLOV/noticeclock)

## Production app URL

Not applicable: standalone Intelligent Contract; no app is claimed.

## Studionet deployment

- Chain 61999, RPC `https://studio.genlayer.com/api`
- Contract: [0x99D41333f28913BA45Fc36C64eb0A88D1600F350](https://explorer-studio.genlayer.com/address/0x99D41333f28913BA45Fc36C64eb0A88D1600F350)
- Explorer: [https://explorer-studio.genlayer.com/address/0x99D41333f28913BA45Fc36C64eb0A88D1600F350](https://explorer-studio.genlayer.com/address/0x99D41333f28913BA45Fc36C64eb0A88D1600F350)
- Verified source SHA-256: `b968431218e2b8e1e24264a13a81c9cadde7a2d321e661df50e907dbed545e13`
- ABI schema SHA-256: `cef0fd7d95e3e616bc62644966e692e28ec805bf1fa738043a0e75e71dc043a4`

## Live demonstration evidence

- Case `NCQUAL-39142055216` finalized at round 2; recorded verdict **INCONCLUSIVE**.
- First and second semantic transaction hashes and finalization hash are preserved in `evidence/noticeclock-live.json`.
- [GitHub workflow run 39142055216](https://github.com/GIFTEDLOV/driftproof/actions/runs/39142055216); exact transaction explorer links are included in the source artifact.
- Qualification source records are synthetic and labelled; this proves GenLayer behavior, not a real-world issuer’s identity or the truth of a physical record.

## Security and qualification summary

The deployed V4 source is byte-identical to the repository source; the deployed ABI matches the locally generated schema. The local regression suite covers role separation, state transitions, source hashes, strict semantic schemas, validator disagreement, prompt injection, challenge fairness, deadlines, duplicates/replay, numeric bounds, address-serialization compatibility and history integrity. Live workflow evidence records transaction status, GenVM execution and canonical readback.

This standalone contract has no browser-signing acceptance criterion.

## Instructions for reviewers

1. Inspect `contracts/noticeclock.py` and verify its hash and ABI using `npm run verify:live`.
2. Run `python -m pytest -q`, `python -m genvm_linter.cli lint contracts/noticeclock.py`, `npm ci`, and `npm run verify:live`.
3. Read `evidence/noticeclock-live.json`; preserve the terminal verdict shown above.
4. For apps, open the production URL read-only; wallet signing is deliberately disabled until its real signed-browser qualification completes.

## Known limitations and external trust assumptions

An attestor signature proves control of the agreed wallet, not real-world issuer identity or notice authenticity. The contract does not give legal advice, authenticate physical documents, or transfer funds. Test evidence was synthetic and explicitly labeled.

Public case creation has no global lifetime cap. Pagination limits each page to 100 records, but total storage and the legacy `get_case_ids()` view can grow. Semantic execution depends on available non-deterministic model services and validator execution; disagreement is not approval. Invoice/minute outputs do not settle assets.
