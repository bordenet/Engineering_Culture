# Genesis Tools Integration Plan for Engineering_Culture

## Overview

This document maps where each Genesis assistant tool should be linked within the Engineering_Culture blog posts to provide readers with practical, deployed tools that implement the concepts discussed.

## Current State

**Already Linked:**
- ✅ `one-pager` - Linked in The_One-Pager.md (line 6)
- ✅ `pr-faq-assistant` - Linked in The_PR-FAQ.md (line 6)
- ✅ `pr-faq-assistant/validator` - Linked in The_PR-FAQ.md (line 7)
- ✅ `product-requirements-assistant` - Linked in Project_Planning_Mechanisms:_Documents.md (line 98)

**Tools Mentioned in AI Engineering:**
- ✅ All 6 tools mentioned in Building_an_AI-First_Engineering_Culture.md (line 45)

## Recommended Additions

### 1. Architecture Decision Record (ADR) Tool
**Tool:** https://bordenet.github.io/architecture-decision-record/  
**Repo:** https://github.com/bordenet/architecture-decision-record

**Where to Add:**

#### A. SDLC/Project_Planning_Mechanisms:_Documents.md
- **Section:** "Technical Design: The How" (around line 119)
- **Rationale:** ADRs are a specific type of technical design document for recording architectural decisions
- **Suggested Addition:**
  ```markdown
  > [!NOTE]
  > Document architectural decisions with [architecture-decision-record](https://bordenet.github.io/architecture-decision-record/) ([repo](https://github.com/bordenet/architecture-decision-record))
  ```

#### B. EngFundamentals/SOA_and_Microservices.md
- **Rationale:** Architectural decisions about SOA vs microservices should be documented
- **Suggested Location:** Near the end, in a "Documenting Your Decisions" section

### 2. Strategic Proposal Tool
**Tool:** https://bordenet.github.io/strategic-proposal/  
**Repo:** https://github.com/bordenet/strategic-proposal

**Where to Add:**

#### A. SDLC/Project_Planning_Mechanisms:_Documents.md
- **Section:** Add new row to "The Document Landscape" table (line 33)
- **Suggested Addition:**
  ```markdown
  | **Strategic Proposal** | Present strategic initiatives to leadership | Leadership/PM | "Should we invest in this direction?" | Major initiatives, platform decisions |
  ```
- **Also add:** New section after PR-FAQ explaining when to use Strategic Proposals vs PR-FAQs

#### B. Culture/People_-_Process_-_Technology_Triad.md
- **Rationale:** Strategic proposals often involve people/process/technology trade-offs
- **Suggested Location:** In examples of how to present strategic technology investments

### 3. Power Statement Assistant
**Tool:** https://bordenet.github.io/power-statement-assistant/  
**Repo:** https://github.com/bordenet/power-statement-assistant

**Where to Add:**

#### A. Culture/Professional_Writing_Tips.md
- **Section:** "Phase 1: Clarify Your Intent" (around line 40)
- **Rationale:** Power statements help clarify intent and purpose
- **Suggested Addition:**
  ```markdown
  > [!TIP]
  > Craft compelling power statements with [power-statement-assistant](https://bordenet.github.io/power-statement-assistant/) ([repo](https://github.com/bordenet/power-statement-assistant))
  ```

#### B. SDLC/Understanding_What_vs_How.md
- **Rationale:** Power statements focus on the "what" and "why" (outcomes), not the "how"
- **Suggested Location:** In examples of outcome-focused communication

### 4. Acceptance Criteria Assistant
**Tool:** https://bordenet.github.io/acceptance-criteria-assistant/  
**Repo:** https://github.com/bordenet/acceptance-criteria-assistant

**Where to Add:**

#### A. SDLC/Project_Planning_Mechanisms:_Documents.md
- **Section:** "PRD: The What and Why" → "Essential Elements" → "User Stories" (around line 105)
- **Suggested Addition:**
  ```markdown
  > [!NOTE]
  > Generate acceptance criteria with [acceptance-criteria-assistant](https://bordenet.github.io/acceptance-criteria-assistant/) ([repo](https://github.com/bordenet/acceptance-criteria-assistant))
  ```

### 5. Business Justification Assistant
**Tool:** https://bordenet.github.io/business-justification-assistant/  
**Repo:** https://github.com/bordenet/business-justification-assistant

**Where to Add:**

#### A. SDLC/Project_Planning_Mechanisms:_Documents.md
- **Section:** Add to "The Document Landscape" table
- **Suggested Addition:**
  ```markdown
  | **Business Justification** | Build financial case for initiatives | PM/Finance | "What's the ROI?" | Budget requests, resource allocation |
  ```

#### B. Culture/People_-_Process_-_Technology_Triad.md
- **Rationale:** Business justifications often require balancing people, process, and technology investments

### 6. Job Description Assistant
**Tool:** https://bordenet.github.io/jd-assistant/  
**Repo:** https://github.com/bordenet/jd-assistant

**Where to Add:**

#### A. Culture/People_-_Process_-_Technology_Triad.md
- **Section:** "People First" section
- **Rationale:** Hiring the right people starts with clear job descriptions
- **Suggested Addition:**
  ```markdown
  > [!NOTE]
  > Create effective job descriptions with [jd-assistant](https://bordenet.github.io/jd-assistant/) ([repo](https://github.com/bordenet/jd-assistant))
  ```

#### B. Culture/Understanding_Conways_Law.md
- **Section:** "Designing Teams for Your Desired Architecture"
- **Rationale:** Team structure starts with hiring the right roles

## Implementation Priority

### High Priority (Core SDLC Documents)
1. ✅ Architecture Decision Record → Project_Planning_Mechanisms:_Documents.md
2. ✅ Acceptance Criteria Assistant → Project_Planning_Mechanisms:_Documents.md
3. ✅ Strategic Proposal → Project_Planning_Mechanisms:_Documents.md

### Medium Priority (Culture Documents)
4. Power Statement Assistant → Professional_Writing_Tips.md
5. Job Description Assistant → People_-_Process_-_Technology_Triad.md
6. Business Justification Assistant → Project_Planning_Mechanisms:_Documents.md

### Low Priority (Engineering Fundamentals)
7. Architecture Decision Record → SOA_and_Microservices.md

## Notes

- All tools follow the same pattern: `[tool-name](https://bordenet.github.io/tool-name/) ([repo](https://github.com/bordenet/tool-name))`
- Use NOTE or TIP callouts to make links stand out
- Place links where they provide immediate practical value to readers
- Avoid over-linking - each tool should appear 1-2 times max in the entire collection

