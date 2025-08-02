# 📐 SDLC Project Planning Mechanisms: A Practical Guide to Documents

> [!NOTE]
> Read more about [mechanisms](./Mechanisms:_Building_Self-Correcting_Systems.md)

In the age of AI, anyone can generate a PRD or technical spec in seconds. But understanding *which* document to create, *when* to use it, and *why* it matters—that's where experience counts.

After 26 years building software at companies from Microsoft to early-stage startups, I've seen planning documents save projects and sink them. The difference? Knowing their purpose and boundaries.

This guide shares what actually works, helping teams avoid the document factories that plague enterprise software while maintaining the rigor needed to ship successfully.

Understanding [what vs. how](Understanding_What_vs_How.md) is foundational to choosing the right document—each serves different purposes in separating outcomes from implementation.

For guidance on writing any of these documents effectively, see [Professional Writing for Engineers](../Culture/Professional_Writing_Tips.md).

## Table of Contents

- [The Document Landscape](#the-document-landscape)
- [The Golden Rules](#the-golden-rules)
- [PR-FAQ: Start with the End in Mind](#pr-faq-start-with-the-end-in-mind)
- [The One-Pager: Your Swiss Army Knife](#the-one-pager-your-swiss-army-knife)
- [PRD: The What and Why](#prd-the-what-and-why)
- [Technical Design: The How](#technical-design-the-how)
- [The Danger of Document Proliferation](#the-danger-of-document-proliferation)
- [Practical Guidance for the AI Era](#practical-guidance-for-the-ai-era)
- [Making It Work at Your Company](#making-it-work-at-your-company)
- [Final Thoughts](#final-thoughts)

## The Document Landscape

Before diving into specifics, here's your quick reference for the most common planning documents:

| Document Type | Purpose | Owner | Key Question Answered | When to Use |
|--------------|---------|--------|---------------------|-------------|
| [**PR-FAQ**](./The_PR-FAQ.md) | Define customer value through future press release | Product Manager | "Would customers care?" | New products, major features |
| [**One-Pager**](./The_One-Pager.md) | Capture ideas quickly, drive decisions | Anyone | "Is this worth pursuing?" | Early exploration, decision points |
| **Product Requirements Document (PRD)** | Specify what to build and why | Product Manager | "What problem are we solving?" | Feature development |
| **Technical Design** | Detail how to build it | Engineering | "How will we implement this?" | Complex features, architecture changes |
| **Functional Spec** | Bridge product vision to engineering | Engineering/TPM | "What exactly should it do?" | When PRD needs technical translation |

## The Golden Rules

Before exploring each document type, remember these principles:

1. **Less is more**: Every document should earn its existence by preventing more confusion than it creates
2. **Stay in your lane**: Product defines the "why" and "what," Engineering owns the "how"
3. **Write for outcomes**: Documents succeed when they help ship the right thing, not when they're "complete"
4. **Maintain one source of truth**: Overlapping documents breed contradictions

## [PR-FAQ](./The_PR-FAQ.md): Start with the End in Mind

The Press Release + Frequently Asked Questions (PR-FAQ) format forces you to think backwards from customer success. 

### When to Use It
- Launching entirely new products or capabilities
- Making strategic pivots
- When stakeholder alignment is critical

### When to Skip It
- Incremental features
- Bug fixes or performance improvements
- When the team already shares context

### What Makes a Good PR-FAQ

The press release should read like something customers would actually want to share. If you're straining to make it exciting, you might be building the wrong thing.

The FAQ section addresses internal concerns—feasibility, risks, dependencies—not customer questions. Common mistakes include:
- Using FAQ as a requirements dump
- Writing implementation details
- Creating wish lists without constraints

**Pro tip**: Use AI to help with writing style, but the strategic thinking must be human. No LLM can tell you if your idea solves a real problem.

📖 **Learn more**: [Working Backwards: The Amazon Method](https://www.amazon.com/Working-Backwards-Insights-Stories-Secrets/dp/1250267595)

## The [One-Pager](./The_One-Pager.md): Your Swiss Army Knife

The most underutilized document in software development, one-pagers excel at:
- Capturing ideas before they're lost
- Driving quick decisions
- Providing checkpoint summaries
- Recording learnings and pivots

### Structure That Works

```markdown
**Problem**: What's broken or missing? (2-3 sentences)
**Impact**: Why should we care? (bullets with data)
**Proposed Solution**: High-level approach (not implementation)
**Alternatives Considered**: What else could we do?
**Recommendation**: Clear next step
```

Anyone can write these—engineers spotting technical debt, designers seeing UX friction, analysts finding data insights. The low effort encourages documentation over perfection.

## PRD: The What and Why
--> [Product Requirements Assistant](https://github.com/bordenet/product-requirements-assistant) <--

A *Product Requirements Document* succeeds when engineering can build the right thing without constant clarification. Modern PRDs focus on:

### Essential Elements
1. **Problem Statement**: What customer pain are we addressing?
2. **Success Metrics**: How will we know it worked?
3. **User Stories**: Core scenarios with acceptance criteria
4. **Non-Goals**: What we're explicitly not doing
5. **Constraints**: Technical, legal, or business boundaries

### Common Pitfalls
- **Overspecifying implementation**: "The API should use REST with JSON..." ❌
- **Under-specifying behavior**: "Make it fast" ❌
- **Missing edge cases**: What happens when things go wrong?

📖 **Templates & Examples**: 
- [Atlassian's PRD Guide](https://www.atlassian.com/agile/product-management/requirements)
- [Lenny's Newsletter: PRD Templates](https://www.lennysnewsletter.com/p/my-favorite-product-requirement-document)

## Technical Design: The How

Once Product Management defines what to build, engineering determines how. Great technical designs:

### Include
- Architecture diagrams and component interactions
- API contracts and data models
- Performance budgets and scaling considerations
- Security and privacy implications
- Migration plans for existing systems

### Avoid
- Justifying the business value (that's the PRD's job)
- Implementation details better left to code
- Premature optimization

📖 **Resources**: 
- [Google's Design Docs Guide](https://www.industrialempathy.com/posts/design-docs-at-google/)
- [System Design Interview Basics](https://github.com/donnemartin/system-design-primer)

## The Danger of Document Proliferation

In my Microsoft days (1998-2012), I'd routinely discover SharePoint graveyards filled with obsolete specs. Each document seemed useful at creation but became confusing technical debt post-launch because they were almost without exception abandoned and unmaintained. Consider what will happen when enterprise AI tools crawl this data and return results.  

### Signs You Have Too Many Documents
- Teams can't find the "real" requirements
- Documents contradict each other
- More time updating docs than building
- New team members get conflicting guidance

### The Fix
1. **Audit regularly**: Archive anything not actively used
2. **Single owner rule**: Each domain needs one authoritative document
3. **Link, don't duplicate**: Reference other docs rather than copying content
4. **Version control**: Use Git for docs, not v1_final_FINAL_2.docx

## Practical Guidance for the AI Era

With LLMs, anyone can generate plausible-looking requirements. But documents without judgment create more problems than they solve. Use AI to:

### ✅ Do This
- Polish writing and improve clarity
- Check for completeness against templates
- Generate examples and edge cases
- Translate technical concepts for different audiences

### ❌ Don't Do This
- Generate requirements without understanding the problem
- Create documents just because you can
- Skip the hard thinking about trade-offs
- Assume AI-generated content is correct

## Making It Work at Your Company

The right documentation strategy depends on your context:

### For Startups (< 50 people)
- One-pagers for most decisions
- PRDs for major features only
- Technical designs for architectural changes
- Skip everything else

### For Growth Companies (50-500 people)
- PR-FAQs for new product lines
- Standardized PRD template
- Technical designs for cross-team work
- Functional specs when needed

### For Enterprises (500+ people)
- Full document suite but with clear ownership
- Automated tooling to detect conflicts
- Regular archive/cleanup cycles
- Training on when NOT to document

## Final Thoughts

Documentation should accelerate development, not impede it. Every document must earn its existence by:
1. Preventing more confusion than it creates
2. Helping ship the right thing faster
3. Serving as a decision record
4. Enabling new team members to contribute quickly

In the end, working software matters more than comprehensive documentation. But the right documentation, at the right time, makes working software possible.

## Additional Reading

These authoritative sources provide essential frameworks for effective project planning and documentation:

- **"The Mythical Man-Month"** by Frederick P. Brooks Jr. - Timeless insights on software project management and communication, particularly relevant for understanding why clear documentation prevents project failures and how adding people to late projects makes them later.

- **"Documentation for Software Engineers"** by Kathy Sierra and Bert Bates - Comprehensive guide to creating documentation that actually helps teams ship better software, with practical frameworks for knowing what to document and when.

- **"Making Things Happen"** by Scott Berkun - Essential reading on project management for technology teams, offering proven strategies for planning, executing, and documenting complex software projects.

- **"The Design of Everyday Things"** by Don Norman - Foundational text on user-centered design thinking that informs how to write requirements documents that focus on user outcomes rather than technical features.

- **"Lean Enterprise"** by Jez Humble, Joanne Molesky, and Barry O'Reilly - Modern approach to scaling product development that emphasizes lightweight documentation practices and continuous validation of assumptions.

- **"Team Topologies"** by Matthew Skelton and Manuel Pais - Critical reading for understanding how team structure affects documentation needs, helping determine the right level of formal specification for different organizational contexts.

---

*Have your own templates or hard-won lessons? I'd love to hear them. Drop a comment or [open an issue](https://github.com/bordenet/Engineering_Culture/issues/new) to share.*

*More engineering leadership insights will be forthcoming. Check back soon!* 
