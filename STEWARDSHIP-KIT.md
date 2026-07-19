# K0NSULT stewardship kit — bootstrapping an open commons without a foundation

**Version:** 1.0 · **License:** Apache-2.0 · **Status:** reference kit (adopt / fork freely).
**Companion to** `CHARTER.md` (the charter this kit operationalises) and
`CONSULTATION-RESPONSE-DRAFT.md` (COM(2026)503 needs #23, #24, #25-28, #32).

A step-by-step kit a **single SME or solo maintainer** can follow to stand up a credible
open commons — one that a public body could endorse, fund, or procure — **before** founding
any legal foundation. The qualifying artefact is a re-derivable, hash-anchored release, not
foundation membership.

> **Doctrine (invariant).** `claim ≤ proof` · engine hidden (zero engine code in any commons
> repo) · agents-not-people (zero scoring of natural persons, zero PII) · reputation soulbound
> (not crypto) · **Human Override Always** · **No Password Custody**.
> Evidence classes used throughout: **DOWÓD** (verifiable link/hash), **GAP** (declared
> roadmap), **NARRACJA** (framing — not a violation, not a proof).

---

## 0. How to use this kit

1. Run the **eligibility checklist** (§1) against your repo — five artefacts, each with a
   machine-checkable pass condition. A repo either passes or it does not; there is no partial
   credit for governance narrative without the artefacts.
2. Adopt the **charter template** (§2) by forking `CHARTER.md` and filling the four bracketed
   fields. Nothing else needs editing to inherit the doctrine.
3. Wire the **decision matrix** (§3) into your process: it names, per action, who proposes and
   whose sign-off is required, and marks the irreversible acts that are **human-gated**.
4. When you outgrow solo stewardship, follow the **micro-OSPO → foundation path** (§4). It is
   designed so graduation needs **no relicensing** and breaks no downstream fork.

This kit is **NARRACJA** (guidance/method). The artefacts it tells you to ship are DOWÓD; the
capabilities it says you still lack are declared GAP. Do not let the kit's confident tone be
read as proof that any given repo has passed — that is what §1 measures.

---

## 1. Eligibility checklist — what makes a module "commons-ready"

A module qualifies for the commons — and, we propose, for EU endorsement / funding / procurement —
when **all five** artefacts are present and each pass condition holds. Ship the five; skip none.

| # | Artefact | File | Pass condition (machine-checkable) | Evidence when present |
|---|---|---|---|---|
| 1 | **OSI licence** | `LICENSE` | Byte-identical to an OSI-approved text (Apache-2.0 recommended for its patent grant). No custom clauses. | DOWÓD |
| 2 | **Explicit patent grant** | `PATENT_GRANT.md` (or Apache-2.0 §3) | A written, irrevocable patent licence from contributors, with the defensive-termination scope stated. | DOWÓD |
| 3 | **Hash-anchored SBOM** | `sbom.json` | Lists every shipped file with a **SHA-256**; a third party can re-derive every hash from the tree and get an exact match. | DOWÓD |
| 4 | **Scoped NOTICE** | `NOTICE` | Declares the **commons ↔ engine boundary**: what is open here, and the explicit statement that no engine code / no PII ships. | DOWÓD (boundary manifest) |
| 5 | **Evidence-class README** | `README.md` | States, per claim or per contents row, its evidence class (DOWÓD / GAP / NARRACJA). No unqualified superlatives. | DOWÓD |

### 1.1 Qualification gate (the honest reading)
- **Present ≠ passing.** An SBOM whose hashes do not re-derive is a *failed* SBOM (GAP), not a
  DOWÓD. Verify before you claim.
- **Signing is a separate, later gate.** A signed release (Sigstore/keyless or a sovereign key)
  strengthens artefact #3 but is **not** required to qualify. Under **No Password Custody** the
  maintainer's tooling never generates or holds a key; signing is an operator-gated act. Absence
  of a signature is declared **GAP**, never hidden.
- **One negative test per invariant.** For agents-not-people, ship a test proving the subject
  enum rejects a natural-person type. A doctrine with no falsifying test is NARRACJA.

### 1.2 Copy-paste self-check
```
[ ] LICENSE        — OSI text, byte-identical, no added clauses
[ ] PATENT_GRANT   — irrevocable grant + defensive-termination scope stated
[ ] sbom.json      — every shipped file, SHA-256, third-party re-derivable
[ ] NOTICE         — commons/engine boundary + "no engine code, no PII"
[ ] README         — evidence class on every claim; no unqualified superlatives
[ ] negative test  — at least one falsifying test per doctrinal invariant
[ ] signing status — signed (DOWÓD) OR explicitly declared GAP (never silent)
```
A repo that ticks the first five boxes is **commons-ready**. The last two raise it from
"ready" to "attestable".

---

## 2. Governance charter template (fork this)

`CHARTER.md` is written to be **forked verbatim** — the doctrine (§2 of the charter) is meant to
be inherited unchanged. To adopt it, copy `CHARTER.md` into your repo and fill only the four
bracketed fields below; edit nothing else unless you are deliberately diverging from the commons.

```markdown
# [PROJECT] open-commons governance charter

**Version:** 1.0 · **License:** Apache-2.0 · **Status:** reference charter (adopt/fork freely).

## 1. Scope boundary (engine hidden, commons open)
- Open commons = the public repositories: surfaces, contracts, schemas, tooling, docs.
- Engine = the private orchestration runtime ([ENGINE-HOST]). It is never merged into a
  commons repo; commons surfaces reference it only across a documented /api/* boundary.
- Each repo declares its side of the boundary in NOTICE.

## 2. Doctrine (invariant — inherit unchanged)
1. claim ≤ proof — every published claim is DOWÓD | GAP | NARRACJA.
2. agents-not-people — only software agents are identified/scored; zero scoring of persons.
3. Reputation is soulbound — non-transferable, no price/market; not a coin.
4. Human Override Always — irreversible acts are human-gated.
5. No Password Custody — no secret or signing key is generated, stored, or committed by tooling.

## 3. Eligibility artefacts
LICENSE (OSI + patent grant) · PATENT_GRANT.md · sbom.json (SHA-256) · scoped NOTICE ·
evidence-class README. (See STEWARDSHIP-KIT.md §1.)

## 4. Decision rights
[MAINTAINER] proposes; irreversible acts require [OPERATOR]'s explicit sign-off.
Graduation to a neutral foundation is permitted without relicensing (Apache-2.0).

## 5. Fork & exit
Every commons repo is forkable under Apache-2.0. Charter + per-repo SBOM + patent grant
constitute a documented, no-lock-in exit path.
```

**Bracketed fields to fill:** `[PROJECT]`, `[ENGINE-HOST]`, `[MAINTAINER]`, `[OPERATOR]`.
If `[MAINTAINER]` and `[OPERATOR]` are the same natural person (the solo case), the charter
still holds: the person wears two hats and the human-gate in §3 of the matrix below is a
deliberate self-checkpoint, not a hierarchy.

---

## 3. Decision matrix — who approves what, what is human-gated

Two roles minimum: **Maintainer** (may be an agent or a person) proposes and prepares;
**Operator** (always a natural person) signs off on anything irreversible. The **Human-gate**
column is the load-bearing part of this kit — it enumerates the acts that tooling must **never**
perform autonomously.

| Action | Maintainer | Operator sign-off | Human-gated? | Reversible? | Evidence produced |
|---|---|---|---|---|---|
| Draft / edit a spec, schema, doc | ✅ proposes | not required | no | yes (git) | DOWÓD (commit) |
| Add / update `sbom.json` hashes | ✅ prepares | not required | no | yes | DOWÓD (re-derivable) |
| Merge to a private/local branch | ✅ | not required | no | yes | DOWÓD (commit) |
| **Publish a repo publicly (first time)** | prepares | ✅ **required** | **YES** | **no** | NARRACJA→DOWÓD once live |
| **Sign / release an artefact** | prepares | ✅ **required** | **YES** | **no** (Rekor is append-only) | DOWÓD (signature) |
| **Submit to an external body / regulator** | drafts | ✅ **required** | **YES** | **no** | DOWÓD (receipt) |
| **Generate / store a signing key** | ❌ **forbidden** | operator acts personally | **YES** | n/a | — (No Password Custody) |
| **Push to a shared/production remote** | prepares | ✅ **required** | **YES** | hard to undo | DOWÓD (deploy log) |
| Record maintainer reputation signal | ✅ | not required | no | append-only | DOWÓD (soulbound entry) |
| **Pay out / transfer any reputation value** | ❌ **forbidden** | — | — | — | — (reputation is not a coin) |
| Relicense a commons repo | proposes | ✅ **required** | **YES** | no | DOWÓD (LICENSE diff) |

**Reading the matrix.**
- Everything reversible and internal, the Maintainer may do alone — this keeps a solo commons fast.
- Every **irreversible or externally-visible** act is human-gated: publication, signing,
  submission, production push, relicensing. Tooling stops and waits for the Operator.
- Two rows are **forbidden outright**, not merely gated: tooling generating/holding a signing key
  (No Password Custody) and any payout of reputation value (reputation soulbound, not crypto).
- Where Maintainer = Operator (solo case), the human-gate is still real: it is the point at which
  the person must consciously accept an irreversible act, on the record.

---

## 4. Growth path — micro-OSPO → foundation, without relicensing

A common blocker: "you cannot be taken seriously until a foundation owns the code." This kit
rejects that as a **precondition**. The path below lets an SME earn credibility incrementally and
transfer to a neutral home **only when it adds value** — never as an entry toll.

### Stage 0 — Solo maintainer (day one)
- One person is both Maintainer and Operator. Ship the §1 five artefacts.
- Qualifying signal: a **re-derivable SBOM**, not headcount, not incorporation.
- Human-gate (§3) is a self-checkpoint. This stage is already **commons-ready** (DOWÓD).

### Stage 1 — Micro-OSPO (the proposed EU-recognised track)
- Still one legal entity (the SME), but stewardship is **codified**: this kit + charter +
  per-repo SBOM + a public decision matrix.
- Add a second reviewer where possible (an agent reviewer counts for preparation; a second
  natural person strengthens the human-gate for irreversible acts).
- Optional: signed releases move the signing row from **GAP** to **DOWÓD** — this is where a
  *sovereign EU keyless-signing* capability (CRA art.25 blind spot) would unblock maintainers
  bound by No Password Custody. **Declared GAP** until such a facility exists.
- Externally attestable: a procurer can score the SBOM + patent grant as acceptance criteria
  today, without any foundation existing.

### Stage 2 — Neutral foundation (only if/when it helps)
- Transfer stewardship to a neutral European host (Eclipse-Europe / NGI-style / a national
  digital-commons body).
- **No relicensing required.** Apache-2.0 already permits redistribution and downstream forks;
  a new steward inherits the licence, the patent grant, and the SBOM baseline unchanged.
- **No downstream break.** Every existing fork remains valid under the same licence; contributors'
  patent grants persist. The foundation gains governance neutrality and continuity; users lose
  nothing.
- Trigger to graduate (not before): multiple independent contributors, a need for neutral IP
  custody, or a funder requiring foundation-held assets. Absent a trigger, Stage 1 is a
  legitimate terminal state — not an unfinished one.

### Why this ordering matters (recommendation to the Commission)
Recognising Stage 1 as a **fundable, procurable track** — qualifying artefact = signed SBOM, not
foundation membership — lets bootstrapped SMEs contribute reusable European building blocks
without the foundation-first chicken-and-egg. Charter §4 and this §4 are the copyable mechanism.

---

## 5. What this kit does **not** do (claim ≤ proof)

- It does **not** ship or describe engine code. The engine (`k0nsult.cloud`) is out of scope of
  every commons repo by construction (NARRACJA here; enforced by the NOTICE boundary, DOWÓD).
- It does **not** provide a sovereign signing capability. Attestation under No Password Custody
  is an open **GAP** pending an EU keyless-signing facility (§4, Stage 1).
- It does **not** score, rank, or profile any natural person. Reputation applies to software
  agents only, is soulbound, and is never a payout (doctrine invariants #2, #3).
- It does **not** authorise any agent to publish, sign, submit, push, or relicense. Those are
  human-gated (§3). This document being confident is NARRACJA — the human-gate is the DOWÓD.
