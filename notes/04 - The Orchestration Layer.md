**Service Orchestration:** automated arrangement, coordination, and management of various system or component functions in a cloud infrastructure to provide and manage cloud service.

Benefits:
- Shorter service provisioning time;
- Eliminates possibility of manual errors;
- Reduces operating expenses;
- Simplifies cloud infrastructure management.

## Orchestrator (Orchestration Software)
The orchestrator provides a **library** of predefined workflows and an **interface** to create user-defined workflows: triggers an appropriate workflow upon receiving a request from the cloud portal.
![[orchestrator.jpg|700]]

Orchestrator commonly interacts with other components using APIs that are defined for these components.
![[orchestrator-apis.png]]

### Workflow Modelling
Orchestrators commonly provide interfaces to model workflows. The following image represents common elements that we can find in a workflow.

![[orchestration-workflow-example.jpg|650]]
Explaining 2 key elements:
- **Manual interaction**: human interaction, needed even in automated systems;
- **Waiting even**: allows to proceed if a certain event happens or not;

#### Workflow Examples
##### Orchestration Use Case: Provisioning DB2 Database
![[orchestration-workflow-use-case-1.jpg|650]]

##### Orchestration Use Case: Removing Tenant
![[orchestration-workflow-use-case-2.jpg|650]]