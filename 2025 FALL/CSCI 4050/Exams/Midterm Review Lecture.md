- [ ] exam 1 includes activity and sequence diagram
- [ ] 25% object diagrams and class diagrams
- [ ] classify nonfunctional requirements
- [ ] and process to compare the models

Mostly multiple choice
- about 27 questions of MCQ's
	- quick questions - this event is internal or external
		- user creates account, is this intenral, external, or temporal event...?
		- external
	- movie marks booking as having a selected seat
		- internal
	- system will expire the seat if user does not finish checking out in time...?
		- temporal
- 2 minutes per question
- matching questions (7-10 minutes)
- matching question for nonfunctional specifications


# 1. File Intro Soft Eng pptx
- Definition of SWE
	- deals with all practical aspects
		- technical aspects covering software lifecycle
		- managerial aspects
			- tools needed to create project

- what are 4-5 main activities in software lifecycle
	- specification
	- design
	- implementation
	- testing/deployment

# 2. System Development pptx
- project and application types
- application type is one aspect that will govern choice of dev process
- what is best choice for dev process
	- ex:
		- see a game, we need ui and prototyping, virtual reality interface
			- **Answer:**we need **prototyping and incremental approach**
	- ex:
		- safety critical system or embedded system
			- **Answer:** best approach is incremental approach with specifications
	- ex: 
		- customer wants system in increments but wants documentation for whole process
			- **Answer:** R.U.P.
				- incremental with heavy documentation

- resolve the activities in the modules
- the activities are better than the quizzes

- which process model not effective if you don't interact with user and not have user as center of process?
	- **Answer:** Scrum - needs user feedback
		- Waterfall is incorrect - waterfall doesn't care
		- Prototyping? also incorrect - need user interaction
		- R.U.P.? incremental, yes, but there is documentation, so its not as user centric
			- Scrum is more interactive and involves user in the software dev process than R.U.P.


## 2.1 Requirements Engineering
- Greenfield Engineering - creating the system from scratch
	- start with requirements
	- then Forward Engineering
- Reverse Engineering - you extract 
- Re-engineering - system that exists but you want to re-engineer
	- enhance interface w/o touching backend
	- or enhance some quality

- System design - NOT INCLUDED

- Scrum
	-  DROPPED QUESTION -> which of agile manifesto contributes more to faster development process?

# 3. SCRUM

- **Sprint Ceremonies** - order and what they are?
	1. Sprint Planning - before sprint
	2. Daily Scrum - every meeting
	3. Sprint Review - review product
		1. no powerpoint presentation
		2. demonstration of system to product owner or customers
	4. Sprint Retrospectives - review process, what went wrong and well, what to keep doing?
		1. presentation, show the whole world

- Sprint Meeting Roles - who and what are their responsibilities?
	- Scrum master and product owner and their responsibilities and etc.

# 3b. User Stories + Scenarios + Cases
- how to write
- test cases for requirements
- As a [role], I want to [action] in order to [result]
	- role is a responsibility and privilege

- Just know scenario is informal and doesn't consider all alternative possible use cases
	- just one path of a use case

- Use case:
	- is how we achieve a case in a system with the main flow and all the alternatives and exceptions
	- user story also has exceptions, but use case is more concrete
	- user story will use a an actor role, not the complete actor
	- more details in use case

- Identify the different properties of use case:
	- may have prompts - if card number incorrect or expired, system will show error message
		- **exception**
	- at checkout, user didn't want to use store card 
		- **alternative flow**
	- user uses card - main flow
		- **may invoke enter payment use case**
	- **Pseudo-requirements / Special Requirements**: *(Nonfunctional requirements)*
		- email must be sent w/in 30 minutes
		- account should be encrypted
		- should be performant
		- usability requirement - page should be not too long to scroll

	- Note: Don't have if else in your use case descriptions

- odn't need to study scenario or watch elc videos
- jhust know the use case scenario in the powerpoint lecture is enough:
	- not complete scenario, just one path

# 3d - Functional Nonfunctional Requirements
- example in activities
- quiz 1 - classify requirements
- read the statement to the end
- Ex:
	- system must allow student to watch online lectures on elC
		- **functional requirement**
	- Lecture should be loaded in 3 seconds at most
		- non functional requirement
	- System should identify user privilege, encryption
		- Security (non functional requirment)
	- Pseudo-requirment
		- specific. database, specific language, specific hashing algorith, specific hashing algorithm
		- saying password should be encrypted -> nonfuctnional security , but
		- password shoul dbe using a specific ecnryption algortihm -> pseudorequirement
		- use MySQL
		- use Java
		- following a standard
		- submit assignment before christmas
		- packaging should submit assignment by downloading... etc
	- System should resist or deal with failure
		- Fault Tolerance / Robustness
		- note -> usually 


More potential questions

- what type of event, internal, external, temporal


- drawing diagram for specific situation - which diagram is correct?
- or drawing actors diagram with excludes and includes and inheritance (generalization)
	- be able to identify "Which actors can directly communicate with Use Case B?"
	- Actor A can directly communicate with which Use Cases??
- don't worry about if it says directly communicates or not, just focus on the lines/arrows, the association of the diagram

![[Drawing 2025-10-14 10.13.53.excalidraw]]


- diagram given, and asks which of the following object diagrams are correct and match?
	- remember, abstract cannot be instantiated

- Given a use case prompt - Use case question. (Two forms Solution document)
	- "A patron must be logged into UGAD to place an order for one or more meals"
	- "Before an order can be placed, system confirms patron is registered for payment deduction"
	- "Payment deducted from patrons account, which is managed in an external system called UGA_Accounts"
![[Drawing 2025-10-14 10.17.45.excalidraw]]


- **Many use case diagramming questions will look like:**
- user edit INVOKES change password:
- "users edit their profile, sometimes they change password"
	- Option 1 diagram: edit Profile -> includes Change Password
	- **Option 2 diagram: edit Profile <--- extended by Change Password**
	- Option 3 diagram: edit Profile ---> extends Change Password
- *Option 2 is correct, because Change Password is optional, so extends edit Profile*

- ORM not included

- 2 questions on System Sequence Diagrams
- And then Class Diagram questions

![[Drawing 2025-10-14 10.27.04.excalidraw]]

Example answers:
- [more items]* ItemInformation := addItem(itemID, quantity)
- addItem(itemID, quantity := ItemInformation)

Example: refer to Class Diagram MCQ [Activity 2]
- During one soccer season, multiple players participate in multiple games. Each player in each game a certain number of goals:
	- THIS IS MANY TO MANY association
![[Drawing 2025-10-14 10.42.55.excalidraw]]

Quiz 2 Question - Class Diagram Question for Doctors and Patients
- many doctors can have many patients
- many patients can have many appointments
![[Drawing 2025-10-14 10.44.34.excalidraw]]

Mistakes:
- **confusing a role with a class**
	- "A vehicle comprises of multiple parts"
	- "Each part can have one super part"
	- "one super part comprises of multiple subparts"

- inheritance is "either or" <- remember this

- Whole-part relationship
	- aggregation vs composition
		- **Composition:**
			- The "whole" diamond is on the one side, not the many
			- is on the super part, not the sub part
		- **Aggregation:**
			- 








focus on class diagrams and object diagrams




<hr>

# Exam1 Study Guide

---

**CSCI 4050/6050**

**Software Engineering**

**Exam policies:**

- The exam is online lockdown
- **Undergrad Students must take the quiz "Exam1 4050".**

**Material Included:**

           Modules 1, 2, and 3 (Only class and Object Diagrams)

**Topics:**

- Software Engineering life cycle.
- Software Process types and software process models.
- Requirements elicitation.
- Requirements analysis.
- Modeling system requirements (Use case diagram, system sequence diagram, domain class diagram, object diagrams).
- Data modeling: Class and object diagrams.
- ~~Object relational mapping~~  Not included


**Basic Study Material:**
1. Lecture notes.
2. You may study from the Textbook: Object-Oriented Software Engineering. Using UML, Patterns, and Java. 3rd Ed., by Bernd Bruegge and Allen H. Dutoit.

# Review the following topics:
## Software Engineering General Topics
- Software life cycle and SE development activities
	- Being able to answer general questions about software engineering.

## Software Process types and software process models.
- **Waterfall model**
	- Incremental and Iterative development
	- The RUP
	- Agile development; Scrum.
	- Reuse-oriented development
	- Prototyping

- **Identify and differentiate the phases of a typical software process and how it relates to the software life cycle.**
- **Identify and differentiate software process models (the SDLC, pros and cons arguments, and applicability of the process model).**

## Requirements Specification and Modeling

- **Differentiate between functional, and non-functional requirements and constraints.**
    - Define and differentiate various types of non-functional requirements.
    - Create functional requirement specifications in the form of user stories and acceptance criteria.
    - Distinguish between scenarios, user stories, and use cases.
    - Be able to develop use case diagrams (actors, generalization, includes and extends relationships)
    - Understand and Develop a use case description (actors, pre and post-conditions, use case dependencies, normal flow, and exceptions).
    - System sequence diagram (purpose, notation, participants, different types of messages)
    - Be able to develop a System sequence diagram given a use case description or an activity diagram.
    - Be able to develop an activity diagram given a use case description.
    - Differentiate different event types, and being able to create functional requirements based on system events.

## Data Modeling
- Be able to develop a domain class diagram and object diagrams. (purpose, notation, class relationships, roles, …)
- ~~Be able to map a class diagram into a relational database schema (identifying tables, their attributes, and their primary and foreign keys).~~ <- Dropped requirement (No longer need to do this for Exam 1)

