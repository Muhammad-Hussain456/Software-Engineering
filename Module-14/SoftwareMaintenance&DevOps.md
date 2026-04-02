# Module 7: Software Maintenance & DevOps

---

## 📌 Module Learning Objectives

By the end of this module, you should be able to:
- Understand the **importance of software maintenance** in the software lifecycle
- Distinguish between **types of maintenance** (corrective, adaptive, perfective, preventive)
- Understand **technical debt** and its management
- Explain **legacy systems** and modernization strategies
- Understand **DevOps culture** and practices
- Describe **CI/CD pipelines** and their components
- Explain **infrastructure as code** and **observability**

---

## 7.1 Introduction to Software Maintenance

---

### 7.1.1 What Is Software Maintenance?

**Software maintenance** is the process of modifying a software system after delivery to correct defects, improve performance, adapt to changing environments, or add new functionality.

> **🔑 Key Insight:** Maintenance is not an afterthought—it is the longest and most expensive phase of the software lifecycle. Most software spends 80-90% of its lifetime in maintenance.

#### The Maintenance Reality

| Statistic | Implication |
|-----------|-------------|
| 80-90% of software costs occur after delivery | Maintenance dominates total cost of ownership |
| 60-70% of maintenance effort is enhancement | Most maintenance is adding value, not fixing bugs |
| 30-50% of maintenance effort is understanding code | Understanding existing code is the biggest challenge |

---

### 7.1.2 Software Evolution vs. Maintenance

| Concept | Description |
|---------|-------------|
| **Software Evolution** | The natural process of software changing over time in response to changing requirements and environments |
| **Software Maintenance** | The deliberate activities to manage and control evolution |

**Lehman's Laws of Software Evolution:**

| Law | Description |
|-----|-------------|
| **Continuing Change** | Software must be continually adapted or it becomes less satisfactory |
| **Increasing Complexity** | As software evolves, its complexity increases unless work is done to reduce it |
| **Self-Regulation** | Product evolution processes are self-regulating with predictable trends |
| **Conservation of Organizational Stability** | Work effort is roughly constant over product lifetime |
| **Conservation of Familiarity** | Release content decreases as product evolves |
| **Continuing Growth** | Functionality must increase to maintain user satisfaction |
| **Declining Quality** | Quality declines unless rigorously maintained |

---

### 7.1.3 Types of Maintenance

The NSCT expects you to distinguish between these four types of maintenance.

| Type | Definition | Example |
|------|------------|---------|
| **Corrective** | Fixing defects discovered after release | Fixing a calculation error; patching a security vulnerability |
| **Adaptive** | Modifying software to work in new environments | Updating for new operating system; migrating to new database |
| **Perfective** | Enhancing functionality or performance | Adding new features; improving response time |
| **Preventive** | Proactively preventing future problems | Refactoring code; updating documentation; improving test coverage |

#### Maintenance Effort Distribution

```
┌─────────────────────────────────────────────────────────────────────────────┐
│                    Typical Maintenance Effort Distribution                  │
├─────────────────────────────────────────────────────────────────────────────┤
│                                                                             │
│   ┌─────────────────────────────────────────────────────────────────────┐   │
│   │                                                                     │   │
│   │   Perfective (Enhancements)          ████████████████████████ 60%  │   │
│   │                                                                     │   │
│   │   Adaptive (Environment)             ██████████ 20%                 │   │
│   │                                                                     │   │
│   │   Corrective (Bug Fixes)             ██████ 15%                     │   │
│   │                                                                     │   │
│   │   Preventive (Proactive)             ██ 5%                          │   │
│   │                                                                     │   │
│   └─────────────────────────────────────────────────────────────────────┘   │
│                                                                             │
│   Source: IEEE / Software Engineering Institute                             │
│                                                                             │
└─────────────────────────────────────────────────────────────────────────────┘
```

> **🔑 Key Insight:** The majority of maintenance effort is **perfective**—adding value through new features and improvements, not just fixing bugs.

---

## 7.2 Technical Debt

---

### 7.2.1 What Is Technical Debt?

**Technical debt** is the implied cost of additional rework caused by choosing an easy (often quick) solution now instead of a better approach that would take longer.

> **🔑 Key Insight:** Technical debt is a powerful metaphor that helps teams make conscious trade-offs between speed and quality.

#### The Debt Analogy

| Debt Concept | Software Equivalent |
|--------------|---------------------|
| **Principal** | The cost of building the quick solution |
| **Interest** | The extra effort required to work with the debt (slower development, more bugs) |
| **Payment** | Refactoring to improve quality |
| **Default** | System becomes unmaintainable; must be rewritten |

---

### 7.2.2 Types of Technical Debt

| Type | Description | Example |
|------|-------------|---------|
| **Deliberate (Prudent)** | Conscious decision to accept debt for business reasons | Ship now to meet market deadline; plan to refactor later |
| **Deliberate (Reckless)** | Ignoring quality without understanding consequences | "We'll never need to change this" |
| **Inadvertent (Prudent)** | Learning from mistakes | Inexperienced team learns better design; debt is recognized |
| **Inadvertent (Reckless)** | Not knowing good practices | Inexperienced team writes poor code; no one recognizes it |

---

### 7.2.3 Sources of Technical Debt

| Source | Description |
|--------|-------------|
| **Code Debt** | Poor code structure, duplication, violations of design principles |
| **Design Debt** | Inadequate architecture, missing abstractions, poor modularity |
| **Documentation Debt** | Missing or outdated documentation |
| **Testing Debt** | Inadequate test coverage, missing test automation |
| **Infrastructure Debt** | Manual deployment, inconsistent environments, configuration drift |
| **Security Debt** | Known vulnerabilities not addressed |

---

### 7.2.4 Managing Technical Debt

| Activity | Description |
|----------|-------------|
| **Identification** | Use static analysis tools; code reviews; team retrospectives |
| **Documentation** | Track debt in backlog; document rationale for deliberate debt |
| **Prioritization** | Assess impact (interest rate) vs. cost to fix (principal) |
| **Repayment** | Dedicate 10-20% of sprint capacity to debt reduction |
| **Prevention** | Enforce standards; code reviews; continuous refactoring |

**Technical Debt Quadrant:**

```
                    High Interest
                         │
                         │
         High Principal  │  Low Principal
         Low Interest    │  High Interest
         (Critical)      │  (Urgent)
                         │
    ┌────────────────────┼────────────────────┐
    │                    │                    │
    │                    │                    │
    │                    │                    │
    │                    │                    │
    └────────────────────┼────────────────────┘
                         │
         High Principal  │  Low Principal
         High Interest   │  Low Interest
         (Strategic)     │  (Quick wins)
                         │
                         │
                    Low Interest
```

| Quadrant | Priority | Action |
|----------|----------|--------|
| **Critical (High Principal, Low Interest)** | Highest | Repay immediately before costs increase |
| **Urgent (Low Principal, High Interest)** | High | Quick fixes with high payoff |
| **Strategic (High Principal, High Interest)** | Medium | Plan for systematic repayment |
| **Quick Wins (Low Principal, Low Interest)** | Low | Address when convenient |

---

## 7.3 Legacy Systems

---

### 7.3.1 What Is a Legacy System?

A **legacy system** is an old software system that remains critical to business operations but is difficult to maintain, evolve, or integrate with modern systems.

> **🔑 Key Insight:** Legacy is not defined by age alone—it's defined by the cost and risk of change. A 20-year-old system with good documentation and tests may be easier to maintain than a 2-year-old system with high technical debt.

---

### 7.3.2 Characteristics of Legacy Systems

| Characteristic | Description |
|----------------|-------------|
| **Outdated Technology** | Uses obsolete languages, frameworks, or platforms |
| **Poor Documentation** | Missing or outdated documentation |
| **Knowledge Loss** | Original developers have left |
| **Brittle Code** | Changes have unexpected side effects |
| **Technical Debt** | Accumulated shortcuts make changes expensive |
| **Integration Difficulty** | Hard to integrate with modern systems |
| **Security Risks** | Unpatched vulnerabilities |
| **High Maintenance Cost** | Disproportionate effort for small changes |

---

### 7.3.3 Legacy System Modernization Strategies

| Strategy | Description | Risk | Cost | Time |
|----------|-------------|------|------|------|
| **Retire** | Decommission the system if no longer needed | Low | Negative (cost savings) | Short |
| **Encapsulate** | Wrap the system with APIs; use as-is | Low | Low | Short |
| **Rehost** | Move to new infrastructure without code changes | Low | Medium | Medium |
| **Refactor** | Restructure code to improve maintainability | Medium | Medium | Medium |
| **Re-architect** | Rebuild on modern architecture while preserving functionality | High | High | Long |
| **Rewrite** | Complete replacement from scratch | Very High | Very High | Very Long |

**Strategy Selection Factors:**

| Factor | Consideration |
|--------|---------------|
| **Business Criticality** | How important is the system to operations? |
| **Technical Quality** | How maintainable is the current code? |
| **Documentation** | Is knowledge available? |
| **Integration Needs** | Does it need to work with modern systems? |
| **Security** | Are there unpatched vulnerabilities? |
| **Cost** | What is the budget for modernization? |
| **Timeline** | How quickly is change needed? |

---

### 7.3.4 The Strangler Pattern

The **Strangler Pattern** is a modernization strategy that gradually replaces parts of a legacy system with new services.

```
Phase 1: Initial State
┌─────────────────────────────────────────────────────────────────────────────┐
│                         Legacy Monolith                                     │
│  ┌─────────────────────────────────────────────────────────────────────┐   │
│  │  All functionality in one application                               │   │
│  └─────────────────────────────────────────────────────────────────────┘   │
│                                                                             │
│  Users ──────────────────────────────────────────────────────────────────▶  │
└─────────────────────────────────────────────────────────────────────────────┘

Phase 2: Begin Strangling
┌─────────────────────────────────────────────────────────────────────────────┐
│                         ┌─────────────────────────┐                         │
│                         │    New Service A        │                         │
│                         │   (Authentication)      │                         │
│                         └────────────┬────────────┘                         │
│                                      │                                      │
│  Users ────────┐                      │                                     │
│               │                      │                                     │
│               ▼                      ▼                                     │
│  ┌─────────────────────────────────────────────────────────────────────┐   │
│  │                         Legacy Monolith                             │   │
│  │  ┌─────────────────────────────────────────────────────────────┐   │   │
│  │  │  Feature A (redirected) │ Feature B │ Feature C │ Feature D │   │   │
│  │  └─────────────────────────────────────────────────────────────┘   │   │
│  └─────────────────────────────────────────────────────────────────────┘   │
└─────────────────────────────────────────────────────────────────────────────┘

Phase 3: Gradual Replacement
┌─────────────────────────────────────────────────────────────────────────────┐
│  ┌─────────────────────────┐  ┌─────────────────────────┐                  │
│  │    New Service A        │  │    New Service B        │                  │
│  │   (Authentication)      │  │     (Orders)            │                  │
│  └────────────┬────────────┘  └────────────┬────────────┘                  │
│               │                            │                               │
│  Users ───────┼────────────────────────────┼───────────────────┐           │
│               │                            │                   │           │
│               ▼                            ▼                   ▼           │
│  ┌─────────────────────────────────────────────────────────────────────┐   │
│  │                         Legacy Monolith                             │   │
│  │  ┌─────────────────────────────────────────────────────────────┐   │   │
│  │  │ Feature A │ Feature B │ Feature C (redirected) │ Feature D │   │   │
│  │  └─────────────────────────────────────────────────────────────┘   │   │
│  └─────────────────────────────────────────────────────────────────────┘   │
└─────────────────────────────────────────────────────────────────────────────┘

Phase 4: Complete Replacement
┌─────────────────────────────────────────────────────────────────────────────┐
│                                                                             │
│  ┌─────────────┐  ┌─────────────┐  ┌─────────────┐  ┌─────────────┐        │
│  │ Service A   │  │ Service B   │  │ Service C   │  │ Service D   │        │
│  │(Auth)       │  │(Orders)     │  │(Inventory)  │  │(Users)      │        │
│  └─────────────┘  └─────────────┘  └─────────────┘  └─────────────┘        │
│                                                                             │
│  Users ─────────────────────────────────────────────────────────────────▶   │
│                                                                             │
│                    Legacy Monolith (Decommissioned)                         │
│                                                                             │
└─────────────────────────────────────────────────────────────────────────────┘
```

**Strangler Pattern Benefits:**
- **Risk Reduction:** Change happens incrementally
- **Continuous Value:** New features can be deployed early
- **Learning:** Team gains experience with new technology gradually
- **Business Continuity:** System never becomes unavailable

---

## 7.4 DevOps Culture

---

### 7.4.1 What Is DevOps?

**DevOps** is a culture and set of practices that combines software development (Dev) and IT operations (Ops) to shorten the development lifecycle and deliver high-quality software continuously.

> **🔑 Key Insight:** DevOps is not a tool or a role—it's a culture of collaboration, automation, and shared responsibility.

---

### 7.4.2 The Problem DevOps Solves

**Traditional Siloed Organization:**

```
┌─────────────┐    ┌─────────────┐    ┌─────────────┐
│   Dev       │───▶│    QA       │───▶│   Ops       │
│             │    │             │    │             │
│ "Works on   │    │ "Found      │    │ "Doesn't    │
│  my machine"│    │  bugs"      │    │  work in    │
│             │    │             │    │  production"│
└─────────────┘    └─────────────┘    └─────────────┘
      │                   │                   │
      └───────────────────┼───────────────────┘
                          │
                    Blame Game
                    Handoffs
                    Delays
```

**DevOps Integrated Culture:**

```
┌─────────────────────────────────────────────────────────────────────────────┐
│                                                                             │
│   ┌─────────────────────────────────────────────────────────────────────┐   │
│   │                     Shared Responsibility                          │   │
│   │                                                                     │   │
│   │   Dev ──────────────────────────────────────────────┐              │   │
│   │   QA  ──────────────────────────────────────────────┼──▶ Customer  │   │
│   │   Ops ──────────────────────────────────────────────┘              │   │
│   │                                                                     │   │
│   │   • Automated pipelines                                            │   │
│   │   • Shared metrics                                                 │   │
│   │   • Blameless post-mortems                                         │   │
│   │   • Continuous feedback                                            │   │
│   │                                                                     │   │
│   └─────────────────────────────────────────────────────────────────────┘   │
│                                                                             │
└─────────────────────────────────────────────────────────────────────────────┘
```

---

### 7.4.3 The Three Ways of DevOps

| Way | Description | Practices |
|-----|-------------|-----------|
| **Flow** | Accelerate flow of work from Dev to Ops | CI/CD, deployment automation, trunk-based development |
| **Feedback** | Shorten feedback loops | Monitoring, logging, alerting, customer feedback |
| **Continuous Learning** | Experiment, learn, improve | Blameless post-mortems, chaos engineering, experimentation |

---

### 7.4.4 DevOps Principles

| Principle | Description |
|-----------|-------------|
| **Automation** | Automate repetitive tasks (deployment, testing, infrastructure) |
| **Collaboration** | Break down silos between Dev, QA, and Ops |
| **Measurement** | Use data to drive decisions (metrics, monitoring) |
| **Sharing** | Share responsibility for quality, deployment, and operations |
| **Continuous Improvement** | Experiment, fail fast, learn, improve |
| **Infrastructure as Code** | Manage infrastructure with version control |

---

## 7.5 Continuous Integration & Continuous Delivery (CI/CD)

---

### 7.5.1 Overview

| Concept | Definition |
|---------|------------|
| **Continuous Integration (CI)** | Automatically building and testing code whenever changes are pushed to the repository |
| **Continuous Delivery (CD)** | Automatically packaging and preparing code for deployment, with manual approval for production |
| **Continuous Deployment** | Automatically deploying code to production after passing all tests |

---

### 7.5.2 Continuous Integration (CI)

**Core Practices:**

| Practice | Description |
|----------|-------------|
| **Frequent Commits** | Developers commit code multiple times per day |
| **Automated Build** | Every commit triggers an automated build |
| **Automated Tests** | Unit tests run on every commit |
| **Fast Feedback** | Test results available within minutes |
| **Fix Broken Builds Immediately** | Broken builds are highest priority |

**CI Pipeline Stages:**

```
┌─────────────────────────────────────────────────────────────────────────────┐
│                         CI Pipeline                                         │
├─────────────────────────────────────────────────────────────────────────────┤
│                                                                             │
│   ┌─────────────┐    ┌─────────────┐    ┌─────────────┐    ┌─────────────┐ │
│   │   Commit    │───▶│   Build     │───▶│   Unit      │───▶│   Static    │ │
│   │   Code      │    │             │    │   Tests     │    │   Analysis  │ │
│   └─────────────┘    └─────────────┘    └─────────────┘    └─────────────┘ │
│                                                                             │
│   Fast (5-10 minutes)                                                       │
│   Runs on every commit                                                      │
│   Block merge if failed                                                     │
│                                                                             │
└─────────────────────────────────────────────────────────────────────────────┘
```

---

### 7.5.3 Continuous Delivery (CD)

**CD Pipeline Stages:**

```
┌─────────────────────────────────────────────────────────────────────────────┐
│                         CD Pipeline                                         │
├─────────────────────────────────────────────────────────────────────────────┤
│                                                                             │
│   ┌─────────────┐    ┌─────────────┐    ┌─────────────┐    ┌─────────────┐ │
│   │   Package   │───▶│   Deploy    │───▶│   Integration│───▶│   Deploy    │ │
│   │             │    │   to Dev    │    │   Tests     │    │   to Staging│ │
│   └─────────────┘    └─────────────┘    └─────────────┘    └─────────────┘ │
│                                                                             │
│   ┌─────────────┐    ┌─────────────┐    ┌─────────────┐                    │
│   │   Security  │───▶│   Deploy    │───▶│   Smoke     │                    │
│   │   Scan      │    │   to Prod   │    │   Tests     │                    │
│   └─────────────┘    └─────────────┘    └─────────────┘                    │
│                                                                             │
│   Slower (30-60 minutes)                                                    │
│   Runs on successful CI                                                     │
│   Production deployment may require approval                                │
│                                                                             │
└─────────────────────────────────────────────────────────────────────────────┘
```

---

### 7.5.4 Deployment Strategies

| Strategy | Description | Pros | Cons |
|----------|-------------|------|------|
| **Recreate** | Stop old version, start new | Simple | Downtime |
| **Rolling** | Gradually replace instances | No downtime; gradual | Complex; version mixing |
| **Blue/Green** | Switch between two environments | Instant rollback; zero downtime | Double infrastructure cost |
| **Canary** | Deploy to small subset first | Risk reduction; real traffic validation | Complex routing |
| **A/B Testing** | Route users based on attributes | Experimentation; feature validation | Requires routing logic |

**Blue/Green Deployment:**

```
┌─────────────────────────────────────────────────────────────────────────────┐
│                         Blue/Green Deployment                               │
├─────────────────────────────────────────────────────────────────────────────┤
│                                                                             │
│   Before Deployment:                                                        │
│   ┌─────────────────────────────────────────────────────────────────────┐   │
│   │  Blue Environment (Live)      │  Green Environment (Idle)           │   │
│   │  ┌─────────────────────────┐  │  ┌─────────────────────────────┐   │   │
│   │  │ Version 1.0             │  │  │ Version 2.0 (not active)    │   │   │
│   │  │ Serving all traffic     │  │  │ Deployed, tested            │   │   │
│   │  └─────────────────────────┘  │  └─────────────────────────────┘   │   │
│   └─────────────────────────────────────────────────────────────────────┘   │
│                                                                             │
│   During Deployment:                                                        │
│   ┌─────────────────────────────────────────────────────────────────────┐   │
│   │  Blue Environment (Live)      │  Green Environment (Staged)         │   │
│   │  ┌─────────────────────────┐  │  ┌─────────────────────────────┐   │   │
│   │  │ Version 1.0             │  │  │ Version 2.0                 │   │   │
│   │  │ Serving all traffic     │  │  │ Smoke tests passing         │   │   │
│   │  └─────────────────────────┘  │  └─────────────────────────────┘   │   │
│   └─────────────────────────────────────────────────────────────────────┘   │
│                                                                             │
│   After Deployment (Switch):                                                │
│   ┌─────────────────────────────────────────────────────────────────────┐   │
│   │  Blue Environment (Idle)       │  Green Environment (Live)          │   │
│   │  ┌─────────────────────────┐  │  ┌─────────────────────────────┐   │   │
│   │  │ Version 1.0 (rollback)  │  │  │ Version 2.0                 │   │   │
│   │  │ Ready for rollback      │  │  │ Serving all traffic         │   │   │
│   │  └─────────────────────────┘  │  └─────────────────────────────┘   │   │
│   └─────────────────────────────────────────────────────────────────────┘   │
│                                                                             │
└─────────────────────────────────────────────────────────────────────────────┘
```

**Canary Deployment:**

```
┌─────────────────────────────────────────────────────────────────────────────┐
│                         Canary Deployment                                   │
├─────────────────────────────────────────────────────────────────────────────┤
│                                                                             │
│   Phase 1: Deploy to small subset                                          │
│   ┌─────────────────────────────────────────────────────────────────────┐   │
│   │  Version 1.0 ──────── 95% traffic                                   │   │
│   │  Version 2.0 ──────── 5% traffic  (Canary)                         │   │
│   └─────────────────────────────────────────────────────────────────────┘   │
│                              │                                              │
│                              ▼ Monitor metrics for X minutes               │
│                                                                             │
│   Phase 2: Gradually increase if healthy                                  │
│   ┌─────────────────────────────────────────────────────────────────────┐   │
│   │  Version 1.0 ──────── 50% traffic                                   │   │
│   │  Version 2.0 ──────── 50% traffic                                   │   │
│   └─────────────────────────────────────────────────────────────────────┘   │
│                              │                                              │
│                              ▼ Monitor metrics                              │
│                                                                             │
│   Phase 3: Full rollout if healthy                                        │
│   ┌─────────────────────────────────────────────────────────────────────┐   │
│   │  Version 1.0 ──────── 0% traffic                                    │   │
│   │  Version 2.0 ──────── 100% traffic                                  │   │
│   └─────────────────────────────────────────────────────────────────────┘   │
│                                                                             │
│   If metrics degrade: automatically rollback to Version 1.0                │
│                                                                             │
└─────────────────────────────────────────────────────────────────────────────┘
```

---

## 7.6 Infrastructure as Code (IaC)

---

### 7.6.1 What Is Infrastructure as Code?

**Infrastructure as Code** is the practice of managing and provisioning infrastructure using machine-readable definition files rather than manual processes.

> **🔑 Key Insight:** IaC applies software engineering practices to infrastructure: version control, code review, testing, and continuous delivery.

---

### 7.6.2 IaC Benefits

| Benefit | Description |
|---------|-------------|
| **Consistency** | Same definition produces same environment every time |
| **Version Control** | Infrastructure changes tracked, reviewed, audited |
| **Repeatability** | Create identical environments (dev, test, prod) |
| **Automation** | Infrastructure provisioning is automated, not manual |
| **Documentation** | Infrastructure definitions serve as documentation |
| **Disaster Recovery** | Rebuild environments quickly from code |

---

### 7.6.3 IaC Approaches

| Approach | Description | Tools |
|----------|-------------|-------|
| **Declarative** | Define desired state; system figures out how to achieve it | Terraform, CloudFormation, ARM |
| **Imperative** | Define specific steps to achieve desired state | Ansible, Chef, Puppet |
| **Configuration Management** | Manage software on existing servers | Ansible, Chef, Puppet |
| **Orchestration** | Provision and manage infrastructure resources | Terraform, CloudFormation |

---

### 7.6.4 Infrastructure as Code Components

| Component | Description |
|-----------|-------------|
| **Version Control** | Infrastructure definitions stored in Git |
| **CI/CD for Infrastructure** | Automated validation, testing, and deployment of infrastructure changes |
| **Testing** | Unit tests for infrastructure; integration tests; compliance tests |
| **State Management** | Tracking provisioned resources to enable updates and teardown |

---

## 7.7 Observability & Monitoring

---

### 7.7.1 What Is Observability?

**Observability** is the ability to understand the internal state of a system from its external outputs.

> **🔑 Key Insight:** Observability is not just monitoring—it's the ability to ask new questions about system behavior without deploying new code.

---

### 7.7.2 Three Pillars of Observability

| Pillar | Description | Example |
|--------|-------------|---------|
| **Logs** | Discrete events | Error messages, audit entries, request details |
| **Metrics** | Aggregated numerical measurements | Request rate, error rate, latency, CPU usage |
| **Traces** | End-to-end request flows | Distributed tracing across services |

**The Three Pillars:**

```
┌─────────────────────────────────────────────────────────────────────────────┐
│                         Three Pillars of Observability                      │
├─────────────────────────────────────────────────────────────────────────────┤
│                                                                             │
│   ┌─────────────────────────────────────────────────────────────────────┐   │
│   │                                                                     │   │
│   │   LOGS                    METRICS                   TRACES          │   │
│   │   ┌─────────────────┐    ┌─────────────────┐    ┌─────────────────┐ │   │
│   │   │ Discrete events │    │ Aggregated      │    │ Request         │ │   │
│   │   │ Timestamped     │    │ measurements    │    │ propagation     │ │   │
│   │   │ Structured      │    │ Time-series     │    │ End-to-end      │ │   │
│   │   │ Searchable      │    │ Alertable       │    │ Latency breakdown│ │   │
│   │   └─────────────────┘    └─────────────────┘    └─────────────────┘ │   │
│   │                                                                     │   │
│   │   "What happened?"        "How much?"             "Where was the    │   │
│   │                           "How often?"            bottleneck?"      │   │
│   │                                                                     │   │
│   └─────────────────────────────────────────────────────────────────────┘   │
│                                                                             │
└─────────────────────────────────────────────────────────────────────────────┘
```

---

### 7.7.3 Key Metrics (The Four Golden Signals)

| Signal | Description | Example |
|--------|-------------|---------|
| **Latency** | Time to process a request | 95th percentile response time < 500ms |
| **Traffic** | Volume of requests | 10,000 requests per second |
| **Errors** | Rate of failed requests | Error rate < 0.1% |
| **Saturation** | How "full" the system is | CPU utilization < 70% |

---

### 7.7.4 Monitoring vs. Observability

| Dimension | Monitoring | Observability |
|-----------|------------|---------------|
| **Focus** | Known unknowns | Unknown unknowns |
| **Question** | "What is happening?" | "Why is this happening?" |
| **Approach** | Predefined dashboards and alerts | Exploratory; ask new questions |
| **Data** | Aggregated metrics | High-cardinality, dimensional data |

---

### 7.7.5 Alerting Principles

| Principle | Description |
|-----------|-------------|
| **Actionable** | Alerts should require human action |
| **No Alert Fatigue** | Too many alerts cause ignored alerts |
| **Page for Rare Events** | Only page for events requiring immediate attention |
| **Symptom-Based** | Alert on user-visible symptoms, not internal metrics |
| **Automated Remediation** | Automate common fixes; only page for what can't be automated |

---

## 7.8 Blameless Post-Mortems

---

### 7.8.1 What Is a Blameless Post-Mortem?

A **blameless post-mortem** is a process for learning from incidents without assigning blame. It focuses on understanding what happened, why, and how to prevent recurrence.

> **🔑 Key Insight:** Blameless culture encourages transparency. When people fear punishment, they hide mistakes, and systemic issues go unaddressed.

---

### 7.8.2 Post-Mortem Structure

| Section | Description |
|---------|-------------|
| **Summary** | Brief overview of incident |
| **Timeline** | Chronological events with timestamps |
| **Root Cause** | Underlying factors (not "human error") |
| **Impact** | Customer impact, duration, severity |
| **Detection** | How was it discovered? How could it be faster? |
| **Response** | What was done? What worked? What didn't? |
| **Action Items** | Specific, tracked improvements |

---

### 7.8.3 Root Cause Analysis Techniques

| Technique | Description |
|-----------|-------------|
| **5 Whys** | Ask "why" repeatedly to reach root cause |
| **Fishbone Diagram** | Categorize potential causes (people, process, technology, environment) |
| **Timeline Analysis** | Map events leading to incident |

**5 Whys Example:**

| Question | Answer |
|----------|--------|
| Why did the system fail? | Database connection pool exhausted. |
| Why was the pool exhausted? | Application didn't close connections. |
| Why didn't it close connections? | Exception handling didn't include close in finally block. |
| Why wasn't this caught in testing? | No integration test for this error scenario. |
| Why was there no test? | Test coverage requirements didn't include error scenarios. |

**Root Cause:** Test coverage standards incomplete; processes need update.

---

## 💡 Study Activity: Deep Dive

---

### Activity 1: Maintenance Type Classification

Classify each scenario as Corrective, Adaptive, Perfective, or Preventive:

| Scenario | Type |
|----------|------|
| Fixing a calculation error in invoice generation | |
| Updating the system to work with a new payment gateway | |
| Adding a new reporting feature requested by users | |
| Refactoring code to reduce technical debt | |
| Applying a security patch for a known vulnerability | |
| Updating documentation for clarity | |

<details>
<summary>Click for answer</summary>

| Scenario | Type |
|----------|------|
| Fixing a calculation error in invoice generation | **Corrective** (fixing defect) |
| Updating the system to work with a new payment gateway | **Adaptive** (new environment) |
| Adding a new reporting feature requested by users | **Perfective** (new functionality) |
| Refactoring code to reduce technical debt | **Preventive** (proactive improvement) |
| Applying a security patch for a known vulnerability | **Corrective** (fixing security defect) |
| Updating documentation for clarity | **Perfective** (improvement) |

</details>

---

### Activity 2: Technical Debt Analysis

For each situation, identify the type of technical debt and recommend action:

| Situation | Debt Type | Recommended Action |
|-----------|-----------|-------------------|
| Team took shortcuts to meet release deadline; planned to refactor later | | |
| Junior developer wrote code without proper design; team unaware of issues | | |
| No automated tests; all testing is manual and slow | | |
| Documentation is outdated; new developers struggle to understand | | |

<details>
<summary>Click for answer</summary>

| Situation | Debt Type | Recommended Action |
|-----------|-----------|-------------------|
| Team took shortcuts to meet release deadline; planned to refactor later | **Deliberate (Prudent)** | Track in backlog; schedule refactoring in upcoming sprints; document rationale |
| Junior developer wrote code without proper design; team unaware of issues | **Inadvertent (Reckless)** | Code review to identify issues; add to backlog; provide mentoring; improve review process |
| No automated tests; all testing is manual and slow | **Testing Debt** | Prioritize building test automation; start with critical paths; measure coverage improvement |
| Documentation is outdated; new developers struggle to understand | **Documentation Debt** | Allocate time for documentation updates; consider documentation-as-code approach |

</details>

---

### Activity 3: Legacy System Strategy Selection

For each scenario, recommend a modernization strategy:

| Scenario | Recommended Strategy |
|----------|---------------------|
| 20-year-old COBOL system handling payroll. No business changes expected for 5 years. | |
| Critical e-commerce system. Needs frequent feature updates. High technical debt. | |
| Internal reporting system. Users prefer Excel; system is rarely used. | |
| 10-year-old Java system with good architecture. Needs to integrate with new API. | |

<details>
<summary>Click for answer</summary>

| Scenario | Recommended Strategy |
|----------|---------------------|
| 20-year-old COBOL system handling payroll. No business changes expected for 5 years. | **Encapsulate** (wrap with APIs, maintain as-is) or **Rehost** (move to modern infrastructure) |
| Critical e-commerce system. Needs frequent feature updates. High technical debt. | **Strangler Pattern** (gradually replace with microservices) or **Re-architect** |
| Internal reporting system. Users prefer Excel; system is rarely used. | **Retire** (decommission if no longer needed) |
| 10-year-old Java system with good architecture. Needs to integrate with new API. | **Encapsulate** (add API layer) or **Refactor** (improve code to enable integration) |

</details>

---

### Activity 4: CI/CD Pipeline Design

Design a CI/CD pipeline for a critical financial application. Include stages, quality gates, and deployment strategy.

<details>
<summary>Click for answer</summary>

**CI Stage (Fast, Every Commit):**
- Code commit triggers pipeline
- Unit tests (must pass)
- Static analysis (security, code quality)
- Build and package

**Quality Gate:**
- If CI fails → block merge, notify team

**CD Stage (On Successful CI):**
- Deploy to development environment
- Integration tests
- API contract tests
- Security scanning (SAST, dependency scan)
- Deploy to staging environment
- Performance tests
- Security penetration tests

**Quality Gate:**
- Manual approval for production

**Production Deployment:**
- Canary deployment (5% traffic, monitor 30 min)
- Gradually increase to 50%, then 100%
- Automated rollback if error rate increases
- Smoke tests after deployment

**Monitoring:**
- Latency, error rate, throughput dashboards
- Alert on error rate > 0.1%
- Blameless post-mortem for incidents

</details>

---

### Activity 5: Post-Mortem Analysis

A payment service was down for 2 hours. Timeline:
- 10:00 - Deployment of new version
- 10:05 - Error rate spikes to 50%
- 10:10 - On-call alerted
- 10:30 - Rollback initiated
- 11:00 - Service fully restored

Create a blameless post-mortem structure.

<details>
<summary>Click for answer</summary>

**Summary:** Payment service unavailable for 2 hours due to database connection leak introduced in version 2.3.0.

**Timeline:**
- 10:00: Deployment of version 2.3.0
- 10:05: Error rate increases to 50%; monitoring alert triggered
- 10:10: On-call engineer receives alert
- 10:15: Engineer identifies error pattern (connection pool exhaustion)
- 10:30: Rollback to version 2.2.0 initiated
- 11:00: Service fully restored; error rate returns to normal

**Root Cause Analysis (5 Whys):**
1. Why did connections leak? → New code didn't close connections
2. Why wasn't this caught? → Integration tests didn't cover error scenarios
3. Why no error scenario tests? → Test coverage standards incomplete
4. Why incomplete standards? → Process not updated for new patterns
5. Why process not updated? → No post-deployment review for standards

**Action Items:**
1. Update test coverage standards to include error scenarios
2. Add database connection leak detection to CI pipeline
3. Enhance monitoring to alert on connection pool metrics
4. Review deployment rollback procedure to reduce time

</details>

---

## 📝 Module 7 Self-Assessment Quiz

1. What are the four types of software maintenance?

   <details>
   <summary>Click for answer</summary>
   Corrective (fix defects), Adaptive (new environments), Perfective (enhancements), Preventive (proactive improvement).
   </details>

2. What percentage of software costs typically occur during maintenance?

   <details>
   <summary>Click for answer</summary>
   80-90% of total software costs occur after delivery, during the maintenance phase.
   </details>

3. What is technical debt?

   <details>
   <summary>Click for answer</summary>
   The implied cost of additional rework caused by choosing an easy solution now instead of a better approach that would take longer.
   </details>

4. What are the four quadrants of technical debt prioritization?

   <details>
   <summary>Click for answer</summary>
   Critical (High Principal, Low Interest), Urgent (Low Principal, High Interest), Strategic (High Principal, High Interest), Quick Wins (Low Principal, Low Interest).
   </details>

5. What is the Strangler Pattern?

   <details>
   <summary>Click for answer</summary>
   A legacy system modernization strategy that gradually replaces parts of a legacy system with new services while maintaining overall system functionality.
   </details>

6. What are the Three Ways of DevOps?

   <details>
   <summary>Click for answer</summary>
   Flow (accelerate work from Dev to Ops), Feedback (shorten feedback loops), Continuous Learning (experiment, learn, improve).
   </details>

7. What is the difference between Continuous Delivery and Continuous Deployment?

   <details>
   <summary>Click for answer</summary>
   Continuous Delivery: every change is ready to deploy but requires manual approval for production. Continuous Deployment: every change that passes tests is automatically deployed to production.
   </details>

8. What are Blue/Green and Canary deployment strategies?

   <details>
   <summary>Click for answer</summary>
   Blue/Green: two identical environments; switch between them. Canary: deploy to small subset of users; gradually increase if healthy.
   </details>

9. What are the three pillars of observability?

   <details>
   <summary>Click for answer</summary>
   Logs (discrete events), Metrics (aggregated measurements), Traces (end-to-end request flows).
   </details>

10. What is a blameless post-mortem?

    <details>
    <summary>Click for answer</summary>
    A process for learning from incidents without assigning blame, focusing on understanding root causes and preventing recurrence.
    </details>

---

## 🔗 Connections to Other Modules

| Concept from Module 7 | Connects to |
|-----------------------|-------------|
| Maintenance types | Module 1: Software lifecycle |
| Technical debt | Module 4: Implementation (clean code) |
| Legacy systems | Module 4: Architecture (modernization) |
| CI/CD | Module 6: Testing (automation) |
| Observability | Module 6: Testing (monitoring) |

---

## ✅ Module 7 Summary

| Section | Key Takeaways |
|---------|---------------|
| **7.1 Maintenance** | 4 types: Corrective, Adaptive, Perfective, Preventive; 80-90% of costs |
| **7.2 Technical Debt** | Principal and interest; 4 quadrants; deliberate vs. inadvertent |
| **7.3 Legacy Systems** | Characteristics; modernization strategies (Retire, Encapsulate, Refactor, Re-architect, Rewrite); Strangler Pattern |
| **7.4 DevOps** | Culture, collaboration, automation; The Three Ways |
| **7.5 CI/CD** | CI (build, test on commit); CD (automated deployment pipeline); deployment strategies |
| **7.6 Infrastructure as Code** | Declarative vs. imperative; version-controlled infrastructure |
| **7.7 Observability** | Logs, metrics, traces; Four Golden Signals; monitoring vs. observability |
| **7.8 Post-Mortems** | Blameless culture; root cause analysis; action items |

---
