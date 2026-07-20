# Detailed review brief — six areas (K0NSULT open commons)

Companion to [`REVIEW-INVITATION.md`](./REVIEW-INVITATION.md). This is the **detailed
scope** for a reviewer who wants to go deep, structured as **six areas**.

Reply format: `severity (HIGH/MED/LOW) · repo/file:line · problem · recommendation`.
**Proof or GAP — no narrative.** Open an issue/PR on the relevant repo, or send a list.

## Read this first — we already audited ourselves (4 rounds)

The commons went through **four rounds of internal adversarial audit** (5-judge and
20-specialist panels, each prompted to *refute*). We fixed a lot — path traversal, DoS,
ReDoS, PII in git history — and we documented the **open, unfixed limitations honestly** in
`KNOWN-LIMITATIONS.md` (in `k0nsult-uni0nai`, `k0nsult-tools`, `k0nsult-eu-shield`).

**Honest posture:** the validators are **REFERENCE / EXPERIMENTAL**, not production guards.

**So your job is NOT to repeat our audit — it is to bring an outside-the-ecosystem
perspective.** Before you start, read:
- `KNOWN-LIMITATIONS.md` — what we already know is leaky.
- the audit reports (available on request) — what our own panels found.

**Repositories (public, `github.com/0n40i4/`):** `k0nsult-tools`, `k0nsult-ai-truth-core`,
`k0nsult-uni0nai`, `k0nsult-eu-shield`, `k0nsult-country-pl`, `k0nsult-country-template`,
`k0nsult-global-cm`, `k0nsult-global-ar`, `k0nsult-governance`. Clone + `node <tool> --selftest`.

## The six areas

### 1. Hidden-engine invariant (most important)
Does any of the 9 repos leak `k0nsult.cloud` engine code, logic, data or credentials? Is the
`/api/*` boundary acceptable or over-disclosing? `k0nsult-uni0nai` is contract-only (ACP +
taxonomy + DID schemas) — is that contract self-sufficient for interop without the engine?

### 2. Are our KNOWN-LIMITATIONS honest AND complete?
The key question: do the openly listed limitations (regex-PII leaks via arrays / unicode /
camelCase / JSON-number / PGP-vs-PEM; validator drift; self-tests-as-theatre) tell the **whole
truth** — or is there a class of problem we did not even admit in the limitations file? Is there
an overclaim that survived all four rounds?

### 3. Is the "reference / experimental" stance right — or dangerous?
We decided **not** to chase "zero findings" on regex-based PII validators (a tar pit) and instead
label them reference + document limitations. **Is that a defensible, honest posture toward a
regulator / adopter — or is there a real risk someone relies on them as a production guard despite
the warning?** What would you change in the framing?

### 4. Licensing + SBOM + legal
Is the scoped Apache-2.0 `NOTICE` correct per repo? Is attribution ("K0NSULT sp. z o.o.,
KRS 0001239441, NIP 5253089872") consistent across all 9? Are the SBOMs (`sbom.json`, SHA-256)
correct and scoped to the right repo (there was a bug where they described the whole monorepo —
fixed)? Licensing / attribution risks.

### 5. Offer to the Commission (`SUBMISSION_EU_OSS_2026-07-18.md` — provided separately)
Do the `[PROOF]` claims hold technically after our honest reframe? Which should move to `[GAP]`?
Do the crosswalks (EUID/eIDAS2, ESCO) labelled NARRATIVE smuggle assumptions in as facts?

### 6. Outside-the-ecosystem perspective (what our own panels cannot give)
Legal, reputational, competitive / IP risks we cannot see from inside. Maintainer-fit: which
repos are ready "as is" for promotion / partnerships and which are not. Does publishing reference
tools *with* stated limitations help or hurt K0NSULT's position? What is the single biggest risk
we have not addressed?

## Out of scope this round
`k0nsult-chain` (not published — behind an S1 / TrustNet wind-down decision); the `k0nsult.cloud`
engine and the `ipIII` product (private, commercial).
