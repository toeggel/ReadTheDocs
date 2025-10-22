---
tags:
  - Architecture
  - Documentation
---

# Documentation

**Possible structure:**

1. Context
2. Functional Overview
3. Quality Attributes
4. Constraints
5. Principles
6. Software Architecture
	1. Containers
	2. Components
	3. Code
7. Data
8. Infrastructure Architecture
9. Deployment
10. Development Environment
11. Operation and Support
12. Decision Log

---

1.  Context
	1. What is this software project/product/system all about?
	2. What is it that is being built?
	3. How does it fit into the existing environment? (e.g. systems, business processes, etc)
	4. Who is using it? (users, roles, actors, personas, etc)
	5. Context Diagram should be included
	6. Technical and non-technical audience
2.  Functional Overview
	1. Highlight and summarize major functions of the software
	2. Is it clear what the system actually does?
	3. Is it clear which features, functions, use cases, user stories, etc are significant to the architecture and why?
	4. Is it clear who the important users are (roles, actors, personas, etc) and how the system caters for their needs?
	5. Is it clear that the above has been used to shape and define the architecture?
	6. Is it clear what the system does from a process perspective?
	7. What are the major processes and flows of information through the system?
	8. Feel free to reference existing documentation
	9. The goal is to provide and *overview*
	10. Sequence diagram when discussing automated business processes is useful
	11. Technical and non-technical people, both inside and outside the immediate development team
3.  Quality Attributes
	1. Summarize key quality attributes
	2. Performance (e.g. latency and throughput)
	3. Scalability (e.g. data and traffic volumes)
	4. Availability (e.g. uptime, downtime, scheduled maintenance, 24x7, 99.9%, etc)
	5. Security (e.g. authentication, authorization, data confidentiality, etc)
	6. Extensibility
	7. Auditing
	8. Monitoring and management
	9. Reliability
	10. Failover/disaster recovery targets (e.g. manual vs automatic, how long will it take?)
	11. Business continuity
	12. Interoperability
	13. Legal, compliance and regulatory requirements (e.g. data protection act)
	14. I18n and L10n
	15. Accessibility
	16. Usability
	17. Use SMART (specific, measurable, achievable, relevant and timely) attributes
	18. Technical people only
4. Constraints
	1. Summarize the constraints your are working in and some of the decisions that have been made for you
	2. Time, budget and resources
	3. Approved technology lists and technology constraints
	4. Target deployment platform
	5. Existing systems and integration standards
	6. Local standards (e.g. development, coding, etc)
	7. Public standards (e.g. HTTP, SOAP, XML, XML Schema, WSDL, etc)
	8. Standard protocols
	9. Standard message formats
	10. Size of software development team
	11. Skill profile of the development team
	12. Nature of the software being build (et, tactical or strategic)
	13. Political constraints
	14. Use of internal intellectual property
	15. Technical and non-technical people
5. Principles
	1. Make it explicit what principles are being followed
	2. Supply existing references, if they exist
	3. Architectural layering strategy
	4. No business logic in views
	5. No database access in views
	6. Use of interfaces
	7. Always use an ORM
	8. Dependency injection
	9. The Hollywood principle
	10. High cohesion, low coupling
	11. Follow SOLID
	12. DRY
	13. Ensure all components are stateless (e.g. to ease scaling)
	14. Prefer a rich domain model
	15. Prefer an anemic domain model
	16. Prefer stored procedures
	17. Avoid stored procedures
	18. Don't reinvent the wheel
	19. Approaches to error handling, logging, etc
	20. Buy rather than build
	21. Technical people only
6. Software Architecture (Containers, Components, Code)
	1. Summarize the software architecture
	2. What does the "big picture" look like?
	3. Is there a clear structure?
	4. Is it clear how the system works from the "30,000 foot view"?
	5. Does it show major containers and technology choices?
	6. Does it show major components and their interactions?
	7. What are the key internal interfaces? (e.g. web service between web and business tiers)
	8. Technical people only
7. (External Interfaces)
	1. What are the key external interfaces?
		1. system-to-system
		2. publicly exposed APIs
		3. exported files
	2. Has each interface been thought about from a technical perspective?
		1. what is the technical definition of an interface?
		2. if messaging is being used, which queues and topics are components using to communicate?
		3. what format are the messages (e.g. plain text, Avro, JSON)?
		4. are they synchronous or asynchronous?
		5. are asynchronous messaging links guaranteed?
		6. are subscribers durable where necessary?
		7. can messages be received out of order and is this a problem?
		8. are interfaces idempotent?
		9. is the interface always available or do you need the cache data locally?
		10. how is performance/security/etc catered for?
	3. Has each interface been thought about from a non-technical perspective?
		1. who has ownership of the interface?
		2. how often does the interface change and how is versioning handled
		3. are there service-level agreements in place?
	4. A paragraph on each interface covering this topics is sufficient
	5. Technical people only
8. (Code)
	1. Describe implementation details for important/complex parts of the system
	2. homegrown frameworks
	3. WebMVC frameworks
	4. approach to security
	5. domain model
	6. component frameworks
	7. configuration mechanisms
	8. architectural layering
	9. exceptions and logging
	10. how patterns and principals are implemented
	11. short description of each element using diagrams as necessary
	12. Technical people only
9. Data
	1. Record anything that is important from the data perspective
	2. What does the data model look like?
	3. Where is data stored?
	4. Who owns the data?
	5. How much storage space is needed for the data?
	6. Are there any requirements for long term archival?
	7. Are there any requirements for log files and audit trails?
	8. Are flat files being used for storage?
	9. short description of each element using diagrams as necessary
	10. Technical people only, including Operations
10. Infrastructure Architecture
	1. Describe the physical/virtual hardware and networks the software will be deployed to.
	2. Is there a clear physical architecture?
	3. What hardware does this include across all tiers?
	4. Does it cater for redundancy, failover and disaster recovery if applicable?
	5. Is it clear how the chosen hardware components have been sized and selected?
	6. If multiple servers and sites are used, what are the network links between them?
	7. Who is responsible for support and maintenance of the infrastructure?
	8. Are there central teams to look after common infrastructure?
	9. Who owns the resources?
	10. Are there sufficient environments for development, testing, acceptance, pre-production, production?
	11. Provide an infrastructure/network diagram with a short narrative
	12. Technical people only, including Operations
11. Deployment
	1. Describe the mapping between software (containers) and the infrastructure.
	2. How and where is the software installed and configured?
	3. Is it clear how the software will be deployed across the infrastructure elements described in the Infrastructure Architecture section?
	4. What are the options and have they been documented?
	5. Is it understood how memory and CPU will be partitioned between the processes running on a single piece of infrastructure?
	6. Are any containers/components running in an active-active, active-passive, hot-standby, cold-standby formation?
	7. Has the deployment and rollback strategy been defined?
	8. What happens in the event of a software or infrastructure failure?
	9. Is it clear how data is replicated across sites?
	10. Can use tables to show mapping between containers and infrastructure
	11. Can use UML deployment diagrams
	12. Can use color coding to designate runtime status (primary vs secondary, etc_
	13. Technical people only, including Operations
12. Operation and Support
	1. Be explicit about to run, monitor and manage the software
	2. Is it clear how the software provides the ability for Operations to monitor and manage the system?
	3. Has is this achieved across all tiers of the architecture?
	4. How can Operations diagnose problems?
	5. Where are errors and information logged?
	6. Do configuration changes require a restart?
	7. Are there any manual housekeeping tasks that need to be performed on a regular basis?
	8. Does old data need to be periodically archived?
	9. A simple narrative should suffice here
	10. Technical people only, including Operations
13. Development Environment
	1. Summarize how new team members set up a development environment
	2. Pre-requisite versions of software needed
	3. Links to software downloads
	4. Links to virtual machines
	5. Environment variables
	6. Host name entries
	7. IDE configuration
	8. Build and test instructions
	9. Database population scripts
	10. Username, passwords and certificates for connecting to services
	11. Links to build servers
	12. Technical people only, developers specifically
14. Decision Log
	1. Capture major decisions that have been made
	2. Why did you choose technology/framework X over Y and Z?
	3. How did you make the selection? PoC? Product evaluation?
	4. Did corporate policy or architecture standards force you to select X?
	5. Why did you choose the selected architecture?  What other options did you consider?
	6. How do you know that the solution satisfies the major non-functional requirements?
	7. Short paragraph describing each decision. Include a date of the decision?
	8. Technical people only

# Markdown example

- [system-architecture-template](examples/system-architecture-template.md)

# Related
- [architectural-decision-records](architectural-decision-records.md)