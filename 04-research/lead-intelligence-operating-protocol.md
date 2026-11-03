# Alamir Pack Lead Intelligence — Operating Protocol
## Version 1.0 — 2026-11-03

## 1. Purpose and operating boundary
This protocol governs discovery, evidence review, candidate approval, Airtable writes, and post-write verification for Alamir Pack.

The system discovers Egyptian companies whose documented operating processes resemble user-confirmed field references for:
- Paper/cardboard cores used in actual winding or reel applications.
- Carton corner protectors used in documented packing, palletizing, or product-protection applications.

A match is a research hypothesis, not proof of purchasing, consumption, a current supplier, or buying intent.

Never contact companies. No calls, email, WhatsApp, contact forms, outreach, or external actions. No change to the sales workflow is authorized by this protocol.

## 2. Sources of truth and precedence
1. Airtable base appb3bXovCXwyc4DD is the operational candidate and evidence database.
2. Field reference files in this repository are the calibration baseline:
   - field-validation-reference-map.md
   - carton-corner-protection-reference-registry.md
   - agricultural-produce-packing-reference-registry.md
3. Official company sources, current government/registry sources, and recognized sector bodies establish current company facts.
4. Secondary directories are discovery leads only unless independently corroborated.

If sources conflict, preserve the conflict; do not silently choose a preferred value. Record source date and verification date separately.

## 3. Product-specific discovery tracks

### A. Paper/cardboard core track
A candidate must have evidence of an actual product/process that is wound, rewound, slit, or supplied as reels/rolls. Strong patterns include:
- Paper and paperboard mills producing industrial reels.
- Plastic film, stretch film, BOPP, PVC, and other flexible-film production with winding/jumbo rolls.
- Adhesive tape and similar converting operations with jumbo rolls.
- Nonwoven, foil, turf, insulation, or other roll goods only where the actual winding process is documented.

Do not qualify a company merely because it is in plastics, textiles, paper, packaging, or manufacturing. Do not confuse a company manufacturing paper cores with a core-consuming prospect.

### B. Carton corner-protector track
Use patterns supported by field references, especially:
- Ceramic and porcelain production/packing.
- Agricultural produce sorting, packing, cold storage, palletizing, and export stations.
- Other packing/protection processes only when a field reference or user-approved extension supports the analogy.

A company shipping cartons is not enough. Find evidence of packing, palletizing, stacking, or product-edge protection operations.

### C. New industry patterns
Do not expand the reference universe autonomously. Put new patterns in a separate proposed-calibration section with evidence and ask for user approval before treating them as search tracks.

## 4. Identity and fit are separate assessments
For every candidate, report two independent confidence assessments:
- Identity/data confidence: legal/trade identity, current operation, site/location, website, public contact details, source reliability, and conflict resolution.
- Reference-fit confidence: evidence that the actual process resembles a named field reference for the specific product.

Do not merge these into a single confidence label. Never award evidence points for core consumption without direct evidence of the core itself. Do not describe a prospect as a customer or qualified opportunity unless the user supplies direct evidence.

## 5. Evidence requirements
For each candidate:
- Confirm the legal or operating name and distinguish brand, site, subsidiary, and parent.
- Confirm the current activity and the relevant physical process.
- Confirm the specific facility/location; do not infer factory location from a head-office address.
- Prefer official website/catalogue, government registry/licence, export/industry body, or first-party company publication.
- Use a second independent source for material identity/location claims where possible.
- Record exact URLs, source type, evidence excerpt/summary, publication date if available, and date checked.
- Separate published phone/email from the factory's direct line; never infer that an office number belongs to a plant.
- List unknowns and contradictions explicitly.

Search snippets alone are not sufficient evidence for a high-confidence candidate.

## 6. Duplicate control
Before presenting a company as new, compare it against all candidate and reference records using:
- normalized legal name and trade name,
- parent/subsidiary/site relationships,
- official domain and known alternate domains,
- phone numbers,
- address and industrial-zone/site,
- Arabic/English transliterations and common abbreviations.

Potential matches are duplicate-review exceptions, not new candidates. Never create a second record just because the company has another brand or site; explain the relationship first.

## 7. Airtable data contract
Base: appb3bXovCXwyc4DD

Tables:
- Candidates: tbldCQRJBO03US5Cu
- Verification log: tblMopnaolqztElRj
- Qualification: tbl4Zvti2Q4jDUIx0
- Action log: tbli1FRGPo6FpF3KC
- Execution plan: tblSf8PXSoDLffYf7
- Confirmed field references: tblPv5YDSxHnNBNe4
- Run ledger: use the table named سجل تشغيل المساعد; resolve its ID live and never guess.

### Candidate record rules
- One candidate record per legal/operating entity/site as justified by evidence.
- Store source URLs and evidence summaries, not unsupported assertions.
- Set initial qualification to مرشح للبحث or قيد التحقق as appropriate.
- Do not set احتياج مثبت unless direct evidence establishes need.
- Do not populate consumption, current supplier, specifications, buyer, or purchase-cycle fields without direct evidence.
- Link verification records, qualification record, action log, and matching field-reference record only after those records exist and the link has been verified.
- Keep priority score as a research triage score, never a purchase probability.

### Verification records
Create one verification record per material claim/source, linked to the candidate. Preserve failed, partial, old, and conflicting evidence as well as positive evidence.

### Qualification records
A qualification record may document an unknown/early-stage state. It must not manufacture buyer, consumption, supplier, or buying-cycle information. Keep هل تم إثبات الاحتياج؟ unchecked unless direct evidence exists.

### Action log
Record research and verification actions. Set يتطلب موافقة مسبقة for any action requiring approval. Do not record an external contact as completed unless it actually occurred with explicit authorization; external contact remains prohibited here.

## 8. Approval gate and write procedure

### Discovery automation
The scheduled weekly task is read-only. It may:
- read Airtable and reference files,
- search and verify companies,
- prepare a structured candidate batch,
- prepare proposed Airtable field values and intended record links,
- produce a report with exclusions, duplicates, confidence, and unresolved questions.

It must not write to Airtable, GitHub, or any other system.

### Human approval
After the report is presented, wait for an explicit user instruction approving a named batch or named companies for saving. A general request to continue research is not save approval.

### Save execution
After approval:
1. Re-read the live Airtable schema and all relevant candidate records.
2. Run duplicate checks again immediately before writing.
3. Create candidate records first.
4. Create verification records and link them to the returned candidate record IDs.
5. Create the qualification record with unknowns left blank and need-proof unchecked.
6. Create a research action record; no external action.
7. Link matching reference records only when the relationship is supported.
8. Write a run-ledger record with the approved batch and action result.
9. Read all created records back from Airtable and verify field values and links.
10. Report created IDs/counts, skipped duplicates, failures, and unresolved links. Never report success until read-back confirms it.

If any step fails, stop dependent writes, preserve successful IDs, report partial completion, and do not blindly retry a create.

## 9. Run ledger
One record per run. Store:
- run label/ID and timestamp,
- run status and tracks searched,
- counts searched, proposed, excluded, duplicate-review, and unresolved,
- report URL or report location,
- save approval state and approval reference,
- created/linked record counts,
- read-back verification result,
- errors and partial-completion details.

Do not fabricate a run ID or claim a run was logged if no record was created and read back.

## 10. Weekly report format
1. Run timestamp, scope, and sources read.
2. Search coverage by product track and geography.
3. New candidates (each with legal/trade name, site, process, product hypothesis, matched field reference, official website, public contacts, evidence links, identity confidence, fit confidence, and limitations).
4. Duplicate/identity exceptions.
5. Rejected candidates and reason.
6. Proposed new patterns requiring user calibration.
7. Counts and limitations, including sources unavailable or searches not completed.
8. Airtable save status: always state not saved — awaiting approval for the discovery automation.
9. Next human decision required.

## 11. Hard safety rules
- No external contact or outreach.
- No unsupported purchase/consumption claims.
- No automatic qualification as a customer.
- No automatic writes by the weekly discovery task.
- No deletion or silent overwriting of existing records.
- No expansion beyond approved reference patterns.
- No claims of completed work without tool-confirmed evidence and read-back.
