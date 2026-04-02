
# Module 09: Software Maintenance & Evolution

## Learning Objectives
- Classify maintenance types: corrective, adaptive, perfective, preventive.
- Analyze the impact of software aging and technical debt.
- Plan reverse engineering and reengineering activities.
- Apply maintenance process models (e.g., quick-fix, iterative).

## Key Topics

### 1. Fundamentals of Maintenance
- **Definition**: Modification of a software product after delivery to correct faults, improve performance, or adapt to environment.
- **Lehman’s Laws of Software Evolution**:
  - Continuing change, increasing complexity, self-regulation, etc.

### 2. Types of Maintenance
- **Corrective**: Fix reported bugs.
- **Adaptive**: Respond to environment changes (OS, hardware, regulations).
- **Perfective**: Enhance performance, maintainability, new features.
- **Preventive**: Proactive improvements to prevent future issues.

### 3. Technical Debt
- **Definition**: Trade-off between short-term speed and long-term quality.
- **Types**: Code debt, design debt, test debt, documentation debt.
- **Measurement**: SonarQube, code analysis tools.
- **Repayment strategies**: Refactoring sprints, dedicated debt reduction.

### 4. Reverse Engineering & Reengineering
- **Reverse Engineering**: Analyze existing system to extract design/requirements.
- **Reengineering**:
  - Inventory analysis → document → restructure → forward engineer.
- **Refactoring** (maintenance context): Daily practice vs. large reengineering.

### 5. Maintenance Process Models
- **Quick-Fix Model**: Immediate patch (high risk).
- **Iterative Enhancement Model**: Small cycles.
- **Reuse-Oriented Model**.
- **IEEE 14764** maintenance process standard.

### 6. Impact Analysis & Prioritization
- Determine what will be affected by a change.
- Prioritization: Severity, urgency, risk, cost-benefit.

## Learning Activities
- Calculate technical debt for a small open-source project using a tool.
- Perform impact analysis for a proposed change request.

## Assessment
- Maintenance request response (impact analysis + solution plan).
- Case study analysis of a legacy system evolution.

## References
- Lehman, M. *Laws of Software Evolution*.
- Fowler, M. *Technical Debt*.
- Sommerville (Maintenance chapter).
