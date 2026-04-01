# Engineering Culture Blog Posts
*Practical essays on engineering leadership, execution, technical fundamentals, and AI-native ways of working*

---

## About This Collection

Across telecom, broadcast, fintech, and AI, I've seen many of the same structural failures derail projects. Once you know what to look for and how to measure systems, they're not hard to spot. Vague requirements, unclear ownership, humans organized around the wrong boundaries. Different companies, different tech stacks (Microsoft, Amazon, live broadcast, fintech, AI), similar patterns. This is what I've learned to look for.

AI is an amplifier. It accelerates everything: good and bad. A team with crisp requirements and clear ownership ships in days what used to take weeks. A team with fuzzy requirements puts themselves at risk of producing buggy code just as fast. AI hasn't changed the organizational dynamics [Conway's Law](Culture/Understanding_Conways_Law.md) describes, the damage from unclear ownership, or how technical debt compounds. It just makes the consequences arrive sooner. The [AI Engineering](AIEngineering/README.md) section explores what it takes to build teams that use AI effectively: culture change, not just tool adoption.

The [genesis](https://github.com/bordenet/genesis) project is the working reference implementation behind several ideas in this collection. For the architectural rationale, see [Genesis: Background](https://github.com/bordenet/genesis/blob/main/BACKGROUND.md).

**Acknowledgments**: I've been lucky to learn from great mentors at Amazon and iStreamPlanet, and from teammates across every company I've worked with who challenged my thinking and made me better. I publish these essays to help engineering leaders think through these problems before they show up in production.


## AI Engineering
* [What AI-First Engineering Looks Like](AIEngineering/What_AI-First_Engineering_Looks_Like.md) - *The mindset shift behind effective AI-native teams, and the anti-patterns that stall adoption*
* [Building an AI-First Engineering Culture](AIEngineering/Building_an_AI-First_Engineering_Culture.md) - *A practitioner's guide from assessment through scaling, with real examples and lessons from doing it wrong first*
* [The Evolution of AI-First Thinking](AIEngineering/The_Evolution_of_AI-First_Thinking.md) - *What 2026 data shows about AI coding assistants: updating assumptions based on evidence*

## Culture
* [The People-Process-Technology Triad: Getting the Order Right](Culture/People_-_Process_-_Technology_Triad.md) - *Why the order matters: people first, process second, technology third*
* [Understanding Conway's Law: Why Team Structure Determines System Architecture](Culture/Understanding_Conways_Law.md) - *How organizational design shapes the systems you build - and what to do about it*
* [The Myth of "Hypercare": Why This Industry Term Undermines Operational Excellence](Culture/The_Myth_of_Hypercare.md) - *How the concept of "hypercare" creates a false dichotomy between launch support and long-term ownership*
* [Professional Writing for Engineers: Beyond Code Comments](Culture/Professional_Writing_Tips.md) - *Why clear writing matters more than most engineers think, and how to get better at it*
* [Constructive Feedback: The SBI Model](Culture/Constructive_Feedback_SBI_Model.md) - *How to give feedback that develops people instead of triggering their defenses*
* [Clear Communication: Avoiding Weasel Words and Clichés](Culture/Weasel_Words.md) - *Eliminate imprecise language and build a culture where ideas are judged on merit, not clever phrasing*

## SDLC
* [What vs. How: The Critical Distinction in Engineering Leadership](SDLC/Understanding_What_vs_How.md) - *Why confusing outcomes with implementation kills projects before they start*
* [Mechanisms: Building Self-Correcting Systems](SDLC/Mechanisms:_Building_Self-Correcting_Systems.md) - *How to replace ad-hoc processes with systems that find and fix their own problems*
* [Project Planning: A Practical Guide to Documents](SDLC/Project_Planning_Mechanisms:_Documents.md) - *Know which document to create, when to use it, and why it matters in the age of AI-generated specs*
* [Project Planning: The PR-FAQ Mechanism](SDLC/The_PR-FAQ.md) - *Amazon's "Working Backwards" approach: when to use this powerful tool and when to skip it*
* [Distilling Clarity: The One-Pager](SDLC/The_One-Pager.md) - *A forcing function for clarity - if you can't fit it on one page, you don't understand it well enough*

## Engineering Fundamentals
* [SOA & Microservices: Clearing the Confusion](EngFundamentals/SOA_and_Microservices.md) - *Why understanding Service-Oriented Architecture is a prerequisite to getting microservices right*
* [The Road to an SLA: From Metrics to Customer Commitments](EngFundamentals/The_Road_to_an_SLA.md) - *How to build Service Level Agreements that protect your business while enabling growth*
* [What Dashboards Are Good For (And What They're Not)](EngFundamentals/What_Dashboards_are_Good_For.md) - *Understanding the proper role of observability dashboards in engineering operations*
* [How to Construct a Useful Dashboard](EngFundamentals/How_to_Construct_a_Useful_Dashboard.md) - *A systematic approach to building dashboards that improve operational visibility*

## License
© 2026 Matt Bordenet. Licensed under [CC0 1.0](https://creativecommons.org/publicdomain/zero/1.0/).

Fork, remix, and reuse freely. Attribution is appreciated, not required.
