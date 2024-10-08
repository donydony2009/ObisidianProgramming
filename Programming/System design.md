
### Purpose
1. translate ambigous problem to Find requirements and constrains
2. make an architecture to do it
3. defend your choices
4. No such thing as the right decision
5. You want to demonstrate communication

### Todo
1. 1. Practice. Schetch something like instagram, linkedin, twitter, uber
2. Study common design patterns of system design. Practice questions like why Redis vs Memcached. Get familiar with whiteboards
3. For each component type get a few names
### Strategy
1. Start by asking questions. Establish requirements and indirect requirements
	1. How many users?
	2. How many read requests per day?
	3. How many write requests per day?
	4. How much data do we need to store?
	---
	1. What latency is required?
	2. What is the availability needed?
	3. What about consistency?
	4. What is the reliability needed?
2. Calculations on data requirements
3. Establish high level design starting from User and from his writes. Make sure to talk through the whole process. Think of tradeoffs. At this point don't name specific technologies. Try to get buy in from interviewer. Make sure he is on  board with your proposal
4. Deep dive. Name technologies and tradeoffs

### Back of the envelope tricks
- 2^10 is 10^3
- For an url generator we can use 64 characters which is a-zA-z0-9_-
- 80-20 rule 20 % of users are responsible for 80% of the work

### Ways to throttle
- Api key
- IP
- Account


### Design patterns

1. Load balancer -> horizontal scaling
2. Servers
3. Pub/sub -> Async jobs or some sort of notification system
4. CDN caching 
5. Database scalability, availability zones, sharding
6. In memory caching (redis, memcached)

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

### CDNs

CDN or Content delivery network is a way to deliver static files to people.
CDNs are usually distributed across the globe aiming to have the data as close to the person as possible.

#### Use case
Any file above 1kb that is needed by a lot of people. Ex: Images, audio files, videos, HTMLs, CSSs. anything static and unmodifiable

#### Types
1. **Push CDN** - Engineers must push the assets to the cdn. Useful if you don't have a lot of stuff or you have specific criteria based on which to push to the cdn
2. **Pull CDN** - You set it up so the CDN requests the resources automatically from the appropriate servers. Much more hands off.

#### Examples
- GCP CDN
- Azure CDN
- AWS Cloudfront
- Cloudfare CDN
- Oracle CDN

### Pub/Subs

Pub sub refers to messaging pattern Publish Subscribe pattern in which publishers post messages that apply to certain topics and cosumers subscribes to topics to get the messages.

Also the is a concept names **Message queue** which basically just a single produces single consumer queue of events

#### Technologies for listening
1. Websockets
2. Grpc
3. WebHook (https request)

#### Advantages
Loose coupling means you don't need to know who is listening you just publish
Usually highly scalable as you can shard based on topic?

#### Disadvantages
- No direct guarantee of delivery
- Potentially disastrous failure of delivery because you can't know if your message made it

#### Use case
1. Notifications
2. Decouple s2s communication

### Caching
Used to memorize request responses that are required often. 

#### Tech
1. Redis
2. Memcached
3. Directly on the loadbalancer
4. Directly on the user machine. Ex: on browser you can cache with headers

#### Cache population strategies
1. Write to the cache and db at the same time
2. Write through - Write to cache, cache writes to db
3. Write around - Write to the DB and on cache miss the cache fetches data from server
4. Lazy write - You write directly to cache and the db is populated from the cache async later.

#### Cache invalidation strategies
1. Explicit PURGE request
2. Explicit REFRESH request
3. BAN - just purge with criteria
4. TTL
5. Stale while updating
6. Event based - When an event such as a DataUpdated Event happens
7. Version based
8. LRU - Least recently used (if we need space we invalidate the least recently used)
9. LFU - Least frequently used
10. FIFO - first in first out - queue
11. Random - GLHF

#### Memcached vs Redis
**Pro memcached:**
Very simple key value store which gives it very good multithreading performance
**Pro redis:**
A lot more versatile in memory operations and data types


### DNS
How a domain name is converted to an  ip. You can do some lb on the DNS

### Load balancer
An entry point for requests to be redirected to one of many servers.  Enables horizontal scaling.
Additionally it usually supports some form of caching

AKA reverse proxy

#### Examples
Nginx - HTTP Lb
HAProxy - TCP lb
Varnish - ??
Balance - TCP lb
Every single cloud


### Databases
Storage with querying capacity.

#### CAP
In databases there is a CAP theory meaning Conistency, Availability and Partition tolerance.
C - Consistency - Read always gets the latest data or an error
A - Availability - Every request received by a non-failing node in the system must result in a response
P - Partition tolerance - The system continues to operate despite an arbitrary  number of messages  being dropped or delayed by the network between node

You can only ever achieve 2. And they are denoted as CA, CP or AP
#### Types
- These types have some overlap
1. Relational databases - Usually organized into tables providing strong consistency guarantees, and trasactions. They stand out in being able to  establish relations between tables and maintaining these relations with strict consistency
2. NoSQL - Usually ditch the relations guarantee and tables
	- Json storage - Mongo
	- key-value - Redis
	- Column-Oriented - Very efficient retrieval of only the columns instead of the whole row. Good for analytics. Similar to ECS
	- Graph dbs - They are made to model graphs. They usually are used for things like fraud detection or social networks
1. Cloud native dbs
	- These dbs are usually built for cloud
	- They scale horizontally extremely good
	- Usually provide some sort of pay for usage
	- Usually they require 0 setup

#### In memory databases
Usually used for caching, ephemeral data, or distributed locking.

#### SQL ACID
Relation databases are used when you need strong consistency.

#### NoSQL drop some consistency
Used for horizontal scaling at the cost of consistency

#### Cassandra vs Mongo
M- For availability Mongo has only one primary node and if it goes down it can spend a bit of time to choose a new one which can cause downtime
C+ Cassandra has many master nodes which allows for 100% availability
M+ You have more ocntrol as you scale allowing you to decide how to particition data across nodes based on your requirements and manage massivle distributed dbs
C- Performance may drop at scale
M+ Mongo supports transactions
C- Cassandra doesn't support transactions

#### What is big data
Extremely large and diverese collections of structured unstructered and semi structured data that continues to grow exponentially over time

#### Text search dbs
- Lucene / Elastic Search - Not trivial to integrate
- Postgres
- Mysql
- Sphinx



### Relational vs nosql
Ditching the relational aspect of a db allows you to much more easily shard horizontally across multiple servers.

Currently neither mysql nor postgres support sharding. But solutions for mysql and postgres exist
Examples of **posgres plugins for sharding**:
- Citrus
- Postgres-XL
Examples of **mysql sharding stuff:** 
- TAO from facebook
- Gizzard at twitter
- Vitess

### Telemetry

Used to track valuable information about our system and how it's used, Can be very important if something bad happens. It is the window into how our system works.

Additionally it can be very important for business reasons

### Content deduplication

With any user content there is a high probability that there is some content duplication which we don't need to store multiple times


### Metrics

#### Health checks
Check on an endpoint if things are not responding

#### Metrics
You can monitor status requests, Errors, latency,

### Twitter

100 M
70 M 
5 writes per user per day
100 reads per user per day
140 chars per tweet
Support images and video
Follower - Followee relation
Likes? Views?

non functional requirements
Highly available 
Consitency - Eventually consistent is fine
Latency - As low as possible
Reliability - We don't want to lose any content

70M * 100 * 140 - tweet read contnet
70M * 5 * 140 - tweet write
70M * 5 * 0.05 * 10MB - audio/video content

1 day - 70M * 5 * 140 * backups/sharding
10 years - 10 * 365 * 70M * 5 * 140 

1 day - 70M * 5 * 0.5 * 10MB
10 years - 10 * 365 * 70M * 5 * 0.05 * 10MB

User -> Write -> LB -> Tweet service -> Tweet, user, date, content metadata
			 -> av we post to object storage
	 -> Read from CDN
	 -> Follow -> LB -> Follow service
	 -> Read timeline -> Get follow list
				 -> Fetch tweets based on followers


### Tricks

- **Proxy Usecase** - When faced with a  many to many relationship, for example group X is fully connected to group Y requires card(X) * card(Y) connections. But putting one or more Proxies in the middle reduces it to card(X) + card(Y) ([[https://www.youtube.com/watch?v=ArBL7eQwc_Q|vid]])
			 
![[Pasted image 20241002232613.png]]

