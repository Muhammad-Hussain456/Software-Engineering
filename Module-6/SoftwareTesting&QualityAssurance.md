# Module 6: Software Testing & Quality Assurance

---

## 📌 Module Learning Objectives

By the end of this module, you should be able to:
- Understand the **importance of testing** in software development
- Distinguish between **verification and validation**
- Describe the **testing hierarchy** (unit, integration, system, acceptance)
- Understand **testing techniques** (black-box, white-box, experience-based)
- Explain **test-driven development (TDD)** and **behavior-driven development (BDD)**
- Understand **test automation** and **continuous testing**
- Apply **quality assurance principles** and metrics

---

## 6.1 Introduction to Software Testing

---

### 6.1.1 What Is Software Testing?

**Software testing** is the process of evaluating a system or its components to determine whether it meets specified requirements and to identify defects.

> **🔑 Key Insight:** Testing is not about proving that software works—it's about finding defects and reducing risk. Exhaustive testing is impossible; testing is always a risk-based activity.

#### Testing vs. Debugging

| Aspect | Testing | Debugging |
|--------|---------|-----------|
| **Purpose** | Find defects | Identify and fix root cause |
| **Who** | Testers, developers | Developers |
| **When** | Throughout development | After test finds a failure |
| **Output** | Defect reports, test results | Corrected code |
| **Mindset** | Find problems | Solve problems |

---

### 6.1.2 Why Testing Matters

| Reason | Description |
|--------|-------------|
| **Quality Assurance** | Ensures product meets requirements and expectations |
| **Risk Reduction** | Identifies critical defects before release |
| **Cost Savings** | Defects found earlier are cheaper to fix |
| **Safety** | Critical systems (medical, aviation) require rigorous testing |
| **Reputation** | Quality failures damage brand trust |
| **Compliance** | Regulatory requirements often mandate testing |

---

### 6.1.3 Verification vs. Validation

This is a fundamental distinction that appears frequently on the NSCT.

| Concept | Definition | Question |
|---------|------------|----------|
| **Verification** | Are we building the product right? | Does the implementation match specifications? |
| **Validation** | Are we building the right product? | Does the product meet user needs? |

**Examples:**

| Activity | Verification or Validation? |
|----------|---------------------------|
| Code review to check against design | Verification |
| Unit tests checking function correctness | Verification |
| User acceptance testing with customers | Validation |
| Checking requirements against user needs | Validation |
| Integration testing against interface specs | Verification |

> **🔑 Key Insight:** Verification ensures technical correctness; validation ensures business value. Both are necessary.

---

### 6.1.4 Testing Principles

| Principle | Description |
|-----------|-------------|
| **Testing Shows Presence of Defects** | Testing can show defects exist, not that they don't exist |
| **Exhaustive Testing Is Impossible** | Cannot test all inputs, scenarios, combinations |
| **Early Testing** | Find defects early when they are cheaper to fix |
| **Defect Clustering** | Small number of modules contain most defects (Pareto principle) |
| **Pesticide Paradox** | Running same tests repeatedly finds no new defects; tests must be updated |
| **Testing Is Context-Dependent** | Different systems require different testing approaches |
| **Absence-of-Errors Fallacy** | Finding and fixing defects doesn't guarantee user satisfaction |

---

## 6.2 Testing Levels (The Testing Pyramid)

---

### 6.2.1 Overview

The **testing pyramid** illustrates the ideal distribution of tests across levels.

```
                    ┌─────────────────────────────────────┐
                    │           UI / End-to-End           │
                    │            (Fewer tests)            │
                    │          Slow, brittle              │
                    ├─────────────────────────────────────┤
                    │        Integration Tests            │
                    │        (Some tests)                 │
                    │      Moderate speed                 │
                    ├─────────────────────────────────────┤
                    │          Unit Tests                 │
                    │         (Many tests)                │
                    │        Fast, reliable               │
                    └─────────────────────────────────────┘
```

---

### 6.2.2 Unit Testing

**Definition:** Testing individual components or units of code in isolation.

| Aspect | Description |
|--------|-------------|
| **Scope** | Single function, method, or class |
| **Isolation** | External dependencies are mocked or stubbed |
| **Responsibility** | Developers |
| **Frequency** | Every code change |
| **Speed** | Very fast (milliseconds to seconds) |

**What Unit Tests Verify:**
- Correctness of logic and algorithms
- Boundary conditions
- Error handling
- Edge cases

> **🔑 Key Insight:** Unit tests are the foundation of the testing pyramid. They are fast, reliable, and provide immediate feedback to developers.

---

### 6.2.3 Integration Testing

**Definition:** Testing interactions between components to verify they work together correctly.

| Aspect | Description |
|--------|-------------|
| **Scope** | Multiple components, modules, or services |
| **Isolation** | Real dependencies or test doubles |
| **Responsibility** | Developers, testers |
| **Frequency** | When components are integrated |
| **Speed** | Moderate (seconds to minutes) |

**Integration Approaches:**

| Approach | Description | Pros | Cons |
|----------|-------------|------|------|
| **Big Bang** | Integrate all components at once | Simple | Difficult to isolate defects |
| **Top-Down** | Integrate from high-level down | Early UI testing | Stubs needed for low-level |
| **Bottom-Up** | Integrate from low-level up | Early API testing | Drivers needed for high-level |
| **Sandwich** | Combine top-down and bottom-up | Balanced | Complex coordination |

---

### 6.2.4 System Testing

**Definition:** Testing the complete, integrated system against requirements.

| Aspect | Description |
|--------|-------------|
| **Scope** | Entire system |
| **Environment** | Production-like or staging |
| **Responsibility** | Test team, QA |
| **Frequency** | Before releases |
| **Speed** | Slow (minutes to hours) |

**Types of System Testing:**

| Type | Focus |
|------|-------|
| **Functional Testing** | Verifies functional requirements |
| **Performance Testing** | Response time, throughput, scalability |
| **Load Testing** | Behavior under expected load |
| **Stress Testing** | Behavior beyond breaking point |
| **Security Testing** | Vulnerabilities, authentication, authorization |
| **Usability Testing** | User experience, ease of use |
| **Compatibility Testing** | Different browsers, devices, operating systems |
| **Reliability Testing** | Mean time between failures, uptime |

---

### 6.2.5 Acceptance Testing

**Definition:** Testing to determine whether the system meets user needs and is ready for delivery.

| Aspect | Description |
|--------|-------------|
| **Scope** | Entire system from user perspective |
| **Environment** | Production-like or production |
| **Responsibility** | Users, product owner, QA |
| **Frequency** | Before release |
| **Speed** | Slow (hours to days) |

**Types of Acceptance Testing:**

| Type | Description |
|------|-------------|
| **User Acceptance Testing (UAT)** | Users verify system meets their needs |
| **Operational Acceptance Testing** | Operations team verifies deployability, backup, recovery |
| **Contract Acceptance Testing** | Verifies against contract specifications |
| **Regulatory Acceptance Testing** | Verifies compliance with regulations |
| **Alpha Testing** | Internal testing at developer site |
| **Beta Testing** | External testing at customer site |

---

### 6.2.6 Regression Testing

**Definition:** Re-running tests to ensure that new changes have not broken existing functionality.

| Aspect | Description |
|--------|-------------|
| **When** | After any change (code, configuration, environment) |
| **What** | Re-run existing tests (unit, integration, system) |
| **Challenge** | Test suite grows; execution time increases |

**Regression Testing Strategies:**

| Strategy | Description |
|----------|-------------|
| **Retest All** | Run all tests; thorough but slow |
| **Selective** | Run only tests affected by changes |
| **Prioritized** | Run most important tests first |
| **Hybrid** | Combine selective and prioritized |

> **🔑 Key Insight:** Automated testing is essential for effective regression testing. Without automation, regression testing becomes prohibitively expensive.

---

## 6.3 Testing Techniques

---

### 6.3.1 Black-Box Testing

**Definition:** Testing based on inputs and outputs without knowledge of internal structure.

| Aspect | Description |
|--------|-------------|
| **Focus** | Functionality, requirements, behavior |
| **Knowledge** | No internal code knowledge needed |
| **Performed By** | Testers, QA, users |

**Black-Box Techniques:**

| Technique | Description | Example |
|-----------|-------------|---------|
| **Equivalence Partitioning** | Divide inputs into groups that should behave similarly | Ages 0-17, 18-64, 65+ |
| **Boundary Value Analysis** | Test at boundaries of partitions | Test ages: 17, 18, 64, 65 |
| **Decision Table Testing** | Combinations of conditions and actions | Credit approval: income, credit score, existing debt |
| **State Transition Testing** | System states and transitions | Login: logged out → logging in → logged in |
| **Use Case Testing** | Test scenarios from use cases | End-to-end user journeys |

---

### 6.3.2 White-Box Testing

**Definition:** Testing based on internal structure, code, and logic.

| Aspect | Description |
|--------|-------------|
| **Focus** | Code coverage, logic paths, internal structures |
| **Knowledge** | Requires code and design knowledge |
| **Performed By** | Developers, technical testers |

**White-Box Techniques:**

| Technique | Description | Coverage Goal |
|-----------|-------------|---------------|
| **Statement Coverage** | Execute each line of code | All statements executed |
| **Branch Coverage** | Execute each decision branch | Both true and false paths |
| **Path Coverage** | Execute all possible paths | All combinations (often impossible) |
| **Condition Coverage** | Test each boolean condition | Each condition true and false |
| **Loop Coverage** | Test loop boundaries | 0, 1, multiple iterations |

**Coverage Levels:**

| Level | Description | Target |
|-------|-------------|--------|
| Statement Coverage | Every line executed | 80-100% |
| Branch Coverage | Every decision path | 70-90% |
| Path Coverage | All possible paths | Often impractical |

---

### 6.3.3 Experience-Based Testing

**Definition:** Testing based on tester's knowledge, intuition, and experience.

| Aspect | Description |
|--------|-------------|
| **Focus** | Uncovered defects, exploratory scenarios |
| **Knowledge** | Domain experience, defect patterns |

**Experience-Based Techniques:**

| Technique | Description |
|-----------|-------------|
| **Exploratory Testing** | Simultaneous learning, test design, and execution |
| **Error Guessing** | Anticipating likely defects based on experience |
| **Checklist-Based Testing** | Using checklists of common failure areas |

---

### 6.3.4 Static Testing

**Definition:** Testing without executing code.

| Technique | Description |
|-----------|-------------|
| **Code Review** | Systematic examination of code by peers |
| **Walkthrough** | Author leads team through code |
| **Inspection** | Formal, structured review with defined roles |
| **Static Analysis** | Automated analysis of code (style, complexity, potential defects) |

**Benefits of Static Testing:**
- Finds defects early (before execution)
- Improves code quality and maintainability
- Knowledge sharing across team
- Lower cost than dynamic testing

---

## 6.4 Test-Driven Development (TDD)

---

### 6.4.1 Overview

**Test-Driven Development** is a development practice where tests are written before the code they verify.

> **🔑 Key Insight:** TDD inverts the traditional development cycle. Instead of "code then test," it is "test then code."

---

### 6.4.2 The TDD Cycle (Red-Green-Refactor)

```
┌─────────────────────────────────────────────────────────────────────────────┐
│                         TDD Cycle (Red-Green-Refactor)                      │
├─────────────────────────────────────────────────────────────────────────────┤
│                                                                             │
│   ┌─────────────────────────────────────────────────────────────────────┐   │
│   │                                                                     │   │
│   │   RED                    GREEN                   REFACTOR           │   │
│   │   ┌─────────────┐        ┌─────────────┐         ┌─────────────┐   │   │
│   │   │ Write a     │───────▶│ Write the  │────────▶│ Improve     │   │   │
│   │   │ failing     │        │ minimal    │         │ code while  │   │   │
│   │   │ test        │        │ code to    │         │ keeping     │   │   │
│   │   │             │        │ pass       │         │ tests green │   │   │
│   │   └─────────────┘        └─────────────┘         └─────────────┘   │   │
│   │         │                      │                       │           │   │
│   │         │                      │                       │           │   │
│   │         ▼                      ▼                       ▼           │   │
│   │   Test fails              Test passes             Tests still     │   │
│   │   (no implementation)     (implementation        pass; code      │   │
│   │                           exists)                improved        │   │
│   │                                                                     │   │
│   │                         Repeat for next test                        │   │
│   └─────────────────────────────────────────────────────────────────────┘   │
│                                                                             │
└─────────────────────────────────────────────────────────────────────────────┘
```

---

### 6.4.3 TDD Benefits

| Benefit | Description |
|---------|-------------|
| **Defect Prevention** | Defects found immediately during development |
| **Design Improvement** | Forces modular, testable design |
| **Documentation** | Tests document expected behavior |
| **Regression Safety** | Comprehensive test suite enables safe refactoring |
| **Confidence** | Developers can change code with confidence |

---

### 6.4.4 TDD Challenges

| Challenge | Description |
|-----------|-------------|
| **Learning Curve** | Requires discipline and practice |
| **Time Investment** | Initially slower than writing code directly |
| **Test Maintenance** | Tests must be maintained as code evolves |
| **Not Always Appropriate** | Some systems (UI, legacy) are difficult to test first |

---

## 6.5 Behavior-Driven Development (BDD)

---

### 6.5.1 Overview

**Behavior-Driven Development** extends TDD by using natural language scenarios to describe expected behavior.

> **🔑 Key Insight:** BDD focuses on system behavior from the user perspective, creating a common language between business stakeholders and developers.

---

### 6.5.2 Gherkin Language

BDD scenarios are written in **Gherkin**, a structured natural language.

**Format:**
```
Feature: [Feature name]
  As a [role]
  I want [feature]
  So that [benefit]

  Scenario: [Scenario name]
    Given [initial context]
    When [action occurs]
    Then [expected outcome]
    And [additional conditions]
```

**Example:**
```
Feature: User Login
  As a registered user
  I want to log in to the system
  So that I can access my account

  Scenario: Successful login
    Given I am on the login page
    When I enter valid credentials
    And I click the login button
    Then I should see my dashboard

  Scenario: Failed login
    Given I am on the login page
    When I enter invalid credentials
    And I click the login button
    Then I should see an error message
    And I should remain on the login page
```

---

### 6.5.3 BDD Benefits

| Benefit | Description |
|---------|-------------|
| **Shared Understanding** | Business, development, and testing use same language |
| **Living Documentation** | Scenarios are executable and always up-to-date |
| **User Focus** | Behavior is described from user perspective |
| **Test Automation** | Scenarios can be automated directly |

---

## 6.6 Test Automation

---

### 6.6.1 What to Automate

| Automate | Don't Automate |
|----------|----------------|
| Repetitive tests | Exploratory testing |
| Regression tests | One-time tests |
| High-risk areas | Tests that change frequently |
| Performance tests | Tests with high maintenance cost |
| Smoke tests | Usability tests (human judgment needed) |

---

### 6.6.2 Test Automation Pyramid

```
                    ┌─────────────────────────────────────┐
                    │         UI Automation               │
                    │      (Few, high-level)              │
                    │    Slow, brittle, expensive         │
                    ├─────────────────────────────────────┤
                    │        API/Service Automation       │
                    │        (Some, medium-level)         │
                    │      Faster, more stable            │
                    ├─────────────────────────────────────┤
                    │         Unit Automation             │
                    │        (Many, low-level)            │
                    │    Fast, reliable, inexpensive      │
                    └─────────────────────────────────────┘
```

---

### 6.6.3 Continuous Testing

**Continuous Testing** is the practice of executing automated tests as part of the software delivery pipeline.

| Principle | Description |
|-----------|-------------|
| **Early Testing** | Tests run on every code commit |
| **Fast Feedback** | Test results available immediately |
| **Gatekeeping** | Failed tests block deployment |
| **Shift Left** | Testing moves earlier in lifecycle |

---

### 6.6.4 Test Doubles

**Test Doubles** replace real dependencies to isolate the system under test.

| Type | Description | Use Case |
|------|-------------|----------|
| **Dummy** | Passed but never used | Filling parameter lists |
| **Stub** | Returns predefined answers | Providing test data |
| **Spy** | Records how it was called | Verifying interactions |
| **Mock** | Pre-programmed expectations | Verifying specific interactions |
| **Fake** | Lightweight working implementation | In-memory database |

---

## 6.7 Quality Assurance

---

### 6.7.1 Quality Assurance vs. Quality Control

| Aspect | Quality Assurance (QA) | Quality Control (QC) |
|--------|------------------------|---------------------|
| **Focus** | Process | Product |
| **Goal** | Prevent defects | Detect defects |
| **Activity** | Process definition, audits, training | Testing, inspections, reviews |
| **When** | Throughout development | During and after development |
| **Responsibility** | Everyone | Testers, QA team |

---

### 6.7.2 Quality Metrics

| Metric | Description | Target |
|--------|-------------|--------|
| **Defect Density** | Defects per unit of size (KLOC, function points) | Depends on criticality |
| **Defect Removal Efficiency** | % of defects found before release | > 95% for critical systems |
| **Mean Time to Detect** | Average time to find a defect | As low as possible |
| **Mean Time to Fix** | Average time to fix a defect | As low as possible |
| **Test Coverage** | % of code exercised by tests | > 80% for unit tests |
| **Escaped Defects** | Defects found in production | As close to zero as possible |

---

### 6.7.3 Code Review Practices

| Review Type | Description | Formality |
|-------------|-------------|-----------|
| **Over-the-Shoulder** | Quick review with colleague | Low |
| **Pair Programming** | Two developers working together | Medium |
| **Tool-Assisted** | Pull request reviews (GitHub, GitLab) | Medium |
| **Formal Inspection** | Structured meeting with defined roles | High |

**Code Review Checklist:**

| Category | Items to Check |
|----------|----------------|
| **Correctness** | Does it do what it should? |
| **Design** | Is it well-structured? Follows patterns? |
| **Readability** | Is it easy to understand? |
| **Maintainability** | Is it easy to change? |
| **Testing** | Are there tests? Do they cover edge cases? |
| **Security** | Are there vulnerabilities? |
| **Performance** | Are there bottlenecks? |

---

### 6.7.4 Continuous Improvement

| Practice | Description |
|----------|-------------|
| **Retrospectives** | Regular team reflection on what went well, what didn't |
| **Root Cause Analysis** | Identify underlying causes of defects |
| **Defect Prevention** | Address root causes to prevent recurrence |
| **Process Improvement** | Continuously refine processes based on data |

---

## 💡 Study Activity: Deep Dive

---

### Activity 1: Testing Level Classification

For each test scenario, identify the appropriate testing level (Unit, Integration, System, Acceptance):

| Scenario | Level |
|----------|-------|
| Testing that a login function correctly hashes passwords | |
| Testing that the login service correctly communicates with the user database | |
| Testing that a user can log in, browse products, add to cart, and checkout | |
| A customer representative testing the system before release | |
| Testing that the system handles 10,000 concurrent users | |

<details>
<summary>Click for answer</summary>

| Scenario | Level |
|----------|-------|
| Testing that a login function correctly hashes passwords | **Unit** (single function in isolation) |
| Testing that the login service correctly communicates with the user database | **Integration** (interaction between components) |
| Testing that a user can log in, browse products, add to cart, and checkout | **System** (end-to-end functionality) |
| A customer representative testing the system before release | **Acceptance** (user validates need) |
| Testing that the system handles 10,000 concurrent users | **System** (performance testing) |

</details>

---

### Activity 2: Testing Technique Selection

For each scenario, recommend the most appropriate testing technique:

| Scenario | Technique |
|----------|-----------|
| Testing a function that calculates tax based on income brackets | |
| Testing a login system with multiple authentication methods | |
| Testing a legacy system with no documentation | |
| Testing a safety-critical system where all code paths must be executed | |

<details>
<summary>Click for answer</summary>

| Scenario | Technique |
|----------|-----------|
| Testing a function that calculates tax based on income brackets | **Equivalence Partitioning + Boundary Value Analysis** (input ranges with clear boundaries) |
| Testing a login system with multiple authentication methods | **Decision Table Testing** (combinations of authentication methods, success/failure) |
| Testing a legacy system with no documentation | **Exploratory Testing** (learning through exploration) |
| Testing a safety-critical system where all code paths must be executed | **Path Coverage** (white-box; ensures all paths executed) |

</details>

---

### Activity 3: TDD Cycle Application

Describe the steps a developer would follow using TDD to implement a discount calculation function:

<details>
<summary>Click for answer</summary>

**RED (Write Failing Test):**
- Write test for 10% discount for orders over $100
- Test expects discount amount
- Test fails because no implementation exists

**GREEN (Write Minimal Code):**
- Implement discount function returning 10% for orders over $100
- Test passes

**REFACTOR (Improve Code):**
- Add additional discount tiers (20% over $200, 5% for new customers)
- Write tests for each tier first
- Refactor to use configurable discount rules
- Ensure all tests continue to pass

**Repeat:**
- Add edge cases (negative amounts, zero, maximum discount caps)
- Each new test follows red-green-refactor cycle
- Final test suite provides confidence in correct behavior

</details>

---

### Activity 4: Quality Metrics Interpretation

Interpret each metric and its implications:

| Metric | Value | Interpretation |
|--------|-------|----------------|
| Defect Density | 5 defects per KLOC | |
| Defect Removal Efficiency | 85% | |
| Escaped Defects | 10 critical defects in production | |
| Test Coverage | 95% | |

<details>
<summary>Click for answer</summary>

| Metric | Value | Interpretation |
|--------|-------|----------------|
| Defect Density | 5 defects per KLOC | Industry average is 2-5; may be acceptable for business applications, high for safety-critical. Requires investigation of quality processes. |
| Defect Removal Efficiency | 85% | Industry benchmark is 95%+ for mature organizations. 15% of defects reach production. Improvement needed in testing or reviews. |
| Escaped Defects | 10 critical defects in production | Unacceptable for most systems. Critical defects should be caught before release. Root cause analysis required. |
| Test Coverage | 95% | Excellent coverage, but coverage doesn't guarantee test quality. Ensure meaningful assertions, not just execution. |

</details>

---

### Activity 5: Verification vs. Validation

Classify each activity as Verification or Validation:

| Activity | Verification or Validation? |
|----------|---------------------------|
| Code review against design specifications | |
| User acceptance testing | |
| Checking that requirements are complete and consistent | |
| Testing that an API meets its contract | |
| Demonstrating new features to stakeholders | |

<details>
<summary>Click for answer</summary>

| Activity | Verification or Validation? |
|----------|---------------------------|
| Code review against design specifications | **Verification** (checking against spec) |
| User acceptance testing | **Validation** (checking user needs) |
| Checking that requirements are complete and consistent | **Validation** (checking requirements meet user needs) |
| Testing that an API meets its contract | **Verification** (checking against contract) |
| Demonstrating new features to stakeholders | **Validation** (stakeholders confirm value) |

</details>

---

## 📝 Module 6 Self-Assessment Quiz

1. What is the difference between verification and validation?

   <details>
   <summary>Click for answer</summary>
   Verification asks "Are we building the product right?" (conformance to specifications). Validation asks "Are we building the right product?" (meets user needs).
   </details>

2. What are the four levels of testing in order from smallest scope to largest?

   <details>
   <summary>Click for answer</summary>
   Unit Testing → Integration Testing → System Testing → Acceptance Testing.
   </details>

3. What is the testing pyramid?

   <details>
   <summary>Click for answer</summary>
   A model showing the ideal distribution of tests: many fast, reliable unit tests at the base; fewer integration tests in the middle; fewest UI/end-to-end tests at the top.
   </details>

4. What is the difference between black-box and white-box testing?

   <details>
   <summary>Click for answer</summary>
   Black-box testing uses inputs and outputs without knowledge of internal structure; white-box testing uses knowledge of code and internal logic.
   </details>

5. What are equivalence partitioning and boundary value analysis?

   <details>
   <summary>Click for answer</summary>
   Equivalence partitioning divides inputs into groups that should behave similarly; boundary value analysis tests at the edges of those partitions where defects are most likely.
   </details>

6. What are the three phases of the TDD cycle?

   <details>
   <summary>Click for answer</summary>
   Red (write failing test), Green (write minimal code to pass), Refactor (improve code while keeping tests green).
   </details>

7. What is the Gherkin format used for?

   <details>
   <summary>Click for answer</summary>
   Gherkin is used in Behavior-Driven Development (BDD) to write scenarios in natural language (Given-When-Then) that are both human-readable and executable.
   </details>

8. What is regression testing?

   <details>
   <summary>Click for answer</summary>
   Re-running tests to ensure that new changes have not broken existing functionality.
   </details>

9. What is the difference between Quality Assurance and Quality Control?

   <details>
   <summary>Click for answer</summary>
   Quality Assurance is process-focused (preventing defects); Quality Control is product-focused (detecting defects).
   </details>

10. What are test doubles and what are the main types?

    <details>
    <summary>Click for answer</summary>
    Test doubles replace real dependencies to isolate the system under test. Types: Dummy (unused), Stub (returns canned answers), Spy (records interactions), Mock (pre-programmed expectations), Fake (lightweight implementation).
    </details>

---

## 🔗 Connections to Other Modules

| Concept from Module 6 | Connects to |
|-----------------------|-------------|
| Verification vs. Validation | Module 2: Requirements (validation of requirements) |
| Test levels | Module 4: Implementation (unit testing by developers) |
| TDD | Module 4: Implementation (development practice) |
| Acceptance testing | Module 2: Requirements (acceptance criteria) |
| Quality metrics | Module 5: Project Management (quality planning) |
| Continuous testing | Module 4: CI/CD pipeline |

---

## ✅ Module 6 Summary

| Section | Key Takeaways |
|---------|---------------|
| **6.1 Introduction** | Testing finds defects; verification vs. validation; testing principles |
| **6.2 Testing Levels** | Unit → Integration → System → Acceptance; regression testing |
| **6.3 Testing Techniques** | Black-box (equivalence, boundary, decision tables); white-box (statement, branch, path coverage); experience-based (exploratory) |
| **6.4 TDD** | Red-Green-Refactor cycle; benefits: design improvement, regression safety |
| **6.5 BDD** | Gherkin scenarios (Given-When-Then); shared language between business and technical |
| **6.6 Test Automation** | Automation pyramid; test doubles; continuous testing |
| **6.7 Quality Assurance** | QA vs. QC; quality metrics; code reviews; continuous improvement |

---
