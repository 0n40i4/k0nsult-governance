# Consultation response — requirement → spec field → evidence class (COM(2026)503)

**Status:** SUBMITTED. **Companion to** the main submission
(`SUBMISSION_EU_OSS_2026-07-18.md`) and the needs annex (`ANNEX-EU-NEEDS-MAPPING.md`).
This table is the machine-checkable backbone: each EU requirement is answered by a concrete
K0NSULT artefact with an honest evidence class (`claim ≤ proof`).

> **Submitted, twice, by the operator.** Both submissions were sent by a human; no agent
> sends correspondence (No Password Custody / Human Override).
>
> - **2026-07-20, 18:21 CEST** — response to the public consultation on the EU Open Source
>   Strategy (COM(2026)503), to the Polish Ministry of Digital Affairs
>   (`konsultacje@cyfra.gov.pl`), position paper attached in English.
> - **2026-07-21, 16:55 CEST** — onboarding request for the **EU Open Source Solutions
>   Catalogue** via the Interoperable Europe Portal contact form; acknowledged the same day
>   by the Portal Support Team, reference **JUS-5388**, with the EU OSS Catalogue team
>   copied.
>
> Figures quoted in those submissions are dated. Their provenance — and the corrections
> that followed an external adversarial review — are recorded in [`ERRATA.md`](./ERRATA.md).
> Read that file alongside this one.

| EU need | K0NSULT answer (artefact) | Repo | Evidence class |
|---|---|---|---|
| #7 Cybersecurity tooling / findings | `finding-v1.schema.json` (vendor-neutral finding + VEX) | k0nsult-tools | DOWÓD (schema shipped) |
| #13-16 Procurement acceptance | `PATENT_GRANT.md` + SBOM as scored criterion | k0nsult-tools | DOWÓD (grant+SBOM+procurement-check.mjs — see `TEST-COUNTERS.md`) |
| #47-50 Operational guidance | `SPEC-claim-le-proof.md` + validator | k0nsult-ai-truth-core | DOWÓD (runnable — counter in `TEST-COUNTERS.md`) |
| #48 Dependency exposure | SBOM SHA-256 per component | k0nsult-tools | DOWÓD (re-derywowalne: `node sbom.mjs --verify` na świeżym klonie; liczby patrz `ERRATA.md`, nie utrwalane w prozie) |
| #49 Mirroring / build integrity | `verify_bundle.mjs` deterministic verifier | k0nsult-tools | GAP (hardening) |
| #6/#19 Agent interoperability | ACP + DID + skill taxonomy contract | k0nsult-uni0nai | GAP (public spec) |
| #9/#43-45 Digital identity | DID method aligned with EUID/eIDAS2 (agent layer) | k0nsult-uni0nai | GAP |
| #21 art.50 transparency | art.50 labelling toolkit + registry | k0nsult-eu-shield | DOWÓD (art50.mjs — counter in `TEST-COUNTERS.md`) |
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
