# Outline

A comprehensive overview of engineering roles, responsibilities, tech stack, and best practices for building modern, scalable systems.

---

## Table of Contents

1. [Frontend & UI](#frontend--ui)
2. [Cart & Checkout](#cart--checkout)
3. [AFCC (Apply for Circle Card)](#afcc-apply-for-circle-card)
4. [Engineering Roles](#engineering-roles)
    - [Lead Java Developer](#lead-java-developer)
    - [Lead Engineer](#lead-engineer)
    - [Fullstack Lead Engineer](#lead-engineer---fullstack)
    - [Backend Lead Engineer](#lead-engineer---backend)
5. [Tech Stack](#tech-stack)
6. [CI/CD & DevOps](#cicd--devops)
7. [Metrics & Visualization](#metrics--visualizations)
8. [Cloud & Compute Platforms](#cloud--compute-platforms)
9. [Best Practices & Culture](#best-practices--culture)
10. [References & Useful Links](#references--useful-links)

---

## Frontend & UI

- **Tech Focus:** [React.js](https://react.dev/), [HTML5](https://developer.mozilla.org/en-US/docs/Web/Guide/HTML/HTML5), [CSS3](https://developer.mozilla.org/en-US/docs/Web/CSS), [JavaScript (ES6+)](https://developer.mozilla.org/en-US/docs/Web/JavaScript), Micro Frontend Architecture.
- **State Management & Build Tools:** [Redux](https://redux.js.org/), [Webpack](https://webpack.js.org/), [Babel](https://babeljs.io/).
- **Getting Started: (IN PROGRESS**)**
    1. Clone the repo: `git clone https://github.com/jlabclouds/outline.git` **
    2. Install dependencies: `npm install` **
    3. Start development server: `npm start` **
    4. Explore micro frontend modules under `/src/microfrontends` **
    5. See [React Docs](https://react.dev/) for component patterns

---

## Cart & Checkout

- **Scope:** Online, brick-and-mortar, Shipt, Google Express; **critical impact on guest experience**
- **Languages:** [Kotlin](https://kotlinlang.org/), Groovy, JAM
- **Frameworks:** [Micronaut](https://micronaut.io/), [Ratpack](https://ratpack.io/)
- **Databases:** [Postgres](https://www.postgresql.org/), [Cassandra](https://cassandra.apache.org/)
- **Events:** [Kafka](https://kafka.apache.org/)
- **Architecture:** Microservices, multi-tenant
- **Deployment Steps:**
    1. **Build Service Module**
    ```bash
    ./gradlew build
    ```
    2. **Run Database Migrations**
    ```bash
    flyway migrate
    ```
    3. Deploy via CI/CD (see [CI/CD & DevOps](#cicd--devops))
    4. Monitor events with Kafka dashboard

**Example: Kotlin Service Endpoint**
```kotlin
@Get("/cart")
fun getCart(): HttpResponse<Cart> = HttpResponse.ok(cartService.fetchCart())
```

---

## AFCC (Apply for Circle Card)

- **Purpose:** Evaluates viability, maintainability, financials, forecasting, lifecycle management, and total cost of ownership of services.
- **How it works:**  
  1. Submit service details via AFCC portal.
  2. Automated evaluation pipeline checks core criteria.
  3. Output includes lifecycle, cost, and maintainability score.
- **Learn more:** [Service Evaluation Best Practices](https://martinfowler.com/bliki/EvaluationCriteria.html)

---

## Engineering Roles

### Lead Java Developer

- **Experience:** Java/J2EE, Kotlin, SQL/NoSQL (Postgres, MongoDB, Cassandra, Graph DB), Python, Ruby, [Chef](https://www.chef.io/), [Drone](https://drone.io/), Kubernetes containers, Cloud tech.
- **Lifecycle:** At least one full-cycle implementation of a major project.

### Lead Engineer

- **Responsibilities:**
    - [Envoy](https://www.envoyproxy.io/) & [HAProxy](https://www.haproxy.org/) API Gateway management
    - Sidecar Proxy Dev (Go)
    - Server Fleet Management: [Ansible](https://www.ansible.com/)
    - Control Plane: Go, Kafka, Redis/MongoDB
    - CDN Strategy & Migration: [Akamai](https://www.akamai.com/), [Fastly](https://www.fastly.com/)
    - API Monitoring & Security: Implement solutions/tools
- **Focus:** API gateways and microservice Kubernetes architectures, JVM-based services, high observability.

**Example: API Gateway Config (Envoy)**
```yaml
static_resources:
  listeners:
  - name: listener_0
    address:
      socket_address: { address: 0.0.0.0, port_value: 8080 }
    filter_chains:
    - filters:
      - name: envoy.filters.network.http_connection_manager
```

### Lead Engineer - Fullstack

- **Responsibilities:**
    - Lead scrum teams
    - [Java](https://www.java.com/), Kotlin, React, Spring Boot/Micronaut
    - Build highly scalable distributed systems
    - Deep knowledge of domain and product features

### Lead Engineer - Backend

- **Responsibilities:**
    - Featurestore, Model ops, experimentation, monitoring, explainability, continuous improvement
    - GCP, MLOps, scalable APIs, ML pipelines
    - Deploy and monitor ML models in production

---

## Tech Stack

- **Languages & Frameworks:** Kotlin, Java, Groovy, [Spring Boot](https://spring.io/projects/spring-boot), Micronaut, [http4k](https://www.http4k.org/), [KTOR](https://ktor.io/), Gradle, JavaScript, TypeScript, ReactJS, Junit, Spock, KotlinTest
- **Event Streaming:** Kafka
- **Databases:** Postgres, Cassandra, MongoDB, RocksDB, InfluxDB, ELK Stack, Exadata
- **ML & Data:** [Vertex AI](https://cloud.google.com/vertex-ai), BigQueryML, Kubeflow, Cloud Composer, FastAPI, Flask

**Example: Spring Boot Application**
```java
@SpringBootApplication
public class Application {
    public static void main(String[] args) {
        SpringApplication.run(Application.class, args);
    }
}
```

---

## CI/CD & DevOps

- **Code Pipelines:** Docker, Drone, [Vela](https://github.com/go-vela/vela)
- **DevOps Tools:** Jenkins, Git, Kubernetes
- **Steps:**
    1. Push code to repo
    2. Automated build/test via CI pipeline
    3. Container deploy to Kubernetes
    4. Monitoring via dashboards (see below)
 
**Example: Drone CI Pipeline**
```yaml
pipeline:
  build:
    image: gradle:latest
    commands:
      - ./gradlew build
```

---

## Metrics & Visualizations

- **Dashboards:** [Grafana](https://grafana.com/)
- **Log Aggregation:** Logstash, Kibana
- **Steps:**
    1. Set up Grafana dashboard
       - Connect to data sources for metrics.
    2. Aggregate logs with Logstash & Kibana (ELK Stack).
       - [ELK Stack](https://www.elastic.co/what-is/elk-stack)
    4. Monitor system health and alerting
       - Configure alerting rules.

**Example: Grafana Dashboard JSON**
```json
{
  "dashboard": {
    "title": "System Metrics",
    "panels": [{ "type": "graph", "targets": [{ "expr": "cpu_usage" }] }]
  }
}
```

---

## Cloud & Compute Platforms

- **Cloud:** [Google Cloud Platform (GCP)](https://cloud.google.com/)
- **Elastic Compute:** [Kubernetes](https://kubernetes.io/)

**Example: Kubernetes Deployment**
```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: my-app
spec:
  replicas: 3
  template:
    spec:
      containers:
      - name: app
        image: my-app:latest
```

---

## Best Practices & Culture

- **Values:** Diversity, inclusion, collaboration
- **Architecture:** Distributed microservices, Kubernetes, event-based (Kafka), CI/CD pipelines
- **Automation:** Everything-as-code, operational excellence, canary/A/B testing, high observability/logs/metrics
- **Approach:** Proactive issue triage, edge computing, elastic infrastructure, agile ceremonies
- **Learning:** Experiment with new tech, continuous improvement

**Example: Canary Deployment Annotation**
```yaml
metadata:
  annotations:
    deploymentstrategy: canary
```

---

## References & Useful Links

- [React Documentation](https://react.dev/)
- [Kotlin Documentation](https://kotlinlang.org/docs/home.html)
- [Spring Boot Guides](https://spring.io/guides)
- [Micronaut Guides](https://guides.micronaut.io/)
- [Kafka Introduction](https://kafka.apache.org/documentation/)
- [Kubernetes Concepts](https://kubernetes.io/docs/concepts/)
- [Google Cloud Documentation](https://cloud.google.com/docs)
- [Grafana Tutorials](https://grafana.com/tutorials/)
- [CI/CD Best Practices](https://martinfowler.com/bliki/ContinuousDelivery.html)

---

**For more details, see respective module directories and check the project wiki.**
