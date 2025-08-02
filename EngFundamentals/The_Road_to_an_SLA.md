# 🎯 The Road to an SLA: From Metrics to Customer Commitments

*How to build Service Level Agreements that protect your business while enabling growth*

Building your first Service Level Agreement (SLA) is a milestone that signals business maturity. When customers start asking "What guarantee can you give me about availability?" you've moved beyond the startup phase into serious business territory.

This post walks through the systematic approach to building SLAs that are both achievable for engineering teams and meaningful for customers. The key insight: SLAs aren't arbitrary numbers—they're the culmination of disciplined measurement and operational excellence.

> [!NOTE]
> **Essential Reading**: [Google SRE Book - Service Level Objectives](https://sre.google/sre-book/service-level-objectives/) provides the foundational concepts this post builds upon.

## Table of Contents

- [Why SLAs Matter: The Business Reality](#why-slas-matter-the-business-reality)
- [The SLA Hierarchy: SLI → SLO → SLA](#the-sla-hierarchy-sli--slo--sla)
- [Building Your First SLIs: What to Measure](#building-your-first-slis-what-to-measure)
- [Setting Realistic SLOs: Internal Targets](#setting-realistic-slos-internal-targets)
- [Crafting Customer SLAs: External Commitments](#crafting-customer-slas-external-commitments)
- [The Buffer Zone: Why SLOs Should Exceed SLAs](#the-buffer-zone-why-slos-should-exceed-slas)
- [Implementation Roadmap](#implementation-roadmap)
- [Common Pitfalls and How to Avoid Them](#common-pitfalls-and-how-to-avoid-them)

## Why SLAs Matter: The Business Reality

Successful businesses with sophisticated customers will eventually face this conversation:

> "We're considering your platform for critical business operations. What availability guarantees can you provide, and what compensation can we expect if you fail to meet them?"

If you can't answer with confidence backed by data, you're not ready for enterprise customers. This isn't just about technical capability—it's about business credibility.

### The Cost of Getting It Wrong

- **Overcommit**: Promise 99.99% when you can deliver 99.5%, face constant penalties and reputation damage
- **Undercommit**: Promise 95% when competitors offer 99%, lose deals to inferior products with better guarantees
- **No commitment**: Signal operational immaturity and get excluded from serious evaluations

## The SLA Hierarchy: SLI → SLO → SLA

Understanding the relationship between these concepts is crucial for building sustainable commitments:

| **Term** | **Definition** | **Audience** | **Purpose** |
|:---------|:---------------|:-------------|:------------|
| **SLI** (Service Level Indicator) | Quantifiable measurements of service performance | Engineering teams | Raw data that enables everything else |
| **SLO** (Service Level Objective) | Internal performance targets based on SLIs | Engineering teams | Goals that drive operational decisions |
| **SLA** (Service Level Agreement) | External commitments with financial consequences | Customers and business | Contractual guarantees that enable sales |

### The Flow: From Data to Commitment

```
SLIs (What we measure) → SLOs (What we target) → SLAs (What we promise)
       ↓                        ↓                       ↓
   Raw metrics          Internal goals        Customer contracts
```

## Building Your First SLIs: What to Measure

SLIs must reflect actual user experience, not just system health. Focus on metrics that directly correlate with customer success.

### The Golden Signals for SLIs

Based on Google's SRE practices, prioritize these four categories:

**1. Latency**
- Response time for successful requests
- Time to first byte, time to meaningful content
- End-to-end transaction completion time

**2. Traffic**
- Requests per second, transactions per minute
- Active user sessions, concurrent connections
- Data throughput rates

**3. Errors**
- Request failure rate, error response codes
- Transaction failure rate, timeout rates
- Service unavailability incidents

**4. Saturation**
- Resource utilization (CPU, memory, disk, network)
- Queue depths, connection pool utilization
- Capacity headroom measurements

### Industry-Specific SLI Examples

**E-commerce Platform:**
- Order completion rate (successful transactions / attempted transactions)
- Search result latency (time from query to results displayed)
- Payment processing success rate

**Communication Service:**
- Call connection success rate (successful connections / attempted calls)
- Message delivery latency (send time to receive confirmation)
- Audio/video quality metrics (packet loss, jitter)

**Data Processing Platform:**
- Job completion rate (successful jobs / submitted jobs)
- Data processing latency (ingestion to availability)
- Data accuracy rate (correct results / total results)

## Setting Realistic SLOs: Internal Targets

SLOs are the bridge between what you can measure (SLIs) and what you can promise (SLAs). They must be achievable based on current operational capability while driving improvement.

### The SLO Development Process

**1. Analyze Historical Data**
- Study at least 3-6 months of SLI data if available
- Identify patterns: daily cycles, weekly trends, seasonal variations
- Calculate percentile distributions (p50, p90, p95, p99)

**2. Account for Operational Reality**
- Current incident response capabilities
- Team on-call maturity and tooling quality
- Known technical debt and system limitations

**3. Set Stretch Goals**
- SLOs should be challenging but achievable
- Too easy: no operational improvement pressure
- Too hard: constant failure and alert fatigue

### Example SLO Setting

**Scenario**: API service with historical 99.7% availability

**Analysis**:
- Current MTTR (Mean Time To Recovery): 2 hours
- Typical outages: 1-2 per month, lasting 30-90 minutes
- Team on-call maturity: developing but improving

**Realistic SLO**: 99.5% monthly availability
- Allows for ~3.6 hours of downtime per month
- Provides buffer for operational growth
- Achievable with current capabilities

## Crafting Customer SLAs: External Commitments

SLAs are business contracts with real financial consequences. They must be conservative enough to avoid frequent penalties while competitive enough to win deals.

### SLA Design Principles

**1. Customer-Focused Metrics**
Use SLIs that directly impact customer business operations:
- ✅ "API responses within 200ms for 99% of requests"
- ❌ "Server CPU utilization below 80%"

**2. Clear Measurement Windows**
Define exactly how and when you measure:
- Monthly rolling windows (most common)
- Business hours vs. 24/7 coverage
- Planned maintenance exclusions

**3. Appropriate Penalties**
Structure penalties that are meaningful but not business-threatening:
- Service credits (percentage of monthly fee)
- Additional service extensions
- Escalation paths for severe breaches

### SLA Structure Template

```
Service Level Agreement: [Service Name]

Commitment: [Specific measurable objective]
Measurement: [How and when measured]
Exclusions: [Planned maintenance, force majeure, etc.]
Remedy: [Service credits or compensation for breach]

Example:
Commitment: 99.9% API availability during business hours
Measurement: Monthly rolling window, business hours (8 AM - 6 PM local time)
Exclusions: Scheduled maintenance with 48-hour notice
Remedy: 10% service credit for each 0.1% below target
```

## The Buffer Zone: Why SLOs Should Exceed SLAs

The gap between internal objectives and external commitments provides operational safety and enables continuous improvement.

### Calculating Your Buffer

**Conservative Approach** (recommended for new services):
- SLO should be 10x more strict than SLA
- If SLA is 99% (1% error budget), SLO should be 99.9% (0.1% error budget)

**Mature Service Approach**:
- SLO should be 2-3x more strict than SLA
- If SLA is 99.9% (0.1% error budget), SLO should be 99.95% (0.05% error budget)

### Using the Buffer Productively

The buffer isn't just safety margin—it's operational capacity:
- **Planned experiments**: Chaos engineering, load testing
- **Deployment flexibility**: Blue-green deployments, canary releases
- **Innovation time**: Technical debt reduction, performance optimization

## Implementation Roadmap

### Phase 1: Foundation (Months 1-2)
1. **Implement comprehensive SLI collection** across critical services
2. **Build initial dashboards** showing key metrics trends—see [What Dashboards Are Good For](What_Dashboards_are_Good_For.md) for guidance
3. **Establish baseline understanding** of current performance

### Phase 2: Internal Targets (Months 3-4)
1. **Set realistic SLOs** based on historical data and operational capability
2. **Create alerting systems** that notify teams when SLOs are at risk
3. **Establish incident response processes** for SLO breaches

### Phase 3: Customer Commitments (Months 5-6)
1. **Design customer-facing SLAs** with appropriate buffers
2. **Create customer-facing status pages** showing real-time service health
3. **Implement SLA tracking and reporting** for business stakeholders

### Phase 4: Continuous Improvement (Ongoing)
1. **Regular SLA reviews** with business and engineering stakeholders
2. **Error budget management** to balance reliability and feature velocity
3. **Iterative improvement** of both technical systems and operational processes

## Common Pitfalls and How to Avoid Them

### Pitfall 1: Vanity Metrics as SLIs
**Problem**: Measuring system metrics that don't reflect user experience
**Solution**: Focus on customer-visible outcomes, not internal system health

### Pitfall 2: Unrealistic Initial SLAs
**Problem**: Promising availability levels beyond current operational capability
**Solution**: Start conservative, improve iteratively with operational maturity

### Pitfall 3: No Buffer Between SLOs and SLAs
**Problem**: Internal targets match external commitments, leaving no room for error
**Solution**: Always maintain meaningful buffer for operational flexibility

### Pitfall 4: SLAs Without Operational Discipline
**Problem**: Making commitments without the processes to maintain them
**Solution**: Build the operational foundation before making external promises

### Pitfall 5: Static SLAs That Never Evolve
**Problem**: Set-and-forget approach that doesn't reflect improving capabilities
**Solution**: Regular review cycles that adjust commitments as systems mature

## From Guesswork to Confidence

The journey from "we think our system is reliable" to "we guarantee 99.9% availability" requires systematic measurement, operational discipline, and customer focus.

SLAs aren't just technical artifacts—they're business enablers that signal operational maturity and customer commitment. Building them properly requires collaboration between engineering, product, and business teams to balance what's technically achievable with what's commercially competitive.

Start with measurement, build operational confidence through SLOs, then make commitments through SLAs that you can consistently meet. The goal isn't perfect availability—it's predictable, measurable reliability that enables business growth.

**Related Reading**: Understanding the [People-Process-Technology](../Culture/People_-_Process_-_Technology_Triad.md) framework helps ensure your organization can support the operational discipline SLAs require. Building effective [mechanisms for continuous improvement](../SDLC/Mechanisms:_Building_Self-Correcting_Systems.md) enables the systematic approach SLA management demands.

-----

*Have your own templates or hard-won lessons? I'd love to hear them. Drop a comment or [open an issue](https://github.com/bordenet/Engineering_Culture/issues/new) to share.*