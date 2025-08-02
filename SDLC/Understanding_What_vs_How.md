# 🎯 What vs. How: The Critical Distinction in Engineering Leadership

*Why confusing outcomes with implementation kills projects before they start*

I've watched countless engineering projects fail not because of technical incompetence, but because teams never clearly separated **what** they were trying to achieve from **how** they planned to achieve it. This confusion leads to over-engineered solutions, missed deadlines, and products that solve the wrong problems elegantly.

The "What vs. How" distinction isn't just product management theory—it's a fundamental engineering leadership skill that determines whether your team builds the right thing, builds it efficiently, and can adapt when circumstances change.

After 26+ years of watching teams succeed and fail, I've learned that the most successful engineering leaders master this distinction early and use it to guide every major decision.

## Why This Distinction Matters

Most engineering disasters start the same way: someone presents a solution (the "how") disguised as a problem statement (the "what"). The team rallies around the proposed solution, builds it beautifully, and then discovers it doesn't actually solve the real problem.

**The stakes are real**: Misaligning what and how can cost months of development time, destroy team morale, and sometimes kill entire products. Get it right, and you build systems that adapt to changing requirements and deliver genuine value.

## Table of Contents

- [The What: Defining Outcomes](#the-what-defining-outcomes)
- [The How: Choosing Methods](#the-how-choosing-methods)  
- [Why Engineers Confuse Them](#why-engineers-confuse-them)
- [The Decision Framework](#the-decision-framework)
- [Common Anti-Patterns](#common-anti-patterns)
- [Practical Implementation](#practical-implementation)
- [Leading Through What vs. How](#leading-through-what-vs-how)

## The What: Defining Outcomes

**The "What" is the desired outcome, not the solution.** It answers: What problem are we solving? What value are we creating? What does success look like?

### What Good "What" Looks Like

- **Problem-focused**: Starts with customer or business pain points
- **Measurable**: Includes specific success criteria
- **Solution-agnostic**: Doesn't prescribe the implementation approach
- **Time-bound**: Has clear deadlines and milestones

**Example of clear "What":**
> "Reduce customer support ticket volume for login issues by 40% within Q2, improving customer satisfaction and reducing operational costs."

**Not:**
> "Build a single sign-on system using OAuth 2.0 and integrate it with our [microservices architecture](../EngFundamentals/SOA_and_Microservices.md)."

The second example is a "how" disguised as a "what"—it prescribes the solution before we've fully understood the problem.

### Engineering-Specific Examples

**Good "What" Statements:**
- "Reduce deployment time from 2 hours to 15 minutes while maintaining zero-downtime deployments"
- "Enable product teams to ship features independently without coordinating database migrations"
- "Provide real-time system health visibility to prevent outages before they impact customers"

**Bad "What" Statements (Actually "How" in Disguise):**
- "Implement Kubernetes with Helm charts and GitOps workflows"
- "Migrate to microservices using event sourcing and CQRS patterns"  
- "Build a React dashboard with GraphQL APIs and Redis caching"

Notice how the good examples focus on business outcomes, while the bad examples jump straight to technical solutions.

## The How: Choosing Methods

**The "How" is your implementation strategy.** It answers: What technologies will we use? What architecture patterns? What's our delivery approach?

### What Good "How" Looks Like

- **Multiple options considered**: Explores different approaches before settling on one
- **Justified choices**: Explains why this approach fits the specific context
- **Constraint-aware**: Acknowledges team capabilities, timeline, and existing systems
- **Adaptable**: Can change if circumstances shift or better options emerge

### The Hierarchy of Constraints

Good "how" decisions consider constraints in order of importance:

1. **Business constraints**: Timeline, budget, compliance requirements
2. **Team constraints**: Skills, experience, capacity
3. **Technical constraints**: Existing systems, performance requirements, scalability needs
4. **Preference constraints**: Technology choices, architectural patterns

Too many teams invert this hierarchy, leading with their preferred technologies rather than business needs.

### Engineering Implementation Examples

**For the login issue "What" above, good "How" options might include:**

**Option 1: Quick Win Approach**
- Improve error messages and add password reset flow
- Add basic monitoring and alerting
- Timeline: 2 weeks, minimal risk

**Option 2: Comprehensive Solution**  
- Implement SSO with existing identity provider
- Add multi-factor authentication
- Timeline: 8 weeks, higher complexity

**Option 3: Hybrid Approach**
- Start with quick wins for immediate impact
- Plan SSO implementation for next quarter
- Timeline: 2 weeks immediate, 6 weeks follow-up

Notice how each "how" maps back to the same "what" but with different trade-offs.

## Why Engineers Confuse Them

Understanding why smart people consistently mix up what and how helps you avoid the trap:

### The Solution-First Mindset
Engineers are trained to solve problems. When presented with a challenge, our instinct is to immediately start designing solutions. This makes us jump to "how" before fully understanding "what."

**The pattern**: 
1. Someone mentions a problem
2. An engineer immediately thinks of a technical solution
3. The solution becomes the goal
4. The original problem gets forgotten or distorted

### The Technology Fascination
We love learning new technologies. When Kubernetes, GraphQL, or the latest framework captures our attention, we start looking for problems that justify using them.

**Result**: Projects that exist primarily to explore technology rather than solve business problems.

### The Complexity Bias
Complex solutions feel more professional and intellectually satisfying than simple ones. This leads to over-engineering—building sophisticated systems to solve problems that could be fixed with configuration changes.

### The Certainty Illusion
"How" feels concrete and actionable. "What" can feel vague and political. Teams gravitate toward discussing implementation details because it feels like progress, even when they're building the wrong thing.

## The Decision Framework

Here's a practical approach for keeping what and how in proper order:

### Step 1: Define Success Criteria (What)
Before any technical discussion, write down:
- What problem are we solving?
- How will we know we've succeeded?
- Who benefits and how?
- What happens if we do nothing?

**Avoid the meeting that starts with**: "We need to migrate to microservices..."  
**Instead, start with**: "Our deployment process is blocking teams from shipping..."

### Step 2: Validate the Problem (Still What)
- Talk to people who have this problem
- Measure the current state
- Understand the costs of the status quo
- Confirm the problem is worth solving

### Step 3: Generate Options (How)
Only after steps 1-2, brainstorm implementation approaches:
- What are 3 different ways to solve this?
- What are the trade-offs of each approach?
- What constraints do we need to consider?

### Step 4: Choose and Commit (How)
Select the approach that best fits your constraints and context. Document why you chose this approach over alternatives.

### Step 5: Build and Measure (How + What)
Implement your chosen solution and measure against your original success criteria. Be prepared to adjust the "how" if you're not achieving the "what."

## Common Anti-Patterns

I've seen these patterns kill projects repeatedly:

### Anti-Pattern 1: The Solution in Search of a Problem
**Symptom**: "We should use GraphQL for our new API"  
**Problem**: Starting with technology choice instead of user needs  
**Fix**: "Our mobile team is struggling with over-fetching data. Let's explore options."

### Anti-Pattern 2: The False Urgency
**Symptom**: "We need to start migrating to microservices immediately"  
**Problem**: Creating urgency around implementation without establishing why  
**Fix**: "Our deployment bottlenecks are costing us X days per quarter. Here's how we'll address them."

### Anti-Pattern 3: The Vague Business Case
**Symptom**: "This will improve performance"  
**Problem**: Unmeasurable outcomes that can't be validated  
**Fix**: "This will reduce page load time from 3 seconds to under 1 second for 80% of users."

### Anti-Pattern 4: The Technology Resume Building
**Symptom**: Choosing technologies based on what engineers want to learn  
**Problem**: Optimizing for individual growth over business needs  
**Fix**: Match technology choices to problem requirements and team capabilities

### Anti-Pattern 5: The Perfectionist Trap
**Symptom**: "We need to get the architecture right before we can build anything"  
**Problem**: Over-designing based on hypothetical future requirements  
**Fix**: Start with the simplest solution that addresses current needs, then evolve

## Practical Implementation

### For Individual Contributors

**In meetings, ask these questions:**
- What problem are we trying to solve?
- How will we measure success?
- What are alternative approaches?
- Why is this approach better than simpler options?

**When writing design docs:**
1. Start with problem statement and success criteria
2. Explore multiple implementation options
3. Justify your chosen approach
4. Include measurement plan

See [Project Planning: A Practical Guide to Documents](Project_Planning_Mechanisms:_Documents.md) for specific guidance on which document types best capture "what" vs "how" decisions.

### For Engineering Managers

**Use the "What vs. How" lens to evaluate proposals:**
- Is this solving a real business problem?
- Are we considering multiple implementation approaches?
- Do we have clear success metrics?
- Can we start simpler and evolve?

**In planning sessions:**
- Demand clear problem statements before discussing solutions
- Push back on technology-first proposals
- Ask for measurement plans, not just delivery plans

### For Senior Leaders

**Set organizational expectations:**
- All project proposals must start with problem definition
- Technical decisions require business justification
- Teams must consider multiple implementation approaches
- Success is measured by outcomes, not outputs

**Create incentives:**
- Reward teams that solve problems simply
- Celebrate when teams change approach based on new information
- Measure and share the business impact of engineering work

## Leading Through What vs. How

### The Art of Productive Tension

Great engineering leaders create productive tension between what and how:

- **Push back on solutions** that don't have clear problem statements
- **Challenge assumptions** about why certain approaches are necessary
- **Demand measurement plans** for all significant engineering investments
- **Celebrate pivots** when teams discover better ways to achieve their goals

### Building the Right Culture

Teams that excel at this distinction share common practices:

**They start meetings with problem context**, not solution proposals  
**They measure business impact**, not just technical metrics  
**They treat architecture as a means**, not an end  
**They're comfortable changing approach** when they learn new information

### The Leadership Mindset

As an engineering leader, your job is to:

1. **Protect the "what"** from being diluted by implementation details
2. **Enable great "how" decisions** by providing context and constraints
3. **Create space for iteration** between what and how as you learn
4. **Model the behavior** by always leading with problem statements

The most successful engineering organizations I've worked with have leaders who are equally comfortable challenging vague problem statements and pushing back on over-engineered solutions.

## The Bottom Line

Separating what from how isn't academic—it's the difference between building systems that matter and building impressive solutions to problems that don't exist.

**Master the "what" first**: Clear problem definitions, measurable outcomes, validated user needs. Without this foundation, even perfect execution leads to beautiful failures.

**Optimize the "how"**: Once you're solving the right problem, choose the simplest approach that meets your constraints. You can always evolve toward sophistication as you learn.

**Stay connected**: Regularly check that your "how" is still serving your "what." The best teams pivot implementation approaches while staying locked on their desired outcomes.

The engineering world is full of elegant solutions looking for problems. Don't be one of them. Lead with what, then figure out how.

## Additional Reading

### Essential Framework Connections
- **[The PR-FAQ Mechanism](The_PR-FAQ.md)** - Amazon's approach to defining "what" before exploring "how"
- **[The One-Pager](The_One-Pager.md)** - Distilling both what and how into clear, actionable summaries
- **[People-Process-Technology Triad](../Culture/People_-_Process_-_Technology_Triad.md)** - Why technology choices (the "how") should serve people and process needs (the "what")

### Recommended Books
- **[Working Backwards](https://www.workingbackwards.com/)** by Colin Bryar - Amazon's systematic approach to separating customer needs from implementation details
- **[The Lean Startup](http://theleanstartup.com/)** by Eric Ries - Build-measure-learn cycles that keep "how" aligned with "what"
- **[Escaping the Build Trap](https://melissaperri.com/book)** by Melissa Perri - Product management principles that apply to engineering leadership

-----

*Have your own templates or hard-won lessons? I'd love to hear them. Drop a comment or [open an issue](https://github.com/bordenet/Engineering_Culture/issues/new) to share.*
