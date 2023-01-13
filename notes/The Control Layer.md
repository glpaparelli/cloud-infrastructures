The control layer includes software tools that are responsible for managing and controlling the underlying cloud infrastructure, and enables provisioning of IT resources for creating cloud services. 

The control layer can be deployed either on top of [[The Virtual Layer]] or on top of [[The Physical Layer]].
It recieves the requests from the service and orchestration layers and provisions the required resources to fullfill the service request.
The key functions of the control layer are resource configuration, resource provisioning and monitoring resources. 

## The Control Software
**The control software ties together the underlying physical resources and their software abstractions to enable resource pooling and dynamic allocation of resources.** 
It provisions resources for services and provides information about provisioned or consumed resources by service instances to the cloud portal and billing systems.

Before configuring the cloud resources the control software should discover all the underlying resources in order to know the total available resources in the environment for service provisioning.
This also provides a complete view of all the resources in the cloud environment and enables to centralize management of IT resources. 

The two types of control software are **element manager** and **unified manager**

### Element Manager
Infrastructure component vendors may provide the element managers as built-in or as external software. It is required to manage infrastructure components independently. 

![[element-manager.png]]

For example, storage vendors offer element manager along with the storage system to configure and make the storage resources available for the applications or services. 

The **key tasks performed by element managers** are the following:
- enables to perform initial component configurations and allow to modify it: installing guest OS, security settings, VLANs, RAID, ...
- allows to expand resource capacity: detects the newly added resources and adds them to an existing pool
- enables to identify the problem and performs troubleshooting
- monitors the infrastructure component for performance, availability, capacity and security

### Unified Manager
Provides a single management interface for configuring and provisioning resources for applications and services.
![[unified-manager.png]]

Most vendors today include native APIs with their management software packages so that administrators can integrate them with other supporing tools. 

Unified managers provide a single management interface to manage cloud infrastructure and provisioning resources for services. 
The unifide manager interacts with all standalone infrastructure elements through the elments; native APIs.

### Key Phases for Provisioning Resources
The key phases for provisioning infrastracture resources to cloud resources (using unified manager) are: 
- **resource discovery**
- **resource pool management**
- **resource provisioning**

#### Resource Discovery
Discovery operations create an inventory of the infrastructure resoruces, so that the unified manager can lear what resources are available for cloude service deployment. 
Discovery also provides info abou the asstes including their configuration, connettivity, capacity, ...

During discovery the unified manager caputers information about the infrastructure resources, such as: 
- compute systems (number of blade servers, CPU speed, ...)
- network components (switch model, network adapters, VLAN IDs, ...)
- storage systems (type of storage system, drive capacity, free capacity, RAID level, ...)

The discovery process is always ongoing since the virtual layer can spawn resources at will.

#### Resource Pool Management - Grading Pools
Once the discovery phase is "completed" the unified manager enables to manage resource pools. The virtual resources are created from these pools.
Unified managers allows an administrator to grade pools. Resource grading is a process that categorizes these pools based on various critiria, such as performance, capacity and availability. 
Pools with different grades are used to create a variety of service offerings, providing choices to the cloud service consumers. 
Costs/prices of resource pools differs depending on the grade.

#### Resource Provisioning
Resource provisioning involves allocating resources from graded resource pools to the service instances. 
Resource provisioning starts when consumers select cloud services from the service catalog. 
The unified manager on receving a provisioning request allocates the resources and integrates as per the service template to create an instance of the service. 

## Software Defined Approach
**The software defined approach abstracts all the infrastructure components and pools them into aggregated capacity**. It separates the control or management functions from the underlying components to the external software, which takes over the conrol operations to manage the multi-vendor infrastructure components centrally. 
**The software runs on a centralized compute system or a standalone device, called the software defined controller.** 
From a data center aspect of software defined approach, there is a software defined compute, software defined storage and software defined network.

![[sw-defined-approach.png|650]]

The **key functions of software defined controller** are: 
- **discovers underlying resources and provides an aggregated view of resources** by abstracting the underlying hardware and pooling it
- **enables the rapid provisioning of resources** based on pre-defined policies
- **enables to apply policies uniformly across the infrastructure components**, all from a software interface
- **provides interfaces that enable applications external to the controller to request resources** and access them

The **benefits of the software defined approach** are:
- **improves buisness agility:** minimizes resource provisioning time to get new services up and running
- **provides cost efficiency:** enables to effectively yse the existing infrastructure and low-cost comodity hardware to lower CAPEX
- **enables to achieve scale-out architecture**
- **provides a central point of access to all management functions**
- **allows to create new innovative services using the underlying resources**

## Resource Management
### Introduction to Resource Management. 
**definition:** The resource management is a process of allocating resources effectively to a service instance from a pool of resources and monitoring the resources that help in maintaining service levels. 

The **key goals of resource management** are: 
- **controls utilization of resources**
- **prevents service instance from monopolizing resources**

**Management server is used to centrally manage the resources** and it
- **enables defining policies**
- **configures and monitors the resources**
- **provides the ability to pool the resources**

### Resource Allocation Models
- **relative resource allocation:** resource allocation to a service instance is defined proportionally relative to the resource allocated to the other service instances
- **absolute resource allocation:** resource allocation for a service instance is based on defining a quantitative bound
	- lower bound guarantees minimum amount of resources
	- upper bound limits a service instance from consuming resources beyond a defined maximum level

**There is no right choice: it depends on the needs of the consumers and the market you are in**

### Key Resource Management Techniques
![[resource-management-techniques.png|650]]

