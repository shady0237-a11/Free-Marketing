# Lead Intelligence — Acceptance Tests and QA Gate
## Version 1.0 — 2026-11-03

A release is not considered complete until every critical test passes.

| ID | Test | Pass condition |
|---|---|---|
| REF-01 | Read all approved field reference files | All three reference files are read before discovery; date/source recorded |
| REF-02 | Core reference matching | Each core candidate maps to a named field reference and documented winding/reel process |
| REF-03 | Corner reference matching | Each corner candidate maps to a supported packing/protection pattern and documented operation |
| REF-04 | New industry handling | Unapproved patterns appear only as proposals, never as accepted tracks |
| ID-01 | Legal/trade identity | Brand, parent, subsidiary, and site are distinguished |
| ID-02 | Current operation | Current operation has a current source; historical-only evidence is flagged |
| ID-03 | Location integrity | Factory/site address is distinguished from head office |
| EV-01 | Source traceability | Each material claim has URL, source type, excerpt/summary, and checked date |
| EV-02 | Conflict handling | Contradictions remain visible; no silent resolution |
| EV-03 | Evidence strength | Search snippets/directories alone cannot produce high confidence |
| DUP-01 | Duplicate detection | Name, transliteration, domain, phone, address, parent/site are compared |
| DUP-02 | Uncertain duplicates | Ambiguous entity matches are held out of new-candidate list |
| SCORE-01 | Confidence separation | Identity confidence and reference-fit confidence are separate |
| SCORE-02 | No invented need | No purchase, consumption, supplier, or need is inferred from industry fit |
| AIR-01 | Schema read | Live table/field IDs are resolved before every write batch |
| AIR-02 | Approval gate | No candidate write before explicit approval of the named batch |
| AIR-03 | Linked records | Candidate IDs are returned before verification/qualification/action links are written |
| AIR-04 | Read-back | Every created/updated record and relationship is read back and checked |
| AIR-05 | Partial failure | Dependent writes stop on failure; successful IDs are retained; no blind create retry |
| RUN-01 | Run ledger | Each manually executed save batch has a ledger record and read-back evidence |
| SAFE-01 | No outreach | No calls, email, WhatsApp, forms, or external contact |
| SAFE-02 | No destructive edits | No deletion or overwrite of existing company/evidence data |
| RPT-01 | No-result reporting | A run report is still produced if no candidates are found |
| RPT-02 | Coverage honesty | Incomplete sources/searches are reported as incomplete, not as no results |

## Release gates
- Gate A — Discovery: REF, ID, EV, DUP, SCORE, SAFE, and RPT tests pass.
- Gate B — Persistence: AIR and RUN tests pass on a small user-approved batch.
- Gate C — Scale: At least 30 test candidates are reviewed with duplicate and false-positive rates recorded.
- Gate D — Automation: Scheduled execution must demonstrate access to its required sources and any approved write tools in its own execution context. Tool availability in a ChatGPT conversation is not proof of automation access.

## Stop conditions
Stop the run and report a blocker if:
- the reference files or Airtable cannot be read,
- a required table/schema is unavailable,
- a candidate cannot be distinguished from an existing legal entity,
- a create operation times out or returns an uncertain result,
- a linked record cannot be verified,
- a request would require external contact or an unapproved industry expansion.


## 30-company QA execution — 2026-11-03

The original 30-company cohort was audited independently from later additions to the base.

| Check | Result |
|---|---|
| Unique candidate names in cohort | 30/30 |
| Candidate source URLs, evidence summary, and limitations present | 30/30 |
| Verification, qualification, and action links present | 30/30 |
| Seven numeric score components present | 30/30 |
| Total score equals component sum | 30/30 |
| Need-proof checkbox incorrectly enabled | 0 |
| Unsupported buyer/consumption/supplier/specification/purchase-cycle values | 0 |
| External contact marked as completed | 0 |
| Structural acceptance issues | 0 |

**Gate C structural/data-integrity result: PASS for the 30-company cohort.** This does not mean all 30 companies are commercially qualified or that every low-confidence identity issue is resolved. Low-confidence and conflicting cases remain explicitly flagged for human review.

### Corrective actions completed

- Cleared 58 placeholder/procedural values from restricted qualification fields across 12 records; those fields are now blank pending direct evidence.
- Removed one exact duplicate run-ledger row after confirming the same run ID, timestamp, summary, counts, and no unique company links. The earlier canonical row was retained.
- Left later, unscored candidate records unscored; blank score fields were not converted to zero.
- No candidate company, source evidence, qualification status, or external-contact history was deleted or overwritten.

### Remaining release blockers

- **Gate B — Persistence:** still requires an explicitly approved named company/batch and a full create/read-back test.
- **Gate D — Automation:** not yet proven. The automation is enabled, but its saved environment is inherited with no explicit connected execution environment visible. A manual inline run is not proof of scheduled-context connector access.
- The 30-company QA result does not close the separate low-confidence identity review task.


## Follow-up candidate verification — Mazeed Produce / AIDC — 2026-11-03

**Disposition: hold out of Airtable pending human review; no candidate record created.**

- The official AIDC/Mazeed site identifies Mazeed Produce as the fresh-produce brand of Agricultural Investment & Development Company (AIDC), describes an integrated grower/packer/exporter operation, and states that it operates its own packhouse with grading, labelling, cold-chain and packing activity.
- The official contact page publishes the farm/packhouse location as Km 125, Cairo–Assiut Western Desert Road, Minya Governorate, and the export email export@aidcegypt.com.
- The official company pages describe customised fruit packaging, including count-packed cartons for oranges and pomegranates, and packing for grapes and peaches. This supports a **corner-protection research hypothesis only**; it does not prove the use or purchase of carton corner protectors.
- No evidence was found for actual winding/reel operations or paper-core consumption. Therefore the candidate is **not** a paper-core-track match.
- The Egyptian Export Portal profile lists a published mobile number and identifies Reham Kamal as export manager, but also shows “previously exported: No” while the company's current website claims 22 export markets. This material conflict is unresolved and must remain visible; the portal profile may be stale or the website claim may be overstated.
- Identity confidence: **medium-high** for the AIDC/Mazeed brand relationship based on the company's own pages and an older independent EBC profile; legal registration/current exporter status is not independently settled.
- Corner-pattern fit: **medium** based on the stated in-house packhouse and carton packing, without direct edge-protection evidence.
- Core-pattern fit: **not supported** by the available evidence.
- Duplicate review against the live candidate and reference names found no existing Mazeed/AIDC record.
- No phone call, email, WhatsApp, form submission, or other contact was made. The company was not saved because the research result is still a hypothesis and the user has not approved this named record for saving.

Sources:
- https://www.aidcegypt.com/about.html
- https://www.aidcegypt.com/contact.html
- https://www.aidcegypt.com/certifications.html
- https://www.expoegypt.gov.eg/co/mazeed-produce
- https://ebc.com.eg/ebc.com.eg/mazeed-produce-fresh-fruits-irrigation-systems/index.html
