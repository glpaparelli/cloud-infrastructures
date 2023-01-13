![[cloud-service-lifecycle.png]]

## Phase 1: Service Planning
**This phase involves making buisness case decisions for cloud service offering portfolio.** 

It has three subphases: 
- **assessing service requirements**
- **developing service enablement roadmap**
- **establishing billing policy**

### Assessing Service Requirements
![[assessing-service-requirements.jpg]]
- **Line of business** (**LOB**) is a general term which refers to a product or a set of related products that serve a particular customer transaction or business need.

#### Service Requirement Assesment Questions
- what services will be created or upgrated?
- what is the appropriate service model (SaaS, PaaS, or IaaS)?
- what levels of performance, availability and security will be provided? 
- who are target consumers? why would consumers desire these services? What is the projected demad level? 
- ...
- if a private or community cloud is chosen, will it be hosted on-premise or externally? 
- what are the regulatory compliance considerations, if any?

#### IT Readiness Assessment: Balanced Scorecard
![[balanced-scorecard.png|700]]

### Developing Service Enablement Roadmap
Service enablement roadmap guides the strategic direction to fulfill service requirements in the provider's organization. 
It provides a framework for needed IT transformation, necessary cloud solutions, eliminating skill gaps and implementation timeline.
![[developing-service-roadmap.jpg]]

### Establishing Billing Policy
**definition: Billing**
A process of generating bills from the resource usage data cloud services using predefined billing policies.

The billing system collects usage data for cloud services from the control layer to generate bill for each consumers
- meseaures number of units of service usage per consumer
- enables metering for cloud services

In private cloud, chargeback and showback are commonly used: 
- **chargeback:** ability to measure resource consumption per buisness unit and charge them back accordingly
- **showback:** reporting of service charges against resource usage without applying charges to buisness units

**Considerations for Billing Policy**
- **provider's buisness goals**
	- making profit
	- justyfing new capital spending
	- influencing consumption behaviors by buisness units
	- making IT more service aware and cost concious
	- comparing IT costs with the charges of the public service provider
- service-specific pricing strategy
	- identifying costs related to a cloud service
	- planning for recovery of cost cost recovery, profit, meeting ROI, ...
	- determining chargable unit of demand per service
	- determining price per chargable unit

## Phase 2: Service Creation
**It involves defining services in the service catalog and creating workflows for the service orchestration.**

The common activities during service creating are: 
- **defining service template**
- **creating orchestration workflow**
- **defining service offering**
- **creating service contract**

### Defining Service Template
**definition:** A service template is a collection of interrelated hardware and/or software components that constitute a service and work together upon deployment of a service. 

- **Resources are allocted, configured and integrated as per service template** to create an instance of a service: **a template provides standard to create predictable service instances**
- **service templates are defined in service catalog**
	- facilitates consumers to understand service capabilities
	- provides guidelines to create workflows for service orchestration
- **service template specifics may include fixed and/or customizable options**

### Creating Orchestration Workflow
Workflows for service orchestration are created and they enable automated allocation, configuration and integration of resources for a service, as per service template. 
According to the workflows, orchestrator interacts with infrastructure components. 

### Defining Service Offering
**definition:** A service offering is an entry in the service catalog that describes a service template combined with **contraints**, **policies**, **rules**, **price** and **SLA**. 
- **constraints:** restricting access to a service to certain individuals or groups
- **policy:** setting bandwidth quota, firewall configuration, and QoS on a per-service or per-consumer basis
- **rule:** guidelines for service deployment and scaling, limiting resource allocation and subscription period
- **price:** service charge, initial data transfer charge, fees for support and recovery of data
- **SLA:** service level targets and responabilities
	- what are the minimally acceptable performance and availability levels?
	- is there a limit on the amount of resources that can be consumed?
	- where will the primary copy of consumer's data will be stored? how it will be protected?
	- will consumers be notified if a law enforcement agency requests their data?
	- ....

![[service-offering-example.jpg]]

### Creating Service Contract
**definition:** A service contract is an agreement between the service provider and the service consumer stating the terms of service usage. The two parties enter into a contract describing agreements on pricing, SLAs, termination of service and any specific configuration options.

Service contract is commpnly presented on portal and it describes the terms and condition for using a service. The service contract must be established with the provider while ordering a service and it is established by agreeing to the terms and conditions. 

## Phase 3: Service Operation
**It involves ongoing management operations to maintain cloud infrastructure and deployed services.** 

Common **activities during service operation** are: 
- **discovering service assets**
- **managing service operations**

### Discovering Service Assets
**definition of Discovery:** an activity that creates an inventory of service assets and provides information about the asstes including their configuration, connectivity, functions, performance, capacity, availability, utilization and physical-to-virtual dependencies

**The discovery provides visibility to each service asset and enables monioring cloud infrastructure resources centrally.**

The discovery is performed using specialized tool. 
The discovery tool commonly interacts with service assets through APIs. The discovery is typically scheduled to occur periodically (but it may be initiated by cloud administrator or orchestrator). 

- what are the service assets? 
- what information needs to be collected for each service? what are the meseaurement metrics? 
- how frequently the information should be collected?
- ...

### Managing Service Operations
It involves service-related operations across cloud infrastructure and ensure&resotre service levels while continuosly optimizing management operations

Key **management operations** are: 
- **monitoring and reporting**
- **provisioning**
- **troubleshooting**

The key is to automate service operations as much as possible.

## Phase 4: Service Termination
**Phase that removes previously assigned service instances and releases resources to resource pool for redeployment to other instances.** 

It must not impact other service instances and cunsumer's data, resources and confidential information. 

A cloud service may be terminated in the following scenarios: 
- **natural termination by contract agreement**
- **initiated termination by a provider or a consumer** 
	- common reasons for provider to terminate service: 
		- buisness circumstances where provider can no longer offer a service
		- a disaster
		- significant consumer violation of contract terms
		- new hardware employment or software upgrade
	- common reasons for consumer to terminate service
		- buisness circumstances where consumer no longer needs service
		- service requirement was planned to be temporary
		- service perfomance or support is not acceptable

**The common activities in Service Termination are:**
- de-provisioning service instance
- handling consumer's data as per contract terms
- providing final billing reports
- asking for feedback to improve service