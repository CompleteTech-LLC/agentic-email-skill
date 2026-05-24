---
name: agentic-email-skill
description: >-
  Create tailored sales, outreach, nurture, follow-up, proposal, objection-handling, closing, onboarding, retention, referral, and win-back emails for agentic development services. Use when Codex needs to draft individual emails or near-complete email sequences that pitch agentic software workflows from first contact through sale and post-sale follow-up.
version: 1.0.0
metadata:
  openclaw:
    skillKey: agentic-email-skill
    homepage: https://github.com/CompleteTech-LLC/agentic-email-skill
    requires:
      bins:
        - python3
---

# Agentic Email Skill

## Purpose

Create practical email copy for selling agentic development services end to end: prospecting, qualification, discovery, proposal, contract, closing, kickoff, delivery updates, retention, referrals, and win-back.

## System Boundary

This skill owns email copy and sequences. It may reference artifacts from the other skills, but it does not replace them: use `agentic-discovery-skill` for discovery artifacts, `agentic-proposal-skill` for proposal/SOW content, `agentic-contract-skill` for agreement packages, `agentic-invoice-skill` for invoice documents, `agentic-delivery-skill` for delivery records, `agentic-customer-success-skill` for account state, and `agentic-case-study-skill` for approved proof. Treat every email as a draft unless the user explicitly asks to send and the recipient/routing facts are verified.

## Core Workflow

1. Identify the stage: cold outreach, warm intro, follow-up, booked meeting, discovery recap, proposal, close, post-sale, retention, referral, or reactivation.
2. Gather only the facts needed for the stage:
   - buyer name, company, role, industry
   - observed trigger or business pain
   - agentic workflow being pitched
   - proof, constraints, offer, CTA, and timing
3. Use the positioning in `references/positioning.md` for the service promise, risk controls, and language to avoid.
4. Use `references/email-catalog.md` when the user asks for a near-exhaustive library, a multi-step sequence, or a specific stage template.
5. Use `references/sequence-blueprints.md` when designing an outreach or sales cadence.
6. Draft in the requested voice, or default to concise, plain, consultative, and specific.
7. Include subject lines when useful. Do not fabricate case studies, client names, metrics, legal claims, or regulated-use assurances.

## Email Selection Guide

Choose the email by the job the message must do:

- New cold prospect, no prior context: use `cold-problem-pilot` unless a more specific buyer fit applies.
- Operations leader with manual queue, triage, routing, or handoff pain: use `cold-operations-bottleneck`.
- CTO, engineering, IT, data, or AI owner: use `cold-technical-evaluation`.
- Executive worried about AI risk or governance: use `cold-executive-risk`.
- Sales leader or revenue operations: use `cold-revenue-team`.
- Support, customer success, or service desk leader: use `cold-support-team`.
- Knowledge management, internal ops, or scattered documentation pain: use `cold-ops-knowledge`.
- Founder or small team: use `cold-founders`.
- First follow-up after cold email: use `followup-workflow-map`.
- Follow-up when risk, approvals, or control are the likely concern: use `followup-risk-controls`.
- Follow-up that needs a concrete example: use `followup-example`.
- Follow-up when the prospect may think the project is too large: use `followup-proofless-value`.
- Follow-up when you need a short diagnostic reply: use `followup-breakthrough-question`.
- Last cold follow-up: use `breakup-close-loop`.
- Referred prospect: use `warm-intro-context`, then `warm-intro-workflow`.
- Inbound lead: use `inbound-fast-response`, then `inbound-qualification`, then `inbound-booking`.
- Before discovery: use `discovery-confirm-agenda`.
- After discovery: use `post-discovery-recap`.
- Before a formal proposal: use `proposal-preview`.
- Sending a proposal: use `proposal-sent`.
- Proposal follow-up: use `proposal-followup-questions`.
- Budget objection: use `close-objection-budget`.
- Risk, compliance, or autonomy objection: use `close-objection-risk`.
- Timing objection: use `close-objection-timing`.
- "We may build internally" objection: use `close-objection-internal-team`.
- Summarizing the close: use `close-decision-summary`.
- Final decision nudge: use `close-final-nudge`.
- Sending contract: use `contract-sent`.
- Contract questions: use `contract-clarifications`.
- Invoice or deposit: use `deposit-invoice`.
- Waiting on signature: use `signature-reminder`.
- After signature: use `kickoff-after-signature`.
- Kickoff logistics: use `kickoff-agenda`.
- Need docs, access, sandbox, or examples: use `access-request`.
- During delivery: use `weekly-update`.
- Prototype ready: use `review-ready`.
- Acceptance review: use `acceptance-request`.
- Handoff complete: use `handoff-complete`.
- Expanding to another workflow: use `expansion-next-workflow`.
- Asking for referral: use `referral-request`.
- Asking for testimonial: use `testimonial-request`.
- Post-project check-in: use `quarterly-checkin`.
- Lost or stale opportunity with new reason to reconnect: use `winback-new-trigger`.
- Hiring trigger: use `trigger-hiring`.
- New tool, platform, migration, or integration trigger: use `trigger-new-tool`.
- Growth, funding, new location, new team, or volume spike trigger: use `trigger-growth`.
- Educational nurture with no immediate ask: use `nurture-educational`.
- Smaller advisory offer: use `nurture-one-page-offer`.
- Old opportunity without a specific new trigger: use `reengage-old-opportunity`.

When multiple templates fit, choose the one closest to the buyer's current decision point. For example, do not send a closing email to a prospect who has not agreed there is a workflow worth scoping; use a mapping or discovery email first.

## Quality Rules

- Keep cold emails under 120 words unless the user asks for long-form.
- Lead with a concrete operational problem, not generic AI excitement.
- Pitch agentic development as workflow design, implementation, evaluation, monitoring, and human approval gates.
- Use one clear CTA per email.
- Make follow-ups additive: new angle, artifact, risk reducer, example workflow, or decision prompt.
- Include a polite opt-out line for cold outbound when appropriate.
- For regulated or high-risk sectors, emphasize review, approvals, logs, and scoped pilots. Do not imply autonomous production decisions.

## Resource Guide

- `references/positioning.md`: load for offer framing, buyer pains, differentiators, proof rules, and compliance guardrails.
- `references/use-case-decision-table.md`: load when deciding which template fits a specific use case.
- `references/sequence-blueprints.md`: load for recommended cadences across cold outbound, warm outbound, inbound, proposal, closing, and post-sale.
- `references/email-catalog.md`: load for the near-exhaustive template library by stage.
- `references/template-index.json`: machine-readable template metadata used by the renderer.
- `scripts/render_email.py`: list templates or render a draft with placeholders.

## Renderer

Use the renderer for repeatable output or quick template discovery:

```bash
python3 scripts/render_email.py --list
python3 scripts/render_email.py --template cold-problem-pilot --var prospect_name=Alex --var company=Acme --var workflow="support triage"
```

If a user needs polished, context-aware copy, use the references and rewrite the rendered draft rather than returning raw placeholders.

## Rendering to a Branded PDF

Artifacts from this skill are delivered as branded CompleteTech LLC **PDF** documents, not raw Markdown. The renderer emits the PDF (and prints the Markdown) in **one command**, using the same reportlab branding engine as the contract skill:

```bash
pip install -r requirements.txt
python3 scripts/render_email.py --template cold-operations-bottleneck \
  --out artifact.pdf --png artifact.png \
  --title "Outbound Email Sequence" --doc-type "EMAIL DRAFTS — VERIFY BEFORE SENDING" \
  --subtitle "Prospect: <b>Northwind Trading Co.</b>" --meta "SEQUENCE=PRO-OUT-014" --meta "STAGE=Cold outreach" \
  --var client_name="Client Name" --var workflow="support triage"
```

- `--no-pdf` emits Markdown only (the original behavior); `--no-cover` drops the cover page.
- Already drafted the Markdown yourself? Render it directly: `python3 scripts/render_pdf.py --markdown artifact.md --out artifact.pdf --logo assets/logo.png --title "..."`.
- The PDF supports a Markdown subset: `#`/`##`/`###` headings, paragraphs, `-` bullets, tables, `>` callouts, `**bold**`, and `[PAGE_BREAK]`. PDF requires `reportlab`; the optional `--png` preview requires `pypdfium2` and `pillow`. See `assets/examples/` for a rendered example.
