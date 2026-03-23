# Building an AI-First Engineering Culture

You've seen [what AI-First looks like](./What_AI-First_Engineering_Looks_Like.md): the anti-patterns, the failure modes, the story of 12 engineers at Telepathy.ai outpacing 70. The question is: how do you build that culture in your organization?

The answer isn't a tool rollout. It's a culture change. And culture change happens through [mechanisms](../SDLC/Mechanisms:_Building_Self-Correcting_Systems.md), not mandates.

## Assess Where You Are

Before changing anything, understand your starting point. [Allie K. Miller's "Four Modes of AI Interaction"](https://aiwithallie.beehiiv.com/p/the-four-modes-of-ai-interaction) provides a useful maturity ladder: Microtasker → Companion → Delegate → Teammate.

Here's the opinion most posts won't give you: **assess the least AI-fluent part of the team and build from there.** Your top performers are already experimenting. They'll figure it out. The transformation stalls when half the team is stuck at Microtasker while the other half operates at Delegate. That gap creates friction: different assumptions about what's possible, resentment from those left behind, and a two-tier team culture that poisons collaboration.

Run an open survey the team can see. Ask: *How often do you use AI tools? For what tasks?* We did this at Telepathy.ai and the transparency enabled engineers to learn from one another. Over half were stuck at Microtasker while a handful were already at Delegate. The gap was wider than I expected, and closing it mattered more than accelerating the high performers.

Here's an uncomfortable reality: when you detect an unfixable gap in productivity due to non-adopters, it's time for an honest, likely difficult conversation with the engineer. This isn't about punishing people who learn differently. It's about recognizing that some gaps won't close with training or encouragement. Leaders need to watch for these signals early. Productivity problems that go undetected by leaders can sink team morale and hurt the product.

I now explicitly hire for AI fluency. Not "AI expertise," but fluency. Can candidates describe how they use AI in their current work? Do they reach for prompting or default to manual approaches? For me, AI fluency is now one signal of adaptability: candidates should be able to explain when AI improves their work and when it does not.

**Identify friction points.** Where do engineers spend time on repetitive work? PR descriptions. Test boilerplate. Documentation. Commit messages. Changelogs. Release notes. These are your targets.

## Your First Four Weeks

Start with the obvious stuff: low risk, high visibility, immediate payoff.

**Week 1: Automate PR descriptions.** This is the lowest-friction entry point. Engineers see immediate value, and the output is low-stakes enough that mistakes don't have a large blast radius. When someone's PR description is better than anything they'd have written manually, they start wondering what else AI can do.

**Week 2: Commit messages.** Same pattern. Low risk, high repetition, visible improvement. By standardizing commit messages with team templates, you seed the path to release notes, changelogs, and other documentation.

**Week 3: Documentation.** AI-generated first drafts for READMEs, API docs, runbooks. Humans edit, but they're not staring at blank pages.

**Week 4: Productivity tools and automation.** Meeting summaries. Slack thread recaps. Script generation for repetitive tasks. This extends AI beyond the codebase and into daily workflow. Suddenly it's not just a coding tool, it's how work gets done.

The goal isn't to automate everything. It's to build momentum. Each small win creates an engineer who's slightly more likely to try AI for the next task. Compound that across the team.

## When Fast, Disposable Internal Tooling Is Appropriate

Here is the practical rule: sometimes fast, disposable internal tooling is fine or even _preferred_.

If an engineer can spend a few hours building a scrappy internal tool that eliminates daily toil for the team, build the simplest version that removes the toil, use it immediately, and harden it only if it proves durable. Yes, the code quality might be questionable. Yes, AI probably generated 80% of it, and you won't have reviewed every line of code. Yes, it'll need to be rewritten eventually.

But "eventually" is the key word. If it saves the team 10 hours a week starting *now*, the ROI is immediate. You can rewrite it properly later when you understand the requirements better. And you'll understand them better because you've been using the tool.

This isn't permission to ship garbage to production or accumulate reckless tech debt in your core systems. It's recognition that internal tooling, automation scripts, and workflow helpers don't need the same scrutiny as customer-facing code. The bar is "does it work and does it help?" not "would this pass a code review from a senior architect?"

I practice what I preach. I've shipped a half-dozen fast, disposable internal tools that our engineering and business teams actually use, now consolidated into [DocForge AI](https://bordenet.github.io/docforge-ai/): [One-Pager](https://bordenet.github.io/docforge-ai/assistant/?type=one-pager), [PR-FAQ](https://bordenet.github.io/docforge-ai/assistant/?type=pr-faq), [ADR](https://bordenet.github.io/docforge-ai/assistant/?type=adr), [Strategic Proposal](https://bordenet.github.io/docforge-ai/assistant/?type=strategic-proposal), and [Power Statement](https://bordenet.github.io/docforge-ai/assistant/?type=power-statement). Through near brute-force continuous improvement, the codebase is now reliable enough for regular team use. But it started scrappy, and that was fine. They removed toil from day one.

The path wasn't smooth. I started with One-Pager. Medium-to-low code quality, but it solved an immediate problem. Then I tried to expand by telling Claude Code to clone and mutate One-Pager into a sibling tool responsible for creating a different type of document with a similar "adversarial" multi-LLM workflow. That effort failed because the generated code varied too widely in design, test coverage, and user experience. So I invested in a common core called [genesis](https://github.com/bordenet/genesis), a template system that gives AI assistants guardrails to work within. Today, spinning up a new tool takes hours, not days, and the quality of results is consistent. That early YOLO phase taught me what the foundation needed to be. The full story of this evolution—including the lessons learned about AI determinism and why I chose a multi-repo architecture—is documented in [Genesis: Background](https://github.com/bordenet/genesis/blob/main/BACKGROUND.md).

AI-First teams that insist on production-quality code for every internal tool move slower than teams that know when fast, disposable internal tooling is the rational choice. Pick your battles.

## Scale Through Mechanisms

Individual experiments are nice. Mechanisms are how you scale.

**From experiments to habits.** Coach your pioneers to invest in their colleagues. The goal isn't just personal productivity, it's making the whole team faster. When a pioneer discovers something useful, their job isn't done until they've taught it to someone else. And when the ROI doesn't pan out? That's an important follow-up discussion. You may have discovered something that's been holding your team back the entire time.

**Shared toolkits, not personal setups.** Remember the [Lone Wolf anti-pattern](./What_AI-First_Engineering_Looks_Like.md#the-lone-wolf)? Counter it with shared infrastructure. Same tools, same prompts, same expectations. This isn't about limiting creativity, it's about enabling collaboration.

**Measure outcomes, not activities.** Skip the OKRs about "AI adoption percentage." Results speak for themselves. If the team is shipping faster with fewer bugs, if documentation is better, if engineers are spending less time on toil, you'll see it. If you're not seeing it, no OKR will fix that.

**Leadership models the behavior.** If directors and VPs use AI in their own work (drafting roadmaps, preparing board materials, analyzing metrics), it signals that this isn't just for individual contributors. I started sharing my Claude skills and tools in leadership meetings with full details in the company's internal wiki. "Here's how I'm drafting interview agendas, preparing debriefs, and tailoring phone-screen plans." That changed things faster than any training session.

## The Math Has Changed

The financial case matters. Strong teams remain indispensable. A strong core team is irreplaceable. But experienced leaders need to confront a reality that would have seemed wasteful five years ago: expensive AI tools are often the right investment now, provided you're getting consistently positive results.

Do the math on a fully-loaded employee. A senior engineer's base salary of $250K plus 30% for benefits, payroll taxes, equipment, office space, and management overhead puts you at $325K annually, all in. Consultants can cost materially more while offering less continuity and less ownership of the long-term system.

Now look at your monthly AI bill. Even aggressive monthly AI spend is typically a fraction of the monthly fully loaded cost of one additional senior engineer.

The old calculus was: tools are cheap, people are expensive, so hire more people. The new calculus is: build a smaller, stronger core team and give them the AI capability to operate at a higher level of output. The 12-person team that outpaced 70 reflected changed economics, not luck. It was this math in action.

Five years ago, a leader who spent heavily on developer tools was often covering for weak process or poor hiring. That pattern-match doesn't hold anymore. If your best engineers are asking for better AI tools and you're saying no because "tools should be cheap," you're optimizing for a world that no longer exists.

## The Compounding Effect

AI-First transformation compounds.

Each iteration makes the team smarter. The prompt library gets better. The shared knowledge grows. New hires onboard faster because there's infrastructure to support them. The gap between your team and teams that haven't made this shift widens every quarter.

At Telepathy.ai, we didn't have months to rebuild after the LLM revolution gutted our proprietary stack. We retired the proprietary stack and rebuilt around an LLM-native architecture with LangGraph. After a few weeks of architecture and design, we had end-to-end scenarios running within three weeks of implementation and a cleaner separation of responsibilities than before. That's not cutting corners. That's a team operating AI-First under survival pressure.

Six months in, the difference was obvious: we were moving faster with 12 than we ever had with 70. I can't give you precise percentages because we weren't running controlled experiments. We were surviving. But the before/after was undeniable.

I'm now applying these principles at my [current company](https://CallBox.com). The transformation is actively in progress. I'll report back in a future post with concrete metrics.

---

## 🧭 Navigation

**🏠 [Engineering Culture](../README.md)** → **📂 [AI Engineering](./README.md)** → **📄 Building an AI-First Engineering Culture**

**Quick Links:** [🔝 Back to Top](#building-an-ai-first-engineering-culture) | [💬 Feedback](https://github.com/bordenet/Engineering_Culture/issues/new)

**In This Series:**
- [What AI-First Engineering Looks Like](./What_AI-First_Engineering_Looks_Like.md) - *The what and why*
- **You are here:** Building an AI-First Engineering Culture
- [The Evolution of AI-First Thinking](./The_Evolution_of_AI-First_Thinking.md) - *2026 update with industry data*

**Related Topics:**
- [Mechanisms: Building Self-Correcting Systems](../SDLC/Mechanisms:_Building_Self-Correcting_Systems.md) - *Scaling AI adoption through mechanisms*
- [People-Process-Technology Triad](../Culture/People_-_Process_-_Technology_Triad.md) - *AI as technology amplifier*
- [The One-Pager](../SDLC/The_One-Pager.md) - *Document format used in genesis tooling*
- [The PR-FAQ](../SDLC/The_PR-FAQ.md) - *Another document format in the tooling suite*

---

**Previous:** [What AI-First Engineering Looks Like](./What_AI-First_Engineering_Looks_Like.md) | **Next:** [The Evolution of AI-First Thinking](./The_Evolution_of_AI-First_Thinking.md)

***

*Licensed under [CC0 1.0](https://creativecommons.org/publicdomain/zero/1.0/). Reuse freely; attribution appreciated, not required.*
