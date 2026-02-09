# Genesis Tools Integration Implementation Plan

> **For Claude:** REQUIRED SUB-SKILL: Use superpowers:executing-plans to implement this plan task-by-task.

**Goal:** Add contextually appropriate links to deployed Genesis assistant tools throughout Engineering_Culture blog posts

**Architecture:** Add NOTE/TIP callouts with tool links at specific locations where tools provide immediate practical value to readers. Follow existing voice and professionalism - zero selling language.

**Tech Stack:** Markdown, str-replace-editor

---

## Task 1: Add Architecture Decision Record to Project_Planning_Mechanisms:_Documents.md

**Files:**
- Modify: `Engineering_Culture/SDLC/Project_Planning_Mechanisms:_Documents.md:119-128`

**Step 1: Add ADR tool link to Technical Design section**

Location: After line 119 ("Once Product Management defines what to build, engineering determines how. Great technical designs:")

```markdown
> [!NOTE]
> Document architectural decisions with [architecture-decision-record](https://bordenet.github.io/architecture-decision-record/) ([repo](https://github.com/bordenet/architecture-decision-record))
```

**Step 2: Verify formatting matches existing callouts**

Check that NOTE callout style matches existing patterns in the file (lines 3-4, 98)

**Step 3: Commit**

```bash
git add Engineering_Culture/SDLC/Project_Planning_Mechanisms:_Documents.md
git commit -m "docs: add architecture-decision-record tool link to Technical Design section"
```

---

## Task 2: Add Acceptance Criteria Assistant to Project_Planning_Mechanisms:_Documents.md

**Files:**
- Modify: `Engineering_Culture/SDLC/Project_Planning_Mechanisms:_Documents.md:103-107`

**Step 1: Add acceptance criteria tool link to User Stories section**

Location: After line 105 ("3. **User Stories**: Core scenarios with acceptance criteria")

```markdown
> [!NOTE]
> Generate acceptance criteria with [acceptance-criteria-assistant](https://bordenet.github.io/acceptance-criteria-assistant/) ([repo](https://github.com/bordenet/acceptance-criteria-assistant))
```

**Step 2: Verify placement doesn't disrupt list flow**

Ensure the callout appears after the numbered list item, before "Common Pitfalls" section

**Step 3: Commit**

```bash
git add Engineering_Culture/SDLC/Project_Planning_Mechanisms:_Documents.md
git commit -m "docs: add acceptance-criteria-assistant tool link to PRD section"
```

---

## Task 3: Add Strategic Proposal to Document Landscape table

**Files:**
- Modify: `Engineering_Culture/SDLC/Project_Planning_Mechanisms:_Documents.md:33-40`

**Step 1: Add Strategic Proposal row to table**

Location: After the "Technical Design" row (line 38), before the "Functional Spec" row (line 39)

```markdown
| [**Strategic Proposal**](https://bordenet.github.io/strategic-proposal/) | Present strategic initiatives to leadership | Leadership/PM | "Should we invest in this direction?" | Major initiatives, platform decisions |
```

**Step 2: Verify table alignment**

Check that pipe characters align with existing rows

**Step 3: Commit**

```bash
git add Engineering_Culture/SDLC/Project_Planning_Mechanisms:_Documents.md
git commit -m "docs: add strategic-proposal to document landscape table"
```

---

## Task 4: Add Business Justification to Document Landscape table

**Files:**
- Modify: `Engineering_Culture/SDLC/Project_Planning_Mechanisms:_Documents.md:33-40`

**Step 1: Add Business Justification row to table**

Location: After the Strategic Proposal row added in Task 3

```markdown
| [**Business Justification**](https://bordenet.github.io/business-justification-assistant/) | Build financial case for initiatives | PM/Finance | "What's the ROI?" | Budget requests, resource allocation |
```

**Step 2: Verify table alignment**

Check that pipe characters align with existing rows

**Step 3: Commit**

```bash
git add Engineering_Culture/SDLC/Project_Planning_Mechanisms:_Documents.md
git commit -m "docs: add business-justification-assistant to document landscape table"
```

---

## Task 5: Add Power Statement Assistant to Professional_Writing_Tips.md

**Files:**
- Modify: `Engineering_Culture/Culture/Professional_Writing_Tips.md`

**Step 1: Locate "Phase 1: Clarify Your Intent" section**

Search for the section heading (approximately line 40 based on integration plan)

**Step 2: Add power statement tool link**

Location: After the section heading, before the main content

```markdown
> [!TIP]
> Craft compelling power statements with [power-statement-assistant](https://bordenet.github.io/power-statement-assistant/) ([repo](https://github.com/bordenet/power-statement-assistant))
```

**Step 3: Commit**

```bash
git add Engineering_Culture/Culture/Professional_Writing_Tips.md
git commit -m "docs: add power-statement-assistant tool link to writing tips"
```

---

## Task 6: Add Job Description Assistant to People_-_Process_-_Technology_Triad.md

**Files:**
- Modify: `Engineering_Culture/Culture/People_-_Process_-_Technology_Triad.md`

**Step 1: Locate "People First" section**

Search for the section heading

**Step 2: Add JD assistant tool link**

Location: In the "People First" section where hiring is discussed

```markdown
> [!NOTE]
> Create effective job descriptions with [jd-assistant](https://bordenet.github.io/jd-assistant/) ([repo](https://github.com/bordenet/jd-assistant))
```

**Step 3: Commit**

```bash
git add Engineering_Culture/Culture/People_-_Process_-_Technology_Triad.md
git commit -m "docs: add jd-assistant tool link to people-first section"
```

---

## Task 7: Final verification

**Step 1: Check all modified files for consistency**

```bash
cd Engineering_Culture
grep -r "bordenet.github.io" SDLC/ Culture/ | grep -E "(architecture-decision-record|acceptance-criteria-assistant|strategic-proposal|business-justification-assistant|power-statement-assistant|jd-assistant)"
```

Expected: 6 new tool links found

**Step 2: Verify no selling language introduced**

Review all changes - ensure links are informational, not promotional

**Step 3: Final commit if any cleanup needed**

```bash
git status
# If any adjustments needed, commit them
```

