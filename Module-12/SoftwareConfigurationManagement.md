
# Module 12: Software Configuration Management (SCM)

## Learning Objectives
- Define configuration items (CIs) and baselines.
- Perform version control, change control, and build management.
- Implement SCM plans using tools (Git, SVN, Artifactory).
- Conduct configuration audits.

## Key Topics

### 1. SCM Fundamentals
- **Configuration Item (CI)**: Any artifact under control (code, docs, models, test data).
- **Baseline**: A formally approved version of a CI at a specific time.
- **SCM Activities**:
  - Configuration identification
  - Version control
  - Change control
  - Configuration status accounting
  - Configuration audits

### 2. Version Control Systems (VCS)
- **Centralized (CVS, SVN)** vs. **Distributed (Git, Mercurial)**.
- **Git basics**:
  - Repository, commit, branch, merge, tag.
  - Workflows: GitFlow, GitHub Flow, Trunk-based.
- **Best practices**: Atomic commits, meaningful messages, avoid large binaries.

### 3. Change Control Process
- **Change Request (CR)** → **Impact analysis** → **Approval** (CCB) → **Implementation** → **Verification**.
- **Change Control Board (CCB)** roles.
- **Tools**: Jira, GitHub Issues, Bugzilla.

### 4. Build Management & Continuous Integration
- **Build**: Compilation, linking, packaging.
- **Tools**: Maven, Gradle, Make, npm.
- **CI/CD**: Jenkins, GitLab CI, GitHub Actions.
  - Automate build, test, and deployment.

### 5. Configuration Audits
- **Functional audit**: Does the CI meet requirements?
- **Physical audit**: Is the implementation as documented?

### 6. SCM Plan (IEEE 828)
- **Sections**:
  - Scope, responsibilities, tools, schedules.
  - Configuration identification scheme.
  - Change control procedure.
  - Version control strategy.
  - Audit and reporting.

## Learning Activities
- Simulate a change control process: submit, review, approve, commit a CR.
- Set up a Git repository with branching strategy for a small team project.

## Assessment
- SCM plan document for a semester project.
- Git log analysis and audit report.

## References
- IEEE Std 828 (SCM standard).
- Pro Git book (free online).
- Sommerville (SCM chapter).
