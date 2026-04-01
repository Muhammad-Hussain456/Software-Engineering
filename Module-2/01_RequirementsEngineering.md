# Section-1: Requirements Engineering

---

## 📌 Module Learning Objectives

By the end of this module, you should be able to:
- Understand the **importance** of requirements engineering in the SDLC
- Distinguish between **functional** and **non-functional requirements**
- Describe **requirements elicitation** techniques
- Create **user stories** and **use cases**
- Understand the structure of a **Software Requirements Specification (SRS)**
- Explain **requirements validation** and **management**
- Apply requirements engineering concepts to real-world scenarios

---

## 2.1 Introduction to Requirements Engineering

---

### 2.1.1 What Are Requirements?

A **requirement** is a statement of what a system must do or what property it must have. It describes:
- **What** the system should do
- **How well** it should do it
- **Constraints** under which it must operate

#### Simple Definition

> A requirement is a capability that a system must provide, or a condition that it must satisfy, to meet the needs of stakeholders.

---

### 2.1.2 Why Requirements Matter

Poor requirements are the #1 cause of project failure. The NSCT expects you to understand this fundamental principle.

| Requirement Issue | Consequence |
|-------------------|-------------|
| **Incomplete requirements** | Missing features; rework; scope creep |
| **Ambiguous requirements** | Different interpretations; wrong implementation |
| **Contradictory requirements** | Confusion; wasted effort; system inconsistencies |
| **Unrealistic requirements** | Schedule overruns; cost overruns; failure to deliver |
| **Changing requirements** | Rework; delayed schedule; technical debt |

> **🔑 Key Insight:** The cost of fixing a requirements error increases exponentially as the project progresses.

#### The Cost of Change Curve

```
Cost to Fix
    │
    │                                         ┌─────────────┐
    │                                         │             │
    │                                   ┌─────┘  Production │
    │                                   │                 │
    │                             ┌─────┘  Testing        │
    │                             │                       │
    │                       ┌─────┘  Implementation       │
    │                       │                             │
    │                 ┌─────┘  Design                     │
    │                 │                                   │
    │           ┌─────┘  Requirements                     │
    │           │                                         │
    └───────────┴─────────────────────────────────────────▶
              Req   Design   Code    Test    Production
                         Project Phase

    Error found in Requirements:     1× cost to fix
    Error found in Design:           5× cost to fix
    Error found in Implementation:  10× cost to fix
    Error found in Testing:         20× cost to fix
    Error found in Production:      50-100× cost to fix
```

> **🔑 Key Insight:** Investing time in requirements engineering saves exponentially more time and cost later. The NSCT often tests this principle.

---

### 2.1.3 Types of Requirements

There are three main categories of requirements. Understanding the distinction is essential.

---

#### Functional Requirements

**Definition:** Statements of what the system **must do**. They describe specific behaviors, functions, and features.

| Aspect | Description |
|--------|-------------|
| **What** | Specific actions, computations, data processing |
| **Form** | "The system shall [do something]" |
| **Examples** | "The system shall allow users to log in with email and password" |
| | "The system shall calculate tax based on user location" |
| | "The system shall send a confirmation email after purchase" |

**Characteristics:**
- Verifiable (can be tested)
- Specific and measurable
- Describe system behavior

---

#### Non-Functional Requirements (Quality Attributes)

**Definition:** Statements about **how well** the system performs its functions. They describe quality characteristics and constraints.

| Aspect | Description |
|--------|-------------|
| **What** | Quality attributes, constraints, performance criteria |
| **Form** | "The system shall [perform action] within [metric]" |
| **Examples** | "The system shall respond to user requests within 2 seconds" |
| | "The system shall be available 99.9% of the time" |
| | "The system shall support 10,000 concurrent users" |

**Common Non-Functional Requirement Categories:**

| Category | Description | Example |
|----------|-------------|---------|
| **Performance** | Speed, throughput, response time | "Page load < 2 seconds" |
| **Security** | Authentication, authorization, data protection | "Passwords must be hashed" |
| **Reliability** | Uptime, mean time between failures | "99.9% availability" |
| **Scalability** | Ability to handle growth | "Support 10,000 concurrent users" |
| **Usability** | Ease of use, learnability | "New users can complete task in 3 minutes" |
| **Maintainability** | Ease of modification | "Code coverage > 80%" |
| **Portability** | Ability to run on different platforms | "Runs on Windows, Linux, macOS" |
| **Compliance** | Regulatory standards | "Compliant with GDPR" |
| **Accessibility** | Usability for people with disabilities | "WCAG 2.1 AA compliant" |

---

#### Domain Requirements

**Definition:** Requirements that come from the application domain rather than from user needs. They reflect constraints or standards in the specific industry.

| Aspect | Description |
|--------|-------------|
| **What** | Industry standards, regulations, domain-specific rules |
| **Examples** | "System must comply with HIPAA for healthcare data" |
| | "System must use ISO 8583 for financial transactions" |
| | "System must support Fahrenheit for US users, Celsius for metric" |

---

### 2.1.4 Requirements vs. User Needs

Understanding the difference between what users *want* and what they *need* is critical.

| Concept | Description | Example |
|---------|-------------|---------|
| **User Need** | High-level goal or problem | "I want to track my expenses easily" |
| **Requirement** | Specific, verifiable statement | "User can enter expense amount, category, and date; system stores and displays monthly totals" |

> **🔑 Key Insight:** Requirements are the *translation* of user needs into technical specifications. A good requirements engineer discovers underlying needs, not just stated wants.

---

### 💡 Section 2.1 Self-Assessment

1. What is the #1 cause of project failure in software development?

   <details>
   <summary>Click for answer</summary>
   Poor requirements management—incomplete, ambiguous, or changing requirements.
   </details>

2. What is the difference between functional and non-functional requirements?

   <details>
   <summary>Click for answer</summary>
   Functional requirements describe WHAT the system does; non-functional requirements describe HOW WELL it does it.
   </details>

3. Why does the cost of fixing a requirements error increase over time?

   <details>
   <summary>Click for answer</summary>
   Later phases have more dependencies; changes ripple through design, code, and tests; rework is more extensive.
   </details>

4. Give three examples of non-functional requirements.

   <details>
   <summary>Click for answer</summary>
   Performance (response time), Security (authentication), Reliability (availability).
   </details>

---

## 2.2 Requirements Elicitation

---

### 2.2.1 What Is Elicitation?

**Elicitation** is the process of discovering, understanding, and gathering requirements from stakeholders. It is the first and most critical step in requirements engineering.

> **🔑 Key Insight:** Elicitation is not just asking users what they want—it involves active discovery, probing, and uncovering hidden needs.

---

### 2.2.2 Stakeholders

Stakeholders are anyone with an interest in the system. Different stakeholders have different perspectives.

| Stakeholder Type | Examples | Perspective |
|------------------|----------|-------------|
| **End Users** | Operators, customers, administrators | Day-to-day usability; functionality |
| **Clients** | Project sponsors, customers paying for system | Cost, timeline, business value |
| **Domain Experts** | Industry specialists, subject matter experts | Domain rules, regulations, best practices |
| **Developers** | Architects, engineers, testers | Feasibility, technical constraints |
| **Operations** | IT support, system administrators | Deployment, maintenance, monitoring |
| **Regulators** | Government, industry bodies | Compliance, safety, standards |

> **🔑 Key Insight:** Different stakeholders have different, often conflicting, needs. Requirements engineering involves negotiating and balancing these.

---

### 2.2.3 Elicitation Techniques

The NSCT expects you to know the main elicitation techniques and when to use each.

---

#### Technique 1: Interviews

**Description:** One-on-one or small group conversations with stakeholders to gather requirements.

| Aspect | Details |
|--------|---------|
| **Types** | Structured (fixed questions), Unstructured (open-ended), Semi-structured (guided but flexible) |
| **When to Use** | Complex domains; key stakeholders; when deep understanding needed |
| **Strengths** | Rich detail; can probe and clarify; builds relationships |
| **Weaknesses** | Time-consuming; may miss stakeholders not interviewed |

**Interview Question Types:**
- Open-ended: "Tell me about your current workflow"
- Closed-ended: "Do you need this feature?"
- Probing: "Why is that important to you?"
- Contextual: "Walk me through a typical day"

---

#### Technique 2: Surveys & Questionnaires

**Description:** Written questions distributed to many stakeholders to gather requirements at scale.

| Aspect | Details |
|--------|---------|
| **When to Use** | Large stakeholder groups; geographically distributed; initial requirements gathering |
| **Strengths** | Scalable; quantifiable data; anonymous feedback possible |
| **Weaknesses** | No follow-up; superficial insights; low response rates |

---

#### Technique 3: Workshops

**Description:** Facilitated group sessions with multiple stakeholders to collaboratively define requirements.

| Aspect | Details |
|--------|---------|
| **Types** | Joint Application Development (JAD), requirements workshops, design thinking sessions |
| **When to Use** | Complex projects with many stakeholders; when alignment needed |
| **Strengths** | Fast consensus; stakeholder alignment; collaborative discovery |
| **Weaknesses** | Logistically complex; dominant personalities may skew |

---

#### Technique 4: Observation (Ethnography)

**Description:** Watching users in their actual work environment to understand real processes and pain points.

| Aspect | Details |
|--------|---------|
| **When to Use** | Complex workflows; users who can't articulate needs; process improvement |
| **Strengths** | Uncovers unspoken needs; reveals actual (vs. stated) behavior |
| **Weaknesses** | Time-consuming; Hawthorne effect (people behave differently when watched) |

---

#### Technique 5: Prototyping

**Description:** Creating mockups, wireframes, or working models to help stakeholders discover requirements.

| Aspect | Details |
|--------|---------|
| **Types** | Low-fidelity (paper, wireframes), High-fidelity (interactive, functional) |
| **When to Use** | When stakeholders can't articulate needs; when visualizing helps |
| **Strengths** | Tangible feedback; early validation; reduces ambiguity |
| **Weaknesses** | May be mistaken for final product; scope creep |

---

#### Technique 6: Document Analysis

**Description:** Reviewing existing documentation (process manuals, system docs, regulations) to extract requirements.

| Aspect | Details |
|--------|---------|
| **When to Use** | Legacy system replacement; regulatory compliance; existing processes |
| **Strengths** | Leverages existing knowledge; uncovers historical decisions |
| **Weaknesses** | Documentation may be outdated; missing tacit knowledge |

---

#### Technique 7: Brainstorming

**Description:** Unstructured group idea generation to explore possibilities.

| Aspect | Details |
|--------|---------|
| **When to Use** | Early exploration; innovation; when broad ideas needed |
| **Strengths** | Creative; encourages participation; generates many ideas |
| **Weaknesses** | Can be unfocused; may produce unfeasible ideas |

---

### 2.2.4 Elicitation Best Practices

| Practice | Description |
|----------|-------------|
| **Listen actively** | Understand underlying needs, not just stated wants |
| **Ask "why"** | Probe to understand the root need |
| **Manage expectations** | Be honest about what is feasible |
| **Document everything** | Capture decisions, assumptions, and rationale |
| **Validate understanding** | Confirm with stakeholders that you understood correctly |
| **Involve the right people** | Include all stakeholder groups |

---

### 💡 Section 2.2 Self-Assessment

1. What is the purpose of requirements elicitation?

   <details>
   <summary>Click for answer</summary>
   To discover, understand, and gather requirements from stakeholders—uncovering both stated and unstated needs.
   </details>

2. Name three elicitation techniques.

   <details>
   <summary>Click for answer</summary>
   Interviews, surveys, workshops, observation, prototyping, document analysis, brainstorming.
   </details>

3. When would you use ethnography (observation) as an elicitation technique?

   <details>
   <summary>Click for answer</summary>
   When users can't articulate needs; when actual behavior differs from reported behavior; for complex workflows.
   </details>

---

## 2.3 Requirements Documentation

---

### 2.3.1 Software Requirements Specification (SRS)

The **SRS** is the formal document that captures all requirements for the system. It serves as the contract between stakeholders and developers.

#### Standard SRS Structure (IEEE 830)

| Section | Content |
|---------|---------|
| **1. Introduction** | Purpose, scope, definitions, references |
| **2. Overall Description** | Product perspective, user characteristics, assumptions, dependencies |
| **3. Specific Requirements** | Functional requirements, non-functional requirements, external interfaces |
| **4. Appendices** | Additional information, diagrams, glossaries |

#### SRS Quality Characteristics

| Characteristic | Description |
|----------------|-------------|
| **Correct** | Accurately describes the intended system |
| **Complete** | Includes all requirements, responses, and conditions |
| **Consistent** | No conflicts between requirements |
| **Unambiguous** | Only one interpretation possible |
| **Verifiable** | Can be tested to confirm satisfaction |
| **Traceable** | Each requirement can be traced to source and downstream artifacts |
| **Feasible** | Can be implemented within constraints |

---

### 2.3.2 User Stories (Agile)

In Agile development, user stories replace detailed SRS documents for many projects.

#### Format

> **"As a [role], I want [feature] so that [benefit]"**

| Component | Description | Example |
|-----------|-------------|---------|
| **Role** | Who needs the feature | "As a customer" |
| **Feature** | What they want | "I want to reset my password" |
| **Benefit** | Why they want it | "so that I can regain access to my account" |

#### INVEST Criteria for Good User Stories

| Letter | Meaning | Description |
|--------|---------|-------------|
| **I** | Independent | Can be developed in any order |
| **N** | Negotiable | Details are discussed, not fixed |
| **V** | Valuable | Provides value to the user |
| **E** | Estimable | Size can be estimated |
| **S** | Small | Fits within one sprint |
| **T** | Testable | Acceptance criteria can be defined |

#### Acceptance Criteria

Acceptance criteria define when a user story is "done." They are the conditions that must be met for the story to be accepted.

| Format | Example |
|--------|---------|
| **Scenario-based** | "Given [context], when [action], then [expected outcome]" |
| **Checklist** | ☐ Password reset email sent; ☐ Link expires in 24 hours; ☐ New password meets complexity rules |

**Example:**
> **User Story:** As a customer, I want to reset my password so that I can regain access to my account.
>
> **Acceptance Criteria:**
> - Given I am on the login page, when I click "Forgot Password," then I am prompted to enter my email
> - Given I enter a registered email, when I submit, then a reset link is sent to that email
> - Given I click the reset link, when I enter a new password, then my password is updated
> - Given I use the new password, when I log in, then I can access my account

---

### 2.3.3 Use Cases

Use cases describe interactions between actors and the system to achieve a goal.

#### Use Case Components

| Component | Description |
|-----------|-------------|
| **Actor** | User or external system interacting with the system |
| **Preconditions** | What must be true before the use case starts |
| **Main Flow** | Primary path of success |
| **Alternate Flows** | Variations, exceptions, errors |
| **Postconditions** | What is true after the use case completes |

#### Use Case Template

```
Use Case: [Name]
Actor: [Primary actor]
Precondition: [State before use case]
Main Flow:
  1. Actor performs action
  2. System responds
  3. ...
Alternate Flows:
  A1. [Description of exception]
  A2. [Description of variation]
Postcondition: [State after use case]
```

**Example:**

```
Use Case: Place Order
Actor: Customer
Precondition: Customer is logged in and has items in cart

Main Flow:
  1. Customer clicks "Checkout"
  2. System displays shipping address form
  3. Customer enters shipping address
  4. System displays payment options
  5. Customer selects payment method
  6. System processes payment
  7. System displays order confirmation
  8. System sends confirmation email

Alternate Flows:
  A1. Invalid payment: System displays error message, returns to step 4
  A2. Out of stock: System displays "Item unavailable" message, returns to cart

Postcondition: Order is created and confirmed; inventory is updated
```

---

### 2.3.4 Comparison: SRS vs. User Stories

| Dimension | SRS (Traditional) | User Stories (Agile) |
|-----------|-------------------|----------------------|
| **Format** | Formal document | Index cards / digital items |
| **Detail** | Comprehensive, detailed | Brief, elaborated in conversation |
| **Timing** | Upfront, before development | Just-in-time, before sprint |
| **Ownership** | Written by analyst | Written by product owner, refined with team |
| **Change** | Formal change control | Negotiable, can be refined |
| **Best For** | Safety-critical, regulated, fixed-price | Exploratory, uncertain, evolving |

> **🔑 Key Insight:** Both approaches have merit. The choice depends on project context. The NSCT expects you to understand when to use each.

---

### 💡 Section 2.3 Self-Assessment

1. What is the standard structure of an SRS (IEEE 830)?

   <details>
   <summary>Click for answer</summary>
   Introduction, Overall Description, Specific Requirements, Appendices.
   </details>

2. What does the INVEST acronym stand for?

   <details>
   <summary>Click for answer</summary>
   Independent, Negotiable, Valuable, Estimable, Small, Testable.
   </details>

3. What is the format of a user story?

   <details>
   <summary>Click for answer</summary>
   "As a [role], I want [feature] so that [benefit]."
   </details>

4. What are the main components of a use case?

   <details>
   <summary>Click for answer</summary>
   Actor, Preconditions, Main Flow, Alternate Flows, Postconditions.
   </details>

---

## 2.4 Requirements Validation & Management

---

### 2.4.1 Requirements Validation

Validation ensures that the requirements accurately represent stakeholder needs and are feasible.

#### Validation Techniques

| Technique | Description |
|-----------|-------------|
| **Reviews (Inspections)** | Formal review of requirements with stakeholders and team |
| **Prototyping** | Building mockups to validate understanding |
| **Model Validation** | Executing models to check consistency |
| **Acceptance Tests** | Defining tests that will verify requirements |
| **Walkthroughs** | Presenting requirements to stakeholders for feedback |

#### Validation Checklist

| Check | Question |
|-------|----------|
| **Correct?** | Do requirements accurately reflect stakeholder needs? |
| **Complete?** | Are all requirements included? Any missing? |
| **Consistent?** | Do any requirements conflict? |
| **Unambiguous?** | Is each requirement clear and singular in meaning? |
| **Verifiable?** | Can we test if the requirement is satisfied? |
| **Feasible?** | Can we build it within constraints? |
| **Traceable?** | Can we trace requirements to source and downstream? |

---

### 2.4.2 Requirements Management

Requirements change over time. Management is the process of handling changes systematically.

#### The Reality of Change

| Fact | Implication |
|------|-------------|
| Requirements **will** change | Expect and plan for change |
| Late changes are expensive | Manage changes carefully |
| Unmanaged change = chaos | Formal change control is essential |

#### Change Control Process

```
Step 1: Request
        └── Stakeholder submits change request
                │
                ▼
Step 2: Analysis
        └── Assess impact (cost, schedule, technical)
        └── Evaluate priority and urgency
                │
                ▼
Step 3: Decision
        └── Change Control Board (CCB) approves or rejects
        └── If approved, prioritize and schedule
                │
                ▼
Step 4: Implementation
        └── Update requirements documents
        └── Communicate changes to team
                │
                ▼
Step 5: Tracking
        └── Track change status
        └── Update traceability matrix
```

#### Requirements Traceability

Traceability links requirements through the development lifecycle.

```
Source (Stakeholder)
        │
        ▼
Requirement ID: REQ-101
        │
        ├──────────► Design Component: DSG-201
        │               │
        │               ▼
        │           Code Module: SRC-301
        │               │
        │               ▼
        │           Test Case: TST-401
        │
        └──────────► Test Case: TST-402
```

**Traceability Matrix:**

| Requirement ID | Source | Design Component | Code Module | Test Case | Status |
|----------------|--------|------------------|-------------|-----------|--------|
| REQ-101 | Customer | DSG-201 | SRC-301 | TST-401, TST-402 | Implemented |
| REQ-102 | Regulation | DSG-202 | SRC-302 | TST-403 | Implemented |
| REQ-103 | Product Owner | DSG-203 | - | - | In Progress |

> **🔑 Key Insight:** Traceability ensures that:
> - All requirements are implemented (no gaps)
> - All implemented code serves a requirement (no gold-plating)
> - Impact analysis for changes is accurate

---

### 💡 Section 2.4 Self-Assessment

1. What is the difference between requirements validation and verification?

   <details>
   <summary>Click for answer</summary>
   Validation asks "Are we building the right product?" (correct requirements). Verification asks "Are we building the product right?" (correct implementation).
   </details>

2. What is the purpose of a requirements traceability matrix?

   <details>
   <summary>Click for answer</summary>
   To link requirements to their source, design, implementation, and tests—ensuring coverage and enabling impact analysis.
   </details>

3. What are the steps in a change control process?

   <details>
   <summary>Click for answer</summary>
   Request → Analysis → Decision → Implementation → Tracking.
   </details>

---

## 2.5 Requirements Engineering Summary

---

### 2.5.1 Process Overview

```
┌─────────────────────────────────────────────────────────────────────────────┐
│                     Requirements Engineering Process                         │
├─────────────────────────────────────────────────────────────────────────────┤
│                                                                             │
│   ┌──────────────┐    ┌──────────────┐    ┌──────────────┐                │
│   │  Elicitation │───▶│  Analysis    │───▶│  Specification│                │
│   │              │    │              │    │              │                │
│   │ - Interviews │    │ - Prioritize │    │ - SRS        │                │
│   │ - Workshops  │    │ - Model      │    │ - User Stories│                │
│   │ - Prototypes │    │ - Negotiate  │    │ - Use Cases  │                │
│   └──────────────┘    └──────────────┘    └──────────────┘                │
│          │                   │                   │                         │
│          │                   │                   │                         │
│          ▼                   ▼                   ▼                         │
│   ┌──────────────┐    ┌──────────────┐    ┌──────────────┐                │
│   │ Validation   │◄───│   Review     │───▶│   Management │                │
│   │              │    │              │    │              │                │
│   │ - Reviews    │    │ - Consistency│    │ - Change Ctrl│                │
│   │ - Prototypes │    │ - Completeness│   │ - Traceability│               │
│   └──────────────┘    └──────────────┘    └──────────────┘                │
│                                                                             │
└─────────────────────────────────────────────────────────────────────────────┘
```

---

### 2.5.2 Key Terminology

| Term | Definition |
|------|------------|
| **Functional Requirement** | Statement of what the system must do |
| **Non-Functional Requirement** | Quality attribute or constraint on how system performs |
| **Stakeholder** | Person or organization with interest in the system |
| **Elicitation** | Process of discovering requirements |
| **SRS** | Software Requirements Specification—formal requirements document |
| **User Story** | Agile format: "As a [role], I want [feature] so that [benefit]" |
| **Use Case** | Description of actor-system interaction to achieve a goal |
| **Acceptance Criteria** | Conditions for a user story to be considered complete |
| **Traceability** | Ability to link requirements through development lifecycle |
| **Change Control** | Process for managing requirements changes |

---

### 2.5.3 Comparison Chart: Traditional vs. Agile Requirements

| Dimension | Traditional (Plan-Driven) | Agile |
|-----------|--------------------------|-------|
| **Documentation** | Detailed SRS | User stories, lightweight |
| **Timing** | Upfront, complete before development | Just-in-time, refined per sprint |
| **Change** | Formal change control | Welcomed, backlog refinement |
| **Stakeholder Involvement** | At milestones | Continuous, daily |
| **Best For** | Stable requirements, safety-critical | Uncertain, evolving requirements |

---

## 📝 Module 2 Self-Assessment Quiz

1. What are the three main categories of requirements?

   <details>
   <summary>Click for answer</summary>
   Functional, Non-Functional, Domain.
   </details>

2. Give three examples of non-functional requirements.

   <details>
   <summary>Click for answer</summary>
   Performance, Security, Reliability, Scalability, Usability, Maintainability.
   </details>

3. What is the cost multiplier for fixing a requirements error found in production compared to requirements phase?

   <details>
   <summary>Click for answer</summary>
   50-100× the cost of fixing it during requirements.
   </details>

4. Name four requirements elicitation techniques.

   <details>
   <summary>Click for answer</summary>
   Interviews, surveys, workshops, observation, prototyping, document analysis, brainstorming.
   </details>

5. What is the structure of a user story?

   <details>
   <summary>Click for answer</summary>
   "As a [role], I want [feature] so that [benefit]."
   </details>

6. What does INVEST stand for?

   <details>
   <summary>Click for answer</summary>
   Independent, Negotiable, Valuable, Estimable, Small, Testable.
   </details>

7. What are the main components of a use case?

   <details>
   <summary>Click for answer</summary>
   Actor, Preconditions, Main Flow, Alternate Flows, Postconditions.
   </details>

8. What is the purpose of requirements traceability?

   <details>
   <summary>Click for answer</summary>
   To link requirements to source, design, code, and tests—ensuring coverage and enabling impact analysis.
   </details>

9. What are the steps in change control?

   <details>
   <summary>Click for answer</summary>
   Request → Analysis → Decision → Implementation → Tracking.
   </details>

10. When would you choose user stories over an SRS?

    <details>
    <summary>Click for answer</summary>
    When requirements are uncertain, changing, and project uses Agile methodology; when lightweight documentation is sufficient.
    </details>

---

## 🔗 Connections to Other Modules

| Concept from Module 2 | Connects to |
|-----------------------|-------------|
| Functional requirements | Module 3: Design (UML, class diagrams) |
| Non-functional requirements | Module 4: Architecture (scalability, security) |
| Use cases | Module 3: Use case diagrams, sequence diagrams |
| User stories | Module 5: Agile project management |
| Requirements validation | Module 6: Testing (acceptance tests) |
| Traceability | Module 6: Test coverage |
| Change management | Module 5: Scope management |

---

## ✅ Module 2 Summary

| Section | Key Takeaways |
|---------|---------------|
| **2.1 Introduction** | Requirements define what system must do; poor requirements are #1 cause of failure; cost of change increases exponentially |
| **2.2 Elicitation** | Multiple techniques: interviews, workshops, observation, prototyping; involve all stakeholders |
| **2.3 Documentation** | SRS for plan-driven; user stories and use cases for Agile; INVEST criteria for stories |
| **2.4 Validation & Management** | Validate through reviews; manage change formally; maintain traceability |
| **2.5 Summary** | Requirements engineering is foundational—errors here are most expensive |

---

Would you like me to continue with **Module 3: System Modeling & Design (UML, SOLID, Design Patterns)** in the same detailed format?
