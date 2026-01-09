---
tags:
  - ddd
  - Architecture
  - EventStorming
---

# Domain Driven Design

> A strategy aimed at improving the quality of software by aligning it more closely with the business needs it serves.

-> Bringing Devs and Domain Experts (Business People) closer together 

## Strategic Design

Higher Level
Is about the **Problem Space**

1. Value:
	- What is the value of our solution
2. Knowledge Discovery
	- Who are our Domain Experts
	- Event Storming
		- Put events on a board (i.e. stick nodes)
			- e.g. Create Cart, Add to Cart, Remove Product, ...
3.  Communication
	- Improve Communication with **Ubiquitous Language**
		- Business and Devs use the same words for the same thing
4. Domain Analysis
	- Cluster events from the Event Storming to form subdomains
		- Core Subdomains
			- (most of the) Business Value
		- Supporting Subdomains
		- Generic Subdomains
			- Can also be outsource or be handled with 3rd party software

### Event Storming

1. Devs, Business experts, PO, ... put Post-Its on a board
2. Find  Events and put it on the board
	- **Cart Created**
	- **Product Added**
3. Find Actor and Commands for Events (one Command can lead to multiple Events)
	- **Customer -> Select First Product ->** Cart Created
	- **Customer -> Adds Product ->** Product Added
4. Policies find  rules or constraints  for the Events
	- Customer -> Select First Product **-> Check Brand Minimum Rules ->** Cart Created
	- Customer -> Adds Product **-> Check Brand Minimum Rules ->** Product Added
5. Find Hotspots (something that is vulnerable and can go wrong) and map to Policies
	- Customer -> Select First Product -> Check Brand Minimum Rules **\[External API Failure]** -> Cart Created
	- Customer -> Adds Product -> Check Brand Minimum Rules **\[External API Failure]** -> Product Added
6. Put everything in a sequence (might also go in parallel)
	1. Customer -> Select First Product -> Check Brand Minimum Rules **\[External API Failure]** -> Cart Created
	2. Customer -> Adds Product -> Check Brand Minimum Rules **\[External API Failure]** -> Product Added
7. Come up with an aggregate
	- **Cart** (Aggregate)
		- Might contain Entities such as Cart and Product
8. ...

## Tactical Design

Lower level (closer to code)
Is about the **Solution Space**

- Bounded Context
- Entity
	- Has an Id
	- Mutable
	- May span over multiple Bounded Contexts
- Value Objects
	- No Id (its defined by its value)
	- Immutable
	- Basic building blocks of Entities
- Aggregates
	- Cluster Entities
	- One root Entity
	- (usually) bound to a transaction scope
- Domain Events
	- Facilitate asynx messaging between Bounded Contexts
- Domain & Application Services
	- No state
	- Application wide services (e.g. Auth)
	- Domain services (e.g. Create Account)
