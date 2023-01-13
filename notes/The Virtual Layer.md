**A cloud infrastructure is basically a distribuited operating system on a datacenter**
It is a way to organize and access computer resources, in a way that may remind an operating system in a classic computer.
The OS has a set of resources (memory, CPU time, whatever) and it allocates them to processes that needs them. 

In cloud computing we have a similar idea. The cloud computing model is a complex organization that is designed to take billions of server and see all of them as a single pool of resources, and an arbitrary number of tenants (single users to whole organizations) want a slice of that resources and pay per use.

Cloud computing started as a buisness model and then evolved in a technology, which now, as said, can be (extremly) simplified and viewed as an operating system for (globally) distribuited computers.

![[cc-ref-model.png|650]]

So far we have seen the [[The Physical Layer]], now we move into the **Virtual Layer.**

Let's start by saying that the virtual layer is not the only way to create the cloud: even if most cloud is based on virtualization it is not strictly required to do so. 
In principle you can imagine a system where when you ask for resources you are given the access to a physical machine with those resources and an operating system: in the above image, the small dent of the yellow layer that touch the physical layer is for this use cases, it is possible to provision the actual physical machine. 
Microsoft, Amazon and others allow you to actually "rent" the physical machines. 
However this cases are not common: **in general the physical layer is dominated by the virtual layer.**

**The ultimate goal of the virtualization layer (and in a sense of the whole cloud infrastructure) is to be able to pool all the resources of multiple servers in a single set so you can allocate and provision this resources to specific users and when not needed anymore let the resources go back in the pool.**

### HyperVisors
The most famous example for virtualization is VirtualBox, while for hypervisor we have KVM or HyperV. 

The main difference is that **an HyperVisor is designed to run a service inside a server operating system.
Basically it runs virtual machines without GUI.** 
Virtualization systems such as VirtualBox are more oriented to single operating systems with graphics.

Moreover, **an hypervisor is designed to run multiple operating systems, aka multiple virtual machines.**
To give an idea: VirtualBox gives you access to the network by installing a virtual network card on your (virtual) operating system while inside hypervisors such as HyperV there is a virtual switch(s) with VLANs. 

### Virtualization
**Virtualization allows us to exectute arbitrary code by emulating the necessary underlying structure, may it be software or hardware.**

**The real question is: how much overhead are we paying to be able to do so?**
**It depends by the process we are executing over the virtualized environment.** 
Some overhead is fixed (aka the execution of the virtualization env) but some may vary. 
If the emulated process is an I/O bound process then the overhead is substantial, because the process have to ask to the virtual env to handle the I/O request, and the virtual env has to ask to the underlying environment to handle that.
On the other hand, if the process is only CPU bound (e.g., generating random numbers) than the overhead is way less.
**It is extimated that, on average, the overhead is up to 15%.
This is mainly because of the interruptions of  the virtualized processes.** 
Let's say the virtualized process hits a page fault (aka, wants a piece of data that is not available). This result in an interruption. 
Then the virtualized kernel tries to fix the interruption, which results in another interruption. 
At the end the real underlying system have to fix (e.g., load in memory the missing data) the fault, so the interruption of the virtualized kernel is fixed and the virtualized kernel can handle the virtualized process interruption. 

**Virtualization also allows advanced features: an example is the "balooning", the idea is that the memory is seen as a baloon that can be inflated or deflated.** 
In this way virtual machines have more or less memory based on their needs, as if it would possible to have physical on-demand memory. 

**Mind that it is possible to exploit virtualization features even in non-virtualized images.** 
For example: it is possible to create a virtual hard drive in any windows based computer and assign to it an arbitrary amout of space, even if that space is actually not available in the underlying hardware.
A simple use case of this is when a certain program requires a certain amount of space "just in case" but you are sure that it will never need that space. In this scenario you simply fix the problem by creating a virtual disk.

Our concept of virtualization is interesting because we virtualize "over the same environment" (x86 architecture emulates something that runs on an x86 archietcture, we do not do "cross virtualization" such as android over x86). 
This obviously allows to make the virtualization process more thin because we can exploit directly the underlying structure. 
At the end of the day this virtualization mechanism a way to have multiple operating system's kernels and protection manager that become hierarchical. 

Another way to look at virtualization is the distinction between how it was then and how things work now. 
In the past we had the hardware and on top of that we had the operating system that was responsible of providing resources.
**Now we have the hardware, the hardware hosts an hypervisor, the hypervisor runs a certain number of virtual machines which are accessible through the network and each of these virtual machines host an operative system.**
The advantage of this approach is that we have multiple domain of resources. 
**This allows the possibility to pool resources** (in the traditional method you had to format and then reinstall). 
**Another big benefit of this advantage is found in security aspects.** While it is not acceptable to run on the same OS the database and the webserver (because the web server is attackable and because they may need different software stack in order to run), it is totally possible to run two machines in the same underlying hardware using an hypervisor.

The concepts of "software stack abstraction" and isolation are so much crucial that they are being always more being addressed with **containers** and not as much with virtual machines.
This is because the virtual machines, efficient as it may be, have overhead and containers are much lighter.

**One of the biggest advandage that virtualization introduce is the fact that you can have differencing disks.** 
Basically you take a virtual disk and, by the hypervisor, you tell it that he is a son of another disk. In the differencing disk you store only the changes that would have happen in the parent disk.
The cool part is that you can then delete the child drive and "defreeze" the parent one, and the result is like going back in time. **In a sense you can have disk versioning**. 
**This allows three of the most crcuial points of virtualization: snapshots/checkpoint, vmotion/live migration and disk migration.**

**Checkpoint** is the ability to freeze the state of a virtual machine wheather the machine is stopped or even running. The cool part is that a checkpoint can be exported. 

**Live migration** is the ability to move a virtual machine from a physical host to another one without interrupting the service. Once you have the ability to checkpoint how the live migration works is pretty intuitive. 
Mind that this involves the virtual switch of the hypervisors in the two hosts machines, since if we move a virtual machine to another hosts than the network requests to that virtual machine have to be forwarded to the new "home" of the migrated virtual machine. This is possible since the virtual switch is a part of the hypervisor and the hypervisor is aware of the migration. 
This is a key of the cloud computing. 
It helps decoupling the physical infrastructure from the virtual systems. It allows to offer services even if the server is broken.

### Containers
The next step of virtualization are the containers. As discussed, virtualization has been disruptive because it allowed to run multiple operative systems on the same box, giving multiple domain of isolation. 

Imagine to have a server in which runs 4 virtual machine with linux based operating systems. It is quite a waste to pay computational power to run 4 times the same linux kernel. 
This is why containers are on the rise. 

**A container is basically a process group that is able to see only a selection of os resources. The kernel only expose a subset of the resources using the cgroup mechanism. The concept of differential file systems is used to share the common data between groups and isolate the differences.**
The concept of differential file systems is similar to differencing disks but performed at a file system level.

**definition:** A container is an isolated environment running an application with only the needed resources (storage, CPU, memory), not knowing anything else on the machine. 
Advantages: 
- similar to VMs but start faster and have less resource overhead. They do not virtualize the hardware
- multiple containerized apps on a single server don't mess up each other
Disadvantages: 
- you can't mix and match: the underlying kernel has to be the same, unlike VMs where you can have linux and windows virtual machines handled by the same hypervisor.

**With a container you can run a process that thinks that it is being executed inside its own virtual machine.**

Mind that the level of isolation of a container is less than the level of isolation provided by virtual machines. Neverthenless it is good enough. 

One of the real challenges of working with containers is the networking. 
Unlike VMs containers do not have their own (virtual) NIC (network interface card), they share the underlying network card using some trick. 

**definition:** A **docker image** is a blueprint containing a set of instructions for creating a container. Generally an image is based on other images, apporting some edits. Each one of the edit from the original images is called **layer**. Layers are there to save on computational effort and bandwidth when distribuiting them, because they only contain information on what is changed. 
- images can't change, but you can start a container from an image, perform operations in it and save another image based on the latest state of the container
- an arbitrary number of brand-new containers can be build and started from the same image

**definition:** A **dockerfile** is a file that contains a set of precise instructions stating how to create a new docker image. Generally it consists in: 
- **FROM**: specify which image to take as the starting point
- **RUN**: you can run commands
- **COPY**: copy local files in the current image
- **CMD**: default command to run, along with the default arguments
- **WORKDIR**: where the effect of the commands will take place
- **EXPOSE**: which port expose to the external
![[dockerfile-example.png||700]]

#### Kubernetes
Since containers are very fast and handy programs that you can start and stop very quickly we can also take a step further: **it is possible to write a multi-node coordination system that allows to orchestrate containers spreaded in multiple servers, so that containers can spawn and die based on requests.** 

**Kubernetes** is a software that orchestrates (start, stop, run, recycle, spawn, ...) containers as if they were processes inside a runtime.

This works really well if your application is designed with microservices in mind: every module is composed of container(s) and they interact with each other through web APIs. 
This allows to create more modules of a specific function of the application if it is needed.