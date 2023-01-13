- [[The Virtual Layer|Virtualization:]] you can assign to a virtual machine a certain number of virtual cores (inside the processor settings of the virtualization environment (may it be an hypervisor or a virtualbox-like program)). *It is considered acceptable an overbooking of 2x*: if your physical processor has 8 cores you can assign 16 virtual cores to virtual machines without degradation. This is because most of the time cores are in an idle state. *Hence with 8 cores you can basically have 16 virtual machines with 2 (virtual) cores each without loss of performance*. This is not true if the task that the virtual machine will have to operate are CPU-intensive, obviously.

- **SuperComputing:** 
	- *Liquid cooling basically obligatory*. 
	- *There is a lot of debate about parallel file systems* thanks to the speed of the drives. 
	- *Photonic Switch: it is becoming possible to extend pcie slots with optic fiber* and hence have gpus or whatever at a great distance from the motherborard. Being a switch is also possible to modify the hardware without touching the hardware. 

- **Stock-keeping unit (SKU)**: a number commonly used in ICT Infrastructure to identify a product that we want to buy. We could use it to infer the number of configurations of a specific CPU (number of SKUs of that specific CPU). **Basically a SKU is a barcode.**
