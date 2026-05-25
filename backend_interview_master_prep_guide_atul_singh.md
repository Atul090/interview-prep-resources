# Backend Interview Master Preparation Guide

Prepared for: Atul Deep Singh
Experience: Backend Software Engineer
Primary Stack: Node.js, Express.js, MongoDB, GraphQL, Docker, WebSockets, AWS

---

# Table of Contents

1. Introduction
2. Node.js Internals
3. Event Loop
4. process.nextTick vs setImmediate
5. Synchronous vs Asynchronous
6. Blocking vs Non-blocking
7. Express.js
8. Middleware
9. Authentication vs Authorization
10. JWT Deep Dive
11. CORS
12. REST vs GraphQL
13. GraphQL Deep Dive
14. MongoDB
15. Indexing
16. Aggregation Pipelines
17. Replication and Sharding
18. Database Design
19. Docker
20. RabbitMQ and Queues
21. WebSockets
22. Scalability and System Design
23. Security
24. Data Structures and Algorithms
25. Production-Level Coding Questions
26. Behavioral Questions
27. Questions to Ask Interviewer
28. Advanced Backend Questions

---

# 1. Introduction

## Strong Introduction

Hi, I’m Atul Deep Singh. I’m currently working as a Software Engineer at Heads Up For Tails where I primarily work on backend development using Node.js, Express.js, MongoDB, GraphQL, and AWS services.

I have worked on Shopify order integrations, personalization systems, backend optimization, authentication systems, and scalable APIs. One of the key improvements I worked on was optimizing MongoDB queries and backend flows which improved response times by around 30%.

I’m particularly interested in backend architecture, distributed systems, scalability, asynchronous systems, and performance optimization. Recently, I’ve also explored WebSockets, semantic search, queue systems, and AI-based applications.

---

# 2. Node.js Internals

## How does Node.js work internally?

Node.js runs on Chrome’s V8 JavaScript engine.

It uses:
- Single-threaded event loop
- Non-blocking I/O
- Asynchronous programming model

Instead of creating one thread per request like traditional servers, Node.js delegates expensive operations like:
- File system operations
- Database access
- Network requests
- DNS operations

to:
- OS kernel
- libuv thread pool

Once the operation finishes, callbacks/promises are pushed into the event loop queue.

This allows Node.js to efficiently handle thousands of concurrent requests.

---

## Why is Node.js scalable despite being single-threaded?

Node.js is scalable because:

- Most backend operations are I/O-bound
- Non-blocking architecture avoids waiting
- Event loop efficiently handles concurrency
- No thread creation overhead per request

This makes Node.js excellent for:
- APIs
- Real-time systems
- Streaming
- Chat systems
- E-commerce backends

---

## What is libuv?

libuv is a C library used by Node.js.

It handles:
- Event loop
- Thread pool
- Async I/O operations
- Networking
- File system operations

---

## What operations use thread pool?

Thread pool handles:
- File system operations
- DNS lookup
- Crypto operations
- Compression

Default thread pool size:

```bash
4
```

Can be increased using:

```bash
UV_THREADPOOL_SIZE
```

---

# 3. Event Loop

## What is Event Loop?

The event loop is the mechanism that allows Node.js to handle asynchronous operations.

It continuously checks:
- Call stack
- Callback queue
- Microtask queue

and executes tasks.

---

## Event Loop Phases

```text
Timers
↓
Pending callbacks
↓
Idle/Prepare
↓
Poll
↓
Check
↓
Close callbacks
```

---

## Microtask Queue

Higher priority queue.

Contains:
- Promise callbacks
- process.nextTick

Microtasks execute before moving to next event loop phase.

---

## Example

```js
setTimeout(() => console.log("timeout"), 0);

setImmediate(() => console.log("immediate"));

Promise.resolve().then(() => console.log("promise"));

process.nextTick(() => console.log("nextTick"));
```

Output:

```text
nextTick
promise
timeout/immediate
```

---

# 4. process.nextTick vs setImmediate

| process.nextTick | setImmediate |
|---|---|
| Executes immediately after current operation | Executes during check phase |
| Higher priority | Lower priority |
| Part of microtask queue | Part of event loop |

---

## Strong Answer

process.nextTick executes before the event loop continues to the next phase, while setImmediate executes in the check phase.

Excessive use of process.nextTick can starve the event loop.

---

# 5. Synchronous vs Asynchronous

| Synchronous | Asynchronous |
|---|---|
| Sequential execution | Parallel waiting |
| Blocking | Non-blocking |
| Slower concurrency | Better scalability |

---

## Example

### Synchronous

```js
const data = fs.readFileSync("file.txt");
console.log(data);
```

---

### Asynchronous

```js
fs.readFile("file.txt", (err, data) => {
   console.log(data);
});
```

---

# 6. Blocking vs Non-blocking

## Blocking

Execution waits until operation completes.

Example:

```js
fs.readFileSync();
```

---

## Non-blocking

Execution continues without waiting.

Example:

```js
fs.readFile();
```

---

# 7. Express.js

## What is Express.js?

Express.js is a lightweight Node.js framework built on top of Node’s HTTP module.

It simplifies:
- Routing
- Middleware
- Request handling
- Response handling
- API development

---

## Basic Express Server

```js
const express = require("express");

const app = express();

app.use(express.json());

app.get("/", (req, res) => {
   res.send("Hello World");
});

app.listen(3000, () => {
   console.log("Server started");
});
```

---

## Request Lifecycle

```text
Request
↓
Middleware
↓
Route Handler
↓
Response
```

---

## app.use vs app.get

| app.use | app.get |
|---|---|
| Middleware | GET route |
| Handles all methods | Only GET |

---

# 8. Middleware

## What is Middleware?

Middleware are functions executed during request-response lifecycle.

Uses:
- Authentication
- Logging
- Validation
- Error handling
- Parsing body

---

## Middleware Example

```js
app.use((req, res, next) => {
   console.log(req.url);
   next();
});
```

---

## Types of Middleware

- Application middleware
- Router middleware
- Error middleware
- Third-party middleware
- Built-in middleware

---

## Error Middleware

```js
app.use((err, req, res, next) => {
   res.status(500).json({
      error: err.message
   });
});
```

---

## Why Middleware Order Matters?

Middleware executes sequentially.

If authentication middleware is placed after routes, protected routes may become publicly accessible.

---

# 9. Authentication vs Authorization

| Authentication | Authorization |
|---|---|
| Verifies identity | Verifies permissions |
| Login | Access control |
| Who are you? | What can you access? |

---

## Example

### Authentication

User logs in using email/password.

### Authorization

Admin can delete products while normal users cannot.

---

# 10. JWT Deep Dive

## What is JWT?

JWT stands for JSON Web Token.

It is a stateless authentication mechanism.

---

## JWT Structure

```text
HEADER.PAYLOAD.SIGNATURE
```

---

## JWT Flow

### Step 1
User logs in.

### Step 2
Server verifies credentials.

### Step 3
Server generates token.

```js
jwt.sign(payload, secret)
```

### Step 4
Client stores token.

### Step 5
Client sends token.

```text
Authorization: Bearer TOKEN
```

### Step 6
Server verifies token.

```js
jwt.verify(token, secret)
```

---

## Why JWT is Stateless?

Server does not store session data.

All required information exists inside token.

---

## Drawbacks of JWT

- Difficult revocation
- Token leakage risks
- Large token size
- Refresh token complexity

---

## Where Should JWT Be Stored?

Preferred:

```text
HttpOnly Secure Cookies
```

because:
- safer against XSS attacks

---

## What is Refresh Token?

Long-lived token used to generate new access tokens.

---

## What if JWT Secret Leaks?

Immediate actions:
- Rotate secrets
- Force re-login
- Invalidate tokens
- Monitor suspicious activity

---

# 11. CORS

## What is CORS?

CORS stands for Cross-Origin Resource Sharing.

Browser security mechanism restricting requests across different origins.

---

## Example

```text
Frontend → localhost:3000
Backend → localhost:5000
```

Different origins.

---

## Why CORS Exists?

To prevent malicious websites from accessing sensitive APIs.

---

## Enable CORS in Express

```js
const cors = require("cors");

app.use(cors());
```

---

## Specific Origin

```js
app.use(cors({
   origin: "https://example.com"
}));
```

---

## Preflight Request

Browser sends:

```text
OPTIONS
```

before:
- PUT
- DELETE
- custom headers

---

# 12. REST vs GraphQL

| REST | GraphQL |
|---|---|
| Multiple endpoints | Single endpoint |
| Fixed response | Flexible response |
| Overfetching possible | Exact data fetching |
| Easier caching | Complex caching |

---

## REST Example

```text
/users/1
/orders/1
```

---

## GraphQL Example

```graphql
{
   user(id: 1) {
      name
      orders {
         total
      }
   }
}
```

---

## When NOT to Use GraphQL?

REST may be better for:
- simple CRUD APIs
- public APIs
- highly cacheable APIs

---

# 13. GraphQL Deep Dive

## What is GraphQL?

GraphQL is a query language for APIs developed by Meta.

It allows clients to request only required data.

---

## What is Resolver?

Resolver is a function responsible for fetching data for a GraphQL field.

Example:

```js
const resolvers = {
   Query: {
      user: async (_, args) => {
         return await User.findById(args.id);
      }
   }
};
```

---

## Query vs Mutation

| Query | Mutation |
|---|---|
| Fetch data | Modify data |

---

## What is N+1 Problem?

When nested queries generate excessive DB calls.

Example:
- Fetch users
- Then fetch posts for every user separately

---

## Solution to N+1 Problem

Use:
- DataLoader
- batching
- caching

---

## How to Optimize GraphQL?

- Pagination
- Query depth limiting
- Caching
- Resolver optimization
- DataLoader batching

---

# 14. MongoDB

## Why MongoDB?

MongoDB is a NoSQL database.

Advantages:
- Flexible schema
- Easy horizontal scaling
- JSON-like documents
- Faster development iteration

---

## SQL vs NoSQL

| SQL | NoSQL |
|---|---|
| Structured schema | Flexible schema |
| Joins | Embedded documents |
| Vertical scaling | Horizontal scaling |
| ACID focus | Scalability focus |

---

## What is BSON?

Binary representation of JSON used internally by MongoDB.

---

# 15. Indexing

## What is Index?

Index is a special data structure improving query performance.

Without index:

```text
Full collection scan
O(n)
```

With index:

```text
B-Tree traversal
O(log n)
```

---

## How Index Works?

Database maintains sorted structure pointing to document locations.

MongoDB mainly uses:

```text
B-Tree indexes
```

---

## Create Index

```js
db.users.createIndex({ email: 1 });
```

---

## Compound Index

```js
db.orders.createIndex({
   userId: 1,
   createdAt: -1
});
```

---

## Left Prefix Rule

Index:

```js
{ name: 1, age: 1 }
```

Efficient for:
- name
- name + age

Not efficient for:
- only age

---

## Why Index Slows Writes?

Because insert/update operations must also update index structure.

---

## How to Find Slow Queries?

Using:
- explain()
- profiler
- execution stats
- monitoring dashboards

---

# 16. Aggregation Pipelines

## What are Aggregation Pipelines?

Aggregation pipelines process documents through multiple transformation stages.

---

## Example

```js
db.orders.aggregate([
   {
      $match: {
         status: "completed"
      }
   },
   {
      $group: {
         _id: "$userId",
         total: {
            $sum: "$amount"
         }
      }
   }
]);
```

---

## Common Stages

- $match
- $group
- $project
- $sort
- $lookup
- $limit
- $unwind

---

# 17. Replication and Sharding

## Replication

Replication creates multiple copies of data.

MongoDB architecture:

```text
Primary
↓
Secondary replicas
```

Benefits:
- High availability
- Failover support
- Backup safety

---

## Sharding

Horizontal scaling technique.

Data distributed across multiple servers.

Benefits:
- Handles huge datasets
- Better scalability
- Load distribution

---

# 18. Database Design

## Embedded Documents

Store related data together.

Good for:
- Read-heavy operations
- Small related datasets

---

## Referenced Documents

Store relationships separately.

Good for:
- Large scalable relations
- Reusable entities

---

## ACID Properties

| Property | Meaning |
|---|---|
| Atomicity | All or nothing |
| Consistency | Valid state maintained |
| Isolation | Transactions isolated |
| Durability | Data persists |

---

# 19. Docker

## What is Docker?

Docker is a containerization platform.

It packages:
- application
- dependencies
- runtime

inside containers.

---

## Docker Lifecycle

```text
Dockerfile
↓
Build Image
↓
Run Container
```

---

## Dockerfile Example

```dockerfile
FROM node:18

WORKDIR /app

COPY package*.json ./

RUN npm install

COPY . .

CMD ["npm", "start"]
```

---

## Difference Between Image and Container

| Image | Container |
|---|---|
| Blueprint | Running instance |

---

## Docker vs VM

| Docker | VM |
|---|---|
| Lightweight | Heavy |
| Shares host kernel | Separate OS |
| Faster startup | Slower |

---

## Docker Compose

Used for multi-container setup.

Example:
- backend
- mongodb
- redis
- nginx

---

# 20. RabbitMQ and Queues

## Why Use Queues?

Queues help:
- decouple services
- asynchronous processing
- retries
- reliability
- load smoothing

---

## RabbitMQ Use Cases

- Email sending
- Notifications
- Order processing
- Background jobs

---

## Queue vs Direct API Calls

| Queue | Direct API |
|---|---|
| Async | Immediate |
| Retry possible | Failure sensitive |
| Reliable | Tight coupling |

---

## What is Dead Letter Queue?

Failed messages after retries are moved to DLQ.

Used for:
- debugging
- recovery
- monitoring

---

# 21. WebSockets

## What are WebSockets?

WebSockets provide persistent full-duplex communication.

Unlike HTTP:
- no repeated connections
- real-time communication

---

## HTTP vs WebSocket

| HTTP | WebSocket |
|---|---|
| Request-response | Persistent connection |
| Stateless | Stateful |
| Repeated requests | Continuous connection |

---

## WebSocket Use Cases

- Chat apps
- Realtime notifications
- Live tracking
- Multiplayer games

---

## How to Authenticate WebSockets?

JWT validated during handshake.

---

# 22. Scalability and System Design

## How to Scale Backend?

Possible improvements:

- Horizontal scaling
- Load balancers
- Redis caching
- CDN
- Query optimization
- Queue systems
- Database indexing
- Sharding

---

## What is Load Balancer?

Distributes traffic across multiple servers.

Benefits:
- Better availability
- Prevent overload
- Improved scalability

---

## What is Redis?

In-memory datastore used for:
- caching
- sessions
- rate limiting
- pub/sub

---

## Why Use Caching?

Reduces:
- database load
- latency
- repeated computations

---

# 23. Security

## How to Secure APIs?

Use:
- JWT authentication
- HTTPS
- Helmet middleware
- Rate limiting
- Input validation
- Sanitization
- Role-based authorization

---

## What is Rate Limiting?

Restricts request count per IP/user within time window.

Protects against:
- abuse
- brute force attacks
- DDoS attacks

---

## What is SQL Injection?

Malicious SQL query injection.

Prevention:
- parameterized queries
- ORM
- validation

---

## What is NoSQL Injection?

Injecting malicious MongoDB operators.

Example:

```js
{ "$ne": null }
```

Prevention:
- validation
- sanitization
- schema enforcement

---

# 24. Data Structures and Algorithms

# Array vs ArrayList

| Array | ArrayList |
|---|---|
| Fixed size | Dynamic size |
| Faster | Flexible |
| Primitive support | Objects only |

---

## When to Use?

### Array
- fixed size
- performance critical

### ArrayList
- dynamic data
- resizing needed

---

# ArrayList vs LinkedList

| ArrayList | LinkedList |
|---|---|
| Dynamic array | Doubly linked list |
| Fast access | Slow access |
| Slow insertion middle | Faster insertion |

---

## ArrayList Insertion

Middle insertion:

```text
O(n)
```

because elements shift.

---

## LinkedList Insertion

If node reference known:

```text
O(1)
```

---

# Stack

## What is Stack?

LIFO data structure.

Operations:
- push
- pop
- peek

---

## Stack Implementation

```js
class Stack {
   constructor() {
      this.items = [];
   }

   push(item) {
      this.items.push(item);
   }

   pop() {
      return this.items.pop();
   }

   peek() {
      return this.items[this.items.length - 1];
   }
}
```

---

# Queue

FIFO data structure.

---

# Two Sum

## Optimal Solution

```js
function twoSum(nums, target) {
   const map = new Map();

   for (let i = 0; i < nums.length; i++) {
      const complement = target - nums[i];

      if (map.has(complement)) {
         return [map.get(complement), i];
      }

      map.set(nums[i], i);
   }
}
```

---

## Complexity

Time:

```text
O(n)
```

Space:

```text
O(n)
```

---

# Reverse Linked List

```js
function reverse(head) {
   let prev = null;
   let curr = head;

   while (curr) {
      let next = curr.next;
      curr.next = prev;
      prev = curr;
      curr = next;
   }

   return prev;
}
```

---

# Valid Parentheses

```js
function isValid(str) {
   const stack = [];

   const map = {
      ")": "(",
      "}": "{",
      "]": "["
   };

   for (let ch of str) {
      if (!map[ch]) {
         stack.push(ch);
      } else {
         if (stack.pop() !== map[ch]) {
            return false;
         }
      }
   }

   return stack.length === 0;
}
```

---

# LRU Cache

Least Recently Used cache removes least recently accessed item.

Usually implemented using:
- HashMap
- Doubly Linked List

---

# 25. Production-Level Coding Questions

## Fetch Salary API Problem

### Problem

```js
const userIds = [1,2,3,4,5];
```

API:

```text
/user/salary?id=1
```

Expected Output:

```js
{
   1: 50000,
   2: 60000
}
```

---

## Productionized Solution

```js
const axios = require("axios");

const userIds = [1, 2, 3, 4, 5];

async function fetchSalary(userId) {
   try {
      const response = await axios.get(
         "https://api.example.com/user/salary",
         {
            params: { id: userId },
            timeout: 5000
         }
      );

      return {
         userId,
         salary: response.data.salary
      };
   } catch (error) {
      console.error(`Failed for user ${userId}`);

      return {
         userId,
         salary: null
      };
   }
}

async function fetchAllSalaries(userIds) {
   const results = await Promise.all(
      userIds.map(fetchSalary)
   );

   return results.reduce((acc, curr) => {
      acc[curr.userId] = curr.salary;
      return acc;
   }, {});
}
```

---

## Production Improvements

Mention additionally:

- Retry logic
- Circuit breakers
- Rate limiting
- Caching
- Bulk APIs
- Monitoring
- Logging
- Concurrency control

---

# 26. Behavioral Questions

# Tell me about a complex technical problem you solved

In our Shopify personalized order integration flow, we faced performance issues during high traffic periods.

Heavy synchronous operations and inefficient database queries caused API slowdowns and timeout issues.

I worked on:
- query optimization
- indexing
- asynchronous processing
- reducing redundant DB calls
- improving schema structure

This improved response times significantly and increased scalability.

---

# Biggest Production Issue Faced

One issue we faced was backend slowdown during peak order traffic.

Root causes:
- synchronous processing
- inefficient queries
- missing indexes

Solutions:
- moved heavy tasks to background workers
- optimized queries
- improved monitoring
- added indexes

---

# Mistake You Made

Earlier in my career, I underestimated async edge cases and retry handling.

That taught me the importance of:
- monitoring
- defensive coding
- logging
- failure handling

---

# Why Switching?

I’m looking for:
- stronger engineering challenges
- larger scale systems
- growth opportunities
- better backend architecture exposure

---

# Why Should We Hire You?

I already have hands-on experience building and optimizing production backend systems involving:
- APIs
- authentication
- GraphQL
- MongoDB
- Docker
- asynchronous systems
- backend optimization

I also focus heavily on understanding system behavior, scalability, and maintainable code.

---

# 27. Questions to Ask Interviewer

## Good Questions

- What kind of backend architecture do you use?
- What are the biggest engineering challenges currently?
- How are deployments and monitoring handled?
- How is ownership distributed across engineers?
- What does success look like in first 3 months?
- What does scaling look like for your backend?
- What is the engineering culture like?

---

# 28. Advanced Backend Questions

# What is CAP Theorem?

Distributed systems can only guarantee two out of:

- Consistency
- Availability
- Partition Tolerance

---

# What is Idempotency?

Multiple identical requests produce same result.

Important for:
- payment APIs
- retries
- distributed systems

---

# What is Horizontal vs Vertical Scaling?

| Horizontal | Vertical |
|---|---|
| Add servers | Upgrade server |
| Better scalability | Hardware limits |

---

# What is Connection Pooling?

Reusing DB/network connections instead of creating new ones repeatedly.

Benefits:
- reduced overhead
- better performance

---

# What is Circuit Breaker Pattern?

Prevents repeated failures from cascading.

States:
- Closed
- Open
- Half-open

---

# What is Debouncing?

Delays execution until user stops triggering event.

Used in:
- search bars
- autocomplete

---

# What is Throttling?

Limits execution frequency.

Used in:
- scrolling
- API protection

---

# What is CDN?

Content Delivery Network.

Distributes static assets geographically closer to users.

Benefits:
- lower latency
- faster loading
- reduced server load

---

# What is API Gateway?

Single entry point managing:
- routing
- authentication
- rate limiting
- monitoring

---

# What is Monolith vs Microservices?

| Monolith | Microservices |
|---|---|
| Single application | Multiple services |
| Easier initially | Better scalability |
| Tight coupling | Independent deployment |

---

# What is Graceful Shutdown?

Properly handling:
- active requests
- DB connections
- cleanup

before shutting server.

---

# Final Tips

## During Interview

- Think aloud
- Clarify assumptions
- Explain tradeoffs
- Mention scalability and security considerations
- Discuss real-world production concerns

---

## Communication Strategy

Structure answers like:

```text
Definition
↓
How it works
↓
Real-world usage
↓
Tradeoffs
↓
Example
```

---

# End of Preparation Guide

