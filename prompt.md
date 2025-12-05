Take a deep breath.# AI Summarization Prompt for Financial/Market DataTake a deep breath.

Your task is to produce a precise, fact-focused summary of the provided sector information. The input contains summaries of multiple companies and statements from officials/analysts; consolidate overlaps and remove repetition. Use only information present in the text—do not infer or add external facts.

Your task is to produce a precise, fact-focused summary of the provided article text. The input may itself be a summary of multiple sources; consolidate overlaps and remove repetition. Write in the same language as the article (if mixed, use the dominant language). Use only information present in the text—do not infer or add external facts.

**CRITICAL PRIORITY: Focus on HIGH-IMPACT, MARKET-MOVING information:**

- Direct quotes and statements from named individuals (CEOs, Fed officials, regulators, analysts, celebrities, influencers)## Core Instructions

- Specific regulatory announcements, policy changes, or legal actions

- Concrete financial figures, valuations, deal terms, earnings surprisesPrioritize financial and market-moving content. When multiple topics appear, cover them in this order (omit categories not present):

- Uncertainty language: "not 100% certain", "may", "might", "possibly", "unlikely", "expected to"

- Probability assessments and confidence levels when mentionedTake a deep breath.

- Conditional statements: "if X happens, then Y"

- Tentative policy positions subject to changeM&A (acquisitions/mergers) — deal terms, valuations, financing, approvals/closing.



**What to PRIORITIZE (in order):**Your task is to produce a precise, fact-focused summary of the provided sector information. The input contains summaries of multiple companies and statements from officials/analysts; consolidate overlaps and remove repetition. Use only information present in the text—do not infer or add external facts.

1. **Named person statements** — ANY statement by a named individual (executives, officials, analysts, influencers) with exact attribution. Include uncertainty/probability language.

2. **Regulatory & policy changes** — New laws, crypto regulations, sanctions, compliance requirements; note if tentative or under reviewLeadership changes — CEO/CFO/key executives, stated reasons, immediate implications/market reaction.

3. **M&A with specific terms** — Deal amounts, valuations, financing details, timelines

4. **Leadership changes** — CEO/CFO/executive moves with reasons and market reaction## CRITICAL PRIORITY: Focus on HIGH-IMPACT, MARKET-MOVING information

5. **Earnings surprises** — Actual vs expected, guidance changes, margin shifts

6. **Legal actions** — Lawsuits, investigations, penalties with amounts and partiesEarnings and outlook — revenue, profit/loss, y/y or q/q growth, margins, guidance.

7. **Product launches with revenue impact** — Not just announcements, but financial projections

8. **Insider transactions** — Size, direction, timing, context- Direct quotes and statements from named individuals (CEOs, Fed officials, regulators, analysts, celebrities, influencers)

9. **Macro factors with sector impact** — Rates, inflation, FX affecting specific companies

- Specific regulatory announcements, policy changes, or legal actionsLegal and regulatory — lawsuits, investigations, approvals/denials, licenses, penalties.

**What to AVOID:**

- Generic sector trends without specific companies/numbers- Concrete financial figures, valuations, deal terms, earnings surprises

- Vague statements like "companies are facing challenges"

- Broad thematic observations without concrete facts- Uncertainty language: "not 100% certain", "may", "might", "possibly", "unlikely", "expected to"New products/technology — launches, patents, milestones, effect on revenue/KPIs.



**Attribution & Nuance:** ALWAYS include WHO said/announced something (full name if available). Preserve the exact degree of certainty/uncertainty. Prioritize individuals who appear frequently in the data.- Probability assessments and confidence levels when mentioned



Explicitly capture drivers and attribution. Preserve numbers, units, currencies, tickers, timeframes exactly as written (no conversions). If conflicting figures exist, note the discrepancy or range.- Conditional statements: "if X happens, then Y"Hot thematic trends — AI, ESG, crypto, recession; specify firm/sector impact.



Sector {sector_id} contains {len(summaries)} company summaries covering various businesses.- Tentative policy positions subject to change



**CRITICAL INSTRUCTION:** Scan ALL {len(summaries)} summaries for:Regulatory changes — new laws/sanctions and expected sector/firm impact.

- Any mention of named individuals (executives, officials, analysts, influencers)

- Specific dollar amounts, percentages, dates## What to PRIORITIZE (in order)

- Direct quotes or paraphrased statements

- Policy announcements or regulatory changesSignificant insider transactions — size, direction (buy/sell), timing/context.



IMPORTANT: You MUST analyze the ACTUAL data provided below. Do not generate generic market commentary.1. **Named person statements** — ANY statement by a named individual (executives, officials, analysts, influencers) with exact attribution. Include uncertainty/probability language.



{context}2. **Regulatory & policy changes** — New laws, crypto regulations, sanctions, compliance requirements; note if tentative or under reviewMacro factors — rates, inflation, FX, commodities, geopolitics affecting markets.



Return only valid RFC 8259 JSON with exactly FOUR fields in this order:3. **M&A with specific terms** — Deal amounts, valuations, financing details, timelines



sector_id — echo "{sector_id}" exactly as given4. **Leadership changes** — CEO/CFO/executive moves with reasons and market reactionExplicitly capture drivers and attribution when stated (e.g., “a regulator/celebrity/executive comment led to a crypto sell-off,” “ETF flows accelerated gains,” “a protocol exploit triggered liquidations”). Preserve numbers, units, currencies, tickers, and timeframes exactly as written (no conversions). If the text presents conflicting figures, briefly note the discrepancy or range. If financial details are absent, summarize the core who/what/when/where/why/how. Keep sentences concise and merge closely related details; there is no fixed sentence limit—be succinct but complete.

generated_date — use today's date: "{datetime.now().strftime('%Y-%m-%d')}"

summary — a detailed string consolidating the most critical developments from the ACTUAL data above. Must reference specific named individuals, companies, financial figures, and real events from the input.5. **Earnings surprises** — Actual vs expected, guidance changes, margin shifts

key_events — an array of exactly 15 strings, each describing ONE specific, high-impact event from the actual data. Each event MUST include: (1) Named person/company, (2) Specific action/statement, (3) Numbers/dates if available, (4) Context. Prioritize statements from frequently-mentioned individuals. Format: 2-3 detailed sentences per event.

6. **Legal actions** — Lawsuits, investigations, penalties with amounts and partiesReturn only valid RFC 8259 JSON with exactly two fields in this order:

No other fields. No code fences or extra text.

7. **Product launches with revenue impact** — Not just announcements, but financial projections

Example output format (use ACTUAL names/data from input, not these examples):

{8. **Insider transactions** — Size, direction, timing, contextsector_id — echo the provided {sector_id} exactly as given (do not modify).

    "sector_id": "{sector_id}",

    "generated_date": "{datetime.now().strftime('%Y-%m-%d')}",9. **Macro factors with sector impact** — Rates, inflation, FX affecting specific companies

    "summary": "[100-200 word summary with real names, companies, and figures from the actual input data]",

    "key_events": [summary — a single string containing the consolidated summary.

        "[Person's actual name from data] stated/announced [specific action with real numbers/dates]. [Additional detail]. [Impact].",

        "[Company's actual name] reported [metric] of [amount] on [date], [change %], driven by [reason]. [Context].",## What to AVOID

        "[Official's actual name] indicated '[uncertainty language]' regarding [topic], suggesting [implication]. [Context].",

        "[Executive's actual name] from [Company] commented on [event with specifics]. [Details]. [Outcome].",If a detail (e.g., date or number) is not in the text, omit it rather than guessing. Properly escape any quotes or special characters so the JSON is valid. Do not include code fences or any extra text.

        "[Analyst/Influencer name] mentioned [statement with numbers/dates]. [Context]. [Significance].",

        "...10 more events - ALL must use actual names, companies, numbers, and dates from the input data above..."- Generic sector trends without specific companies/numbers

    ]

}- Vague statements like "companies are facing challenges"Inputs:


- Broad thematic observations without concrete facts

{sector_id}

## Attribution & Nuance

{text}

ALWAYS include WHO said/announced something (full name if available). Preserve the exact degree of certainty/uncertainty. Prioritize individuals who appear frequently in the data.

Output shape (example only; replace with your result):

Explicitly capture drivers and attribution. Preserve numbers, units, currencies, tickers, timeframes exactly as written (no conversions). If conflicting figures exist, note the discrepancy or range.{

"sector_id": "6",

## CRITICAL INSTRUCTION"summary": "Text of summary."

}
Scan ALL summaries for:
- Any mention of named individuals (executives, officials, analysts, influencers)
- Specific dollar amounts, percentages, dates
- Direct quotes or paraphrased statements
- Policy announcements or regulatory changes

IMPORTANT: You MUST analyze the ACTUAL data provided below. Do not generate generic market commentary.

## Output Format

Return only valid RFC 8259 JSON with exactly FOUR fields in this order:

- **sector_id** — echo the sector_id exactly as given
- **generated_date** — use today's date in YYYY-MM-DD format
- **summary** — a detailed string consolidating the most critical developments from the ACTUAL data above. Must reference specific named individuals, companies, financial figures, and real events from the input.
- **key_events** — an array of exactly 15 strings, each describing ONE specific, high-impact event from the actual data. Each event MUST include: (1) Named person/company, (2) Specific action/statement, (3) Numbers/dates if available, (4) Context. Prioritize statements from frequently-mentioned individuals. Format: 2-3 detailed sentences per event.

No other fields. No code fences or extra text.

## Example Output Format

**Note:** Use ACTUAL names/data from input, not these examples

```json
{
    "sector_id": "example_sector",
    "generated_date": "2025-11-07",
    "summary": "[Detailed summary with real names, companies, and figures from the actual input data]",
    "key_events": [
        "[Person's actual name from data] stated/announced [specific action with real numbers/dates]. [Additional detail]. [Impact].",
        "[Company's actual name] reported [metric] of [amount] on [date], [change %], driven by [reason]. [Context].",
        "[Official's actual name] indicated '[uncertainty language]' regarding [topic], suggesting [implication]. [Context].",
        "[Executive's actual name] from [Company] commented on [event with specifics]. [Details]. [Outcome].",
        "[Analyst/Influencer name] mentioned [statement with numbers/dates]. [Context]. [Significance].",
        "...10 more events - ALL must use actual names, companies, numbers, and dates from the input data above..."
    ]
}
```

## Key Points to Remember

- **15 key_events total** - not 10, not 12, exactly 15
- **Real names only** - no placeholders like "Company A" or "Executive B"
- **Preserve uncertainty** - "may", "not certain", "possibly", "expects to"
- **Numbers matter** - include all dollar amounts, percentages, dates
- **Attribution is critical** - always say WHO made the statement
- **Frequently mentioned = important** - if someone appears many times in the data, they MUST be in key_events
