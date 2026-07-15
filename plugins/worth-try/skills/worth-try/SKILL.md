---
name: worth-try
description: Evaluate whether a company or job offer is worth taking, compare competing offers, and surface role, team, compensation, company-health, culture, and personal-fit tradeoffs. Use when Codex is asked to decide "should I join this company?", "which offer should I choose?", "is this offer worth it?", "what red flags should I check?", or to assess accept/reject, negotiation, career-growth, risk, workload, manager, public-company financials, earnings reports, startup funding rounds, runway, investors, internship offers, full-time offers, new-grad offers, return offers, or company-fit questions for an employment opportunity.
---

# Worth Try

## Overview

Use this skill to turn an offer or company-joining decision into a structured decision aid. Default to bilingual Chinese-English output unless the user requests another language, combine user context with current public research when available, and clearly separate evidence, inference, unknowns, and confidence.

This skill is not legal, financial, immigration, tax, or mental-health advice. Treat the result as a decision memo that helps the user ask better questions and choose deliberately.

## Workflow

1. Classify the decision.
   - Single offer: decide accept, reject, negotiate, or investigate further.
   - Multiple offers: compare options using the same rubric and highlight decisive deltas.
   - Company-only check: assess whether the company seems worth pursuing, with lower confidence if offer/team details are missing.
   - Company stage: identify whether the company is public, private late-stage, early startup, subsidiary, agency/consultancy, or unknown; use stage-specific research signals.
   - Offer type: identify whether the opportunity is internship, return offer, new-grad full-time, experienced full-time, contract, or ambiguous; use offer-type-specific scoring.

2. Gather only decision-critical missing context.
   - Ask concise follow-up questions when the company, role, location, seniority, compensation, offer type, timing, internship duration, return-offer path, visa/relocation constraints, or competing options are missing.
   - If enough context exists to proceed, continue with explicit assumptions instead of blocking.
   - Do not put private personal details, compensation documents, names of non-public interviewers, or sensitive constraints into web searches.

3. Research real companies when current public information matters.
   - Read [research-checklist.md](references/research-checklist.md) before researching.
   - Browse current public sources unless the user explicitly asks not to or web access is unavailable.
   - Prefer primary and dated sources; cite sources used in the final answer.
   - If browsing is unavailable, say so and lower confidence.

4. Score and reason.
   - Read [evaluation-rubric.md](references/evaluation-rubric.md) before scoring.
   - Use the balanced default weights unless the user states a different career strategy.
   - Mark unknowns as unknown; do not invent precision.
   - Red flags can cap or override a high average score.

5. Produce the decision memo.
   - Give a clear recommendation, but preserve nuance when evidence is thin.
   - Explain the decisive tradeoffs and what new information would change the answer.
   - Include negotiation levers and questions to ask recruiter, hiring manager, future manager, and current or former employees.

## Output Contract

Default to Chinese first with concise English labels in headings or table columns. Use this shape:

- **结论 / Recommendation**: accept, reject, negotiate, pursue, pause, or choose offer A/B, with confidence.
- **公司阶段与资金面 / Stage and Financial Snapshot**: public-company financials or startup funding/runway signals when relevant.
- **Offer 类型 / Internship vs Full-Time Lens**: distinguish internship, return offer, new-grad, and full-time decision logic.
- **评分表 / Scorecard**: weighted dimensions, scores, evidence, unknowns, and risk notes.
- **红黄绿灯 / Risk Lights**: green strengths, yellow uncertainties, red flags.
- **关键取舍 / Decisive Tradeoffs**: what matters most for this user.
- **谈判杠杆 / Negotiation Levers**: compensation, title, scope, location, start date, equity refresh, severance, manager access, or written commitments.
- **待追问 / Questions to Ask**: specific questions for recruiter, hiring manager, future manager, and employees.
- **资料与置信度 / Sources and Confidence**: cite researched sources with dates; state low/medium/high confidence and why.

For multiple offers, include a side-by-side comparison and call out whether the score gap is decisive or preference-sensitive.

## Guardrails

- Do not treat the weighted score as objective truth; use it to make tradeoffs visible.
- Do not average away severe unresolved risks such as unpaid wages, unethical work, materially misleading recruiter claims, unstable immigration support, abusive manager signals, or a business model the user cannot tolerate.
- Do not advise breaching NDAs, misrepresenting competing offers, or sharing confidential employer information.
- If the user asks for a final decision with too little information, give a provisional recommendation and list the smallest set of questions that could change it.
- Use exact dates for "latest", "recent", "today", or time-sensitive claims.

## Resources

- [evaluation-rubric.md](references/evaluation-rubric.md): scoring dimensions, default weights, score interpretation, and red-flag caps.
- [research-checklist.md](references/research-checklist.md): source hierarchy, search patterns, currentness checks, and citation rules for public company research.
