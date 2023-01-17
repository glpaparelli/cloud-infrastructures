A **Data Center** is a large group of networked computer servers typically used by organizations for the remote storage, processing, or distribution of large amounts of data.

[OCP](https://www.opencompute.org/) is an organization that open source the design of hardware related to Data Centers (e.g. servers). It is defining new standards.

**A rack (armadio) is a type of physical steel and electronic framework designed to house servers, networking devices, cables and other Data Center computing equipment.**
![[rack.png]]

**A rack has 3 main measures:**
- **Server Rack Height**: **most important measure, as it is often used to distinguish between racks.** Generally, the hole spacing for standard 19″ racks on the mounting flange is spaced in groups of three holes. This three hole group is defined as a Rack Unit (RU) or just **Unit (U)**, which is defined as 1.75″ (44.45 mm) of vertical space. **The Unit is the measure commonly used to define the height of a Rack.** Basically a unit is the space needed to host a single blade server and their spacing in a single rack. ![[rack-sizes.png]]
- **Server Rack Depth**: the depth is commonly measured in inches or cm. Server racks can range from 0 to 50-inches in depth, but are commonly seen at 24 and 48-inch depths; ![[rack-depth.png]]
- **Server Rack Width**: the most common standard rack width is 19 inches. Most rack-mounted equipment, especially servers, have a mounting width of 19 inches measured from one hole to another; ![[rack-width.png]]

**There are two rack types:**
- **2-post rack**: constructed from 2 vertical upright support beams. It costs less and it has have stringent depth and weight restrictions. Unless of having very small equipment, they are not used
- **4-post rack**: constructed from 4 vertical upright support beams. Rails and shelves connect on all 4 posts. It can carry a lot of weight;

**The most popular modern server rack is the 42U rack, with the cabinet dimensions being 23.6″ - 60cm wide, 78.74″ - 2m - 42U tall, and 39.37″ - 107cm deep. It is also common to use 48U racks.**

In a Unit, following the standards, you can fit 2 2-CPU Servers, side by side, even if OCP has pushed to change the standard width in order to fit 3 3-CPU Servers, without success.

**Of course, the larger a rack, the less we can accommodate in room. But with larger racks is easier to manage cabling. However, the width of the rail is fixed.**

In a Data Center, modular design comprehending **PoD** (Point of Delivery) is often used: a module of network, compute, storage, and application components that work together to deliver networking services. **Typically, it is an aggregation of multiple racks.** The PoD is a repeatable design pattern, and its components maximize the modularity, scalability, and manageability of Data Centers. 

## Floating Floor
Data Centers generally have a **floating floor** design, with composable raised tiles. Apart from supporting the equipment, they create a plenum space, which is used to route wiring and distribute conditioned air. **Modern tiles can support on average $1.5t/m^2$**, as racks are very dense at the moment.

## Cooling
**Data Centers needs custom solutions for cooling. Consider that the air passing through a Rack gets outputted with a difference in temperature of about 10° C.**

### CRAC
A **Computer Room Air Conditioning (CRAC)** unit is a device that monitors and maintains the temperature, air distribution and humidity in a Data Center, network or server room. 
**Basically a CRAC is a glorified air conditioner.**
They work via a refrigeration cycle where air is blown over a cooling coil filled with refrigerant. Refrigerant in the cooling coil is kept cold by a compressor. Excess heat is expelled as air, water or a glycol mixture.

Basically, you could just position the **CRAC** at the edge of the room to make it work: the cold air gets pushed in the floating floor, heated by the IT equipment and pulled through to the hot aisle behind where the CRACs’ air intakes are situated, and so the cycle continues. 
**This design is fine for up to 5kw per rack, but not for today's multi-core processors (15-20 kw per rack).** 
Also, it leads to unbalanced temperature section in the Data Center;
![[crac.png]]

**Several techniques are now used to improve the cooling:**
- **Hot/Cold Aisles**: one other key observation is to keep cold and hot air as separated as possible. This is done by placing the racks in the way shown in the following image: the rows of racks are disposed to have their hot exhaust airs facing. This leads to hot and cold aisles (the rows of racks creates aisles and by how the racks are faced we have cold or hot aisles)![[hot-n-cold-aisles.png]]
- **Hot/Cold Aisle Containment Systems**: further develop the *Hot/Cold Aisles* concept by introducing physical barriers that keep hot and cold air completely separate. Cold-Aisle Containment was popular when the temperature of the CPUs was at around 17/18C, so it was cheaper overall. Also, CACS is easier to retrofit into an existing, non-contained hot/cold aisle setup however, because the racks are already facing the correct way. Both HACS and CACS commonly make use of In-Row and, to a lesser extent, in-Rack cooling
- **In-Row Cooling**: in between racks there are in-row coolers (e.g. CRAC), so that cool air is produced closer to the servers that heat it. Since they are very close to the servers, CRAC's fans can be run slower and the cooling is more responsive; ![[in-row-cooler.png]]
- Blow cold air **directly into the rack**, to avoid dispersion which is caused by other designs. Racks then have a glass/crystal panel to further reduce dispersion;
- **Put fans in the building**: during the summer it rotates to eject hot air, during winter it rotates inverse to inject fresh air.

### Other techniques
**Air conditioning may not be enough for modern processors.** So, instead of CRAC, there are other techniques now:
- **Geo-thermal**: pushing the cables down in the terrain where it is cooler;
- **Liquid cooling**: water flows directly onto the CPUs, is risky but lowers temperatures of 40% approx. As the racks are getting more and more densed, chilling massive amounts of air became more costly, so liquid cooling is becoming more popular. This is what University of Pisa uses. We have big refrigerators outside of the building, which brings cold water inside the in-row cooler; ![[unipi-chillers.png]]
- **Oil cooling**: as liquid cooling, but with oil. Oil is an electrical insulator, but it can degrade and is flammable.

## Electrical Current
Nowadays, electrical current is transported via **Alternate Current (AC)**, since it is simpler to distribute and it allows to transport current for long distance without dispersion.

However, servers and other IT products in a Data Center run on **low-voltage Direct Current (DC)**, since it contains less components, which means less heat production, hence less energy loss.

A conversion to DC can be done using _Direct Current Transformers_, using the Switching technology. You can get the power (W) obtained after the conversion using the formula:
$$W = cos(\theta) * V * C$$
where:
- V: **tension**;
- C: **current**;
- $cos(\theta)$: **efficiency of the conversion**. It depends on how the conversion is made, but nowadays a value of 0.96 is considered good.

Another formula to keep in mind is the Ohm's Law:
$$E = IR$$
where:
- E: Voltage (Volts, V);
- I: current (Ampere, A);
- R: resistance (Watts, W);
- Remember V=AW, VAW.

### Power Usage Effectiveness (PUE)
**PUE is a measure to describe how much energy is used by the computing equipment in contrast to cooling and other overhead.**

**PUE is defined as:**
$$PUE = \frac{\text{total current}}{\text{compute current}}$$
where *total current* is the **total amount of energy** used in the data centre and *compute current* is the **energy delivered to computing** equipment.
An alternative measure exist, called **Data Centre Infrastructure Efficiency** (DCIE), which is simply the inverse of PUE.

As example, consider that the PUE of the university's data centre during 2018 is less than 1.2, while the average italian Data Center's PUE are around 2-2.5 (they are basically using more electricity for chilling than what they are using for computing). 
**A good design in a Data Center is one that compress as much as possible the PUE.**

### Power Distribution
Current comes to the Data Center through 1 or more **lines** coming from different power plants (for reliability and fault tolerance reasons). The Industrial current has 380 Volts in 3 phases.

The lines are attached to a **generator**. A generator generates current by transforming mechanical energy in electrical energy: a generator may be alimented with oil, by burning the oil it generates heat and steam, then the steam moves a turbine that generates electrical energy. A generator in the 99.9% of cases just lets the current from the lines pass through. It the lines fails it is then turned on. It is logical to use the generator just to let pass the current from the power lines: if the lines fails everything is already connected to the generator.
It is thought as the long-term energy backup, but they have a long start time. It is the first step to increase the availability of the Data Center.

Then, the generator is usually connected to **UPS** (*Uninterruptible Power Supply*). It is a rack with **batteries** (not enough to keep-on the servers) that in some cases can power the Data Center for ~20 minutes. Them are also used to prevent current oscillation. Generally it is advised to have at least 2 of them.
The UPSs are meant to keep the data center alive the time needed by the generators to start producing current.

The UPS is then attached to a **PDU** (*Power Distribution Unit*), a sort of power strip to divide electrical power among the devices (servers, switches...). Racks generally have 2 PDUs.
![[pdu.png|600]]

For redundancy reasons, servers are generally **dual-corded**, with electricity coming from 2 distinct electrical sources and arriving to 2 different PDU. If a dual-corded server has two 300-Watt power supplies, it can still draw no more than 300 Watts in your power design, because each power supply has to be able to handle the server's full load (not including power supply efficiency calculations).

Racks in the Data Center can be generally grouped in **three levels of density**: Low density racks run 3.5 to 5 kW; medium density run 5 to 10 kW; high density run 10 to 15 kW. 
**Nowadays, it is common to have them at 16 or 32 KW (Cisternino).** 
The amount of each rack type to allocate depends on your operation. 
**Generally, data centers operate with about 50% low density cabinets, 35% medium and 15% high density.** 

**Example of rack PDU: 2 PDU, 12 plugs each, 16A each bank, 15 KW per rack, 42 servers per rack.**

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

**The more we aggregate computing units, the more East-West traffic we will have. 
As of today, most of the traffic inside a Data Center is East-West.**

### VLAN
In all traditional Data Centers, VLANs (Virtual Local Area Networks) are used to enforce **Layer 2 isolation**: preventing communication between wired and wireless clients in the network.

**A VLAN is a logical overlay network that groups together a subset of devices that share a physical LAN, isolating the traffic for each group. It partitions the broadcast domain, creating isolated computer networks.**

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

In a conventional switch, packet forwarding (the data path) and high-level routing (the control path) occur on the same device. An OpenFlow switch separates the data path from the control path. The data path portion resides on the switch itself; a separate controller makes high-level routing decisions. The switch and controller communicate by means of the OpenFlow protocol (effectively doing Software Defined Networking, discussed in [[03 - The Control Layer]]).

### Network Chassis
The Network Chassis is a sort of big modular and resilient switch. At the bottom it has a pair of power plugs and then it's made of modular **line cards** (with some kind of ports) and a pair of **RPM** Routing Processing Modules (for redundancy) to ensure that the line cards work: they are CPUs responsible to receive the configuration entered in the console and propagate the configuration onto all the line cards.

It is typical to use the chassis in a **star network**: two chassis are interconnected in active-passive mode (using the STP protocol, discussed later), which are then connected to the rest of the devices.

![[network-chassis.png]]

**Advantages**:
- **Cheap upgrades**: pay a big price at the beginning, then upgrades are cheap (add line cards);
- **Few cables**: everything is internal;
- **Easy to manage**: only 2 devices to manage (using the star-shaped network);
- **No oversubscription**;

**Disadvantages**:
- **Space**: they are big, and occupies rack units just for routing engines and other shared system components;
- **Hard to debug**: fabric links between line cards are internal to the chassis, usually proprietary;
- **Large fault domain**: losing a chassis means losing 1/2 of the bandwidth (using the star-shaped network);
- **Passive-Active**: the STP protocol only allows half of the bandwidth to be used, and the passive device can take several seconds to start and take the place of the active one;
- **Does not satisfy today's needs of big Data Center**: it's difficult to design a backplane for the chassis that offers terabits of bandwidth;

### Spine and Leaf architecture
The Spine and Leaf architecture has become the dominant way to organise the flow of the network traffic in Data Center. It employs fixed-configuration switches instead of modular switches (chassis).

This architecture consists of 2 layers of switches:
- **Leaf layer**: each of the switch in this layer connects to devices (e.g. servers). They aggregate traffic from the servers, providing redundant connections to servers. *A common alternative to a single switch per node, is to use 2 interconnected switches, which both connect to the spine, providing additional redundancy* (Cisternino);
- **Spine layer**: each of the switch in this layer connects to every switch in the leaf layer (i.e. full-mesh topology). They perform routing;

This architecture implements the LCAP protocol (discussed in the next section).

![[spine-and-leaf.png]]

**Advantages**:
- **Redundancy**: a leaf switch is connected to every spine switch, providing a robust architecture capable of resisting to all the spine switches going down before completely failing;
- **Minimization of latency for East-West traffic**: no matter which leaf switch a server is connected to, it must cross the same number of devices every time it connects to another server (the only exception is when the other server is on the same leaf). Generally, the path is randomly chosen, so that the traffic load is evenly distributed among the spine switches;
- **Scalability**: if the **bandwidth** is not enough or the **oversubscription** (discussed later) is an issue, we can add a **spine switch**. If the port density (number of ports available on a switch) is not enough, we can add a leaf switch. All of this without disrupting connectivity, as opposed to chassis;
- **Cost efficient**: fixed-configuration switches require less energy to work;
- **Greater bandwidth**: this is given by the employment of LCAP.

**Limitations**:
- **Significant amount of cabling**;
- **Limited hosts**: adding an host could lead to adding a new leaf switch. However, spine switches have a fixed amount of ports, thus we could get to a point where spine switches can't connect to the new leaf switch anymore;

Note that with respect to the chassis, spine and leaf introduces **more hops**, so more latency. The solution for this problem is using as a base of the spine a **huge switch (256 ports)** which actually acts as a chassis, in order to reduce the number of hops and latency (Cisternino).

A typical configuration of the ports and bandwidth of the leaves is:
- 1/3 going upwards (from leaves to spines) and 2/3 going downwards (from leaves to racks);
- 48 ports 10 (or 25) Gbps each, downward;
	- plus 6 ports 40 (or 100) Gbps each, upward;

### Network loop
When a packet arrives on a port of the network switch, it gets copied on all the ports tagged with the same VLAN.

However, if we have 2 ports on the same switch on the same VLAN connected through a cable we have a **bridge loop**: the packet will continuously get copied without an end, causing a phenomenon called **broadcast radiation**. Since there is no TTL in layer 2, we will eventually saturate all the resources and bring down the system.

**But having loops is essential because it allows redundancy: switch may fail, so it is important to be able to reach a server using another path.**
There are 2 main strategies to manage loops:
1) **Spanning Tree Protocol (STP)**: builds a logical loop-free topology (spanning tree) for Ethernet networks. Taken a node as root, it builds a spanning tree from the existing topology graph, and disables all the arch that are not in use, obtaining a tree. The protocol also defines **Bridge Protocol Data Units (BPDUs)** packages for exchanging information. In 2001 the IEEE introduced **Rapid Spanning Tree Protocol (RSTP)** that provides significantly faster spanning tree convergence after a topology change. Using the Spanning Tree protocol, if we unplug a link the network will auto fix in less than a minute, rebuilding a new tree with the edges previously discarded. However, nowadays it is used only in campus and not in Data Centers, because of these drawbacks:
	- **High latency of convergence** (~50s), that is not sufficient for an always-on system (especially for East-West traffic);
	- **Active-passive redundancy**: assuming every server is connected to 2 switch, we are using half of the bandwidth at our disposal: we are considering only one link at a time in order to remove loops. This could lead to oversubscription (seen later);
	- **Little overhead** (even if today is neglectable);
2) **Link Aggregation Control Protocol (LACP)**: instead of removing a link, this technique aggregates two different physical links between two devices into a logical point-to-point link. That means that both links can be used to communicate, increasing the bandwidth and gaining **active-active redundancy** in case of failure of a link (ensuring no loops because each link is a single channel);

### Oversubscription
It is the practice of connecting multiple devices to the same switch port to optimize use. For example, it is particularly useful to connect multiple slower devices to a single port to take advantage of the unused capacity of the port and improve its utilization. However, devices and applications that require high bandwidth should generally connect with a switch port 1-on-1, because multiple devices connected to the same switch port may contend for that port's bandwidth, resulting in poor response time. Hence, significant increases in the use of multi-core CPUs, server virtualization, flash storage, Big Data and cloud computing have driven the requirement for modern networks to have lower oversubscription. For this reason, it is important to keep in mind the **oversubscription ratio**, when designing your fabric.

In a leaf-spine design, this oversubscription is measured as the **ratio of downlink ports** (to servers/storage) **to uplink ports** (to spine switches). Current **modern network designs** should have an oversubscription ratio of **3:1** or less. For example, if we have 20 servers each connected with 10Gbps downlinks (leaf switches - servers) and 4 10Gbps uplinks (leaf switches - spine switches), we have a 5:1 oversubscription ratio (200Gbps/40Gbps).

**QUESTION: In a Spine & Leaf architecture is it possible to have no oversubscription? Yes, and it is possible by just linking half the ports upwards and half down. This is the basis of the full fat tree.**

#### Full Fat Tree
In this network topology, the link that are nearer the top of the hierarchy are "fatter" (thicker, which means high-bandwidth) than the link further down the hierarchy. **Used only in high performance computing** where performances have priority over budgets.

The full fat tree **resolves the problem of over-subscription**. Adopting the spine and leaf there is the risk that the links closer to the spines can't sustain the traffic coming from all the links going from the servers to the leaves. The full fat tree is a way to build a tree so that the capacity is never less than the incoming traffic. It's **quite expensive** and because of this reason some over subscription can be accepted.

![[full-flat-tree.png]]


## Storage
Storage and network are realted: the network is used to implement storage today. One of important aspect is that networking is stateless: the network is a **pure functional element** so the switchs have the configuration. This configuration determines the behaviour of the switch but this behaviour is also independent from the network’s flow.

**Memory Hierarchy**
![[memory-hierachy.png]]

Storage is about **state to be stored:** Tiered storage policies place the **most frequently accessed data on the highest performing storage.** Rarely accessed data goes on low-performance, cheaper storage that have larger capacity of storage.

**Caches**:
- CPU Registries
- CPU Cache

**Memory tiering**:
- RAM
- MCDRam: when you go multicore, like 72 core, the risk of contention is higher so they expanded the number of channel that can serve in parallel to reduce contention
- nvRAM (see [nvDIMM](https://github.com/davePirol/ict-infrastructure-2022#nvdimm)): Non Volatile Dual Inline Memory Module allows to have a variation of current available on the bus so you can power persistent storage aside from RAM.

**Storage tiering**:
- SSD Memory:
- Hard drive: it’s a sort of tape, used for cold storage. **nb: defragmentation** allows to reduce the seek time by moving data across external cilinders of the disks that are also larger so can store more data. Latency is in the range of millisecond: this have impact also on bandwidth. The disk controller in a server is **12 Gigabit/s** for multiple driver.
- Tapes;

**Typical HDD figures**
![[hdd-specs.png]]

### SCSI
SCSI was basically a bus that allows you to connect multiple disk driver on a single flat cable (up to 16) and then attach the final cable to controller. The protocol was sophisticated enough to handle the communication to all the drives with a single flat cable.

Note that a controller is a board inside the system that is responsible to talk to the disk using a block protocol and manage data transfer. It’s also responsible for RAID1.

iSCSI: it’s basically the SCSI protocol on internet.

### SSD
Solid state drives use flash memory (electrical, no mechanicals) to deliver superior performance and durability.

The measure of lifetime for SSD is **TWD** (Total Writes per Day). Internally an SSD have more than gigabytes than declared because they using **3D NAND** technology that layering multiple logic ports (NAND) on multiple layers. It’s showed that by time the NAND ports tend to lose the bit so there is an internal operating system that every 3 weeks rewrite the entire disk, refreshing the data stored. This is not visible from the user’s perspective.

#### SSD Interfaces
An interface connects two or more separate components to exchange data or information. The SATA and PCIe interfaces are the physical connections that transmit data from the memory storage to the computer.

##### SATA
The SATA interface was designed for hard drives, but when SSDs came on the market, they adopted the same interface so users could easily upgrade their storage drives.

If you have a SATA interface, only a SATA SSD will work with your computer.

##### PCIe
**PCIe (Peripheral Component Interconnect Express)** is a newer interface that features a smaller physical footprint, meaning it takes up less space in your computer, as seen in the image below. The real advantage of the PCIe interface over SATA is the ability to transmit data on up to four lanes, whereas SATA only has one. When combined with an NVMe SSD, which we’ll discuss shortly, PCIe SSD read/write speeds increase even more than SATA.

### NVMe
![[NVMe.png]]
**NVMe** is an open, logical-device interface specification for accessing a computer's non-volatile storage media attached via PCIe bus. This allow exponential speed increase with respect to classic SATA disks. NVMe SSDs combined with a PCIe interface create unrivaled read and write speeds. However, you can also get PCIe compatible SSDs that are non-NVMe.

It's totally **controller-less**. From the software side it's simpler in this way to talk with the disk because the driver is directly attached to the PCI, there is no controller and minor latency (Cisternino).

NVMe is what stopped the storage from being the bottleneck in basically every application. Since the software latency in disk IOs is 5 microseconds more or less, TCP/IP software introduces also a latency of 70-80 microseconds, the disk is no more a problem. Indeed, the problem is now the network, not only for the latency, but also for the bandwidth: 4 NVMe totally saturates a 100 Gbps network.

**IOPS**: Input/output operations per second is an input/output performance measurement used to characterize computer storage devices (associated with an access pattern: random or sequential). It evolved from a standard of 1 Gigabit to 4 Gbyte.

Extra: **Ruler SSD**. The shape of the disk in different because it allows to cool down the temperature of the device. It have also different connectors and can store up to 1 Petabyte.

![[ruler-ssd.png|600]]

### Cisternino - roba
A bus is a component where I can attach different devices. It has a clock and some lanes (16 in PCI, ~15 GBps because each lane is slightly less then 1 GB). **Four drives are enough to exhaust a full PCI v3 bus**. They are also capable of saturating a 100 Gbps link, since a NVMe SSD has a bandwidth of 3.5 GBps 
(3.5 x 4 = 14 GBps => almost filled the 15 GBps of the PCI-e).

### Storage Aggregation
### Calculation on interface speed and size
Let’s say we want to transfer 1 Terabyte through a 4 Gigabit/s interface.
- 1 Terabyte ~= 8 Terabit;
- 8 Terabit ~= 8,000 Gigabit;
- The transfer time would be: 8,000 / 4 = 2,000 s;
- 2,000 / 60 ~= 30min;

The aggregation is necessary both for redundancy and performance (by going parallel): there are many software (like BeeGFS or Lustre) that basically are file system designed to be highly parallel and highly performant, by losing redundancy.

Here a schema on Lustre:
![[lustre-schema.png|600]]

You can have up to 200,000 clients on a single storage: the system also keeps metadata which contains indexes and the object storage is where the storage is.

## RAID - Redundant Array Inexpensive Disk
**RAID** is a a data storage **virtualization technology** that combines multiple physical disk drive components into one or more logical units for the purposes of data redundancy. The goal of RAID is to improve disk performances, increase redundancy to protect the data or the ability to swap a disk without problems.

The more common RAID configurations are:
- **RAID-0**: striping, a minimum of two drives aggregated that works as a single one (no fault tolerance);
  ![[raid0.png]]
- **RAID-1**: mirroring, data is copied across multiple drives;
  ![[raid1.png]]
- **RAID-5**: block-level striping with distributed parity. It's XOR based: the first bit goes in the first disk, the second bit in the second one and their XOR in the third. If one disk crashes I can recompute its content with the other two (for each two bits of info I need one extra bit, so one third more disk storage). This means mirroring with only 50% more space;
  ![[raid5.png]]
- **RAID-6**: block-level striping with double distributed parity. Similar to RAID1 but parity is written to 2 drives.
  ![[raid6.png]]

**JBOD** (Just a Bunch Of Disks) is on the opposite side of RAID, and it means that your data is on single, stand-alone hard drives. If a one of your JBOD disks fails, the data on that disk is probably lost.

There are several **storage architectures**:
- **DAS** (Direct Attach Storage): a storage device is directly attached to a host device. It is **performant**, but it's **not suitable** when we want to provide storage connectivity to **multiple users**. It is also **not scalable**;
- **NAS** (Network Attached Storage): file-level data storage solution that provides storage via the network. NAS devices can provide simultaneous connectivity to **multiple users** and can support **RAID configurations**, but the **performance** is network-dependent;
- **SAN** (Storage Area Network): block-level data storage, using the iSCSI protocol to facilitate connectivity. It provides the **performance** of a DAS with the flexibility of a NAS, with **high scalability**, but it is very complex and costly;

Surely these proposals were valid in ‘90s under the hypothesis that the disk was the bottleneck: nowadays we known, as seen in previous sec, that the bottleneck nowadays is the network.

Generally it’s better to slice the total aggregated storage in **LUN** (Logical Unit Number). A LUN is a is a number used to identify a logical unit, which is a device addressed by the SCSI protocol or by Storage Area Network protocols that encapsulate SCSI, such as Fibre Channel or iSCSI. It is common to abuse the notation and refer to LUN as to the logical disk itself: a virtual drive that expose a subset of the total aggregated storage to multiple servers. Dividing the storage in LUN can create concurrency problems in a SAN between writing operations but there exists a protocol to select a **writer server** among the servers connected to the disk, avoiding concurrency.

One problem of this approach is that LUN tends to fragmentation of data thus was introduced the **Dynamic LUN so grows and shrinks overtime.** I also can overbook my storage and exhaust the storage space. This is avoidable by attaching a controller process that checks the physical space available and compare it to the virtual space allocated to ensure that there is enough space to avoid overbooking.

When manage large storage drives, aggregated or not, we have to contemplate other methods or mechanism aside LUN, like:
- **Deduplication:** avoid duplication of file/same data among the all storage by identify them and allowing only a single copy of it.
- **Compression:** allows to save space and increase the performance of a storage because minimize the amount of bit to be transferred, enlarging bandwidth.
- **Snapshot/Checkpoint:** basically you can freeze the state of the drive and then keep change the state of the drive. Allows to go back to reverse all the changes. It’s like “versioning the drives”. To implement is, aside from technical and optimized algorithms, the basic idea is to have a tree in which at each level there is some version of your drive.

## Compute
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

