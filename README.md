# software-construction-microservices


##How Netflix uses Microservices?

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



##Companies that moved to microservices and had to go back to Monolithic and why?
