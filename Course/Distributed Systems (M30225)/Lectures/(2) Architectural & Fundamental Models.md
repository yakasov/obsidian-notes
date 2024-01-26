# Communication Entities
### Process
A program in execution.

### Objects
Objects represent natural units of decomposition for the given problem domain. Objects are *accessed via interfaces*, with an associated interface definition language (or IDL). Examples include Java RMI or COBRA.

### Components
Components are similar to objects and are accessed through interfaces. Components specify not only their (provided) interface but also specify the required interfaces that must be present for a component to fulfil its function.

### Web Services
A software application identified by a URI, whose interfaces and bindings are capable of being defined, described and discovered by XML artefacts.

A Web service supports direct interactions with other software agents using XML-based message exchanges via Internet-based protocols.

# Communication Paradigms
### Interprocess Communication
- message passing
- shared memory

### Remote Invocation
- request reply protocols
- remote procedure calls (RPC)
- remote method invocation (RMI)

### Indirect Communication
- group communication
- publish-subscribe systems
- message queues
- tuple spaces
- distributed shared memory

# Examples

### Client-server diagram
![[Pasted image 20240126155325.png]]

### Two-tier Architecture diagram
![[Pasted image 20240126155421.png]]

### Three-tier Architecture diagram
![[Pasted image 20240126155438.png]]

### Peer-to-peer diagram
![[Pasted image 20240126155459.png]]

# Placement Policies

### Mapping of services to multiple servers
The servers may partition the set of objects on which the service is based and distribute those objects between themselves, e.g. a distributed database, or...

They may maintain replicated copies of them on several hosts e.g. replicated databases.

### Caching
A cache is a store of recently used data. Web browsers maintain a cache of recently visited web pages and other web resources in the client's local file system.

### Mobile code
Applets are a well-known and widely used example of mobile code.

### Mobile agents
A mobile agent is a running program (including both code and data) that travels from one computer to another in a network carrying out a task on someone's behalf, such as collecting information, and eventually returning with the results.

### Proxy server
![[Pasted image 20240126160753.png]]
A service provided by multiple servers.

# Middleware
The task of middleware is
- to provide a higher-level programming abstraction for the development of distributed systems and, through layering,
- to abstract over heterogeneity in the underlying infrastructure to promote interoperability and portability

Many distributed applications rely entirely on the services provided by middleware to support their needs for communication and data sharing.

Middleware services include
- scheduling
- transactions
- replication
- fault tolerance
- persistence
- high availability

![[Pasted image 20240126160953.png]]
A distributed system organised in a middleware layer which extends over multiple machines, offering each application the same interface.

### Categories of Middleware
- distributed objects
- distributed components
- publish-subscribe systems
- message queues
- web services
- peer-to-peer

# Remote Roles
### Remote Procedure Call (RPC)
![[Pasted image 20240126161135.png]]
Roles of the client and server stub procedures in RPC.

### Remote Object and Remote Interface
![[Pasted image 20240126161159.png]]

### Remote Method Invocation (RMI)
![[Pasted image 20240126161219.png]]
Roles of the proxy and skeleton in remote method invocation.

# Fundamental Models
### Model Types
Interaction Models:
- Synchronous Distributed Systems
- Asynchronous Distributed Systems

Failure Models:
- Process omission failures
- Communication omission failures
- Arbitrary failures

Security:
- Securing processes and their integrations

### Synchronous vs Asynchronous
**Synchronous Distributed Systems:**
- The time to execute each step of a process has known *upper and lower bounds*.
- Each message transmitted over a channel is received within a *known bounded time*.
- Each process has a local clock whose drift rate from real time has a *known bound*.

**Asynchronous Distributed Systems:**
There are *no bounds* on:
- process execution speeds
- message transmission delays
- clock drift rates

### Failure Models
**Process omission failures:** 
A process can crash due to any reason. A timeout can be used to detect process failure in synchronous distributed systems.

A process crash is called fail-stop if other processes can detect certainly that the process has crashed.

**Communication omission failures:** 
- send omission failure
- receive omission failure
- channel omission failure

**Arbitrary or Byzantine failures:**
Any type of failure can occur.