# Spring Boot Engineering Development
## Project and Learning Handoff

**Purpose:** Build stronger, more independent software engineering skills through the development of a realistic Spring Boot application.

---

# 1. Overall objective

This is not simply a portfolio project or an exercise in learning Spring Boot.

The objective is to become a more confident, competent and autonomous software engineer, particularly in Java backend development.

The project should help develop the ability to:

- Understand business requirements and translate them into software.
- Design maintainable applications and meaningful domain models.
- Write clean, readable and testable Java code.
- Understand the principles behind frameworks and libraries rather than merely using them.
- Make sound technical decisions and explain their trade-offs.
- Identify problems, investigate them and solve them independently.
- Discuss architecture, implementation choices and engineering practices with other developers.

The emphasis is on **depth of understanding, not the quantity of code produced**.

# 2. Project definition

## Client Onboarding Management API

We will build a backend application that manages the onboarding of business clients, inspired by enterprise and banking environments.

### Initial business capabilities

**Client management**
- Create a client.
- Retrieve a client.
- List and search clients.
- Validate client information.

**Onboarding management**
- Create an onboarding case for a client.
- Retrieve and list onboarding cases.
- Track the onboarding lifecycle.
- Approve or reject an onboarding case.
- Enforce valid business transitions.

**Document management**
- Register required document metadata.
- Track document submission and verification status.
- Identify missing or invalid documents.
- Apply document requirements to onboarding cases.

The first version will manage document metadata and statuses, not actual file storage.

### Important domain questions to resolve

We should not make these decisions prematurely. We will reason about them during domain modelling.

- Can a client have several independent onboarding cases over time?
- Can an onboarding case be reopened?
- What are the possible onboarding statuses?
- Which status transitions are valid?
- What documents are required?
- Do requirements vary according to client type?
- Can an onboarding case be approved when documents are missing?
- What happens when a case is rejected and subsequently resubmitted?

# 3. Technical direction

## Architecture

We will use a **modular monolith**:

- One deployable application.
- One database.
- Clearly separated business modules.
- Explicit boundaries and controlled dependencies.

Potential initial modules:

- `client`
- `onboarding`
- `document`
- `user`

These boundaries will be validated as we understand the domain.

### Hexagonal architecture

We will introduce hexagonal architecture incrementally, where it provides real value.

We will not try to make every class follow an architectural pattern from the beginning.

The intended approach is:

1. Start with a simple, well-structured modular monolith.
2. Implement a real vertical slice.
3. Identify responsibilities and dependencies.
4. Introduce ports and adapters where they improve separation and testability.
5. Refine module boundaries as the application evolves.

The objective is to understand the reasons behind architectural decisions, not to reproduce diagrams or patterns mechanically.

## Proposed technology stack

| Area | Technology |
|---|---|
| Language | Java 21 or a suitable current LTS version |
| Framework | Spring Boot |
| API | Spring MVC, REST, OpenAPI |
| Database | PostgreSQL |
| Persistence | Spring Data JPA, Hibernate |
| Database migrations | Flyway |
| Build | Maven |
| Testing | JUnit 5, Mockito, Testcontainers |
| Security | Spring Security, OAuth2, JWT |
| Containers | Docker, Docker Compose |
| CI/CD | GitHub Actions |
| IDE | IntelliJ IDEA |
| Version control | Git, GitHub |

We will confirm framework and dependency compatibility when initializing the project.

## Explicitly excluded from the first version

To avoid unnecessary complexity, the initial project will not include:

- A frontend.
- Microservices.
- Kafka or event streaming.
- Distributed architecture.
- Cloud deployment.
- Actual document storage.
- A workflow engine.
- AI features.

These can become future extensions if they serve a learning objective.

# 4. Learning scope

The project will cover the following areas.

1. Java and Spring Boot fundamentals.
2. REST API design and OpenAPI.
3. Database modelling and SQL.
4. JPA and Hibernate.
5. Clean code, SOLID and design patterns.
6. Software architecture and Domain-Driven Design.
7. Unit, integration and acceptance testing.
8. TDD and Testcontainers.
9. Security, OAuth2 and JWT.
10. Docker and CI/CD.

**Important:** Java fundamentals are an explicit part of the plan. They are not assumed to be mastered simply because of previous professional experience.

# 5. Java foundations track

We will assess and strengthen Java knowledge alongside the project.

This will not become a separate, lengthy prerequisite course. We will introduce concepts when they become relevant, with focused exercises when independent practice is useful.

## Topics to cover

### Object-oriented programming
- Classes and objects.
- Encapsulation.
- Abstraction.
- Inheritance and polymorphism.
- Interfaces and abstract classes.
- Composition versus inheritance.
- Object modelling and responsibilities.

### Core Java language
- Primitive and reference types.
- Classes, records and enums.
- Constructors and methods.
- Access modifiers.
- Generics.
- Annotations.
- Exceptions and exception handling.
- Pass-by-value and object references.

### Collections and data structures
- List, Set and Map.
- ArrayList, HashSet and HashMap.
- equals() and hashCode().
- Collection selection and complexity.
- HashMap internals, collisions and performance.

### Functional Java
- Lambdas.
- Functional interfaces.
- Method references.
- Streams.
- Intermediate and terminal operations.
- Stream laziness.
- Optional.

### Java internals
- References and object lifecycle.
- Immutability.
- JVM fundamentals.
- Memory and garbage collection.

### Concurrency fundamentals
- Threads.
- Synchronization.
- Executors.
- CompletableFuture.
- Basic concurrency problems.

### Modern Java
- Records.
- Sealed classes.
- Pattern matching.
- Relevant language improvements.

We will prioritize the topics according to their practical relevance. Not every advanced topic needs to be mastered before building the application.

## Initial Java assessment

Before the first project implementation, we will perform a practical baseline assessment.

It will cover:

- Object-oriented modelling.
- Collections and HashMap.
- Generics.
- Streams and Optional.
- Exceptions.
- Basic Java internals.
- Basic concurrency.

This is not an exam or a gatekeeping exercise. Its purpose is to identify what is already understood, what is partially understood and what needs focused work.

We will repeat selected exercises later to measure progress.

# 6. Development roadmap

The roadmap is intentionally incremental.

### Phase 0 — Java foundations assessment
- Establish a baseline.
- Identify knowledge gaps.
- Select the first topics to reinforce.

### Phase 1 — Requirements and domain modelling
- Understand the business problem.
- Identify domain concepts and relationships.
- Define the main use cases.
- Discuss lifecycle and business rules.
- Make initial architecture decisions.

### Phase 2 — Database and application design
- Design the initial database model.
- Understand entity relationships.
- Identify domain responsibilities.
- Define the initial module structure.

### Phase 3 — Project initialization
- Configure Java and Spring Boot.
- Set up Maven.
- Configure PostgreSQL.
- Introduce Flyway.
- Set up Git and the initial repository structure.

### Phase 4 — First vertical slice: Create a client

Implement the complete flow:

`HTTP request → Controller → Application service → Repository → PostgreSQL`

This slice will introduce:
- DTOs.
- Validation.
- Dependency injection.
- Domain modelling.
- Persistence.
- Transactions.
- Error handling.
- Unit and integration testing.

After implementation, we will review the design and discuss possible improvements.

### Phase 5 — Onboarding cases
- Create and retrieve onboarding cases.
- Define relationships with clients.
- Implement business rules.
- Introduce lifecycle management.

### Phase 6 — Documents and business workflows
- Register documents.
- Track document status.
- Enforce document requirements.
- Implement approval and rejection rules.

### Phase 7 — Security
- Authentication.
- Authorization.
- Spring Security.
- OAuth2 and JWT.

### Phase 8 — Quality and delivery
- Improve test coverage.
- Introduce Testcontainers where appropriate.
- Dockerize the application.
- Configure CI/CD.
- Improve documentation.

### Phase 9 — Architecture and engineering review
- Review module boundaries.
- Evaluate dependencies.
- Assess maintainability.
- Identify unnecessary complexity.
- Refactor where justified.
- Document architectural decisions.

The first version was initially estimated at approximately 4–6 weeks, but this is an indicative estimate, not a deadline. Learning and understanding take priority.

# 7. Recommended development setup

The following setup is intended to provide continuity and a clear working environment.

## ChatGPT Project

Create a dedicated ChatGPT Project named:

**Java & Spring Boot Engineering Development**

Keep the following material there:
- This handoff document.
- Project requirements and decisions.
- Architecture decisions.
- Learning assessments.
- Important explanations and notes.
- Progress summaries.

The purpose is to maintain a consistent mentoring context throughout the project.

## Development environment

**IntelliJ IDEA**
- Main development environment.
- Use its debugging, navigation and refactoring capabilities.
- Avoid relying on automatic code generation without understanding the result.

**GitHub**
- Store the source code.
- Use meaningful commits.
- Track tasks and issues.
- Keep a README and a learning log.

**Official documentation**
- Java documentation.
- Spring Boot documentation.
- PostgreSQL documentation.
- Relevant library documentation.

We will select the specific documentation when a topic becomes relevant. You should not need to spend time searching for and comparing numerous courses and tutorials.

## Learning log

Create a `LEARNING_LOG.md` file in the repository.

For each meaningful milestone, record:

- What was implemented.
- What concepts were learned.
- What is now understood.
- What remains unclear.
- What mistakes were made.
- What important decisions were taken.
- What should be remembered for the next implementation.

This is important: we will measure learning progress, not just application progress.

## ChatGPT Plus and Codex

The recommendation discussed was:

**ChatGPT Plus:** Recommended if affordable and if the additional usage limits and capabilities are useful for sustained mentoring. Free is sufficient to start, but usage limits may interrupt longer learning sessions. Pro is not considered necessary at this stage.

**Codex:** Useful as a supplementary coding agent, not as the primary developer of this learning project.

We can progressively use Codex for:
- Independent code reviews.
- Identifying potential bugs.
- Suggesting missing tests.
- Challenging architecture decisions.
- Reviewing refactoring proposals.
- Repetitive tasks.

We should avoid asking Codex to implement entire features or solve every coding problem. That would risk reproducing the old habit of copying working code without fully understanding it.

The main learning loop remains between you and the mentor: reason, implement, explain, review and improve.

# 8. Working methodology and mentoring approach

This section is particularly important.

The project should be conducted as a practical mentorship, not as a sequence of tutorials or code-generation requests.

## The learning cycle

For each meaningful feature or technical topic, we will follow this process:

### 1. Understand
Start with the business problem and requirements.

Clarify what needs to be achieved and why.

### 2. Reason
Before writing code, discuss possible solutions.

You should have the opportunity to propose an approach, explain assumptions and identify uncertainties.

I will challenge your reasoning and help you evaluate alternatives.

### 3. Practise
You implement the solution yourself.

I will provide guidance, hints and explanations incrementally. I should not immediately give you the complete implementation.

If you get stuck, we will investigate the problem together rather than simply replacing your code with a solution.

### 4. Review
Once the implementation works, we examine it critically.

Questions may include:
- Why does this implementation work?
- What responsibilities does each component have?
- Could this be simpler?
- What alternatives exist?
- What happens in exceptional situations?
- How should it be tested?
- What are the trade-offs?
- Would this design remain maintainable as requirements evolve?

### 5. Reflect
Consolidate the learning.

Summarize:
- What you understood.
- What you can now explain independently.
- What remains uncertain.
- What you would do differently next time.

### 6. Apply
Use the concepts again in a different context.

The objective is to build transferable engineering knowledge, not memorize one implementation.

## Mentoring principles

**Incremental guidance**

One meaningful task at a time. Avoid overwhelming the process with too many concepts or activities.

**Socratic questioning**

I should ask you to reason about a problem before revealing the answer when appropriate.

**Honest feedback**

I should challenge incorrect assumptions and identify weaknesses clearly. Encouragement should not replace technical accuracy.

**No unnecessary complexity**

We should avoid overengineering, premature abstractions and applying patterns simply because they exist.

**Understanding over speed**

A small feature that you understand deeply is more valuable than several features implemented without understanding.

**Relevant theory at the right moment**

We will explain concepts when they become useful in the implementation, supported by focused exercises where necessary.

**Progress visibility**

We will periodically review your understanding and compare it with the initial assessment.

**No resource overload**

I will select relevant resources and documentation when needed. You should not have to continuously search for the best course, tutorial or learning path.

## What I should avoid as your mentor

- Giving complete solutions too early.
- Moving to the next topic before the current one is understood.
- Introducing several unrelated concepts at once.
- Treating a working implementation as proof of understanding.
- Making the architecture unnecessarily sophisticated.
- Turning the project into passive video-course consumption.
- Creating elaborate plans that delay actual implementation.

# 9. Definition of success

Success is not simply finishing the application.

By the end of the project, you should be increasingly able to:

- Design and implement a Spring Boot feature independently.
- Explain the Java concepts used in your implementation.
- Model a business domain and its rules.
- Design and query a relational database.
- Build and test REST APIs.
- Understand the role of Spring components and the persistence layer.
- Write meaningful unit and integration tests.
- Explain architectural decisions and trade-offs.
- Identify and improve code-quality problems.
- Work through unfamiliar technical problems methodically.

The project should also provide a credible portfolio example that you can discuss during technical interviews.

# 10. Immediate next step

We will not start by generating the entire application or configuring every technology.

The first step is the **Java foundations baseline assessment**.

We will work through small practical exercises, one at a time. I will evaluate your reasoning and understanding, not just whether the code compiles.

Once we have a reasonable baseline, we will move into the domain modelling of the Client Onboarding Management API and begin the first vertical slice.

**The guiding principle for the entire project:**

*Engage → Understand → Practise → Reflect → Experience progress.*

