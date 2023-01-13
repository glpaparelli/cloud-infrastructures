A **Data Center** is a large group of networked computer servers typically used by organizations for the remote storage, processing, or distribution of large amounts of data.

[OCP](https://www.opencompute.org/) is an organization that open source the design of hardware related to Data Centers (e.g. servers). It is defining new standards.

A **rack (armadio)** is a type of physical steel and electronic framework designed to house servers, networking devices, cables and other data center computing equipment.

![[rack.png]]

A rack has 3 main measures:
- **Server Rack Height**: most important measure, as it is often used to distinguish between racks. Generally, the hole spacing for standard 19″ racks on the mounting flange is spaced in groups of three holes. This three hole group is defined as a Rack Unit (RU) or just **Unit (U)**, which is defined as 1.75″ (44.45 mm) of vertical space. The Unit is the measure commonly used to define the height of a Rack; ![[rack-sizes.png]]
- **Server Rack Depth**: the depth is commonly measured in inches or cm. Server racks can range from 0 to 50-inches in depth, but are commonly seen at 24 and 48-inch depths; ![[rack-depth.png]]
- **Server Rack Width**: the most common standard rack width is 19 inches. Most rack-mounted equipment, especially servers, have a mounting width of 19 inches measured from one hole to another; ![[rack-width.png]]
- **Rack type**: there are 2 types:
	- **2-post rack**: constructed from 2 vertical upright support beams. It costs less and it has have stringent depth and weight restrictions. Unless of having very small equipment, they are not used;
	- **4-post rack**: constructed from 4 vertical upright support beams. Rails and shelves connect on all 4 posts. It can carry a lot of weight;

The most popular modern server rack is the **42U rack**, with the cabinet dimensions being 23.6″ - 600mm wide, 78.74″ - 2,000mm - 42U tall, and 39.37″ - 107cm deep. It is also common to use 48U racks.

In a Unit, following the standards, you can fit 2 2-CPU Servers, side by side, even if OCP has pushed to change the standard width in order to fit 3 3-CPU Servers. But in the end the standard didn't change.

Of course, the larger a rack, the less we can accommodate in room. But with larger racks is easier to manage cabling. However, the width of the rail is fixed.

In a Data Center, modular design comprehending **PoD** (Point of Delivery) is often used: a module of network, compute, storage, and application components that work together to deliver networking services. Typically, it is an aggregation of multiple racks. The PoD is a repeatable design pattern, and its components maximize the modularity, scalability, and manageability of data centers. 

## Floating Floor
Data Centers generally have a **floating floor** design, with composable raised tiles. Apart from supporting the equipment, they create a plenum space, which is used to route wiring and distribute conditioned air. Modern tiles can support on average $1.5t/m^2$, as racks are very dense at the moment.

## Cooling
Data Centers needs custom solutions for cooling. Consider that the air passing through a Rack gets outputted with a difference in temperature of about 10° C.

### CRAC
A **Computer Room Air Conditioning (CRAC)** unit is a device that monitors and maintains the temperature, air distribution and humidity in a data center, network or server room. They work via a refrigeration cycle where air is blown over a cooling coil filled with refrigerant. Refrigerant in the cooling coil is kept cold by a compressor. Excess heat is expelled as air, water or a glycol mixture.

Basically, you could just position the **CRAC** at the edge of the room to make it work: the cold air gets pushed in the floating floor, heated by the IT equipment and pulled through to the hot aisle behind where the CRACs’ air intakes are situated, and so the cycle continues. This design is fine for up to 5kw per rack, but not for today's multi-core processors (15-20 kw per rack). Also, it leads to unbalanced temperature section in the Data Center;
![[crac.png]]

Several techniques are now used to improve the cooling:
- **Hot/Cold Aisles**: one other key observation is to keep cold and hot air as separated as possible. ![[hot-n-cold-aisles.png]]
- **Hot/Cold Aisle Containment Systems**: further develop the *Hot/Cold Aisles* concept by introducing physical barriers that keep hot and cold air completely separate. Cold-Aisle Containment was popular when the temperature of the CPUs was at around 17/18C, so it was cheaper overall. Also, CACS is easier to retrofit into an existing, non-contained hot/cold aisle setup however, because the racks are already facing the correct way. Both HACS and CACS commonly make use of In-Row and, to a lesser extent, in-Rack cooling
- **In-Row cooling**: in between racks there are in-row coolers (e.g. CRAC), so that cool air is produced closer to the servers that heat it. Since they are very close to the servers, CRAC's fans can be run slower and the cooling is more responsive;![[in-row-cooler.png]]
- Blow cold air **directly into the rack**, to avoid dispersion which is caused by other designs. Racks then have a glass/crystal panel to further reduce dispersion;
- **Put fans in the building**: during the summer it rotates to eject hot air, during winter it rotates inverse to inject fresh air.

### Other techniques
Air conditioning may not be enough for modern processors. So, instead of CRAC, there are other techniques now:
- **Geo-thermal**: pushing the cables down in the terrain where it is cooler;
- **Liquid cooling**: water flows directly onto the CPUs, is risky but lowers temperatures of 40% approx. As the racks are getting more and more densed, chilling massive amounts of air became more costly, so liquid cooling is becoming more popular. This is what University of Pisa uses. We have big refrigerators outside of the building, which brings cold water inside the in-row cooler; ![[unipi-chillers.png]]
- **Oil cooling**: as liquid cooling, but with oil. Oil is an electrical insulator, but it can degrade and is flammable.

## Electrical Current
Nowadays, electrical current is transported via **Alternate Current (AC)**, since it is simpler to distribute and it allows to transport current for long distance without dispersion.

However, servers and other IT products in a Data Center run on **low-voltage Direct Current (DC)**, since it contains less components, which means less heat production, hence less energy loss.

A conversion to DC using can be done using _Direct Current Transformers_, using the Switching technology. You can get the power (W) obtained after the conversion using the formula:
$$W = cos(\theta) * V * C$$
where:
- V: tension;
- C: current;
- $cos(\theta)$: efficiency of the conversion. It depends on how the conversion is made, but nowadays a value of 0.96 is considered good.

### Power Usage Effectiveness (PUE)
PUE is a measure to describe how much energy is used by the computing equipment (in contrast to cooling and other overhead).

PUE is defined as:
$$PUE = \frac{\text{total current}}{\text{compute current}}$$
where *total current* is the **total amount of energy** used in the data centre and *compute current* is the **energy delivered to computing** equipment. An alternative measure exist, called **Data Centre Infrastructure Efficiency** (DCIE), which is simply the inverse of PUE.

As example, consider that the PUE of the university's data centre during 2018 is less 1.2, while the average italian data center's PUE are around 2-2.5 (they are basically using more electricity for chilling than what they are using for computing). A good design in a data center is one that compress as much as possible the PUE.

### Power Distribution
Current comes to the Data Center through 1 or more **lines** coming from different power plants (for reliability and fault tolerance reasons). The Industrial current has 380 Volts in 3 phases.

The lines are attached to a **generator**, a machine that converts mechanical energy into electrical power. It is thought as the long-term energy backup, but they have a long start time. It is the first step to increase the availability of the Data Center.

Then, the generator is usually connected to **UPS** (*Uninterruptible Power Supply*). It is a rack with **batteries** (not enough to keep-on the servers) that in some cases can power the Data Center for ~20 minutes. Them are also used to prevent current oscillation. Generally it is advised to have at least 2 of them.

The UPS is then attached to a **PDU** (*Power Distribution Unit*), a sort of power strip to divide electrical power among the devices (servers, switches...). Racks generally have 2 PDUs.
![[pdu.png|600]]

For redundancy reasons, servers are generally **dual-corded**, with electricity coming from 2 distinct electrical sources and arriving to 2 different PDU. If a dual-corded server has two 300-Watt power supplies, it can still draw no more than 300 Watts in your power design, because each power supply has to be able to handle the server's full load (not including power supply efficiency calculations).

Racks in the Data Center can be generally grouped in **three levels of density**: Low density racks run 3.5 to 5 kW; medium density run 5 to 10 kW; high density run 10 to 15 kW. Nowadays, it is common to have them at 16 or 32 KW (Cisternino). The amount of each rack type to allocate depends on your operation. Generally, data centers operate with about 50% low density cabinets, 35% medium and 15% high density. 

Example of rack PDU: 2 banks, 12 plugs each, 16 A each bank, 15 KW per rack, 42 servers per rack.

## Software Defined Approach
Architecture that allows an infrastructure to be entirely under the control of software, with no operator or human intervention. We have:
- **Software Defined Networking (SDN)**: manage the network in a dynamic way;
- **Hyper-converged infrastructure (HCI)**: combines storage, computing and networking into a single system in an effort to reduce Data Center complexity and increase scalability. It is even more abstracted.

## Networking
Most of the Data Center networking is performed at Layer 2 of ISO/OSI model.
Having everything in this layer can be problematic, introducing security, performance issues.

Key concepts:
- **MAC Address**: unique identifier assigned to a network interface controller (NIC) for use as a network address in communications within a network segment. It is 6 bytes;
- **Broadcast**: transferring a message to all recipients simultaneously;
- **Maximum Transfer Unit (MTU)**: maximum size allowed for a packet in a network. The standard is 1.5Kb, but it has become very popular to use the **Jumbo Frame**, which are of 9Kb;
- **Multiple protocols** relevant for Data Centers: LLDP, DCBX, ETS (standard way to prioritize the streams), LACP, RSTP (discussed later). *They were only mentioned in the lecture.*

Inside the Data Center the traffic tends to follow 2 main directions:
- **North-South**: traffic outgoing and incoming to the Data Center (internet);
- **East-West**: internal traffic between servers (intranet).

The more we aggregate computing units, the more East-West traffic we will have. As of today, most of the traffic inside a Data Center is East-West.

### VLAN
In all traditional data centers, VLANs (Virtual Local Area Networks) are used to enforce **Layer 2 isolation**: preventing communication between wired and wireless clients in the network.

A VLAN is a **logical overlay network** that groups together a subset of devices that share a physical LAN, isolating the traffic for each group. It partitions the broadcast domain, creating isolated computer networks.

It works by applying **tags** (from 1 to 4094) to network packets (in Ethernet frame) and handling these tags in the networking systems.
![[vlan.png]]

In a **multi-tenant** cloud environment, the provider typically creates and assigns a **separate VLAN to each consumer**. This provides a private network and IP address space to a consumer, and ensures isolation from the network traffic of other consumers.

### Cables
Cabling inside Data Center is pretty much static: once everything is setup, it's unlikely something will need to be changed.

The most common cables are:
- **Copper Cable**: most common. There are different types, each defined by their own plug:
	- RJ45: there are different categories:
		- CAT5: up to 5 Gbps;
		- CAT6 and CAT7: up to 10 Gbps;
	- Twinax;
- **Optical Fiber**: made of fiber of glass, with beam of lights inside it. The light is more robust to outside interferences, so it allows for greater bandwidth. As for RJ45, we have different evolutions of the cable (e.g. OM-4). There are 2 types:
	- **Multi-Modal** (850 nm wavelength for the light): cheap, covers distances up to 2km. Used in data centres. The multi-modal cables carries multiple beams of light projected at different angles simultaneously onto the core of the cable, but some of these light beams tend to disperse and collide. This collision weakens the signal strength after it travels a certain distance, this phenomena is called modal dispersion.
	- **Mono-Modal** (1250 nm wavelength for the light): expensive, lower loss, cover distances up to 60km. Used in WAN/MAN. Single-Modal cables carry a single ray of light projected at the centre of the core. The small core and the single light wave limits modal dispersion. Among all types of fibre cables, mono-modal cables provide minimal signal attenuation over maximum distance. A single-modal cable is used for long distance cable runs, limited only by the laser at the transmitter and the sensitivity of the receiver.
	- The **plugs** can be of 2 types:
		- **LC**: thinner, typically used inside Data Center because it is more manageable;
		- **SC**: thicker, typically used for MAN;
- Powerline;

#### Notes
**Documenting** from where to where a cable is going is **crucial**. Having cables correctly organised is important for management as well as for cooling (having a mess could act as an obstacle to the air flow).

### Network Switch
![[network-switch.png]] 
A **network switch** is networking hardware that connects devices on a computer network by using packet switching to receive and forward data to the destination device. It is capable of distinguishing between different recipients.

The internal of the switch is made of 2 planes:
- **Control plane**: a CPU and HDD to manage the switch's configuration. Now they run an OS (e.g. SONiC) and provide a CLI;
- **Data plane**: all the ports, connected to a NPU (Network Processing Unit) that manages the traffic. The configuration to do so is pushed from the control plane using a PCI-Express interface;

Data Center switches are usually **non-blocking**. It basically means that it has the forwarding capacity that supports concurrently **all ports at full capacity**.

Note that nowadays switches are not bounded to layer 2 only anymore: we have Layer 2 and Layer 3 switches. The main difference is the **routing** function: a Layer 2 switch only deals with MAC addresses, while a Layer 3 switch also cares about IP addresses and manages VLAN and Intra-VLAN communications.

An important piece in networking is the **transceiver**, an electronic device which can both transmits and receives signals. Contextualizing it to networking, we have transceivers to send/receive packages. In the case of optical fiber, transceivers allows to convert the electrical signal to optical signal, and viceversa.
![[transceviers.png]]

Transceivers (as well as their own plugs present in switches/servers), have seen many standards during the years:
- GBK, XFP: very old standards not used anymore. However, GBK (read: Gibik) is still used as a name to refer to the specific port for transceivers;
- **SFP (Small form-factor pluggable)**: 1 Gbps;
- **SFP+**: 10 Gbps;
- **SFP28 (SFP with 28 number of pins)**: 25 Gbps. Retro-compatible, can insert **SFP+** if needed;
- **QSFP+ (Quad SFP+)**: 40 Gbps. The cable is always SFP+, but there are 4 plugs;
- **QSFP28**: 100 Gbps. Retro-compatible, can insert **QSFP+** if needed;

#### OpenFlow
**OpenFlow** is a communication protocol that **gives access to the data plane** of a network switch or router over the network. With OpenFlow, the packet-moving decisions are centralized, so that the network can be programmed independently of the individual switches and Data Center gear.

In a conventional switch, packet forwarding (the data path) and high-level routing (the control path) occur on the same device. An OpenFlow switch separates the data path from the control path. The data path portion resides on the switch itself; a separate controller makes high-level routing decisions. The switch and controller communicate by means of the OpenFlow protocol (effectively doing Software Defined Networking).

### Network Chassis
The Network Chassis is a sort of big modular and resilient switch. At the bottom it has a pair of power plugs and then it's made of modular **line cards** (with some kind of ports) and a pair of **RPM** Routing Processing Modules (for redundancy) to ensure that the line cards work: they are CPUs responsible to receive the configuration entered in the console and propagate the configuration onto all the line cards.

![[network-chassis.png]]

The chassis can be over provisioned to resist to aging. They were popular until 2012, having 2 chassis (for redundancy), and then the chassis were connected to the rest of the Data Center, obtaining the so called **star-shaped network**.

Ultimately, they have become less and less interesting because the bandwidth of the network was growing so fast that became impossible to design it in a future-proof way.

### Spine and Leaf architecture
Since chassis are not an option anymore, we have to find a way to better organise all the switches in the Data Center, to ensure scalability, reliability and better performance. The Spine and Leaf architecture has become the dominant way to accomplish it.

The leaf layer consists of access switches that aggregate traffic from servers and connect directly into the spine or network core. 

This architecture consists of 2 layers:
- **Leaf layer**: aggregate traffic from the servers, providing redundant connections to servers;
- **Spine layer**: allows to interconnect all leaf switches in a full-mesh topology, performing routing;

Using this topology, any server can communicate with any other server with no more than one interconnection switch path between any two leaf switches, making it suitable for modern data centers that experience more East-West network traffic than North-South traffic.

![[spine-and-leaf.png]]

It is highly scalable: if the **bandwidth** is not enough, simply add an additional spine switch and connect it to all the leaf switches (it also reduces **oversubscription**, discussed later); if the ports are not enough, simply add a new leaf switch and connect it to all the spine switches.

A typical configuration of the ports and bandwidth of the leaves is:
- 1/3 going upwards (from leaves to spines) and 2/3 going downwards (from leaves to racks);
- 48 ports 10 (or 25) Gbps each, downward;
	- plus 6 ports 40 (or 100) Gbps each, upward;

Just a small remark: with spine and leaf we introduce **more hops**, so more latency, than the chassis approach. The solution for this problem is using as a base of the spine a **huge switch (256 ports)** which actually acts as a chassis, in order to reduce the number of hops and latency.

### Network loop
When a packet arrives on a port of the network switch, it gets copied on all the ports tagged with the same VLAN.

However, if we have 2 ports on the same switch on the same VLAN connected through a cable we have a **bridge loop**: the packet will continuously get copied without an end, causing a phenomenon called **broadcast radiation**. Since there is no TTL in layer 2, we will eventually saturate all the resources and bring down the system.

But having loops is essential because it allows redundancy: switch may fail, so it is important to be able to reach a server using another path.

There are 2 main strategies to manage loops:
1) **Spanning Tree Protocol (STP)**: builds a logical loop-free topology (spanning tree) for Ethernet networks. Taken a node as root, it builds a spanning tree from the existing topology graph, and disables all the arch that are not in use, obtaining a tree. The protocol also defines **Bridge Protocol Data Units (BPDUs)** packages for exchanging information. In 2001 the IEEE introduced **Rapid Spanning Tree Protocol (RSTP)** that provides significantly faster spanning tree convergence after a topology change. Using the Spanning Tree protocol, if we unplug a link the network will autofix in less than a minute, rebuilding a new tree with the edges previously discarded. However, nowadays it is used only in campus and not in datacenters, because of these drawbacks:
	- **High latency of convergence** (~50s), that is not sufficient for an always-on system (especially for East-West traffic);
	- **Little overhead** (even if today is neglectible);
	- **Active-passive redundancy**: assuming every server is connected to 2 switch, we are using half of the bandwidth at our disposal: we are considering only one link at a time in order to remove loops;
2) **Link Aggregation Control Protocol (LACP)**: instead of removing a link, this technique aggregates two different physical links between two devices into a logical point-to-point link. That means that both links can be used to communicate, increasing the bandwidth and gaining **active-active redundancy** in case of failure of a link (ensuring no loops because each link is a single channel);

### Oversubscription
It is the practice of connecting multiple devices to the same switch port to optimize use. For example, it is particularly useful to connect multiple slower devices to a single port to take advantage of the unused capacity of the port and improve its utilization. However, devices and applications that require high bandwidth should generally connect with a switch port 1-on-1, because multiple devices connected to the same switch port may contend for that port's bandwidth, resulting in poor response time. Hence, significant increases in the use of multi-core CPUs, server virtualization, flash storage, Big Data and cloud computing have driven the requirement for modern networks to have lower oversubscription. For this reason, it is important to keep in mind the **oversubscription ratio**, when designing your fabric.

In a leaf-spine design, this oversubscription is measured as the **ratio of downlink ports** (to servers/storage) **to uplink ports** (to spine switches). Current **modern network designs** have oversubscription ratios of **3:1** or less. For example, if you have 20 servers each connected with 10Gbps downlinks (leaf switches - servers) and 4 10Gbps uplinks (leaf switches - spine switches), you have a 5:1 oversubscription ratio (200Gbps/40Gbps).

QUESTION: In a Spine & Leaf architecture is it possible to have no oversubscription? Yes, and it is possible by just linking half the ports upwards and half down. This is the basis of the full fat tree.

#### Full Fat Tree
In this network topology, the link that are nearer the top of the hierarchy are "fatter" (thicker, which means high-bandwidth) than the link further down the hierarchy. **Used only in high performance computing** where performances have priority over budgets.

The full fat tree **resolves the problem of over-subscription**. Adopting the spine and leaf there is the risk that the links closer to the spines can't sustain the traffic coming from all the links going from the servers to the leaves. The full fat tree is a way to build a tree so that the capacity is never less than the incoming traffic. It's **quite expensive** and because of this reason some over subscription can be accepted.

![[full-flat-tree.png]]


# Storage & Compute
Storage and network are realted: the network is used to implement storage today. One of important aspect is that networking is stateless: the network is a **pure functional element** so the switchs have the configuration. This configuration determines the behaviour of the switch but this behaviour is also independent from the network’s flow.

**Memory Hierarchy**
![[memory-hierachy.png]]

Storage is about **state to be stored:** Tiered storage policies place the **most frequently accessed data on the highest performing storage.** Rarely accessed data goes on low-performance, cheaper storage that have larger capacity of storage.

**Caches**:
-   CPU Registries
-   CPU Cache

**Memory tiering**:
-   RAM
-   MCDRam: when you go multicore, like 72 core, the risk of contention is higher so they expanded the number of channel that can serve in parallel to reduce contention
-   nvRAM (see [nvDIMM](https://github.com/davePirol/ict-infrastructure-2022#nvdimm)): Non Volatile Dual Inline Memory Module allows to have a variation of current available on the bus so you can power persistent storage aside from RAM.

**Storage tiering**:
-   SSD Memory:
-   Hard drive: it’s a sort of tape, used for cold storage. ******************************************nb: defragmentation****************************************** allows to reduce the seek time by moving data across external cilinders of the disks that are also larger so can store more data. Latency is in the range of millisecond: this have impact also on bandwidth. The disk controller in a server is ********************12 Gigabit/s******************** for multiple driver.
-   Tapes

**Typical HDD figures**
![[hdd-specs.png]]

### Disk controllers, protocols and evolutions
The controller is a board inside the system that is responsible to talk to the disk using a block protocol and manage data transfer. It’s also responsible for RAID1.

**SCSI**
SCSI was basically a bus that allows you to connect multiple disk driver on a single flat cable (up to 16) and then attach the final cable to controller. The protocol was sophisticated enough to handle the communication to all the drives with a single flat cable.

A bus is a component where I can attach different [devices.It](http://devices.It) has a clock and some lanes (16 in PCI, ~15 GBps because each lane is slightly less then 1 GB). **Four drives are enough to exhaust a full PCI v3 bus**. They are also capable of saturating a 100 Gbps link, since a NVMe SSD has a bandwidth of 3.5 GBps 
(3.5 x 4 = 14 GBps => almost filled the 15 GBps of the PCI-e).

iSCSI: it’s basically the SCSI protocol on internet.

### SSD
In Solid State you actually consume the media: the measure of lifetime for SSD is TRD (Total Writes per Day). Internally an SSD have more than gigabytes than declared because they using ****************3D NAND**************** technology that layering multiple logic ports (NAND) on multiple layers. It’s showed that by time the NAND ports tend to lose the bit so there is an internal operating system that every 3 weeks rewrite the entire disk, refreshing the data stored. This is not visible from the user’s perspective.

## NVMe
![[NVMe.png]]

It's a protocol on the PCI-express bus and it's totally **controller-less**. From the software side it's simpler in this way to talk with the disk because the driver is directly attached to the PCI, there is no controller and minor latency.

A bus is a component where I can attach different devices. It has a clock and some lanes (16 in PCI, ~15 GBps because each lane is slightly less then 1 GB). **Four drives are enough to exhaust a full PCI v3 bus**. They are also capable of saturating a 100 Gbps link, since a NVMe SSD has a bandwidth of 3.5 GBps 
(3.5 x 4 = 14 GBps => almost filled the 15 GBps of the PCI-e).

NVMe has now almost totally replaced SATA, since the latter uses 2 PCIe lines and for that reasons represents the bottleneck considering the actual SSD speed.Furthermore, NVMe is often uses in the lower memory tier of the RAM: its speed is only one order of magnitude less than RAM, but can have a very big size without any problem. For that reason represent a valid super-fast cache level for the RAM and them started being associated in one single level to implement a big RAM tier, in a totally transparent way for the system.

Since the software latency in disk IOs is 5 microseconds more or less, TCP/IP software introduces also a latency of 70-80 microseconds, the disk is no more a problem. Indeed, the problem is now the network, not only for the latency, but also for the bandwidth: 4 NVMe totally saturates a 100 Gbps network.

**IOPS**: Input/output operations per second is an input/output performance measurement used to characterize computer storage devices (associated with an access pattern: random or sequential). It evolved from a stanrd of 1 Gigabit to 4 Gbyte.

Ruler SSD: the shape of the disk in different because it allows to cool down the temperature of the device. It have also different connectors and can store up to 1 PetaByte.
![[ruler-ssd.png|600]]

## Storage Aggregation
### Calculation on interface speed and size
Let’s say 4 Gigabit per second.

1 Terabyte = 1.048.576 bit / 4 = 262.144 second / 60 = minutes / 60 =72 hour so reading a full terabyte in your system throught an interface of 4Gigabit take 72 hour.

The aggregation is necessary both for redundancy and performance (by going parallel): there are many software (like BeeGFS or Lustre) that basically are file system designed to be highly parallel and highly performant, by losing redundancy.

Here a schema on Lustre:
![[lustre-schema.png|600]]

You can have up to 200,000 clients on a single storage: the system also keeps metadata which contains indexes and the object storage is where the storage is.

## RAID - Redundant Array Inexpensive Disk
The more common RAID configurations are:

-   RAID-0: striping, two drivers aggregated that works as a single one (no fault tolerance)
-   RAID-1: mirroring, write on both the drives, one is the copy of the other.
-   RAID-5: block-level striping with distributed parity. It's xor based: the first bit goes in the first disk, the second bit in the second one and their xor in the third. If one disk crashes I can recompute its content with the other two (for each two bits of info I need one extra bit, so one third more disk storage). This means mirroring with only 50% more space.
-   RAID-6: block-level striping with double distributed parity. Similar to RAID1 but with more disks.

Usually RAID is implemented inside a single server but **JBOD (Just Bunch of Drives)** it consists of optical fiber connected to the server that acts like a **head of storage** that is also connected to the disks.
![[jbod.png|600]]

Aside from JBOD, during the ‘90 emerged two forms of aggregated storage:
- **SAN - Storage Area Network:** assume that you have an HBA (Host Base Adapter) inside the server, that expose a subset of address space of the original storage. This allows to join multiple drive in a single or multiple other spaces and then exploit block-based protocol as if it was a standard drive inside the server. The typical configuration was to have two disk drives configured in RAID to allows the system to boot with an HBA.
	- Pro: is faster than NAS, it become modular
- **NAS: Network Attached Storage:** it’s accessed network file system that give you the representation of the file system via network calls
	- Cons: No total control over file system, based on network property
- **iSCSI:** despite it’s a block-based protocol it was proposed as a protocol for block-device file system but never used as it.
- **DAS - Direct Attach Storage:** direct attacha card inside the server that plays the very same roles as the HBA in SAN and expose the storage. The key point is that it’s directly attached so there is no switch in the middle, while in fiber channel there is a switch.

Surely these proposals were valid in ‘90s under the hypothesis that the disk was the bottleneck: nowadays we known, as seen in previous sec, that the bottleneck nowadays is the network.

Generally it’s better to slice the total aggregated storage in **LUN** or **Logical Unit**: it’s a virtual drive that expose a subset of the total aggregated storage to multiple servers. This approach can create concurrency problems between writing operations but exists a protocol to select a **writer server** among the servers connected to the disk, avoiding concurrency.

One problem of this approach is that LUN tends to fragmentation of data thus was introduced the **Dynamic LUN so grows and shrinks overtime.** I also can overbook my storage and exhaust the storage space. This is avoidable by attaching a controller process that checks the physical space available and compare it to the virtual space allocated to ensure that there is anough space to avoid overbooking.

When manage large storage drives, aggregated or not, we have to contemplate other methods or mechanism aside LUN, like:

- **Deduplication:** avoid duplication of file/same data among the all storage by identify them and allowing only a single copy of it.
- **Compression:** allows to save space and increase the performance of a storage because minimize the amount of bit to be transferred, enlarging bandwidth.
- **Snapshot/Checkpoint:** basically you can freeze the state of the drive and then keep change the state of the drive. Allows to go back to reverse all the changes. It’s like “versioning the drives”. To implement is, aside from technical and optimized algorithms, the basic idea is to have a tree in which at each level there is some version of your drive.

### HCI - HyperConverged Infrastructure
You basically can implement a SAN abstraction by means of software that is capable to joining the disk drives of multiple servers and make these servers appears as a single storage.

You have a specific virtual machine on any software node which is the storage virtual machine that talks with other nodes and coordinat ethe storage.

It’s the idea behind the Virtual Machine Storage on any VM.

It’s called HCI because you basically converge the three pillars of computing (1) network, (2) storage and (3) computer in a single, unified element.

![[hci.png|650]]

This model introduced some problems, respect to other proposed solution in ‘90s. Some operations are more “stable” on SAN while in HCI the workload can be not evenly distributed so you may have some VM that overloads the CPU of a server and data on that server gets slow. In a very traditional workload, like a standard database, the HCI model is not very suitable because maybe you can lost bandwidth but you get more reliability and maturity of the codebase of the storage respect to the HCI Model approach. Some parameters are usefull:

- **RPO - Recovery Point Objective:** indicates how many time passes between the production of a data and its securing
- **RTO - Recovery Time Objective:** time it will take to have a full recovery. Relates to the time taken to recover data from backup

### Compute - Part 1
Comparing a server with a standard PC, they shared only few things like instruction set, bootload and memory management. Generally, servers have a different architecture: more cache capacity, different types of drivers, use software mechanism to implement Error Correction Code for corruption memory checks, that is also perfomed ad physical layer by controller. In a server usually there is also another OS, aside from the one used to provide the service: it’s called **BMC - Bare Management Console** that is a fully-fledged OS. It exposes an HTTP server to allows, by a management dashboard, to see and modify system details.

**Let’s see the anatonomy of a server:**
![[server-anatomy.png|650]]
With this type of design, generally we can put 21 server inside a single rack.

**Another design can be the following:**
![[server-anatomy-2.png]]

**Pizzabox**
It have 2 CPU per unit and less space for drives.
![[pizzabox.png]]

**Blade:**
This design allows to simplify cabling and allows a shared infrastructure among the server inside che chassis. Have it’s own **BMC** and the chassis is active so that’s mean that it’s own firmware, OS, controllers, own network connectors positioned in back-plane and mid-plane.
![[blade.png]]

### 4-way CPU servers
They host 4 CPUs: this implies having a cross-bar between the 4 CPUs.

If a system is **NUMA - Non Uniform Memory Architecture** that means that you got too many memory baks so the performance of the memory modules become not really good.

If you make the server bigger so you make the unit of computation growing in capacity, you’re scaling up. If you are adding multiple servers to increase your capacity, so you’re creating a distributed system, you’re scaling out.

### GPUs
Having 4 GPUs in one unit of rack, you’ll need 2 kiloWatts power supplier to power the system, 500 W per GPU.

### Compute - Part 2
![[compute-capacity-kinds.png]]

**Based on a given problem, we classify the complexity by the problem’s size and the compute capacity required to solve the problem.**
- **Cloud:** my problem is to slice the server in small portions so that I can efficiently use the CPU, storage and network I have.
- **HPC:** for problems that require multiple nodes and usually need huge memory workload and not so much Input/Output (like Simulations). The structure of the problem is homogeneous.
- **Big Data:** again the problem require multiple nodes. The structure of the problem is not homogeneous because it depends on the data and not necessarily on the algorithm.
- **Machine Learning:** the structure of the problem is highly etherogeneous because it depends both on data and algorithms. The underlying model is variable in size and data in input.

The barrier with this type of highly computation problems is the power because each of those solution require a huge amount of power.

**At [HPC](https://top500.org/system/180047/) we can found an example of this HPC system "FRONTIER" with the following charateristics:**
![[frontier.png|600]]

**Another machine is the "SUPERCOMPUTER FUGAKU":**
![[fugaku.png|650]]

## How a CPU works
The architecture of a CPU is block-based: there are a number of function unit inside the CPU which runs in parallel that performs specific functions (cryptography, ALU, etc).

The process of building these blocks is executed by using ultraviolet light on a small surface that alter the property of the silicone: because we are physical at the limit of how distant can be the atoms inside the chip, the market create parallel processors.

Design parallel CPU it’s a complex task performed by specific software. Another approach adopted by Intel is to design what is called **chiplet,** basically 4 standard CPU in a single space. The advantage here is that are synchronized by the clock speed. The CPU controller is not anymore a chip installed on the motherboard but it’s inside the CPU itself: this allows to have 4 CPU syncrhonized and without delay of communication with the controller.
![[chiplet.png|200]]

Here the schema of **Intel Xeon Phi Processor called Knights Landing (KNL) - 2019**: on a single dice chip there are 72 cores. To communicate each other they need a bus protocol: KNL uses a bi-dimensional bus and as a communication protocol on bus the token ring. The bottleneck was the communication with the RAM so Intel introduced a 4 multi-channel RAM modules. So the CPU was shipped with 16 GB of RAM on the CPU.
![[xeon.png|650]]

## Silvermont Architecture - Core Design
![[silvermont.png|500]]

There is a parallel with the following schema and the previous one but it’s not immediate: surely there is inside the instruction cache, the branch predictor to estimate the branching jump, FPC Scheds that are the Floating Point Function, etc.

## Intel CPU Ring Architecture
![[cpu-ring-2.png|650]]

**Let’s first introduce the concept of ring:**
Operating systems provide different levels of access to resources. A **protection ring** is one of two or more hierarchical _levels_ or _layers_ of privilege within the architecture of a computer system. This is generally hardware-enforced by some CPU architecture that provide different CPU modes at the hardware or microcode level. Rings are arranged in a hierarchy from most privileged (most trusted, usually numbered zero) to least privileged (least trusted, usually with the highest ring number). Ring 0 is the level with the most privileges and allows direct interaction with the physical hardware such as certain CPU functionality and chips on the motherboard.

![[cpu-ring.png|400]]
This concepts allows the basic idea of virtualization by allowing to track which kernel (in case of multiple OS running on same machine) execute an operation and giving the right privileges.

The idea behind virtualization was embedded directly into the instruction set of the machine by designing a **Virtualization Instruction (VI).**

So that picking back from this idea on the fact that you can have multiple rings, that's introduce some specific instructions for virtualization that help to implement efficiently the transition between the different states so that when you have two kernels running into the memory, they were correct.

