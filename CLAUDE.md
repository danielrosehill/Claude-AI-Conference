# AI Symposium 2026 — Project Context

## Project Overview

This is an experiment in **agentic perspective synthesis**: simulating a tech conference where AI agents, each embodying a distinct persona, deliver speeches on "AI in 2026: Looking Forward."

## Core Architecture

### Orchestration Pattern
```
┌─────────────────────┐
│  Orchestrator Agent │
│  (distributes prompts)
└──────────┬──────────┘
           │
     ┌─────┴─────┐
     ▼           ▼
┌─────────┐ ┌─────────┐
│ Agent 1 │ │ Agent N │  ... (30+ agents)
│ (HR Pro)│ │ (Rabbi) │
└────┬────┘ └────┬────┘
     │           │
     └─────┬─────┘
           ▼
┌─────────────────────┐
│   Output Compiler   │
│   (PDF / Audio)     │
└─────────────────────┘
```

### Key Design Decisions

1. **No Rebuttal**: Unlike a panel, agents don't respond to each other. This keeps context windows clean and implementation simple.

2. **Credible Fakes**: Each agent receives a fictional identity (e.g., "CEO of Meridian Textiles") to ground their perspective.

3. **Grounded Generation**: Must use an LLM with search/grounding (Gemini 3 preferred) so agents can reference 2025 events.

4. **3-Minute Speeches**: ~450 words per agent, keeping content focused and total runtime manageable.

## Directory Structure

```
/design/
  agents/           # Agent persona definitions by track
  methodology.md    # Implementation approach and pipeline

/notes/
  notes.mp3                          # Original voice recording
  agentic-ai-panel-and-experiment-design.md  # Verbatim transcript
  voice-note.md                      # Lightly cleaned transcript
  design-notes-cleaned.md            # Fully structured transcript

/output/            # Generated outputs (future)
/src/               # Implementation code (future)
```

## Implementation Notes

### Text Generation
- **Model**: Gemini 3 with search enabled (essential for grounding)
- **Fallback**: Tavily or Perplexity for grounding
- **Prompt Style**: "Just be yourself and talk as if you're at this conference. No formalities needed."

### Audio Generation
- **TTS Provider**: Resemble AI (large voice library)
- **Voice Diversity**: ~30 unique voices to differentiate agents
- **MC Voice**: Stable voice for introductions between speakers
- **Pauses**: Required between speeches to avoid back-to-back audio

### Output Compilation
- **PDF**: Title page per agent → description → speech → next page
- **Audio**: MC intro → pause → agent speech → pause → repeat → summary

## Agent Categories (Tracks)

1. Industry Leadership (HR, SMB, Enterprise, C-Suite)
2. Workers and Employees (Small/Medium/Large/AI company)
3. Industry Analysis (Consultants)
4. Government (National, Municipal, Smart City)
5. AI Sentiment (Skeptic, Enthusiast, Hyper-Enthusiast)
6. Education (University, High School, Career Counseling)
7. Traditional Professions (Law, Architecture, Medicine, Engineering)
8. Children and Parenting (Experts, Content Creators)
9. AI Industry (Labs, Consultants, Bias Researchers)
10. Upskilling and Training
11. Security and Defense (Military, Intelligence)
12. Geopolitical (East/West, Developing Countries, Impact)
13. Finance (Regulators, Traders, Advisors)
14. Language and Localization (Non-English perspectives)
15. Media and Publishing (Streaming, Books, Journalism)
16. Religion (Multi-faith perspectives)
17. Edge Cases (Whistleblowing, Anonymization)

## Future Extensions

- **V2**: Video avatars (TED-style stage presentation)
- **Diplomatic track**: Foreign policy perspectives
- **Scientific track**: Researchers, data scientists
- **Aviation/Transport**: Real-time operational AI

## Working With This Project

When implementing:
1. Start with the agent definitions in `/design/agents/`
2. Follow the pipeline in `/design/methodology.md`
3. Use grounded LLM calls (search-enabled)
4. Compile outputs to both PDF and audio formats
5. Generate summary after all speeches complete
