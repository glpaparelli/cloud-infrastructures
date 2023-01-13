**definition of Cloud Service:** IT resources that are packaged by the service providers and are offered to the consumers.

### Service Layer Functions
1) **enables defining services in a service catalog:** service catalog provides central source of information on service offerings
2) **enables on-demand, self-provisioning of services:** consumers order or request services from a service catalog unilaterally
3) **presents cloud interfaces to consume services:** cloud interfaces are functional and management interfaces

#### 1) Service Catalog
**Menu of service that lists services**, attributes of services, service level commitments, terms and conditions for service provisioning, and prces of services. 
You may see the service catalog as the app store for cloude services.

**Providers define services in a catalog and consumers order services from the catalog in a self-service way.** 

The **common elements of service catalog** are
- **service category**
- **service name**
- **service description**
	- what is the service?
	- what buisness process it supports? 
	- what value it provides? 
- **featuers and options**
	- what are the constraints, policies, and rules? 
	- what options are available for selection? 
	- ...
**- service and support expectations**
	- what are the qualities of the service? 
	- what are the available technical support services? 
- **provisioning timeframe**
- **reference to service-related documents** (for examle, SLA, specification sheet, ...)

#### 2) Service Ordering
1) **choose a service from a service catalog**
2) **click on appropriate link to start ordering**
3) **fill up web form**
4) **agree to contract terms and submit the form**

#### 3) Cloud Interfaces
**Enable computing and management of rented service instances.** 

There are two types of cloud interface: 
- **management interface:** enables a consumer to control his use of a rented service
- **functional interface:** enables a consumer to use service functions

![[cloud-interfaces.png|500]]

##### Management Interface
- **A self-service interface to monitor, modify, start and stop rented service instances**
- **it facilitates consumers to prepare desired functional interface**
- **management functions are different for service models**

![[management-interface.png|650]]

##### Functional Interface
Presents functional content of a service instance to perform computing activities. 
Functional content is different different for different service models. 

![[functional-interface.png|650]]

### Cloud Portal
**definition: Cloud Portal** 
A cloud portal is a web portal that presents service catalog and cloud interfacs, enabling consumers to order and manage cloud services in an on-demand, self service way. 
A cloud portal is also accessed by the cloud administrators to manage cloud infrastructures and the lifecycle of cloud service. 

Cloud portals are hosted on one or more portal servers and are created using portal software. A user may use the URL of the cloud portal to login to the portal.

A **cloud portal has two main functions:**
- **presentation:** organization and display of service information and management functions to the users
- **interaction with orchestration layer:** sending service requests to orchestration layer and receiving response

##### Presentation
A cloud portal commonly presents following elements:
- **service cataog**
	- lists and describes service offering
	- includes action buttons or links to order a service
- **management interface**
	- presents information about all services ordered by a consumer
	- includes action buttons or links to manage rented service instances
- **link to functional interface**
	- portal provides link to a provisioned service instance
	- consumer gets access to functional interface using the link

###### Layout of Management Interface
- **management interface is designed like a digital dashboard**
	- displays service information in real-time
	- provides a central point ti manage rented service instances
- **management interface is presented across portlets or windows**
	- portlets group management functions and service information

##### Interaction with Orchestration Layer
- **portal routes service requests to orchestration layer**
	- orchestration layer triggers appropriate workflows for process automation
- **portal receives response back from orchestration layer**
	- responses are presented to users

![[interaction-orchestration-layer.png|650]]

##### Personalization of Cloud Portal
- personalization helps displaying information based on user's identity, role, organization, ...
- personalization ensures that a user has his own view of portal content
- portal populates personalized content based on predefined policy

### Interface Standards and Protocols
**Cloud Interface Standardization:** A process to formulate a norm or a specification for commong repreated use in regard to development and implementation of cloud interfaces for achieving uniformity across service. 

The **benefits** are clear:
- **establishes conformity to specify feature set or quality level**
- **enhances portability and interoperability across clouds**

Standards are cool and useful, their weakpoint is that they are slow when compared to technology.

Their main use case? Let's suppose I have a cloud based application deployed on AWS. 
If I want to move my application to Azure I have a big problem. It would be nice to have a standardized way to represent my architecture so that I'd be able to abstract from tech providers.
**Standards are crucial because they help you to avoid vendor lockin.**

**Lockin is a tricky concept:** it does not only apply to the obvious things. 
If you are using a certain service and there are alternatives with the same functionality but not with the same performance you are still locked-in!

#### Interface Standards for Portabilty - TOSCA
**Topology and Orchestration Specification for Cloud Applications (TOSCA).** 
- standardizes language to define a service independent of provider or hosting technology
- topology and plans can be interpreted by TOSCA compliant cloud
	- facilitates portable deployment of services to any compliant

TOSCA is cool in theory but in the real world de-facto standard have been imposed by the tech providers (AWS, Azure, ...)

#### Interface Standards for Portability - OVF
**Open Virtualizaion Format.** 
- open standard for packaging and distribuition of virtual appliances: enables packaging services as a virtual appliances and facilitates portability across different cloud platforms
- OVF package includes metadata about VMs such as number of processors, memory space and network configuration
- Metadata is used by a cloud platform to deploy a service

OVF is slightly more successful than TOSCA

#### Interface Standards for Interoperability
![[interface-standards-interoperability.png|700]]

