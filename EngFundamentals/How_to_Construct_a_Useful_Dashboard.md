# 🔧 How to Construct a Useful Dashboard

*I've built observability programs at four companies with four different starting points: zero metrics, useless metrics, expensive tools without a holistic strategy or plan, and teams that already get it. The approach is the same; the pace differs.*

Many teams build dashboards that don't help them understand how their services operate. They don't find out until they're reacting to a production incident.

This guide is for teams who already ship services and have some monitoring in place, even if it's not great. If you're starting from zero, read [What Dashboards are Good For](What_Dashboards_are_Good_For.md) first.

Here, the focus is on what actually works when you're building dashboards from scratch or fixing ones that don't help. It's not about perfection; it's about visibility that enables better decisions, service runbooks, and, eventually, reliable alerting.

## Table of Contents

- [The Five-Phase Dashboard Evolution](#the-five-phase-dashboard-evolution)
- [Common Dashboard Anti-Patterns](#common-dashboard-anti-patterns)
- [From Visualization to Action](#from-visualization-to-action)

## The Five-Phase Dashboard Evolution

Effective dashboards evolve through predictable stages. Don't try to build the perfect dashboard immediately - focus on progression.

### Phase 1: Collect Data

**Goal**: Establish comprehensive metrics collection

**Actions**:
1. **Implement time-series metrics** across your service code
2. **Start with [golden signals](https://sre.google/sre-book/monitoring-distributed-systems/#xref_monitoring_golden-signals)**: Latency, Errors, Traffic, and Saturation
3. **Add context metrics**: CPU, memory, disk, network I/O, and application-specific measurements
4. **Deploy to staging first** to validate metrics collection before production
5. **Debug your data**: Look for metrics that should correlate but don't

**Key principle**: Every metric should either help you understand user experience or system health. If it doesn't serve one of these purposes, consider removing it.

> **Expect to see what was always broken**: At iStreamPlanet, we extracted publishing functionality from our monolithic C++ transcoder into a new distributed service in AWS, with data flowing over gRPC from the private cloud. We instrumented the new service properly from day one. Because it sat at the tail end of the live video pipeline, it immediately surfaced every upstream problem, issues the old monolith had been silently swallowing. Good metrics don't create problems; they reveal the ones you didn't know you had.

**Common mistakes**:
- Collecting too many vanity metrics that don't indicate problems
- Failing to validate that metrics accurately represent what they claim to measure
- Not considering edge cases where metrics might behave unexpectedly

### Phase 2: Organize Data

**Goal**: Create readable, scannable dashboard layouts

**Design principles**:
1. **Most important information on top**: Place critical metrics where they're immediately visible
2. **Focus on upper percentiles**: Use p90/p95/p99 rather than averages for latency and resource utilization
3. **Match dashboard layout to system characteristics**: I/O-bound services should emphasize latency and queue metrics over CPU
4. **Create visual consistency**: Use similar layouts across different services for faster comprehension
5. **Start charts at zero** (usually): Bar charts and histograms should always start at zero. Line charts can start above zero when trends matter more than absolute values. For availability, invert to show failure rates so problems are visible.

**Recommended layout pattern**:

| **Top Row** | **Second Row** | **Third Row** |
|:------------|:---------------|:--------------|
| Requests/sec | Failures/sec | Latency (p95) |
| Memory Available/Consumed | Disk I/O (if relevant) | Network I/O (if relevant) |
| Service-specific queues | CPU utilization | Additional context metrics |

**Visual mistakes to avoid**:
- **Pie charts**: Generally unhelpful unless you have a compelling reason
- **Line charts with sparse data**: Lines trick the eye into seeing continuity that doesn't exist. If you're only collecting data every 5 minutes, use bars.
- **Excessive colors**: Limit color palette to maintain readability
- **Cluttered displays**: If it's hard to read, simplify or split. You can't monitor for defects or debug a service with a dashboard that looks like the Flying Spaghetti Monster sneezed on it.

**Build a dashboard hierarchy**:
- **Executive summary dashboards**: High-level health for leadership visibility
- **Operational dashboards**: Day-to-day monitoring for engineering teams
- **Debugging dashboards**: Detailed metrics for incident response

**Provide context**:
- **Add glossary text boxes** explaining non-obvious metrics
- **Include threshold lines** showing warning and error levels
- **Link to related dashboards** and documentation

> **Stop using averages**: At Telepathy, teams had dashboards full of averages, which meant the worst problems were invisible. Your average can look fine while 1% of your users are on fire. We replaced every latency metric with p95 and p99. The problems we'd been missing became obvious overnight.

### Phase 3: Study Data and Establish Thresholds

**Goal**: Transform dashboards from pretty pictures into operational tools

**Threshold development**:
- **Warning thresholds**: Levels where something has gone wrong and customer impact might follow
- **Error thresholds**: Levels where customer impact is imminent or already happening
- **Historical analysis**: Use actual system behavior to set realistic bounds

**Code optimization opportunities**:
- **Tune magic numbers**: Replace development-time guesses with production-informed values
- **Adjust timeouts**: Set realistic values based on actual latency distributions
- **Optimize resource allocation**: Right-size based on actual usage patterns

**Validation approach**:
- Study at least 2-4 weeks of historical data before setting thresholds
- Account for daily and weekly usage patterns
- Consider seasonal variations in traffic or usage

> **The coordination problem**: At Stash, every team was told to define their own SLOs, and that those SLOs would be their "report card." So they went off and did it alone. Some had decent dashboards, hacked together over time; others had basically nothing. Even the teams doing okay had patchwork coverage. Legacy services had it worst. The platform was swiss cheese for observability: gaps everywhere, no end-to-end view, and teams incentivized to set targets they could hit rather than targets that mattered. We formed an Operational Excellence community and built all our dashboards via git-based JSON. That was the unlock: teams could directly borrow from each other, customize, and iterate. We strongly encouraged stealing. When one team figured something out, everyone benefited.

### Phase 4: Test Alerting Logic

**Goal**: Validate monitoring rules before they wake people up

**Testing approach**:
1. **Route alerts to chat channels** (not paging systems) for initial validation
2. **Monitor alert frequency**: If you're alerting every hour, adjust thresholds
3. **Validate alert accuracy**: Ensure alerts correspond to actual problems
4. **Tune sensitivity**: Balance between false positives and missed incidents

**Common tuning scenarios**:
- **Too sensitive**: Alerting on minor fluctuations that don't affect users
- **Not sensitive enough**: Missing actual problems until customer impact is severe
- **Wrong metrics**: Alerting on symptoms rather than root causes

> **Expect to be flooded**: At two of my former companies, we were already years into designing ourselves into the same corner: treating Kafka as an RPC mechanism under the banner of "elastic architecture." The moment we started measuring the latency (which was obscene at daily peak traffic) alarms poured in, revealing problems long suspected but never understood. Every alert had to be triaged, debugged, documented, and tuned. Only the most critical ones got armed with PagerDuty. The flood was exhausting, but it gave us vital signals about the shortcomings of our architecture. Phase 4 is triage, not perfection.

### Phase 5: Implement Production Alerting

**Goal**: Create reliable, actionable monitoring that improves system reliability

**Implementation guidelines**:
- **Page your own team first**: Don't alert other teams until you've validated your monitoring
- **Document alert response**: Create runbooks that explain what each alert means and how to respond
- **Plan for cross-team dependencies**: Determine who should be alerted when your service affects others
- **Continuous improvement**: Expect to iterate on alerting rules as your system evolves

**Success metrics**:
- **Alert-to-incident ratio**: High-quality alerts should correspond to real problems
- **Time to resolution**: Good monitoring should help teams resolve issues faster
- **Prevention vs. reaction**: Mature monitoring helps prevent problems rather than just detecting them

> **Sustainability over heroics**: Every team at every company has to work through this with new services. There's no shortcut. The trick is continuous improvement, not martyrdom. At iStreamPlanet, some folks tried to shoulder all the alarms themselves. It didn't help. They burned out, the alarms kept coming, and the underlying problems didn't get fixed any faster. Those same people eventually helped lead us to a place of sustainability: spreading the load, tuning relentlessly, and accepting that Phase 5 is never really "done."

## Common Dashboard Anti-Patterns

Once you've built basic dashboards, watch for these failure modes.

### Anti-Pattern 1: The Everything Dashboard
**Problem**: Trying to show every possible metric on a single dashboard
**Result**: Information overload that makes it impossible to identify actual problems
**Fix**: Create focused dashboards for specific use cases

### Anti-Pattern 2: The Vanity Metrics Display
**Problem**: Showing metrics that look impressive but don't indicate system health
**Result**: False confidence and missed real problems
**Fix**: Focus on metrics that correlate with user experience

> I've seen teams construct performative dashboards without a clear purpose or plan. They hadn't conceived of an OE strategy, so they created "something" rather than "nothing" and didn't get much consistent value from it. I'm not naming names for this one.

### Anti-Pattern 3: The Spaghetti Monster
**Problem**: Too many overlapping lines on a single graph
**Result**: Unreadable visualizations that provide no useful information
**Fix**: Filter to show only top/bottom values or split into multiple graphs

### Anti-Pattern 4: The Misleading Scale
**Problem**: Y-axis manipulation that exaggerates or minimizes changes
**Result**: Incorrect assessment of problem severity
**Fix**: Use consistent scaling and start charts at zero when appropriate

> Too many teams to cite wanted to show how great their service was. So they'd graph availability from 0% to 100%, and all the valuable signal was lost in the top few pixels. If you're running at 99.9% availability, the difference between "fine" and "on fire" is invisible at that scale. Invert these graphs to show failure rates, not success rates.

## From Visualization to Action

Dashboards are only useful if they change how you operate.

The role of dashboards: a critical tool, but a small part of a larger Operational Excellence program. They inform which metrics should be armed with the pager, which thresholds constitute warnings, which thresholds constitute errors, and what month-over-month or day-over-day trends tell us. When alarms fire and an engineer gets paged, dashboards tell them where to investigate.

### Building Operational Discipline
- **Regular dashboard reviews**: Make monitoring review part of team routines
- **Post-incident dashboard analysis**: Ask "What dashboard would have helped us detect this sooner?"
- **Cross-team sharing**: Learn from other teams' monitoring approaches. See ["The coordination problem"](#phase-3-study-data-and-establish-thresholds) above.

### Enabling Automation
- **SLA monitoring**: Use dashboard metrics to track service level objectives
- **Capacity planning**: Automate scaling decisions based on trending data
- **Self-healing systems**: Build automation that responds to threshold breaches

### Supporting Business Goals
- **Customer impact correlation**: Connect technical metrics to user experience
- **Cost optimization**: Use monitoring data to inform resource allocation decisions
- **Feature impact assessment**: Measure how new features affect system performance

Dashboards exist to tell you what your system is doing. As your business scales and changes, you'll use them to tune thresholds and understand system behavior under different loads. And the proof is whether they help when something breaks. Bring them online in pre-production as part of your development cycle so they add value from day one after you've shipped to production.

## Additional Reading

### Related Framework Posts
- **[What Dashboards are Good For](What_Dashboards_are_Good_For.md)** - Understanding the proper role of dashboards in operations
- **[SOA & Microservices](SOA_and_Microservices.md)** - Monitoring patterns for distributed systems
- **[Mechanisms: Building Self-Correcting Systems](../SDLC/Mechanisms:_Building_Self-Correcting_Systems.md)** - Using monitoring data to build automated operational processes

### Industry References
- **[Google SRE Book: Monitoring Distributed Systems](https://sre.google/sre-book/monitoring-distributed-systems/)** - Comprehensive guide to monitoring principles
- **[Golden Signals](https://sre.google/sre-book/monitoring-distributed-systems/#xref_monitoring_golden-signals)** - The four key metrics every service should monitor
- **[Data Visualization Best Practices](https://www.datylon.com/blog/bad-data-visualization-examples)** - Common visualization mistakes and how to avoid them

---

## 🧭 Navigation

**🏠 [Engineering Culture](../README.md)** → **📂 [Engineering Fundamentals](../README.md#engineering-fundamentals)** → **📄 How to Construct a Useful Dashboard**

**Quick Links:** [🔝 Back to Top](#-how-to-construct-a-useful-dashboard) | [📚 Additional Reading](#additional-reading) | [💬 Feedback](https://github.com/bordenet/Engineering_Culture/issues/new)

**Related in This Series:**
- [What Dashboards Are Good For](./What_Dashboards_are_Good_For.md) - *Understanding dashboard purpose and limitations*
- [The Road to an SLA](./The_Road_to_an_SLA.md) - *Using metrics for customer commitments*
- [SOA & Microservices](./SOA_and_Microservices.md) - *Monitoring distributed systems*

**Related Topics:**
- [Mechanisms: Building Self-Correcting Systems](../SDLC/Mechanisms:_Building_Self-Correcting_Systems.md) - *Using data for systematic improvement*

---

*Have your own templates or hard-won lessons? I'd love to hear them. Drop a comment or [open an issue](https://github.com/bordenet/Engineering_Culture/issues/new) to share.*

***

*Licensed under [CC0 1.0](https://creativecommons.org/publicdomain/zero/1.0/). Reuse freely with attribution.*
