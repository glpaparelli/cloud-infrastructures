A **cloud infrastructure** can be seen (in an extremely simplified way) as a **distributed operating system** in a Data Center.

![[cc-ref-model.png|650]]

In general, the virtual layer is strictly needed to create a cloud, even if most clouds are based on virtualization. In the above image, the small dent of the yellow layer that touch the physical layer is for this use cases, it is possible to provision the actual physical machine. Microsoft, Amazon and others allow you to actually "rent" the physical machines.

However this cases are not common: **in general the physical layer is dominated by the virtual layer.**

The ultimate **goal** of the virtualization layer (and in a sense of the whole cloud infrastructure) is to be able to **pool all the resources of multiple servers in a single set** so you can allocate and provision this resources to specific users and when not needed anymore let the resources go back in the pool.

## HyperVisors
A hypervisor, also known as a virtual machine monitor or VMM, is **software that creates and runs virtual machines (VMs)**. A hypervisor allows one host computer to support multiple guest VMs by virtually sharing its resources, such as memory and processing.

We can distinguish between 2 types:
- **Type-1, native or bare-metal hypervisors**: these hypervisors run directly on the host's hardware to control the hardware and to manage guest operating systems. It generally has no GUI. Hyper-V and KVM are the most famous example;
- **Type-2 or hosted hypervisors**: these hypervisors run on a conventional operating system (OS) just as other computer programs do. A virtual machine monitor runs as a process on the host. Type-2 hypervisors abstract guest operating systems from the host operating system. VirtualBox is the most famous example.

Of course, it is also different in the way they act. For example, VirtualBox gives you access to the network by installing a virtual network card on your (virtual) operating system while inside hypervisors such as HyperV there is a virtual switch(s) with VLANs.

## Virtualization
Virtualization allows us to **execute arbitrary code by emulating the necessary underlying structure**, may it be software or hardware.

It is possible to **exploit virtualization features** even in **non-virtualized images**. For example: it is possible to create a **virtual hard drive** in any windows based computer and assign to it an arbitrary amount of space, even if that space is actually not available in the underlying hardware. A simple use case of this is when a certain program requires a certain amount of space "just in case" but you are sure that it will never need that space. In this scenario you simply fix the problem by creating a virtual disk.

Our concept of virtualization is interesting because we **virtualize "over the same environment"** (x86 architecture emulates something that runs on an x86 architecture, we do not do "cross virtualization" such as android over x86). This obviously allows to make the virtualization process **more thin** because we can exploit directly the underlying structure. At the end of the day this virtualization mechanism a way to have multiple operating system's kernels and protection manager that become hierarchical. 

In the past we had the hardware and on top of that we had the operating system that was responsible of providing resources. Now:
- We have the **hardware**;
- The hardware hosts an **hypervisor**;
- The hypervisor runs a certain number of **virtual machines**;
- The virtual machines are accessible through the network, each of them hosting an operative system.

The advantage of this approach is that we have multiple domain of resources, allowing to **pool resources** (in the traditional method you had to format and then reinstall).

Another big benefit of this advantage is found in **security** aspects. While it is not acceptable to run on the same OS the database and the webserver (because the web server is attackable and because they may need different software stack in order to run), it is totally possible to run two machines in the same underlying hardware using an hypervisor. The concepts of "software stack abstraction" and isolation are so much crucial that they are being always more being addressed with **containers** and not as much with virtual machines. This is because the virtual machines, efficient as it may be, have overhead and containers are much lighter.

One of the biggest advantage that virtualization introduce is the fact that you can have **differencing disk**. A differencing disk is **a virtual hard disk (VHD) that stores changes made to another VHD or to the guest operating system**. The purpose of differencing disks is to make it possible to maintain information about changes made so that they can be reversed if necessary. In a sense you can have **disk versioning**.
This allows three of the most crucial points of virtualization:
- **Snapshots/checkpoint**: ability to freeze the state of a virtual machine whether the machine is stopped or even running. The cool part is that a checkpoint can be exported;
- **Motion/live migration**: ability to move a virtual machine from a physical host to another one without interrupting the service. Once you have the ability to checkpoint how the live migration works is pretty intuitive. Mind that this involves the virtual switch of the hypervisors in the two hosts machines, since if we move a virtual machine to another hosts than the network requests to that virtual machine have to be forwarded to the new "home" of the migrated virtual machine. This is possible since the virtual switch is a part of the hypervisor and the hypervisor is aware of the migration. This is a key of the cloud computing: it helps **decoupling** the physical infrastructure from the virtual systems. It allows to offer services even if the server is broken;
- **Disk migration**;

**Thin provisioning** involves using virtualization technology to give the appearance of having more physical resources than are actually available.

### Overhead
In principles virtualization is great, but how much **overhead** are we paying to be able to do so? It depends by the process we are executing over the virtualized environment.

Some overhead is **fixed** (aka the execution of the virtualization env) but some may vary. If the emulated process is an **I/O bound process** then the overhead is **substantial**, because the process have to ask to the virtual env to handle the I/O request, and the virtual env has to ask to the underlying environment to handle that. On the other hand, if the process is mostly **CPU bound** (e.g., generating random numbers) than the overhead is way less.

It is extimated that, **on average**, the overhead is up to **15%**. This is mainly because of the interruptions of the virtualized processes. Let's say the virtualized process hits a page fault (aka, wants a piece of data that is not available). This result in an interruption.  Then the virtualized kernel tries to fix the interruption, which results in another interruption. At the end the real underlying system have to fix (e.g., load in memory the missing data) the fault, so the interruption of the virtualized kernel is fixed and the virtualized kernel can handle the virtualized process interruption. 

### Advanced features
Virtualization also allows **advanced features**. An example is the **ballooning**: the idea is that the memory is seen as a balloon that can be inflated or deflated. In this way virtual machines have more or less memory based on their needs, as if it would possible to have physical on-demand memory.

## Containers
The next step of virtualization are the containers. As discussed, virtualization has been disruptive because it allowed to run multiple operative systems on the same box, giving multiple domain of isolation. Imagine to have a server in which runs 4 virtual machine with Linux based operating systems. It is quite a waste to pay computational power to run 4 times the same Linux kernel. This is why containers are on the rise. 

A **container** is an **isolated environment** running an application with only the needed resources (storage, CPU, memory), not knowing anything else on the machine. 
**Advantages**: 
- similar to VMs but start faster and have less resource overhead. They do not virtualize the hardware
- multiple containerized apps on a single server don't mess up each other
**Disadvantages**: 
- you can't mix and match: the underlying kernel has to be the same, unlike VMs where you can have Linux and windows virtual machines handled by the same hypervisor.

With a container you can run a process that thinks that it is being executed inside its own virtual machine. Mind that the level of isolation of a container is less than the level of isolation provided by virtual machines. Nevertheless it is good enough. 

One of the real challenges of working with containers is the networking. Unlike VMs containers do not have their own (virtual) NIC (network interface card), they share the underlying network card using some trick. 

### Docker
**Docker** is a tool that allows to easily deploy applications in a sandbox (called container) to run on
the host OS.

A **Docker image** is a blueprint containing a set of instructions for creating a container. Generally an image is based on other images, apporting some edits. Each one of the edit from the original images is called **layer**. Layers are there to save on computational effort and bandwidth when distributing them, because they only contain information on what is changed. 
- images can't change, but you can start a container from an image, perform operations in it and save another image based on the latest state of the container
- an arbitrary number of brand-new containers can be build and started from the same image

A **Docker file** is a file that contains a set of precise instructions stating how to create a new docker image. Generally it consists in: 
- **FROM**: specify which image to take as the starting point
- **RUN**: you can run commands
- **COPY**: copy local files in the current image
- **CMD**: default command to run, along with the default arguments
- **WORKDIR**: where the effect of the commands will take place
- **EXPOSE**: which port expose to the external
![[dockerfile-example.png||700]]

### Kubernetes
Since containers are very fast and handy programs that you can start and stop very quickly we can also take a step further: **it is possible to write a multi-node coordination system that allows to orchestrate containers spread in multiple servers, so that containers can spawn and die based on requests.** 

**Kubernetes** is a software that orchestrates (start, stop, run, recycle, spawn...) containers as if they were processes inside a runtime.

This works really well if your application is designed with microservices in mind: every module is composed of container(s) and they interact with each other through web APIs. 
This allows to create more modules of a specific function of the application if it is needed.