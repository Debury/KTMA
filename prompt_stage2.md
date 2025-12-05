# Stage 2 Prompt - Quality Control and Deduplication

## Purpose
Takes key_events array from Stage 1 and validates quality. NO summary generation.

## Input
Array of key_events from Stage 1 (typically 15-20 events)

## Tasks
1. **DEDUPLICATE**: Remove events describing EXACT SAME occurrence
2. **VALIDATE**: Keep only high-quality, specific, fact-based events
3. **FILTER**: Remove generic statements without concrete facts

## Rules

### Deduplication
- Same person/EXACT SAME statement → keep only ONE (most detailed)
- EXACT SAME regulatory action/merger/earnings → keep only ONE
- **CRITICAL: Check for semantic duplicates** - events may use different words but describe the same fact
  * Example: "Lisa Su confirmed AMD deal with OpenAI" and "AMD CEO discussed OpenAI agreement" = SAME EVENT
  * Example: "Company announced Q1 earnings of $5M" and "Q1 results showed $5M revenue" = SAME EVENT
- Preserve attribution and uncertainty language in kept events
- Keep ALL events describing DIFFERENT occurrences

### Quality Validation
**KEEP** events with:
- Named individuals with specific statements/actions
- Concrete numbers, dates, percentages
- Specific company/regulatory actions
- Uncertainty language with attribution

**REMOVE** events that are:
- Generic sector trends without specifics
- Vague statements without attribution
- Duplicate information
- Low-impact routine operations

## Output Format
```json
{
  "sector_id": "string",
  "generated_date": "YYYY-MM-DD",
  "key_events": [
    {
      "date": "YYYY-MM-DD",
      "event": "detailed description with attribution and specifics"
    }
  ]
}
```

## Key Principles
- NO summary field in output
- NO artificial limit on event count
- Focus on quality and uniqueness, not quantity reduction
- Each event must be DISTINCT (no duplicates)
- Preserve all high-quality unique events
- Include specific attribution to named individuals
