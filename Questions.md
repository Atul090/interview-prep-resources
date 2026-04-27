# Mock Technical Interview – Atul Deep Singh

## Format
- Real interview simulation
- One question at a time
- Follow-ups and deep dives expected
- Focus: Backend, System Design, Real-world experience

---

# ROUND 1: INTRODUCTION

**Interviewer:**
Hey Atul, thanks for joining.

### Question 1:
Walk me through your experience so far. Focus on:
- What you’ve built
- Your role and ownership
- The most impactful system you worked on

**Constraints:**
- Max 2 minutes
- No generic statements
- Use numbers, scale, impact

---

# ROUND 2: PROJECT DEEP DIVE (SHOPIFY INTEGRATION)

### Question 2:
You mentioned leading the Shopify Order Integration Project.

Explain the architecture end-to-end:
- How do orders flow from Shopify to your system?
- What services are involved?
- Where does RabbitMQ fit?

### Question 3 (Follow-up):
Why did you choose RabbitMQ over a direct API-based approach?

### Question 4:
What challenges did you face in this system?

### Question 5:
How did you ensure reliability in order processing?

---

# ROUND 3: DISTANCE CALCULATION API

### Question 6:
Explain how your Distance Calculation API works.

### Question 7:
Did you use Haversine formula or something else?

### Question 8:
How did you optimize performance for multiple store lookups?

### Question 9 (Scaling):
If stores increase from 100 → 10,000, how would you scale this system?

---

# ROUND 4: MONGODB OPTIMIZATION

### Question 10:
You mentioned reducing query time by 30%.

- What was slow?
- What changes did you make?

### Question 11:
Explain your indexing strategy.

### Question 12:
How do you decide between embedding vs referencing?

### Question 13:
How do you debug a slow MongoDB query?

---

# ROUND 5: SEMANTIC SEARCH (CRITICAL)

### Question 14:
Explain your semantic search pipeline step by step:
- Data ingestion
- Embedding generation
- Storage
- Query handling

### Question 15:
How do you compute similarity?

### Question 16:
Why use semantic search over keyword search?

### Question 17:
What are trade-offs (latency, cost, accuracy)?

### Question 18:
How would you scale this system?

---

# ROUND 6: NODE.JS & BACKEND FUNDAMENTALS

### Question 19:
Explain how Node.js handles concurrency.

### Question 20:
Explain event loop in detail.

### Question 21:
What are microtasks vs macrotasks?

### Question 22:
What causes event loop blocking?

### Question 23:
How do you debug performance issues in Node?

---

# ROUND 7: GRAPHQL

### Question 24:
GraphQL vs REST — when would you use each?

### Question 25:
What is the N+1 problem?

### Question 26:
How does DataLoader solve it?

### Question 27:
How do you secure a GraphQL API?

---

# ROUND 8: RABBITMQ & ASYNC SYSTEMS

### Question 28:
Explain how RabbitMQ works internally.

### Question 29:
What happens if a consumer crashes?

### Question 30:
How do you ensure message reliability?

### Question 31:
What is a dead letter queue?

### Question 32:
How do you prevent duplicate processing?

---

# ROUND 9: SYSTEM DESIGN

### Question 33:
Design a scalable e-commerce order system.

### Question 34:
How would you handle inventory consistency?

### Question 35:
How do you prevent double payments?

### Question 36:
What is idempotency?

### Question 37:
How do you design a real-time notification system?

---

# ROUND 10: AWS & SCALABILITY

### Question 38:
Explain your usage of AWS services.

### Question 39:
EC2 vs Lambda — when to use what?

### Question 40:
How do you design a scalable backend on AWS?

### Question 41:
What is load balancing?

---

# ROUND 11: DSA / PROBLEM SOLVING

### Question 42:
Given transactions (userId, amount), find top K users.

### Question 43:
How would you optimize this?

### Question 44:
What data structures would you use?

---

# ROUND 12: DEBUGGING & REAL-WORLD THINKING

### Question 45:
API latency suddenly increased — how do you debug?

### Question 46:
Database CPU spikes — what steps?

### Question 47:
Queue backlog increasing — what do you check?

### Question 48:
Search accuracy dropped — what could be wrong?

---

# ROUND 13: BEHAVIORAL

### Question 49:
Tell me about a challenging production issue.

### Question 50:
Tell me about a disagreement with a teammate.

### Question 51:
How do you handle pressure?

### Question 52:
What motivates you?

---

# ROUND 14: CLOSING

### Question 53:
What would you improve in your current system if given time?

### Question 54:
Where do you see yourself in 2–3 years?

---

# NOTES FOR PRACTICE

## How to Answer
Use this structure:

**1. Context**  
**2. Problem**  
**3. Approach**  
**4. Trade-offs**  
**5. Result (metrics if possible)**

---

## What Interviewers Evaluate

- Depth of understanding
- Real-world thinking
- Trade-off awareness
- Communication clarity
- Ownership mindset

---

## Practice Strategy

- Answer aloud (not in your head)
- Record yourself
- Refine answers
- Focus on clarity > complexity

---
