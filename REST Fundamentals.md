# REST


## HTTP

### HTTP Requests
- Method: A verb like GET, POST, or noun like OPTIONS or HEAD
- Path: The path of the resource to fetch
- Version of the protocol: HTTP/1.1 or HTTP/2
- Headers: convey additional information for the servers.

### HTTP Response



## Collections
A collection is a group of elements with the same representation.

Supported Methods:
- GET: List the collection's elements
- POST: Insert an element to the collection
- PUT: Replace the entire collection with another collection
- DELETE: Delete the entire collection

## Elements
Represents a single entity

Supported Methods:
- GET: Get the element
- PUT: Update the element
- DELETE: Remove the element from the collection


## Remote Procedures
Use verbs that describe the procedure that is being executed
`/search/reply`

Use GET for safe procedures and POST, PUT, or DELETE for unsafe procedures


## What is REST?
REST stands for Representational State Transfer.
REST is an architecture for designing network-based applications.

#### REST is not a:
- Protocol
- Framework
- Standard

## REST Constrains
The REST architectural style describes six constraints. 
These constraints, applied to the architecture, were originally communicated by Roy Fielding in his doctoral dissertation and defines the basis of RESTful-style.

#### The six constraints are:
- Uniform Interface
- Stateless
- Cacheable
- Client-Server
- Layered System
- Code on Demand (optional)

## Choosing the right database
### Relational Databases
- Store data in tables
- Enforce strict schemas at the database level
- Queried using SQL
- Proven to work for sites of all sizes

### Document-Oriented Databases
- Store data in collections of documents
- Flexible schema for collecting aggregate data
- Queried using JSON
- Fast.growing and relatively new

### Scaling Relational Databases
- Sharding: Split in two tables
- Replication: Copy the tables
- Partitioning: Move tables to diferent DBs

### Scaling a Document-Oriented Database
- Sharding


## Load Testing
Apache Benchmark

## API Documentation
http://apidocjs.com/
https://swagger.io/
https://apiblueprint.org/
https://github.com/danielgtaylor/aglio
https://github.com/Aconex/drakov
https://apiary.io/

## API Versioning
http://restify.com/

## API Caching
### In Memory Data Stores
https://www.memcached.org/
https://redis.io/
https://varnish-cache.org/
 
 ## Reliability
 https://grafana.com/
 
 
 
 ## Identity
 
 ### SAML
It is an XML-based standard for communicating identity information between organizations and the cloud, It is used for enabling the secure transmittal of authentication tokens and other user attributes across cloud domains. 
 
 Entities involved:
 - User: Has a known account with the Entity Provider
 - Identity Provider: Maintains a directory of users and authentication mechanisms
 - Service Provider: Applications consumed by the User
 
 1. The user attempts to access SP.
    - If it is logged in, 
 2. IdP validates and if its correct it creates an Assertion, then it communicates with the SP and creates a session in the SP to access its resources.
 
 
 ## OAuth
 - User
 - Application
 - API
 
 Workflow:
 - Authorization Request
 - Authorization Grant
 