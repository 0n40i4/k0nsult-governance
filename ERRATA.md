# ERRATA — provenance and corrections of published figures

We publish `claim ≤ proof` as a method. A method that cannot correct itself in public is
not a method. Everything below is recorded rather than silently amended, and every figure
is reproducible from this repository's git history.

## 2026-07-22 — component counts: provenance of the figure "119"

Material describing the commons — including the response to the public consultation on
the EU Open Source Strategy (COM(2026)503), submitted 2026-07-20 — states a total of
**119 components**.

**That figure was exact when it was computed, and covered the nine commons repositories.**
The repositories were under active development that day, and a tenth repository
(`k0nsult-chain`) was created the same afternoon. Counting the committed CycloneDX SBOMs
at pinned commits gives:

| 2026-07-20 (Europe/Warsaw) | 9 commons repos | k0nsult-chain | total |
|---|---|---|---|
| 15:00 | 109 | — | 109 |
| **16:00** | **119** | — | **119** |
| 16:30 | 119 | 7 (repository created) | 126 |
| 17:30 | 127 | 7 | 134 |
| 18:21 (submission sent) | 127 | 7 | 134 |

So the sentence enumerated ten repositories while the count described nine, taken a few
hours earlier. Since then the commons have continued to grow — including the audit
remediation work described below, which added test vectors, a mutation-testing harness
and these errata files.

**Current figures (2026-07-22):** 9 commons repositories = **153**; including
`k0nsult-chain` = **163**.

Reproduce any row:

```bash
git rev-list -1 --before="2026-07-20T16:00:00+02:00" master   # pin the commit
git show <sha>:sbom.json | node -e "…components.length"       # count at that commit
```

## 2026-07-22 — re-derivability: the property did not hold, and now does

The same material describes the component figure as independently re-derivable with the
open generator. **On the date of submission that was not true**, for two independent
defects in `sbom.mjs`, both now fixed:

1. The SBOM artefact was excluded from its own output **only** when written via `--out`.
   A committed `sbom.json` in the working tree was counted as a component of itself, so
   the total depended on the state of the clone rather than on repository content.
2. The default output path was anchored to the **script's** directory while the scanned
   root was the **current working directory**. Running `node ../k0nsult-tools/sbom.mjs`
   from another repository scanned *that* repository but wrote the result into
   `k0nsult-tools/sbom.json` — silently overwriting one repository's evidence artefact
   while leaving the scanned repository's own SBOM stale. Present since the tool's first
   commit; this is the underlying reason recomputation did not agree.

Regenerated output now matches the committed `sbom.json` in **10 of 10** repositories:

```bash
node sbom.mjs --verify     # or: node ../k0nsult-tools/sbom.mjs --verify
```

## 2026-07-22 — documented self-test counters were stale

Published as validator `11/11`, golden vectors `22/22`, DID resolver `25/25`, art.50
`19/19`. The suites grew and the prose did not follow; the counters understated actual
coverage. A documented number that disagrees with the tool is a defect in the claim
regardless of direction.

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
move. Detail: [`k0nsult-chain/ERRATA.md`](https://github.com/0n40i4/k0nsult-chain/blob/master/ERRATA.md).

## 2026-07-22 — self-tests were not evidence of guard coverage

Round 2 of the external review established, and we reproduced, that six guards in the DID
resolver's `validate()` could each be disabled outright without a single test failing —
while the suite reported 28/28 passed. Every legacy negative vector failed for the wrong
reason, so the guard it was written to exercise was never reached.

Vectors have been rebased and isolating vectors added; every guard now fails at least one
test when disabled. `k0nsult-chain` ships `mutation-test.mjs`, which neutralises each
guard in turn and asserts that exactly the test named for it fails (20/20). Reviewers are
invited to run it against us.

## Status of the external review

The commons are under external adversarial review by a partner organisation. **The review
is in progress**, not concluded: round 2 closed 2026-07-21 with findings open and a
further round is expected. Where our material describes the review in the past tense, it
should be read as ongoing. The reviewing organisation is also a commercial partner; we
state this because a review commissioned from a partner is not equivalent to an
unaffiliated audit, and readers are entitled to weigh it accordingly.

All findings and fixes are public in the git history and in issue #1 of this repository.

## Note on the defect class

The recurring failure is the same one: a number was computed once, copied into prose, and
then diverged from the artefact meant to prove it. That is precisely what `claim ≤ proof`
exists to prevent, occurring in the documents that advocate it. The remedy applied
throughout is structural rather than editorial — figures are derived from tool output at
read time, and where a figure must be stated it is stated with its date and the command
that reproduces it.
