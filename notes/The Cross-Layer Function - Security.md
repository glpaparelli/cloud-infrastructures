Security is one of the most complex and vast aspect in computer science and in cloud computing. Too big to be trated in this class. 
The following are just hints and basic terminology.
Security is related to SLA: if you have a breach it means that you did not protect the data, hence you are liable.

- information is an organization's most valuable asset
- various tools are deployed to protect the assets
- trust is one of the key concerns of consumers adopting cloud 
	- Trust = Visibility + Control
- managing security has become increasingly important for cloud service providers

**Remember that a system is secure as much is secure the more unsecure element if the system.** 

**Definition: Information Security** 
A terrm that includes a set of practices that protect information and information systems from unauthorized access, use, information disclosure, disruption, modification or estruction. 

The goal of information security is to provide **confidentiality**, **integrity**, and **availability**

Security mechanisms ensure right users have access to right resources at the right time. Auditng enables assessing effectivness of the security mechanism.

**Trusted Computing Base**
A set of all those components that are critical to the security of the cloud infrastructure and that you trust.
It defines boundary for security-critical and non critical parts of a systems. 
Vulnerabilities in the TCB migh jeopardize security of the entire system. 

**Defense-in-Depth**
A strategy in which multiple layers of defense are deployed throughout the infrastructure to help mitigate the risk of security threats in case one layer of the defense is compromised. 
It is also known as a layered approach to security and it provides service providers additional time to detect and respond to an attack. 

**Secure Multi-Tenancy**
Requires mechanism that prevent a tenant or its process from affecting another tenant's information/process.
Providers are resoponsible for ensuring secure multi-tenancy. 

**Velocity-of-Attack**
Refers to a situation where an existing security threat in a cloud may spread rapidly and have large impact. 

**Data Ownership**
Service provider must ensure that consumers own their data and that only them can access them. 
Two scenarios to determine ownership of data
- **data created on-premise and then stored in cloud**
	- data ownership remain with the creator based on facotrs such as
		- contracutal ownership
		- copyright law
		- ...
- **data created in the cloud enviornment**
	- determination of who owns the data depends on
		- terms of services
		- type of information
		- ...

**Security Concepts and Relationships**
![[security-relationship.jpg|600]]

**Account Hijacking**
![[account-hijacking.png]]
The control measures for account hijacking are: multi-factors auth, IPSec, firewall, ...

**Insecure APIs**
Cloud relies heavly on APIs: if they are vulnerable the whole system is at risks

**Denial of Service Attack**
Prevents legimate users from accessing resources or services

**Malicious Insiders**
A malicious insider is a current or former employee, contrator or other buisness partner who has or had authorized access to an organization's compute systems, network or storage. 

**Physical Security**
Every system is compromised if the attacker has physical access to the system. 