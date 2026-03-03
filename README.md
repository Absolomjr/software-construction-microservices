# software-construction-microservices


Netflix is one of the world’s largest streaming platforms, serving millions of users globally. To support massive scale, high availability, and continuous innovation, Netflix uses a **microservices architecture** instead of a traditional monolithic system.

## Why Netflix Moved to Microservices

Originally, Netflix ran a monolithic application hosted in its own data centers. However, as the platform grew, several challenges emerged:

1. **Scalability Issues** – The monolith could not easily handle rapid growth in users and streaming demand.
2. **Single Point of Failure** – A failure in one part of the system could affect the entire platform.
3. **Slow Deployment** – Small updates required redeploying the whole application.
4. **Limited Agility** – Multiple teams working on the same codebase caused bottlenecks.

After a major database outage in 2008, Netflix decided to redesign its architecture and migrated to cloud infrastructure (notably AWS) and adopted microservices to improve resilience and scalability.

## How Microservices Operate at Netflix

### 1. Service-Based Architecture

Netflix breaks its system into **hundreds (even thousands) of small, independent services**, each responsible for a specific function. Examples include:

* User authentication service
* Recommendation service
* Billing service
* Streaming service
* Content catalog service
  
Each microservice: Runs independently,has its own database (in most cases),Can be deployed separately and Can scale independently


### 2. API Communication

Microservices communicate through lightweight APIs (mostly RESTful APIs and sometimes messaging systems).

For example:

* When you log in → the Authentication Service verifies credentials.
* When you open the homepage → the Recommendation Service fetches personalized content.
* When you click play → the Streaming Service delivers video content via CDN.

Each service talks to others without tightly coupling the entire system.

### 3. Cloud & Auto-Scaling

Netflix runs its microservices in the cloud using auto-scaling:

* If traffic increases (e.g., new season release), services automatically scale up.
* If traffic drops, resources scale down to reduce cost.

This ensures performance even with millions of concurrent users worldwide.


### 4. Fault Tolerance & Resilience

Netflix designs microservices to **fail gracefully**:

* If the Recommendation Service fails, users can still browse content.
* Circuit breakers prevent cascading failures.
* Services are isolated so one failure doesn’t crash the entire platform.

This improves system reliability.


### 5. Continuous Deployment

Each team owns specific microservices and can:

* Develop independently
* Deploy updates independently
* Experiment safely

This enables fast innovation and frequent feature releases.



## Companies that moved to microservices and had to go back to Monolithic and why?
Many companies adopted microservices for scalability and agility, but some later reverted to monolithic (or more centralized) architectures because microservices introduced excessive complexity, cost, and operational overhead.

Here are notable examples:

### 1. Amazon (Some Internal Teams)

Although Amazon is famous for pioneering microservices, some internal teams have moved certain systems back toward modular monoliths.

**Why?**

Too many small services created high operational complexity

Increased network latency due to excessive service-to-service calls

Difficult debugging across distributed systems

Higher infrastructure and DevOps costs

Lesson:

Microservices work at massive scale, but not every subsystem needs to be distributed. Some services were merged for simplicity and performance.

### 2. Segment

Segment initially adopted microservices but later consolidated parts of their system.

**Why?**

Complex distributed system debugging

Operational burden managing many services

Slower developer productivity

Coordination challenges between teams

They found that for their size and workload at the time, microservices added more problems than benefits.

### 3. InVision

InVision publicly discussed architectural simplification efforts.

**Why?**

Microservices required heavy DevOps investment

High infrastructure cost

System became harder to reason about

Communication overhead between services

They moved toward consolidation to reduce engineering overhead.

### 4. Shopify (Selective Consolidation)

Shopify experimented with microservices but maintains large modular components.

**Why?**

Too many services caused latency

Deployment coordination complexity

Data consistency issues

They favor a “modular monolith” approach for many core systems while using microservices where truly needed.

## Why Companies Go Back to Monoliths

Common reasons include:

### 1. Over-Engineering

Microservices were adopted too early without real scaling needs.

### 2. Operational Complexity

Service discovery

Distributed tracing

Monitoring

CI/CD for dozens or hundreds of services

Requires strong DevOps maturity.

### 3. Network Latency

Inter-service communication over the network is slower than in-process function calls.

### 4. Higher Costs

More servers, containers, orchestration tools (e.g., Kubernetes), monitoring systems.

### 5. Harder Debugging

Tracing a single user request across 10–20 services is difficult.
