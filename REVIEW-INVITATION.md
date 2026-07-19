# Open invitation — independent audit of the K0NSULT open commons

We invite independent, **adversarial** review of the K0NSULT open-source commons — the
building blocks published as our contribution to the EU Open Source Strategy consultation
(COM(2026)503). Model: **hidden engine, open commons** — the proprietary orchestration
engine stays private; contracts, schemas, tools and transparency surfaces are open (Apache-2.0).

## Repositories (public)
`k0nsult-tools` · `k0nsult-ai-truth-core` · `k0nsult-uni0nai` · `k0nsult-eu-shield`
`k0nsult-country-pl` · `k0nsult-country-template` · `k0nsult-global-cm` · `k0nsult-global-ar` · `k0nsult-governance`

All under `github.com/0n40i4/`.

## Try to break it (evidence-first)
Every tool is zero-dependency (Node ≥18) and ships a self-test. Run them and try to falsify:
```bash
git clone https://github.com/0n40i4/k0nsult-ai-truth-core && cd k0nsult-ai-truth-core
node schema/validate.mjs --selftest      # claim<=proof validator (7/7)

git clone https://github.com/0n40i4/k0nsult-uni0nai && cd k0nsult-uni0nai
node conformance.mjs --selftest          # 19/19 golden-vectors
node did-resolver.mjs --selftest         # 22/22

# k0nsult-tools:   node sbom-expose.mjs|dep-provenance.mjs|procurement-check.mjs|attest-verify.mjs --selftest
# k0nsult-eu-shield: node art50/art50.mjs --selftest ; node gen-publiccode.mjs --selftest ; node a11y-check.mjs --selftest
```
Nine tools; all self-tests pass for us. We want them independently re-run and challenged.

## What we most want reviewed
1. **Hidden-engine invariant** — does any repo leak engine code, data, or credentials? Surfaces call an `/api/*` boundary; is that boundary acceptable or over-disclosing?
2. **Are the negative tests real, not theatre?** Especially: PII rejection (`art50.mjs`), no scoring of a person's nationality (`dep-provenance.mjs`), `subject_type=agent` only + no PID + non-transferable reputation (`conformance.mjs`).
3. **agents-not-people in code, not just docs** — try to smuggle a PII record or `subject_type='human'` past the guards. (We already found and fixed a P0↔P1 inconsistency and a synthetic-PESEL test value → look for more.)
4. **Licensing + SBOM** — is the scoped `NOTICE` accurate per repo? Are the SBOM hashes correct and complete?
5. **Claim discipline** — is anything labelled as fact that is really roadmap? Flag it.

## Out of scope this round
- Any component not present in these public repos.
- The proprietary engine and commercial modules — private by design.

## How to report
`severity (HIGH/MED/LOW) · repo/file:line · problem · recommendation`. Proof or GAP — no narrative.
Open an issue on the relevant repo, or a PR. Thank you.
