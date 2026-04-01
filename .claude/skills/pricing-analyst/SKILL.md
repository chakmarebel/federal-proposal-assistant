---
name: pricing-analyst
description: Use this skill to develop pricing strategy, cost estimates, basis of estimate (BOE) narratives, and a cost volume draft. Reads from working/ files and prompts for rate inputs. Writes to working/pricing-inputs.md and drafts/cost-volume.md.
---

# Pricing Analyst Skill

## Capture Mode
**Read `working/proposal-brief.md` before proceeding.** Check:
- `Capture Mode:` — Full Capture or Responsive
- `Proposal type:` — identifies the specific vehicle for responsive pricing

- **Full Capture** → run the complete workflow below
- **Responsive** → skip to [Responsive Mode](#responsive-mode) at the bottom of this skill

If the field is blank, ask the user before proceeding.

## Purpose
Translate the approved solution architecture into a defensible pricing strategy and cost volume narrative. Pricing is not just numbers — it is an argument for value and a commitment to execution at a stated cost.

## When to Use
- Solution architecture is approved (`working/solution-strategy.md` and `working/architecture-concept.md` exist)
- A cost volume or pricing narrative is required by the solicitation
- User needs a price-to-win estimate or pricing strategy discussion
- Run after `/proposal-solution-architect`, before or parallel to `/proposal-writer`

## Inputs
Read before prompting for any information:
- `working/proposal-plan.md` — cost volume requirements, evaluation weight for price, contract type
- `working/solution-strategy.md` — scope of work, deliverables, key activities
- `working/architecture-concept.md` — components, interfaces, deployment model
- `working/requirement-matrix.md` — scope and performance requirements
- `inputs/00_priority/` — solicitation for any stated pricing format requirements

## Interactive Input Collection
After reading the above, ask the user for the following. Ask in one organized block — do not ask one question at a time unless the user prefers that.

### Labor
- What labor categories will you propose? (e.g., Senior ML Engineer, Program Manager, Systems Engineer, Junior Analyst)
- For each: billing rate ($/hr), estimated hours per period, and clearance level if relevant
- Are any team members named / key personnel?

### Period of Performance
- How many base periods? Option periods?
- Duration of each (e.g., 12 months base + 2 x 12 month options)?

### Subcontractors / Teammates
- Are any work shares going to subcontractors or teammates?
- If yes: company name, work description, estimated dollars or percentage of total

### Other Direct Costs (ODCs)
- Travel: estimated trips, destinations, per diem approach
- Equipment / hardware: any GFE assumptions? Any vendor hardware to be purchased?
- Software licenses: any commercial tools in the solution
- Other: cloud compute, data, facilities, etc.

### Fee / Profit
- What fee rate are you targeting? (typical range: 8-12% for services, lower for R&D)
- Any fee restrictions stated in the solicitation?

### Pricing Strategy
- Is this LPTA (price is the deciding factor) or best value (quality matters more than lowest price)?
- Do you have intelligence on competitor pricing or the government's budget?
- Is there a should-cost target or program budget ceiling you know about?

## Workflow

### Step 1: Build the Work Breakdown Structure (WBS)
From the solution strategy and architecture, define the major work elements:
- Each deliverable or capability becomes a WBS line
- Each phase of execution becomes a cost period
- Flag any GFE, ODCs, or subcontract work separately

### Step 2: Build the Cost Model
Calculate:
- Direct labor: hours × rate by category by period
- Fringe/benefits: apply rate if provided (typical: 25-35% of direct labor)
- Overhead: apply rate if provided (typical: 15-25% for tech companies)
- G&A: apply rate if provided (typical: 10-15%)
- Subcontracts: pass-through with any markup
- ODCs: travel, equipment, software licenses
- Fee: apply to total cost before fee
- Total evaluated price (TEP) by period and cumulative

### Step 3: Price-to-Win Assessment
Based on the pricing strategy inputs:
- Is the total price competitive relative to known market rates?
- Is the fee rate defensible given the risk profile?
- Are there any areas where cost reduction is possible without scope reduction?
- Flag any assumptions that could blow the budget (e.g., travel not well scoped)

### Step 4: Draft the BOE Narrative
For each major WBS element, write a basis of estimate paragraph:
- What work is being performed
- Who is performing it (labor category)
- How the hours were estimated (analogy, parametric, or engineering build-up)
- Key assumptions

### Step 5: Draft the Cost Volume
Structure depends on solicitation requirements. Default structure:

```
1. Cost Summary Table
   - By period, by cost element
   - Total evaluated price

2. Basis of Estimate (by WBS)
   - Narrative for each work element
   - Labor category, hours, rates

3. Labor Rate Justification
   - How rates were set (market data, GSA schedule, certified rates)
   - Named personnel rates if required

4. ODC Narrative
   - Travel plan with justification
   - Equipment/hardware with justification

5. Subcontractor Approach
   - What work, why subcontracted, how managed

6. Fee Rationale
   - Rate and justification

7. Assumptions and Exclusions
   - What is NOT included in price
   - Key pricing assumptions
```

## Output Files
**Always write to disk — never just display in chat.**

- `working/pricing-inputs.md` — raw inputs, WBS, cost model calculations, and pricing strategy notes
- `drafts/cost-volume.md` — formatted cost volume narrative ready for inclusion in proposal

## Cost Volume Writing Rules
- Justify every number — evaluators will probe unsupported estimates
- Be specific about labor categories and hours — "sufficient staffing" is not a basis of estimate
- Acknowledge assumptions explicitly — "This estimate assumes Government-furnished facilities and network access"
- Do not promise more than you've priced — if a commitment is in the technical volume, it must be funded in the cost volume
- Match the cost volume structure to the solicitation's required format exactly

## Pricing Strategy Rules
- For LPTA: sharpen the pencil on ODCs and overhead; margin compression is expected
- For best value: price to win on merit, not on lowest cost; defend the fee as risk-appropriate
- Never price below your cost to execute — a win you can't deliver is worse than a loss
- If budget ceiling is known, work backward from it to the WBS

## After Running This Skill
Tell the user:
1. Total evaluated price summary (base + options)
2. Top 3 pricing risks or assumptions that could break the estimate
3. Price-to-win assessment and any suggested adjustments
4. Confirm that `working/pricing-inputs.md` and `drafts/cost-volume.md` were written

---

## Responsive Mode

For SBIR, CSO, OTA, and BAA — no full BOE required. Pick the branch that matches the proposal type.

---

### SBIR Phase I
**Budget ceiling: $150,000 / 6 months** (verify against current solicitation — limits vary by agency)

Ask the user for:
- Principal Investigator name and hourly rate
- Other key personnel (name, role, hours, rate)
- Estimated materials / equipment
- Travel (if any)
- Indirect cost rate (fringe + overhead combined, or separately)
- Fee %

Produce a standard SBIR budget table:

| Cost Element | Cost |
|-------------|------|
| Direct Labor | |
| &nbsp;&nbsp;PI: [name], [hrs] hrs @ $[rate]/hr | $X |
| &nbsp;&nbsp;[Other personnel] | $X |
| Fringe Benefits ([rate]%) | $X |
| Materials / Supplies | $X |
| Travel | $X |
| Other Direct Costs | $X |
| **Total Direct Costs** | **$X** |
| Overhead ([rate]%) | $X |
| **Total Costs** | **$X** |
| G&A ([rate]%) | $X |
| Fee ([rate]%) | $X |
| **Total Price** | **$X** |

Also draft a 1-paragraph budget narrative explaining the major cost drivers and why the budget is sufficient for the proposed scope.

Write to: `drafts/cost-volume.md` and `working/pricing-inputs.md`

---

### SBIR Phase II
**Budget ceiling: ~$750,000 / 24 months** (verify against current solicitation)

Same structure as Phase I but expanded for 24 months and larger team. Organize by period (Period 1: Months 1–12, Period 2: Months 13–24).

Include: personnel plan (who does what in each period), major milestones by period, equipment or subcontract justification if any.

---

### OTA (Other Transaction Authority)
OTA pricing is milestone-based. Evaluators want to see: what will be demonstrated at each milestone, what does each milestone cost, and what is the total prototype cost.

Ask the user for:
- Number of milestones (typically 3–5 for a prototype agreement)
- Description and deliverable for each milestone
- Estimated cost per milestone
- Period of performance per milestone
- Any cost-sharing contribution (OTAs often require non-traditional contractor cost share)

Produce:

**Milestone Payment Schedule:**

| Milestone | Description / Deliverable | Period | Cost |
|-----------|--------------------------|--------|------|
| M1 | [what is delivered / demonstrated] | Month X | $X |
| M2 | | | |
| **Total** | | | **$X** |

Draft a 2-paragraph cost narrative: (1) methodology for estimating milestone costs, (2) cost-share approach if applicable.

Write to: `drafts/cost-volume.md` and `working/pricing-inputs.md`

---

### BAA (Broad Agency Announcement)
BAAs are typically cost-reimbursable (CPFF). No detailed BOE format required — a rough order of magnitude with narrative justification is standard for white papers; full budget may be required for full proposals.

Ask the user for:
- Total estimated cost (ROM)
- Major cost categories (labor, materials, travel, subcontracts, overhead)
- Period of performance
- Contract type preferred (CPFF recommended for research)

Produce:
- A cost summary table (category-level, not line-item)
- A 1–2 paragraph cost narrative: scope of work → major cost drivers → why the budget is appropriate → CPFF rationale

For white paper stage: one paragraph ROM with range ($X–$Y) is sufficient. Flag that a full budget will be provided at full proposal stage if selected.

Write to: `drafts/cost-volume.md` and `working/pricing-inputs.md`

---

### CSO (Commercial Solution Opening)
CSOs are commercial-style procurements. Pricing should feel like a commercial proposal, not a government cost volume. Ask the user:

- Is this a product sale, subscription/license, professional services engagement, or a combination?
- What is the unit price or annual price?
- What is the proposed contract value (total or per year)?
- Is this a fixed price or variable/usage-based model?

Produce:
- A simple pricing table (1 page max) showing what is being purchased and at what price
- A 1-paragraph pricing narrative: how the price was set (market-based, cost-plus, subscription model), why it represents good value, and any volume or multi-year discount options

Avoid government cost accounting language (fringe rates, G&A, overhead percentages) in CSO submissions — it reads as unfamiliar with commercial practice.

Write to: `drafts/cost-volume.md` and `working/pricing-inputs.md`

---

### White Paper / Unsolicited Proposal
No cost volume required for submission. Produce an internal ROM for pipeline purposes only:
- Total estimated value if awarded
- Rough cost breakdown (labor, ODCs, fee)
- Write to `working/pricing-inputs.md` only — do not include in submission drafts

## Lessons Learned

### On BOE Narratives
- Evaluators read BOE narratives to assess whether the team understands the work. A vague BOE ("we will provide X senior engineers as needed") signals that the team hasn't thought through execution.
- Engineering build-up estimates (hours derived from task analysis) are more credible than analogy estimates ("we did something similar for $Y").

### On Fee
- Fee is not just profit — it is a signal of confidence and risk tolerance. Too low (below 8%) looks desperate. Too high (above 12% on a competitive bid) draws scrutiny. Match fee to competition type and risk profile.

### On Teaming / Subcontracts
- Price subcontractor work as pass-through with a small handling fee (typically 5-8%). Excessive markup on subcontracts is a red flag for evaluators.
- If a subcontractor's work is core to the solution, justify why it's not being done by the prime.

### On Assumptions
- Every assumption that inflates cost should be called out so the customer can choose to provide GFE or change scope to reduce price.
- Every assumption that deflates cost is a risk — if the assumption is wrong, you absorb the overrun.
