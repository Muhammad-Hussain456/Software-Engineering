## 1.2 Software Process Models & Methods

### 📌 Learning Objectives

By the end of this section, you should be able to:
- Define a **software process** and explain why it matters
- Compare and contrast **plan-driven vs. agile** approaches
- Describe the **Waterfall model**: phases, strengths, weaknesses, and appropriate use cases
- Describe **Incremental and Iterative** development
- Explain the **Spiral model** and its risk-driven nature
- Articulate the **Agile Manifesto** and its core values and principles
- Differentiate between **Scrum** and **Extreme Programming (XP)**
- Select appropriate process models for different project contexts

---

### 1.2.1 What Is a Software Process?

#### Definition

A **software process** is a structured set of activities required to develop a software system. It defines:

- **What** activities to perform
- **When** to perform them (sequence and timing)
- **Who** performs them (roles and responsibilities)
- **How** to perform them (methods and tools)

#### Why Process Matters

| Without Process | With Process |
|-----------------|--------------|
| Ad-hoc "code and fix" | Systematic, repeatable approach |
| Quality depends on individual heroics | Quality is built into the process |
| Unpredictable schedules | Measurable progress |
| High risk of failure | Risk managed proactively |
| Knowledge lost when people leave | Knowledge captured in artifacts |

> **🔑 Key Insight:** A process doesn't guarantee success, but it dramatically improves predictability. The NSCT expects you to understand that process selection is a **strategic decision** based on project characteristics.

---

### 1.2.2 Plan-Driven vs. Agile: The Fundamental Divide

This is one of the most important distinctions in software engineering. The NSCT frequently tests understanding of when to use each approach.

| Dimension | **Plan-Driven (Waterfall-style)** | **Agile** |
|-----------|----------------------------------|-----------|
| **Philosophy** | Predictability over flexibility | Flexibility over predictability |
| **Requirements** | Defined up front, change controlled | Emergent, change embraced |
| **Planning** | Detailed upfront plan for entire project | Rolling-wave planning; detailed only for near term |
| **Customer Involvement** | At milestones and phase reviews | Continuous, daily collaboration |
| **Delivery** | Single delivery at project end | Frequent, incremental delivery (every 1-4 weeks) |
| **Documentation** | Comprehensive, formal | "Just enough," working software prioritized |
| **Team Structure** | Hierarchical, specialized roles | Cross-functional, self-organizing teams |
| **Success Metric** | Conformance to plan | Delivering value to customer |
| **Best For** | Safety-critical, stable requirements, regulated domains | Exploratory, fast-changing markets, startups |

#### When to Choose Plan-Driven

```
✓ Requirements are stable and well-understood
✓ System is safety-critical (medical devices, aviation)
✓ Regulatory compliance requires extensive documentation
✓ Fixed-price contract with clearly defined scope
✓ Large distributed teams where coordination requires formal interfaces
✓ Organization has established plan-driven culture
```

#### When to Choose Agile

```
✓ Requirements are uncertain or expected to change
✓ Customer is available for continuous collaboration
✓ Project needs to deliver value quickly (time-to-market critical)
✓ Team is small to medium-sized (ideally < 10 people)
✓ Organization supports autonomy and experimentation
✓ Technical risk is manageable; primary risk is requirements uncertainty
```

> **🔑 Key Insight:** The choice isn't binary. Many successful projects use a **hybrid approach**—plan-driven for high-risk, stable components; agile for exploratory, customer-facing parts.

---

### 1.2.3 Waterfall Model

Also known as the **Classic Lifecycle** or **Linear Sequential Model**. The first published process model (Winston Royce, 1970—though Royce actually criticized it as risky).

#### Phases of Waterfall

```
┌─────────────────────────────────────────────────────────────────┐
│                                                               │
│   ┌──────────┐    ┌──────────┐    ┌──────────┐              │
│   │Requirements│───▶│  Design  │───▶│Implementation│              │
│   └──────────┘    └──────────┘    └──────────┘              │
│         │              │               │                      │
│         ▼              ▼               ▼                      │
│   ┌──────────┐    ┌──────────┐    ┌──────────┐              │
│   │Verification│   │Verification│   │   Unit    │              │
│   │& Validation│   │& Validation│   │  Testing  │              │
│   └──────────┘    └──────────┘    └──────────┘              │
│                                       │                      │
│                                       ▼                      │
│                                  ┌──────────┐               │
│                                  │Integration│               │
│                                  │  Testing  │               │
│                                  └──────────┘               │
│                                       │                      │
│                                       ▼                      │
│                                  ┌──────────┐               │
│                                  │  System  │               │
│                                  │  Testing  │               │
│                                  └──────────┘               │
│                                       │                      │
│                                       ▼                      │
│                                  ┌──────────┐               │
│                                  │Operation │               │
│                                  │& Maintenance│            │
│                                  └──────────┘               │
└─────────────────────────────────────────────────────────────────┘
```

#### Phase Details

| Phase | Activities | Outputs |
|-------|------------|---------|
| **Requirements** | Elicit, analyze, document, validate | Software Requirements Specification (SRS) |
| **Design** | Architecture, component design, interfaces, data structures | Design Document, UML diagrams |
| **Implementation** | Coding, unit testing | Source code, unit test results |
| **Testing** | Integration, system, acceptance testing | Test reports, validated system |
| **Operation & Maintenance** | Deployment, bug fixes, enhancements | Updated versions, support documentation |

#### Strengths

| Strength | Explanation |
|----------|-------------|
| **Simple and understandable** | Easy to explain to stakeholders |
| **Phase completion checkpoints** | Clear milestones for progress tracking |
| **Disciplined approach** | Forces documentation and planning |
| **Works for stable requirements** | When requirements won't change, it's efficient |

#### Weaknesses

| Weakness | Explanation |
|----------|-------------|
| **Late feedback** | Customer sees working software only at the end |
| **Inflexible to change** | Changes require going back to earlier phases |
| **Sequential assumption** | Reality has overlap between phases |
| **Documentation heavy** | Creates overhead, especially for small projects |
| **Risk ignored until testing** | Technical risks surface late |

> **🔑 Key Insight:** Royce's original paper described Waterfall but noted it was "risky and invites failure." He recommended doing it at least twice (iterating) to reduce risk.

#### When to Use Waterfall

```
✓ Requirements are stable and well-understood
✓ Project is small to medium with clear scope
✓ Technology is well-understood (no technical exploration needed)
✓ Customer is not available for continuous collaboration
✓ Regulatory compliance requires phase documentation
✓ Fixed-price contract with penalties for scope change
```

---

### 1.2.4 Incremental & Iterative Development

These concepts are often confused. Understanding the distinction is important for NSCT.

#### Iterative vs. Incremental

| Concept | Definition | Analogy |
|---------|------------|---------|
| **Iterative** | Refine through repeated cycles; start with a rough version and improve each time | Sketching a portrait—start with rough shapes, then add detail, then refine |
| **Incremental** | Build in pieces; deliver parts of functionality, then add more | Building a house—first the foundation, then frame, then roof, then interior |

#### Iterative Development

```
Cycle 1: ┌────────────────────────────────────────────────────┐
         │ Basic UI │ Simple Logic │ Test │ Learn │ Refine │
         └────────────────────────────────────────────────────┘
                                    │
                                    ▼
Cycle 2: ┌────────────────────────────────────────────────────┐
         │ Improved UI │ More Logic │ Test │ Learn │ Refine │
         └────────────────────────────────────────────────────┘
                                    │
                                    ▼
Cycle 3: ┌────────────────────────────────────────────────────┐
         │ Final UI │ Complete Logic │ Full Test │ Deploy │
         └────────────────────────────────────────────────────┘
```

#### Incremental Development

```
Version 1: ┌──────────────────────────────┐
           │ Login │ Dashboard │ Logout │
           └──────────────────────────────┘
                                    │
                                    ▼
Version 2: ┌─────────────────────────────────────────────┐
           │ + Profile │ + Settings │ + Password Reset │
           └─────────────────────────────────────────────┘
                                    │
                                    ▼
Version 3: ┌─────────────────────────────────────────────┐
           │ + Search │ + Notifications │ + API Access │
           └─────────────────────────────────────────────┘
```

#### Combined Approach: Iterative & Incremental

Most modern processes (including Agile) use **both**:
- **Iterative:** Each sprint refines the product based on feedback
- **Incremental:** Each sprint delivers working, valuable functionality

> **🔑 Key Insight:** Waterfall is neither iterative nor incremental. Agile is both. The NSCT expects you to understand that Agile's power comes from combining iterative refinement with incremental delivery.

---

### 1.2.5 Spiral Model

Developed by Barry Boehm (1986) as a **risk-driven** process model. It combines elements of Waterfall and prototyping with explicit risk management.

#### Structure

The spiral model is represented as a spiral where each loop represents one phase:

```
                      ┌─────────────────────────────┐
                      │   Cumulative Cost          │
                      │         │                   │
                      │         ▼                   │
                      │    ┌─────────────────┐     │
                      │    │                 │     │
                  ┌───┼────┼───┐ Risk       │     │
                  │   │    │   │ Analysis   │     │
                  │   │    │   │   ┌────────▼─────┐
                  │   │    │   └───► Prototype 2 │
                  │   │    │       └──────────────┘
                  │   │    │
                  │   │    │   Risk Analysis
                  │   │    │   ┌─────────────┐
                  │   │    └───► Prototype 1│
                  │   │        └─────────────┘
                  │   │
                  │   │   Operational
                  │   │   Prototype
                  │   │
                  │   ▼
                  │   ┌─────────────────────────────┐
                  └───┤ Requirements                │
                      │ Planning                    │
                      │                             │
                      │                             │
                      └─────────────────────────────┘
```

#### Four Quadrants per Loop

| Quadrant | Activity | Purpose |
|----------|----------|---------|
| **1** | Determine objectives, alternatives, constraints | Define what to build and what options exist |
| **2** | Identify and resolve risks | Analyze risks; prototype to mitigate |
| **3** | Develop and verify next-level product | Build and test |
| **4** | Plan next iteration | Review progress; plan next loop |

#### Strengths

| Strength | Explanation |
|----------|-------------|
| **Risk management** | Risks are explicitly identified and addressed each loop |
| **Flexible** | Can accommodate changes between loops |
| **Early risk resolution** | High-risk issues are tackled first |
| **Scalable** | Works for large, complex projects |

#### Weaknesses

| Weakness | Explanation |
|----------|-------------|
| **Complex** | Requires experienced risk management expertise |
| **Risk assessment skill** | Success depends on accurate risk identification |
| **Not widely adopted** | Less common than Waterfall or Agile; can be heavy |

#### When to Use Spiral

```
✓ Large, complex, high-risk projects
✓ Technical risk is significant (new technology, integration challenges)
✓ Requirements are complex and may evolve
✓ Organization has experience with risk management
✓ Safety-critical systems where failure is unacceptable
```

> **🔑 Key Insight:** The Spiral model is the first process model to treat **risk management** as a primary activity rather than an afterthought.

---

### 1.2.6 Agile Software Development

#### The Agile Manifesto (2001)

Seventeen software practitioners met at Snowbird, Utah, and created the Agile Manifesto:

> **We are uncovering better ways of developing software by doing it and helping others do it. Through this work we have come to value:**

> **Individuals and interactions** over processes and tools
> **Working software** over comprehensive documentation
> **Customer collaboration** over contract negotiation
> **Responding to change** over following a plan

> *That is, while there is value in the items on the right, we value the items on the left more.*

#### The 12 Agile Principles

| # | Principle |
|---|-----------|
| 1 | Our highest priority is to satisfy the customer through early and continuous delivery of valuable software |
| 2 | Welcome changing requirements, even late in development |
| 3 | Deliver working software frequently, from a couple of weeks to a couple of months |
| 4 | Business people and developers must work together daily throughout the project |
| 5 | Build projects around motivated individuals. Give them the environment and support they need, and trust them |
| 6 | The most efficient and effective method of conveying information is face-to-face conversation |
| 7 | Working software is the primary measure of progress |
| 8 | Agile processes promote sustainable development. Sponsors, developers, and users should be able to maintain a constant pace indefinitely |
| 9 | Continuous attention to technical excellence and good design enhances agility |
| 10 | Simplicity—the art of maximizing the amount of work not done—is essential |
| 11 | The best architectures, requirements, and designs emerge from self-organizing teams |
| 12 | At regular intervals, the team reflects on how to become more effective, then tunes and adjusts its behavior accordingly |

> **🔑 Key Insight:** The Agile Manifesto is not a process—it's a **set of values and principles**. Scrum and XP are *implementations* of these values.

---

### 1.2.7 Scrum

Scrum is the most widely used Agile framework. It's lightweight, simple to understand, but difficult to master.

#### Scrum Roles

| Role | Responsibility |
|------|----------------|
| **Product Owner** | Manages the Product Backlog; prioritizes work; represents stakeholders; defines what to build |
| **Scrum Master** | Facilitates Scrum events; removes impediments; coaches the team; protects team from external interference |
| **Development Team** | Self-organizing, cross-functional group (typically 3-9 members) who build the product |

> **⚠️ Important:** In Scrum, there is no "project manager" role. The traditional PM responsibilities are distributed among the Product Owner (what) and Scrum Master (how).

#### Scrum Artifacts

| Artifact | Description |
|----------|-------------|
| **Product Backlog** | Ordered list of everything needed in the product; dynamic and continuously refined |
| **Sprint Backlog** | Set of Product Backlog items selected for the current Sprint; includes a plan for delivering them |
| **Increment** | The sum of all completed Product Backlog items at the end of a Sprint; must be "Done" (potentially releasable) |

#### Scrum Events (Ceremonies)

| Event | Timebox | Purpose |
|-------|---------|---------|
| **Sprint** | 1-4 weeks | Fixed timebox where a usable increment is created |
| **Sprint Planning** | 8 hours for 4-week sprint | Team selects items from Product Backlog and defines Sprint Goal |
| **Daily Scrum** | 15 minutes | Daily stand-up; plan next 24 hours; inspect progress |
| **Sprint Review** | 4 hours for 4-week sprint | Inspect increment; adapt Product Backlog; stakeholders provide feedback |
| **Sprint Retrospective** | 3 hours for 4-week sprint | Inspect team process; identify improvements for next Sprint |

#### Scrum Flow Diagram

```
┌─────────────────────────────────────────────────────────────────────────────┐
│                                                                             │
│   Product Backlog          Sprint Backlog          Increment               │
│   ┌─────────────┐          ┌─────────────┐        ┌─────────────┐         │
│   │ Item 1      │          │ Item A      │        │             │         │
│   │ Item 2      │          │ Item B      │        │  Working    │         │
│   │ Item 3      │─────────▶│ Item C      │────────▶│  Software   │         │
│   │ Item 4      │          │ Plan        │        │             │         │
│   │ ...         │          └─────────────┘        └─────────────┘         │
│   └─────────────┘                ▲                       │                 │
│          │                        │                       │                 │
│          │                        │                       ▼                 │
│          │              ┌─────────────────┐     ┌─────────────┐           │
│          │              │    Sprint       │     │ Sprint      │           │
│          └─────────────▶│   Planning      │     │ Review      │           │
│                         └─────────────────┘     └─────────────┘           │
│                                                                             │
│                         ┌─────────────────┐                                │
│                         │   Daily Scrum   │◀─── Daily inspection          │
│                         └─────────────────┘                                │
│                                                                             │
│                         ┌─────────────────┐                                │
│                         │   Retrospective │◀─── Process improvement       │
│                         └─────────────────┘                                │
│                                                                             │
└─────────────────────────────────────────────────────────────────────────────┘
```

---

### 1.2.8 Extreme Programming (XP)

XP is an Agile methodology focused on **engineering practices** for high-quality software. While Scrum focuses on management, XP focuses on technical excellence.

#### Core XP Practices

| Practice | Description |
|----------|-------------|
| **Test-Driven Development (TDD)** | Write test first, then write code to pass it |
| **Pair Programming** | Two developers work together at one workstation |
| **Continuous Integration** | Code is integrated and tested multiple times daily |
| **Simple Design** | Build the simplest solution that works; refactor when needed |
| **Small Releases** | Release frequently (every 1-3 weeks) |
| **Sustainable Pace** | 40-hour week; avoid burnout |
| **Collective Ownership** | Anyone can change any code |
| **Coding Standards** | Consistent style across the team |
| **On-Site Customer** | Customer available full-time to answer questions |
| **Refactoring** | Continuously improve code without changing behavior |

#### XP Values

| Value | Meaning |
|-------|---------|
| **Communication** | Face-to-face conversation; pair programming |
| **Simplicity** | Do the simplest thing that could possibly work |
| **Feedback** | Tests, customer feedback, continuous integration |
| **Courage** | Refactor code; discard bad code; make tough decisions |
| **Respect** | Respect teammates, customers, and the codebase |

#### Scrum vs. XP Comparison

| Dimension | Scrum | XP |
|-----------|-------|-----|
| **Primary Focus** | Project management | Engineering practices |
| **Roles** | Product Owner, Scrum Master, Team | Developer, Customer, Coach, Tracker |
| **Practices** | Sprints, backlog, ceremonies | TDD, pair programming, refactoring |
| **Prescriptiveness** | Framework (what to do) | Methodology (how to do it) |
| **Team Size** | 3-9 | 2-10 |
| **Change** | Changes between sprints | Welcomes changes anytime |

> **🔑 Key Insight:** Scrum and XP are **complementary**. Many teams use Scrum for management and XP for technical practices. The NSCT expects you to know the distinction.

---

### 1.2.9 Process Model Summary Comparison

| Model | Approach | Risk Handling | Customer Involvement | Documentation | Best For |
|-------|----------|---------------|---------------------|---------------|---------|
| **Waterfall** | Linear sequential | Late (after testing) | At milestones | Heavy | Stable requirements, safety-critical |
| **Incremental** | Build in pieces | Distributed across increments | After each increment | Moderate | Early value delivery |
| **Spiral** | Risk-driven | Continuous, explicit | At review points | Heavy (but flexible) | High-risk, large systems |
| **Scrum** | Agile (management) | Through inspection and adaptation | Continuous (Product Owner) | "Just enough" | Uncertain requirements, fast delivery |
| **XP** | Agile (engineering) | Through TDD and continuous integration | Continuous (on-site customer) | Minimal | Technical quality, small teams |

---

### 💡 Study Activity: Deep Dive

#### Activity 1: Comparison Charts

Create these comparison charts to solidify your understanding:

**1. Waterfall vs. Agile**

| Dimension | Waterfall | Agile |
|-----------|-----------|-------|
| Requirements timing | Fixed up front | Emergent throughout |
| Customer involvement | Milestones only | Continuous daily |
| Delivery | Single at end | Frequent increments |
| Team structure | Hierarchical | Self-organizing |
| Success measure | Plan conformance | Value delivered |

**2. Scrum vs. XP**

| Dimension | Scrum | XP |
|-----------|-------|-----|
| Focus | Management framework | Engineering practices |
| Key roles | Product Owner, Scrum Master | Customer, Developer |
| Key practices | Sprints, backlog | TDD, pair programming |
| Output | Potentially releasable increment | High-quality, tested code |

#### Activity 2: Decision Scenarios

For each scenario, recommend a process model and justify your choice:

**Scenario A:** A medical device company needs software for a pacemaker. Requirements are strictly regulated by FDA. Failure could be fatal.

<details>
<summary>Click for answer</summary>
<strong>Waterfall or Spiral.</strong> Safety-critical systems require extensive documentation, verification at each phase, and formal change control. Waterfall provides clear phase gates. Spiral adds explicit risk management for safety analysis.
</details>

**Scenario B:** A startup is building a mobile app for an undefined market. They need to test ideas quickly and pivot based on user feedback.

<details>
<summary>Click for answer</summary>
<strong>Agile (Scrum + XP).</strong> Requirements are uncertain; fast feedback is essential. Scrum provides iterative delivery; XP ensures technical quality doesn't suffer from rapid changes.
</details>

**Scenario C:** A government agency needs a system with 50+ teams across three countries. Requirements are stable but the project is massive in scale.

<details>
<summary>Click for answer</summary>
<strong>Hybrid (Plan-driven with Agile teams).</strong> Large scale requires formal coordination and interfaces (plan-driven), but individual teams can work with Agile practices internally.
</details>

#### Activity 3: Agile Manifesto Interpretation

Match each Agile principle to the value it supports:

| Principle | Value |
|-----------|-------|
| "Deliver working software frequently" | |
| "Welcome changing requirements" | |
| "Business people and developers work together daily" | |
| "Continuous attention to technical excellence" | |
| "Self-organizing teams" | |

<details>
<summary>Click for answer</summary>
| Principle | Value |
|-----------|-------|
| "Deliver working software frequently" | Working software |
| "Welcome changing requirements" | Responding to change |
| "Business people and developers work together daily" | Customer collaboration |
| "Continuous attention to technical excellence" | Individuals and interactions (quality) |
| "Self-organizing teams" | Individuals and interactions |
</details>

---

### 📝 Self-Assessment Quiz

Test yourself on Section 1.2:

1. What is the fundamental difference between plan-driven and Agile approaches?

   <details>
   <summary>Click for answer</summary>
   Plan-driven prioritizes predictability and conformance to plan; Agile prioritizes flexibility and responding to change.
   </details>

2. Name the five phases of the Waterfall model in order.

   <details>
   <summary>Click for answer</summary>
   Requirements → Design → Implementation → Testing → Operation & Maintenance
   </details>

3. What is the key weakness of the Waterfall model?

   <details>
   <summary>Click for answer</summary>
   Inflexibility to change; customer sees working software only at the end; risk isn't addressed until testing.
   </details>

4. What is the difference between iterative and incremental development?

   <details>
   <summary>Click for answer</summary>
   Iterative = refining through repeated cycles (getting better). Incremental = building in pieces (adding more).
   </details>

5. What makes the Spiral model unique among process models?

   <details>
   <summary>Click for answer</summary>
   It is risk-driven; each loop explicitly identifies and resolves risks before development.
   </details>

6. What are the four values of the Agile Manifesto?

   <details>
   <summary>Click for answer</summary>
   (1) Individuals and interactions over processes and tools; (2) Working software over comprehensive documentation; (3) Customer collaboration over contract negotiation; (4) Responding to change over following a plan.
   </details>

7. What are the three roles in Scrum?

   <details>
   <summary>Click for answer</summary>
   Product Owner, Scrum Master, Development Team.
   </details>

8. What is the primary focus of Extreme Programming (XP)?

   <details>
   <summary>Click for answer</summary>
   Engineering practices for high-quality software, including TDD, pair programming, and continuous integration.
   </details>

9. Which process model would you choose for a project with high technical risk but stable requirements?

   <details>
   <summary>Click for answer</summary>
   Spiral model—it is designed for high-risk projects with explicit risk management in each loop.
   </details>

10. What is the timebox for a Daily Scrum?

    <details>
    <summary>Click for answer</summary>
    15 minutes.
    </details>

---

### 🔗 Connections to Upcoming Modules

| Concept from 1.2 | Connects to |
|------------------|-------------|
| Waterfall requirements phase | Module 2: Requirements Engineering |
| Agile user stories | Module 2: Requirements Engineering |
| Design phase | Module 3: System Modeling & Design |
| Architecture decisions | Module 4: Software Architecture |
| Sprint planning, estimation | Module 5: Project Management |
| TDD, continuous integration | Module 6: Software Testing |
| XP practices | Module 6: Software Testing |

---

### ✅ Section 1.2 Summary

| Key Takeaway | Explanation |
|--------------|-------------|
| **Process defines the "how"** | A software process structures development activities |
| **Plan-driven vs. Agile** | Fundamental trade-off: predictability vs. flexibility |
| **Waterfall** | Sequential phases; best for stable, safety-critical systems |
| **Incremental/Iterative** | Building in pieces and refining through cycles |
| **Spiral** | Risk-driven; each loop addresses risks before development |
| **Agile Manifesto** | Four values, twelve principles; mindset over method |
| **Scrum** | Management framework; roles, artifacts, events |
| **XP** | Engineering practices; TDD, pair programming, CI |

---
