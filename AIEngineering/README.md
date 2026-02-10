# 🤖 AI Engineering

*How AI-First practices change engineering culture*

---

This series documents what I'm learning building Cari at CallBox.com, an AI-First project where the practices in these posts are working in production.

But the lessons didn't start there. They started at Telepathy.ai in 2025, where the LLM shift sunk the company. Our 6+ year proprietary conversational AI backend became obsolete in months. Where there had been 70 engineers, 12 remained. We couldn't compete by doing things the old way with fewer people.

That failure taught me what not to do. Cari is teaching me what works. These posts capture both.

## The Series

### [What AI-First Engineering Looks Like](./What_AI-First_Engineering_Looks_Like.md)
*The mindset shift that defines high-performing AI-native teams*

What AI-First means and what it's not. Covers the anti-patterns that kill AI adoption (Lone Wolf, Tool Sprawl, AI as Crutch, The Big Bang) and when NOT to use AI. Starts with the Telepathy.ai story and ends with a clear definition: AI is how we work now. Not a novelty. Not a shortcut. The default.

### [Building an AI-First Engineering Culture](./Building_an_AI-First_Engineering_Culture.md)
*A practitioner's guide to bringing your engineering culture into the present day*

How to build AI-First culture in your organization, from assessment through scaling. Covers the first four weeks of adoption, when YOLO vibe coding is acceptable, mechanisms for scaling beyond individual experiments, and the math that's changed about tools vs. headcount. Includes real examples from my own tooling, including a [document generation framework](https://github.com/bordenet/genesis) I built to test AI-assisted development patterns. For the full backstory on that experiment (1,600+ commits, 9 repos, what worked and what didn't), see [the background doc](https://github.com/bordenet/genesis/blob/main/BACKGROUND.md).

### [The Evolution of AI-First Thinking](./The_Evolution_of_AI-First_Thinking.md)
*What the 2026 data shows and how the approach must change*

The state of the art has changed. This post examines the 2026 industry data (26% productivity gains, velocity trade-offs, AI adoption rates) and what it means for how we work. Covers lessons from a [personal experiment in deterministic AI-assisted development](https://github.com/bordenet/genesis/blob/main/BACKGROUND.md) (1,600+ commits, 9 repos, conformity tooling pushed to its limits) and the principles that actually work: architecture-first design, automated verification at every layer, tooling that earns its keep, and human-AI feedback loops that compound over time.

---

## Key Themes

**Culture over tools.** Mindset beats technology, especially when the technology changes every few months. Teams that default to "collaborate with AI" outperform teams with better tools but no cultural shift. See [Building an AI-First Engineering Culture](./Building_an_AI-First_Engineering_Culture.md) for the full playbook.

**Mechanisms over mandates.** Individual experiments teach you what works and sometimes advance the state of the art. [Mechanisms](../SDLC/Mechanisms:_Building_Self-Correcting_Systems.md) are how you scale those learnings. Coach pioneers to teach, build shared toolkits, measure outcomes not activities.

**The math has changed.** A senior engineer's fully-loaded cost is $325K/year. Your monthly AI bill (even with aggressive usage) rarely exceeds a single headcount. Build smaller, stronger teams with AI firepower.

**It compounds, in both directions.** Vince Lombardi said it best: "Practice does not make perfect. Only perfect practice makes perfect." Sloppy AI prompts, unchecked code generation, and undocumented lessons don't just fail to improve; they entrench bad habits. The wrong things compound just as easily as the right ones. Deliberate practice means machine-readable docs, adversarial review, and feedback loops that capture what went wrong. Do it right, and each iteration makes the team smarter. Do it wrong, and you're hardwiring mediocrity at scale. (Congratulations to the Seattle Seahawks on their recent Super Bowl victory. Lombardi would approve of their fundamentals.)

---

## 🧭 Navigation

**🏠 [Engineering Culture](../README.md)** → **📂 AI Engineering**

**In This Section:**
- [What AI-First Engineering Looks Like](./What_AI-First_Engineering_Looks_Like.md) - *Mindset and anti-patterns*
- [Building an AI-First Engineering Culture](./Building_an_AI-First_Engineering_Culture.md) - *Practical implementation guide*
- [The Evolution of AI-First Thinking](./The_Evolution_of_AI-First_Thinking.md) - *2026 update with industry data*

**Related Topics:**
- [Mechanisms: Building Self-Correcting Systems](../SDLC/Mechanisms:_Building_Self-Correcting_Systems.md) - *Framework for scaling practices*
- [People-Process-Technology Triad](../Culture/People_-_Process_-_Technology_Triad.md) - *AI amplifies the Technology layer*
- [Professional Writing Tips](../Culture/Professional_Writing_Tips.md) - *AI-assisted documentation*
- [The One-Pager](../SDLC/The_One-Pager.md) - *Document format used in AI tooling*

---

*Have questions or want to share your own AI transformation story? [Open an issue](https://github.com/bordenet/Engineering_Culture/issues/new) to start the conversation.*

***

*Licensed under [CC0 1.0](https://creativecommons.org/publicdomain/zero/1.0/). Reuse freely with attribution.*

