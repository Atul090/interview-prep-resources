
# 🚀 Atul Deep Singh — Advanced Interview Question Bank

---

# ⚙️ SECTION 11: Advanced Node.js & Backend Internals

161. What happens internally when a request hits a Node.js server?
162. Explain how libuv works.
163. What is the thread pool in Node.js and when is it used?
164. Why is Node.js single-threaded yet scalable?
165. What are worker threads and when would you use them?
166. What causes event loop blocking in production?
167. How do you detect event loop lag?
168. How do you fix event loop blocking issues?
169. What is clustering in Node.js?
170. PM2 vs Node cluster module?
171. How do memory leaks occur in Node.js?
172. How do you detect and debug memory leaks?
173. What is heap vs stack memory in V8?
174. How does garbage collection work in V8?
175. What are streams in Node.js?
176. When would you use streams over buffers?
177. How do you process large files efficiently?
178. What are race conditions in Node.js?
179. How do you ensure thread safety in Node?
180. How do you debug memory spikes in production?

---

# 🧱 SECTION 12: Advanced System Design

181. Design a scalable e-commerce checkout system.
182. How do you ensure inventory consistency?
183. Design a distributed rate limiter.
184. Design a URL shortener system.
185. Design a real-time chat system.
186. Design search autocomplete.
187. Design a recommendation system (like Netflix).
188. Design a real-time order tracking system.
189. Design a distributed cache system.
190. What is consistent hashing?
191. How do you handle cache invalidation?
192. Redis vs Memcached?
193. How do you prevent cache stampede?
194. What is eventual consistency?
195. Strong vs weak consistency?
196. How do you design idempotent systems?
197. What is distributed locking?
198. How do you prevent double payments?
199. Saga pattern vs Two-Phase Commit?
200. How do you design fault-tolerant systems?
201. What is circuit breaker pattern?
202. What is bulkhead pattern?
203. What are retry strategies?
204. How do you handle partial failures?
205. What is observability in distributed systems?

---

# 🗄️ SECTION 13: MongoDB Deep Dive

206. How does MongoDB handle concurrent writes?
207. What is oplog?
208. How does replication lag affect reads?
209. How do you design high-write systems in MongoDB?
210. What are write conflicts?
211. What is journaling in MongoDB?
212. How do transactions work internally?
213. What is read preference?
214. What is read concern?
215. How does sharding work internally?
216. What is chunk migration?
217. How do you avoid hot shards?
218. How do you design shard keys?
219. What is index cardinality?
220. What are covered queries?
221. How do you analyze slow queries?
222. How does aggregation pipeline optimize queries?
223. MapReduce vs aggregation pipeline?
224. How do you scale MongoDB horizontally?
225. When would MongoDB not be a good choice?

---

# 🔗 SECTION 14: GraphQL Advanced

226. How does GraphQL execution work?
227. What is a resolver chain?
228. How do you optimize nested queries?
229. What is DataLoader and how does it help?
230. How do you implement caching in GraphQL?
231. How do you secure GraphQL APIs?
232. What are query complexity attacks?
233. How do you prevent over-fetching and under-fetching?
234. How do GraphQL subscriptions work?
235. GraphQL vs gRPC?
236. Schema stitching vs federation?
237. Apollo vs Relay?
238. How do you version GraphQL APIs?
239. How is error handling done in GraphQL?
240. How do you monitor GraphQL performance?

---

# 🤖 SECTION 15: AI / Semantic Search Advanced

241. What is tokenization?
242. What is transformer architecture?
243. How do embeddings capture semantics?
244. Explain cosine similarity mathematically.
245. What is the curse of dimensionality?
246. How do you reduce embedding dimensionality?
247. What is Approximate Nearest Neighbor (ANN)?
248. What is HNSW algorithm?
249. Trade-offs in vector search systems?
250. How do you scale embedding pipelines?
251. Real-time vs batch embeddings?
252. What is Retrieval-Augmented Generation (RAG)?
253. How would you build a ChatGPT-like system?
254. What is hallucination in AI?
255. How do you evaluate AI model performance?

---

# 📡 SECTION 16: RabbitMQ Advanced

256. How does exchange routing work internally?
257. Fanout vs direct vs topic exchange?
258. How do you handle duplicate messages?
259. What is idempotent consumer?
260. How do you handle poison messages?
261. What is message TTL?
262. What are queue overflow strategies?
263. What is a lazy queue?
264. How do you design high-throughput queues?
265. What is publisher confirm?
266. How do you handle backpressure?
267. How do you guarantee message ordering?
268. Is exactly-once delivery possible?
269. How do you migrate queues safely?
270. How do you monitor RabbitMQ at scale?

---

# ☁️ SECTION 17: AWS Advanced

271. What is a VPC?
272. Public vs private subnet?
273. What is a NAT gateway?
274. Security groups vs NACL?
275. How does a load balancer work internally?
276. What is ALB vs NLB?
277. ECS vs EKS?
278. What is CloudWatch?
279. What is distributed tracing?
280. What is AWS X-Ray?
281. How does IAM policy structure work?
282. How do you secure APIs on AWS?
283. Cost optimization strategies?
284. What are spot instances?
285. How do you design multi-region architecture?

---

# 🧪 SECTION 18: Advanced Testing

286. What is contract testing?
287. What is mutation testing?
288. What is load testing?
289. Tools for load testing?
290. What is chaos engineering?
291. How do you simulate failures?
292. What is canary testing?
293. What is A/B testing?
294. How do you test distributed systems?
295. What is the test pyramid?

---

# 🔐 SECTION 19: Security Advanced

296. What is SQL injection?
297. What is XSS?
298. What is CSRF?
299. How do you prevent them?
300. What is OAuth?
301. OAuth vs JWT?
302. What is hashing vs encryption?
303. What is salting?
304. How do you store passwords securely?
305. What is zero trust architecture?

---

# 🧠 SECTION 20: Debugging & Production Thinking

306. API latency increased — how do you debug?
307. Database CPU spikes — what steps?
308. Memory leak in production — how to find?
309. Search accuracy dropped — why?
310. Queue backlog increasing — what to check?
311. Deployment broke system — rollback strategy?
312. Logs missing — what to do?
313. Third-party API failure — fallback?
314. Cache causing stale data — fix?
315. High GraphQL error rate — debugging steps?

---

# 💀 SECTION 21: Edge-Case Thinking

316. Can Node.js truly be multi-threaded?
317. Can MongoDB lose data?
318. Can RabbitMQ guarantee delivery?
319. Can REST be stateful?
320. Can GraphQL replace REST entirely?
321. Is microservices always better?
322. Can caching make systems slower?
323. Is eventual consistency acceptable for payments?
324. Can AI search replace keyword search?
325. What is the hardest engineering problem you’ve faced?

---

# 🎯 HOW TO USE THIS

- Pick 10 questions/day  
- Answer out loud  
- Focus on depth, not memorization  
- Practice explaining trade-offs  

---

# ⚠️ FINAL INSIGHT

These questions are designed to:
- Break shallow understanding  
- Test real-world thinking  
- Evaluate system-level knowledge  

---
