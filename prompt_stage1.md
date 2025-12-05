# Stage 1 Prompt - Key Events Extraction

## Purpose
Extract all significant events from raw article summaries without generating final summary. Stage 1 focuses purely on identifying and extracting key events.

## Input
Collection of article summaries (may be 100s or 1000s of entries)

## Core Instructions

### HIGH-IMPACT Information Priority
Focus on MARKET-MOVING information:
- Direct quotes from named individuals (CEOs, Fed officials, regulators, analysts, celebrities)
- Specific regulatory announcements, policy changes, legal actions
- Concrete financial figures, valuations, deal terms, earnings surprises
- **Uncertainty language**: "not 100% certain", "may", "might", "possibly", "unlikely"
- **Probability assessments** and confidence levels
- **Conditional statements**: "if X happens, then Y"

### Topic Priority Order
Cover topics in this order (omit categories not present):

1. **M&A (Mergers & Acquisitions)**
   - Deal amounts, valuations, financing details
   - Strategic rationale and timelines
   - Market impact and reactions
   
2. **Leadership Changes**
   - CEO/CFO/executive appointments and departures
   - Reasons for changes
   - Market reactions and implications
   
3. **Earnings & Financial Outlook**
   - Actual vs expected results
   - Guidance changes
   - Revenue surprises and margin shifts
   
4. **Legal & Regulatory Matters**
   - Lawsuits and investigations with amounts
   - Regulatory approvals/rejections
   - Penalties and settlements
   
5. **New Products & Technology**
   - Product launches with revenue impact
   - Patents and innovations
   - Market positioning and competitive advantages
   
6. **Thematic Trends**
   - AI/ML developments
   - ESG initiatives
   - Crypto/blockchain
   - Recession indicators
   - Sector shifts
   
7. **Regulatory Changes**
   - New laws and sanctions
   - Compliance requirements
   - Policy changes affecting sectors/companies
   
8. **Insider Transactions**
   - Significant insider buying/selling
   - Size, direction, timing, context
   
9. **Macroeconomic Factors**
   - Interest rates and inflation
   - FX movements
   - Geopolitical tensions affecting specific companies
   
10. **Named Person Statements**
    - Direct quotes with attribution
    - Predictions and forecasts
    - Market outlook with uncertainty levels

### Extraction Rules
- **MUST analyze ACTUAL data** - not generic statements
- Extract 15+ significant events
- Include BOTH frequent AND rare important topics
- Preserve exact quotes and attributions
- Keep specific numbers, dates, percentages
- Capture uncertainty and probability language
- Include context for why events matter

### Language Rules
- Write in same language as source articles
- If mixed languages, use dominant language
- Maintain technical terminology
- Preserve quoted statements in original language

## Output Format

Return only valid RFC 8259 JSON with exactly THREE fields:

```json
{
  "sector_id": "string",
  "generated_date": "YYYY-MM-DD",
  "key_events": [
    {
      "date": "YYYY-MM-DD",
      "event": "Detailed description with attribution, numbers, and uncertainty language"
    }
  ]
}
```

### Key Events Requirements
- Minimum 15 events
- Each event must include:
  - **date**: YYYY-MM-DD (or YYYY-MM if day unknown, YYYY if month unknown)
  - **event**: Detailed description including:
    - Who (named individuals/organizations)
    - What (specific action/statement)
    - Numbers/percentages when available
    - Attribution for claims
    - Uncertainty language if present

## Critical Reminders
- NO summary field in Stage 1 output (summary created in Stage 2)
- Extract from ACTUAL data, not examples
- Include diverse topics (crypto, tech, regulatory, etc.)
- Capture frequently-mentioned individuals and their statements
- Preserve uncertainty and probability statements
- Each event should be distinct and significant

## Example Output Structure
```json
{
  "sector_id": "factor",
  "generated_date": "2024-01-15",
  "key_events": [
    {
      "date": "2024-01-10",
      "event": "[Named Person] stated that [specific claim with uncertainty language like 'may' or 'possibly'], citing [specific numbers/data]"
    },
    {
      "date": "2024-01-08",
      "event": "Regulatory body announced [specific policy change] affecting [sector/companies], expected to [impact with probability language]"
    }
  ]
}
```

**Note**: Above is structure example only. Generate events from INPUT DATA.
