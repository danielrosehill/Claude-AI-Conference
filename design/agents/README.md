# Agent Definitions

This folder contains persona definitions for all conference speakers, organized by thematic cluster.

## Cluster Overview

| Cluster | Folder | Description |
|---------|--------|-------------|
| Industry | [industry/](industry/) | Leadership and C-suite perspectives |
| Workforce | [workforce/](workforce/) | Employee and worker perspectives |
| Government | [government/](government/) | Public sector and policy |
| Education | [education/](education/) | Academic and training perspectives |
| Professions | [professions/](professions/) | Traditional professional fields |
| AI Perspectives | [ai-perspectives/](ai-perspectives/) | Industry insiders and sentiment spectrum |
| Finance | [finance/](finance/) | Financial services sector |
| Geopolitical | [geopolitical/](geopolitical/) | International and development |
| Media & Publishing | [media-publishing/](media-publishing/) | Content and journalism |
| Religion | [religion/](religion/) | Faith perspectives |
| Security & Defense | [security-defense/](security-defense/) | Military and intelligence |
| Children & Parenting | [children-parenting/](children-parenting/) | Family and youth |
| Edge Cases | [edge-cases/](edge-cases/) | Unusual perspectives |

## Agent Definition Format

Each agent file contains:

```yaml
agent_id: unique identifier
role: "[Title/Position]"
organization: "[TBD - Fictional Organization]"
cluster: "[Cluster Name]"

focus_areas:
  - Primary topic
  - Secondary topic

prompt_questions:
  - Question they should address
  - Another question

notes: |
  Additional context for this persona
```

## Implementation Notes

- Each agent needs a **credible fake identity** generated at runtime
- The orchestrator injects identity into the system prompt
- Agents speak naturally, as if at a real conference
- Speech length: ~450 words (3 minutes at average speaking rate)
- Speaking order is determined at runtime, not by file structure
