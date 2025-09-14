```table-of-contents
```
# Use Cases + Scenarios
- use case:
	- definition of goal=oriented set of interactions between external actors and system under consideration
- actor:
	- party outside of system that interacts w/ system
	- Use Case is initiated by actor w/ goal in mind and compeltes successfully when goal is satisfied
- scenario: 
	- instance of use case
	- represents single path through use case

## Actors
- actor may be *class of users*, roles users can play, or other computer system (actors don't need to be human)
- **Primary actor** 
- Secondary actor
## Scenario
- synthetic description of event or series of actions and events
- textual description of usage of system, written from end user's POV
- text, video, pictures, storyboards, etc.
- contains details about work place, social situations and resource constraints

- Definition: " A narrative description of what people do and experience as they try to make use of computer systems and applications "
- **concrete, focused, informal description of single feature of system used by single actor**
## Scenario Ex: Warehouse on Fire

## Scenario-based Design
Scenarios can have many diff uses during software lifecycle
- Requirements Elicitation: As-is scenario, visionary scenario
- Client Acceptance Test: Evaluation scenario
- System Deployment: Training scenario

## After scenarios are formulated: Use Cases
- Find all use cases in scenario that specify all instances of "how to report a fire"
	- Ex: "Report Emergency" is candidate for use case
- Describe each of these use cases in more detail
	- Participating actors
	- Describe entry condition
	- Describe flow of events
	- Describe exit condition
	- Describe exceptions
	- Describe nonfunctional requirements
- Functional Modeling

## Use case Description
- describes basic sequence of itneractions b/w actors and system necessary to satisfy goal
- may include variants of this sequence
- may include exceptions
- system is treated as a "black box"

![[UML Use Case Diagram.png]]

## How to Find Use Cases

## Textual Use Case Description Example
1. Name
2. Participating Actor:
3. Entry condition:
4. Exit condition:
5. Flow of events:
	1. Passenger selects destination station
	2. Ticket Machine displays the amount due
	3. Passenger inserts money, at least the amount due
	4. Ticket Machine returns change
	5. Ticket Machine issues ticket
6. Special requirements: (None)

## Fully Developed Use Case Description
- Use Case: Create customer account
![[Use Case Doc Ex.png]]

**Actors:**
- Logged-in users

**No Preconditions necessary**

**Post Conditions:**
- User profile changes are saved to database

**Normal Flow:** 
- User
	1. User selects edit profile
	2. If user selects to change password
	3. If user selects to change address
	4. User selects to subscribe/unsubscribe to receive promo email
- System
	1.1) System invokes Edit Personal

**Exceptions:**
- not here, referred to in Assumptions

**Assumptions:**
- Validity checks and exceptions are handled by the invoked use cases

**Special requirements:**
- Users can exit at any time choosing to save/ not save changes




**User Story: As an admin, I want to have the ability to manage movies, manage users, and manage promotions**

Admins:
- manage movies
	- add movie
	- update movie
		- add movie showtime
	- delete movie
	- Schedule movies:
		- Have rooms 1-3 (at least 3)
			- Each room has show times
		- **Cannot schedule movie time at same time for diff movie:**
			- If book movie in this room while playing diff movie, 
- manage users
	- **promote / demote users to and from admin**
		- NO "admins can delete or edit accounts"
	- **suspend users**
		- keep in database but call them "suspended" for weird activities (don't actually implement when to suspend, just the ability to suspend user)
		- they can't login
	- *DATABASE:*
		- "status": verified(active) / unverified / suspended /
- manage promotions

