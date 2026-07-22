# ERRATA — corrections to published figures

We publish `claim ≤ proof` as a method. A method that cannot correct itself in public is
not a method. Findings below came from external adversarial review and are recorded here
rather than silently amended.

## 2026-07-22 — SBOM component counts are restated, and made re-derivable

**Previous statement:** the commons comprise *"119 components"*, described as
independently re-derivable with the open generator.

**Restated.** The figure was stale when published and did not match the repositories at
the time. Measured from the committed SBOMs, the totals are:

| as of | 10 repositories |
|---|---|
| 2026-07-20 (date of the consultation submission) | 134 |
| 2026-07-22 (after the fixes described below) | 163 |

The 9 commons repositories excluding the trust layer total **153** as of 2026-07-22.

**Root cause — two independent defects in the generator, both now fixed:**

1. The SBOM artefact was excluded from its own output *only* when written via `--out`. A
   committed `sbom.json` in the working tree was counted as a component of itself, so the
   total depended on the state of the clone rather than on repository content.
2. More seriously, the default output path was anchored to the **script's** directory
   while the scanned root was the **current working directory**. Running
   `node ../k0nsult-tools/sbom.mjs` from another repository scanned *that* repository but
   wrote the result into `k0nsult-tools/sbom.json` — silently overwriting one
   repository's evidence artefact while leaving the scanned repository's own SBOM stale.
   This defect was present from the first commit of the tool and is the underlying reason
   the counts were not reproducible.

**Current state:** regenerated output matches the committed `sbom.json` in **10 of 10**
repositories. Verify on a fresh clone of any of them:

```bash
node sbom.mjs --verify     # or: node ../k0nsult-tools/sbom.mjs --verify
```

## 2026-07-22 — documented self-test counters were stale

**Previous statements:** validator `11/11`, golden vectors `22/22`, DID resolver `25/25`,
art.50 `19/19`.

**Restated.** The suites grew and the prose did not follow. The counters understated
actual coverage, but a documented number that disagrees with the tool is a defect in the
claim regardless of direction.

Hard-coded counters have been removed from `REVIEW-INVITATION.md` and from the
consultation response table. Each `--selftest` prints its own count and that output is
authoritative.

## 2026-07-22 — "soulbound / non-transferable" restated as "no transfer primitive"

The trust layer was described as carrying *soulbound (non-transferable)* reputation.
Adversarial review showed the guard rejected transfer-shaped **field names** while the
transfer **effect** remained reachable. Reputation is not a conserved quantity, so no
per-event guard can prohibit it.

What is enforceable is now enforced; what is not is stated plainly. Read the term as
*"there is no transfer operation in the data model"*, not as proof that value cannot
move. Full detail: [`k0nsult-chain/ERRATA.md`](https://github.com/0n40i4/k0nsult-chain/blob/master/ERRATA.md).

## Status of the external review

The commons are under external adversarial review by a partner organisation. **The review
is in progress**, not concluded: round 2 closed on 2026-07-21 with findings open and a
further round is expected. Where our material describes the review in the past tense, it
should be read as ongoing. The reviewing organisation is also a commercial partner; we
state this because a review commissioned from a partner is not equivalent to an
unaffiliated audit, and readers are entitled to weigh it accordingly.

All findings and fixes are public in the git history and in the issue tracker of
`k0nsult-governance`.

## Note on the defect class

Each entry above is the same failure: a number was copied into prose once and then
diverged from the artefact meant to prove it. That is precisely the failure mode
`claim ≤ proof` exists to prevent, occurring in the documents that advocate it. The
remedy applied throughout is structural rather than editorial — figures are now derived
from tool output at read time instead of being restated in text.
