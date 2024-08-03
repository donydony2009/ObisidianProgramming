
### Purpose
1. translate ambigous problem to Find requirements and constrains
2. make an architecture to do it
3. defend your choices
4. No such thing as the right decision
5. You want to demonstrate communication

### T
### Strategy
1. Practice. Schetch something like instagram, linkedin, twitter, uber
2. Study common design patterns of system design. Practice questions like why Redis vs Memcached. Get familiar with whiteboards
3. Start by asking questions to understand technical constrains and requirements. Try to set in stone what is needed.
4. Start drawing all the components and vocalize all your thoughts. Mention tradeoffs. Usually you should start with the user, probably with the writes and where the data arrives

### Design patterns

1. Load balancer -> horizontal scaling
2. Pub/sub -> Async jobs or some sort of notification system
3. CDN caching 
4. Database scalability, availability zones, sharding
5. In memory caching (redis, memcached)

### Requirements
1. Req / s
2. Writes vs reads
3. Queries
4. Streaming / processing
5. Data read amount and data write amount

### Secondary Requirements
1. Security
2. Availability
3. Consistency, immediate vs eventually
4. Probabilistic counting or normal counting

### To study
- How to resume uploads / downloads
- Queues
- Config system
- Types of pub subs
- Load balancing caching
- types of CDNs and how to populate it
- types of DBs (relational, column, analytical, nosql, graph)
- Caching and caching strategies
- Microsoft cloud options