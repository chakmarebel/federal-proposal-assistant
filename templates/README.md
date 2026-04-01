# Proposal Templates

This directory contains the empty scaffold for a new proposal. The `/new-proposal` skill copies this structure and seeds it with boilerplate.

## Directory Structure
```
templates/
├── inputs/
│   ├── 00_priority/    ← Solicitation, eval criteria, distribution statement
│   ├── 01_customer/    ← Mission context, problem statement, constraints
│   ├── 02_yourCompany/  ← Our capabilities, past performance, components
│   ├── 03_teammates/   ← Partner capabilities (if teaming)
│   ├── 04_patterns/    ← Reference architectures, win themes from past efforts
│   ├── 05_graphics/    ← HTML graphic templates, visual standards
│   └── 06_notes/       ← Raw notes, meeting inputs, call summaries
├── working/            ← Analysis artifacts (requirement matrix, solution strategy)
├── drafts/             ← Proposal section drafts
└── reviews/            ← Red team notes, compliance checks, gap logs
```

## Quick Start
1. Run `/new-proposal` — it will create a named copy of this structure
2. Drop your source materials into `inputs/`
3. Run `/proposal-solution-architect` to analyze and design
4. Run `/proposal-graphics` to create visuals
5. Run `/proposal-writer` to draft sections
6. Run `/red-team-review` to identify gaps
