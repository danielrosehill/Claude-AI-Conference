# Implementation Methodology

This document outlines the technical approach for generating the AI Symposium 2026.

---

## Overview

The system follows a simple orchestration pattern:

```
┌─────────────────────────────────────────────────────────────────┐
│                        ORCHESTRATOR                              │
│  - Loads agent definitions                                       │
│  - Generates fictional identities                                │
│  - Distributes prompts to generation model                       │
│  - Collects outputs                                              │
│  - Passes to compilation layer                                   │
└─────────────────────────────────────────────────────────────────┘
                              │
                    ┌─────────┴─────────┐
                    ▼                   ▼
            ┌─────────────┐      ┌─────────────┐
            │  Agent 1    │ ...  │  Agent N    │
            │  Generation │      │  Generation │
            └─────────────┘      └─────────────┘
                    │                   │
                    └─────────┬─────────┘
                              ▼
            ┌─────────────────────────────────┐
            │        OUTPUT COMPILATION        │
            │  - PDF assembly                  │
            │  - TTS generation                │
            │  - Audio concatenation           │
            │  - Summary generation            │
            └─────────────────────────────────┘
```

---

## Phase 1: Agent Configuration

### 1.1 Load Agent Definitions

Read all agent definitions from `/design/agents/*.md` files.

For each agent, extract:
- `agent_id`
- `role`
- `track`
- `focus_areas`
- `prompt_questions`

### 1.2 Generate Fictional Identities

For each agent, the orchestrator generates a **credible fake identity**:

```yaml
name: "Dr. Sarah Chen"
organization: "Meridian Textiles Inc."
location: "Republic of Techland"
background: "15 years in HR, previously at Fortune 500 companies"
```

This identity is injected into the system prompt to ground the persona.

### 1.3 System Prompt Template

```
You are {name}, {role} at {organization}.

You've been invited to speak at "AI in 2026: Looking Forward," a symposium
gathering diverse perspectives on artificial intelligence.

Your task is to deliver a 3-minute speech (~450 words) from your perspective.

Context:
- Today is January 2026
- You're speaking to an audience of professionals from many fields
- Be authentic to your role and experience
- Share specific observations, not generalities
- Just be yourself—no excessive formalities needed

Your focus areas:
{focus_areas}

Questions to consider addressing:
{prompt_questions}

Deliver your speech now.
```

---

## Phase 2: Speech Generation

### 2.1 Model Selection

| Priority | Model | Notes |
|----------|-------|-------|
| Primary | Gemini 3 (with search) | Cost-effective, grounding essential |
| Fallback 1 | Tavily-augmented model | For grounding if Gemini unavailable |
| Fallback 2 | Perplexity | Alternative grounding source |

**Critical Requirement**: Search/grounding must be enabled.

Without grounding, the model will think it's 2024 and cannot reflect on 2025 events. This makes the speeches unrealistic and dated.

### 2.2 Speech Constraints

| Parameter | Value | Rationale |
|-----------|-------|-----------|
| Target length | ~450 words | 3 minutes at 150 wpm |
| Max length | 500 words | Buffer for natural variation |
| Min length | 400 words | Ensure substantive content |
| Temperature | 0.7-0.8 | Balance creativity and coherence |

### 2.3 Generation Loop

```python
for agent in agents:
    identity = generate_identity(agent)
    prompt = build_system_prompt(agent, identity)

    speech = llm.generate(
        prompt=prompt,
        search_enabled=True,  # CRITICAL
        max_tokens=700,
        temperature=0.75
    )

    outputs.append({
        "agent_id": agent.id,
        "identity": identity,
        "speech": speech,
        "track": agent.track
    })
```

---

## Phase 3: Output Compilation

### 3.1 PDF Generation

Structure:
```
[Title Page]
AI Symposium 2026: Looking Forward
Perspectives from a Diverse Range of Contributors

[For each agent]
---
Page N: Agent Introduction
  - Name and Role
  - Organization
  - Track
  - Brief description of their perspective

Page N+1: Speech
  - Full text of their speech
---

[End Matter]
- Summary (if generated)
- Agent index
```

### 3.2 Audio Generation (TTS)

#### Provider Selection

**Primary: Resemble AI**
- Large voice library
- High quality
- API access

**Voice Diversity**:
- Select ~30 distinct voice IDs
- Span different:
  - Genders
  - Ages
  - Accents
  - Vocal characteristics
- Assign voices to agents based on persona fit

#### Audio Structure

```
1. MC Introduction
   Voice: [Stable MC voice]
   Text: "Welcome to AI in 2026: Looking Forward..."

2. For each agent:
   a. [Pause: 1.5s]
   b. MC Introduction
      Voice: [MC voice]
      Text: "Our next speaker is {name}, {role} at {organization}.
             They'll be sharing perspectives on {focus}."
   c. [Pause: 1.0s]
   d. Agent Speech
      Voice: [Agent-specific voice]
      Text: [Generated speech]
   e. [Pause: 2.0s]

3. MC Closure
   Voice: [MC voice]
   Text: "Thank you to all our speakers. That concludes..."

4. [Optional] Summary
   Voice: [Narrator voice]
   Text: [Generated summary]
```

#### Audio Concatenation

Learned requirements:
- **Pauses are essential** between speeches
- Without pauses, speeches run back-to-back awkwardly
- Use consistent pause durations for professional feel

```python
final_audio = []
for segment in segments:
    final_audio.append(segment.audio)
    final_audio.append(silence(duration=segment.pause_after))

export(final_audio, "symposium_2026.mp3")
```

---

## Phase 4: Summary Generation

After collecting all speeches:

### 4.1 Summary Agent

```
You are a conference summarizer.

You've just heard {N} speakers at "AI in 2026: Looking Forward."

Below are all their speeches. Your task is to generate a comprehensive
10-minute summary (~1500 words) that:

1. Identifies key themes across speakers
2. Notes points of agreement and disagreement
3. Highlights surprising or notable perspectives
4. Synthesizes the overall picture of AI in 2026

Speeches:
{all_speeches}

Generate your summary.
```

### 4.2 Summary Output

- Generate text summary
- Convert to audio (single narrator voice)
- Append to main audio or create separate file

---

## Execution Checklist

### Pre-Flight
- [ ] Agent definitions complete
- [ ] Model API access confirmed
- [ ] TTS voice IDs selected
- [ ] Output directories created

### Generation
- [ ] Identity generation working
- [ ] Grounded search confirmed
- [ ] Speech length validation
- [ ] All agents processed

### Compilation
- [ ] PDF generated and reviewed
- [ ] TTS audio generated for each agent
- [ ] MC segments generated
- [ ] Pauses inserted correctly
- [ ] Audio concatenated
- [ ] Summary generated (optional)

### Quality Check
- [ ] Speeches are grounded in 2025/2026
- [ ] No hallucinated organizations referenced
- [ ] Voice diversity is evident
- [ ] Audio quality consistent
- [ ] PDF formatting clean

---

## Cost Estimation

Rough estimates (will vary by provider):

| Component | Units | Est. Cost |
|-----------|-------|-----------|
| Speech generation (Gemini 3) | ~40 agents × 500 tokens | ~$0.50 |
| TTS (Resemble AI) | ~40 × 450 words × 5 chars | ~$5-10 |
| Summary generation | 1 × ~2000 tokens | ~$0.05 |
| **Total** | | **~$6-12** |

"A very worthwhile use of a few dollars."

---

## Future Enhancements (V2+)

### Video Avatars
- TED-style stage background
- Avatar walks on, speaks, walks off
- Next avatar enters
- Requires:
  - Avatar generation platform
  - Lip-sync technology
  - Video composition pipeline

### Simpler Video
- Talking heads (more feasible)
- Static or minimal animation
- Less engaging but achievable

### Additional Agents
- Diplomatic corps / Foreign policy
- Scientific researchers
- Data analysts
- Aviation / Transport industry

---

*End of methodology document*
