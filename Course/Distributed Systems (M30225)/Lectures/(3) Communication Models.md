A Distributed System is a set of communicating components.
![[Pasted image 20240129140355.png]]

### Client-Server Model (Direct Communication)
- **Space Coupling:** The sender needs to know the identity of the receiver.
- **Time Coupling:** The client and the server should be live at the same time.
Server failure impacts the client. It is difficult to replace the server.

### Asynchronous vs Synchronous Communication

#### Asynchronous Mode
The sender continues its operation without waiting for a response. There are no time limits defined. An example might be an email.

#### Synchronous Mode
The sender is blocked until it gets a response. It is a time constrained communication. An example might be a phone call.

![[Pasted image 20240129141530.png]]

### Indirect Communication
- **Space Uncoupling:** The sender does not need to know the identity of the receiver.
- **Time Uncoupling:** Senders and receivers can have an independent lifetime.
Indirect communication is suitable for changing environments as well as for event dissemination. There is a performance overhead due to indirection.
![[Pasted image 20240129142401.png]]
![[Pasted image 20240129142200.png]]

### Group Communication
- Manages group membership
- Detects failures
- Provides reliability
- Ensures the correct order of messages
Senders do not know the identities of the receivers.
![[Pasted image 20240129144144.png]]

### Application Area Examples
- **Financial Industry:** Reliable information dissemination to large clients
- **Multiuser Games:** Support for collaborative applications
- **Consistent updates for replicated data:** Support for a range of fault-tolerance strategies
- **Support for system monitoring and management:** Load balancing

### Types of Group Communication
- Unicast
- Multicast
- Broadcast
![[Pasted image 20240129145303.png]]
Additionally, we can have
- **Open Group:** anyone can send messages in the group e.g. a notice board
- **Closed Group:** only members of the group can send messages in the group e.g. house group chat

### Publish-Subscribe Systems (Distributed event-based systems
*Publishers* publish structured *events*.
*Subscribers* express interest in particular events through *subscriptions*.
Publish-subscribe system *matches subscriptions against published events* and ensures correct delivery of event notifications.
![[Pasted image 20240129150055.png]]

#### Applications of Publish-Subscribe Systems
- Financial information systems
- Other areas with live feeds of real-time data
- Support for cooperative working, where a number of participants need to be informed of events of shared interest
- Support for ubiquitous computing, including the management of events emanating from the ubiquitous infrastructure e.g. location events
- Monitoring applications, including network monitoring on the Internet

Example of a Dealing Room System
![[Pasted image 20240129150422.png]]

#### Characteristics of Publish-Subscribe Systems
- Heterogeneity
- Asynchronicity
- Delivery Guarantees

Subscription Model:
- Channel-based
- Topic-based
- Content-based
![[Pasted image 20240129150502.png]]

#### Publish-Subscribe System Architecture
![[Pasted image 20240129151527.png]]

### Message Queues
- Point-to-point communication
- Producer processes can send messages to a specific queue
- Other (consumer) processes can then receive messages from this queue
- Receive styles:
	- a blocking receive 
	- a non-blocking receive (a polling operation)
	- a notify operation

Examples: IBM's WebSphere MQ, Microsoft's MSMQ, Oracle's AQ
![[Pasted image 20240129151658.png]]

#### Queuing Policy
- FIFO system, but also supports priority
- Consumers can also select messages based on message properties
- Message size is configurable, can be very large i.e. 100MB+
- Messages are persistent

#### Distributed Shared Memory
![[Pasted image 20240129152324.png]]

### Tuple Space
A tuple space is a collection of tuples, which is a set of one or more typed data fields. Processes communicate through a shared tuple space.

Tuples are immutable.

Three operations are defined:
- **Write:** put a new tuple in the space 
- **Read:** read the value of a tuple
- **Take:** read and remove the tuple
For synchronisation purposes, Write and Read are blocking operations.

#### Tuple Space Communication
![[Pasted image 20240129152547.png]]
