# Outline
- HTTP Request-Response Model
- Web Service Definition
- Enabling Technologies
	- XML
	- SOAP
	- WSDL
- Example Grid Computing
- Cloud Computing
- Research Questions
	- Integration of Services
	- Performance Evaluation of Services
	- Scalability
	- Consistency and Replication


# URI, URL and URN
**URI (Uniform Resource Identifier):** A URI is a generic term used to identify all types of names and addresses referring to objects on the Internet, regardless of the specific naming scheme used. It serves as a super-category that encompasses both URLs and URNs. A URI can be a name, a locator, or both for an online resource.

**URL (Uniform Resource Locator):** A URL is a specific type of URI that includes the location of a resource on the Internet and the protocol used to access it. It's what we commonly use to access websites. For example, `https://www.example.com` is a URL - it not only identifies the resource, but also explains how to access it (using the HTTPs protocol).

 **URN (Uniform Resource Name):** A URN is another specific type of URI that uses the URN scheme. It is used to uniquely identify a resource, but unlike a URL, it doesn't provide any information on how to locate or access the resource. URNs are used in applications where persistent or long-lived identifiers are necessary, such as in XML and PDF identifiers.
# Web Server vs Application Server
A web server delivers static web content e.g. HTML pages, files, images, video, primarily in response to HTTP requests from a web browser.

An application server
- enables interaction between end-user clients and server-side application code (implements business logic)
- generates and delivers dynamic content, such as transaction results, decision support, or real-time analytics
- the client can be the application's own end-user UI, a web browser or a mobile app
- the client-server interaction can occur via any number of communication protocols

# Web Services Overview
A web service interface generally consists of a collection of operations that can be used by a client over the Internet. The operations in a web service may be provided by a variety of different resources, for example programs, objects or databases.

A web service may be managed by a web server along with web pages, or it may be a totally separate service. Many well-known commercial web servers including Amazon, Yahoo, Google or eBay offer web service interfaces that allow clients to manipulate their web resources.
![[Pasted image 20240222141313.png]]

## Web Service Architecture
**Provider**
- creates an offers web services
- describes web services in a standard format to publish in service registry

**Registry**
- contains data of the service provider
	- address and contact
	- technical details

**Consumer**
- retrieves the information from the registry
- uses the description to bind to and invoke the web service
![[Pasted image 20240222141433.png]]

## Protocols/Standards for Web Services
- **XML:** a uniform data representation and exchange of services offered
- **SOAP:** a standard way for communication
- **WSDL:** a standard meta language to describe the services offered
- **UDDI:** a mechanism to register and locate WS based applications

### Extensible Markup Language (XML)
XML is used to communicate with web services and for defining the interfaces and other properties of web services. XML is also used in archiving and retrieval systems.

The *tags* describe the logical structure of the data and to associate attribute-value pairs with logical structures. XML *namespaces* define the meaning of the tags.

**Advantages**
- uses human language
- easy to code
- completely compatible with Java and 100% portable
- any application that can process XML can use your information, regardless of platform
- XML is extensible

**Disadvantages**
- syntax is verbose and redundant
- the redundancy in syntax causes higher storage and transportation cost when the volume of data is large
- XML document is less readable compared to other text-based data transmissions formats such as JSON

### Simple Object Access Protocol (SOAP)
A definition of how web services talk to each other or talk to client applications that invoke them; a lightweight (XML-based) protocol for exchange of information in a decentralised distributed environment over HTTP.

SOAP consists of
- an envelope that defines a framework for describing what is in a message and how to process it
- a heavy reliance on XML and related standards (schemas and namespaces)
![[Pasted image 20240222142057.png]]

### Web Service Definition Language (WSDL)
Interface definitions are needed to allow clients to communicate with services.

Service description of a WSDL document
- the WSDL document actually tells a client application what are the types of SOAP messages which are sent and accepted by the Web service
- gives the client all the information required to connect to the web service and use all the functionality provided by the Web service
- is an XML format for describing network services
![[Pasted image 20240222142239.png]]

### Universal Description, Discovery and Integration (UDDI)
A specification for a distributed registry of web services. It is a platform-independent, open framework that can communicate via SOAP, COBRA or Java RMI Protocol (among others). It uses Web Service Definition Language (WSDL) to describe interfaces to web services.

UDDI is one of the three foundation standards of web services (others are SOAP and WSDL). It is an open industry initiative, enabling services to discover each other and define how they interact over the Internet. It enables enterprises to quickly and dynamically discover and invoke Web Services both internally and externally.

Key parts of UDDI include
- a registry of all web services' metadata, including a pointer to the WSDL description of a service
- a set of WSDL port type definitions for manipulating and searching that registry
UDDI has a common web services API for publishing and locating businesses and services advertised within the registry.
![[Pasted image 20240222142628.png]]

### Web Services Advantages
Allows programs written in different languages on different platforms to distribute in a standard base manner. It adapts the loosely coupled Web programming module for use in applications that are not browser based.

The goal is to provide a platform for building distributed systems using software
- running on different operating systems and devices
- written using programming languages and tools from multiple vendors
- all potentially developed and deployed independently 

## Semantic Web
A proposed development of the Web in which data in web pages is structured and tagged in such a way that it can be read directly by computers. The goal of the Semantic Web is to make Internet data machine-readable.

## Web Services Quality of Service
QoS is a key metric - the challenge here is the competition for network resources. Cracking the QoS challenges could give an application a competitive edge and results in a network accessible interface to application functionality, built using standard IP.

### Quality of Services (QoS) Metrics
**Performance**
- Speed of services requests (workload arrival rate)
	- Throughput - number processed in a particular time
	- Response time - time to complete a web service request
	- Latency - round trip delay
		- Connection latency
		- Request latency
		- User perceived latency
	- Execution time
- The aim is high throughput, low latency and low execution time
The challenge here comes from the uniqueness of the needs of each service architectures.

**Reliability**
- Delivery assurance
- Ability to perform the required function under the stated conditions for a specified time
The challenge here is that is relies on stateless protocols, and there is no guarantee of delivery.

**Integrity**
- Prevention of unauthorised access
- No modification of the data
- Good consistency
Transaction integrity is missing from SOAP, UDDI and WSDL.

**Interoperability**
- Ability to function with different languages and/or platforms
However, web services must conform to certain protocols to achieve this.

**Security**
- Non-repudiation (rejection of a proposal or idea)
- Authentication
- Authorisation
- Encryption
- Traceability
- Access control
The challenge here is the ability of the protocols to support proper security.