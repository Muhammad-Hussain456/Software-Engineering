# Software Architecture

## 5.1 Introduction to Software Architecture

---

### 5.1.1 What Is Software Architecture?

**Software architecture** is the fundamental organization of a system, embodied in its components, their relationships to each other and to the environment, and the principles guiding its design and evolution.

> **🔑 Key Insight:** Architecture is the "blueprint" of the system—the high-level structure that makes the system understandable, manageable, and adaptable.

#### Architecture vs. Design

| Aspect | **Architecture** | **Design** |
|--------|------------------|------------|
| **Scope** | High-level, system-wide | Component-level, detailed |
| **Focus** | Structure, relationships, constraints | Implementation, algorithms, data structures |
| **Decisions** | Technology stack, deployment, component boundaries | Class structures, method implementations, patterns |
| **Change Impact** | Broad, affects many components | Localized to specific components |
| **Audience** | Stakeholders, developers, operations | Developers, testers |

---

### 5.1.2 Why Architecture Matters

| Reason | Description |
|--------|-------------|
| **Manages Complexity** | Divides system into understandable parts with clear boundaries |
| **Enables Quality Attributes** | Performance, security, scalability, maintainability are determined by architecture |
| **Supports Communication** | Common vocabulary for stakeholders, developers, and operations |
| **Facilitates Evolution** | Well-architected systems can adapt to changing requirements |
| **Reduces Risk** | Architecture decisions affect project success more than any other factor |

---

### 5.1.3 Architecture vs. Design: The Decision Continuum

Understanding the distinction between architecture and design is critical for the NSCT.

```
┌─────────────────────────────────────────────────────────────────────────────┐
│                         Decision Continuum                                  │
│                                                                             │
│   High-Level (Architecture)          Mid-Level          Low-Level (Design)  │
│   ─────────────────────────          ─────────          ─────────────────   │
│                                                                             │
│   • Technology stack                • Component         • Class design      │
│   • Deployment model                  interfaces        • Method design     │
│   • Component boundaries            • Design patterns   • Algorithm choice  │
│   • Communication patterns          • Database schema   • Code structure    │
│   • Security model                  • API design        • Error handling    │
│   • Scalability strategy            • State management  • Data validation   │
│                                                                             │
│   ▲                                                                         │
│   │                                                                         │
│   │  Harder to change later                                                │
│   │  Broader impact                                                         │
│   │  More strategic                                                         │
│                                                                             │
└─────────────────────────────────────────────────────────────────────────────┘
```

> **🔑 Key Insight:** Architecture decisions are the most expensive to change later. Getting architecture right is critical to project success.

---

### 5.1.4 Quality Attributes (Non-Functional Requirements)

Architecture directly enables quality attributes. The NSCT expects you to understand these.

| Attribute | Definition | Architectural Considerations |
|-----------|------------|------------------------------|
| **Performance** | Response time, throughput | Caching, asynchronous processing, database optimization, CDN |
| **Scalability** | Ability to handle growth | Horizontal scaling, stateless services, load balancing |
| **Availability** | System uptime | Redundancy, failover, disaster recovery, health checks |
| **Security** | Protection from threats | Authentication, authorization, encryption, audit logging |
| **Maintainability** | Ease of modification | Modularity, separation of concerns, documentation |
| **Testability** | Ease of testing | Loose coupling, dependency injection, test harnesses |
| **Reliability** | Consistent behavior | Error handling, retry logic, circuit breakers |
| **Deployability** | Ease of deployment | Containerization, infrastructure as code, CI/CD |
| **Usability** | User experience | Responsive design, accessibility, user feedback |

---

## 5.2 Architectural Styles

---

### 5.2.1 Overview

An **architectural style** is a set of principles and patterns that guide the structure of a system. The NSCT expects you to recognize and compare the major styles.

| Style | Core Concept | Best For |
|-------|--------------|----------|
| **Layered (N-Tier)** | Separation into logical layers | Enterprise applications with clear separation of concerns |
| **MVC** | Separation of Model, View, Controller | Web applications, user interfaces |
| **Client-Server** | Distributed computing with request-response | Networked applications |
| **Microservices** | Small, independent, deployable services | Large-scale, evolving systems |
| **Event-Driven** | Asynchronous communication via events | Real-time, loosely coupled systems |
| **Monolithic** | Single, unified application | Simple applications, startups |

---

### 5.2.2 Layered (N-Tier) Architecture

**Description:** Organizes the system into horizontal layers where each layer has a specific responsibility. Layers communicate only with adjacent layers.

#### Structure

```
┌─────────────────────────────────────────────────────────────────────────────┐
│                         Presentation Layer                                  │
│                    (UI, user interaction, views)                            │
│                                                                             │
│                              ▼                                              │
├─────────────────────────────────────────────────────────────────────────────┤
│                         Business Logic Layer                                │
│              (Domain logic, rules, calculations, workflows)                 │
│                                                                             │
│                              ▼                                              │
├─────────────────────────────────────────────────────────────────────────────┤
│                         Persistence Layer                                   │
│              (Data access, repositories, ORM)                               │
│                                                                             │
│                              ▼                                              │
├─────────────────────────────────────────────────────────────────────────────┤
│                         Database Layer                                      │
│                    (Data storage, tables, indexes)                          │
└─────────────────────────────────────────────────────────────────────────────┘
```

#### Common N-Tier Variants

| Variant | Layers | Use Case |
|---------|--------|----------|
| **2-Tier** | Client + Database | Simple desktop applications |
| **3-Tier** | Presentation + Business + Data | Most enterprise web applications |
| **4-Tier** | Presentation + Business + Service + Data | Complex distributed systems |
| **N-Tier** | Multiple distributed layers | Large-scale enterprise systems |

#### Example: 3-Tier E-Commerce Application

```
┌─────────────────────────────────────────────────────────────────────────────┐
│                         Presentation Layer                                  │
│  ┌─────────────────────────────────────────────────────────────────────┐   │
│  │  React/Angular/Vue Frontend                                        │   │
│  │  • User interface                                                   │   │
│  │  • Form handling                                                    │   │
│  │  • Client-side validation                                           │   │
│  │  • API calls                                                        │   │
│  └─────────────────────────────────────────────────────────────────────┘   │
│                              │                                             │
│                              │ REST API                                    │
│                              ▼                                             │
├─────────────────────────────────────────────────────────────────────────────┤
│                         Business Logic Layer                               │
│  ┌─────────────────────────────────────────────────────────────────────┐   │
│  │  Spring Boot / .NET Core Backend                                    │   │
│  │  • Controllers (handle requests)                                    │   │
│  │  • Services (business logic)                                        │   │
│  │    - OrderService (calculations, validation)                        │   │
│  │    - PaymentService (payment processing)                            │   │
│  │    - InventoryService (stock management)                            │   │
│  │  • DTOs (data transfer objects)                                     │   │
│  └─────────────────────────────────────────────────────────────────────┘   │
│                              │                                             │
│                              │ Repository/DAO                              │
│                              ▼                                             │
├─────────────────────────────────────────────────────────────────────────────┤
│                         Persistence Layer                                  │
│  ┌─────────────────────────────────────────────────────────────────────┐   │
│  │  • JPA / Entity Framework                                          │   │
│  │  • Repositories (CRUD operations)                                   │   │
│  │  • Query builders                                                   │   │
│  │  • Connection pooling                                               │   │
│  └─────────────────────────────────────────────────────────────────────┘   │
│                              │                                             │
│                              │ SQL                                        │
│                              ▼                                             │
├─────────────────────────────────────────────────────────────────────────────┤
│                         Database Layer                                     │
│  ┌─────────────────────────────────────────────────────────────────────┐   │
│  │  • PostgreSQL / MySQL / Oracle                                      │   │
│  │  • Tables, indexes, constraints                                     │   │
│  │  • Stored procedures                                                │   │
│  │  • Replication, backups                                             │   │
│  └─────────────────────────────────────────────────────────────────────┘   │
└─────────────────────────────────────────────────────────────────────────────┘
```

#### Strengths and Weaknesses

| Strengths | Weaknesses |
|-----------|------------|
| Clear separation of concerns | Can lead to "leaky" abstractions |
| Reusable layers | Performance overhead from multiple layers |
| Easy to understand and maintain | Tight coupling between layers |
| Standardized approach | Changing one layer may affect others |
| Good for enterprise applications | May not suit simple applications |

---

### 5.2.3 MVC (Model-View-Controller)

**Description:** Separates application into three interconnected components: Model (data), View (UI), and Controller (logic).

#### Structure

```
┌─────────────────────────────────────────────────────────────────────────────┐
│                                                                             │
│   ┌─────────────────────────────────────────────────────────────────────┐   │
│   │                         CONTROLLER                                  │   │
│   │  • Handles user input                                               │   │
│   │  • Updates Model                                                    │   │
│   │  • Selects View                                                     │   │
│   │  • Business logic (or delegates to services)                        │   │
│   └─────────────────────────────────────────────────────────────────────┘   │
│          ▲                              │                                   │
│          │                              │                                   │
│          │ updates                     │ updates                          │
│          │                              ▼                                   │
│   ┌─────────────────────────────────────────────────────────────────────┐   │
│   │                           MODEL                                     │   │
│   │  • Domain data                                                     │   │
│   │  • Business logic                                                  │   │
│   │  • State management                                                │   │
│   │  • Notifies observers (View) of changes                            │   │
│   └─────────────────────────────────────────────────────────────────────┘   │
│          │                              ▲                                   │
│          │ notifies                     │ displays                         │
│          │                              │                                   │
│          ▼                              │                                   │
│   ┌─────────────────────────────────────────────────────────────────────┐   │
│   │                            VIEW                                     │   │
│   │  • User interface                                                  │   │
│   │  • Displays data from Model                                        │   │
│   │  • Sends user actions to Controller                                │   │
│   │  • No business logic                                               │   │
│   └─────────────────────────────────────────────────────────────────────┘   │
│                                                                             │
└─────────────────────────────────────────────────────────────────────────────┘
```

#### Example: MVC in Web Application

```java
// Model
public class Product {
    private Long id;
    private String name;
    private BigDecimal price;
    private int stock;
    
    // Getters, setters, business methods
    public boolean isInStock() {
        return stock > 0;
    }
    
    public void reduceStock(int quantity) {
        if (stock >= quantity) {
            stock -= quantity;
        } else {
            throw new InsufficientStockException();
        }
    }
}

// Controller
@RestController
@RequestMapping("/api/products")
public class ProductController {
    
    @Autowired
    private ProductService productService;
    
    @GetMapping
    public List<ProductDTO> getAllProducts() {
        return productService.findAll();
    }
    
    @PostMapping
    public ProductDTO createProduct(@RequestBody ProductDTO productDTO) {
        return productService.create(productDTO);
    }
    
    @PutMapping("/{id}/stock")
    public ProductDTO updateStock(@PathVariable Long id, 
                                   @RequestParam int quantity) {
        return productService.adjustStock(id, quantity);
    }
}

// View (Thymeleaf template)
<!DOCTYPE html>
<html xmlns:th="http://www.thymeleaf.org">
<body>
    <h1>Products</h1>
    <table>
        <tr th:each="product : ${products}">
            <td th:text="${product.name}">Name</td>
            <td th:text="${product.price}">Price</td>
            <td th:text="${product.stock}">Stock</td>
            <td>
                <button th:if="${product.inStock}" 
                        th:onclick="addToCart(${product.id})">
                    Add to Cart
                </button>
            </td>
        </tr>
    </table>
</body>
</html>
```

#### MVC Variants

| Variant | Description | Use Case |
|---------|-------------|----------|
| **MVC (Traditional)** | Controller handles input, updates Model, selects View | Desktop apps, server-side web apps |
| **MVVM** | Model-View-ViewModel (with two-way binding) | Frontend frameworks (React, Vue, Angular) |
| **MVP** | Model-View-Presenter | Android, Windows Forms |

> **🔑 Key Insight:** MVC is a specialization of the layered architecture for user-facing applications. The separation enables independent development, testing, and maintenance of UI and business logic.

---

### 5.2.4 Client-Server Architecture

**Description:** Distributed architecture where clients request services from servers.

#### Structure

```
┌─────────────────────────────────────────────────────────────────────────────┐
│                                                                             │
│   ┌─────────────┐      ┌─────────────┐      ┌─────────────┐               │
│   │   Client    │      │   Client    │      │   Client    │               │
│   │  (Browser)  │      │  (Mobile)   │      │  (Desktop)  │               │
│   └──────┬──────┘      └──────┬──────┘      └──────┬──────┘               │
│          │                    │                    │                       │
│          └────────────────────┼────────────────────┘                       │
│                               │ HTTP/HTTPS                                 │
│                               ▼                                            │
│                    ┌─────────────────────────┐                            │
│                    │       Server(s)         │                            │
│                    │  • Web Server           │                            │
│                    │  • Application Server   │                            │
│                    │  • Database Server      │                            │
│                    └─────────────────────────┘                            │
│                                                                             │
└─────────────────────────────────────────────────────────────────────────────┘
```

#### Client-Server Variants

| Variant | Description | Example |
|---------|-------------|---------|
| **2-Tier** | Client connects directly to database | Desktop app with JDBC |
| **3-Tier** | Client → Application Server → Database | Web applications |
| **N-Tier** | Multiple server layers (web, app, data, caching) | Large enterprise systems |

---

### 5.2.5 Microservices Architecture

**Description:** Decomposes the application into small, independent services that communicate via well-defined APIs. Each service is:
- **Independently deployable**
- **Organized around business capabilities**
- **Owned by a small team**
- **Built with its own technology stack**

#### Structure

```
┌─────────────────────────────────────────────────────────────────────────────┐
│                                                                             │
│   ┌─────────────────────────────────────────────────────────────────────┐   │
│   │                         API Gateway                                  │   │
│   │              (Routing, authentication, rate limiting)                │   │
│   └─────────────────────────────────────────────────────────────────────┘   │
│                                    │                                        │
│       ┌────────────────────────────┼────────────────────────────┐          │
│       │                            │                            │          │
│       ▼                            ▼                            ▼          │
│ ┌─────────────┐            ┌─────────────┐            ┌─────────────┐     │
│ │   Order     │            │  Customer   │            │  Inventory  │     │
│ │   Service   │◀──────────▶│  Service    │◀──────────▶│  Service    │     │
│ └─────────────┘            └─────────────┘            └─────────────┘     │
│       │                            │                            │          │
│       ▼                            ▼                            ▼          │
│ ┌─────────────┐            ┌─────────────┐            ┌─────────────┐     │
│ │  Payment    │            │  Shipping   │            │  Catalog    │     │
│ │  Service    │            │  Service    │            │  Service    │     │
│ └─────────────┘            └─────────────┘            └─────────────┘     │
│       │                            │                            │          │
│       └────────────────────────────┼────────────────────────────┘          │
│                                    │                                        │
│                                    ▼                                        │
│                    ┌─────────────────────────────┐                         │
│                    │     Service Registry        │                         │
│                    │  (Discovery, health checks) │                         │
│                    └─────────────────────────────┘                         │
│                                                                             │
└─────────────────────────────────────────────────────────────────────────────┘
```

#### Monolithic vs. Microservices

| Dimension | Monolithic | Microservices |
|-----------|------------|---------------|
| **Deployment** | Single unit | Independent services |
| **Scalability** | Scale entire application | Scale individual services |
| **Technology** | Single stack | Multiple stacks (per service) |
| **Team Structure** | Single large team | Small, autonomous teams |
| **Development Speed** | Slow (coordinated releases) | Fast (independent releases) |
| **Complexity** | Internal complexity | Operational complexity |
| **Data Management** | Single database | Database per service |
| **Communication** | In-memory calls | Network calls (HTTP, gRPC) |
| **Testing** | End-to-end tests | Service-level tests |

#### Microservices Challenges

| Challenge | Description | Mitigation |
|-----------|-------------|------------|
| **Distributed Complexity** | Network latency, failures, distributed transactions | Circuit breakers, saga pattern, eventual consistency |
| **Data Consistency** | No single database; eventual consistency | Event sourcing, CQRS, distributed transactions |
| **Operational Overhead** | Deploying, monitoring, logging many services | Kubernetes, centralized logging, distributed tracing |
| **Service Discovery** | Services need to find each other | Service registry (Consul, Eureka) |
| **API Versioning** | Multiple service versions coexisting | API gateways, versioned endpoints |
| **Testing** | Integration testing across services | Contract testing, consumer-driven contracts |

> **🔑 Key Insight:** Microservices are not a silver bullet. They trade internal complexity for operational complexity. Use them when you need independent scalability, team autonomy, or technology diversity.

---

### 5.2.6 Event-Driven Architecture

**Description:** Components communicate by producing and consuming events. Events represent state changes or significant occurrences.

#### Structure

```
┌─────────────────────────────────────────────────────────────────────────────┐
│                                                                             │
│   ┌─────────────┐                                                          │
│   │  Producer   │ ──────┐                                                  │
│   │  (Order     │       │  Event: "Order Created"                          │
│   │   Service)  │       ▼                                                  │
│   └─────────────┘   ┌─────────────────────────────────────┐                │
│                     │          Message Broker             │                │
│   ┌─────────────┐   │    (Kafka, RabbitMQ, SQS)          │                │
│   │  Producer   │ ──▶│                                     │                │
│   │  (Payment   │   │    • Topics: order.events           │                │
│   │   Service)  │   │    • Partitions                     │                │
│   └─────────────┘   │    • Consumer groups                │                │
│                     └─────────────────────────────────────┘                │
│                               │        │        │                         │
│                               ▼        ▼        ▼                         │
│                     ┌─────────────┐ ┌─────────────┐ ┌─────────────┐       │
│                     │  Consumer   │ │  Consumer   │ │  Consumer   │       │
│                     │  (Inventory │ │  (Shipping  │ │  (Notification)│     │
│                     │   Service)  │ │   Service)  │ │   Service)  │       │
│                     └─────────────┘ └─────────────┘ └─────────────┘       │
│                                                                             │
└─────────────────────────────────────────────────────────────────────────────┘
```

#### Event-Driven Patterns

| Pattern | Description | Example |
|---------|-------------|---------|
| **Event Notification** | Service emits event to notify others; no expectation of response | "Order placed" notification to shipping |
| **Event-Carried State Transfer** | Event contains data needed by consumers | Customer update event includes full profile |
| **Event Sourcing** | System state is derived from event log | Audit log; financial systems |
| **CQRS** | Separate read and write models | High-read applications |

---

### 5.2.7 Comparison of Architectural Styles

| Dimension | Layered | MVC | Client-Server | Microservices | Event-Driven |
|-----------|---------|-----|---------------|---------------|--------------|
| **Complexity** | Medium | Low | Medium | High | High |
| **Scalability** | Vertical | Vertical | Vertical | Horizontal | Horizontal |
| **Deployment** | Single unit | Single unit | Multiple units | Independent services | Independent services |
| **Team Structure** | Single team | Single team | Single team | Multiple teams | Multiple teams |
| **Data Management** | Centralized | Centralized | Centralized | Per service | Event logs |
| **Communication** | In-process | In-process | Network | Network | Asynchronous |
| **Best For** | Enterprise apps | Web apps | Distributed apps | Large-scale, evolving | Real-time, loose coupling |

---

## 5.3 Implementation Best Practices

---

### 5.3.1 Clean Code Principles

Clean code is code that is easy to understand, easy to modify, and easy to test. The NSCT expects you to understand these principles.

| Principle | Description | Example |
|-----------|-------------|---------|
| **Meaningful Names** | Variables, functions, classes should reveal intent | `elapsedTimeInDays` not `d` |
| **Single Responsibility** | Each function/class does one thing | `calculateTotal()` not `calculateAndSaveAndEmail()` |
| **Small Functions** | Functions should be small (10-20 lines) | One screen height |
| **Few Arguments** | Functions should have few parameters (0-3) | Use objects for >3 arguments |
| **Avoid Duplication** | Don't repeat yourself (DRY) | Extract common code into functions |
| **Express Intent** | Code should tell a story | Comments explain why, not what |
| **Error Handling** | Handle errors, don't ignore them | Use try-catch, return meaningful errors |

#### Code Example: Clean vs. Unclean

**Unclean Code:**
```java
// What does this do?
public void a(List<Object> l) {
    for (Object o : l) {
        if (o instanceof User) {
            User u = (User) o;
            if (u.getAge() > 18 && u.getStatus().equals("active")) {
                double t = 0;
                for (Order o2 : u.getOrders()) {
                    t += o2.getAmount();
                }
                if (t > 1000) {
                    u.sendEmail("You're a VIP!");
                }
            }
        }
    }
}
```

**Clean Code:**
```java
public void sendVIPEmailToActiveAdultUsers(List<User> users) {
    for (User user : users) {
        if (isActiveAdultUser(user)) {
            double totalSpent = calculateTotalSpent(user);
            if (isVIP(totalSpent)) {
                user.sendEmail(VIP_WELCOME_MESSAGE);
            }
        }
    }
}

private boolean isActiveAdultUser(User user) {
    return user.getAge() >= ADULT_AGE 
           && user.getStatus() == UserStatus.ACTIVE;
}

private double calculateTotalSpent(User user) {
    return user.getOrders().stream()
               .mapToDouble(Order::getAmount)
               .sum();
}

private boolean isVIP(double totalSpent) {
    return totalSpent > VIP_THRESHOLD;
}
```

---

### 4.3.2 Documentation

Good documentation is essential for maintainability. The NSCT expects you to understand the types of documentation and when to use them.

| Documentation Type | Purpose | Audience |
|--------------------|---------|----------|
| **Code Comments** | Explain why, not what | Developers |
| **API Documentation** | How to use the API | API consumers |
| **Architecture Documentation** | High-level structure | Architects, new developers |
| **User Documentation** | How to use the system | End users |
| **Operations Documentation** | How to deploy, monitor, troubleshoot | DevOps, operations |
| **README** | Project overview, setup instructions | All stakeholders |

#### Comment Best Practices

| Do | Don't |
|----|-------|
| Explain **why** code exists | Explain what code does (code should be self-documenting) |
| Document complex algorithms | Comment obvious code |
| Note workarounds or hacks | Leave commented-out code |
| Document API contracts | Write lengthy comments for simple code |
| Use TODOs for planned work | Use comments for version control |

**Good Comments:**
```java
// Using exponential backoff to avoid overwhelming the server
// due to known rate limiting issues (see JIRA-1234)
for (int attempt = 1; attempt <= MAX_RETRIES; attempt++) {
    try {
        return apiClient.sendRequest(request);
    } catch (RateLimitException e) {
        long waitTime = (long) Math.pow(2, attempt) * BASE_DELAY;
        Thread.sleep(waitTime);
    }
}
```

---

### 5.3.3 Version Control with Git

Version control is fundamental to modern software development. The NSCT expects you to understand Git concepts and workflows.

#### Git Basics

| Concept | Description |
|---------|-------------|
| **Repository** | Collection of files and their history |
| **Commit** | Snapshot of changes with a message |
| **Branch** | Independent line of development |
| **Merge** | Combining changes from different branches |
| **Remote** | Shared repository (GitHub, GitLab) |
| **Pull Request** | Proposal to merge changes with review |

#### Essential Git Commands

| Command | Purpose |
|---------|---------|
| `git init` | Create new repository |
| `git clone` | Copy existing repository |
| `git add` | Stage changes for commit |
| `git commit -m "message"` | Save staged changes |
| `git push` | Upload commits to remote |
| `git pull` | Download changes from remote |
| `git branch` | List/create branches |
| `git checkout` | Switch branches |
| `git merge` | Combine branches |
| `git status` | Show working directory status |
| `git log` | Show commit history |

#### Branching Strategies

| Strategy | Description | Use Case |
|----------|-------------|----------|
| **Git Flow** | Master, develop, feature, release, hotfix branches | Large projects with scheduled releases |
| **GitHub Flow** | Main branch with feature branches; deploy from main | Continuous deployment |
| **Trunk-Based** | Single main branch with short-lived feature branches | CI/CD, high velocity teams |

**Git Flow Structure:**
```
main (production) ──────●──────────────────●─────────────────────●────
                        │                  │                     │
develop ────────────────●──●──●──●─────────●──●──●──────────────●────
                        │  │  │  │         │  │  │              │
feature/feature1 ───────┘  │  │  │         │  │  │              │
feature/feature2 ──────────┘  │  │         │  │  │              │
feature/feature3 ─────────────┘  │         │  │  │              │
release/1.0 ─────────────────────┘         │  │  │              │
hotfix/1.0.1 ───────────────────────────────┘  │  │              │
release/2.0 ───────────────────────────────────┘  │              │
hotfix/2.0.1 ──────────────────────────────────────┘              │
```

#### Commit Message Best Practices

**Format:**
```
<type>(<scope>): <subject>

<body>

<footer>
```

**Types:**
| Type | Purpose |
|------|---------|
| `feat` | New feature |
| `fix` | Bug fix |
| `docs` | Documentation |
| `style` | Formatting |
| `refactor` | Code restructuring |
| `test` | Adding tests |
| `chore` | Maintenance |

**Example:**
```
feat(auth): add OAuth2 login support

- Implement Google OAuth2 provider
- Add session management
- Store refresh tokens securely

Closes #123
```

---

### 5.3.4 Code Quality Metrics

The NSCT may test your understanding of code quality metrics.

| Metric | Definition | Target |
|--------|------------|--------|
| **Cyclomatic Complexity** | Number of independent paths through code | < 10 per function |
| **Code Coverage** | Percentage of code executed by tests | > 80% |
| **Duplication** | Percentage of duplicated code | < 3% |
| **Comment Density** | Comments per line of code | 10-20% for complex code |
| **Technical Debt Ratio** | Cost to fix vs. cost to develop | < 5% |
| **Maintainability Index** | 0-100 score of maintainability | > 70 |

#### Technical Debt

> **Technical Debt** is the implied cost of additional rework caused by choosing an easy solution now instead of a better approach that would take longer.

| Type | Description | Example |
|------|-------------|---------|
| **Deliberate** | Conscious trade-off to meet deadline | Skipping tests to ship on time |
| **Inadvertent** | Unintentional due to lack of knowledge | Poor design from junior developer |
| **Bit Rot** | Accumulation of outdated code | Dependencies no longer supported |
| **Documentation** | Missing or outdated docs | No architecture documentation |

**Managing Technical Debt:**
1. **Identify:** Use static analysis tools (SonarQube, ESLint)
2. **Track:** Add to backlog with priority
3. **Prioritize:** High-impact, high-cost debt first
4. **Pay down:** Dedicate 10-20% of sprint capacity to refactoring
5. **Prevent:** Code reviews, standards, automated checks

---

## 5.4 Modern Development Practices

---

### 5.4.1 DevOps Culture

**DevOps** is a culture and set of practices that combines software development (Dev) and IT operations (Ops) to shorten the development lifecycle and deliver high-quality software continuously.

#### The Three Ways of DevOps

| Principle | Description |
|-----------|-------------|
| **Flow** | Accelerate flow of work from Dev to Ops (CI/CD, automation) |
| **Feedback** | Shorten feedback loops (monitoring, alerts, testing) |
| **Continuous Learning** | Experiment, learn, improve (blameless post-mortems) |

#### DevOps Practices

| Practice | Description |
|----------|-------------|
| **CI/CD** | Continuous Integration and Continuous Deployment |
| **Infrastructure as Code** | Manage infrastructure with code (Terraform, CloudFormation) |
| **Monitoring & Observability** | Understand system behavior (logs, metrics, traces) |
| **Automated Testing** | Tests run automatically in pipeline |
| **Collaboration** | Breaking down silos between Dev and Ops |

---

### 5.4.2 Continuous Integration (CI)

**Continuous Integration** is the practice of automatically building and testing code whenever changes are pushed to the repository.

#### CI Pipeline

```
┌─────────────────────────────────────────────────────────────────────────────┐
│                         CI Pipeline                                         │
│                                                                             │
│   ┌─────────┐    ┌─────────┐    ┌─────────┐    ┌─────────┐    ┌─────────┐ │
│   │  Code   │───▶│  Build  │───▶│  Unit   │───▶│  Static │───▶│ Package │ │
│   │  Push   │    │         │    │  Tests  │    │ Analysis│    │         │ │
│   └─────────┘    └─────────┘    └─────────┘    └─────────┘    └─────────┘ │
│                                                                             │
│   • Triggered on every commit              • Fast feedback (< 10 min)      │
│   • Ensures code doesn't break build       • Prevents integration hell    │
│   • Tools: Jenkins, GitHub Actions, GitLab CI, CircleCI                   │
│                                                                             │
└─────────────────────────────────────────────────────────────────────────────┘
```

---

### 5.4.3 Continuous Delivery (CD) & Deployment

| Concept | Definition |
|---------|------------|
| **Continuous Delivery** | Every change is automatically tested and ready to deploy to production |
| **Continuous Deployment** | Every change that passes tests is automatically deployed to production |

#### CD Pipeline

```
┌─────────────────────────────────────────────────────────────────────────────┐
│                         CD Pipeline                                         │
│                                                                             │
│   ┌─────────┐    ┌─────────┐    ┌─────────┐    ┌─────────┐    ┌─────────┐ │
│   │ Package │───▶│ Deploy  │───▶│Integra- │───▶│ Deploy  │───▶│ Smoke   │ │
│   │         │    │ to Dev  │    │tion Tests│    │ to Stg  │    │ Tests   │ │
│   └─────────┘    └─────────┘    └─────────┘    └─────────┘    └─────────┘ │
│                                                                   │        │
│                                                                   ▼        │
│   ┌─────────┐    ┌─────────┐    ┌─────────┐    ┌─────────┐    ┌─────────┐ │
│   │ Monitor │◀───│ Deploy  │◀───│ Perform-│◀───│  Canary │◀───│  E2E    │ │
│   │         │    │ to Prod │    │ance Tests│    │ Deploy  │    │ Tests   │ │
│   └─────────┘    └─────────┘    └─────────┘    └─────────┘    └─────────┘ │
│                                                                             │
└─────────────────────────────────────────────────────────────────────────────┘
```

#### Deployment Strategies

| Strategy | Description | Pros | Cons |
|----------|-------------|------|------|
| **Rolling** | Gradually replace instances | No downtime; gradual rollout | Complex; version mixing |
| **Blue/Green** | Switch between two identical environments | Instant rollback; zero downtime | Double infrastructure cost |
| **Canary** | Deploy to small subset first | Risk reduction; real traffic validation | Complex traffic routing |
| **A/B Testing** | Route users based on attributes | Experimentation; feature validation | Requires routing logic |

---

### 5.4.4 Containerization

**Containers** package code with its dependencies, ensuring consistency across environments.

#### Docker Concepts

| Concept | Description |
|---------|-------------|
| **Image** | Immutable template with code and dependencies |
| **Container** | Running instance of an image |
| **Dockerfile** | Instructions to build an image |
| **Registry** | Repository for images (Docker Hub, ECR) |
| **Orchestration** | Managing multiple containers (Kubernetes) |

#### Example Dockerfile

```dockerfile
# Build stage
FROM maven:3.8-openjdk-11 AS builder
WORKDIR /app
COPY pom.xml .
RUN mvn dependency:go-offline
COPY src ./src
RUN mvn package -DskipTests

# Run stage
FROM openjdk:11-jre-slim
WORKDIR /app
COPY --from=builder /app/target/app.jar .
EXPOSE 8080
ENTRYPOINT ["java", "-jar", "app.jar"]
```

---

### 5.4.5 Kubernetes Orchestration

**Kubernetes** automates deployment, scaling, and management of containerized applications.

#### Kubernetes Concepts

| Concept | Description |
|---------|-------------|
| **Pod** | Smallest deployable unit; one or more containers |
| **Deployment** | Desired state for pods; handles rollouts, rollbacks |
| **Service** | Stable network endpoint for pods |
| **Ingress** | HTTP/HTTPS routing to services |
| **ConfigMap** | Configuration data |
| **Secret** | Sensitive data (passwords, tokens) |

#### Example Kubernetes Deployment

```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: order-service
spec:
  replicas: 3
  selector:
    matchLabels:
      app: order-service
  template:
    metadata:
      labels:
        app: order-service
    spec:
      containers:
      - name: order-service
        image: myregistry/order-service:latest
        ports:
        - containerPort: 8080
        env:
        - name: DATABASE_URL
          valueFrom:
            secretKeyRef:
              name: db-secret
              key: url
        resources:
          requests:
            memory: "256Mi"
            cpu: "250m"
          limits:
            memory: "512Mi"
            cpu: "500m"
---
apiVersion: v1
kind: Service
metadata:
  name: order-service
spec:
  selector:
    app: order-service
  ports:
  - port: 80
    targetPort: 8080
  type: LoadBalancer
```

---

## 5.5 Architecture Decision Records (ADRs)

**Architecture Decision Records** capture important architectural decisions and their rationale.

#### ADR Structure

| Section | Content |
|---------|---------|
| **Title** | Short description of the decision |
| **Status** | Proposed, Accepted, Deprecated, Superseded |
| **Context** | Problem statement, forces, constraints |
| **Decision** | What we decided and why |
| **Consequences** | Positive and negative outcomes |
| **Alternatives** | Options considered and why rejected |

#### Example ADR

```
# ADR 001: Use PostgreSQL as Primary Database

## Status
Accepted

## Context
We need a primary database for the order management system.
Requirements:
- ACID compliance for financial transactions
- Complex querying for reporting
- High availability
- Developer familiarity

## Decision
We will use PostgreSQL as the primary database.
- Use Amazon RDS for managed hosting
- Enable Multi-AZ for high availability
- Use pgBouncer for connection pooling

## Consequences
Positive:
- ACID compliance ensures data integrity
- Strong community and tooling
- Familiar to team

Negative:
- Requires careful schema migration management
- Not as horizontally scalable as NoSQL options

## Alternatives Considered
1. **MongoDB**: Rejected due to ACID requirement for transactions
2. **MySQL**: Rejected; PostgreSQL has better feature set for reporting
3. **DynamoDB**: Rejected due to complex querying requirements
```

---

## 💡 Study Activity: Deep Dive

---

### Activity 1: Architecture Selection

For each scenario, recommend an architectural style and justify your choice:

**Scenario A:** A large e-commerce platform with 50+ developers. The company wants to deploy multiple times per day and scale individual components independently.

<details>
<summary>Click for answer</summary>
<strong>Microservices Architecture.</strong>
- Independent deployment enables multiple daily releases
- Independent scaling allows scaling cart service during sales, catalog service during browsing
- Multiple teams can work autonomously on different services
- Challenges: Requires mature DevOps practices, distributed transaction handling
</details>

**Scenario B:** A university student portal with 5 developers. Requirements are stable and system is expected to last 10+ years.

<details>
<summary>Click for answer</summary>
<strong>Layered Architecture (3-Tier) with MVC.</strong>
- Simple, understandable architecture for small team
- Stable requirements don't need microservice complexity
- Clear separation of concerns enables long-term maintenance
- Well-understood patterns for future developers
</details>

**Scenario C:** A real-time fraud detection system that must process 100,000 transactions per second with millisecond latency.

<details>
<summary>Click for answer</summary>
<strong>Event-Driven Architecture.</strong>
- Asynchronous processing enables high throughput
- Can scale consumers independently based on load
- Decoupled services can be optimized for specific processing
- Event sourcing provides audit trail for fraud investigation
</details>

---

### Activity 2: Clean Code Refactoring

Refactor the following code to follow clean code principles:

```java
public void p(List<Item> i, User u) {
    double t = 0;
    for (Item x : i) {
        if (x.getQuantity() > 0) {
            t += x.getPrice() * x.getQuantity();
            x.setStock(x.getStock() - x.getQuantity());
        }
    }
    if (u.getCreditLimit() >= t) {
        u.setCredit(u.getCredit() - t);
        Email.send(u.getEmail(), "Order confirmed: $" + t);
    } else {
        throw new Exception("Insufficient credit");
    }
}
```

<details>
<summary>Click for answer</summary>

```java
public void processOrder(List<Item> items, User user) {
    double totalAmount = calculateTotalAmount(items);
    
    validateCreditLimit(user, totalAmount);
    
    updateInventory(items);
    deductCredit(user, totalAmount);
    sendOrderConfirmation(user, totalAmount);
}

private double calculateTotalAmount(List<Item> items) {
    return items.stream()
        .filter(item -> item.getQuantity() > 0)
        .mapToDouble(item -> item.getPrice() * item.getQuantity())
        .sum();
}

private void validateCreditLimit(User user, double amount) {
    if (user.getCreditLimit() < amount) {
        throw new InsufficientCreditException("Credit limit exceeded");
    }
}

private void updateInventory(List<Item> items) {
    for (Item item : items) {
        if (item.getQuantity() > 0) {
            item.reduceStock(item.getQuantity());
        }
    }
}

private void deductCredit(User user, double amount) {
    user.deductCredit(amount);
}

private void sendOrderConfirmation(User user, double amount) {
    String message = String.format("Order confirmed: $%.2f", amount);
    emailService.send(user.getEmail(), message);
}
```
</details>

---

### Activity 3: CI/CD Pipeline Design

Design a CI/CD pipeline for a microservices-based application with the following requirements:
- Automated testing at multiple levels
- Security scanning
- Deploy to production with minimal risk
- Ability to rollback quickly

<details>
<summary>Click for answer</summary>

```
┌─────────────────────────────────────────────────────────────────────────────┐
│                         CI/CD Pipeline Design                               │
├─────────────────────────────────────────────────────────────────────────────┤
│                                                                             │
│  STAGE 1: Continuous Integration                                           │
│  ┌─────────────────────────────────────────────────────────────────────┐   │
│  │ • Code commit triggers pipeline                                     │   │
│  │ • Unit tests (parallel per service)                                 │   │
│  │ • Static analysis (SonarQube)                                       │   │
│  │ • Security scanning (SAST)                                          │   │
│  │ • Build container images                                             │   │
│  │ • Push to registry                                                   │   │
│  └─────────────────────────────────────────────────────────────────────┘   │
│                                    │                                        │
│                                    ▼                                        │
│  STAGE 2: Integration Testing                                              │
│  ┌─────────────────────────────────────────────────────────────────────┐   │
│  │ • Deploy to ephemeral environment                                   │   │
│  │ • Contract testing (Pact) between services                          │   │
│  │ • Integration tests with dependencies                                │   │
│  │ • Performance tests (10% load)                                      │   │
│  └─────────────────────────────────────────────────────────────────────┘   │
│                                    │                                        │
│                                    ▼                                        │
│  STAGE 3: Staging Deployment                                               │
│  ┌─────────────────────────────────────────────────────────────────────┐   │
│  │ • Deploy to staging environment                                     │   │
│  │ • Full regression tests                                              │   │
│  │ • Security penetration tests                                        │   │
│  │ • Performance/load tests                                            │   │
│  │ • Manual approval gate                                               │   │
│  └─────────────────────────────────────────────────────────────────────┘   │
│                                    │                                        │
│                                    ▼                                        │
│  STAGE 4: Production Deployment                                           │
│  ┌─────────────────────────────────────────────────────────────────────┐   │
│  │ • Canary deployment (5% traffic)                                    │   │
│  │ • Monitor metrics (error rate, latency) for 30 min                  │   │
│  │ • If healthy, increment to 50%, then 100%                           │   │
│  │ • If unhealthy, automatic rollback                                  │   │
│  │ • Smoke tests after full deployment                                 │   │
│  └─────────────────────────────────────────────────────────────────────┘   │
│                                                                             │
└─────────────────────────────────────────────────────────────────────────────┘
```
</details>

---

## 📝 Module 5 Self-Assessment Quiz

1. What is the difference between software architecture and software design?

   <details>
   <summary>Click for answer</summary>
   Architecture is high-level, system-wide structure and decisions; design is detailed, component-level implementation decisions. Architecture decisions are harder to change and have broader impact.
   </details>

2. Name five architectural styles.

   <details>
   <summary>Click for answer</summary>
   Layered (N-Tier), MVC, Client-Server, Microservices, Event-Driven, Monolithic.
   </details>

3. What are the three components of MVC and their responsibilities?

   <details>
   <summary>Click for answer</summary>
   Model (data, business logic), View (user interface), Controller (handles input, updates Model, selects View).
   </details>

4. What is the difference between monolithic and microservices architecture?

   <details>
   <summary>Click for answer</summary>
   Monolithic is a single, unified application; microservices decomposes into small, independent, deployable services. Monolithic scales vertically; microservices scale horizontally.
   </details>

5. What are the three layers in a 3-tier architecture?

   <details>
   <summary>Click for answer</summary>
   Presentation Layer (UI), Business Logic Layer (domain logic), Data Layer (persistence).
   </details>

6. What is technical debt?

   <details>
   <summary>Click for answer</summary>
   The implied cost of additional rework caused by choosing an easy solution now instead of a better approach that would take longer.
   </details>

7. What is the difference between Continuous Delivery and Continuous Deployment?

   <details>
   <summary>Click for answer</summary>
   Continuous Delivery: every change is ready to deploy but requires manual approval. Continuous Deployment: every change that passes tests is automatically deployed to production.
   </details>

8. What are the three deployment strategies discussed?

   <details>
   <summary>Click for answer</summary>
   Rolling (gradual replacement), Blue/Green (switch between environments), Canary (deploy to small subset first).
   </details>

9. What is the purpose of an Architecture Decision Record (ADR)?

   <details>
   <summary>Click for answer</summary>
   To capture important architectural decisions, their context, rationale, and consequences for future reference.
   </details>

10. What are the three ways of DevOps?

    <details>
    <summary>Click for answer</summary>
    Flow (accelerate work from Dev to Ops), Feedback (shorten feedback loops), Continuous Learning (experiment, learn, improve).
    </details>

---

## 🔗 Connections to Other Modules

| Concept from Module 5 | Connects to |
|-----------------------|-------------|
| Architecture styles | Module 4: Design (UML component diagrams) |
| Clean code | Module 6: Testing (testable code) |
| Technical debt | Module 7: Maintenance |
| CI/CD | Module 6: Testing (automated testing) |
| Containers | Module 7: DevOps, Deployment |

---

## ✅ Module 5 Summary

| Section | Key Takeaways |
|---------|---------------|
| **5.1 Introduction** | Architecture is high-level structure; enables quality attributes; harder to change than design |
| **5.2 Architectural Styles** | Layered, MVC, Client-Server, Microservices, Event-Driven—each with trade-offs |
| **5.3 Implementation** | Clean code principles; documentation; Git; code quality metrics; technical debt |
| **5.4 Modern Practices** | DevOps culture; CI/CD pipelines; containerization; Kubernetes orchestration |
| **5.5 ADRs** | Capture architectural decisions with rationale for future reference |

---
