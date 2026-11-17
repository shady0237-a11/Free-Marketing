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

## 8. Standing authorization and write procedure — approved 2026-11-17

### Discovery automation
The user has explicitly authorized the weekly discovery task to save qualifying new companies automatically in Airtable. This is a standing authorization for this defined workflow; do not ask for approval for each weekly batch or each company.

The scheduled task may read approved references and Airtable, research and verify companies, perform duplicate checks, create qualifying candidate records and their linked evidence/qualification/research-action records, write a run-ledger entry, and verify all writes by reading them back.

### Eligibility gate for automatic candidate creation
Create a candidate only when all of the following are supported by reviewable evidence:
- company/trading identity and current operating activity are sufficiently established;
- the actual process matches an approved reference pattern for paper cores or carton corner protectors;
- the relevant operating site/location is reasonably attributed;
- no exact or probable duplicate remains unresolved;
- the company is not a competitor manufacturing the same product for sale, unless a separate evidenced consuming operation independently qualifies.

Save qualifying P3 and P2 candidates when the minimum identity, activity, and reference-fit evidence is met. Label P3 as an exact reference-pattern match and P2 as an adjacent/partial match with the missing process link stated. Do not save P1 watchlist entries, P0 competitors/exclusions, unresolved identities, or unresolved probable duplicates. P2 is not a confirmed customer or confirmed product user.

### Required linked records and field discipline
1. Re-read the live Airtable schema, select options, and all relevant candidate/reference/run records before each write batch.
2. Re-run duplicate checks immediately before creating a candidate.
3. Create one candidate record per supported legal/operating entity/site; never use an upsert that could merge distinct companies or overwrite an existing record.
4. Create one verification record per material claim/source and link it to the returned candidate record ID.
5. Create a linked initial qualification record with status لم يبدأ (or the closest existing schema option), and leave need-proof unchecked.
6. Create a linked research-only action record; state clearly that no external contact occurred.
7. Link a confirmed field reference only when the actual process relationship is supported; preserve the P3/P2 distinction in the available classification fields/notes.
8. Populate only evidenced identity, activity, location, public contact, product-hypothesis, source, verification-date, confidence, and limitation fields. Keep consumption, current supplier, specifications, purchasing decision-maker, and purchase-cycle fields blank unless direct company-specific evidence exists. Never mark the company as a confirmed customer or confirmed need based on pattern fit.
9. Leave all score components and totals blank if the required scoring inputs are incomplete; never use zero to mean unassessed.
10. Do not modify or delete existing candidate, reference, execution-plan, or historical records as part of discovery.

### Safe write, recovery, and verification
- Write in stages: candidate first, then verification, qualification, and research-action records using the actual returned candidate ID; write the run ledger with unique run ID and batch counts/status.
- If a later stage fails, stop dependent writes, retain successful IDs, report partial completion, and do not blindly retry a create or create a duplicate candidate.
- Read back every created record and verify key fields and linked-record relationships. A create response alone is not success.
- If Airtable access, schema resolution, or write permission is unavailable in the scheduled execution context, stop all writes, report the batch as not saved, and list drafts/exceptions. Never imply that conversation-level connector access proves scheduled-task access.
- Report saved P3 and P2 separately, plus P1 watchlist (not saved), duplicates/existing companies, competitors/exclusions, and unresolved identities.

### Authorization boundary
This standing authorization covers only research-driven candidate/evidence/qualification/action/run-ledger records described above. It does not authorize calls, email, WhatsApp, forms, outreach, quotes, sales actions, paid services, new industry tracks, deletion, or edits to existing records. External contact remains prohibited. New reference-pattern expansion requires separate user approval.

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
8. Airtable save status: report the actual automatic-save result, separating saved P3/P2, not-saved P1/watchlist, duplicates, exclusions, and partial failures; never claim success without read-back.
9. Next human decision required.

## 11. Hard safety rules
- No external contact or outreach.
- No unsupported purchase/consumption claims.
- No automatic qualification as a customer.
- Automatic writes are permitted only within the user's standing authorization in Section 8; no unrelated or destructive writes are permitted.
- No deletion or silent overwriting of existing records.
- No expansion beyond approved reference patterns.
- No claims of completed work without tool-confirmed evidence and read-back.


## 12. Data hygiene and scoring controls — QA addendum 2026-11-03

- Keep the following qualification fields genuinely blank until direct evidence exists: monthly consumption, current supplier, required specifications, named purchasing decision-maker, and purchase cycle.
- Do not store placeholders such as "غير معروف", "غير متاحة", "غير مثبت", or workflow instructions in those data fields. Put explanatory notes in the notes/limitations field instead.
- If a candidate has not been scored, leave all score components and the total blank. Do not use zero to mean "not assessed".
- If a candidate is scored, all seven components must be numeric and the total must equal their sum. The score remains a research triage measure, never a purchase probability.
- Run IDs must be unique. Before creating a run-ledger row, read existing IDs and confirm that the proposed ID is unused. A run must have one canonical ledger row.
- Do not claim scheduled-task source access from a conversation-level connector test. Gate D passes only after a genuinely scheduled execution demonstrates access from its own context.
- A duplicate technical run-ledger row may be removed only after confirming exact duplication, absence of unique linked data, and explicit user authorization. Preserve one canonical row and document the correction.
