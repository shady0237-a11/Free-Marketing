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
