**Service Orchestration:** automated arrangement, coordination, and management of various system or component functions in a cloud infrastructure to provide and manage cloud service. 
The benefits are:
- saves service provisioning time
- eliminates possibilty of manual errors
- reduces operating expenses
- simplifies cloud infrastraction management

## Orchestration Software or Orchestrator
**Programmatically integrates and sequences various systems functions into automated workflows for executing service provisioning and management functions provided by the cloud portal.** 

**The orchestrator provides a library of predefined workflows and an interface to create user-defined workflows:** triggers an appropriate workflow upon receiving a request from the cloud portal.
![[orchestrator.jpg|700]]

**The orchestrator interacts with other components using the components APIs t** 
![[orchestrator-apis.jpg|650]]

### Workflow Modelling
Orchestrators commonly provide interfaces to model workflows. The following image represents common elements that we can find in a workflow.
![[orchestration-workflow-example.jpg|650]]

- **manual interaction:** sometimes even in the cloud a human interaction is needed
- **waiting even:** this is a key element, it allows to proceed if a certain event happens or not...

#### Workflow Examples
##### Orchestration Use Case: Provisioning DB2 Database
![[orchestration-workflow-use-case-1.jpg|650]]

##### Orchestration Use Case: Removing Tenant
![[orchestration-workflow-use-case-2.jpg|650]]