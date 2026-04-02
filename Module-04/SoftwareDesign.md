# Module 04: Software Design

## Learning Objectives
- Understand the role of design in the software development lifecycle.
- Apply key software design concepts: abstraction, modularity, encapsulation, coupling, cohesion.
- Create design models using structured and object-oriented approaches.
- Evaluate design quality using metrics and heuristics.

## Key Topics

### 1. Design Fundamentals
- **Design vs. Analysis**: Analysis focuses on *what* is needed; design defines *how* to satisfy those needs.
- **Key Concepts**:
  - **Abstraction**: Hiding unnecessary details.
  - **Modularity**: Decomposing system into smaller, manageable components.
  - **Coupling & Cohesion**: Low coupling + high cohesion = maintainable design.
  - **Encapsulation & Information Hiding**: Limiting access to internal data/behavior.

### 2. Design Process
- **Design Activities**:
  - Architectural design (high-level structure)
  - Interface design (component interactions)
  - Component-level design (internal details)
  - Database/data design
- **Design Models**:
  - Structural models (static relationships)
  - Behavioral models (dynamic interactions)

### 3. Structured Design
- **Approach**: Function-oriented, using DFDs, structure charts.
- **Advantages**: Clear flow, suitable for smaller systems.
- **Limitations**: Not ideal for systems with complex state or reuse.

### 4. Object-Oriented Design (OOD)
- **UML Diagrams**: Class, sequence, state, activity.
- **Design Patterns** (Gang of Four):
  - Creational (Singleton, Factory)
  - Structural (Adapter, Decorator)
  - Behavioral (Observer, Strategy)
- **Principles** (SOLID):
  - Single Responsibility, Open-Closed, Liskov Substitution, Interface Segregation, Dependency Inversion.

### 5. User-Centered Design (Overview)
- Iterative design based on user feedback.
- Prototyping (low-fidelity, high-fidelity).

### 6. Design Quality & Metrics
- **Metrics**: Depth of inheritance, coupling between objects, response for a class.
- **Heuristics**: Consistent naming, avoid deep inheritance, limit component size.

## Learning Activities
- Group exercise: Redesign a given module to reduce coupling.
- Case study: Apply three design patterns to a simple system (e.g., parking lot, ATM).

## Assessment
- Quiz on coupling/cohesion identification.
- Design document (UML diagrams + rationale) for a small system.

## References
- Pressman, R. *Software Engineering: A Practitioner’s Approach*.
- Gamma et al. *Design Patterns*.
- Sommerville, I. *Software Engineering*.
