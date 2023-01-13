**definition:** Buisness Continuity entails preparing for, responding to and recovering from service outage that adversely affects buisness operations. 

**BC enables continuos availability of cloud services in the event of failure and helps to meet required service level.**
BC involves various proactive and reactive measures. Disaster recovery is a part of BC, which coordinates the process of restoring infrastructure, including data (required to support ongoing cloud services, after a disaster occurs)

## Cloud Service Availability
**Cloud Service Availability refers to the ability of a cloud service to perform its agreed functions according to buisness requirements and customer expecations during its specified time of operation.** 

**Service availability** is based on the agreed service time and the downtime, where the agreed service time is the period where the service is supposted to be available
$$
 \text{Service Availabilty (\%) =} \,\, \frac{\text{Agreed Service Time - Downtime}}{\text{Agreed Service Time}}
$$
### Causes of Service Unavailability
- **application failure:** bad logic in the code may cause catastrophic fails
- **data loss**
- **failure of dependent services**
- **data center or site down**
- **refreshing IT infrastructure**

### Impact of Cloud Service Unavailability
- **money:** cost of unavailability of services is greater than ever and outages could cost millions per hour
- **reputation:** unavailability of service also effects reputation
- **loss of revenue:** direct loss, compensatory payments, future revenue loss, ...

### Methods to Achieve Required Cloud Service Availabilty
**- building resilient cloud infrastructure facilitates meeting the requied service availability**
**- building resilient cloud requires infrastructure requires various high availability solutions**
	**- implementing fault tollerance mechanism**
		- deploying redundancy at both cloud infrastructure compnent level and site level to avoid single point of failure
	**- deploying data protection solutions sush as backup and replication**
	**- implementing automated cloud service failover**
	**- architecting resilient cloud applications**

#### Building Fault Tollerance Infrastructure
**definition:** **Single Points of Failure** refers to any individual component or aspect of an infrastructure whose failure can make the entire system or service unabailable. 

Single points of failure may occur at: 
- component level (compute, storage, and network)
- site or data center level

##### Avoiding Single Points of Failure
- SPoF can be avoided by implementing fault tolerance mechanisms such as redundancy (at component level: compute, storage and network)
- Implementing multiple service availability zones
	- avoids SPoF at data center (site) level
	- enable service failvoer globally
- it is important to have high availability mechanisms that enable automated service failover

![[avoid-SPoF.jpg]]

###### Clustering
**definition:** Clustering is a technique where at least two compute systems (or nodes) work together and are viewed as a single compute system to provide high availability and load balancing. 

**Clustering enables failover in the event of compute system failure to another system to minimize or avoid any service outage.** 

**Two common clustering implementations** are: 
- **active/active:** the redundant unit is active and ready to take action if needed
- **active/passive:** the redundant unit is off and it is activated to recovery the outage of the active compute system

Hypervisor cluster is a common clustering implementation in cloud environment

**Hypervisor Cluster**
Multiple hypervisors running on different systems are clustered. It provides continuos availability of services running on VMs even if a physical compute system or a hypervisor fails. 
Typically a live instance (i.e.m a secondary VM) of a primary VM is created on another compute system
![[hypervisor-cluster.jpg]]

###### Virtual Machine Live Migration
Running services on VMs are moved from one physical compute system to another without any downtime
- allows scheduled mainenance without any downtime
- facilitates VM load balancing

###### Link and Switch Aggregation
- **link aggregation:**
	- combines links between two switches and also between a switch and a node
	- enables network trafic failover in the event of a link failure in the aggregation
	- enables distribution of network traffic across links in the aggregation
- **switch aggregation:**
	- provides fault tolerance agains switch and link failures
	- improves node performance by providing more active paths and bandwidth
![[link-and-switch-aggregation.png|400]]

###### NIC Teaming
**definition:** A link aggregation technique that groups NICs so that they as a single, logical NIC to the OS or hypervisor. 

- provides network traffic failover in the event of a NIC/link failure. 
- distributes network traffic across NICs
- NICs within a team can be configured as active and standby

###### Multipathing
- enables a compute system to use multiple paths for transferring data to a LUN
- enables failover by redirecting I/O from a failed path to another active path
- performs load balancing by distribuiting I/O across active paths
	- standby paths become active if one or more active paths fail
![[multipathing.jpg|400]]

###### In-Service Software Upgrade (ISSU)
- **allows updating software on network devices (switch and routers) without impacting the network availability**
	- eliminates the need to stop the ongoing process on a device
	- ensures network availability as a result of a network device maintenance or upgrade process
- typically requires a network device with redundant control plane elements (supervisior or routing engines)
	- this setup allows the administrators to update the software image on one engine wile the other maintains network availability

###### RAID and Dynamic Disk Sparing
- **RAID:** combines multiple drives into a logical unit called a RAID set that provides data protection against drive failure
- **Dynamic Disk Sparing:**
	- automatically replaces a failed drive with a spare drive to protect against data loss
	- multiple spare drives can be configured to improve availability

###### Erasure Coding
Provides space-optimal data redundancy to protect data loss against multiple drive failure: a set of n disks is divided into m disks to hold data and k disks to hold coding information. 

###### Storage Resiliency Using Mirrored LUN
Mirrored LUN is created using virtualization appliance:
- each I/O to the LUN is mirrored to the LUNs on the storage systems
- mirrored LUN is continuosly available to the compute system
	- even if one of the storage systems is unavailable due to failure
![[mirrored-lun.jpg|400]]

##### Service Availability Zones
**A service availability zone is a location with its own set of resources and isolated from other zones**

A zone can be a part of a data center or may even be comprised of the whole data center
- enables running multiple service instances within and across zones to survice data center or site failure
- in the even of outage the service should seamlessy failover across the zones

Zones within a particular region are typically connected through low-latency network (enables faster cloud service failover)

###### Automated Service Failover Across Zones
- automated service failover
	- ensures robust and consistent failover
	- enables to meet stringent service levels
- automated failover process primarly depends on
	- replication across zones
	- live migration with streched cluster (zones in different remote locations)
	- reliable netowork infrastructure between zones
- **zones can be configured as active/passive and active/active configuration**

##### Data Protection
**Protecting critical data ensures availability of services: seamless service failover requires the avaiabilty of data**

Two common data protection solutions: 
- **backup**
- **replication**

###### Backup
**A backup is an additional copy of production data, created and retained for the sole purpose of recovering lost or corrupted data**

- RPO and RTO are the primary considerations in selecting and implementing a specific backup strategy
	- RPO specifies the time interval between two backups
	- RTO relates to the time taken to recover data from backup
		- RTO influences the type of backup target that should be used
- To implement a successful backup and recovery solutioon service proveders need to evaluate the backup methods along with their recovery consideratoins and retention requirements

- backup requires integration between backup application and management server of virtualized environment
- backup requiresements may differ from one service to another based of RTO and RPO (requires well-defined backup strategies to meet the requirements)
- recovery requires file level and/or full VM recovery
- huge volume of redundant data in the backup envirnoment
	- large number of VMs having identical data and configurations
- backup and recovery operations need to be automated

**Key Backup Components**
- **backup client**
	- gathers the data that is sto be backed up
	- sends the data to the storage node
- **backup server**
	- manages backup operations
	- maintains backup catalog
- **storage node:** responsible for writing data to backup device
- **backup device (backup target):** 
	- **tape library** 
	- **disk library**
	- **virtual tape library**
![[backups.png]]

**Backup Methods**
There are two key backup methdos:
- **guest-level**
- **image-level**

**Guest-Level Backup**
- Backup agent is installed on each VM. Performs file-level backup and recovery, it does not backup VM configuration files. 
- Performing backup on multiple VMs on a compute system may consume more resources and lead to resource contention

**Image-Level Backup**
- Image-Level Backup creates a copy of the entire virtual disk and configuration data associated with a particular VM image.
- The backup is saved as a single entity called a VM image. 
- No backup agent is required inside the VM to backup. Backup processing is offload from VMs to a proxy server

**Backup as a Service**
- enables consumers to procure backup services on demand
	- provides offsite backup for consumer desktops, laptops and application servers
	- backs up data to the cloud storage
- reduces the backup management overhead
	- transformation from CAPEX to OPEX
	- pay-per-use/subscription-based pricing
- gives consumers the flexibility to select a backup technology based on their current requirements

**Backup Service Deployment Options**
- **managed backup service**
	- suitable when a cloud service provider hosts consumer applications and data
	- backup service is offered by the provider to protect consumer's data
	- backup is managed by the service provider
- **replicated backup serice**
	- service provider only manages data replication and IT infrastructure at disaster recovery site
	- local backups are managed by consumers
- **remote backup service**
	- service provider receives data from consumers
	- backup is managed by service provider

Backup is also related to **data deduplication**, which is the process of detecting and identifying the unique data segmenets within a given set of data to eliminate redundancy. 
The deduplication process has 3 steps
- chunk the data set
- identify duplicate chunk
- eliminate the redundant chunk

###### Replication
**Replication** is the process of creating an exact copy of the data for ensuring availability of services (the already seem snapshots are a key ingrediant for replication)

