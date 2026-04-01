
# Module 3: System Modeling & Design

---

## 📌 Module Learning Objectives

By the end of this module, you should be able to:
- Understand the purpose of **system modeling** in software development
- Create and interpret **UML diagrams** (class, sequence, use case, activity)
- Apply **object-oriented design principles** (SOLID, GRASP)
- Recognize and apply common **design patterns**
- Understand the relationship between **requirements and design**

---

## 3.1 Introduction to System Modeling & Design

---

### 3.1.1 What Is System Modeling?

**System modeling** is the process of creating abstract representations of a system to understand, document, and communicate its structure and behavior before implementation.

> **🔑 Key Insight:** A model is a simplification of reality. The purpose is to manage complexity by focusing on relevant details and ignoring irrelevant ones.

#### Why Model?

| Reason | Description |
|--------|-------------|
| **Communication** | Models provide a common language between stakeholders, analysts, and developers |
| **Complexity Management** | Breaking complex systems into understandable parts |
| **Validation** | Models can be analyzed for consistency and completeness before coding |
| **Documentation** | Models serve as permanent documentation of design decisions |
| **Code Generation** | Some models can be used to generate code (MDA - Model Driven Architecture) |

---

### 3.1.2 Analysis vs. Design

Understanding the distinction between analysis and design is essential for the NSCT.

| Aspect | **Analysis** | **Design** |
|--------|--------------|------------|
| **Focus** | Understanding the problem | Creating the solution |
| **Question** | "What does the system need to do?" | "How will the system do it?" |
| **Artifacts** | Use cases, conceptual models | Class diagrams, sequence diagrams, architecture |
| **Language** | User/domain terminology | Technical terminology |
| **Output** | Requirements, analysis models | Design specifications, code structure |

> **🔑 Key Insight:** Analysis is about *understanding* the domain; design is about *constructing* the solution. The NSCT expects you to understand this progression.

---

### 3.1.3 The Role of UML

**Unified Modeling Language (UML)** is the standard notation for software modeling. It provides a set of diagram types to represent different views of a system.

#### UML Diagram Categories

| Category | Purpose | Diagrams |
|----------|---------|----------|
| **Structural** | Static structure of the system | Class, Component, Deployment, Package, Object |
| **Behavioral** | Dynamic behavior of the system | Use Case, Activity, State Machine |
| **Interaction** | Flow of interactions | Sequence, Communication, Timing, Interaction Overview |

#### For NSCT Preparation, Focus On:

| Diagram | Use |
|---------|-----|
| **Class Diagram** | Static structure: classes, attributes, methods, relationships |
| **Sequence Diagram** | Dynamic behavior: object interactions over time |
| **Use Case Diagram** | System functionality: actors and use cases |
| **Activity Diagram** | Workflow: flow of control and activities |

---

## 3.2 Use Case Diagrams

---

### 3.2.1 Purpose

Use case diagrams show the **functionality** of a system from the user's perspective. They answer: "What can users do with the system?"

---

### 3.2.2 Components

| Component | Notation | Description |
|-----------|---------|-------------|
| **Actor** | 👤 Stick figure | User or external system interacting with the system |
| **Use Case** | ⚪ Oval | Specific functionality or goal |
| **System Boundary** | 📦 Rectangle | Boundary between system and external world |
| **Association** | —— | Line between actor and use case (interaction) |
| **Include** | `<<include>>` | One use case always includes another |
| **Extend** | `<<extend>>` | One use case optionally extends another |
| **Generalization** | ——▷ | Inheritance between actors or use cases |

---

### 3.2.3 Example: Online Banking System

```
┌─────────────────────────────────────────────────────────────────────────────┐
│                           Online Banking System                             │
│                                                                             │
│                         ┌─────────────────────────────────────┐             │
│                         │                                     │             │
│                         │      ┌──────────────────┐           │             │
│                         │      │   View Balance   │           │             │
│                         │      └──────────────────┘           │             │
│                         │              ▲                      │             │
│                         │              │                      │             │
│   ┌─────────────┐       │      ┌──────┴──────┐               │             │
│   │  Customer   │───────┼─────▶│ Transfer     │               │             │
│   └─────────────┘       │      │ Funds        │               │             │
│                         │      └──────────────┘               │             │
│                         │              │                      │             │
│                         │              ▼                      │             │
│                         │      ┌──────────────────┐           │             │
│                         │      │  Authenticate    │◀──┐       │             │
│                         │      │  User           │   │       │             │
│                         │      └──────────────────┘   │       │             │
│                         │              ▲              │       │             │
│                         │              │              │       │             │
│   ┌─────────────┐       │      ┌──────┴──────┐       │       │             │
│   │  Admin      │───────┼─────▶│ Manage      │       │       │             │
│   └─────────────┘       │      │ Accounts    │       │       │             │
│                         │      └──────────────┘       │       │             │
│                         │              │              │       │             │
│                         │              ▼              │       │             │
│                         │      ┌──────────────────┐   │       │             │
│                         │      │   <<include>>    │   │       │             │
│                         │      │   Log Activity   │   │       │             │
│                         │      └──────────────────┘   │       │             │
│                         │                             │       │             │
│                         │      ┌──────────────────┐   │       │             │
│                         │      │   <<extend>>     │   │       │             │
│                         │      │   Fraud Alert    │◀──┘       │             │
│                         │      └──────────────────┘           │             │
│                         │                                     │             │
│                         └─────────────────────────────────────┘             │
│                                                                             │
└─────────────────────────────────────────────────────────────────────────────┘
```

---

### 3.2.4 Include vs. Extend

| Relationship | Meaning | Example |
|--------------|---------|---------|
| **Include** | Required behavior that is always executed as part of the base use case | "Transfer Funds" always includes "Authenticate User" |
| **Extend** | Optional behavior that may be executed under certain conditions | "Fraud Alert" extends "Transfer Funds" only if suspicious activity detected |

> **🔑 Key Insight:** Include = mandatory; Extend = optional. The NSCT often tests this distinction.

---

## 3.3 Class Diagrams

---

### 3.3.1 Purpose

Class diagrams show the **static structure** of a system: classes, attributes, methods, and relationships between classes.

---

### 3.3.2 Class Notation

```
┌─────────────────────────────────────────┐
│              Class Name                  │
├─────────────────────────────────────────┤
│  - attribute1: Type                      │
│  # attribute2: Type                      │
│  + attribute3: Type                      │
├─────────────────────────────────────────┤
│  + method1(): ReturnType                 │
│  - method2(param: Type): ReturnType      │
│  # method3(): void                       │
└─────────────────────────────────────────┘
```

#### Visibility Symbols

| Symbol | Visibility | Meaning |
|--------|------------|---------|
| `+` | Public | Accessible to any class |
| `-` | Private | Accessible only within the class |
| `#` | Protected | Accessible to subclasses and same package |
| `~` | Package | Accessible within the same package |

---

### 3.3.3 Relationships

The NSCT expects you to understand the different types of relationships between classes.

---

#### Association

**Definition:** A structural relationship indicating that objects of one class are connected to objects of another.

**Notation:** Solid line (——)

```
┌─────────────┐                    ┌─────────────┐
│   Customer  │                    │   Account   │
├─────────────┤                    ├─────────────┤
│ - name      │                    │ - accountNo │
│ - email     │                    │ - balance   │
└─────────────┘                    └─────────────┘
       │                                    ▲
       │                                    │
       └────────────────────────────────────┘
                    (1 owns 0..*)
```

**Multiplicity:**

| Notation | Meaning |
|----------|---------|
| `1` | Exactly one |
| `0..1` | Zero or one |
| `0..*` or `*` | Zero or more |
| `1..*` | One or more |
| `n..m` | Between n and m |

---

#### Aggregation (Weak "Has-A")

**Definition:** A "whole-part" relationship where parts can exist independently of the whole.

**Notation:** Hollow diamond on the whole side (◇——)

```
┌─────────────┐ ◇───────────────────┐
│  University │                     │  Department
├─────────────┤                     ├─────────────┤
│ - name      │                     │ - name      │
└─────────────┘                     └─────────────┘

A University has Departments.
Departments can exist without the University (if University closes, Departments continue).
```

---

#### Composition (Strong "Has-A")

**Definition:** A "whole-part" relationship where parts cannot exist independently of the whole. Parts are destroyed when the whole is destroyed.

**Notation:** Filled diamond on the whole side (◆——)

```
┌─────────────┐ ◆───────────────────┐
│   House     │                     │   Room
├─────────────┤                     ├─────────────┤
│ - address   │                     │ - name      │
└─────────────┘                     │ - size      │
                                    └─────────────┘

A House has Rooms.
Rooms cannot exist without the House.
```

---

#### Inheritance (Generalization)

**Definition:** An "is-a" relationship where a subclass inherits from a superclass.

**Notation:** Hollow triangle arrow (——▷)

```
                    ┌─────────────┐
                    │  Employee   │
                    ├─────────────┤
                    │ - id        │
                    │ - name      │
                    │ + work()    │
                    └─────────────┘
                           ▲
                           │
           ┌───────────────┼───────────────┐
           │               │               │
┌──────────┴───┐   ┌───────┴──────┐   ┌────┴─────────┐
│  Developer   │   │  Manager     │   │  Designer    │
├──────────────┤   ├──────────────┤   ├──────────────┤
│ + writeCode()│   │ + manageTeam()│   │ + createDesign()│
└──────────────┘   └──────────────┘   └──────────────┘

Developer, Manager, and Designer are types of Employee.
```

---

#### Dependency

**Definition:** A temporary relationship where one class uses another (e.g., as a method parameter or local variable).

**Notation:** Dashed arrow (----▶)

```
┌─────────────┐                    ┌─────────────┐
│   Order     │ ─ ─ ─ ─ ─ ─ ─ ─ ▶ │   Payment   │
├─────────────┤                    ├─────────────┤
│ + process() │                    │ + charge()  │
└─────────────┘                    └─────────────┘

Order depends on Payment (uses it temporarily), but doesn't own it.
```

---

### 3.3.4 Relationship Summary

| Relationship | Notation | Type | Example |
|--------------|----------|------|---------|
| **Association** | —— | "Uses" | Customer —— Account |
| **Aggregation** | ◇—— | Weak "has-a" | University ◇—— Department |
| **Composition** | ◆—— | Strong "has-a" | House ◆—— Room |
| **Inheritance** | ——▷ | "Is-a" | Car ——▷ Vehicle |
| **Dependency** | ----▶ | Temporary use | Order ----▶ Payment |

---

### 3.3.5 Example: Complete Class Diagram

```
┌─────────────────────────────┐         ┌─────────────────────────────┐
│         Customer            │         │           Order             │
├─────────────────────────────┤         ├─────────────────────────────┤
│ - id: int                   │         │ - orderId: int              │
│ - name: String              │         │ - orderDate: Date           │
│ - email: String             │         │ - status: OrderStatus       │
├─────────────────────────────┤         ├─────────────────────────────┤
│ + placeOrder(): Order       │1       *│ + addItem(product): void   │
│ + viewOrders(): List<Order> │────────▶│ + calculateTotal(): double │
│ + updateProfile(): void     │         │ + submit(): void            │
└─────────────────────────────┘         └─────────────────────────────┘
                                                │
                                                │ ◆ (composition)
                                                │
                                                ▼
┌─────────────────────────────┐         ┌─────────────────────────────┐
│          Product            │         │        OrderItem            │
├─────────────────────────────┤         ├─────────────────────────────┤
│ - productId: int            │         │ - quantity: int             │
│ - name: String              │         │ - unitPrice: double         │
│ - price: double             │         ├─────────────────────────────┤
│ - stock: int                │         │ + getSubtotal(): double     │
├─────────────────────────────┤         └─────────────────────────────┘
│ + updateStock(qty): void    │               * │
│ + isAvailable(): boolean    │                 │
└─────────────────────────────┘                 │
         ▲                                      │
         │                                      │
         └──────────────────────────────────────┘
                    (association)

┌─────────────────────────────┐
│      Payment (abstract)     │
├─────────────────────────────┤
│ - amount: double            │
│ - date: Date                │
├─────────────────────────────┤
│ + process(): boolean        │
└─────────────────────────────┘
         ▲
         │
    ┌────┴────┐
    │         │
┌───┴───┐ ┌───┴───┐
│ Credit│ │ PayPal│
│ Card  │ │       │
└───────┘ └───────┘
```

---

## 3.4 Sequence Diagrams

---

### 3.4.1 Purpose

Sequence diagrams show **interactions over time** between objects. They answer: "How do objects collaborate to accomplish a task?"

---

### 3.4.2 Components

| Component | Notation | Description |
|-----------|----------|-------------|
| **Lifeline** | `[object]: Class` | Vertical line representing an object's existence |
| **Activation Bar** | ████ | Rectangle on lifeline showing when object is active |
| **Message** | ——▶ | Arrow from sender to receiver showing communication |
| **Return** | ----▶ | Dashed arrow showing return value |
| **Alternative** | `alt` | Conditional flow (if-else) |
| **Loop** | `loop` | Repetitive flow |
| **Creation** | ----▶ `new` | Object creation |
| **Destruction** | ❌ | Object destruction |

---

### 3.4.3 Example: Place Order Sequence

```
Customer          :OrderController    :OrderService      :Inventory         :PaymentService
    │                    │                  │                 │                    │
    │ placeOrder(items)  │                  │                 │                    │
    │───────────────────▶│                  │                 │                    │
    │                    │                  │                 │                    │
    │                    │ createOrder()    │                 │                    │
    │                    │─────────────────▶│                 │                    │
    │                    │                  │                 │                    │
    │                    │                  │ checkStock()    │                    │
    │                    │                  │────────────────▶│                    │
    │                    │                  │                 │                    │
    │                    │                  │ stockAvailable  │                    │
    │                    │                  │◀────────────────│                    │
    │                    │                  │                 │                    │
    │                    │                  │                 │                    │
    │                    │                  │ reserveStock()  │                    │
    │                    │                  │────────────────▶│                    │
    │                    │                  │                 │                    │
    │                    │                  │                 │                    │
    │                    │                  │ processPayment(amount)             │
    │                    │                  │────────────────────────────────────▶│
    │                    │                  │                 │                    │
    │                    │                  │                 │ paymentConfirmed  │
    │                    │                  │◀────────────────────────────────────│
    │                    │                  │                 │                    │
    │                    │ orderConfirmed   │                 │                    │
    │                    │◀─────────────────│                 │                    │
    │                    │                  │                 │                    │
    │ confirmation       │                  │                 │                    │
    │◀───────────────────│                  │                 │                    │
    │                    │                  │                 │                    │
```

---

### 3.4.4 Combined Fragments

| Fragment | Symbol | Meaning |
|----------|--------|---------|
| **Alternative** | `alt` | If-else; multiple conditional paths |
| **Option** | `opt` | Optional execution (if condition true) |
| **Loop** | `loop` | Repeat while condition true |
| **Parallel** | `par` | Concurrent execution |
| **Critical** | `critical` | Atomic execution (no interleaving) |

**Example with Combined Fragments:**

```
:User          :System          :Database
  │                │                │
  │   login()      │                │
  │───────────────▶│                │
  │                │                │
  │                │  authenticate()│
  │                │───────────────▶│
  │                │                │
  │                │                │
  │                │    result      │
  │                │◀───────────────│
  │                │                │
  │                │                │
  ┌──────────────────────────────────┐
  │ alt [valid credentials]          │
  │   │                │                │
  │   │  success       │                │
  │   │◀───────────────│                │
  │   │                │                │
  └──────────────────────────────────┘
  ┌──────────────────────────────────┐
  │ else [invalid credentials]       │
  │   │                │                │
  │   │  error         │                │
  │   │◀───────────────│                │
  │   │                │                │
  └──────────────────────────────────┘
```

---

## 3.5 Activity Diagrams

---

### 3.5.1 Purpose

Activity diagrams model **workflows** and **process flows**. They answer: "What happens step-by-step?"

---

### 3.5.2 Components

| Component | Notation | Description |
|-----------|----------|-------------|
| **Start Node** | ● | Beginning of flow |
| **Activity** | (rounded rectangle) | Action or step |
| **Decision** | ◇ | Branch (if-else) |
| **Merge** | ◇ | Combine branches |
| **Fork** | ———▷ | Parallel split |
| **Join** | ◁——— | Parallel merge |
| **End Node** | ◉ | End of flow |
| **Swimlane** | Columns | Partition by actor/role |

---

### 3.5.3 Example: Order Processing Workflow

```
┌─────────────────────────────────────────────────────────────────────────────┐
│                              Order Processing                               │
├─────────────────────────────────────────────────────────────────────────────┤
│                                                                             │
│     Customer           │      System        │    Warehouse    │   Payment   │
│                        │                    │                 │             │
│  ┌──────────┐          │                    │                 │             │
│  │ Place    │          │                    │                 │             │
│  │ Order    │          │                    │                 │             │
│  └────┬─────┘          │                    │                 │             │
│       │                │                    │                 │             │
│       ▼                │                    │                 │             │
│  ┌──────────┐          │                    │                 │             │
│  │ Enter    │          │                    │                 │             │
│  │ Details  │          │                    │                 │             │
│  └────┬─────┘          │                    │                 │             │
│       │                │                    │                 │             │
│       ▼                │                    │                 │             │
│       └────────────────┼────────────────────┼─────────────────┘             │
│                        ▼                    │                 │             │
│                   ┌──────────┐              │                 │             │
│                   │ Validate │              │                 │             │
│                   │ Order    │              │                 │             │
│                   └────┬─────┘              │                 │             │
│                        │                    │                 │             │
│                        ▼                    │                 │             │
│                     ┌──┴──┐                 │                 │             │
│                     │ ◇   │                 │                 │             │
│                     └──┬──┘                 │                 │             │
│                ┌───────┴───────┐            │                 │             │
│                │               │            │                 │             │
│            [Valid]          [Invalid]       │                 │             │
│                │               │            │                 │             │
│                ▼               ▼            │                 │             │
│           ┌──────────┐    ┌──────────┐     │                 │             │
│           │ Process  │    │ Show     │     │                 │             │
│           │ Payment  │    │ Error    │     │                 │             │
│           └────┬─────┘    └────┬─────┘     │                 │             │
│                │               │           │                 │             │
│                ▼               │           │                 │             │
│           ┌──────────┐         │           │                 │             │
│           │ Authorize│         │           │                 │             │
│           │ Payment  │         │           │                 │             │
│           └────┬─────┘         │           │                 │             │
│                │               │           │                 │             │
│             ┌──┴──┐            │           │                 │             │
│             │ ◇   │            │           │                 │             │
│             └──┬──┘            │           │                 │             │
│        ┌───────┴───────┐       │           │                 │             │
│        │               │       │           │                 │             │
│    [Approved]      [Declined]  │           │                 │             │
│        │               │       │           │                 │             │
│        ▼               ▼       │           │                 │             │
│   ┌──────────┐    ┌──────────┐│           │                 │             │
│   │  Notify  │    │  Notify  ││           │                 │             │
│   │  Success │    │  Failure ││           │                 │             │
│   └────┬─────┘    └────┬─────┘│           │                 │             │
│        │               │      │           │                 │             │
│        └───────────────┼──────┘           │                 │             │
│                        │                  │                 │             │
│                        ▼                  │                 │             │
│                   ┌──────────┐            │                 │             │
│                   │  Update  │            │                 │             │
│                   │  Order   │            │                 │             │
│                   │  Status  │            │                 │             │
│                   └────┬─────┘            │                 │             │
│                        │                  │                 │             │
│                        ▼                  │                 │             │
│                   ┌──────────┐            │                 │             │
│                   │  Notify  │            │                 │             │
│                   │  User    │            │                 │             │
│                   └────┬─────┘            │                 │             │
│                        │                  │                 │             │
│                        ▼                  ▼                 │             │
│                        └──────────────────┼─────────────────┘             │
│                                           │                               │
│                                           ▼                               │
│                                      ┌──────────┐                         │
│                                      │  Ship    │                         │
│                                      │  Order   │                         │
│                                      └──────────┘                         │
│                                                                           │
└───────────────────────────────────────────────────────────────────────────┘
```

---

## 3.6 SOLID Design Principles

---

### 3.6.1 Overview

SOLID is an acronym for five design principles that make software more maintainable, understandable, and flexible. The NSCT expects you to understand these principles.

| Principle | Full Name | Core Idea |
|-----------|-----------|-----------|
| **S** | Single Responsibility | One class, one reason to change |
| **O** | Open/Closed | Open for extension, closed for modification |
| **L** | Liskov Substitution | Subtypes must be substitutable for base types |
| **I** | Interface Segregation | Many specific interfaces over one general interface |
| **D** | Dependency Inversion | Depend on abstractions, not concretions |

---

### 3.6.2 S: Single Responsibility Principle (SRP)

> **"A class should have only one reason to change."**

**Violation Example:**
```java
// Bad: This class has multiple responsibilities
public class Employee {
    // Responsibility 1: Employee data management
    private String name;
    private double salary;
    
    // Responsibility 2: Payroll calculation
    public double calculatePay() { ... }
    
    // Responsibility 3: Database persistence
    public void saveToDatabase() { ... }
    
    // Responsibility 4: Report generation
    public String generateReport() { ... }
}
```

**Corrected Example:**
```java
// Good: Each class has a single responsibility
public class Employee {
    private String name;
    private double salary;
    // Only employee data
}

public class PayrollCalculator {
    public double calculatePay(Employee e) { ... }
}

public class EmployeeRepository {
    public void save(Employee e) { ... }
}

public class EmployeeReportGenerator {
    public String generate(Employee e) { ... }
}
```

> **🔑 Key Insight:** When a class has multiple responsibilities, changes to one responsibility may break others. Separation makes code more maintainable.

---

### 3.6.3 O: Open/Closed Principle (OCP)

> **"Software entities should be open for extension but closed for modification."**

**Violation Example:**
```java
// Bad: Adding a new shape requires modifying this class
public class AreaCalculator {
    public double calculateArea(Object shape) {
        if (shape instanceof Rectangle) {
            Rectangle r = (Rectangle) shape;
            return r.width * r.height;
        } else if (shape instanceof Circle) {
            Circle c = (Circle) shape;
            return Math.PI * c.radius * c.radius;
        }
        // Adding Triangle requires modifying this method!
        return 0;
    }
}
```

**Corrected Example:**
```java
// Good: Open for extension via polymorphism
public interface Shape {
    double calculateArea();
}

public class Rectangle implements Shape {
    private double width;
    private double height;
    
    public double calculateArea() {
        return width * height;
    }
}

public class Circle implements Shape {
    private double radius;
    
    public double calculateArea() {
        return Math.PI * radius * radius;
    }
}

public class AreaCalculator {
    public double calculateArea(Shape shape) {
        return shape.calculateArea();  // No modification needed for new shapes
    }
}
```

> **🔑 Key Insight:** New functionality should be added by creating new classes, not by modifying existing ones.

---

### 3.6.4 L: Liskov Substitution Principle (LSP)

> **"Objects of a superclass should be replaceable with objects of a subclass without affecting correctness."**

**Violation Example:**
```java
// Bad: Square breaks Rectangle behavior
public class Rectangle {
    protected double width;
    protected double height;
    
    public void setWidth(double w) { this.width = w; }
    public void setHeight(double h) { this.height = h; }
    public double getArea() { return width * height; }
}

public class Square extends Rectangle {
    @Override
    public void setWidth(double w) {
        super.setWidth(w);
        super.setHeight(w);  // Violates expectation!
    }
    
    @Override
    public void setHeight(double h) {
        super.setWidth(h);
        super.setHeight(h);  // Violates expectation!
    }
}

// This test fails with Square
public void testArea(Rectangle r) {
    r.setWidth(5);
    r.setHeight(4);
    assert r.getArea() == 20;  // With Square, area becomes 16!
}
```

**Corrected Example:**
```java
// Good: Separate abstractions
public interface Shape {
    double getArea();
}

public class Rectangle implements Shape {
    private double width;
    private double height;
    
    public void setWidth(double w) { this.width = w; }
    public void setHeight(double h) { this.height = h; }
    public double getArea() { return width * height; }
}

public class Square implements Shape {
    private double side;
    
    public void setSide(double s) { this.side = s; }
    public double getArea() { return side * side; }
}
```

> **🔑 Key Insight:** Subtypes must honor the contract of their supertypes. If a subclass changes behavior in unexpected ways, it violates LSP.

---

### 3.6.5 I: Interface Segregation Principle (ISP)

> **"Clients should not be forced to depend on interfaces they do not use."**

**Violation Example:**
```java
// Bad: Fat interface
public interface Worker {
    void work();
    void eat();
    void sleep();
    void attendMeeting();
}

public class Robot implements Worker {
    public void work() { ... }      // OK
    public void eat() { /* Not needed! */ }  // Forced to implement
    public void sleep() { /* Not needed! */ } // Forced to implement
    public void attendMeeting() { ... }       // OK
}
```

**Corrected Example:**
```java
// Good: Segregated interfaces
public interface Workable {
    void work();
}

public interface Eatable {
    void eat();
}

public interface Sleepable {
    void sleep();
}

public interface MeetingAttendable {
    void attendMeeting();
}

public class Human implements Workable, Eatable, Sleepable, MeetingAttendable {
    public void work() { ... }
    public void eat() { ... }
    public void sleep() { ... }
    public void attendMeeting() { ... }
}

public class Robot implements Workable, MeetingAttendable {
    public void work() { ... }
    public void attendMeeting() { ... }
    // No need to implement eat() or sleep()
}
```

> **🔑 Key Insight:** Smaller, focused interfaces are better than large, general ones. This prevents clients from depending on methods they don't need.

---

### 3.6.6 D: Dependency Inversion Principle (DIP)

> **"High-level modules should not depend on low-level modules. Both should depend on abstractions."**

**Violation Example:**
```java
// Bad: High-level module depends directly on low-level module
public class EmailService {
    public void sendEmail(String to, String message) { ... }
}

public class NotificationService {
    private EmailService emailService = new EmailService();  // Direct dependency
    
    public void notify(String user, String message) {
        emailService.sendEmail(user, message);
    }
}
```

**Corrected Example:**
```java
// Good: Both depend on abstraction
public interface MessageSender {
    void send(String to, String message);
}

public class EmailService implements MessageSender {
    public void send(String to, String message) { ... }
}

public class SMSService implements MessageSender {
    public void send(String to, String message) { ... }
}

public class NotificationService {
    private MessageSender messageSender;  // Depends on abstraction
    
    public NotificationService(MessageSender sender) {
        this.messageSender = sender;  // Dependency injection
    }
    
    public void notify(String user, String message) {
        messageSender.send(user, message);
    }
}

// Usage
NotificationService emailNotifier = new NotificationService(new EmailService());
NotificationService smsNotifier = new NotificationService(new SMSService());
```

> **🔑 Key Insight:** Depend on interfaces/abstract classes, not concrete implementations. This makes code more flexible and testable.

---

## 3.7 GRASP Principles

---

### 3.7.1 Overview

**GRASP (General Responsibility Assignment Software Patterns)** are principles for assigning responsibilities to classes in object-oriented design.

| Principle | Core Idea |
|-----------|-----------|
| **Information Expert** | Assign responsibility to the class that has the information needed |
| **Creator** | Assign creation responsibility to the class that contains or uses the object |
| **Controller** | Assign responsibility for handling system events to a controller class |
| **Low Coupling** | Minimize dependencies between classes |
| **High Cohesion** | Keep classes focused and responsibilities related |
| **Polymorphism** | Use polymorphism for behavior variations |
| **Pure Fabrication** | Create artificial classes when needed to maintain low coupling/high cohesion |
| **Indirection** | Use intermediary classes to reduce coupling |
| **Protected Variations** | Identify points of predicted variation and create stable interfaces |

---

### 3.7.2 Information Expert

> **Assign responsibility to the class that has the information needed to fulfill it.**

**Example:**
```java
// ShoppingCart should calculate total because it knows its items
public class ShoppingCart {
    private List<Item> items;
    
    // Information Expert: Cart has the items, so it calculates total
    public double calculateTotal() {
        return items.stream()
            .mapToDouble(item -> item.getPrice() * item.getQuantity())
            .sum();
    }
}
```

---

### 3.7.3 Low Coupling & High Cohesion

| Principle | Description |
|-----------|-------------|
| **Low Coupling** | Classes should have minimal dependencies on other classes |
| **High Cohesion** | Classes should have focused, related responsibilities |

**Good Design:**
```
┌─────────────┐     ┌─────────────┐     ┌─────────────┐
│   Order     │────▶│  Customer   │     │  Payment    │
└─────────────┘     └─────────────┘     └─────────────┘
      │
      │
      ▼
┌─────────────┐
│  OrderItem  │
└─────────────┘

Each class has clear purpose; dependencies are minimal.
```

**Bad Design (High Coupling, Low Cohesion):**
```
┌─────────────┐
│   Utils     │ (Everything in one class)
└─────────────┘
      │
      ├────▶ Everything depends on Utils
      ├────▶ Low cohesion (unrelated responsibilities)
      └────▶ Changes to Utils affect everything
```

---

## 3.8 Design Patterns

---

### 3.8.1 Overview

**Design patterns** are reusable solutions to common design problems. The NSCT expects you to recognize common patterns.

| Category | Purpose | Examples |
|----------|---------|----------|
| **Creational** | Object creation | Singleton, Factory, Builder, Prototype |
| **Structural** | Class/object composition | Adapter, Decorator, Facade, Proxy |
| **Behavioral** | Object interaction | Observer, Strategy, Command, Template |

---

### 3.8.2 Singleton Pattern

**Purpose:** Ensure a class has only one instance and provide global access to it.

**Structure:**
```
┌─────────────────────────┐
│      Singleton          │
├─────────────────────────┤
│ - instance: Singleton   │
├─────────────────────────┤
│ - Singleton()           │
│ + getInstance(): Singleton│
└─────────────────────────┘
```

**Example:**
```java
public class DatabaseConnection {
    private static DatabaseConnection instance;
    
    private DatabaseConnection() { }  // Private constructor
    
    public static DatabaseConnection getInstance() {
        if (instance == null) {
            instance = new DatabaseConnection();
        }
        return instance;
    }
    
    public void connect() { ... }
}
```

**When to Use:** Configuration managers, connection pools, logging, caching.

---

### 3.8.3 Factory Pattern

**Purpose:** Create objects without specifying the exact class.

**Structure:**
```
┌─────────────────────────┐         ┌─────────────────────────┐
│      Creator            │         │       Product           │
├─────────────────────────┤         ├─────────────────────────┤
│ + factoryMethod(): Product│───────▶│ + operation(): void    │
└─────────────────────────┘         └─────────────────────────┘
         ▲                                      ▲
         │                                      │
┌────────┴────────┐                   ┌─────────┴─────────┐
│ ConcreteCreator │                   │ ConcreteProduct  │
└─────────────────┘                   └───────────────────┘
```

**Example:**
```java
// Product interface
public interface Payment {
    void pay(double amount);
}

// Concrete products
public class CreditCardPayment implements Payment {
    public void pay(double amount) { ... }
}

public class PayPalPayment implements Payment {
    public void pay(double amount) { ... }
}

// Factory
public class PaymentFactory {
    public static Payment createPayment(String type) {
        switch (type) {
            case "credit": return new CreditCardPayment();
            case "paypal": return new PayPalPayment();
            default: throw new IllegalArgumentException();
        }
    }
}
```

---

### 3.8.4 Observer Pattern

**Purpose:** Define a one-to-many dependency where when one object changes state, all dependents are notified.

**Structure:**
```
┌─────────────────────────┐         ┌─────────────────────────┐
│      Subject            │         │      Observer           │
├─────────────────────────┤         ├─────────────────────────┤
│ + attach(Observer)      │         │ + update()              │
│ + detach(Observer)      │         └─────────────────────────┘
│ + notify()              │                  ▲
└─────────────────────────┘                  │
         ▲                                   │
         │                                   │
┌────────┴────────┐                ┌─────────┴─────────┐
│ ConcreteSubject │                │ ConcreteObserver  │
└─────────────────┘                └───────────────────┘
```

**Example:**
```java
// Observer interface
public interface OrderObserver {
    void update(Order order);
}

// Subject
public class Order {
    private List<OrderObserver> observers = new ArrayList<>();
    private String status;
    
    public void attach(OrderObserver observer) {
        observers.add(observer);
    }
    
    public void setStatus(String status) {
        this.status = status;
        notifyObservers();
    }
    
    private void notifyObservers() {
        for (OrderObserver observer : observers) {
            observer.update(this);
        }
    }
}

// Concrete observer
public class EmailNotifier implements OrderObserver {
    public void update(Order order) {
        System.out.println("Order status changed to: " + order.getStatus());
        // Send email...
    }
}
```

---

### 3.8.5 Strategy Pattern

**Purpose:** Define a family of algorithms, encapsulate each one, and make them interchangeable.

**Structure:**
```
┌─────────────────────────┐         ┌─────────────────────────┐
│      Context            │         │      Strategy           │
├─────────────────────────┤         ├─────────────────────────┤
│ - strategy: Strategy    │────────▶│ + execute()             │
│ + executeStrategy()     │         └─────────────────────────┘
└─────────────────────────┘                  ▲
                                             │
                              ┌──────────────┼──────────────┐
                              │              │              │
                    ┌─────────┴─────┐ ┌──────┴──────┐ ┌─────┴────────┐
                    │ ConcreteStrategyA│ │ConcreteStrategyB│ │ConcreteStrategyC│
                    └─────────────────┘ └───────────────┘ └────────────────┘
```

**Example:**
```java
// Strategy interface
public interface SortStrategy {
    void sort(int[] data);
}

// Concrete strategies
public class BubbleSort implements SortStrategy {
    public void sort(int[] data) { /* Bubble sort implementation */ }
}

public class QuickSort implements SortStrategy {
    public void sort(int[] data) { /* Quick sort implementation */ }
}

// Context
public class Sorter {
    private SortStrategy strategy;
    
    public Sorter(SortStrategy strategy) {
        this.strategy = strategy;
    }
    
    public void setStrategy(SortStrategy strategy) {
        this.strategy = strategy;
    }
    
    public void sort(int[] data) {
        strategy.sort(data);
    }
}

// Usage
Sorter sorter = new Sorter(new QuickSort());
sorter.sort(data);  // Uses QuickSort
sorter.setStrategy(new BubbleSort());
sorter.sort(data);  // Uses BubbleSort
```

---

## 💡 Study Activity: Deep Dive

---

### Activity 1: UML Diagram Creation

Create the following diagrams for a **Library Management System**:

1. **Use Case Diagram** with actors: Librarian, Member. Use cases: Borrow Book, Return Book, Search Catalog, Manage Members (Librarian only)

2. **Class Diagram** with classes: Book, Member, Loan, Library. Show relationships.

3. **Sequence Diagram** for "Borrow Book" use case showing Member → Library System → Loan → Book interactions

<details>
<summary>Click for solutions</summary>

**Use Case Diagram:**
```
┌─────────────────────────────────────────────────────────┐
│                    Library System                       │
│                                                         │
│   ┌─────────┐       ┌──────────────┐                   │
│   │ Member  │──────▶│ Search Catalog│                   │
│   └─────────┘       └──────────────┘                   │
│        │                     ▲                         │
│        │                     │                         │
│        │              ┌──────┴──────┐                  │
│        │              │             │                  │
│        ▼              ▼             │                  │
│   ┌─────────┐    ┌──────────────┐   │                  │
│   │ Borrow  │    │ Return Book  │   │                  │
│   │ Book    │    └──────────────┘   │                  │
│   └─────────┘                       │                  │
│        │                            │                  │
│        └──────────────┬─────────────┘                  │
│                       │                                │
│   ┌─────────┐         │                                │
│   │Librarian│─────────┼────────────────────────────────┤
│   └─────────┘         │                                │
│                       ▼                                │
│                ┌──────────────┐                        │
│                │ Manage       │                        │
│                │ Members      │                        │
│                └──────────────┘                        │
└─────────────────────────────────────────────────────────┘
```

**Class Diagram:**
```
┌─────────────────────┐     ┌─────────────────────┐
│        Book         │     │       Member        │
├─────────────────────┤     ├─────────────────────┤
│ - isbn: String      │     │ - memberId: String  │
│ - title: String     │     │ - name: String      │
│ - author: String    │     │ - email: String     │
│ - isAvailable: bool │     └─────────────────────┘
├─────────────────────┤              ▲
│ + borrow()          │              │
│ + return()          │              │
└─────────────────────┘              │
         │                           │
         │                           │
         ▼                           │
┌─────────────────────┐              │
│        Loan         │              │
├─────────────────────┤              │
│ - loanId: String    │              │
│ - borrowDate: Date  │              │
│ - dueDate: Date     │              │
├─────────────────────┤              │
│ + calculateFine()   │              │
└─────────────────────┘              │
         │                           │
         │                           │
         └───────────────────────────┘
```

</details>

---

### Activity 2: SOLID Identification

For each scenario, identify which SOLID principle is violated and explain why:

1. A `UserManager` class handles user authentication, email notifications, database operations, and audit logging.

<details>
<summary>Click for answer</summary>
<strong>Single Responsibility Principle (SRP) violation.</strong> The class has multiple reasons to change: authentication rules, email format, database schema, audit requirements.
</details>

2. To add a new payment method (Bitcoin), developers must modify the existing `PaymentProcessor` class and add a new `if` statement.

<details>
<summary>Click for answer</summary>
<strong>Open/Closed Principle (OCP) violation.</strong> The class should be open for extension (new payment methods) but closed for modification.
</details>

3. A `Bird` class has a `fly()` method. A `Penguin` class extends `Bird` but `fly()` throws an exception because penguins can't fly.

<details>
<summary>Click for answer</summary>
<strong>Liskov Substitution Principle (LSP) violation.</strong> A `Penguin` cannot substitute for a `Bird` without changing program behavior.
</details>

4. An `Animal` interface has methods `eat()`, `sleep()`, and `fly()`. A `Dog` class implements `Animal` but `fly()` is empty.

<details>
<summary>Click for answer</summary>
<strong>Interface Segregation Principle (ISP) violation.</strong> The `Animal` interface is too broad; `Dog` is forced to implement methods it doesn't need.
</details>

5. A `ReportGenerator` class directly instantiates a `DatabaseConnection` class, making testing difficult.

<details>
<summary>Click for answer</summary>
<strong>Dependency Inversion Principle (DIP) violation.</strong> High-level `ReportGenerator` depends on low-level `DatabaseConnection` rather than an abstraction.
</details>

---

### Activity 3: Design Pattern Matching

Match each scenario to the appropriate design pattern:

| Scenario | Pattern |
|----------|---------|
| Only one database connection should exist | |
| Creating different types of documents (PDF, Word, HTML) | |
| Notify all subscribers when news is published | |
| Different sorting algorithms interchangeable at runtime | |
| Add logging functionality without modifying existing classes | |

<details>
<summary>Click for answer</summary>
| Scenario | Pattern |
|----------|---------|
| Only one database connection should exist | **Singleton** |
| Creating different types of documents (PDF, Word, HTML) | **Factory** |
| Notify all subscribers when news is published | **Observer** |
| Different sorting algorithms interchangeable at runtime | **Strategy** |
| Add logging functionality without modifying existing classes | **Decorator** |
</details>

---

## 📝 Module 3 Self-Assessment Quiz

1. What is the difference between analysis and design?

   <details>
   <summary>Click for answer</summary>
   Analysis focuses on understanding the problem ("what"); design focuses on creating the solution ("how").
   </details>

2. What are the four main UML diagrams covered in this module?

   <details>
   <summary>Click for answer</summary>
   Use Case Diagram, Class Diagram, Sequence Diagram, Activity Diagram.
   </details>

3. What is the difference between `<<include>>` and `<<extend>>` in use case diagrams?

   <details>
   <summary>Click for answer</summary>
   Include = mandatory behavior always executed; Extend = optional behavior executed only under certain conditions.
   </details>

4. What is the difference between aggregation and composition?

   <details>
   <summary>Click for answer</summary>
   Aggregation is a weak "has-a" where parts can exist independently; composition is a strong "has-a" where parts cannot exist without the whole.
   </details>

5. What does the Liskov Substitution Principle (LSP) state?

   <details>
   <summary>Click for answer</summary>
   Objects of a superclass should be replaceable with objects of a subclass without affecting program correctness.
   </details>

6. What is the purpose of the Dependency Inversion Principle (DIP)?

   <details>
   <summary>Click for answer</summary>
   High-level modules should not depend on low-level modules; both should depend on abstractions.
   </details>

7. What design pattern ensures a class has only one instance?

   <details>
   <summary>Click for answer</summary>
   Singleton Pattern.
   </details>

8. What design pattern defines a family of interchangeable algorithms?

   <details>
   <summary>Click for answer</summary>
   Strategy Pattern.
   </details>

9. What does the Information Expert principle state?

   <details>
   <summary>Click for answer</summary>
   Assign responsibility to the class that has the information needed to fulfill it.
   </details>

10. What is the difference between low coupling and high cohesion?

    <details>
    <summary>Click for answer</summary>
    Low coupling means minimal dependencies between classes; high cohesion means classes have focused, related responsibilities.
    </details>

---

## 🔗 Connections to Other Modules

| Concept from Module 3 | Connects to |
|-----------------------|-------------|
| Use case diagrams | Module 2: Requirements (use cases) |
| Class diagrams | Module 4: Implementation (code structure) |
| Sequence diagrams | Module 4: Implementation (object interactions) |
| SOLID principles | Module 4: Implementation (code quality) |
| Design patterns | Module 4: Implementation (reusable solutions) |
| High cohesion/low coupling | Module 4: Architecture (component design) |

---

## ✅ Module 3 Summary

| Section | Key Takeaways |
|---------|---------------|
| **3.1 Introduction** | Models manage complexity; analysis (what) vs. design (how); UML standard notation |
| **3.2 Use Case Diagrams** | Actors and use cases; include (mandatory) vs. extend (optional) |
| **3.3 Class Diagrams** | Classes, attributes, methods; relationships: association, aggregation, composition, inheritance |
| **3.4 Sequence Diagrams** | Object interactions over time; lifelines, messages, combined fragments |
| **3.5 Activity Diagrams** | Workflow modeling; decisions, forks, joins, swimlanes |
| **3.6 SOLID Principles** | SRP, OCP, LSP, ISP, DIP—foundational design principles |
| **3.7 GRASP Principles** | Responsibility assignment: Information Expert, Low Coupling, High Cohesion |
| **3.8 Design Patterns** | Singleton, Factory, Observer, Strategy—reusable solutions |

---

# Module 4: Software Architecture & Implementation

---

## 📌 Module Learning Objectives

By the end of this module, you should be able to:
- Understand the **role of software architecture** in the development lifecycle
- Describe and compare **architectural styles** (MVC, layered, microservices, etc.)
- Apply **design patterns** to solve recurring problems
- Understand **implementation best practices** (clean code, documentation, version control)
- Explain **modern development practices** (DevOps, CI/CD, containerization)
- Understand **code quality metrics** and **technical debt**

---

