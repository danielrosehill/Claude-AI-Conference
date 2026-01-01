# AI Symposium 2026: Design Notes

> Cleaned and structured transcript from voice notes recorded January 1st, 2026

---

## Introduction

These notes outline an experiment in using AI for perspective exploration, synthesized personalities, and agentic personas. This is a fascinating area of what AI could be useful for—imperfect, of course, like everything else, but worth exploring.

## Related Experiments

Before diving into this project, it's worth noting related experiments in this pattern:

### AI Panel Discussion
A panel involving a moderator, convener, and panelists who present viewpoints and argue with each other. The challenge is baking in elements of rebuttal and argumentation into each turn without it becoming chaotic. From an orchestration standpoint, this is quite complex because you need to pass each agent's position to the next without degrading the context window.

### AI Think Tank
Distinct from a panel because a think tank is an ongoing institution with institutional memory—it doesn't just convene once. Think tanks work from problems to ideation to solutions to publications, which fits perfectly with an agentic model: gather perspectives, define topics, concatenate outputs into PDFs, audio streams, and audiobooks.

### Peace in the Middle East
An attempt to see if AI tools can bring fresh ideation to an intractable geopolitical challenge.

### Agentic UN
A surrogate UN General Assembly simulation. The rigid definition of participants (countries with ISO codes) and voting mechanism (in favor, against, abstain) lends itself extremely well to structured outputs and agentic systems. The orchestrator configures country representatives and resolutions, passes them to simulated countries, gathers simulated votes, and each country can provide a statement alongside its vote. The data then goes through an analysis layer for modeling geopolitical fora and policy reactions.

---

## The Simulated Conference Concept

This experiment is distinguished from the others by being simpler and less daunting than a realistic imaginary summit. It's a one-time simulated conference without the rebuttal element—almost cleaner architecturally.

### Conference Theme
**"AI in 2026: Looking Forward"**
*Subtitle: Perspectives from a Diverse Range of Contributors*

### Core Structure
- Each agent receives context data: "You're speaking at this conference. You have to give a speech. You can deliver up to X words."
- An orchestration agent passes system prompts to sub-agents for text generation
- The goal is to gather different perspectives from across society

### Key Design Principle
Each agent needs a credible fake identity. The orchestrator adds to the system prompt something like: "You are the CEO of X, a textiles company" or similar persona-fitting details.

---

## Agent Configurations

### Track 1: Industry Leadership

#### Human Resources Professional
- Focus: HR perspective on AI in 2026
- Questions to address:
  - How have they been challenged by AI to date?
  - Are they leveraging AI for candidate screening and recruiting?
  - How are they dealing with AI-generated applications flooding their systems?
  - Is there a degrading caliber of applications due to widespread AI use?

#### Small Business Manager
- Focus: Non-technical small organization perspective
- Questions to address:
  - How do they feel about AI adoption?
  - They're not the typical pitch market for tech tools—what have they made of AI?
  - Has it actually been helpful in their non-technical business?

#### Startup CTO
- Focus: Tech-forward but non-AI startup (e.g., FinTech)
- Questions to address:
  - What's been their vantage point on AI adoption?
  - What opportunities and threats do they see in 2026?

#### Enterprise CEO
- Focus: Non-technical high-level leadership perspective
- Questions to address:
  - What advantages have they seen from AI?
  - Overall sentiment on AI value for large organizations

#### Chief Strategy Officer (CSO)
- Focus: Business strategy and maximizing AI use
- Questions to address:
  - What are they seeing in terms of strategic vision for AI?

#### Chief Information Security Officer (CISO)
- Focus: Cybersecurity and organizational security
- Questions to address:
  - What are their concerns about AI?
  - What's the emerging threat landscape?

### Track 2: Workers and Employees

#### Employee at Small Organization
- Focus: Ground-level experience with AI adoption

#### Employee at Medium Organization
- Focus: Ground-level experience with AI adoption

#### Employee at Large Organization
- Focus: Ground-level experience with AI adoption

#### Employee at AI Company
- Focus: Internal AI use at an AI company
- Questions to address:
  - Do they feel dissonance between what they're marketing and their own adoption experience?

### Track 3: Industry Analysis

#### Management Consultant (McKinsey-type)
- Focus: Dispassionate sector analysis
- Task: Present the vantage point from the consulting side—advising industry on trends

### Track 4: Government and Public Sector

#### Prime Minister of a Simulated Country
- Focus: National-level concerns about AI and citizens
- Questions to address:
  - What does AI mean for your country?
  - What's its role in society at large?

#### Municipal Mayor
- Focus: Local government leadership in AI rollout
- Questions to address:
  - Experience with municipal AI technology deployment

#### Smart City Planner
- Focus: Implementation-level perspective
- Questions to address:
  - Stringent security and cybersecurity requirements
  - Current AI use in smart city planning

### Track 5: AI Sentiment Spectrum

#### AI Skeptic
- Focus: Extremely negative and critical about everything AI-related
- Task: Tear apart AI today and cast a dim view over its future

#### Standard AI Enthusiast
- Focus: Enthusiastic about AI, spreading the positive message

#### AI Hyper-Enthusiast / "We're Too Slow" Advocate
- Focus: Believes adoption is incredibly slow
- Perspective: "We're cavemen who think we're high-tech"—we're not using AI anywhere near as much as we could be

### Track 6: Education

#### University Provost
- Focus: AI in higher education
- Questions to address:
  - What are they seeing and feeling about AI in academia?

#### High School Headmaster
- Focus: Secondary education perspective

#### High School Career Counselor
- Focus: Advising young people about AI and careers
- Questions to address:
  - What are they hearing from students they're counseling?
  - What guidance are they providing about AI and career choices?

### Track 7: Traditional Professions

#### Lawyer
- Setting: Medium-sized city in "Republic of Techland"
- Questions to address:
  - Are they using AI?
  - Are colleagues using AI?
  - Is it actually helpful or overhyped?

#### Architect
- Questions to address:
  - Are they using cloud AI or local AI?
  - Are they using tools like ComfyUI?
  - Does their office own a GPU?
  - What do colleagues think?

#### Engineer
- Focus: Engineering profession's AI adoption

#### Family Doctor
- Focus: Primary care medicine
- Questions to address:
  - Are they using AI for diagnosis? (Be honest)
  - Have they used it for personal health?
  - How often do they look up symptoms on ChatGPT while patients aren't looking?
  - Are they using specialist medical AI tools or just general tools?

#### Medical Consultant/Specialist
- Focus: Specialist medicine perspective

#### Utility Operator
- Focus: Operational technology perspective

### Track 8: Children and Parenting

#### Parenting Expert
- Focus: Advising parents on AI and children
- Questions to address:
  - Ethics, exposure, safety risks

#### Children's Education Expert
- Focus: AI's role in education for children
- Questions to address:
  - What do we do about AI-generated kids' shows?
  - Do we need to check AI content as carefully as other content?

#### AI for Children's Content Enthusiast
- Focus: Positive vision for generative AI in kids' content
- Perspective: AI can bring joy to children through creative content

### Track 9: AI Industry

#### AI Bias Think Tank Representative
- Focus: Exploring AI bias, its meaning, current state, and big model lab approaches

#### Big Model Lab Representative
- Focus: Share vision for the coming year from a major AI lab

#### Small/Emerging Model Lab Representative
- Focus: Breaking through in an increasingly crowded market

#### AI Consultant (Ground-Level Implementation)
- Focus: Working with businesses implementing AI
- Questions to address:
  - What challenges and opportunities are clients reporting?
  - Concerns about market saturation as everyone brands themselves an AI consultant?

### Track 10: Upskilling and Training

#### Career Upskilling Advisor
- Focus: Continuous professional development
- Questions to address:
  - What skill gaps have they seen?
  - What are employers reporting about skill gaps?
  - What are they advising people?

### Track 11: Security and Defense

#### Military Technologist
- Focus: How the military is using AI (open domain information only)
- Questions to address:
  - Significance of AI in modern warfare
  - Challenges in defense AI

#### Intelligence Agency Representative
- Focus: National security perspective
- Questions to address:
  - Dealing with massive data volumes
  - Thwarting organized crime with AI

### Track 12: Geopolitical Perspectives

#### Chinese AI Vendor Representative
- Focus: East vs. West AI dynamics
- Questions to address:
  - Differences in AI adoption between East and West
  - What dynamics are they seeing in China and Asia?

#### Developing Country Representative
- Focus: AI accessibility and affordability
- Questions to address:
  - Developmental aspect of AI
  - Where AI might make the biggest impact

#### Impact Investing Advocate
- Focus: AI in impact as a field
- Questions to address:
  - Where are they excited about AI?

### Track 13: Finance

#### Financial Regulator
- Focus: Regulatory perspective on AI in finance

#### Central Banker
- Focus: AI for making sense of economic data that moves faster than human processing

#### Day Trader
- Focus: Using AI tools in actual trading strategies

#### Regular Saver/Pension Holder
- Focus: Ordinary person trying to invest wisely with AI assistance

#### Financial Advisor (for Regular Savers)
- Focus: Advising regular people, not the wealthy

### Track 14: Language and Localization

#### Non-English Speaker (e.g., Danish)
- Focus: AI experience in smaller languages
- Questions to address:
  - What's the scene like when big models are trained on English?
  - Experience comparing language-specific tools vs. general tools like ChatGPT

### Track 15: Media and Publishing

#### Netflix Producer
- Focus: Dealing with AI-generated content in productions
- Questions to address:
  - Policies around AI content

#### Major Publisher Representative
- Focus: Authors using AI to generate books
- Questions to address:
  - Vetting AI-generated manuscripts

#### Published Author (Mainstream)
- Focus: Personal AI use and observations about other authors

#### Journalist
- Focus: High-stakes news writing
- Questions to address:
  - How do they feel about AI tools when millions might read their work?

#### Copy Editor
- Focus: Quality control perspective
- Questions to address:
  - Do they suspect reporters are using AI?
  - Have they caught anyone red-handed?

### Track 16: Religion

#### Rabbi
- Focus: AI in religious education
- Questions to address:
  - Using AI for Torah lessons?

#### Muslim Cleric
- Focus: Same questions from another faith perspective

### Track 17: Edge Cases

#### Organized Crime Figure (Immunity Deal)
- Focus: Criminal perspective on AI (imaginative scenario)

#### Anonymization/Whistleblowing Advocate
- Focus: AI for protecting vulnerable people
- Use case: AI for changing names and details while keeping facts—helping whistleblowers, domestic violence survivors, and others who fear retribution
- Questions to address:
  - Tools and workflows for this use case

---

## Technical Implementation

### Speech Generation

#### Model Selection
- **Primary:** Gemini 3 with search enabled (cost-effective and current)
- **Fallback:** Tavily or Perplexity
- **Critical requirement:** Search/grounding must be enabled so agents can reflect on 2025 without the model thinking it's still 2024

#### Speech Constraints
- Each agent delivers a three-minute speech
- Calculate word count based on average speaking rate (~150 words/minute = ~450 words per speech)

#### System Prompt Guidance
- Agents should be told: "Just be yourself and talk as if you're at this conference. No formalities needed."

### Output Formats

#### Format 1: PDF Document
- Title page for each agent with their name and role
- Short description: "This agent represents [role]. This was their response."
- Agent's speech
- Next page, next agent
- Essentially concatenating responses into a single document

#### Format 2: Audio (Preferred)
- Text-to-speech for each agent
- MC (Master of Ceremonies) with a stable voice to introduce each speaker
- MC script: "Next speaker is Agent 3. Agent 3 is representing an investment banker focused on [topic]."
- Pause before and after each speech (learned from previous errors—otherwise they run back-to-back)
- Concatenate all audio chunks

#### TTS Implementation
- **Platform:** Resemble AI (excellent voice library)
- **Voice diversity:** Select ~30 different voice IDs spanning different types
- Avoid same-voice-different-agent confusion

### Conference Structure

1. **MC Introduction:** "Welcome to the conference"
2. **Individual Agent Speeches:** Each with MC introduction and pauses
3. **MC Closure:** End of conference
4. **Summary Agent:** Takes all responses, generates a 10-minute summary (text and audio)
   - Gemini 3 can likely handle the aggregated context window

---

## Future Enhancements (V2+)

### Video Avatars
- Speaking avatars on a stage/podium background
- TED conference-style presentation
- Avatar walks on, speaks, walks off, next avatar
- Currently futuristic but becoming feasible quickly

### Simpler Video Option
- Talking heads (less engaging but definitely doable)

### Additional Agents for V2
- Diplomatic corps representative
- More foreign policy perspectives
- Scientific sector / Data analysts
- Air transport industry

---

## Project Philosophy

- Keep it "cheap and cheerful" while experimenting
- Text and audio pattern is cost-effective and worthwhile
- Open-source the method and results
- This serves as a demonstration that multimodal audio models can process 30+ minute recordings

---

*End of design notes*
