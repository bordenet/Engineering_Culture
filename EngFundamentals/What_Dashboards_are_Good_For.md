# 📊 What Dashboards Are Good For (And What They're Not)

In 2016, I joined iStreamPlanet, an operationally challenged startup handling live video transcoding for nationally televised broadcasts. They had done some phenomenal work to build their solution, but when systems failed, customer impact was immediate and highly visible. The company had zero useful metrics: just crash dumps and poorly structured, duplicative logs sent to a log store that made investigation harder, not easier.

We invested heavily in observability infrastructure, including a prominent dashboard display system. The team built high-quality, trustworthy dashboards. And yet production availability remained stuck at ~92% month-over-month. Services failed silently and stayed down for hours. The dashboards continued to look great in the early days, meaning they didn't help.

The dashboards themselves didn't solve the reliability problems. But they provided the foundation needed to identify and fix the underlying issues. That distinction matters: dashboards are essential, but they're not sufficient.

## Table of Contents

- [The Reality Check: Dashboards Are Passive](#the-reality-check-dashboards-are-passive)
- [What Dashboards Actually Excel At](#what-dashboards-actually-excel-at)
- [The Passive Monitoring Trap](#the-passive-monitoring-trap)
- [Why Engineering Teams Still Need Dashboards](#why-engineering-teams-still-need-dashboards)
- [The Path Forward](#the-path-forward)

## The Reality Check: Dashboards Are Passive

Dashboards are passive. They display data; they do not act on it:

| **Dashboards Will NEVER** | **What This Means** |
|:---------------------------|:--------------------|
| **Alert when systems begin to degrade** | Dashboards display information but don't actively notify anyone when thresholds are crossed |
| **Alert when consumption drops unexpectedly** | If your service receives zero requests during business hours, that's likely a critical issue - but dashboards won't tell you |
| **Alert when resources are exhausted** | Memory limits, disk space, connection pools filling up - all require active monitoring, not passive visualization |
| **Be monitored 24/7 by human eyes** | No one stares at dashboards continuously; expecting humans to watch for problems doesn't scale |
| **Take corrective action** | Dashboards display the problem but do not page anyone or trigger remediation |

## What Dashboards Actually Excel At

Once you accept that dashboards are passive, here's what they *are* great at:

- **Historical correlation**: Review past performance, correlate events across services, identify patterns for capacity planning
- **Threshold calibration**: Study normal operational ranges to establish warning/error thresholds and SLIs before connecting to paging systems
- **Incident investigation**: Gain situational awareness during outages, distinguish real problems from anecdotal reports, support post-incident analysis
- **Cross-team visibility**: Enable data-driven conversations about dependencies across [SOA service teams](SOA_and_Microservices.md)
- **On-call triage**: Instant situational awareness when paged

## The Passive Monitoring Trap

Dashboards aren't the only passive monitoring approach that teams mistakenly rely on.

All four of my most recent engineering teams used Slack or Teams for alerts. At one company, a few engineers carried the operational load because nobody else watched. At another, eight channels created a noise tsunami that numbed everyone. The alerts fired; they just didn't matter.

## Why Engineering Teams Still Need Dashboards

Dashboards remain essential because building them forces you to engineer trustworthy metrics, develop SLIs, and understand system behavior well enough to set meaningful thresholds. That work becomes the foundation for automated alerting, self-healing systems, and capacity planning.

For the systematic approach to building them, from collecting data through production alerting, see [How to Construct a Useful Dashboard](How_to_Construct_a_Useful_Dashboard.md).

## The Path Forward

Back to iStreamPlanet: once we had trustworthy dashboards, we could finally see the patterns. Services that looked healthy were actually bleeding. Latency spikes correlated with specific upstream behaviors. The ~92% availability wasn't random. It was predictable, and the dashboards showed us where to dig.

We didn't fix availability by staring at dashboards harder. We fixed it by using dashboard data to build automated alerting, then runbooks, then eventually self-healing systems. The dashboards were the foundation. But the foundation isn't the house.

**Start with dashboards, but don't stop there.** Use them to build the understanding and data foundation needed for automated monitoring, alerting, and eventually, systems that fix themselves.

## Additional Reading

### Related Framework Posts
- **[How to Construct a Useful Dashboard](How_to_Construct_a_Useful_Dashboard.md)** - Practical guidance for building effective dashboards
- **[SOA & Microservices](SOA_and_Microservices.md)** - Understanding distributed systems that dashboards help monitor
- **[Mechanisms: Building Self-Correcting Systems](../SDLC/Mechanisms:_Building_Self-Correcting_Systems.md)** - Using dashboard insights to build automated operational processes

### Industry References
- **[Google SRE Book: Monitoring Distributed Systems](https://sre.google/sre-book/monitoring-distributed-systems/)** - Comprehensive guide to monitoring principles
- **[Golden Signals](https://sre.google/sre-book/monitoring-distributed-systems/#xref_monitoring_golden-signals)** - The four key metrics every service should monitor

---

## 🧭 Navigation

**🏠 [Engineering Culture](../README.md)** → **📂 [Engineering Fundamentals](../README.md#engineering-fundamentals)** → **📄 What Dashboards Are Good For**

**Quick Links:** [🔝 Back to Top](#what-dashboards-are-good-for-and-what-theyre-not) | [📚 Additional Reading](#additional-reading) | [💬 Feedback](https://github.com/bordenet/Engineering_Culture/issues/new)

**Related in This Series:**
- [How to Construct a Useful Dashboard](./How_to_Construct_a_Useful_Dashboard.md) - *Practical implementation guide*
- [SOA & Microservices](./SOA_and_Microservices.md) - *Understanding systems that need monitoring*
- [The Road to an SLA](./The_Road_to_an_SLA.md) - *Using metrics for customer commitments*

**Related Topics:**
- [Mechanisms: Building Self-Correcting Systems](../SDLC/Mechanisms:_Building_Self-Correcting_Systems.md) - *Using insights for systematic improvement*

---

*Have hard-won lessons about observability? I'd love to hear them. [Open an issue](https://github.com/bordenet/Engineering_Culture/issues/new) to share.*

***

*Licensed under [CC0 1.0](https://creativecommons.org/publicdomain/zero/1.0/). Reuse freely; attribution appreciated, not required.*