# ERRATA — corrections to published figures

This file exists because we publish `claim ≤ proof` as a method. A method that cannot
correct itself in public is not a method. Every entry below was found by adversarial
review and is recorded here rather than silently edited away.

## 2026-07-22 — SBOM component counts were not re-derivable

**Published claim (CONSULTATION-RESPONSE-DRAFT.md, and the consultation submission
built from it):** *"k0nsult-tools SBOM = 21 komponentów; 119 w 9 repo — liczba
re-derywowalna `node sbom.mjs`"*.

**Status: WRONG on both figures, and the "re-derivable" property did not hold.**

Root cause: `sbom.mjs` excluded the SBOM artefact from its own output **only** when
written via `--out`. A committed `sbom.json` present in a working tree was therefore
counted as a component of itself, so the number depended on the state of the clone
rather than on the repository content. Three independent recomputes produced three
different totals — including two by external reviewers.

Corrected, after making the generator deterministic (`*sbom.json` is now excluded
unconditionally):

| repo | components |
|---|---|
| k0nsult-tools | 23 |
| k0nsult-ai-truth-core | 21 |
| k0nsult-eu-shield | 25 |
| k0nsult-uni0nai | 17 |
| k0nsult-country-pl | 15 |
| k0nsult-governance | 14 |
| k0nsult-country-template | 14 |
| k0nsult-global-ar | 11 |
| k0nsult-global-cm | 10 |
| **total, 9 commons repos** | **150** |
| k0nsult-chain (added after the submission) | 9 |
| **total, 10 repos** | **159** |

Verification, on a fresh clone of any repo:

```bash
node sbom.mjs --verify     # recompute vs committed sbom.json
```

Regenerated output now matches the committed `sbom.json` in 10 of 10 repositories.
The figure is re-derivable as of this entry; it was not when first published.

## 2026-07-22 — documented self-test counters had gone stale

**Published claims:** validator `11/11`, golden vectors `22/22`, DID resolver `25/25`,
art.50 `19/19`.

**Status: WRONG.** The suites grew; the prose did not. The counters understated actual
coverage, but a documented number that disagrees with the tool is a defect in the claim
regardless of direction.

Remedy: hard-coded counters have been removed from `REVIEW-INVITATION.md` and from the
consultation response table. Each `--selftest` prints its own count and that output is
authoritative. Where a count is stated at all, it is stated with the command that
produces it.

## Note on the underlying defect class

Both entries are the same failure: a number was copied into prose once and then
diverged from the artefact that was supposed to prove it. That is precisely the failure
mode `claim ≤ proof` exists to prevent, occurring in the documents that advocate it. It
is recorded here in full rather than corrected quietly.
