## Written Tests
### Test 2021
- **Discuss the spine and leaf fabric organization model. Why it is so popular? How does it affect the oversubscription of L2 fabric (assume switches 48/6 ports of 25Gbps and 100Gbps bw respectively and 32 ports by 100Gps)?**
	- We will use 48 downward, 6 upward;
	- Downstream: 48\*25 = 1200 Gbps;
	- Upstream: 6\*100 = 600 Gbps;
	- Oversubscription of 1:2;
	- However, we generally have 2 switches per leaf node, interconnected with each other two times (for redundancy). The ports used for this are generally the most performant, thus we are left with 48/4;
	- If we redo the computation we obtain oversubscription of 1:3.
* **Discuss the cloud reference model layers with particular attention to the physical, virtual and service orchestration layer. How these layer interact together? How are useful to chargeback/show back costs models?**
	* **Chargeback:** **applies the costs** of IT hardware, software, cloud services or shared services to the **business unit** in which they are used;
	- **Showback:** similar to chargeback, but the prices are for **informational purposes** only and no one is billed.
- **Discuss a Data Center architecture made of 16 racks, assuming a power distribution of 15 KW/rack with respect to cooling and cabling.**
	- Since the racks have a very high power consumption, we need to put very high focus on cooling. First, we would ideally prefer to spread the racks as much as we can in the room. We could assume of positioning them in group of 8, 4 faced against other 4. Since the racks needs to be very well cooled, we dispse them in order to form hot isles and and use containment systems to isolate the heat. To handle the generated heat we can use in row coolers between racks.
	- We will need to put particular care in cabling, making them as organised as possible: if they are not managed well, they could get in the way of the cooling process. The fabric can be placed in the spaces of the floating floor as much as possible.
	- Then, if bandwidth requisite are not much and the Data Center don't think of scaling too much, we could think of using 2 chassis for providing network connectivity, as they are easier to manage the cabling. Otherwise, a spine and leaf architecture could be used.
- **A service requires a sustained throughput towards the storage of 30 GB/sec, how would you organize the storage layer? Would you prefer SAN or HCI organization?**
	- 30 GB/s ~= 240 Gbps. It needs to be passed through optical fiber, and we need very high speed. HCI is easier to organise and maintain and for this speed it seems like a reasonable choice and it provides redundancy, less physical hardware and lower costs than SAN storage. However, in case we will have diverse, nonvirtualized systems, SAN might be the better choice (e.g. when we would like for storage to be shared).

### Test 2022
- **There is a need to install 128 dual socket servers in a Data Center to implement an HCI infrastructure. Propose an organization of the servers in clusters and rack and explain why and how fabric could be organized.**
	- Using the standard 42U racks, we will need at least 4 racks in total. 
	- We dispose the racks in order to form hot aisles, then we use the containment systems to isolate the heat and for dissipation we use in row coolers. 
	- since the datacenter is small, for the networking we can use a chassis if there is the certanity that the datacenter will not be expanded further
	- ...
	- **equal to the previous question**
- **Discuss the role of APIs in private cloud infrastructures. Why organizing software systems in smaller units (microservices) is more cloud friendly? What are the challenges that this organiztion may pose to security and SLA?**
	- APIs are used at every level of the cloud infrastructure: the physical components interacts with the virtualization system (hypervisor) thorugh APIs. The control software interacts with the virtual resources through APIs, the consumers use the service catalog thorugh APIs and so on. 
	- Microservices are more scalable, they can be migrated to other virtual machines since they are contenairized and offer multiple domains of isolation. Since the application is "distribuited" among multiple entities there is an expanded attack surface. For an organization may be more complex to define and respect the SLA if using a microservices architecture (e.g., in the SLA I may state that a certain number of instances of a given microservices are always active) 
- **A data center power distribution should deliver half megawatt in a large building. How would you organize the internal data center? Comment cooling and PUE**
	- Half MW = 500 kW. We want to achive a Power Usage Effectivness of 1.2, hence we have for computing, so we use the PUE as follows
		- PUE = 1.25 = total current / compute current = 500 kw / x -> x = 400
		- we have 400kW for computing
		- from this follows that, using 15kW for each rack, we can in theory have 26 racks
	- the power lines are connected to the ATS (automatic transfer switch, automaically choose which power line use) along with the generators, then after the generators we have UPSs that are capable of handling the power consumption for ~20mins. From the UPSs the cables reach the PDUs inside the racks and that's it.
	- the rest of the question is identical to the previous ones.
- **How would you dimension an HCI cluster in order to ingest 2TB of data every 30 min? Propose the number of servers, fabric and storage dimensioning**
	- the important part is that you need a 8Gbps bandwidth (33 min to ingest 2TB)
	- the rest is fluff as already discussed (disposition of racks, redundancy techniques, ...)

### Random Questions from Written Exams
- **Discuss the difference between spine and leaf fabric and the more traditional fabric architecture based on larger chassis. How bandwidth and latency are affected?**
	- **already done**
- **What actions can take the orchestration layer of a cloud system (and based on what information) in order to decide how many web server istances should be used to serve a Web system?**
	- **already done**
- **Design a data center that should contain 40 Racks, consuming 15 kW each. Discuss all necessary considerations, e.g. Power Distribution, Cabling, Cooling.**
	- **already done**

## Oral Questions
#### Cooling system of a physical DC affect the service catalog and SLA defined by the private cloud that runs on the physical infrastructure?
Yes. If the cooling system is not able to handle the heat of the data center then some services may not even be offered or it could be stated in the SLA that the given service has some peformance until a certain temperature is reached.

#### What can we say about the service catalog?
The service catalog is accessed by consumers that are interested in using the cloud as a service provider. It is a list of all the supported services that the cloud infrastructure of a given provider is capable of. 

#### How can service catalog be affected by physical constraints? Example of service that you can run with 15 kwatts per rack of power?
**The simpliest example is to imagine a service that is highly demanding in terms of computational power.** Heavy computation effects the power consumptions and the amount of heat generated. If the data center is not able to provide the required power or handle appropriately the cooling then such services would not be offered, hence effecting the service catalog. 
An example of service that is possible to run with 15kwats per rack is cloud storage. 

#### **What's a Full Fat Tree?**
Full Fat tree is a network topology where the link nearer to the top are fattier (thickier), as they have more bandwidth then the links in the lower levels. 
It is only used in high performance computing

#### What's Spine and Leaf architecture? Is there a limit of leaf in a network? What can i do if i finish the spine's ports?
The spine and leaf architecture is a way to organize the the network traffic flow in a data center. 

The architecture consists in a two layer of switches
- **leaf layer:** A certain number of servers are connected to a leaf switch. All servers in the end are connected to a leaf layer switch. The servers that are connected to the same leaf switch can already talk with each other
- **spine layer**: all the leaf layer switches are coonected to ALL spine layer switches. This allow every server to talk with every other server with at most 1-hop. This is also a very redundant architecture: if a spine layer switch fails the connection becomes just of 2-hops. 

Spine and Leafs has both pros and cons:
- **the pros are:**
		- redundancy
		- scalability (until a certain level)
		- minimization of east-west traffic
		- cost efficient
		- greater bandwidth
- **the cons are:**
		- heavy fabric
		- it can be hard to scale up if you have so many servers that you need a very high number of leafs: every leaf has to be connected to every spine, what if the spine has not enough ports?

**A typical configuration of the ports and bandwidth of the leaves is:
- 1/3 going upwards (from leaves to spines) 
- 2/3 going downwards (from leaves to racks);
- in a 54 ports scenario
	- 48 ports, 10 (or 25) Gbps each, downward;
	- 6 ports, 40 (or 100) Gbps each, upward;

#### **What's thin provisioning?**
**Thin provisioning involves using virtualization technology to give the appearance of having more physical resources than are actually available.** If a system always has enough resource to simultaneously support all of the virtualized resources, then it is not thin provisioned. 
The term thin provisioning can be used to refer to an allocation scheme for any resource: 
For example, real memory in a computer is typically thin-provisioned to running tasks with some form of address translation technology doing the virtualization. Each task acts as if it has real memory allocated. The sum of the allocated virtual memory assigned to tasks typically exceeds the total of real memory.

#### **What happen when you do a snapshot of a VM? How is the drive snapshoted?**
**Snapshots/checkpoint**: ability to freeze the state of a virtual machine whether the machine is stopped or even running. The cool part is that a checkpoint can be exported;

How (plain guessing): the hypervisor has access to the working memory ("ram") and non-volatile memory ("disk") of the VM. Copy those and you can basically clone the VM. 
(Differencing Diks may be useful in this scnario, see question "how doest live migration works")

#### **What is the main problem of SAN architecture in storage?**
- **it is complex to handle it**
- the bandwidth may be not enough
- the access to the SAN may be a single point of failure

#### **Why we use virtualization in servers?**
Virtualization allows to abstract the physical resources. 
This has a ton of advantages, from being able to see physical resources of different machines as a single pool of usable resources to be able to move the "software server" from a physical machine to another without interrupting the service. 

#### **How does live migration works? What are its physical constraints?**
One of the biggest advantage that virtualization introduce is the fact that you can have **differencing disk**. A differencing disk is **a virtual hard disk (VHD) that stores changes made to another VHD or to the guest operating system**. The purpose of differencing disks is to make it possible to maintain information about changes made so that they can be reversed if necessary. In a sense you can have **disk versioning**.

**This allows three of the most crucial points of virtualization:**
- **Snapshots/checkpoint**: ability to freeze the state of a virtual machine whether the machine is stopped or even running. The cool part is that a checkpoint can be exported;

This lead to **Motion/Live Migration**: **ability to move a virtual machine from a physical host to another one without interrupting the service.** 
**Live migration refers to the process of moving a running virtual machine (VM) or application between different physical machines without disconnecting the client or application.** 

Memory, storage, and network connectivity of the virtual machine are transferred from the original guest machine to the destination. 
The time between stopping the VM or application on the source and resuming it on destination is called 'downtime'. When the downtime of a VM during live migration is small enough that it is not noticeable by the end user, it is called a 'seamless' live migration.

**Once you have the ability to checkpoint how the live migration works is pretty intuitive.** 
Mind that this involves the virtual switch of the hypervisors in the two hosts machines, since if we move a virtual machine to another hosts than the network requests to that virtual machine have to be forwarded to the new "home" of the migrated virtual machine. This is possible since the virtual switch is a part of the hypervisor and the hypervisor is aware of the migration. This is a key of the cloud computing: it helps **decoupling** the physical infrastructure from the virtual systems. It allows to offer services even if the server is broken;

The constraints are (**plain guessing**, not provided) that you have to be able to handle the overhead needed by the migration.

#### **What's capacity management/planning? How CAPEX and OPEX are related to it?**
- **capacity planning:** you have to see the future and be able to predict the capacity (capacity of storage, capacity of computational power, whatever it is) that you are going to need to fullfil the services that you want to provide. 
- **capacity management:** ensures that a cloud infrastructure is able to meet the required demands for cloud services in a cost effective and timely manner

The planning affects the CAPEX since after the planning you pay upfront to buy the things you deemed necessary. 
The management affects the OPEX since handle things requires operational expenses. 

#### **What's RAID?**
- RAID stands for Redundant Array of Inexspensive Disk and it is a technique of installation of a group of physical disk that allow a system to see different disks as a single one. The goal of RAID is to improve disk performances, increase redundancy to protect the data or the ability to swap a disk without problems. 
- The main common raid configuration are:
	- **RAID 0:** two drive works as a single one to increase the speed of the drive, no redundancy
	- **RAID 1:** mirroring, for redundancy
	- **RAID 5:** mirroring using only 50% of space: 1 bit in a drve and the other in the other drive. If a drive fails you can recompute the data from a single drive
	- **RAID 6:** like 1 but with n disks instead of 2

#### **What is the Pizza Model?**
**The pizza model is analogy made to clarify the differences between IaaS, PaaS and SaaS.** 
- In the pizza model analogy
	- **legacy/traditional:** make the pizza by yourself at home
	- **IaaS:** "take and bake", the vendor provides the infrastructure (the oven, the gas, the table, ...) and you are responsible to buy the ingredients of the pizza and to bake it
	- **PaaS:** "pizza, delivery", the vendor provides the pizza, you are responsible only of the drinks and table
	- **SaaS:** "go to a pizzeria", the vendor provides everything, you just pay.

#### **Cooling and energy management. Definition of PUE.**
- **PUE**
	- **PUE stands for Power Usage Effectivness** and it is defined as the total current used divided by the amount of current dedicated to the actual computing.
	- PUE basically measures how much current you use to compute and how much is needed for cooling. 
	- A PUE of 1 it is perfect efficiency, a PUE of 2 means that for every watt dedicated to compute you need 2 watt for cooling. A PUE of 1.1 or 1.2 is considered acceptable
- **Cooling**
	- Cooling can be done in many ways and using different techniques and technologies:
		- plain CRACs: just use CRAC (glorified air conditioners) to cool the einvoironment in which the racks are.
		- hot/cold aisles: you dispose the rows of racks in order to have hot aisles (where the exhaust air of two rows of racks ends) and cold aisles (aisles where the server suck up cold air in order to dissipate heat). At the begining of hot aisles you place CRACs to manage heat
		- hot/cold aisles isolation: plexiglass to confine the heat in hot aisles, this prevent the heat to affect the einvorinment
		- in-row cooling: uses hot/cold aisles and aisles isolation in combo with in-row cooling devices (stackable cracs disposed between racs)

#### **What is NVMe?**
NVM Expres (Non-Volatile Memory) is an open, logical-device interface specification for accessing a computer's non-volatile storage media attached via PCI Express bus. This allow exponential speed increase with respect to classic sata disks. NVMe is what stopped the storage from being the bottleneck in basically every application.

#### **What's a Hyperconvergent infrastructure?**
- **Hyperconverged infrastructure (HCI) is a software-defined IT infrastructure that virtualizes all of the elements of conventional "hardware-defined" systems.** 
- HCI includes, at a minimum, virtualized computing (a hypervisor), software-defined storage, and virtualized networking (software-defined networking). 
- The primary difference between converged infrastructure and hyperconverged infrastructure is that in HCI both the storage area network and the underlying storage abstractions are implemented virtually in software (at or via the hypervisor) rather than physically in hardware. 
- Because software-defined elements are implemented in the context of the hypervisor, management of all resources can be federated (shared) across all instances of a hyper-converged infrastructure. 
- **The potential impact of the hyper-converged infrastructure is that companies will no longer need to rely on different compute and storage systems**, though it is still too early to prove that it can replace storage arrays in all market segments. It is likely to further simplify management and increase resource-utilization rates where it does apply.

#### **We want to implement a storage service with hundred thousand users how do you think about the infrastructure? Tell me about storage, servers and cooling.**
**See the written exams.**

#### **What's a LUN?**
**In computer storage, a logical unit number, or LUN, is a number used to identify a logical unit**, which is a device addressed by the SCSI protocol or by Storage Area Network protocols that encapsulate SCSI, such as Fibre Channel or iSCSI.

**A LUN may be used with any device which supports read/write operations**, such as a tape drive, but is most often used to refer to a logical disk as created on a SAN. 
**Though not technically correct, the term "LUN" is often also used to refer to the logical disk itself.**
**A "LUN" is  a virtual drive that expose a subset of the total aggregated storage to multiple servers.** 
This approach can create concurrency problems between writing operations but exists a protocol to select a **writer server** among the servers connected to the disk, avoiding concurrency.

#### **How is possible in an hypervisor to overbook the memory? How can you guarantee that a VM does not go in space memory of another VM?**
Really don't know, hopes he don't ask and if the does improvvise.

#### **Why Monitoring is important?**
Monitoring is crucial for a thousands of reasons:
- **billing:** some services may be pay-per-use, and monitoring how many resouces are used and by who is crucial to bill the consumers
- **SLA:** some performances may be agreed in the SLA and it is important to keep them under control
- **in order to know where to invest futher**
- **emergency reaction**
- ...

#### **What are the strategy to build a HA system?**
The main concept is the **redundancy**, redundancy of basically everything, from the delivery of current and going up.

**building resilient cloud requires infrastructure requires various high availability solutions**:
- **implementing fault tollerance mechanism:** redundancy to avoid SPoF
- **deploying data protection solutions sush as backup and replication**
- **implementing automated cloud service failover**
- **architecting resilient cloud applications**

#### **Discuss the role (functions) of the orchestration layer. Give an example workflow. Where does it lie in the cloud stack?**
**Service Orchestration:** automated arrangement, coordination, and management of various system or component functions in a cloud infrastructure to provide and manage cloud service.

The use orchestration software (aka the orchestrator) provides many benefits:
- **Shorter service provisioning time;**
- **Eliminates possibility of manual errors;**
- **Reduces operating expenses;**
- **Simplifies cloud infrastructure management.**

**The orchestrator provides a library of already defined workflows and an interface to build user defined workflows.** 

An example might be the workflow that remove a tenant (the how is in the intersection of "who cares" and "it's intuitive").

**The service orchestration is the 4th layer of the cloud stack, just beneath the service layer and on top of the control layer.**

#### **What is a virtual firewall? Where will you put it? And how many?**
A virtual firewall, aka cloud firewall, is a network security solution designed specifically for environments in which deploying hardware firewalls is difficult or impossible, such as public and private cloud environments; software-defined networks, or SDN; and software-defined wide area networks, or SD-WAN.

Like hardware firewalls, virtual firewalls grant or reject network access to traffic flows between untrusted zones and trusted zones. Unlike hardware firewalls – which are physically located on-premises in data centers – virtual firewalls are essentially software, making them ideal for securing virtual environments.

#### **How does live migration of a VM happen and would you prefer to do it over HCI or SAN?**
- first part kinda already answered before
- ideally over HCI: since HCI has everything virtualized, hence It may be more easy (plain guessing) to interact 