# K0NSULT open-commons governance charter

**Version:** 1.0 · **License:** Apache-2.0 · **Status:** reference charter (adopt/fork freely).

A minimal, machine-checkable governance charter separating a **proprietary engine** from
an **open commons**, so a single SME can steward reusable modules credibly without first
founding a full legal foundation. Offered to COM(2026)503 as a copyable stewardship kit
(needs #23, #24, #25-28, #32).

## 1. Scope boundary (engine hidden, commons open)
- **Open commons** = the public repositories: surfaces, contracts, schemas, tooling, docs.
- **Engine** = the private orchestration runtime (`k0nsult.cloud`). It is **never** merged
  into a commons repo. Commons surfaces may reference an engine only across a documented
  `/api/*` integration boundary.
- Each repo declares its side of the boundary in `NOTICE` (scope block) — this is the
  testable commons-vs-engine manifest.

## 2. Doctrine (invariant across every commons repo)
1. `claim ≤ proof` — every published claim is DOWÓD | GAP | NARRACJA (see `k0nsult-ai-truth-core`).
2. **agents-not-people** — only software agents are identified/scored; **zero** scoring of natural persons.
3. **Reputation is soulbound** — non-transferable, no turnover/price/market; **not** a coin.
4. **Human Override Always** — irreversible acts (publication, external submission, signing) are human-gated.
5. **No Password Custody** — no secret or signing key is ever generated, stored, or committed by tooling.

## 3. Eligibility artefacts (what makes a module "commons-ready")
A module qualifies for the commons — and, we propose, for EU endorsement/funding — when it ships:
- an **OSI licence with an explicit patent grant** (`LICENSE` = Apache-2.0 + `PATENT_GRANT.md`);
- a **hash-anchored SBOM** (`sbom.json`, SHA-256 per file), re-derivable by a third party;
- a scoped **`NOTICE`** declaring the commons/engine boundary;
- a **`README`** stating evidence classes for its claims.
This is the **micro-OSPO / solo-maintainer track**: the qualifying artefact is a signed SBOM,
**not** foundation membership (#32, #33).

## 4. Decision rights
- Maintainer proposes; irreversible acts require the human operator's explicit sign-off.
- Reputation of maintainers (if recorded) is a governance-legitimacy signal — soulbound, never a payout.
- Graduation path: an SME-stewarded commons can later transfer to a neutral European foundation
  (Eclipse-Europe / NGI-style) **without relicensing** — Apache-2.0 permits it (#25-28).

## 5. Fork & exit
Every commons repo is forkable under Apache-2.0. A documented fork/exit path (this charter +
per-repo SBOM + patent grant) is itself an eligibility criterion — no adopter is locked in.
