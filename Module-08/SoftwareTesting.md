
# Module 08: Software Testing

## Learning Objectives
- Differentiate between verification and validation.
- Apply black-box and white-box testing techniques.
- Design test cases using equivalence partitioning, boundary value analysis, and basis path testing.
- Plan testing levels: unit, integration, system, acceptance.
- Use test automation frameworks.

## Key Topics

### 1. Testing Fundamentals
- **Verification**: Are we building the product right? (static, reviews).
- **Validation**: Are we building the right product? (dynamic, execution).
- **Error, Fault, Failure**:
  - Error → mistake by person.
  - Fault (defect) → incorrect code/design.
  - Failure → visible incorrect behavior.

### 2. Testing Levels
- **Unit Testing**: Individual components (JUnit, pytest).
- **Integration Testing**: Interaction between modules (top-down, bottom-up, big-bang).
- **System Testing**: Entire system (functional, performance, security).
- **Acceptance Testing**: User validation (alpha/beta, UAT).

### 3. Black-Box Testing
- **Equivalence Partitioning**: Divide inputs into classes.
- **Boundary Value Analysis**: Test edges of partitions.
- **Decision Table Testing**: Combinations of conditions.
- **State Transition Testing**: Event-driven systems.
- **Use Case Testing**: Scenarios from requirements.

### 4. White-Box Testing
- **Basis Path Testing** (McCabe): Control flow graph, cyclomatic complexity.
- **Loop Testing**: Simple, nested, concatenated.
- **Data Flow Testing**: Define-use paths.
- **Statement & Branch Coverage**.

### 5. Test Automation
- **Frameworks**: Selenium (web), Appium (mobile), JUnit/TestNG.
- **Test Doubles**: Stubs, mocks, fakes (Mockito, unittest.mock).
- **Continuous Testing**: Run tests on every commit.

### 6. Testing Metrics & Reports
- **Coverage**: Line, branch, path.
- **Defect density**, **mean time to failure**.
- **Test execution reports** (pass/fail, logs).

## Learning Activities
- Create test cases for a given function using equivalence partitioning and boundary value analysis.
- Write unit tests for a small module using a test framework.

## Assessment
- Test plan document (levels, techniques, tools).
- Implement automated tests achieving ≥80% branch coverage.

## References
- Myers, G. *The Art of Software Testing*.
- Pressman (Testing chapters).
- JUnit / pytest documentation.
