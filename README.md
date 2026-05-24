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
- Python packages: `reportlab>=4.0` (optional PNG preview: `pypdfium2`, `pillow`)
- Intended registry/discovery tags: `latest`, `complete-tech`, `codex-skill`, `agentic-development`, `agentic-workflows`, `email`, `outreach`, `sales`, `pdf`, `pdf-generator`
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
- `scripts/render_pdf.py` - branded CompleteTech PDF generator (Markdown -> PDF + optional PNG preview).
- `requirements.txt` - Python dependencies for branded PDF rendering.

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

![Outbound Email Sequence preview](assets/examples/example.png)

Full-document **branded PDF** rendered from the generated artifact: [example.pdf](assets/examples/example.pdf). Markdown source: [example.md](assets/examples/example.md).

**Outbound email sequence: 3-step cold cadence for a support-triage bottleneck**

- Three drafts: cold operations bottleneck, workflow-map follow-up, and breakup.
- One clear CTA per email; polite opt-out on cold outbound.
- Drafts only — verify recipient and routing before sending.
- No fabricated metrics or client names.

Generate the branded PDF (artifacts are delivered as PDFs, not raw Markdown):

```bash
pip install -r requirements.txt
# 1) Draft the artifact (optionally start from a catalog template)
python3 scripts/render_email.py --template cold-operations-bottleneck > assets/examples/example.md
# 2) Render the branded CompleteTech PDF (+ optional PNG preview)
python3 scripts/render_pdf.py --markdown assets/examples/example.md \
  --out assets/examples/example.pdf --png assets/examples/example.png \
  --logo assets/logo.png --title "Outbound Email Sequence" \
  --doc-type "EMAIL DRAFTS — VERIFY BEFORE SENDING" --subtitle "Prospect: <b>Northwind Trading Co.</b>" --meta "SEQUENCE=PRO-OUT-014" --meta "STAGE=Cold outreach" --meta "STEPS=3 emails"
```

## Brand Notes

Use a direct, concrete, low-hype tone. Pitch agentic development as bounded workflow implementation with human approval gates, evaluation examples, logging, monitoring, and handoff documentation. Do not invent client proof, metrics, regulated-use assurances, or legal claims.

## License

Code, templates, and documentation are licensed under the MIT License. CompleteTech LLC names, logos, seals, and brand assets are reserved and are not licensed for reuse except to identify this project. See `LICENSE` and `BRAND_ASSETS.md`.
