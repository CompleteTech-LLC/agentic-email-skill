# Agentic Email Skill

<p align="center">
  <img src="assets/logo.png" alt="CompleteTech LLC logo" width="260">
</p>

A CompleteTech LLC Codex skill for creating agentic development outreach, sales, follow-up, delivery, retention, referral, and win-back emails.

## About

Part of the CompleteTech LLC agentic services skill library. This skill drafts message copy and sequences that support sales, delivery, retention, referral, and reactivation without replacing specialist artifacts.

## OpenClaw / ClawHub Metadata

- Skill key: `agentic-email-skill`
- Version-ready metadata: `1.0.0`
- Homepage: https://github.com/CompleteTech-LLC/agentic-email-skill
- README: https://github.com/CompleteTech-LLC/agentic-email-skill#readme
- Runtime binaries: `python3`
- Python packages: none
- Intended registry/discovery tags: `latest`, `complete-tech`, `codex-skill`, `agentic-development`, `agentic-workflows`, `email`, `outreach`, `sales`
- License: repository code, templates, and documentation use MIT; ClawHub publishing is intentionally skipped for now.
- Brand assets: CompleteTech LLC names, logos, seals, and brand assets are reserved; see `BRAND_ASSETS.md`.

## Workflow Diagram

```mermaid
flowchart LR
  A[Audience and stage] --> B[Template or sequence choice]
  B --> C[Verified trigger, offer, proof, and CTA]
  C --> D[Draft email]
  D --> E{Human review needed?}
  E -->|Yes| F[Revise before sending]
  E -->|No| G[Ready-to-send copy]
  classDef source fill:#eef6ff,stroke:#3778c2,color:#102a43;
  classDef gate fill:#fff7e6,stroke:#c97a12,color:#3d2600;
  classDef output fill:#eefaf0,stroke:#2f8f46,color:#12351d;
  class A,B,C source;
  class E gate;
  class D,F,G output;
```

## What It Does

- Selects the right email for the prospect or client stage.
- Drafts individual emails or full outreach/sales cadences.
- Keeps the pitch focused on practical agentic workflow development: discovery, implementation, evaluation, approval gates, monitoring, documentation, and handoff.
- Includes a near-exhaustive template catalog for end-to-end sales motion.

## Contents

- `SKILL.md` - operating instructions and template-selection guide.
- `references/email-catalog.md` - 52 reusable email templates.
- `references/use-case-decision-table.md` - quick guide for choosing the right email.
- `references/sequence-blueprints.md` - recommended multi-email cadences.
- `references/positioning.md` - CompleteTech LLC agentic development positioning and guardrails.
- `scripts/render_email.py` - deterministic template listing and rendering helper.

## Quick Start

```bash
python3 scripts/render_email.py --list
python3 scripts/render_email.py \
  --template cold-problem-pilot \
  --var prospect_name=Alex \
  --var company=Acme \
  --var trigger="the team is scaling support operations" \
  --var workflow="support triage"
```

Rendered templates are drafts. Replace placeholders with verified prospect, client, offer, proof, and timing details before use.

## Example

![Proposal cover email preview](assets/examples/example.png)

**Proposal cover email: Pilot scope ready for review**

```bash
python3 scripts/render_email.py \
  --template proposal-sent \
  --var prospect_name="Jordan" \
  --var company="Northstar Support" \
  --var workflow="support triage pilot" \
  --var next_step="review the pilot scope and confirm whether the approval gate matches your process"
```

Example draft:

> Subject: Support triage pilot scope for review
>
> Jordan, I attached the pilot scope for the reviewed support triage workflow. The key design choice is the approval gate: the agent prepares classification notes and reply drafts, but your support lead approves anything customer-facing. If that matches your process, the next step is confirming the sample ticket set and pilot reviewers.

## Brand Notes

Use a direct, concrete, low-hype tone. Pitch agentic development as bounded workflow implementation with human approval gates, evaluation examples, logging, monitoring, and handoff documentation. Do not invent client proof, metrics, regulated-use assurances, or legal claims.

## License

Code, templates, and documentation are licensed under the MIT License. CompleteTech LLC names, logos, seals, and brand assets are reserved and are not licensed for reuse except to identify this project. See `LICENSE` and `BRAND_ASSETS.md`.
