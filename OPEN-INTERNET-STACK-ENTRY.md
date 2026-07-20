# Open-Internet-Stack — catalogue entry (K0NSULT open-commons polyrepo)

**Version:** 1.0 · **License of this entry:** Apache-2.0 · **Status:** catalogue submission,
ready for `code.europa.eu` / an EU open-source building-block catalogue.

Answers COM(2026)503 needs **#15** (discoverable EU catalogue of reusable building blocks) and
**#38-39** (a machine-readable, per-repo metadata record so a public administration can find,
assess, and adopt a module without contacting the maintainer first).

> **Doctrine (invariant):** `claim ≤ proof` · engine hidden · agents-not-people ·
> reputation soulbound (not crypto) · Human Override Always · No Password Custody.
> This entry lists **only the open commons**. The proprietary `k0nsult.cloud` engine is **not**
> a building block, is **not** catalogued, and is never part of any repo below.

## 1. What this entry is
A single directory record for a **polyrepo** — a set of independently forkable Apache-2.0
repositories that together form an evidence-first "open internet stack" for AI-Act-era public
administration. Each repo is self-describing: it carries its own OSI licence with an explicit
patent grant, a hash-anchored SBOM, a scoped `NOTICE` (commons/engine boundary), and a README
that states the evidence class of each of its claims.

The catalogue does not need to trust a narrative. Every row is re-derivable by a third party:
clone the repo, recompute the SBOM hashes (computed over LF-normalized content; a fresh clone with
`.gitattributes eol=lf` reproduces an exact match), and run the shipped tool self-tests.

## 2. Catalogue metadata (repo-level)
Each commons repo publishes the following fields (proposed minimal record for #38-39):

| Field | Source of truth in the repo | Re-derivable? |
|---|---|---|
| `repo` | git remote / folder name | yes |
| `license` | `LICENSE` (SPDX id) | yes |
| `patent_grant` | Apache-2.0 §3 or `PATENT_GRANT.md` | yes |
| `sbom` | `sbom.json` (SHA-256 per file) | yes — recompute hashes |
| `notice_scope` | `NOTICE` scope block (OPEN vs engine boundary) | yes |
| `evidence_class` | README claims table (DOWÓD \| GAP \| NARRACJA) | partly — `k0nsult-ai-truth-core` ships a `claims.json` to run through `validate.mjs`; other repos evidence their claims via SBOM + tool self-tests |
| `contains_pii` | asserted `false` for every commons repo | yes — grep / schema enum |
| `contains_engine` | asserted `false` for every commons repo | yes — NOTICE + review |

## 3. The polyrepo (per-repo entry)

| Repo | Building block | License + patent | SBOM | Evidence class | PII | Engine |
|---|---|---|---|---|---|---|
| `k0nsult-ai-truth-core` | `claim ≤ proof` spec + `validate.mjs` + claims sample | Apache-2.0 §3 | hash-anchored | **DOWÓD** (validator runnable, tests pass) | none | none |
| `k0nsult-tools` | vendor-neutral finding+VEX schema, SBOM profile, procurement-acceptance check, `PATENT_GRANT` | Apache-2.0 + `PATENT_GRANT.md` | hash-anchored (per-component) | DOWÓD (schemas shipped) / GAP (scoring tool) | none | none |
| `k0nsult-uni0nai` | agent-interop contract: ACP + DID-agent schema + golden vectors | Apache-2.0 §3 | hash-anchored | GAP (public spec, roadmap) | none | none |
| `k0nsult-eu-shield` | AI-Act art.50 labelling spec + OSOR mapping + pilot | Apache-2.0 §3 | hash-anchored | GAP (extractable repo) | none | none |
| `k0nsult-governance` | governance charter, stewardship kit, consultation-response backbone | Apache-2.0 §3 | hash-anchored | DOWÓD (charter shipped) | none | none |

*(Rows carry the same honest evidence class the module's own README asserts — the catalogue
never upgrades a GAP to a DOWÓD. Publication of each repo is operator-gated and may lag this
entry; a repo not yet public is marked GAP until its remote resolves. As of 2026-07 all nine commons repos are public.)*

**Scope note (repo count).** The table above lists the **5 core open-internet-stack repos**. The full K0NSULT open-commons polyrepo is **9 repos**: the 5 above **plus** the national-layer pair (`k0nsult-country-pl` reference + `k0nsult-country-template` scaffold) and the two NON-EU global tracks (`k0nsult-global-cm`, `k0nsult-global-ar`), which are catalogued separately and — per the EU/global separation — carry their own funding, not EU-earmarked resources. Where other documents cite "9 repos", they mean this full polyrepo; the 5-row table is the EU-facing core.

## 4. Adoption path (no maintainer contact required)
1. **Find** — one catalogue row per repo, machine-readable fields (Section 2).
2. **Assess** — clone, recompute `sbom.json` hashes, run the repo's validator, read the evidence
   classes. No trust in the maintainer is required at this step.
3. **Adopt** — Apache-2.0 permits fork, integration, and relicence-free downstream use.
4. **Graduate** — an SME-stewarded repo can later transfer to a neutral European foundation
   (Eclipse-Europe / NGI-style) **without relicensing** (charter §4, needs #25-28).

## 5. What the catalogue must NOT infer
- No repo here is a network, ledger, token, or coin. Reputation, where recorded, is soulbound.
- No repo scores natural persons; subjects are software agents (closed subject enum + negative test).
- The engine is out of scope by construction — do not catalogue `k0nsult.cloud`.

## 6. Eligibility claim to the catalogue (claim ≤ proof)
K0NSULT asserts each commons repo meets the **micro-OSPO / solo-maintainer eligibility bar**
(charter §3): OSI licence + explicit patent grant + re-derivable SBOM + scoped NOTICE + evidence-classed
README. The qualifying artefact is the **signed SBOM, not foundation membership**. Signing under a
sovereign EU keyless capability is an explicit **GAP** (No Password Custody — the maintainer holds no key
today); the unsigned, hash-anchored SBOM is shipped now and re-derivable.
