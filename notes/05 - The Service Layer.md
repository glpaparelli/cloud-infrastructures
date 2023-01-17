A **Cloud Service** is a collection of IT resources that are packaged by the service providers and are offered to the consumers.

The Service Layer exposes cloud services and do the following functions:
1) **Service catalogue**: provides central source of information on service offerings. The common elements are: category, name, description, features/options, support expectations, provisioning timeframe, reference to documents;
2) **Service ordering**: on-demand, self-provisioning of services. Consumers order or request services from a service catalogue unilaterally. The steps are:
	- **Choose** a service from a service catalogue;
	- **Click** on appropriate link to start ordering;
	- **Fill** up web form;
	- **Agree** to contract terms and submit the form;
3) **Cloud interfaces**: functional and management interfaces to consume services. There are 2 types:
	- **Management interface:** enables a consumer to **monitor, modify, start and stop** rented service instances. It varies based on service model; ![[management-interface.png|650]]
	- **Functional interface:** enables a consumer to **use** service functions. It varies based on service model; ![[functional-interface.png|650]]

## Cloud portal
A **cloud portal** is a web portal that **presents service catalogue** and **cloud interfaces**, enabling consumers to order and manage cloud services in an on-demand, self service way. A cloud portal is also accessed by the cloud administrators to manage cloud infrastructures and the lifecycle of cloud service. 

Cloud portals are hosted on one or more **portal servers**.

A cloud portal has **2 main functions**:
- **Presentation**: organization and display of service information and management functions to the users. It has 3 elements: service catalogue, management interface, link to functional interface (link to a service instance);
- **Interaction with orchestration layer**: sending service requests to orchestration layer and receiving response;

![[interaction-orchestration-layer.png|650]]

## Interface Standards and Protocols
**Cloud Interface Standardization**: a process to formulate a norm or a specification for common repeated use in regard to development and implementation of cloud interfaces for achieving uniformity across service. The **benefits** are clear:
- Establishes **conformity** to specify feature set or quality level;
- Enhances **portability** and **interoperability** across clouds.

Standards are cool and useful, their weak point is that they are slow when compared to technology. However, they are crucial because they help to avoid **vendor lock in**. Let's suppose I have a cloud based application deployed on AWS. If I want to move my application to Azure I have a big problem. It would be nice to have a standardized way to represent my architecture so that I'd be able to abstract from tech providers.

This doesn't address the problem completely: for example, if you are using a certain service and there are alternatives with the same functionality but not with the same performance you are still locked-in!

### Interface Standards for Portability
- Topology and Orchestration Specification for Cloud Applications (**TOSCA**): standardizes language to **define a service** independent of provider or hosting technology. Topology and plans can be interpreted by TOSCA compliant cloud. TOSCA is cool in theory but in the real world de-facto standard have been imposed by the tech providers (AWS, Azure...);
- Open Virtualization Format (**OVF**): open standard for packaging and distribution of **virtual appliances** (preconfigured software solution installed on a _virtual machine_). The OVF package includes metadata about VMs such as number of processors, memory space and network configuration;

OVF is slightly more successful than TOSCA.

### Interface Standards for Interoperability
![[interface-standards-interoperability.png|700]]

