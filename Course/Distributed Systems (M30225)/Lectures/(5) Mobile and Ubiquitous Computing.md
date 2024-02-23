(ubiquitous meaning present, appearing or found everywhere)

# Characteristics of Mobile and Ubiquitous Systems
![[Pasted image 20240222145733.png]]
## Sensing and Context Awareness
**Context**
- values such as location, time, temperature, identity, presence of other entities, etc.

**Sensors**
- examples include location, velocity, motion
- presence sensors: load, RFID readers, microphones, key presses on a computer, etc.
- data produced is not fully accurate
- may not work in particular circumstances

## Smart Spaces
This is a physical space within embedded services. This concept uses dynamic mobility alongside more traditional computing e.g. smart homes
![[Pasted image 20240222150705.png]]

## Volatile Systems
Volatile Systems are highly dynamic and unpredictable spontaneous networking (Ad Hoc). These systems are prone to failure and rely on their association of software components which are often service driven.

## Sensors and Actuators
Sensors are usually measurable physical parameters
- orientation
- load
- light
- sounds

Actuator software controllable devices
- air conditioning
- motors
- smart home devices


# Association Problem and Discovery Services

## Associations
Volatile components need to interoperate, and access to the network is essential for communication. Components either associate to the services in their smart space and/or provide services elsewhere.

Challenges include the scale and scope - many devices and software components can exist in a single space. Associations are not constrained by boundaries they can use discovery services.

## Discovery Service
![[Pasted image 20240222153155.png]]

### Discovery Services in Smart Spaces
How can we discover services in a smart space? By using a server that provides discovery services. A service lookup is provided, and devices and services can register and deregister themselves.

**Implementation Challenges**
- Client needs are determined at runtime
- Push Model
	- Advertise services (multicast) - needs to be done regularly
	- Clients run queries on them (cache)
- Pull Model
	- Client multicast requests - repeated
	- Devices providing these services respond
- Not all smart spaces have servers

### Discovery Services Implementation
We can have a server based implementation that involves a centralised directory. Alternatively, we can also have a serverless (decentralised) implementation with no central directory. This requires each device to maintain their own directory in their cache.

The challenge for both is maintaining volatile services.

### Discovery Services Challenges
- Bandwidth use
- Push Model advertising is wasteful
- Pull Model is more efficient but may need more responses
- A hybrid model may work better
- Volatile services management is difficult
	- Clients lease a service for a length of time
		- Clients need to renew the lease for continued use
		- If the service is not renewed it is released
- Scale is problematic
- Smart space boundaries are also a challenge
![[Pasted image 20240222161103.png]]

### Physical Association
**Human input to scope delivery**
- select the scope identifier e.g. room number

**Sensing and physically constrained channels to scope discovery**
- read the code for smart space identifier
- an infrared transmitter propagates the space identifier

**Direct association**
- address sensing
- physical correlation
	- two button protocol

# Programming models for volatile systems

## Interoperability
This means the interface between devices and services. It relies on protocols and programming models. The goal is to avoid the "lost opportunity problem".

Challenges:
- to improve software interfaces compatibility
- interfaces to be heterogeneous
- for every $N$ interfaces, $N^2$ adaptors are needed to be determined at runtime

## Data-oriented programming
Unvarying service interfaces, e.g. Unix pipes.

**Event Systems**
- event service provides interfaces
- *Publishers* publish and *Subscribers* consume events
- Challenges:
	- discovery
	- agreement on event service instance
	- service scope

**Tuple Spaces**
- allows for exchange of application specific structured data
- device puts tuple, consuming device looks for tuple

## Interoperability - interfaces
Constraining interfaces
- Unix pipes (read/write)
- Web HTTP (GET/POST)

If smart spaces have their own programming interface, this would inhibit mobility. Components moving in the smart space need to communicate via adapting to interoperate with services. This requires complex runtime support.

# Sensing and Context Awareness

## Challenges of Context Aware Systems
**Integration of sensors:** specialised knowledge may be required
**Abstraction from sensor data:** applications will need to abstract from raw sensor data e.g. location
**Sensor fusion:** multiple sensors data need to be combined and interpreted to perform a complex sensing task such as detecting the presence of a human
**Context is dynamic:** applications typically need to respond to changes in context

## Wireless Sensor Networks
- nodes arranged randomly
- no global control
- nodes communicate only with neighbours
	- saves energy
	- reduces network contention
Root node is used for longer-range communication with a conventional system

## Software Architecture for WSN
**In-network processing**
- processing on the sensor nodes
- aggregating from nearby nodes
**Disruption-tolerant networking**
- no end-to-end path exists continuously
- opportunistic communications
**Data-oriented programming models**
- directed diffusion
	- interests (tasks) injected into the system at certain nodes called sinks
	- runtime system diffuses the interests in the system
- distributed query processing
-