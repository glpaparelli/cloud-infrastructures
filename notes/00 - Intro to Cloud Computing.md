- **Cloud**: collection of network-accessible IT resources;
- **Cloud computing**: a model for enabling ubiquitous, convenient, on-demand network access to a shared pool of configurable computing resources (e.g. servers, storage, networks, applications, and services) that can be rapidly provisioned and released with minimal management effort or service provider interaction;

Cloud computing started as a business model and went down becoming a disruptive technology. Its main goal is to **decouple** the **provisioning of a service** from the **user** of that service.
 
Cloud has **5 characteristics**:
- **On-demand self-service**: consumer can request computing capabilities as needed without requiring human interaction. They could use a web-based self-service portal to view a service catalogue and request clouds services;
- **Broad Network Access**: capabilities are available over the network and accessed through standard mechanisms (OSI/TCP-IP, SOAP/REST) by heterogeneous thin/thick (e.g. browser/API) clients;
- **Resource Pooling**: provider's computing resources are pooled (collected) and served to multiple consumers at the same time using a **multi-tenant model** (i.e. the user view only its instance of the software, even if the server has other one going on, and resources are dynamically managed). There is a sense of location independence in that the customer generally has no control or knowledge over the exact location of the provided resources but may be able to specify location at a higher level of abstraction (country, state, and so on); ![[tenant-def.png|500]]
- **Rapid Elasticity**: capabilities can scale rapidly outward and inward, and the consumer could perceive them as unlimited;
- **Measured Service**: resource usage can be monitored, controlled, and reported. Cloud systems can automatically control/optimize resource use.

Cloud computing comes with a lot of benefits:
- **Business agility**: quick resource provisioning, reducing time-to-market;
- **Reduces IT costs**: resource utilization is optimised, reducing up-front capital expenditure;
- **High availability**: resource availability is ensured based on consumer's requirements, adding fault tolerance;
- **Business continuity**: impact of downtime is reduced (e.g. by using clusters, backups...);
- **Flexible scaling**;
- **Flexibility of access**: services can be accessed from anywhere;
- **Application development and testing**: on greater scale and on multiple platforms;
- **Simplified infrastructure management**: consumers manage minimal resources to access cloud services;
- **Increased collaboration**: sharing and simultaneous access to resources;
- **Masked complexity**: intricacies of IT operations are hidden from the users;

## Cloud Service Models (CSM)
A cloud service model specifies the services and the capabilities provided to consumers.

![[pizza.png]]

There are 3 primary cloud service models:
- **Infrastructure as a Service** (IaaS):
	- Consumer CAN: provision processing, storage, networks and deploy arbitrary software.
	- Consumer CAN'T: manage/control the underlying cloud infrastructure, even if it could have limited control on networking components (e.g. host firewalls);
	- **E.g.: rent a server**;
	- ![[iaas.png]]
- **Platform as a Service** (PaaS):
	- Consumer CAN: deploy applications created using tools (e.g. programming languages, libraries, services...) supported by the provider;
	- **E.g: Wordpress**;
	- ![[paas.png]]
- **Software as a Service** (SaaS):
	- Consumer CAN: use provider's applications;
	- **E.g.: Gmail, Office 365**;
	- ![[saaas.png]]

## Cloud Service Brokerage (CSB)
A **cloud broker** acts as an intermediary between cloud consumers and providers, adding value to the cloud services. He can manage use, performance and delivery of cloud services.

He can either do:
- **Service intermediation**: enhance/add value;
- **Service aggregation**: combine multiple services from a single agency into one or more new services;
- **Service arbitrage**: combine multiple services from multiple agencies into one or more new services.

## Cloud Deployment Models
A cloud deployment model specifies how a cloud infrastructure is build, managed and accessed. 

There are four primary cloud deployment models: 
- **Public**: open use by the general public;
- **Private**: exclusive use by a single organization (possibly comprising multiple consumers). It has 2 variants:
	- **On-premise**: deployed internally;
	- **Externally-hosted**.
- **Community**: exclusive use by a community (consumers from multiple organizations having shared concerns). It has 2 variants:
	- **On-premise**;
	- **Externally-hosted**;
- **Hybrid**: composition of multiple cloud infrastructures (public/private/community) bound by technology that enables data and application portability. Use-cases:
	- **Cloud bursting**: provisioning resources for a limited time from a public cloud to handle peak workloads;
	- **Web application hosting**: less critical applications can be hosted on public cloud;
	- **Application development and testing**: developing and testing applications in the public cloud before launching them.

## Building the Cloud Infrasturcture
The **reference model** is an abstract framework to define relationships among entities in an environment and for the development of standards/specifications. It facilitates communication between stakeholders and provides a point of reference for system designers to extract system specification.

![[cc-ref-model.png|550]]

The **Cloud Computing Reference Model** is composed of several **layers**:
- **Physical**: executes requests generated by virtualization and control layer.
	- Entities: Compute systems, network devices, storage devices, OS, protocol, tools, processes;
- **Virtual**: abstracts physical resources (making them appear as virtual) and executes the requests generated by control layer. It enables the multi-tenant environment.
	- Entities: Virtualization software, resource pools, virtual resources;
- **Control**: executes requests generated by service layer, enables configuration of resources/pools and resource provisioning, exposes resources to the service layer, collaborates with virtualization layer (resource pooling, virtual resources creation, dynamic allocation of resources).
	- Entities: Control software;
- **Service Orchestration**: provides workflows for executing automated tasks (e.g. provisioning tasks).
	- Entities: Orchestration software;
- **Service**: enables consumers to access and manage cloud services via a self-service portal, also storing information about cloud services.
- **Business Continuity**: supports all layers to provide uninterrupted services, ensuring their availability is in line with SLA (Service-Level Agreement). Specifies counter-measures to mitigate impact of downtime (i.e. proactive like risk assessment, backup, replication... or reactive like disaster recovery/restart);
- **Security**: supports all layers to provide secure services, deploying security mechanisms to meet GRC (Governance Risk and Compliance) requirements. Specifies administrative mechanisms (personnel policies, standardised procedures for safe execution of ops) and technical mechanisms (firewall, antivirus...);
- **Service Management**: adoption of 2 activities: service portfolio management (planning, budgeting/pricing, customers' support...) and service operation management (infrastructure configuration, capacity/availability management, monitoring...);

## Options for Building a Cloud Infrastructure
**Ways** to build it:
- **Greenfield**: infrastructure does not exist;
- **Brownfield**: some of the infrastructure entities exist;

**Solutions** to build it:
- **Integrating best-of-breed cloud infrastructure components**: like assembled pc, infrastructure components are integrated from multiple vendors;
- **Cloud-ready converged infrastructure**: like pre-fabricated pc, you buy a ready to be used infrastructure;

## Considerations for Building a Cloud Infrastructure
- **Governance**: enables service provider to ensure resources are implemented and used according to policies and procedures, and that resources are properly controlled and maintained, providing value to the organization; ![[governance.png|500]]
- **Organization**: new roles in cloud. They are:
	- **Service manager**: defines the service, manages SLA, ensure service meets consumers' expectation;
	- **Account manager**: responsible for the management of sales and relationships with customers;
	- **Cloud architect**: creates detailed designs for the cloud infrastructure;
	- **Service Operations Manager**: coordinates with different departments in order to streamline service delivery and execution.
- **Finance**: 2 concerns:
	- How much the consumer is expected to pay to meet the provider's business goal (recovery of cost, profit, reinvestment);
	- How consumers pay:
		- **Pay-as-you-go**;
		- **Subscription by time**;
		- **Subscription by peak usage**;
		- **Fixed cost or pre-pay**;
		- **User-based** (based on number of users logged in);
- **Tools**: virtualization, orchestration, security, business continuity, self-service portal, API...;
- **Avoid Vendor Lock-in**: consumer is unable to move from current provider to another;
- **Considerations for SaaS**: features must meet consumers' needs, software must be scalable, resilient and secure, software must be tested;
- **Considerations for PaaS**: provide application development platform to consumer, support variety of OS/application dev tools/deployment tools, ensure security and enough computing resources;
- **Considerations for IaaS**: provide infrastructure resources for deployment, ensure security;
- **Migration**: consumer may plan to migrate application or data in 2 ways:
	- **Forklift**: application is migrated at once. It is good for tightly couples or self-contained applications;
	- **Hybrid migration strategy**: application is migrated in parts. It is a lower-risk approach, good for applications having loosely couples components;
- **Testing**: it is a 4 step process;
	1) **Define**: define roles and responsibilities of personnel involved in testing;
	2) **Identify**: identify tools to perform test management and automation;
	3) **Design**:
		1) Design tests for data migration to cloud;
		2) Design test cases for different scenario (performance, stress cases, compatibility test...);
	4) **Test**: test cloud capabilities committed by provider, such as fault tollerance, disaster recovery and security controls.
