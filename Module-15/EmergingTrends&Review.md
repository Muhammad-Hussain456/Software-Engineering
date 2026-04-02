# Module 8: Emerging Trends & Review

---

## 📌 Module Learning Objectives

By the end of this module, you should be able to:
- Understand **emerging trends** shaping the future of software engineering
- Describe **artificial intelligence** applications in software development
- Explain **cloud-native** principles and practices
- Understand **security** considerations (DevSecOps, Zero Trust)
- Review and integrate knowledge from all previous modules
- Prepare effectively for the NSCT

---

## 8.1 Artificial Intelligence in Software Engineering

---

### 8.1.1 Overview

**Artificial Intelligence (AI)** is increasingly transforming software engineering practices, from development assistance to intelligent systems.

> **🔑 Key Insight:** AI is not replacing software engineers—it is augmenting them. The future belongs to engineers who can effectively leverage AI tools.

---

### 8.1.2 AI Applications Across the SDLC

| Phase | AI Application | Description |
|-------|----------------|-------------|
| **Requirements** | Natural Language Processing | Extracting requirements from documents; detecting ambiguities; generating user stories |
| **Design** | Architecture Recommendations | Suggesting design patterns; identifying potential issues |
| **Development** | Code Generation | Autocompletion; code generation from comments (Copilot, CodeWhisperer) |
| **Testing** | Test Generation | Automatically generating unit tests; identifying untested paths |
| **Debugging** | Defect Prediction | Identifying high-risk areas; suggesting fixes |
| **Maintenance** | Technical Debt Detection | Identifying code smells; refactoring suggestions |
| **Operations** | Anomaly Detection | Detecting system anomalies; predicting failures |

---

### 8.1.3 AI-Powered Development Tools

| Tool Category | Examples | Capabilities |
|---------------|----------|--------------|
| **Code Assistants** | GitHub Copilot, Amazon CodeWhisperer, TabNine | Real-time code suggestions; function generation; documentation |
| **Code Review** | DeepCode, CodeGuru | Automated code review; security vulnerability detection |
| **Testing** | Diffblue Cover, Test.ai | Automated test generation; test maintenance |
| **DevOps** | Harness AI, Datadog Watchdog | Deployment recommendations; anomaly detection |
| **Project Management** | Jira AI, Linear AI | Task estimation; risk prediction; prioritization |

---

### 8.1.4 AI Ethics & Challenges

| Challenge | Description |
|-----------|-------------|
| **Bias** | AI models may perpetuate or amplify biases in training data |
| **Explainability** | AI decisions must be explainable, especially in critical systems |
| **Security** | AI models can be attacked (adversarial inputs, data poisoning) |
| **Intellectual Property** | Training data copyright; ownership of AI-generated code |
| **Responsibility** | Who is accountable for AI-generated code defects? |
| **Accuracy** | AI suggestions may be incorrect; human oversight required |

---

### 8.1.5 Large Language Models (LLMs) in Software Engineering

| Application | Description |
|-------------|-------------|
| **Code Generation** | Generating code from natural language descriptions |
| **Code Explanation** | Explaining complex code for understanding |
| **Documentation** | Generating comments, READMEs, API docs |
| **Refactoring** | Suggesting improvements; converting code patterns |
| **Language Translation** | Converting code between languages |
| **Test Generation** | Creating test cases from code or specifications |

> **🔑 Key Insight:** LLMs are powerful assistants but require careful validation. Always review, test, and understand AI-generated code before integration.

---

## 8.2 Cloud-Native Development

---

### 8.2.1 What Is Cloud-Native?

**Cloud-native** is an approach to building and running applications that fully exploit the cloud computing model.

> **🔑 Key Insight:** Cloud-native is not simply moving existing applications to the cloud (lift-and-shift). It involves designing applications specifically for cloud environments.

---

### 8.2.2 Cloud-Native Principles

| Principle | Description |
|-----------|-------------|
| **Microservices** | Small, independently deployable services |
| **Containers** | Consistent packaging across environments |
| **Orchestration** | Automated management (Kubernetes) |
| **DevOps** | Collaboration and automation |
| **API-First** | Expose functionality through APIs |
| **Stateless** | Services designed to scale horizontally |
| **Observability** | Comprehensive monitoring and logging |
| **Automation** | Infrastructure as Code, CI/CD |

---

### 8.2.3 Cloud Service Models

| Model | Description | Responsibility |
|-------|-------------|----------------|
| **IaaS** | Infrastructure as a Service | You manage OS, middleware, runtime, data, applications |
| **PaaS** | Platform as a Service | You manage data, applications |
| **SaaS** | Software as a Service | Provider manages everything |
| **FaaS** | Function as a Service (Serverless) | You deploy code; platform handles scaling |

**Responsibility Distribution:**

```
┌─────────────────────────────────────────────────────────────────────────────┐
│                     Cloud Responsibility Model                              │
├─────────────────────────────────────────────────────────────────────────────┤
│                                                                             │
│   On-Premises    │    IaaS        │    PaaS        │    SaaS      │ FaaS   │
│   ─────────────  │   ─────────    │   ─────────    │   ─────────  │───────│
│                                                                             │
│   Applications   │ Applications   │ Applications   │ Applications│Function│
│   Data           │ Data           │ Data           │ Provider    │ Code   │
│   Runtime        │ Runtime        │ Provider       │             │        │
│   Middleware     │ Middleware     │                │             │Platform│
│   OS             │ OS             │ Platform       │ Platform    │ (auto) │
│   Virtualization │ Virtualization │ Virtualization │ Virtualization│      │
│   Servers        │ Servers        │ Servers        │ Servers     │        │
│   Storage        │ Storage        │ Storage        │ Storage     │        │
│   Networking     │ Networking     │ Networking     │ Networking  │        │
│                                                                             │
│   User Managed   │ Provider Managed                                         │
│                                                                             │
└─────────────────────────────────────────────────────────────────────────────┘
```

---

### 8.2.4 Serverless Computing

**Serverless** (FaaS) allows developers to run code without managing servers.

| Aspect | Description |
|--------|-------------|
| **Execution Model** | Code runs in response to events; scales automatically |
| **Billing** | Pay per execution, not for idle capacity |
| **Stateless** | Functions are stateless; state stored externally |
| **Use Cases** | APIs, data processing, event-driven workflows |

**Serverless Advantages:**
- No infrastructure management
- Automatic scaling
- Pay-per-use cost model
- Faster deployment

**Serverless Limitations:**
- Cold start latency
- Execution time limits
- Vendor lock-in
- Debugging complexity

---

### 8.2.5 Cloud-Native Patterns

| Pattern | Description |
|---------|-------------|
| **Circuit Breaker** | Prevent cascading failures by failing fast |
| **Service Discovery** | Services find each other without hardcoded addresses |
| **Sidecar** | Deploy auxiliary components alongside main service |
| **Ambassador** | Proxy communications for services |
| **Leader Election** | Coordinate single active instance in distributed system |
| **Retry with Backoff** | Retry failed operations with exponential delay |

---

## 8.3 Security in Software Engineering (DevSecOps)

---

### 8.3.1 What Is DevSecOps?

**DevSecOps** integrates security practices into the DevOps pipeline, making security a shared responsibility throughout the development lifecycle.

> **🔑 Key Insight:** Security is not an afterthought—it is built into the process from the beginning ("shift left").

---

### 8.3.2 Shift Left Security

**Shift Left** means moving security testing and practices earlier in the development lifecycle.

```
Traditional Security (Shift Right):
┌─────────────┐    ┌─────────────┐    ┌─────────────┐    ┌─────────────┐
│   Plan      │───▶│   Code      │───▶│   Build     │───▶│   Test      │
└─────────────┘    └─────────────┘    └─────────────┘    └─────────────┘
                                                                   │
                                                                   ▼
                                                           ┌─────────────┐
                                                           │   Security  │
                                                           │   (Late)    │
                                                           └─────────────┘

Shift Left Security:
┌─────────────┐    ┌─────────────┐    ┌─────────────┐    ┌─────────────┐
│   Plan      │───▶│   Code      │───▶│   Build     │───▶│   Test      │
│   (Threat   │    │   (SAST,    │    │   (DAST,    │    │   (Penetration,│
│    Modeling)│    │    Secrets) │    │    SCA)     │    │    Fuzzing) │
└─────────────┘    └─────────────┘    └─────────────┘    └─────────────┘
       ▲                 ▲                  ▲                  ▲
       │                 │                  │                  │
       └─────────────────┴──────────────────┴──────────────────┘
                              Security Integrated at Every Stage
```

---

### 8.3.3 Security Practices in the SDLC

| Stage | Security Practice | Description |
|-------|-------------------|-------------|
| **Plan** | Threat Modeling | Identify potential threats; design countermeasures |
| **Code** | SAST | Static Application Security Testing (analyze source code) |
| **Code** | Secrets Detection | Prevent credentials in code |
| **Build** | SCA | Software Composition Analysis (vulnerabilities in dependencies) |
| **Build** | Container Scanning | Vulnerabilities in container images |
| **Test** | DAST | Dynamic Application Security Testing (running application) |
| **Test** | Penetration Testing | Simulated attacks to find vulnerabilities |
| **Deploy** | Infrastructure Scanning | Misconfiguration detection |
| **Operate** | Runtime Monitoring | Detect and respond to attacks |

---

### 8.3.4 Zero Trust Security

**Zero Trust** is a security model that assumes no implicit trust—verify everything.

| Principle | Description |
|-----------|-------------|
| **Never Trust, Always Verify** | Every request authenticated and authorized |
| **Least Privilege** | Minimum access needed to perform function |
| **Assume Breach** | Design assuming attacker may be inside |
| **Micro-segmentation** | Isolate workloads to limit blast radius |
| **Continuous Monitoring** | Ongoing validation of trust |

---

### 8.3.5 Common Security Vulnerabilities (OWASP Top 10)

The NSCT may reference common security vulnerabilities.

| Rank | Vulnerability | Description |
|------|---------------|-------------|
| 1 | Broken Access Control | Users can access unauthorized resources |
| 2 | Cryptographic Failures | Weak encryption; sensitive data exposure |
| 3 | Injection | SQL, NoSQL, OS injection attacks |
| 4 | Insecure Design | Security flaws in design phase |
| 5 | Security Misconfiguration | Default passwords; exposed services |
| 6 | Vulnerable Components | Outdated libraries with known vulnerabilities |
| 7 | Identification Failures | Weak authentication; session management |
| 8 | Software Integrity Failures | Unverified updates; supply chain attacks |
| 9 | Monitoring Failures | Insufficient logging; delayed detection |
| 10 | Server-Side Request Forgery | Abusing server to make unauthorized requests |

---

## 8.4 Additional Emerging Trends

---

### 8.4.1 Platform Engineering

**Platform Engineering** involves building and maintaining internal developer platforms that abstract infrastructure complexity.

| Aspect | Description |
|--------|-------------|
| **Goal** | Improve developer productivity and experience |
| **Internal Developer Platform** | Self-service capabilities for developers |
| **Golden Paths** | Standardized, approved ways to build and deploy |
| **Outcome** | Reduced cognitive load; faster delivery |

---

### 8.4.2 Edge Computing

**Edge Computing** processes data closer to the source (users, devices) rather than in centralized cloud data centers.

| Aspect | Description |
|--------|-------------|
| **Drivers** | Low latency; bandwidth constraints; data sovereignty |
| **Use Cases** | IoT, autonomous vehicles, real-time analytics |
| **Challenges** | Distributed systems complexity; security; device management |

---

### 8.4.3 Low-Code / No-Code Development

**Low-Code/No-Code** platforms enable application development with minimal hand-coding.

| Aspect | Description |
|--------|-------------|
| **Target Users** | Citizen developers; rapid prototyping; business applications |
| **Benefits** | Faster development; reduced skills gap |
| **Limitations** | Customization constraints; vendor lock-in; scalability |
| **Trend** | Integration with professional development (pro-code + low-code) |

---

### 8.4.4 Green Software Engineering

**Green Software Engineering** focuses on building energy-efficient, sustainable software.

| Principle | Description |
|-----------|-------------|
| **Carbon Efficiency** | Minimize carbon emissions per user |
| **Energy Efficiency** | Reduce energy consumption |
| **Hardware Efficiency** | Use resources effectively |
| **Measurement** | Track and optimize energy impact |
| **Carbon Awareness** | Shift workloads to cleaner energy sources |

---

## 8.5 Comprehensive Module Review

---

### 8.5.1 Module 1: Introduction & Processes

| Key Concept | Quick Recall |
|-------------|--------------|
| Software vs. Program | Program = code; Software = program + documentation + configuration + support |
| Software Crisis | 1960s-80s; led to software engineering as discipline |
| Waterfall | Sequential phases; stable requirements |
| Agile | Iterative, incremental; responding to change |
| Scrum | Roles (PO, SM, Team); artifacts (backlog, increment); events (sprint, daily, review, retrospective) |
| XP | Engineering practices: TDD, pair programming, CI |
| Team Structures | Chief Programmer (hierarchical); Democratic (flat); Open Source (layered) |
| ACM/IEEE Code | 8 principles; PUBLIC highest priority |

---

### 8.5.2 Module 2: Requirements Engineering

| Key Concept | Quick Recall |
|-------------|--------------|
| Functional Requirements | What system does |
| Non-Functional Requirements | How well system performs (performance, security, reliability) |
| Elicitation | Interviews, workshops, observation, prototyping, surveys |
| User Story | "As a [role], I want [feature] so that [benefit]" |
| INVEST | Independent, Negotiable, Valuable, Estimable, Small, Testable |
| Use Case | Actor, preconditions, main flow, alternate flows, postconditions |
| SRS | Introduction, Overall Description, Specific Requirements, Appendices |
| Validation | Are we building the right product? |
| Traceability | Linking requirements to design, code, tests |

---

### 8.5.3 Module 3: System Modeling & Design

| Key Concept | Quick Recall |
|-------------|--------------|
| UML | Unified Modeling Language; structural and behavioral diagrams |
| Use Case Diagram | Actors, use cases, include (mandatory), extend (optional) |
| Class Diagram | Classes, attributes, methods; relationships (association, aggregation, composition, inheritance) |
| Sequence Diagram | Object interactions over time; lifelines, messages, combined fragments (alt, loop) |
| Activity Diagram | Workflow; decisions, forks, joins, swimlanes |
| SOLID | Single Responsibility, Open/Closed, Liskov Substitution, Interface Segregation, Dependency Inversion |
| GRASP | Information Expert, Creator, Controller, Low Coupling, High Cohesion |
| Design Patterns | Singleton, Factory, Observer, Strategy |

---

### 8.5.4 Module 4: Software Architecture & Implementation

| Key Concept | Quick Recall |
|--------------|--------------|
| Architecture vs. Design | Architecture = high-level structure; Design = component-level details |
| Layered (N-Tier) | Presentation, Business, Data layers |
| MVC | Model (data), View (UI), Controller (logic) |
| Microservices | Small, independent, deployable services |
| Event-Driven | Asynchronous communication via events |
| Clean Code | Meaningful names; small functions; no duplication; express intent |
| Technical Debt | Cost of rework from quick solutions |
| DevOps | Culture of collaboration between Dev and Ops |
| CI/CD | Continuous Integration (build, test on commit); Continuous Delivery (automated deployment) |

---

### 8.5.5 Module 5: Project Management

| Key Concept | Quick Recall |
|--------------|--------------|
| Triple Constraint | Scope, Time, Cost |
| WBS | Work Breakdown Structure; hierarchical decomposition |
| COCOMO | Parametric estimation based on KLOC |
| Function Points | Size based on functionality delivered |
| Planning Poker | Consensus-based Agile estimation |
| Critical Path | Longest path; tasks with zero slack |
| Velocity | Story points per sprint |
| Burndown Chart | Remaining work over time |
| Risk Management | Identify → Analyze → Prioritize → Respond (Avoid, Transfer, Mitigate, Accept) |
| Quality Assurance | Process-focused (prevent defects) |
| Quality Control | Product-focused (detect defects) |

---

### 8.5.6 Module 6: Testing & Quality Assurance

| Key Concept | Quick Recall |
|--------------|--------------|
| Verification | Building product right |
| Validation | Building right product |
| Testing Pyramid | Unit (many, fast) → Integration (some) → System (few) → Acceptance |
| Black-Box | Testing without internal knowledge; equivalence, boundaries |
| White-Box | Testing with internal knowledge; statement, branch, path coverage |
| TDD | Red-Green-Refactor |
| BDD | Given-When-Then; shared language |
| Regression Testing | Re-run tests after changes |
| Test Doubles | Stub, mock, spy, fake, dummy |
| Code Review | Over-the-shoulder, pair programming, tool-assisted, formal inspection |

---

### 8.5.7 Module 7: Maintenance & DevOps

| Key Concept | Quick Recall |
|--------------|--------------|
| Maintenance Types | Corrective (fix), Adaptive (environment), Perfective (enhance), Preventive (proactive) |
| Technical Debt | Principal and interest; deliberate vs. inadvertent |
| Legacy Systems | Old, critical, hard to maintain |
| Strangler Pattern | Gradual replacement of legacy system |
| Three Ways of DevOps | Flow, Feedback, Continuous Learning |
| Deployment Strategies | Rolling, Blue/Green, Canary, A/B Testing |
| Infrastructure as Code | Version-controlled infrastructure definitions |
| Observability | Logs, Metrics, Traces |
| Four Golden Signals | Latency, Traffic, Errors, Saturation |
| Blameless Post-Mortems | Learning from incidents without blame |

---

### 8.5.8 Module 8: Emerging Trends

| Key Concept | Quick Recall |
|--------------|--------------|
| AI in SE | Code generation, testing, debugging, documentation |
| LLMs | Code assistance, explanation, refactoring |
| Cloud-Native | Microservices, containers, orchestration, DevOps |
| Serverless | Pay-per-execution; no server management |
| DevSecOps | Security integrated into DevOps; shift left |
| Zero Trust | Never trust; always verify |
| OWASP Top 10 | Most critical security vulnerabilities |
| Platform Engineering | Internal developer platforms; golden paths |
| Edge Computing | Processing near data source; low latency |
| Green Software | Energy-efficient, sustainable software |

---

## 8.6 NSCT Preparation Guide

---

### 8.6.1 Test Structure Overview

| Aspect | Details |
|--------|---------|
| **Test Name** | HEC National Skills Competency Test (NSCT) |
| **Target Dates** | April 4–5, 2026 |
| **Format** | Multiple-choice questions (MCQs) |
| **Focus** | Core software engineering concepts, not programming syntax |
| **Depth** | Conceptual understanding; application of principles |

---

### 8.6.2 Key Areas to Master

| Priority | Area | Modules |
|----------|------|--------|
| **High** | SDLC & Process Models | Module 1 |
| **High** | Requirements Engineering | Module 2 |
| **High** | Testing & QA Concepts | Module 6 |
| **Medium** | Design & UML | Module 3 |
| **Medium** | Architecture Styles | Module 4 |
| **Medium** | Project Management | Module 5 |
| **Medium** | Maintenance & DevOps | Module 7 |
| **Low** | Emerging Trends | Module 8 |

---

### 8.6.3 Common Question Patterns

| Pattern | Example |
|---------|---------|
| **Definition Recognition** | "What is the primary purpose of integration testing?" |
| **Comparison** | "What is the difference between verification and validation?" |
| **Application** | "Which process model is best for a project with stable requirements?" |
| **Scenario Analysis** | "A project is behind schedule. Adding more people will likely:" |
| **Principle Identification** | "Which SOLID principle is violated when a class has multiple reasons to change?" |
| **Diagram Interpretation** | "In this class diagram, what does the relationship between A and B represent?" |

---

### 8.6.4 Study Strategies

| Strategy | Description |
|----------|-------------|
| **Conceptual Understanding** | Focus on understanding, not memorization |
| **Practice Questions** | Test yourself with scenario-based questions |
| **Flashcards** | Key terms and definitions |
| **Teach Others** | Explain concepts to reinforce understanding |
| **Connect Concepts** | Understand how modules relate (e.g., requirements → design → testing) |
| **Time Management** | Allocate study time based on priority areas |

---

### 8.6.5 Last-Minute Review Checklist

- [ ] Can I explain the difference between Waterfall and Agile?
- [ ] Do I know the Scrum roles, artifacts, and events?
- [ ] Can I write a user story in correct format?
- [ ] Do I understand functional vs. non-functional requirements?
- [ ] Can I identify relationships in a class diagram?
- [ ] Do I know the SOLID principles?
- [ ] Can I distinguish verification from validation?
- [ ] Do I understand the testing pyramid?
- [ ] Can I name the four types of maintenance?
- [ ] Do I know the Three Ways of DevOps?
- [ ] Can I explain technical debt?
- [ ] Do I remember the ACM/IEEE Code principles?

---

## 💡 Study Activity: Final Review

---

### Activity 1: Concept Mapping

Create connections between concepts across modules:

```
Module 1 (Process) ──▶ Module 2 (Requirements) ──▶ Module 3 (Design)
        │                      │                          │
        │                      │                          │
        ▼                      ▼                          ▼
Module 4 (Architecture) ◀───────────────────────── Module 5 (Management)
        │
        │
        ▼
Module 6 (Testing) ──▶ Module 7 (Maintenance) ──▶ Module 8 (Emerging)
```

**Fill in the connections:**
- How does process selection affect requirements?
- How do requirements influence design?
- How does design affect implementation?
- How does testing relate to quality assurance?
- How does maintenance relate to technical debt?

<details>
<summary>Click for answers</summary>

- **Process selection affects requirements:** Waterfall requires complete upfront requirements; Agile allows evolving requirements via user stories.
- **Requirements influence design:** Functional requirements become use cases and class methods; non-functional requirements guide architectural decisions.
- **Design affects implementation:** Design models (UML) translate directly to code structure; design patterns provide implementation templates.
- **Testing relates to quality assurance:** Testing is quality control (detecting defects); quality assurance is the process framework that includes testing.
- **Maintenance relates to technical debt:** High technical debt increases maintenance cost; good maintenance practices reduce technical debt.

</details>

---

### Activity 2: Scenario Integration

A company is building a critical financial system. Answer these questions integrating multiple modules:

1. What process model would you recommend and why? (Module 1)
2. How would you gather requirements? (Module 2)
3. What architectural style is appropriate? (Module 4)
4. How would you estimate effort? (Module 5)
5. What testing levels are essential? (Module 6)
6. How would you manage technical debt? (Module 7)

<details>
<summary>Click for answers</summary>

1. **Process:** Hybrid approach—Waterfall for regulatory compliance documentation; Agile for development to accommodate evolving requirements.
2. **Requirements:** Interviews with stakeholders; workshops for consensus; use cases for user interactions; non-functional requirements for security, performance.
3. **Architecture:** Layered with microservices for scalability; event-driven for audit trails; security by design.
4. **Estimation:** COCOMO for overall size; planning poker for sprints; historical data from similar projects.
5. **Testing:** Unit (TDD); integration (API contracts); system (performance, security); acceptance (UAT); regression (automated).
6. **Technical Debt:** Track in backlog; dedicate 20% of sprint capacity; static analysis tools; code reviews.

</details>

---

### Activity 3: NSCT Practice Questions

**Question 1:** A software project consistently delivers features that meet technical specifications, but users are dissatisfied. Which of the following is most likely the root cause?

A) Poor verification practices
B) Poor validation practices
C) Insufficient unit testing
D) Lack of architectural documentation

<details>
<summary>Click for answer</summary>
**B) Poor validation practices.** Verification ensures technical correctness; validation ensures user needs are met. Users dissatisfied despite meeting specs indicates validation failure.
</details>

---

**Question 2:** Which of the following best describes the difference between aggregation and composition in UML?

A) Aggregation is a stronger relationship than composition
B) Composition allows parts to exist independently of the whole
C) Aggregation is represented with a filled diamond
D) Composition implies that parts cannot exist without the whole

<details>
<summary>Click for answer</summary>
**D) Composition implies that parts cannot exist without the whole.** Composition is the stronger relationship; parts are destroyed with the whole. Aggregation uses hollow diamond; composition uses filled diamond.
</details>

---

**Question 3:** A team estimates user stories using planning poker. The estimates are consistently 20% higher than actual effort. What should they do?

A) Reduce all estimates by 20%
B) Use a different estimation technique
C) Review their definition of story points
D) Estimate in hours instead of points

<details>
<summary>Click for answer</summary>
**C) Review their definition of story points.** Story points measure effort, complexity, and uncertainty—not time. Consistent variance suggests calibration needed. Velocity should track actual completed points, not adjust estimates.
</details>

---

**Question 4:** Which of the following is a primary characteristic of the Strangler Pattern?

A) Complete rewrite of legacy system
B) Gradual replacement of system components
C) Moving system to new infrastructure without changes
D) Wrapping legacy system with APIs

<details>
<summary>Click for answer</summary>
**B) Gradual replacement of system components.** The Strangler Pattern incrementally replaces parts of a legacy system while maintaining overall functionality.
</details>

---

**Question 5:** A developer writes a test that fails, then writes minimal code to make it pass, then refactors. This describes:

A) Behavior-Driven Development
B) Acceptance Test-Driven Development
C) Test-Driven Development
D) Exploratory Testing

<details>
<summary>Click for answer</summary>
**C) Test-Driven Development.** The Red-Green-Refactor cycle is fundamental to TDD.
</details>

---

### Activity 4: Final Self-Assessment

Rate your confidence in each area (1 = Need Review, 5 = Confident):

| Area | Confidence (1-5) |
|------|------------------|
| Software processes (Waterfall, Agile, Scrum, XP) | |
| Requirements engineering (functional, non-functional, user stories) | |
| UML diagrams (class, sequence, use case) | |
| SOLID principles | |
| Architectural styles (layered, MVC, microservices) | |
| Project management (estimation, WBS, critical path) | |
| Risk management | |
| Testing levels and techniques | |
| TDD and BDD | |
| Maintenance types and technical debt | |
| DevOps and CI/CD | |
| ACM/IEEE Code of Ethics | |

<details>
<summary>Click for review guidance</summary>

**Score 1-2:** Revisit the corresponding module. Focus on conceptual understanding.
**Score 3:** Moderate review needed. Practice with scenarios.
**Score 4-5:** Ready. Use for teaching others to reinforce.

</details>

---

## 📝 Module 8 Self-Assessment Quiz

1. What are three applications of AI in software engineering?

   <details>
   <summary>Click for answer</summary>
   Code generation, test generation, defect prediction, code review, documentation generation, requirement analysis.
   </details>

2. What does "shift left" mean in security?

   <details>
   <summary>Click for answer</summary>
   Moving security practices earlier in the development lifecycle—from production and testing into planning, coding, and building phases.
   </details>

3. What are the three pillars of observability?

   <details>
   <summary>Click for answer</summary>
   Logs (discrete events), Metrics (aggregated measurements), Traces (end-to-end request flows).
   </details>

4. What is the difference between IaaS, PaaS, SaaS, and FaaS?

   <details>
   <summary>Click for answer</summary>
   IaaS: infrastructure; PaaS: platform; SaaS: software; FaaS: serverless functions. Increasing levels of abstraction and decreasing user management responsibility.
   </details>

5. What is the Zero Trust security model?

   <details>
   <summary>Click for answer</summary>
   A model that assumes no implicit trust; every request is authenticated and authorized regardless of source.
   </details>

6. What is platform engineering?

   <details>
   <summary>Click for answer</summary>
   Building internal developer platforms that abstract infrastructure complexity, enabling self-service capabilities and faster delivery.
   </details>

7. What are the Four Golden Signals of monitoring?

   <details>
   <summary>Click for answer</summary>
   Latency, Traffic, Errors, Saturation.
   </details>

8. What is green software engineering?

   <details>
   <summary>Click for answer</summary>
   Building energy-efficient, sustainable software focused on carbon efficiency, energy efficiency, and hardware efficiency.
   </details>

9. What are the primary limitations of serverless computing?

   <details>
   <summary>Click for answer</summary>
   Cold start latency, execution time limits, vendor lock-in, debugging complexity.
   </details>

10. What is the OWASP Top 10?

    <details>
    <summary>Click for answer</summary>
    A list of the ten most critical web application security vulnerabilities, maintained by the Open Web Application Security Project.
    </details>

---

## 🔗 Integration Across Modules

| Concept | Modules |
|---------|---------|
| **Requirements** | Module 2 (elicitation), Module 3 (use cases), Module 6 (acceptance tests) |
| **Design** | Module 3 (UML), Module 4 (architecture), Module 1 (process) |
| **Quality** | Module 5 (QA), Module 6 (testing), Module 7 (technical debt) |
| **Management** | Module 1 (process), Module 5 (estimation, risk), Module 7 (DevOps) |
| **Ethics** | Module 1 (ACM/IEEE), Module 4 (security), Module 8 (AI ethics) |

---

## ✅ Module 8 Summary

| Section | Key Takeaways |
|---------|---------------|
| **8.1 AI in SE** | AI augments development; code generation, testing, debugging; ethical challenges |
| **8.2 Cloud-Native** | Microservices, containers, orchestration, serverless; designed for cloud |
| **8.3 DevSecOps** | Security integrated into pipeline; shift left; Zero Trust; OWASP Top 10 |
| **8.4 Emerging Trends** | Platform engineering, edge computing, low-code, green software |
| **8.5 Module Review** | Comprehensive review of all 8 modules with key concepts |
| **8.6 NSCT Preparation** | Test structure, priority areas, question patterns, study strategies |

---

## 🎯 Final Preparation Checklist

| Task | Status |
|------|--------|
| Review all 8 module summaries | ☐ |
| Practice with scenario-based questions | ☐ |
| Create flashcards for key terms | ☐ |
| Understand relationships between modules | ☐ |
| Review ACM/IEEE Code of Ethics | ☐ |
| Practice UML diagram interpretation | ☐ |
| Review testing levels and techniques | ☐ |
| Understand architectural styles | ☐ |
| Review project management concepts | ☐ |
| Get adequate rest before test day | ☐ |

---

## 📚 Complete Course Summary

| Module | Core Focus | Key Takeaways |
|--------|------------|---------------|
| **1** | Processes & Ethics | SDLC models; Agile vs. Waterfall; ACM/IEEE Code |
| **2** | Requirements | Functional vs. non-functional; user stories; use cases |
| **3** | Design | UML; SOLID; GRASP; design patterns |
| **4** | Architecture | Styles (layered, MVC, microservices); clean code; DevOps |
| **5** | Management | Estimation; scheduling; risk; Agile metrics |
| **6** | Testing | Levels; techniques; TDD; BDD; test automation |
| **7** | Maintenance | Types; technical debt; legacy systems; CI/CD |
| **8** | Emerging | AI; cloud-native; DevSecOps; trends; review |

---
