**Main System Components**
- Multimedia databases
- Information servers
- Proxy servers
- Clients
**Purpose**
- *distribution* of *multimedia* content over the networks

A variety of multimedia resources over the network are combined into an application for end users. The user may control the level of interaction e.g. required data flow

## Web Based Multimedia Applications
Web based multimedia applications use best-effort QoS access of audio and video data e.g. Youtube, BBC iPlayer

**Challenges**
- managing the finite bandwidth
- variable latency
- resource scheduling

**QoS Parameters**
- latency: tolerable end-to-end delay
- throughput (bandwidth): rate at which data flows through
- loss rate: dropped video frames or audio samples

## Characteristics of a Multimedia System
Multimedia systems generate and consume continuous streams of data. They are time based (throughput/latency, controlling jitter):
- arrival time
- arrival order
- reliability
- high-quality
The system must be capable of serving a large number of end users - concurrency, especially concurrency of data access. Multimedia applications can tolerate a small amount of packet loss.

### User Experiential Requirements
Users should experience low latency and have a synchronised distributed state between each other, e.g. all users should see the same things within 50ms of each other.

### Multimedia Service Requirements
- needs high end specification
- requires fast data retrieval
- real-time resources
- proper scheduling
- expandable I/O capabilities
- minimum response time (must meet user expectations and have fast processing)
- fault tolerance - minimal down time
- ability to sustain guaranteed simultaneous data streams
- presentation (image resolution)
- must provide differential QoS requirements

### Quality of Service Management
Networks are designed to be shared by applications. Round-robin and other best effort methods for resource sharing cannot meet the needs of multimedia applications. 

Multimedia applications need resource guarantees that the necessary resources will be allocated and scheduled at the required times. The management and allocation of resources to provide such guarantees is refereed to as quality of service management.
![[Pasted image 20240223175822.png]]

#### Specifying the QoS parameters for streams
Flow specification -> bandwidth, latency, loss

**Explicitly**
e.g. for the camera output stream we might require *bandwidth*: 50Mbps, *delay*: 150ms, *loss*: < 1 frame in 1000

**Implicitly**
e.g. the bandwidth of the input stream to the network connection is the result of applying MPEG-1 compression to the stream

### Creating a smooth stream
The model of linear-bounded arrival processes (LBAP) defines the maximum number of messages in a stream during any time interval $t$ as $$ Rt + b $$where $R$ is the rate and $B$ is the maximum size of burst.

We cannot send a burst of size $B$.

#### Token Bucket
Tokens to send data are generated at a fixed rate, $R$. They are collected in a 'bucket' of size $B$. Data of size $S$ can be sent only if at least $S$ tokens are in the bucket. The send process then removes these $S$ tokens. 

Over any interval $t$, the amount of data sent is not larger than $Rt + b$ - we are now able to send a burst of size $B$.

### Specifying Latency
**Frame buffer time**: a frame must on average not remain in a buffer for longer than $\frac{1}{R}$, where $R$ is the frame rate of the stream.

**End-to-end delay**: e.g. not more than 150ms for smooth conversation.

**Jitter**: variation in delivery of two adjacent frames.

**Loss rate:** the probability of each packet being dropped.

### RFC 1363 Flow Spec
![[Pasted image 20240223180751.png]]

### Typical infrastructure components for multimedia applications
![[Pasted image 20240223180827.png]]

### Negotiation Procedures
Each source sends the flow spec to the local QoS manager. Intermediate nodes aggregate QoS feedback messages. Desired and worst-case values are calculated for each QoS parameter. Streams might have multiple sinks. The negotiations can have two types: sender initiated, or receiver initiated.

### Admission Control
We must regulate access to resources. Allocation of resources can be based on min, max or average resource requirement from application.

Resources with distributed access points need centralised or distributed admission control. Guaranteed QoS results in a reservation of a portion of resource bandwidth.

To a network of a certain bandwidth $B$, multimedia streams $s$ of a bandwidth $b_s$ can be admitted as long as $\Sigma{b_s} \leq B$.

### QoS Mechanisms
- size of the buffer (dynamic)
- compression requirements
- bandwidth reservation
- traffic shaping
- flow specification
- stream adaptions

### Challenges
The main challenge is adapting to the users needs:
- flexibility
- availability
- scalability
There are additional challenges however, such as
- maintaining simultaneous streams
- cache consistency
	- the cache is required for fast delivery of data
	- number of copies of the multimedia database
- allocating resources appropriately
- managing the available bandwidth