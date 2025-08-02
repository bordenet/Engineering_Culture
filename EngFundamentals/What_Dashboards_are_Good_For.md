# 📊 What Dashboards Are Good For (And What They're Not)

*Understanding the proper role of observability dashboards in engineering operations*

Most engineering teams treat dashboards as the solution to their observability problems. Install a monitoring tool, create some charts, put them on a big screen—problem solved, right? After years of building and iterating on monitoring systems, I've learned that dashboards are incredibly valuable when used correctly, but they're often misunderstood and misapplied.

This post explores the real strengths and limitations of dashboards, helping engineering teams build monitoring strategies that actually improve system reliability rather than just creating pretty visualizations.

## Table of Contents

- [The Reality Check: Dashboards Are Passive](#the-reality-check-dashboards-are-passive)
- [What Dashboards Actually Excel At](#what-dashboards-actually-excel-at)
- [The Passive Monitoring Trap](#the-passive-monitoring-trap)
- [Why Engineering Teams Still Need Dashboards](#why-engineering-teams-still-need-dashboards)
- [Building Toward Operational Excellence](#building-toward-operational-excellence)
- [Key Takeaways for Engineering Leaders](#key-takeaways-for-engineering-leaders)

<details>
<summary>A Real-World Example</summary>

In 2016, I joined an operationally challenged startup handling live video transcoding for nationally televised broadcasts. When systems failed, customer impact was immediate and highly visible. The company had zero useful metrics—just crash dumps and poorly structured logs sent to a subpar vendor.

After investing in proper observability infrastructure, including a prominent dashboard display system, the team built high-quality, trustworthy dashboards. However, production availability remained at ~92% month-over-month due to services silently failing and staying down for hours.

The dashboards themselves didn't solve the reliability problems, but they provided the foundation needed to identify and fix the underlying issues. This experience taught valuable lessons about the proper role of dashboards in operational excellence.

</details>

## The Reality Check: Dashboards Are Passive

Understanding what dashboards cannot do is crucial for building effective monitoring strategies:

| **Dashboards Will NEVER** | **What This Means** |
|:---------------------------|:--------------------|
| **Alert when systems begin to degrade** | Dashboards display information but don't actively notify anyone when thresholds are crossed |
| **Alert when consumption drops unexpectedly** | If your service receives zero requests during business hours, that's likely a critical issue—but dashboards won't tell you |
| **Alert when resources are exhausted** | Memory limits, disk space, connection pools filling up—all require active monitoring, not passive visualization |
| **Be monitored 24/7 by human eyes** | No one stares at dashboards continuously; expecting humans to watch for problems doesn't scale |
| **Take corrective action** | Dashboards show you the fire but don't call the fire department |

## What Dashboards Actually Excel At

Despite their limitations, dashboards serve critical functions in engineering operations:

### Historical Analysis and Context
- **Review past performance trends** to understand system behavior over time
- **Correlate events** across different services and time periods
- **Identify patterns** that inform capacity planning and architectural decisions

### Current State Assessment
- **Quick health checks** when investigating reported issues
- **System status at a glance** for on-call engineers during incident response
- **Resource utilization snapshots** for scaling decisions

### Threshold Development
- **Establish warning and error thresholds** by studying normal operational ranges
- **Identify Service Level Indicators (SLIs)** that accurately reflect user experience
- **Calibrate alerting systems** before connecting them to paging systems

### Cross-Team Collaboration
- **Provide shared visibility** into distributed system behavior
- **Enable data-driven conversations** about system dependencies
- **Support [SOA service teams](SOA_and_Microservices.md)** in understanding their customer impact

### Incident Investigation
- **Gain situational awareness** when troubleshooting outages (though the incident response is already late at this point)
- **Distinguish real problems from anecdotal reports** through objective data
- **Support post-incident analysis** with concrete evidence of what happened

## The Passive Monitoring Trap

Dashboards aren't the only passive monitoring approach that teams mistakenly rely on:

### Chat Notifications
Chat webhooks and bot notifications suffer from the same fundamental problem—they require humans to be actively monitoring communication channels during business hours. This doesn't scale and creates a false sense of monitoring coverage.

### Log Monitoring
Manual log analysis and log-tailing are equally passive. While logs contain valuable diagnostic information, expecting engineers to continuously monitor log streams is unrealistic and ineffective.

### Email Alerts
Email-based monitoring notifications often go unread or get lost in busy inboxes, making them unsuitable for time-sensitive operational issues.

## Why Engineering Teams Still Need Dashboards

This isn't a contradiction—dashboards remain essential despite their limitations:

### Foundation for Automation
Creating useful dashboards forces teams to:
- **Engineer trustworthy metrics** that accurately reflect system health
- **Develop Service Level Indicators (SLIs)** that can be reused for automated monitoring
- **Understand system behavior** well enough to set meaningful thresholds

### Building Block for Advanced Operations
Dashboards provide the data foundation for:
- **Automated alerting systems** that notify engineers when intervention is needed
- **Self-healing systems** with contingency switches, circuit breakers, and load shedding
- **Capacity planning** based on actual usage patterns rather than estimates

### Business Visibility
Engineering dashboards enable:
- **Executive reporting** that translates technical metrics into business impact
- **SLA tracking** and availability reporting for leadership—see [The Road to an SLA](The_Road_to_an_SLA.md) for building customer commitments from operational data
- **Customer impact assessment** during and after incidents

The key insight: dashboards are the first step toward operational excellence, not the final destination.

## Building Toward Operational Excellence

Effective dashboard implementation follows a progression:

### Phase 1: Visibility
- Implement comprehensive metrics collection
- Create dashboards for all critical services
- Establish baseline understanding of system behavior

### Phase 2: Intelligence
- Develop meaningful SLIs based on dashboard observations
- Set warning and error thresholds informed by historical data
- Create automated alerting for actionable problems

### Phase 3: Automation
- Build self-healing systems that respond to threshold breaches
- Implement capacity management based on trending data
- Create feedback loops that improve system reliability over time

## Key Takeaways for Engineering Leaders

### For Engineering Teams
1. **Build trustworthy dashboards for every service** - they're essential components of feature delivery, not afterthoughts
2. **Share dashboard patterns across teams** to create consistency and reduce learning curves
3. **Learn from every outage** by asking "What dashboards would have helped us identify this problem sooner?"

### For Engineering Managers
- **Treat dashboard development as infrastructure investment**, not optional work
- **Encourage cross-team collaboration** on monitoring standards and practices
- **Measure dashboard effectiveness** by how well they support incident response and capacity planning

### For Senior Leaders
- **Recognize that dashboards enable business visibility** into technical operations
- **Support investment in monitoring infrastructure** as a foundation for system reliability
- **Understand that passive monitoring alone is insufficient** for production systems

## The Path Forward

Dashboards serve as the foundation for operational excellence, but they're not the complete solution. Teams that understand this distinction build monitoring systems that actually improve reliability rather than just creating impressive visualizations.

The goal isn't perfect dashboards—it's building monitoring systems that enable teams to identify problems before customers do, respond quickly when issues occur, and continuously improve system reliability over time.

**Start with dashboards, but don't stop there.** Use them to build the understanding and data foundation needed for automated monitoring, alerting, and eventually, self-healing systems.

## Additional Reading

### Related Framework Posts
- **[How to Construct a Useful Dashboard](How_to_Construct_a_Useful_Dashboard.md)** - Practical guidance for building effective dashboards
- **[SOA & Microservices](SOA_and_Microservices.md)** - Understanding distributed systems that dashboards help monitor
- **[Mechanisms: Building Self-Correcting Systems](../SDLC/Mechanisms:_Building_Self-Correcting_Systems.md)** - Using dashboard insights to build automated operational processes

### Industry References
- **[Google SRE Book: Monitoring Distributed Systems](https://sre.google/sre-book/monitoring-distributed-systems/)** - Comprehensive guide to monitoring principles
- **[Golden Signals](https://sre.google/sre-book/monitoring-distributed-systems/#xref_monitoring_golden-signals)** - The four key metrics every service should monitor

-----

*Have your own templates or hard-won lessons? I'd love to hear them. Drop a comment or [open an issue](https://github.com/bordenet/Engineering_Culture/issues/new) to share.*