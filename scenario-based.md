
# 🚀 Atul Deep Singh — Scenario-Based Interview Question Bank

---

# 🧠 SECTION 1: Real-World Backend Scenarios

### Scenario 1: API Latency Spike
Your production API latency suddenly increased from 200ms → 2s.

👉 Questions:
- How would you debug this step by step?
- What metrics/logs would you check first?
- How do you isolate whether the issue is DB, code, or network?
- How would you fix it and prevent recurrence?

---

### Scenario 2: High Traffic Spike
Your system suddenly gets 10x traffic during a sale.

👉 Questions:
- What breaks first?
- How would you scale your Node.js backend?
- How would you use caching here?
- What AWS components would you introduce?

---

### Scenario 3: API Rate Limiting
A public API is being abused.

👉 Questions:
- How do you implement rate limiting?
- Where would you implement it (gateway vs app)?
- How do you handle distributed rate limiting?

---

# 🗄️ SECTION 2: Database Scenarios (MongoDB)

### Scenario 4: Slow Queries
A critical query takes 5 seconds.

👉 Questions:
- How do you debug it?
- What role do indexes play?
- How do you analyze query plans?
- What schema changes might help?

---

### Scenario 5: Scaling Database
Your data grows from 1M → 100M records.

👉 Questions:
- How do you redesign your schema?
- Would you shard? Why?
- What challenges come with sharding?

---

### Scenario 6: Data Consistency Issue
Two services update the same document simultaneously.

👉 Questions:
- What problems can arise?
- How do you handle concurrency?
- Would you use transactions?

---

# 🔎 SECTION 3: Semantic Search Scenarios

### Scenario 7: Search Accuracy Drops
Users complain that search results are irrelevant.

👉 Questions:
- What could be wrong in your pipeline?
- How would you debug embeddings?
- How do you evaluate search quality?

---

### Scenario 8: Scaling Search
Your search system needs to handle 100x more queries.

👉 Questions:
- How do you scale Elasticsearch?
- Would you cache results?
- Would you change architecture?

---

### Scenario 9: Cost vs Performance Trade-off
Embedding generation cost becomes too high.

👉 Questions:
- How do you optimize?
- Batch vs real-time embeddings?
- Would you reduce vector size?

---

# 📡 SECTION 4: Messaging (RabbitMQ)

### Scenario 10: Queue Backlog
Messages are piling up in RabbitMQ.

👉 Questions:
- What could be causing this?
- How do you scale consumers?
- How do you monitor queues?

---

### Scenario 11: Message Loss
Orders are occasionally lost.

👉 Questions:
- Where could failure occur?
- How do you ensure reliability?
- What is acknowledgment strategy?

---

### Scenario 12: Duplicate Processing
Same message is processed twice.

👉 Questions:
- Why does this happen?
- How do you make consumers idempotent?

---

# ⚙️ SECTION 5: Node.js Scenarios

### Scenario 13: Event Loop Blocking
Your server becomes unresponsive under load.

👉 Questions:
- What causes event loop blocking?
- How do you detect it?
- How do you fix it?

---

### Scenario 14: Memory Leak
Memory usage keeps increasing.

👉 Questions:
- How do you debug this?
- What tools would you use?
- Common causes in Node.js?

---

### Scenario 15: CPU Spike
CPU usage hits 100%.

👉 Questions:
- How do you investigate?
- Would you use clustering?

---

# 🧱 SECTION 6: System Design Scenarios

### Scenario 16: Design E-commerce Checkout
Design a checkout system like HUFT.

👉 Questions:
- How do you handle payments?
- How do you ensure consistency?
- How do you prevent double orders?

---

### Scenario 17: Real-Time Notifications
Design a system for order updates.

👉 Questions:
- WebSockets vs polling?
- How do you scale?
- How do you handle failures?

---

### Scenario 18: Caching Strategy
Your system is DB-heavy.

👉 Questions:
- Where do you cache?
- What do you cache?
- How do you invalidate cache?

---

# ☁️ SECTION 7: AWS Scenarios

### Scenario 19: Scaling Backend
You need to serve millions of users.

👉 Questions:
- What AWS services would you use?
- How do you design load balancing?
- How do you ensure fault tolerance?

---

### Scenario 20: Deployment Failure
A deployment breaks production.

👉 Questions:
- How do you rollback?
- What deployment strategies exist?

---

### Scenario 21: Cost Optimization
AWS bill spikes unexpectedly.

👉 Questions:
- How do you analyze costs?
- What optimizations would you apply?

---

# 🧪 SECTION 8: Testing Scenarios

### Scenario 22: Flaky Tests
Tests fail randomly.

👉 Questions:
- Why does this happen?
- How do you fix it?

---

### Scenario 23: Regression Bug
A bug reappears after deployment.

👉 Questions:
- What testing gap exists?
- How do you prevent this?

---

# 🔐 SECTION 9: Security Scenarios

### Scenario 24: API Exploited
Users exploit your API.

👉 Questions:
- What vulnerabilities could exist?
- How do you secure endpoints?

---

### Scenario 25: Authentication Issue
Users report unauthorized access.

👉 Questions:
- What could be wrong with JWT?
- How do you fix it?

---

# 🧠 SECTION 10: Behavioral + Ownership

### Scenario 26: Production Outage
System goes down at night.

👉 Questions:
- What do you do first?
- How do you communicate?

---

### Scenario 27: Team Conflict
Disagreement on architecture.

👉 Questions:
- How do you handle it?
- How do you justify your approach?

---

### Scenario 28: Tight Deadline
Feature must be shipped quickly.

👉 Questions:
- What trade-offs do you make?
- How do you ensure quality?

---

# 💀 SECTION 11: Edge Case Thinking

### Scenario 29: Payment Double Charge
User is charged twice.

👉 Questions:
- What went wrong?
- How do you prevent this?

---

### Scenario 30: Cache Stale Data
Users see outdated info.

👉 Questions:
- Why does this happen?
- How do you fix cache invalidation?

---

### Scenario 31: Third-Party Failure
External API is down.

👉 Questions:
- How do you handle fallback?
- Do you retry?

---

# 🎯 HOW TO PRACTICE

## Answer Framework

1. Understand problem  
2. Identify root causes  
3. Propose solution  
4. Discuss trade-offs  
5. Suggest improvements  

---

# ⚠️ WHAT INTERVIEWERS LOOK FOR

- Structured thinking
- Real-world debugging ability
- Trade-off awareness
- Ownership mindset

---

# 🚀 FINAL NOTE

If you can confidently answer these scenarios:

👉 You’re already ahead of ~80% candidates

---
