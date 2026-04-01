# Module-3: Software Project Management

---

## 📌 Module Learning Objectives

By the end of this module, you should be able to:
- Understand the **role of project management** in software development
- Describe **project planning activities** (estimation, scheduling, risk management)
- Apply **estimation techniques** (COCOMO, function points, planning poker)
- Understand **Agile metrics** (velocity, burndown charts)
- Explain **risk management** processes and strategies
- Understand **team management** and **stakeholder communication**

---

## 3.1 Introduction to Software Project Management

---

### 3.1.1 What Is Software Project Management?

**Software project management** is the application of knowledge, skills, tools, and techniques to software development activities to meet project requirements.

> **🔑 Key Insight:** Project management is not just about tracking tasks—it's about delivering value within constraints while managing uncertainty.

#### The Triple Constraint (Iron Triangle)

Traditionally, project management balances three competing constraints:

```
                    ┌─────────────────────────┐
                    │                         │
                    │        SCOPE            │
                    │   (Features, Quality)   │
                    │                         │
          ┌─────────┼─────────────────────────┼─────────┐
          │         │                         │         │
          │         │                         │         │
          │  TIME   │                         │  COST   │
          │(Schedule)│                         │(Budget) │
          │         │                         │         │
          │         │                         │         │
          └─────────┼─────────────────────────┼─────────┘
                    │                         │
                    │      Cannot change      │
                    │      one without        │
                    │      affecting others   │
                    │                         │
                    └─────────────────────────┘
```

**The Reality:**
- If scope increases → time or cost must increase
- If time decreases → scope must decrease or cost increase
- If cost decreases → scope must decrease or time increase

> **🔑 Key Insight:** Modern Agile thinking adds a fourth dimension: **value**. The goal is not just to deliver on time and budget, but to deliver the most valuable features within constraints.

---

### 3.1.2 Project Management Knowledge Areas

The Project Management Institute (PMI) defines ten knowledge areas. For NSCT, focus on these:

| Knowledge Area | Description |
|----------------|-------------|
| **Integration Management** | Coordinating all aspects of the project |
| **Scope Management** | Defining and controlling what is included |
| **Schedule Management** | Ensuring timely completion |
| **Cost Management** | Planning and controlling budget |
| **Quality Management** | Meeting quality requirements |
| **Resource Management** | Managing team and physical resources |
| **Communications Management** | Stakeholder communication |
| **Risk Management** | Identifying and responding to uncertainty |
| **Stakeholder Management** | Managing expectations and engagement |

---

### 3.1.3 Project Manager Roles and Responsibilities

| Responsibility | Description |
|----------------|-------------|
| **Planning** | Define scope, create schedule, estimate effort, allocate resources |
| **Organizing** | Structure the team, define roles, establish processes |
| **Leading** | Motivate team, resolve conflicts, provide direction |
| **Controlling** | Track progress, manage changes, report status |
| **Communicating** | Manage stakeholders, facilitate meetings, document decisions |
| **Risk Management** | Identify, analyze, and mitigate risks |

#### Project Manager vs. Scrum Master

| Dimension | Project Manager (Traditional) | Scrum Master (Agile) |
|-----------|------------------------------|---------------------|
| **Role** | Command and control | Servant leader |
| **Authority** | Direct authority over resources | No authority; facilitates |
| **Focus** | Plan adherence, reporting | Process improvement, removing impediments |
| **Decision Making** | Makes decisions | Enables team to decide |
| **Success Metric** | On time, on budget | Team effectiveness, value delivery |

---

## 3.2 Project Planning

---

### 3.2.1 Work Breakdown Structure (WBS)

A **Work Breakdown Structure** is a hierarchical decomposition of the total scope of work to be carried out by the project team.

#### WBS Principles

| Principle | Description |
|-----------|-------------|
| **100% Rule** | WBS includes 100% of the work defined by the project scope |
| **Mutually Exclusive** | No overlap between elements |
| **Outcome-Oriented** | Describes deliverables, not activities |
| **Decomposable** | Can be broken down into manageable pieces |

#### WBS Example (E-Commerce Platform)

```
1.0 E-Commerce Platform
│
├── 1.1 Project Management
│   ├── 1.1.1 Project Planning
│   ├── 1.1.2 Status Reporting
│   └── 1.1.3 Stakeholder Communication
│
├── 1.2 Requirements
│   ├── 1.2.1 Requirements Elicitation
│   ├── 1.2.2 Requirements Documentation
│   └── 1.2.3 Requirements Validation
│
├── 1.3 Design
│   ├── 1.3.1 Architecture Design
│   ├── 1.3.2 Database Design
│   └── 1.3.3 UI/UX Design
│
├── 1.4 Implementation
│   ├── 1.4.1 User Authentication
│   ├── 1.4.2 Product Catalog
│   ├── 1.4.3 Shopping Cart
│   ├── 1.4.4 Order Processing
│   └── 1.4.5 Payment Integration
│
├── 1.5 Testing
│   ├── 1.5.1 Unit Testing
│   ├── 1.5.2 Integration Testing
│   ├── 1.5.3 System Testing
│   └── 1.5.4 User Acceptance Testing
│
└── 1.6 Deployment
    ├── 1.6.1 Environment Setup
    ├── 1.6.2 Data Migration
    └── 1.6.3 Production Release
```

---

### 3.2.2 Estimation Techniques

Estimation is predicting the effort, duration, and cost required to complete project work.

#### Types of Estimates

| Type | Purpose | Accuracy |
|------|---------|----------|
| **Rough Order of Magnitude** | Early decision making | -23% to +73% |
| **Budgetary Estimate** | Budget approval | -10% to +23% |
| **Definitive Estimate** | Commitments, contracts | -3% to +10% |

---

#### Technique 1: Expert Judgment

**Description:** Consulting individuals with relevant expertise to provide estimates.

| Strengths | Weaknesses |
|-----------|------------|
| Fast and inexpensive | Subject to bias |
| Leverages experience | Depends on expert availability |
| Accounts for nuance | Hard to replicate |

---

#### Technique 2: Analogous Estimation (Top-Down)

**Description:** Using historical data from similar projects to estimate the current project.

| Aspect | Details |
|--------|---------|
| **Formula** | New Estimate = Historical Effort × Similarity Factor |
| **Strengths** | Fast; uses real data |
| **Weaknesses** | Depends on truly similar projects; less accurate for novel work |

---

#### Technique 3: Parametric Estimation (COCOMO)

**Description:** Using mathematical models based on project parameters.

**COCOMO (COnstructive COst MOdel)** is one of the most widely used parametric models.

| COCOMO Mode | Description | Formula |
|-------------|-------------|---------|
| **Organic** | Small teams, familiar environment, flexible requirements | Effort = 2.4 × (KLOC)^1.03 |
| **Semi-Detached** | Medium teams, mixed experience, some constraints | Effort = 3.0 × (KLOC)^1.12 |
| **Embedded** | Tight constraints, complex integration, hardware/software | Effort = 3.6 × (KLOC)^1.20 |

**COCOMO II** adds cost drivers:
- Product attributes (reliability, complexity)
- Platform attributes (execution time, memory constraints)
- Personnel attributes (capability, experience)
- Project attributes (tools, schedule pressure)

> **🔑 Key Insight:** COCOMO is useful for large projects but requires accurate size estimation (lines of code or function points).

---

#### Technique 4: Function Point Analysis

**Description:** Estimating size based on functionality delivered to the user, independent of implementation language.

| Function Type | Description | Weight Factors |
|---------------|-------------|----------------|
| **External Inputs** | User inputs (screens, forms) | Low/Medium/High (3-6) |
| **External Outputs** | Reports, outputs to users | Low/Medium/High (4-7) |
| **External Inquiries** | Queries, lookups | Low/Medium/High (3-6) |
| **Internal Logical Files** | Databases, files maintained | Low/Medium/High (7-13) |
| **External Interface Files** | Interfaces to other systems | Low/Medium/High (3-10) |

**Process:**
1. Count each function type and apply weight
2. Calculate **Unadjusted Function Points (UFP)**
3. Apply complexity adjustment factors (14 factors, 0-3 each)
4. Calculate **Adjusted Function Points (FP)**

**Conversion:** FP can be converted to lines of code using language-specific averages:
- Java: 30-30 LOC per FP
- C++: 40-60 LOC per FP
- Python: 13-23 LOC per FP

---

#### Technique 3: Planning Poker (Agile)

**Description:** A consensus-based estimation technique used in Agile teams.

**Process:**
1. Product Owner describes a user story
2. Team discusses the story
3. Each member privately selects a story point card
4. All cards revealed simultaneously
3. If estimates differ, discuss and re-estimate
6. Repeat until consensus

**Story Points vs. Hours:**

| Dimension | Story Points | Hours |
|-----------|--------------|-------|
| **Focus** | Effort, complexity, uncertainty | Time |
| **Team-Specific** | Yes (relative to team) | Universal |
| **Stability** | Stable over time | Varies by developer |
| **Velocity** | Can track team velocity | Harder to aggregate |

> **🔑 Key Insight:** Story points measure **effort**, not time. They account for complexity and uncertainty, making them more stable than hour estimates for Agile teams.

---

### 3.2.3 Scheduling

Scheduling is determining when work will be performed and when milestones will be achieved.

#### Gantt Charts

A **Gantt chart** is a visual representation of project tasks over time.

| Component | Description |
|-----------|-------------|
| **Tasks** | Work items listed vertically |
| **Timeline** | Time scale horizontally |
| **Bars** | Duration of each task |
| **Dependencies** | Lines showing task relationships |
| **Milestones** | Key events (diamond markers) |

**Example Gantt Chart Structure:**

```
Task                    | Week 1 | Week 2 | Week 3 | Week 4 | Week 3
------------------------|--------|--------|--------|--------|--------
Requirements            | ██████ |        |        |        |
Design                  |        | ██████ | ██     |        |
Implementation          |        |        | ██████ | ██████ |
Testing                 |        |        |        | ██     | ██████
Deployment              |        |        |        |        | ██
```

---

#### Critical Path Method (CPM)

**Critical Path** is the longest path through the project network. Tasks on the critical path have zero slack—any delay delays the project.

| Concept | Description |
|---------|-------------|
| **Early Start (ES)** | Earliest a task can begin |
| **Early Finish (EF)** | ES + Duration |
| **Late Start (LS)** | Latest a task can begin without delaying project |
| **Late Finish (LF)** | LS + Duration |
| **Slack (Float)** | LS - ES (or LF - EF) |

**Critical Path Characteristics:**
- Tasks with zero slack are on the critical path
- Any delay to critical path delays project completion
- Management should focus on critical path tasks

---

#### PERT (Program Evaluation and Review Technique)

**Description:** A probabilistic scheduling technique that accounts for uncertainty.

**Three Estimates:**
- **Optimistic (O):** Best-case scenario
- **Most Likely (M):** Realistic estimate
- **Pessimistic (P):** Worst-case scenario

**Formula:**
```
Expected Duration = (O + 4M + P) / 6

Standard Deviation = (P - O) / 6
```

**Use Case:** Projects with high uncertainty where historical data is limited.

---

### 3.2.4 Resource Management

Resource management involves allocating people, tools, and facilities to project tasks.

| Resource Type | Considerations |
|---------------|----------------|
| **Human Resources** | Skills, availability, experience, location, cost |
| **Infrastructure** | Servers, network, development tools, licenses |
| **Facilities** | Office space, meeting rooms, equipment |

**Resource Leveling:** Adjusting start/finish dates to address resource constraints (e.g., avoiding over-allocation).

**Resource Smoothing:** Adjusting activities to keep resource usage within limits without changing the critical path.

---

## 3.3 Agile Project Management

---

### 3.3.1 Agile Principles for Management

The Agile Manifesto emphasizes:

| Value | Implication for Management |
|-------|---------------------------|
| **Individuals and interactions** over processes and tools | Empower teams; reduce bureaucracy |
| **Working software** over comprehensive documentation | Focus on delivery; minimize non-value work |
| **Customer collaboration** over contract negotiation | Continuous stakeholder engagement |
| **Responding to change** over following a plan | Embrace uncertainty; adapt |

---

### 3.3.2 Scrum Framework

Scrum is the most widely used Agile framework.

#### Roles

| Role | Responsibility |
|------|----------------|
| **Product Owner** | Maximizes value; manages Product Backlog; prioritizes work |
| **Scrum Master** | Facilitates process; removes impediments; coaches team |
| **Development Team** | Self-organizing; delivers increments; collectively accountable |

#### Artifacts

| Artifact | Description |
|----------|-------------|
| **Product Backlog** | Ordered list of everything needed; dynamic; refined continuously |
| **Sprint Backlog** | Set of items selected for current Sprint; includes plan to deliver |
| **Increment** | Sum of completed items; must be "Done" (potentially releasable) |

#### Events (Ceremonies)

| Event | Timebox | Purpose |
|-------|---------|---------|
| **Sprint** | 1-4 weeks | Fixed timebox for delivering increment |
| **Sprint Planning** | 8 hours (4-week sprint) | Select backlog items; define Sprint Goal |
| **Daily Scrum** | 13 minutes | Inspect progress; plan next 24 hours |
| **Sprint Review** | 4 hours (4-week sprint) | Inspect increment; adapt backlog; stakeholder feedback |
| **Sprint Retrospective** | 3 hours (4-week sprint) | Inspect process; identify improvements |

---

### 3.3.3 Agile Metrics

| Metric | Description | Purpose |
|--------|-------------|---------|
| **Velocity** | Sum of story points completed per sprint | Forecasting; capacity planning |
| **Burndown Chart** | Remaining work over time | Tracking progress; identifying slippage |
| **Burnup Chart** | Completed work over time | Tracking value delivered |
| **Cycle Time** | Time from start to completion of work | Process efficiency |
| **Lead Time** | Time from request to delivery | Customer responsiveness |
| **Cumulative Flow Diagram** | Work in progress across stages | Identifying bottlenecks |

#### Burndown Chart

```
Remaining Work
    │
 80 │ ●
    │    ●
 60 │       ●
    │          ●
 40 │             ●
    │                ●
 20 │                   ●
    │                      ●
  0 └─────────────────────────▶ Time
        1   2   3   4   3   6   Sprint Days
      
    ● Actual    ── Ideal
```

**Interpreting Burndown Charts:**
- **Above ideal line:** Behind schedule (more work remains than planned)
- **Below ideal line:** Ahead of schedule
- **Flat line:** No progress; blocked tasks
- **Upward spike:** New work added or re-estimation

---

### 3.3.4 Kanban

**Kanban** is a flow-based Agile method focused on visualizing work and limiting work in progress.

| Principle | Description |
|-----------|-------------|
| **Visualize Work** | Kanban board with columns (To Do, In Progress, Done) |
| **Limit WIP** | Maximum items in each column; prevents overload |
| **Manage Flow** | Monitor cycle time; identify bottlenecks |
| **Explicit Policies** | Clear rules for moving items |
| **Continuous Improvement** | Inspect and adapt |

**Kanban vs. Scrum:**

| Dimension | Scrum | Kanban |
|-----------|-------|--------|
| **Cadence** | Fixed timebox (Sprints) | Continuous flow |
| **Roles** | Defined (PO, SM, Team) | Optional |
| **Work Limits** | Sprint capacity | WIP limits |
| **Changes** | Between sprints | Any time |
| **Metrics** | Velocity | Cycle time, throughput |

---

## 3.4 Risk Management

---

### 3.4.1 What Is Risk?

> **Risk** is an uncertain event or condition that, if it occurs, has a positive or negative effect on project objectives.

| Type | Description |
|------|-------------|
| **Threat (Negative Risk)** | Potential harm to project (delay, cost overrun, failure) |
| **Opportunity (Positive Risk)** | Potential benefit (early delivery, cost savings, new capability) |

---

### 3.4.2 Risk Management Process

```
┌─────────────────────────────────────────────────────────────────────────────┐
│                         Risk Management Process                             │
├─────────────────────────────────────────────────────────────────────────────┤
│                                                                             │
│   ┌──────────────┐    ┌──────────────┐    ┌──────────────┐                │
│   │ Identification│───▶│   Analysis   │───▶│  Prioritization│               │
│   │              │    │              │    │               │               │
│   │ Find risks   │    │ Assess       │    │ Rank by       │               │
│   │ Document     │    │ Probability  │    │ Impact ×      │               │
│   │              │    │ & Impact     │    │ Probability   │               │
│   └──────────────┘    └──────────────┘    └──────────────┘                │
│          │                   │                   │                         │
│          │                   │                   │                         │
│          ▼                   ▼                   ▼                         │
│   ┌──────────────┐    ┌──────────────┐    ┌──────────────┐                │
│   │   Response   │───▶│   Monitoring │───▶│   Control    │                │
│   │   Planning   │    │              │    │              │                │
│   │              │    │ Track risks  │    │ Implement    │                │
│   │ Mitigation   │    │ Reassess     │    │ responses    │                │
│   │ Strategies   │    │              │    │              │                │
│   └──────────────┘    └──────────────┘    └──────────────┘                │
│                                                                             │
└─────────────────────────────────────────────────────────────────────────────┘
```

---

### 3.4.3 Risk Identification

| Technique | Description |
|-----------|-------------|
| **Brainstorming** | Team generates risks collaboratively |
| **Interviews** | Consult stakeholders and experts |
| **Checklists** | Historical risks from similar projects |
| **SWOT Analysis** | Strengths, Weaknesses, Opportunities, Threats |
| **Assumptions Analysis** | Validate assumptions that may be wrong |
| **Root Cause Analysis** | Identify underlying causes of potential problems |

---

### 3.4.4 Risk Analysis

**Probability:** Likelihood of risk occurring (0-100%)

**Impact:** Consequence if risk occurs (cost, schedule, quality, reputation)

**Risk Score = Probability × Impact**

| Score | Category | Action |
|-------|----------|--------|
| > 0.7 | **Critical** | Immediate action required |
| 0.4 - 0.7 | **High** | Active management; response plan needed |
| 0.2 - 0.4 | **Medium** | Monitor; contingency plan |
| < 0.2 | **Low** | Accept; periodic review |

---

### 3.4.5 Risk Response Strategies

#### For Threats (Negative Risks)

| Strategy | Description | Example |
|----------|-------------|---------|
| **Avoid** | Eliminate the threat | Choose proven technology instead of cutting-edge |
| **Transfer** | Shift impact to third party | Purchase insurance; fixed-price contract |
| **Mitigate** | Reduce probability or impact | Add testing; implement redundancy; train team |
| **Accept** | Acknowledge and monitor | Budget contingency; schedule buffer |
| **Escalate** | Raise to higher authority | Risk beyond project scope |

#### For Opportunities (Positive Risks)

| Strategy | Description | Example |
|----------|-------------|---------|
| **Exploit** | Ensure opportunity happens | Allocate resources to promising feature |
| **Share** | Partner to capture benefit | Collaborate with external expert |
| **Enhance** | Increase probability/impact | Add features to increase market appeal |
| **Accept** | Take advantage if occurs | Be ready to capitalize |

---

### 3.4.6 Risk Register

A **Risk Register** is the central document for tracking risks throughout the project.

| Field | Description |
|-------|-------------|
| **ID** | Unique identifier |
| **Description** | Clear statement of risk |
| **Category** | Technical, organizational, external, etc. |
| **Probability** | Likelihood (0-100%) |
| **Impact** | Consequence (cost, schedule, quality) |
| **Risk Score** | Probability × Impact |
| **Priority** | Critical, High, Medium, Low |
| **Response Strategy** | Avoid, Transfer, Mitigate, Accept |
| **Action Plan** | Specific steps to implement response |
| **Owner** | Person responsible for monitoring |
| **Status** | Open, Mitigated, Closed |

---

## 3.5 Stakeholder & Communication Management

---

### 3.5.1 Stakeholder Identification

**Stakeholders** are individuals or groups who can affect or are affected by the project.

| Stakeholder Type | Examples |
|------------------|----------|
| **Internal** | Project sponsor, development team, management, operations |
| **External** | Customers, end users, regulators, vendors, investors |
| **Primary** | Directly impacted; actively involved |
| **Secondary** | Indirectly impacted; may influence |

---

### 3.5.2 Stakeholder Analysis

| Attribute | Description |
|-----------|-------------|
| **Power** | Ability to influence project |
| **Interest** | Level of concern about project outcomes |
| **Influence** | Capacity to affect decisions |
| **Impact** | Degree to which project affects them |

**Power/Interest Grid:**

```
High Power  │  Keep Satisfied    │  Manage Closely
            │  (Engage regularly)│  (Frequent communication)
            │                    │
            ├────────────────────┼────────────────────
            │                    │
Low Power   │  Monitor           │  Keep Informed
            │  (Minimal effort)  │  (Regular updates)
            │                    │
            └────────────────────┴────────────────────
                Low Interest         High Interest
```

---

### 3.5.3 Communication Plan

A **Communication Plan** defines who needs what information, when, and how.

| Element | Description |
|---------|-------------|
| **Stakeholder** | Who needs information |
| **Information** | What they need (status, decisions, risks) |
| **Frequency** | How often (daily, weekly, milestone) |
| **Format** | How delivered (email, meeting, report, dashboard) |
| **Responsible** | Who provides the information |
| **Purpose** | Why they need it (decision making, awareness, feedback) |

---

### 3.5.4 Communication Channels

| Channel | Best For | Considerations |
|---------|----------|----------------|
| **Face-to-Face** | Complex discussions, conflict resolution, team building | Most effective; not always possible |
| **Video Conference** | Distributed teams, visual demonstrations | Requires scheduling; technology dependent |
| **Email** | Formal communication, documentation, asynchronous | Can be misinterpreted; information overload |
| **Instant Messaging** | Quick questions, informal coordination | Disruptive; information silos |
| **Status Reports** | Formal progress updates | Ensure consistent format; avoid too much detail |
| **Dashboards** | Real-time metrics, transparency | Requires tooling; ensure accuracy |

---

## 3.6 Quality Management

---

### 3.6.1 Quality Concepts

| Concept | Description |
|---------|-------------|
| **Quality** | Degree to which the product meets requirements and satisfies stakeholders |
| **Quality Assurance (QA)** | Process-focused; preventing defects |
| **Quality Control (QC)** | Product-focused; detecting defects |

---

### 3.6.2 Quality Management Processes

| Process | Description |
|---------|-------------|
| **Plan Quality** | Identify quality requirements and standards |
| **Manage Quality** | Audit processes; ensure adherence |
| **Control Quality** | Monitor results; verify compliance |

---

### 3.6.3 Cost of Quality (CoQ)

| Category | Description | Examples |
|----------|-------------|----------|
| **Prevention Costs** | Avoiding defects | Training, planning, standards, reviews |
| **Appraisal Costs** | Finding defects | Testing, inspections, audits |
| **Failure Costs (Internal)** | Defects found before release | Rework, debugging, retesting |
| **Failure Costs (External)** | Defects found after release | Support, recalls, reputation damage |

> **🔑 Key Insight:** Investing in prevention reduces total cost of quality. Defects found later cost exponentially more to fix.

---

### 3.6.4 Quality Metrics

| Metric | Description |
|--------|-------------|
| **Defect Density** | Defects per unit of size (e.g., per KLOC) |
| **Defect Removal Efficiency** | Percentage of defects found before release |
| **Mean Time Between Failures** | Average time between system failures |
| **Customer Satisfaction** | Stakeholder perception of quality |
| **Rework Effort** | Percentage of effort spent fixing defects |

---

## 💡 Study Activity: Deep Dive

---

### Activity 1: Estimation Scenarios

For each scenario, recommend an estimation technique and justify:

**Scenario A:** A small startup with 4 developers building a new mobile app. Requirements are uncertain and will evolve.

<details>
<summary>Click for answer</summary>
<strong>Planning Poker (Story Points).</strong> Team is small and co-located; requirements are uncertain; relative estimation using story points allows for uncertainty and enables velocity tracking. Points avoid false precision of hour estimates for unknown work.
</details>

**Scenario B:** A government agency needs a fixed-price contract for a large system. Detailed requirements are available.

<details>
<summary>Click for answer</summary>
<strong>COCOMO or Function Point Analysis.</strong> Fixed-price contracts require predictable estimates. Function points provide a language-independent size measure that can be converted to effort using historical productivity data. COCOMO accounts for project complexity factors.
</details>

**Scenario C:** A company is building its 10th similar project with historical data available.

<details>
<summary>Click for answer</summary>
<strong>Analogous Estimation.</strong> Historical data from similar projects provides reliable basis for estimation. Fast and inexpensive. Can be refined with parametric models if needed.
</details>

---

### Activity 2: Risk Analysis

For each risk, calculate risk score and recommend a response strategy:

| Risk | Probability | Impact | Risk Score | Strategy |
|------|-------------|--------|------------|----------|
| Key developer leaves mid-project | 30% | High (schedule delay) | | |
| New technology fails to meet requirements | 20% | Critical (project failure) | | |
| Requirements change significantly | 80% | Medium (scope creep) | | |
| Vendor goes out of business | 3% | Critical (dependency loss) | | |

<details>
<summary>Click for answer</summary>

| Risk | Probability | Impact | Risk Score | Strategy |
|------|-------------|--------|------------|----------|
| Key developer leaves | 30% | High (0.7) | 0.21 | **Mitigate**: Cross-train team; document knowledge; use pair programming |
| New technology fails | 20% | Critical (1.0) | 0.20 | **Avoid**: Create proof-of-concept early; have fallback technology |
| Requirements change | 80% | Medium (0.4) | 0.32 | **Accept** with contingency: Agile approach; budget buffer for scope |
| Vendor goes out of business | 3% | Critical (1.0) | 0.03 | **Transfer** or **Mitigate**: Multi-sourcing; escrow agreement |

</details>

---

### Activity 3: Communication Plan Design

Design a communication plan for a project with:
- 8 developers (co-located)
- Product owner in different city
- External stakeholders (executives, customers)
- 3-month duration

<details>
<summary>Click for answer</summary>

| Stakeholder | Information | Frequency | Format | Responsible |
|-------------|-------------|-----------|--------|-------------|
| Development Team | Daily progress, blockers | Daily | Daily Scrum (13 min) | Scrum Master |
| Product Owner | Sprint progress, backlog | Weekly | Sprint Review | Team |
| Product Owner | Impediments, decisions | As needed | Video call, Slack | Scrum Master |
| Executives | High-level progress, risks | Bi-weekly | Dashboard, email summary | Project Manager |
| Customers | Feature demonstrations | Per sprint | Sprint Review (recorded) | Product Owner |
| All Stakeholders | Milestone completion | Per milestone | Status report | Project Manager |

</details>

---

## 📝 Module 3 Self-Assessment Quiz

1. What are the three constraints in the project management "iron triangle"?

   <details>
   <summary>Click for answer</summary>
   Scope, Time, Cost. (Some models add Quality or Value as a fourth dimension.)
   </details>

2. What is the 100% rule in Work Breakdown Structure?

   <details>
   <summary>Click for answer</summary>
   The WBS must include 100% of the work defined by the project scope. No work should be outside the WBS.
   </details>

3. What is the difference between COCOMO and Function Point Analysis?

   <details>
   <summary>Click for answer</summary>
   COCOMO estimates effort based on lines of code (KLOC) with cost drivers; Function Point Analysis estimates based on functionality delivered to the user, independent of implementation language.
   </details>

4. What is story points in Agile estimation?

   <details>
   <summary>Click for answer</summary>
   Story points are a relative measure of effort, complexity, and uncertainty. They are team-specific and more stable than hour estimates for Agile teams.
   </details>

5. What is the Critical Path?

   <details>
   <summary>Click for answer</summary>
   The longest path through the project network. Tasks on the critical path have zero slack; any delay delays the project completion.
   </details>

6. What is velocity in Scrum?

   <details>
   <summary>Click for answer</summary>
   The sum of story points completed per sprint. Used for forecasting and capacity planning.
   </details>

7. What is the difference between a burndown chart and a burnup chart?

   <details>
   <summary>Click for answer</summary>
   Burndown shows remaining work over time; burnup shows completed work over time.
   </details>

8. What are the four risk response strategies for threats?

   <details>
   <summary>Click for answer</summary>
   Avoid, Transfer, Mitigate, Accept.
   </details>

9. What is the difference between Quality Assurance and Quality Control?

   <details>
   <summary>Click for answer</summary>
   Quality Assurance is process-focused (preventing defects); Quality Control is product-focused (detecting defects).
   </details>

10. What is the Power/Interest Grid used for?

    <details>
    <summary>Click for answer</summary>
    To classify stakeholders based on their power to influence the project and their interest in project outcomes, guiding communication strategies.
    </details>

---

## 🔗 Connections to Other Modules

| Concept from Module 3 | Connects to |
|-----------------------|-------------|
| Estimation (COCOMO) | Module 5: Implementation (size metrics) |
| Risk management | Module 4: Design (technical risk) |
| Agile metrics | Module 2: Requirements (backlog management) |
| Quality management | Module 6: Testing (QA/QC processes) |
| Communication plan | Module 1: Team structures, stakeholder communication |

---

## ✅ Module 3 Summary

| Section | Key Takeaways |
|---------|---------------|
| **3.1 Introduction** | Project management balances scope, time, cost; PM roles differ in traditional vs. Agile |
| **3.2 Project Planning** | WBS decomposes work; estimation methods: expert, analogous, parametric (COCOMO, function points), planning poker; scheduling: Gantt, Critical Path, PERT |
| **3.3 Agile Management** | Scrum (roles, artifacts, events); metrics: velocity, burndown; Kanban (WIP limits, flow) |
| **3.4 Risk Management** | Identify, analyze (probability × impact), prioritize, respond (avoid, transfer, mitigate, accept) |
| **3.5 Communication** | Stakeholder analysis (Power/Interest Grid); communication plan; channels |
| **3.6 Quality** | Quality Assurance (process) vs. Quality Control (product); Cost of Quality |

---


