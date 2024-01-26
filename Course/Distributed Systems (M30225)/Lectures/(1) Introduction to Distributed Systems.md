# Outline
### Distributed Systems Examples
- Web Search
- Online Games
- Financial Trading

### Trends in Distributed Systems
- Pervasive Networking
- Mobile Computing
- Distributed Multimedia Systems
- Distributed Systems as a utility

### Challenges
- Heterogeneity
- Openness
- Security
- Scalability
- Failure Handling
- Concurrency
- Transparency
- Quality of Service

### Architectures
- Elements
- Patterns
- Layering
- Tiered architectures
- Thin clients
- Middleware solutions

### Fundamental Models
- Interaction Model
- Communication Channel
- Failure Model
- Security Model


# Why Distributed Systems?
There are three ways of doing things faster:
- working harder - better hardware performance
- working smarter (eg assembly lines, racing lines in F1) - better algorithms
- getting help (the army, committees, bureaucrats) - distributed / parallel processing

# Definition
A distributed system is one in which *hardware or software components located at networked computers communicate and coordinate their actions only by passing messages.*
![[Pasted image 20240126151258.png]]

The three major characteristics of distributed systems include
1. Concurrency
2. No global clock
3. Independent failures

# Challenges of Distributed Systems

### Naming
Names assigned to resources or objects must have global meanings:
- they must be independent of the locations of the object
- they must be supported by a name interpretation system that can translate names to enable programs to access named resources.
It should scale and translate efficiently.

### Communication
- **Costly Communications** - bandwidth and latencies are costly if you want to match those available to localised processors - all in one box (SMP)
- **Unreliable Communications** - connections may be unavailable, messages may be lost or corrupted, a remote computer may not be available, etc.
- **Independent Failure** - the distributed system needs to continue working after the failure of a network or computer
- **Insecure Communications** - exposed to unauthorised access, could be malicious.

### Heterogeneity
- Networks
- Computer Hardware
- Operating Systems
- Programming Languages
- Implementations by different developers
All are examples of things that can differ largely between systems. Openness is achieved through the design and construction of software components with well defined interfaces - APIs.

### Load Balancing
Deployment of the processing and communications resources in the network to optimum effect for processing a changing workload.

### Scalability
A system is described as scalable if it will remain effective when there is a significant increase in the number of resources and the number of users.

Issues:
- controlling the cost of physical resources
- controlling the performance loss
- avoiding performance bottlenecks

### Failure Handling
Any software or hardware component might fail. Failure handling can be split into several mitigations:
- detecting failures
- masking failures
- tolerating failures
- recovery from failures
- redundancy

### Consistency Maintenance
The maintenance of consistency in the distributed system, where we are concerned with
- data - concurrent access of same data
- replication - of data, fault tolerance
- cache - performance/FT/availability
- failure - master/slave, DNS
- consistent time
- user interface - ergonomics/ease of use

### Transparency
To the user and the application programmer, the system is perceived as a whole rather than as a collection of independent components. The types of transparency include
- access
- location
- replication
- concurrency
- failure
- mobility

### Security
- **Authentication** - ensure users have the right to access resources
- **Access Control** - different levels of access to different users
- **Auditing** - every access to a resource can be logged, as evidence used to record authentication (audit trail)

### Quality of Service
The responsiveness and computational throughput; the ability to meet timeliness guarantees.

# Summary
Distributed systems consist of autonomous devices that work together to make the complete system look like a single computer-based resource.

### Advantages
- price vs performance
- lower application turnaround
- reliability
- incremental growth as workload increases

### Disadvantages
- complexity of software (system and application)
- communications bottlenecks
- weaker security
- reliability

