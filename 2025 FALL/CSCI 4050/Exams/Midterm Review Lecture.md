- [ ] exam 1 includes activity and sequence diagram
- [ ] 25% object diagrams and class diagrams
- [ ] classify nonfunctional requirements
- [ ] and process to compare the models

# Review of Exam 1 in Class

Mostly multiple choice
- about 27 questions of MCQ's
	- quick questions - this event is internal or external
		- user creates account, is this internal, external, or temporal event...?
		- **external**
	- movie marks booking as having a selected seat
		- **internal**
	- system will expire the seat if user does not finish checking out in time...?
		- **temporal**
- 2 minutes per question
- matching questions (7-10 minutes)
- matching question for nonfunctional specifications


# 1. File Intro Soft Eng pptx
- Definition of SWE
	- deals with all practical aspects
		- technical aspects covering software lifecycle
		- managerial aspects
			- tools needed to create project

- **Software Engineering is an engineering discipline that is concerned with all aspects of software production from the early stages of system specification through to maintaining the system after it has gone into use.**
	- **Engineering discipline:** Using appropriate theories and methods to solve problems bearing in mind organizational and financial constraints.
	- **All aspects of software production:** Not just the technical process of development. Also project management and the development of tools, methods, etc. to support software production.
- **Software Engineering** is a collection of techniques, methodologies, and tools that help with the production of a high-quality software system developed within a given budget, meeting a given deadline, while change occurs.

- what are 4-5 main activities in software lifecycle
	- specification
	- design
	- implementation
	- testing
	- evolution

# 2. System Development pptx
- project and application types
- application type is one aspect that will govern choice of dev process
- what is best choice for development process?
	- ex:
		- see a game, we need ui and prototyping, virtual reality interface
			- **Answer:** we need prototyping and incremental approach
	- ex:
		- safety critical system or embedded system
			- **Answer:** best approach is incremental approach with specifications
	- ex: 
		- customer wants system in increments but wants documentation for whole process
			- **Answer:** R.U.P.
				- incremental with heavy documentation
	- ex:
		- a change-tolerant project
			- **Answer:** ? what is it? R.U.P. or iterative or plan-driven

- *Waterfall vs Prototype vs RUP vs Scrum and what is best for what examples*
	- **Prototype** - best when no understanding and help the customer understand better
	- **RUP** - incremental, but with heavy documentation
	- **SCRUM** - is good for non-safety critical, but bad for large groups
	- **Factors affecting our choice of model:**
		- communication skills/availability, requirements stability, required level of documentation, customer interaction
		- documentation slows down the process
	- *look at pdf comparing models*
" Continuing with software development Processes;
1- Prototyping
2- The Rational Unified Process.
3- The Reuse-Oriented Process 
4- Agile Methodology " - Team Contract and defining team team norms


![[RUP.png]]
Orange text represents the RUP characteristic:
![[plan driven vs incremental.png]]
What is the difference between RUP and SCRUM methodologies?
Compare and contrast with respect to approach (agile/ iterative or sequential), artifacts,
defining scope, cycle and when recommended.
Both methodologies are considered to be Agile and approach project activities in the iterative
way. However, RUP methodology calls for a formal definition of scope and major project
milestones are associated with specific dates. SCRUM methodology uses project backlog
instead of scope and allows the backlog to be redefined at the end of each iteration (usually
about every 4 weeks). In addition, RUP subdivides the project lifecycle into 4 major
phases **(Inception, Elaboration, Construction, Transition)**. Even though it encourages
concurrent workflows across the entire cycle, the general understanding is that ***certain activities will peak during certain phases (for instance, requirements analysis will spike during the***
***elaboration phase)***. On the contrary, SCRUM dictates that the entire “traditional”
lifecycle fits into one iteration. In other words, a workload for one iteration at a time is
determined and then the entire cycle occurs within one iteration (e.g. the requirements for a
particular feature are collected, documented as a user story, then coded, tested and presented for
the user review).
RUP is recommended for large, long- term, enterprise-level projects with
medium-to-high complexity. While SCRUM is recommended for quick
enhancements and organizations that are not dependent on a deadline

- re-solve the activities in the modules
- the activities are better than the quizzes

- which process model not effective if you don't interact with user and not have user as center of process?
	- **Answer:** Scrum - needs user feedback
		- Waterfall is incorrect - waterfall doesn't care about customer feedback
		- Prototyping? also incorrect - need user interaction
		- R.U.P.? incremental, yes, but there is documentation, so its not as user centric
			- Scrum is more interactive and involves user in the software dev process than R.U.P.


# 2.1 Requirements Engineering
- Greenfield Engineering - creating the system from scratch
	,- start with requirements
- Forward Engineering - creating a system (e.g. database tables) from the documents (class diagrams)
- Reverse Engineering - have a system, extract the decision making diagram of a Database
- Interface Engineering - redisigning UI w/o touching backend
- Re-engineering - updating existing system to meet new quality goals or for new tech
	- or enhance some quality ...

- System design - NOT INCLUDED

- Scrum
	-  DROPPED QUESTION -> which of agile manifesto contributes more to faster development process?

# 3a. SCRUM

- **Sprint Ceremonies** - order and what they are?
	1. Sprint Planning - before sprint
	2. Daily Scrum - every meeting, whole world invited
	3. Sprint Review - review product, informal
		- no powerpoint presentation
		- demonstration of system to product owner or customers
		- invite whole world
	4. Sprint Retrospectives - review process, what went wrong and well, what to keep doing?
		- presentation
		- 15-30 min
- **Artifacts from SCRUM:**
	- Product backlog
	- Sprint backlog
	- Burndown charts

- Sprint Meeting Roles - who and what are their responsibilities?
	- Scrum master vs Project manager and product owner and scrum etc. their responsibilities and etc.

# 3b. User Stories + Scenarios + Cases
- formats for all 
- know how to write them...
- test cases for requirements
- stories and cases formally define actors by roles
	- An actor may be a class of users, roles users can play, or another computer system that interacts with the system. Actors don’t need to be human users.
	- A primary actor has a goal requiring the assistance of the system and initiates a use case.
	- A secondary actor is an actor from which the system needs assistance
- User story:
	- As a [role], I want to [action] in order to [result]
		- role is a responsibility and privilege

- Scenarios use concrete names
- It's imagining how a use case will play out.
- Just know scenario is informal and doesn't consider all alternative possible use cases
	- just one path of a use case

- Use case:
	- is how we achieve a case in a system with the main flow and all the alternatives and exceptions
	- user story also has exceptions, but use case is more concrete
	- user story will use an actor role, not the complete actor
	- more details in use case
	- Main flow has perfect assumption of the case
	- Alternate flows and Exceptions contain all conditionals

- Identify the different properties of use case description:
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
- Know all the nonfunctional requirement types and how to classify requirements to correct one
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


# More potential questions

## Types of Events
- what type of event, internal, external, temporal?
- External:
	- initiated by user
- Internal:
	- initiated by system
- Temporal:
	- initiated by system, relies on time limit

Association Relationships:
- If two classes in a model are related in some way, or need to communicate with each other, there must be a connection between them. An association denotes that connection
- The name of an association represents its meaning. It should be a verb or a verb phrase
- An association may be navigable or non-navigable. A navigable association has an arrow indicating the direction of navigability
- By default, an association is navigable in both directions and the arrows are omitted
- self/reflexive association
![[selfreflexive association.png]]

Multiplicity:
- We can indicate the multiplicity of an association by adding multiplicity adornments to the line denoting the association.


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
- system sequence diagrams:
	- alt frame vs opt frame vs loop frame
	- loop frame: either use * or have loop frame (they are slightly different)

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
- many patients can have many doctors
- many doctors can have many patients
- many to many relationship -> associate class: appointments

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

# Exam1 Study Guide from ELC

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

<hr>

# Activities (Bolded ** ** are correct)
## 1. Introduction to SE and Process Models
Methodology of developing software systems is frequently referred to as ____
- soft dev process
- soft process
- soft proc model
- **all of the above**

## 2. Prototypes
Which of the following is **not** considered in a software prototype?
- dependability requirements
- exceptions and error handling
- auth
- **all of the above**

## 3. Module 1 Review
Which two of the following models will not be able to give the desired outcome if users' participation is not involved?
- Waterfall and Prototyping
- **Prototyping and Scrum**
- Waterfall and RUP
- reuse oriented model and waterfall

Selection of a software development model is based on –
- proj reqs
- dev team and customers
- proj type and associated risk
- **all of the above**

In the RUP, testing the product is done during
- construction phase

Which of the following statements are correct about the Rational Unified Process (RUP) and the waterfall process model? Select all true answers
- **Both have a set of defined phases**
- **RUP is an iterative and incremental process but the Waterfall is a sequential process model.**
- **Both are heavy processes; that involve producing project documents.**
- RUP does not define the scope ahead of starting development.
- Both have the same probability of whole project failure risk.
- Both are sequential processes

*(Note: RUP DOES in fact scope ahead of starting development, since its super documented and plan heavy)*

## 4. Requirements Classification
Match the requirement with its type

| \|__1__\|The system must allow a user to check a purchase order status by its order number\|<br>\|__2__\|All financial transactions should be encrypted.\|<br>\|__3__\|The user password should be encrypted using the XYZ encryption algorithm.\|<br>\|__1__\|The user must be able to search for a book.\|<br>\|__2__\|The system must send the verification email within 2 seconds after the user confirmation.\|<br>\|__3__\|The user interface should be implemented using Java FX\| |     | \|**1**.\|Functional requirement\|<br>\|**2**.\|Nonfunctional requirement\|<br>\|**3**.\|Pseudo requirement (Constraint)\| |
| ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | --- | -------------------------------------------------------------------------------------------------------------------------- |

Match each description or requirement below to the single most appropriate term.
(Note: terms (choices) may apply to none, one, or more than one description.)
Match each description or requirement below to the single most appropriate term.

(Note: terms (choices) may apply to none, one, or more than one description.)

| \|__7__\|The system must run on windows and mac devices.\|<br>\|__8__\|The Medication Monitoring System shall not allow dispensing any dose of medication that is greater than maximum amount prescribed by the physician. (System blocks if the user attempts to take an extra dose)\|<br>\|__1__\|The ticket issuing time, after credit card validation has been received, should not exceed 10 seconds.\|<br>\|__6__\|Four out of five users shall be able to book a guest within 5 minutes after a 2-hour introduction to the system.\|<br>\|__2__\|The system must not disclose any stored user information including personal information, passwords, and payment information\| |     | \|**1**.\|Performance\|<br>\|**2**.\|Security\|<br>\|**3**.\|Robustness\|<br>\|**4**.\|Maintainability\|<br>\|**5**.\|Availability\|<br>\|**6**.\|Usability\|<br>\|**7**.\|Portability\|<br>\|**8**.\|Safety\| |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | --- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |

The extends relationships implies what? (UC1 --<\<extends>>--> UC2)
- **UC1 conditionally adds steps to UC2**

## 6. Draw a UC Diagram
![[UC Diagram Quiz Answer.png]]
