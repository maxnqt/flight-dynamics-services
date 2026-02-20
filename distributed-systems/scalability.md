# Scalability

- [ ] Vertical scaling
- [ ] Horizontal scaling
- [ ] Caching
- [ ] Load balancing
- [ ] Database replication
- [ ] Database partitioning
- [ ] Asynchronism

---

## Scaling reads

- Even I/O has physical limits; too many reads cause bottlenecks
- Aporoches:
  1. Optimize read performance within database (indexing, denormalization)
  2. Scale database horizontally (read replicas, sharding)
  3. Add external caching layers (application, CDN)
- Add indexes on columns that are frequently queried (modern databases have little write overhead for indexes)
- Scale database vertically
- Denormalize: Organize data differently, in a way that is optimized for reads (trade-off between duplication \[more storage\] and joins)
- Note: Denormalization causes storage and write overheads (more memory, every write has to update many rows instead of one row)
- Read replicas: Copy data from primary/leader to followers async or sync (for strong consistency); all writes go to the primary, reads can be served from any of the replicas
- Sharding: Splits data scross multiple databases; each shard holds a smaller dataset, reads get distributed across the databases
- Use sharding when even well-indexed queries become slow or a single machine can no longer store all of your data on disk anymore
- Functional sharding: Split by features (e.g., posts, users, likes)
- Shard keys: Split by a computable key
- Note: Sharding adds coordination overhead (shard maps, rebalancing, cross-shard queries); typically sharding is more commonly used for scaling writes (avoid sharding until you truly need it)
- Caching: Better performance in read-heavy systems
- Most applications have highly skewed access patterns: Lots of times, a few records are accessed most while lots of records are hardly ever accessed
- If the data isn't changing between requests, caches can store those "hot" results and serve it orders of magnitude faster than the DB
- Application-level caching: Add cache alongside database, requests first go to cache, only in case of cache miss or stale data to the database (e.g., Redis, Memcache)
- CDN and edge caching: Caches spread across the world, across different data centers
- Use CDNs and edge caching to reduce the load on origin servers
- Originally CDNs were only used for static assets (content-/media-heavy)
- Modern CDNs can also cache dynamic contents
- Note: Cache invalidation introduces an operational overhead

---

- What happens when your queries start taking longer as your dataset grows? (Indexing: Which queries/columns are slowing down exactly?)
- Even with indexing, how do you scale to 100s of thousands of reads per second? (Heavily skewed data \[access patterns\]? Caching; otherwise read replicas)
- How do you handle millions of concurrent reads for the same cached data? (Hot key problem: Request Coalescing: When multiple users request the same key at the same time, combine into a single request; if not enough, Cache Key Fan-out: Shard cache and spread hot key amongst all of them \[Trade-off: extra memory usage, invalidation overhead across shards\])
- How do you handle cache invalidation when data updates need to be immediately visible? (Strong concistency: Caches by nature introduce eventual consistency; if strong consistency matters, every time we write a new value to the database, invalidate the cache; more reliable technique than cache invalidation is Cache Versioning: Make old cache keys irrelevant by changing them every time the data changes; each record has a version number in the database \[incremented during same transaction the row is updated\], write new version to the cache \[in its own key "event:123:version"-> 43\], then populate the keys "event:123:v43")

## Scaling writes

- Write scaling is about reducing throughput per component
- Approaches:
  1. Vertical scaling and database choices
  2. Sharding and partitioning
  3. Handling bursts with queues and load shedding
  4. Batching and hierarchical aggregation
- 

## Credits

- [https://github.com/donnemartin/system-design-primer](https://github.com/donnemartin/system-design-primer)
- [https://www.hellointerview.com/learn/system-design/patterns/scaling-reads](https://www.hellointerview.com/learn/system-design/patterns/scaling-reads)
- []()
