Adoption of cloud computing is significantly rising in organizations and it is seen as a leading "disruptive" thecnology in the coming decade. 
**Cloud computing started as a buisness model and went down becoming a disruptive technology.** 
**The main goal of the cloud is to decouple the provisioning of a service from the user of that service**
Cloud is driving optimization and innovation of buisness models in organizations and trends like mobility, big data, and social media are also influencing cloud adaption. 

# What is Cloud Computing
**definition:** a model for enabling ubiquitous, convenient, on-demand network access to a shared pool of configurable computing resources (e.g, servers, storage, networks, applications, and services) that can be rapidly provisioned and released with minimal menagement effort or service provider interaction. 

A cloud is a collection of network-accessible IT resources
- consists of a shared pools of hardware and software resources deployed in data centers
- enables consumers to hire a provider's IT resources as a service
 
## Essential Cloud CHaracteristics
- **On-Demand Self-Service**
- **Broad Network Access** 
- **Resource Pooling**
- **Rapid Elasticity** 
- **Meseaured Service**

### On-Demand Self-Service
**definition:** a consumer can unilaterally provision computing capabilities, such as server time and network storage, as needed automatically without requiring human interaction with each service provider.

Consumers use a web-based self-service portal to view a service catalog and request cloud services. 
This reduces the time needed to provision new or additional IT resources since there is no intervention from the provider.

### Broad Network Access
**definition:** capabilities are available over the network and accessed through standard mechanism that promote use by heterogeneous thin or thick client platform. 

Consumers access cloud services on any client/end-point defice from anywhere over a network, standard mechanisms (such as REST web services..) are used to support the use of heterogeneous client platforms.

### Resource Pooling
**definition:** The provider's computing resources are pooled to serve multiple consumers using a **multi-tenant model**, with different physical and virtual resources dynamically assigned and reassigned according to consumer demand. 
There is a sense of location independence in that the customer generally has no control or kownledge over the exact location of the provided resources but may be able to specify location at a higher level of abstraction (country, state, and so on). 
Examples of resources include storage, processing, memory and network bandwidth. 

Resource Pooling enables providers to improve resource utilization and to flexibily provision and reclaim resources.

![[tenant-def.png|650]]

### Rapid Elasticity
**definition:** Capabilities can be elastically provisioned and released, in some cases automatically, to scale rapidly outward and inward commensurate with demand. To the consumer the capabilities available for provisioning ofter appear to be unlimited and can be appropriated in any quantity at any time. 

Consumers can adapt to variations in workloads and maintain required performance levels over time and they may be able to avoid excessive costs from over-provisioning resources.

### Measured Service
**definition:** Cloud systems automatically control and optimize resource use by leveraging a metering capabilty at some level of abstraction appropriate to the type of service (e.g., storage, processing, bandwidth, ...).
Resource usage can be monitored, controlled, and reported, providing transparency for both the provider and the consumer of the utilized service. 

This enables billing of cloud services and helps providers with the capacity and service planning. 

## Cloud Computing Benefits
- **buisness agility**
	- enables quick resource provising 
	- facilitates innovation
	- reduces time-to-market
- **reduces IT costs**
	- reduces up-front capital expenditure (capex)
	- improves resource utilization
	- reduces energy and space consumption
- **high availabilty**
	- ensures resource availability based on consumer's requirements
	- enables fault tollerance
- **buisness continuity**
	- reduces impact of downtime (eg: cloud-based backup)
- **flexible scaling**
	- enables scaling of resources to meet demand
	- unilateral and automatic resource scaling
- **flexibility of access**
	- enables access to services from anywhere
	- eliminates depenency on a specific end-point device 
- **application develpoment and testing**
	- enables application development and testing at a greater scale
	- enables testing on multiple platforms
- **simplified infrastructure management**
	- consumers manage only those resources that are required to access cloud services
- **increased collaboration**
	- enables sharing and simultaneous access of resources and information
- **masked complexity**
	- intricacies of IT operations are hidden from the users

# Cloud Service Models and Service Brokerage
## Introduction to Cloud Service Models
A cloud service model specifies the services and the capabilities provided to consumers. 
Three primary cloud service models: 
- **infrasturcure as a service (IaaS)**
- **platform as a service (Paas)**
- **software as a service (SaaS)**

![[pizza-aas.png|650]]

### Infrastructure as a Service
**definition:** the capability provided to the consumer is to *provision* processing, storage, networks and other *fundamental computing resources where the consumers is able to deploy and run arbitrary software*, which can include os and applications.
The consumer does not manage or control the underlyuing cloud infrastrucutre but has control over OS, storage and deployed applications; and possibly a limited control of selecting network components (eg, host firewalls).

**e.g: rent a server**

### Platform as a Service
**definition:** the capability provided to the consumer is to **deploy onto the cloud infrastructure consumer-created or acquired applications** created using programming languages, libraries, services and tools supported by the provider. 
The consumer does not manage or control the underlying cloud infrastructure including network, servers, operating systems or storage, but has control over the deployed settings for the application-hosting environment.

**e.g: wordpress**

### Software as a Service
**The capability provided to the consumer is to use the provider's applications running on a cloud infrastructure**. The applications are accessible from various client devices through either a thin client interface (such as a web browser) or a program interface. The consumer **does not manage or control the underlying cloud infrastructure** including network, servers, OS, storage **or even individual application capabilities**, with the possible exception of limited user-specific application configuration settings.

**e.g: gmail or office 365**

## Cloud Service Brokerage (CSB)
**definition:** cloud services brokerage (CSB) is an IT role and buisness model in which a company or other entity adds value to one or more (public or private) cloud services on behalf of one or more consumers of that service.

CSB is provided by a **cloud broker**, which is an entity that acts as an intermediary between cloud consumers and providers. The cloud broker manages the use, performance, and delivery of cloud services.

### Categories of Cloud Services Brokerage
- **service intermadition:** the broker enhances and adds value to a given service
- **service aggregation:** the broker combines and integrates multiple services into one or more new services
- **service arbitrage:** similar to service aggregation except that the services being aggregated may vary

# Cloud Deployment Models
A cloud deployment model specifies how a cloud infrastrucure is build, managed and accessed. 
There are four primary cloud deployment models: 
- **public**
- **private**
- **community**
- **hybrid**

## Public Cloud
**definition:** the cloud infrastructures is provisioned for open use by the general public. It may be owned, managed and operated by a buisness, academic or government organization.
It exists on the premises of the cloud provider.

## Private Cloud
**definition:** the cloud infrastructure is provisioned for exclusive use by a single organization comprising multiple consumers (for example, buisness units). It may be owned, managed and operated by the organization itself or a third party contractor.
It may exists on or off premises.

There are two variants of private cloud
- **on-premise**
- **externally-hosted**

### On-Premise Private Cloud
The cloud infrastructure is deployed by an organization on its data center within its premises
- provides complete control over the infrastructure and data
- enables standardization of IT resources, processes and services. 

### Externally-Hosted Private Cloud
The cloud implementation is outsourced to an external provider. The cloud is hosted on the provider's premises and the consumers connect to it over a secure network (access policies isolete the cloud resources from other tenants).

## Community Cloud
**definition:** the cloud infrastructure is provisioned for exlusive use by a specific community of consumers from organizations that have shared concerns. It may be owned, managed and operated by one or more of the organizations in the community, a third party or some combination of them. 
It may exists on or off premises.

## Hybrid Cloud
**definition:** the cloud infrastructure is a composition of two or more distinct cloud infrastructure (private, community or public) that remain unique entities but are bound togheter by standardized or propritary technology that enables data and application portabilit.

**Hybrid Cloud is the norm today.**

This model has, among others, the following use cases: 
- **cloud bursting:** provisioning resources for a limited time from a public cloud to handle peak workloads.
- **web application hosting:** hosting less critical applications such as e-commerce applications on the public cloud.
- **migrating packaged applications:** migrating standard packaged applications such as email to the public cloud. 
- **application development and testing:** developing and testing applications in the public cloud before launching them. 

# Building the Cloud Infrasturcture
**definition:** a reference model is an abstract framework for understanding significant relationships among the entities of some environment, and for the development of consistent standards or specifications supporting that environment. 
It is based on a small number of unifying concepts and may be used as a basis for education and explaining standards. It is not directly tied to any standard/technology but it does seek to provide a common semantics that can be used unambiguously across and between different implementations. 

**A reference model:** 
- facilitates efficient communication of system details between stakeholders
- provides a point of reference for system designers to extract system specification

## The Cloud Computing Reference Model
![[cc-ref-model.png|550]]

### Physical Layer
Foundation layer of the cloud infrastructure, it specifies entities that operate at this layer:
- compute systems, network devices and storage devices
- operating environment, protocol, tools and processes

**The function of the physical layer is to execute the requests generated by the virtualization and control layer.**

### Virtual Layer
The virtual layer is deployed on the physical layer, it specifies entities that operate at his layer: 
- virtualization software
- resource pools
- virtual resources

**The function of the virtual layer is to abstract physical resources and make them appear as virtual resources and execute the requests generated by the control layer.**
The virtual layer enables mulitenant environment.

[[The Virtual Layer]]

### Control Layer
The control layer is deployed either on a virtual layer or on a physical layer. It specifies the entities that operate at this layer: the control software.

The **functions of control layer:**
- **enables resource configuration and resource pool configuration**
- **enables resource provisioning**
- **executes requestes generated by the service layer**
- **exposes resources** to and supports the service layer
- **collaborates with the virtualization software** and enables
	- **resource pooling and creating virtual resources**
	- **dynamic allocation of resources**
	- **optimizing utilization of resources**

[[The Control Layer]]

### Service Orchestration Layer
The service orchestration layer specifies the entities that operate at this layer: the orchestration software. 

The functions of the orchestration layer are:
- proivdes workflows for executing automated tasks
- interacracts with various entities to invoke provisioning tasks

[[The Orchestration Layer]]

### Service Layer
Consumers interact and consume cloud resource via the service layer. 
It specifies the entities that operate at this layer, such as the service catalog and the self-service portal.

The **functions of service layer are:**
- **stores information about cloud services in service catalog** and presents them to the consumers
- **enables consumers to access and manage cloud services** via a self-service portal

[[The Service Layer]]

### Cross-Layer Function: Buisness Continuity
It specify the adoption of meseaures to mitigate the impact of downtime: 
- **proactive meseaures:** 
	- buisness impact analysis
	- risk assessment
	- technology solutions deployment (backup and replication)
- **reactive measures:**
	- disaster recovery
	- disaster restart

[[The Cross-Layer Function - Buisness Continuity]]

### Cross-Layer Function: Security
It specify the adaption of: 
- **administrative mechanisms**
	- security and personnel policies
	- standard procedures to direct safe execution of operations
- **technical mechanisms**
	- firewall
	- intrusion detection and prevention systems
	- antivirus

Deploys security mechanisms to meet the GRC requirements (Governance, Risk and Complience). 
This function also supports all the layers to provide secure services. 

### Cross-Layer Function: Service Management
It specifies the adoption of activities related to: 
- **service portfolio management:**
	- defines service roadmap, service features and service levels
	- enstablishes budgeting and pricing
	- deals with consumers in supporting activities
	- performs market research
	- collects information about competitors
- **service operation management:**
	- enables infrastructure configuration and resource provisioning
	- enables problem resolution
	- enables capacity and availability management
	- enables compliance conformance
	- enables monitoring cloud services and their constituent elements

## Options for Building a Cloud Infrastructure
- **greenfield deployment option:** it is typically used when an infrastructure does not exist and an organization has to build the cloud infrastructure from the physical layer
- **brownfield deployment option:** it is used when "some" of the infrastructure entities exist, which can be transformed to cloud infrastructure by deploying the remaining entities required for the cloud infrastructure. 

## Solutiuns for Building a Cloud Infrastructure
Two main solutions: 
- **integrating best-of-breed cloud infrastructure components**
- **cloud-ready converged infrastructure**

### Integrating Best-of-Breed Cloud Infrastructure Components
Build the cloud infrastructure by integrating multi-vendor infrastructure components. 
It enables repurposing of the existing infrastructure components. 
It also allows oranizations to choose and switch vendors easly.

The problem is that it requires a significan amount of IT staff time on: 
- evaluating individual and disparate hardware compontents
- intalling and integrating infrastructure components
- testing hardware, middleware and software
- checking compatibility of all the coponents. 

### Cloud-Ready Converged Infrastructure
Converged infrastructure is a pre-packaged bundle of systems, including servers, storage, networking, and management software. 
Companies usually purchase these systems from one company, instead of buying the hardware and software components separately from different suppliers. 
Converged infrastructure systems are typically pre-configured and pre-tested, making them easier and faster to deploy when building out a data center.

This way as its pros, such as: 
- cost saving
- simplification
- ...
And its cons: 
- vendor lockin in the provider of the converge infrastructure
- increased complexity to add a new "external" component

## Considerations for Building a Cloud Infrastructure
We now covers some factors that have to be considered while building a cloud infrastructure. 

### Governance
**definition:** governance is the active distribution of decision-making rights and accountability among different stakeholders in an organization. It also describes the rules and procedures for making and monitorinmg those decisions to determine and achieve the desired behaviors and results. 

**IT governance** enables the serivce provider to: 
- ensure IT resources are implemented and used according to policies and procedures
- ensure the resource are properly controlled and maintained
- ensure the resources are providing value to the organization

Instituting IT governance involves establishing a review board.

![[governance.png|650]]

### Organization
There are many new roles because of cloud computing
- **service manager:** 
	- key interface between clients and IT staff
	- understands consumers needs and industry trends
	- ensures IT delivers cost-competitive services
	- manages consumers expectations of product offerings
- **account manager:**
	- supports service managers in service planning, development and deployment
- **cloud architect:**
	- creates detailed designs for the cloud infrastructure
- **service operations manager:**
	- streamlines service delivery and execution 
	- coordinates with architecture team to define technology roadmaps and ensure SLO's are met.

### Finance
Determines the price (or chargeback) that a service consumer is expected to pay to meet the provider's buisness goals (recovery of costs, profit, ROI, reinvestment goal)

**Chargeback Models**
- **pay-as-you-go:** 
	- metering and pricing is based on consumption of resources
	- consumers do not pay for unused resources
- **subscription by time:**
	- cost of providing a service for a subscription perios is divided among a predefined number of consumers
- **subscription by peak usage:**
	- consumers are billed according to their peak usage of IT resources for a subscription period
- **fixed cost or pre-pay:**
	- consumers commit needed resource upfront for a committed period
	- consumers pay fixed charge periodically through a billing cycle regardless of the utilization of resources
- **user-based:** 
	- billing is based on the number of users logged in

### Tools
Tools play an important role in building a cloud infrastructure: 
- virtualization and orchestration software
- security and buisness continuity software
- self-service portal software

Other tools that should be considered specially when deploying hybrid cloud, community cloud or brokerage service: 
- cloud integration tools
- application programming interface (API)
- specialized connection
- transformation and buisness logic programs

### Service-Level Agreement and Legal Contract
**definition:** a contract negotiated between a provider and a consumer that specifies various parameters and metrics, such as cost, service availabilty, maintanance schedules, performance levels, service desk response time and consumer's and provider's responabilities. 

The key points that must be included in a legal contract are:
- buisness level policies such as data privacy, data ownership, security and jurisdiction
- availability and performance metrics
- DR plan, exit plan, and penalties for not meeting SLA
- how unexpected incidents and prolonged service outage will be handled

### Avoid Vendor Lock-In
**definition:** a situation where a consumer is unable to move readly from the current provider to another. 

Causes for vendor lock-in includes: 
- high migration cost
- application requires significant re-engineering for migration
- restrictions or burdersome penalties imposed by the current provider

Vendor lock-in can be prevented by: 
- using open standard tools, APIs, and file formats
- including appropriate exit clause in the agreement

### Software Licensing Concerns
Tipically relevant to IaaS and PaaS models. 
Consumers can use their existing license if it is cloud enabled, otherwise: 
- pay additional fees may get their license cloud enabled
- may use software provided by the service provider

Providers must work to understand the software license rights and its usage.

### About SaaS
**Software as a Service:** 
- ensures the software offered are thoroughy tested
- ensures the new features and functionalities are developed to the software to meet consumer's needs
- ensures applications are scalable and can handle increasingly larger consumer workloads
- ensures the applications are resilient and can withstand failures such as 
	- underlying component failure
	- dependant service
- ensures the consumers are provided a secure environment

### About PaaS and IaaS
**Platform as a Service:**
- provides application development platform to the consumers
- support large variety of OS, application dev tools and deployment tools
- ensures the consumers are provided a secure environment
- provides the consumer the required computing resources to operate the application

**Infrastructure as a Service:**
- provides the consumer the required infrastructure resources to deploy their OS, application and data
- ensures that the consumers are provided with a secure environment

### About Migration
The consumer may plan to migrate application or only data. 

The two **application migration strategies** are: 
- **forklift:** 
	- entire application is migrated at once insted of in parts
	- good for thightly coupled or self contained applications
- **hybrid migration strategy:**
	- applications and its compontents are moved in parts
	- lower-risk approach to migrate applications to the cloud 
	- good for application that have loosely coupled components

For migrating data to cloud:
- consider copying data to cloud using replication technology
- consider factors such as network bandwidth, data security, integrity and jurisdiction. 

### About Testing
Testing the cloud infrastructure is a 4 step processes:
1) **define:** define roles and responabilities of personnel involved in testing
2) **identify:** identify tools to perform test management and automation
3) **design:** 
	1) design tests for data migration to cloud
	2) design test cases for different scenario (performance, stress cases, compatibilty test, ...)
3) **test:** test cloud capabilities committed by provider, such as fault tollerance, disaster recovery and security controls
