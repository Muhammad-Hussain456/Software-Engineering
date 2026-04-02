# Module 05: Software Architecture

## Learning Objectives
- Define software architecture and its role in quality attributes.
- Compare common architectural styles.
- Apply Architecture Trade-off Analysis Method (ATAM).
- Document architecture using views (e.g., 4+1 view model).

## Key Topics

### 1. Introduction to Architecture
- **Definition**: Fundamental organization of a system, its components, relationships, and guiding principles.
- **Importance**: Enables analysis of quality attributes (performance, security, modifiability).

### 2. Architectural Styles & Patterns
- **Data-Centered**: Shared data repository (e.g., database, blackboard).
- **Data Flow**: Batch sequential, pipe-and-filter.
- **Call-and-Return**: Main program/subroutine, OO, layered.
- **Independent Components**: Client-server, event-driven, peer-to-peer.
- **Virtual Machine**: Interpreter, rule-based.
- **Modern Styles**: Microservices, serverless, service-oriented architecture (SOA).

### 3. Quality Attributes & Tactics
- **Performance**: Manage event rate, prioritize tasks.
- **Modifiability**: Localize changes, prevent ripple effects.
- **Security**: Authenticate users, encrypt data, limit access.
- **Availability**: Redundancy, failover, heartbeat.
- **Testability**: Record/playback, internal interfaces.

### 4. Architecture Trade-off Analysis Method (ATAM)
- **Steps**:
  1. Present business drivers.
  2. Present architecture.
  3. Identify architectural approaches.
  4. Generate quality attribute utility tree.
  5. Analyze trade-offs.
- **Output**: Risks, non-risks, sensitivity points, trade-offs.

### 5. Architecture Documentation
- **4+1 View Model** (Kruchten):
  - Logical, Development, Process, Physical + Scenarios.
- **C4 Model**: Context, Containers, Components, Code.
- **Architecture Decision Records (ADRs)**.

## Learning Activities
- Compare microservices vs. layered architecture for an e-commerce site.
- ATAM simulation: Evaluate a given architecture for modifiability vs. performance.

## Assessment
- Architecture comparison table for a real-world system.
- Mini-ATAM report (2 pages).

## References
- Bass, L., Clements, P., Kazman, R. *Software Architecture in Practice*.
- Kruchten, P. *The 4+1 View Model of Architecture*.
