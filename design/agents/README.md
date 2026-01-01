# Agent Definitions

This folder contains the persona definitions for all conference speakers, organized by thematic track.

## Track Overview

| Track | File | Agent Count |
|-------|------|-------------|
| 1. Industry Leadership | [01-industry-leadership.md](01-industry-leadership.md) | 6 |
| 2. Workers & Employees | [02-workers-employees.md](02-workers-employees.md) | 4 |
| 3. Industry Analysis | [03-industry-analysis.md](03-industry-analysis.md) | 1 |
| 4. Government & Public Sector | [04-government.md](04-government.md) | 3 |
| 5. AI Sentiment Spectrum | [05-ai-sentiment.md](05-ai-sentiment.md) | 3 |
| 6. Education | [06-education.md](06-education.md) | 3 |
| 7. Traditional Professions | [07-traditional-professions.md](07-traditional-professions.md) | 6 |
| 8. Children & Parenting | [08-children-parenting.md](08-children-parenting.md) | 3 |
| 9. AI Industry | [09-ai-industry.md](09-ai-industry.md) | 4 |
| 10. Upskilling & Training | [10-upskilling.md](10-upskilling.md) | 1 |
| 11. Security & Defense | [11-security-defense.md](11-security-defense.md) | 2 |
| 12. Geopolitical | [12-geopolitical.md](12-geopolitical.md) | 3 |
| 13. Finance | [13-finance.md](13-finance.md) | 5 |
| 14. Language & Localization | [14-language.md](14-language.md) | 1 |
| 15. Media & Publishing | [15-media-publishing.md](15-media-publishing.md) | 5 |
| 16. Religion | [16-religion.md](16-religion.md) | 2 |
| 17. Edge Cases | [17-edge-cases.md](17-edge-cases.md) | 2 |

**Total Agents: ~54** (V1 target: ~30-40 for manageable runtime)

## Agent Definition Format

Each agent definition includes:

```yaml
agent_id: unique identifier
name: "[Fictional Name]"
role: "[Title/Position]"
organization: "[Fictional Organization]"
track: "[Track Name]"
focus_areas:
  - Primary topic
  - Secondary topic
prompt_questions:
  - Question they should address
  - Another question
system_prompt_template: |
  You are [Name], [Role] at [Organization]...
```

## Implementation Notes

- Each agent needs a **credible fake identity** (name, organization, background)
- The orchestrator injects the identity into the system prompt
- Agents should speak naturally, as if at a real conference
- Speech length: ~450 words (3 minutes at average speaking rate)
