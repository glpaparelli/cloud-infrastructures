The control layer includes software tools that are responsible for **managing** and **configuring** the underlying cloud infrastructure, and enables **provisioning** of IT resources for creating cloud services. 

The control layer can be deployed either on top of [[02 - The Virtual Layer]] or on top of [[01 - The Physical Layer]]. It receives the requests from the service and orchestration layers and provisions the required resources to fulfil the service request.

## The Control Software
The control software ties together the underlying physical resources and their software abstractions to enable resource pooling and dynamic allocation of resources. It **provisions resources** for services and **provides information** about provisioned or consumed **resources** by service instances to the cloud portal and billing systems.

Before configuring the cloud resources the control software should **discover** all the underlying resources in order to know the total available resources in the environment for service provisioning. This also provides a complete view of all the resources in the cloud environment and enables to centralize management of IT resources. 

There are 2 types of control software: the **element manager** and the **unified manager**.

### Element Manager
Element manager can control a **single infrastructure component independently**. Infrastructure component vendors may provide it as **built-in** or as **external** software. For example, storage vendors offer element manager along with the storage system to configure and make the storage resources available for the applications or services.

![[element-manager.png]]

The **key tasks performed by element manager** are the following:
- **Configuration**: enables to perform **initial component configurations** and allow to **modify** it. E.g.: installing guest OS, security settings, VLANs, RAID...;
- **Expansion**: allows to **expand resource capacity**: detects the newly added resources and adds them to an existing pool;
- **Troubleshooting**: Enables to identify the problem and performs **troubleshooting**;
- **Monitoring**: **monitors** the infrastructure component for performance, availability, capacity and security;

### Unified Manager
Unified manager can control **multiple infrastructure components**. It provides a single management interface for configuring and provisioning resources for applications and services. Most vendors today include native APIs with their management software packages so that administrators can integrate them with other supporting tools.

![[unified-manager.png]]

The **key tasks performed by unified manager** are the following:
- **APIs exposure**: it exposes APIs that can be integrated with the orchestration layer to automate service provisioning;
- **Expansion**: add/remove infrastructure resources to an already provisioned service;
- **Compliance**: performs compliance check during resource configuration;
- **Dashboard**: monitoring, reporting, root cause analysis.

#### Key Phases for Provisioning Resources
Using unified manager, the key phases for provisioning infrastructure resources to cloud resources are: 
1) **Resource discovery**: create an **inventory** of the infrastructure resources (compute systems, network components, storage systems), providing **useful information** (e.g. configuration, connectivity, capacity...). The discovery process is **always ongoing** since the virtual layer can spawn resources at will;
2) **Resource pool management**: manage and grade resource pools. Grading allows to categorize the pools based on various criteria (e.g. performance, capacity, availability...). Costs/prices of resource pools depend on the grade;
3) **Resource provisioning**: allocation of resources from graded resource pools to service instances. This process starts when consumers select cloud services from the service catalogue: the unified manager receives the provisioning request and allocates as per the service template to create an instance of the service;

## Software Defined Approach
Architecture that allows an infrastructure to be entirely under the control of software, with no operator or human intervention. It abstracts all the infrastructure components and pools them into aggregated capacity. We have:
- **Software Defined Compute**: manage the computing in a dynamic way;
- **Software Defined Storage**: manage the storage in a dynamic way;
- **Software Defined Networking (SDN)**: manage the network in a dynamic way;
- **Hyper-converged infrastructure (HCI)**: combines computing, storage and networking into a single system in an effort to reduce Data Center complexity and increase scalability. It is even more abstracted.

The **benefits of the software defined approach** are:
- **Improves business agility**: minimizes resource provisioning time to get new services up and running;
- **Provides cost efficiency**: enables to effectively use the existing infrastructure and low-cost commodity hardware to lower CAPEX;
- Enables to achieve **scale-out architecture**;
- Provides a **central point of access** to all management functions;

An important piece is the **Software Defined Controller**, an application that manages the flow control. Its key functions are:
- **Discovers** underlying resources and **provides an aggregated view** of resources by abstracting the underlying hardware and pooling it;
- **Enables** the **rapid provisioning** of resources based on pre-defined policies;
- **Enables** to **apply policies** uniformly across the infrastructure components, all from a software interface;
- **Provides interfaces** that enable applications external to the controller to **request resources** and **access** them;

![[sw-defined-approach.png|650]]

### HCI - HyperConverged Infrastructure
Data centers can be notoriously complex places where a multitude of vendors compete to deliver myriad different devices, systems and software. This **heterogeneous mix** often **struggles to interoperate** -- and rarely delivers peak performance for the business without careful, time-consuming optimizations. Today, IT teams simply **don't have the time** to wrestle with the deployment, integration and data center management challenges posed by traditional heterogeneous environments.

The notion of _convergence_ originally arose as a means of addressing the challenges of heterogeneity. Early on, a single vendor would gather the systems and software of different vendors into a single pre-configured and optimized set of equipment and tools that was sold as a package. This was known as **Converged Infrastructure** (CI): an **hardware-based** approach to converging storage and processes that reduces compatibility issues, complex deployments, and overall costs.

Later **Hyperconverged Infrastructure** (HCI) emerged: a **software-based** approach that virtualizes all of the elements of conventional "hardware-defined" systems. It includes, at a minimum, virtualized **computing** (a hypervisor), software-defined **storage**, and virtualized **networking** (software-defined networking). Importantly, the term ‘hyperconverged’ here does not imply that this technology is superior to regular converged infrastructures.

HCI shares storage resources across all the nodes in a virtual cluster and presents one or more logical units of storage to all the hosts within that cluster.

HCI surely **simplifies the management** and **speed-up the creation** process of the Data Center, but one needs to be careful of the **vendor lock-in**.

![[hci.png|650]]
HCI introduced some problems, respect to other proposed solution in ‘90s. Some operations are more “stable” on SAN while in HCI the workload can be not evenly distributed so you may have some VM that overloads the CPU of a server and data on that server gets slow. In a very traditional workload, like a standard database, the HCI model is not very suitable because maybe you can lost bandwidth but you get more reliability and maturity of the codebase of the storage respect to the HCI Model approach. Some parameters are useful:
- **RPO - Recovery Point Objective:** indicates how much time passes between the production of a data and its securing
- **RTO - Recovery Time Objective:** time it will take to have a full recovery. Relates to the time taken to recover data from backup

## Resource Management
Resource management is the process of **allocating resources effectively to a service instance** from a pool of resources and monitoring the resources that help in maintaining service levels. 

It **controls the utilization** of resources and **prevents** service instance from **monopolizing** resources. A **management server** is generally assigned to do the job.

We can allocate resources in 2 ways, depending on the needs of the customers and the market we are in:
- **Relative resource allocation**: based on resources allocated to other service instances;
- **Absolute resource allocation**: based on defining 2 quantitative bounds:
	- **Lower bound** guarantees minimum amount of resources;
	- **Upper bound** limits a service instance from consuming resources beyond a defined maximum level.

### Key Resource Management Techniques
![[resource-management-techniques.png|650]]

