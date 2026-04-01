---
name: proposal-manager
description: Use this skill to analyze a solicitation and build a proposal plan before solution design begins. Extracts response type, page limits, section structure, evaluation criteria, win themes, and bid/no-bid assessment. Reads from inputs/ and writes to working/proposal-plan.md.
---

# Proposal Manager Skill

## Purpose
Bridge the gap between a blank proposal workspace and the technical solution design. Before the architect designs anything and before the writer drafts anything, this skill reads the solicitation and produces a complete proposal plan that governs every subsequent step.

## When to Use
- A solicitation, RFP, RFI, white paper request, BAA, or CSO has been dropped into `inputs/00_priority/`
- User says "analyze the solicitation", "build the proposal plan", or runs this after `/new-proposal`
- Immediately after `/new-proposal` and before `/proposal-solution-architect`

## Inputs
Read in this order:
1. All files in `inputs/00_priority/` — solicitation, evaluation criteria, instructions to offerors
2. All files in `inputs/01_customer/` — customer context, mission, constraints
3. `working/proposal-brief.md` — created by `/new-proposal`

If `inputs/00_priority/` is empty, tell the user to drop the solicitation there first and stop.

## Workflow

### Step 1: Classify the Opportunity
Determine:
- **Response type:** RFP / RFQ / RFI / White Paper / BAA / SBIR / STTR / OTA / CSO
- **Evaluation approach:** Best Value / LPTA / Fixed-price / Sole-source / Advisory
- **Competition type:** Full & Open / Small Business Set-Aside / Sole Source / Task Order
- **Contract type if applicable:** FFP / CPFF / T&M / IDIQ
- **Incumbent advantage:** Is there a known incumbent? Who?
- **Page/volume constraints:** Hard limits, if any

### Step 2: Extract Response Requirements
Pull directly from the solicitation:
- Required sections/volumes and their page limits
- Required fonts, margins, file formats
- Required attachments (past performance forms, resumes, certifications)
- Proposal due date, submission method, and POC
- Any questions/clarifications deadline

### Step 3: Build the Compliance Framework
Create a table of every stated requirement the proposal must address:

| ID | Requirement | Source (Section) | Mandatory/Desired | Addressed By | Notes |
|----|-------------|-----------------|-------------------|--------------|-------|

Flag:
- Requirements with no obvious capability match → will become gaps for the architect
- Ambiguous requirements that need assumption documentation
- Requirements that imply certifications, clearances, or registrations we must confirm

### Step 4: Analyze Evaluation Criteria
Extract all stated evaluation factors and subfactors:

| Factor | Subfactor | Weight / Order of Importance | Evaluation Standard | Your Strength |
|--------|-----------|------------------------------|--------------------|--------------------|

Note:
- Which factors are most heavily weighted
- Which factors are easy wins vs. competitive battlegrounds
- Whether price is evaluated separately or as a factor in best value

### Step 5: Prime vs. Sub Decision
Before scoring bid/no-bid, make the prime vs. sub call. This shapes every downstream decision — competitive strategy, teaming, pricing, and proposal structure all differ fundamentally based on this.

**Bid as Prime when:**
- Your company has the customer relationship and technical lead
- You can credibly perform the majority of work (typically 51%+)
- You have relevant past performance at comparable scope and dollar value
- Winning as prime advances your strategic positioning in this customer/domain

**Bid as Sub when:**
- A large prime has the customer relationship and you do not
- Your capability fills a specific gap in their solution but you can't cover the full scope
- The contract value or complexity exceeds your current capacity as prime
- Subcontracting builds a customer reference you can prime a follow-on

**Conditional: Sub with intent to Prime the follow-on** — a valid strategy for early-stage companies. Document this intent explicitly.

Record the decision: **PRIME / SUB / PRIME-SUB TEAMING (co-prime) / CONDITIONAL**

If bidding as sub: note which prime(s) to approach and what work share your company brings to the team.

---

### Step 6: Bid/No-Bid Assessment
Score each factor and produce a recommendation. For **prime bids**, all factors apply. For **sub bids**, skip factors marked *(prime only)*.

| Factor | Question | Score (1-5) | Notes |
|--------|---------|-------------|-------|
| Technical alignment | Do we have capabilities that directly address the core requirements? | | |
| Customer alignment | Have we worked with this specific program office or below? *(prime only)* | | |
| Relevant experience | Do we have past performance at equivalent scope and dollar value? *(prime only)* | | |
| Incumbency | Is the incumbent vulnerable? Are we positioned to unseat them? *(prime only)* | | N/A if no incumbent |
| Customer mission familiarity | Do we understand this customer's specific mission domain (C2, ISR, logistics, etc.)? | | |
| Contract size fit | Is the contract value appropriate for our current scale and capacity? *(prime only)* | | |
| Competitive position | Can we win against likely competitors in this role? | | |
| Customer relationship | Do we know the decision maker or have a path to them? | | |
| Pricing competitiveness | Can we price to win at an acceptable margin? | | |
| Resource availability | Do we have the people to execute the work AND write the proposal? | | |
| Strategic value | Does winning this advance our positioning in this customer/domain? | | |

**Scoring:** 5=strong yes, 4=likely yes, 3=neutral/uncertain, 2=likely no, 1=significant gap

**Threshold guidance:**
- Average ≥ 4.0 → BID
- Average 3.0–3.9 → CONDITIONAL BID (state conditions)
- Average < 3.0 → NO-BID
- Any single factor scored 1 → flag as a blocking risk before proceeding

**Recommendation:** BID / NO-BID / CONDITIONAL BID (with conditions stated)

### Step 7: Define Win Themes
Write 3-5 win themes. Each must:
- Map directly to an evaluation factor
- Reference a specific company capability or proof point
- Be expressible in one sentence

Format:
| Theme | Evaluation Factor | Proof Point |
|-------|------------------|-------------|

### Step 8: Write the Proposal Plan
Write all findings to `working/proposal-plan.md` using this structure:

```markdown
# Proposal Plan — [Proposal Name]

## Opportunity Classification
- Type:
- Evaluation approach:
- Competition:
- Contract type:
- Incumbent:
- **Prime vs. Sub decision:** [PRIME / SUB / CO-PRIME / CONDITIONAL]
- **If sub:** Target prime(s) and your company's work share:

## Response Requirements
- Due date:
- Submission method:
- Questions deadline:
- Page limits: [by volume/section]
- Format requirements:
- Required attachments:
- POC:

## Compliance Framework
[compliance table]

## Evaluation Criteria Analysis
[evaluation table]

## Bid/No-Bid Assessment
[scoring table]
**Recommendation:**

## Win Themes
[win themes table]

## Open Questions / Assumptions
[list of ambiguities to resolve before writing]

## Recommended Proposal Structure
[proposed outline with section owners and page budget]
```

## Output File
**Always write to `working/proposal-plan.md` — do not just display in chat.**

## Rules
- Pull every requirement directly from the solicitation text — do not invent or assume
- Flag every gap explicitly; the architect will address them
- Win themes must connect to specific proof points, not general claims
- If evaluation weights are not stated, infer priority from order listed and section prominence
- If this is a white paper with no formal evaluation criteria, infer criteria from the stated purpose and decision maker

## After Running This Skill
Tell the user:
1. Bid/no-bid recommendation with rationale
2. Top 3 compliance risks (requirements with no obvious match)
3. Win theme summary
4. Suggested next step: `/proposal-solution-architect`

## Lessons Learned

### On White Papers
- White papers rarely state explicit evaluation criteria — infer from the office, the stated problem, and the decision maker's known priorities. For SOCPAC-type submissions, operational utility and DDIL compatibility were the implied discriminators even though never stated.
- For CDAO/DIU-type solicitations, evaluation innovation and mission-representative benchmarking matter more than past performance volume.

### On Win Themes
- Generic themes ("we're the best") fail. Win themes must be specific: "[Model Name] matches [Competitor Model] on military tasks while running air-gapped on a laptop" is a win theme. "We have deep military AI expertise" is not.
- Three themes is usually the right number. Five or more dilutes focus.

### On Compliance Frameworks
- Government evaluators score compliance before they score merit. A technically brilliant proposal that misses a formatting requirement or skips a required section can be disqualified outright.
- Build the compliance table first — before writing a single word of the proposal.
