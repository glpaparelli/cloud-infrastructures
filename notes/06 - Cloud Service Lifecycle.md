This is mostly a summary of what we have seen so far, put into action from a service creator perspective.

![[cloud-service-lifecycle.png]]

## Phase 1: Service Planning
This phase involves making **business case decisions** for cloud service offering portfolio.

It has 3 subphases:
- Assessing service requirements;
- Developing service enablement roadmap;
- Establishing billing policy;

### Assessing Service Requirements
![[assessing-service-requirements.jpg]]
Note that **Line of business** (**LOB**) is a general term which refers to a product or a set of related products that serve a particular customer transaction or business need.

#### Service Requirement Assessment Questions
- What services will be created or upgraded?
- What is the appropriate service model (SaaS, PaaS, or IaaS)?
- What levels of performance, availability and security will be provided? 
- Who are target consumers? why would consumers desire these services? What is the projected demand level? 
- …
- If a private or community cloud is chosen, will it be hosted on-premise or externally? 
- What are the regulatory compliance considerations, if any?

### Developing Service Enablement Roadmap
Service enablement roadmap **guides** the **strategic direction** to **fulfil service requirements** in the provider's organization. It provides a framework for needed IT transformation, necessary cloud solutions, eliminating skill gaps and implementation timeline.

![[developing-service-roadmap.jpg]]

### Establishing Billing Policy
**Billing** is a process of **generating bills** from the resource usage data cloud services using predefined billing policies. The billing system collects usage data for cloud services from the control layer to generate bill for each consumers:
- Measures number of units of service usage per consumer;
- Enables metering for cloud services.

In private cloud, other 2 accounting strategies are commonly followed:
- **Chargeback:** **applies the costs** of IT hardware, software, cloud services or shared services to the **business unit** in which they are used;
- **Showback:** similar to chargeback, but the prices are for **informational purposes** only and no one is billed.

Both strategies are intended to shift responsibility to users and encourage them, as corporate customers, to become more aware of costs and treat IT services as they would any other utility.

## Phase 2: Service Creation
It involves **defining services** in the service catalogue and **creating workflows** for the service orchestration.

The common activities during service creating are: 
- Defining service template;
- Creating orchestration workflow;
- Defining service offering;
- Creating service contract;

### Defining Service Template
A **service template** is a **collection** of interrelated **hardware** and/or **software** components that **constitute a service** and work together upon deployment of a service. A template provides **standard** to create **predictable service instances**.

Service templates are defined in service catalogue., facilitating consumers to understand service capabilities.

### Creating Orchestration Workflow
Workflows for service orchestration are created/generated and they enable **automated allocation**, **configuration** and **integration** of resources for a service, as per service template. According to the workflows, orchestrator interacts with infrastructure components.

### Defining Service Offering
A **service offering** is an **entry** in the **service catalogue** that describes a service template combined with **constraints** (access restriction), **policies** (bandwidth quota, firewall configuration...), **rules** (service deployment/scaling, limiting resource allocation...), **price** and **SLA** (Service Level Agreement).

Example:
![[service-offering-example.jpg]]

### Creating Service Contract
A **service contract** is an **agreement** between the **service provider** and the **service consumer** stating the terms of service usage. The two parties enter into a contract describing agreements on pricing, SLAs, termination of service and any specific configuration options.

Service contract is commonly presented on portal and it describes the terms and condition for using a service. The service contract must be established with the provider while ordering a service and it is established by agreeing to the terms and conditions.

## Phase 3: Service Operation
It involves ongoing management operations to maintain cloud infrastructure and deployed services.

Common activities during service operation are: 
- Discovering service assets;
- Managing service operations;

### Discovering Service Assets
The **discovery** is an **activity** that provides **visibility to each service asset** and enables **monitoring** cloud infrastructure resources centrally.

The discovery is performed using specialized tool. The discovery tool commonly interacts with service assets through APIs. The discovery is typically scheduled to occur periodically (but it may be initiated by cloud administrator or orchestrator). 

### Managing Service Operations
Ensure and restore service levels while continuously optimizing management operations.

Key **management operations** are: 
- Monitoring and reporting;
- Provisioning;
- Troubleshooting;

The key is to automate service operations as much as possible.

## Phase 4: Service Termination
Phase that removes previously assigned service instances and releases resources to resource pool for redeployment to other instances.

It must not impact other service instances and consumer's data, resources and confidential information. 

A cloud service may be terminated in the following scenarios: 
- **Natural termination** by contract agreement;
- **Initiated termination** by a provider or a consumer;

**The common activities in Service Termination are:**
- De-provisioning service instance;
- Handling consumer's data as per contract terms;
- Providing final billing reports;
- Asking for feedback to improve service.