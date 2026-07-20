# Consultation response — requirement → spec field → evidence class (COM(2026)503)

**Status:** DRAFT for operator sign-off. **Companion to** the main submission
(`SUBMISSION_EU_OSS_2026-07-18.md`) and the needs annex (`ANNEX-EU-NEEDS-MAPPING.md`).
This table is the machine-checkable backbone: each EU requirement is answered by a concrete
K0NSULT artefact with an honest evidence class (`claim ≤ proof`).

> **Not sent.** Submission is via the operator to `konsultacje@cyfra.gov.pl` (deadline 21.07.2026).
> No agent sends it (No Password Custody / Human Override).

| EU need | K0NSULT answer (artefact) | Repo | Evidence class |
|---|---|---|---|
| #7 Cybersecurity tooling / findings | `finding-v1.schema.json` (vendor-neutral finding + VEX) | k0nsult-tools | DOWÓD (schema shipped) |
| #13-16 Procurement acceptance | `PATENT_GRANT.md` + SBOM as scored criterion | k0nsult-tools | DOWÓD (grant+SBOM+procurement-check.mjs 15/15) |
| #47-50 Operational guidance | `SPEC-claim-le-proof.md` + validator (11/11 tests) | k0nsult-ai-truth-core | DOWÓD (runnable) |
| #48 Dependency exposure | SBOM SHA-256 per component | k0nsult-tools | DOWÓD (k0nsult-tools SBOM = 21 komponentów; 119 w 9 repo — liczba re-derywowalna `node sbom.mjs`, hash na treści LF-znormalizowanej = świeży klon) |
| #49 Mirroring / build integrity | `verify_bundle.mjs` deterministic verifier | k0nsult-tools | GAP (hardening) |
| #6/#19 Agent interoperability | ACP + DID + skill taxonomy contract | k0nsult-uni0nai | GAP (public spec) |
| #9/#43-45 Digital identity | DID method aligned with EUID/eIDAS2 (agent layer) | k0nsult-uni0nai | GAP |
| #21 art.50 transparency | art.50 labelling toolkit + registry | k0nsult-eu-shield | DOWÓD (art50.mjs 19/19) |
| #23/#24/#32 Stewardship | this `CHARTER.md` (micro-OSPO track) | k0nsult-governance | DOWÓD (charter shipped) |
| #62 CRA art.25 attestation | signed SBOM + provenance | k0nsult-tools | GAP (needs sovereign signing) |
| #69/#76 Choice / no lock-in | Apache-2.0 forkable polyrepo | all | DOWÓD (licence) |

## Consolidated recommendations to the Commission
1. Make an OSI licence **with an explicit patent grant** + a **re-derivable SBOM** baseline eligibility for EU-funded/endorsed/procured building blocks.
2. Recognise the **micro-OSPO / solo-maintainer track** (qualifying artefact = signed SBOM, not foundation membership).
3. Fund a **sovereign EU keyless-signing** capability so maintainers under No-Password-Custody can attest (the CRA art.25 blind spot).
4. Adopt **agents-not-people, no-personal-data-on-ledger** as an eligibility criterion, enforced in code (closed subject enum + negative test).
5. Fund a **Poland/ePUAP art.50 pilot** before 2.08.2026.

## Honest limitations (claim ≤ proof)
Some modules are GAP/roadmap today; the repositories are **public (Apache-2.0) on
github.com/0n40i4** (publication is irreversible and already done). Signed releases await an
operator key. We submit the unsigned draft now and mark signing as an explicit GAP.
