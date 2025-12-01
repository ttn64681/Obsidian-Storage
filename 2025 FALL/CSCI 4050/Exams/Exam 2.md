Nov 20th
Attend review lecture



**Exam 2 Study Guide**

**The exam will be on eLC Quizzes tool. Bring your laptop.**

**Read the exam policy on the syllabus.**

  

**There are two versions of the exam on the quizzes page. Exam2 CSCI 4050 and Exam2 CSCI 6050 and Honors.**

**Complete the CSCI 4050 exam if you are registered in CSCI 4050.**

**Complete the CSCI 6050 and Honors exam if you are an honors student or you are registered in CSCI 6050.**

  

**Exam Material** 

**Make sure to review the following topics:**

**Strikethrough** **topics are NOT required for this test.**

- **Software Engineering General Topics**

- Software life cycle and SE development activities
- Being able to answer general questions about software engineering.

- **Software Process Types and Software Process Models.**

- Be able to differentiate between (RUP, Waterfall, prototyping, and Scrum)

- **Requirements Specification and Modeling**

- Differentiate between functional, non-functional requirements, and constraints (pseudo requirements).
- Define and differentiate non-functional requirements.
- Differentiate between scenarios, use cases, and user stories.
- User stories and acceptance criteria
- Scenarios and their types
- Use case diagram (generalization, includes and extends relationships)
- Be able to create and understand domain class diagrams (purpose, notation: classes, associations (roles, multiplicities, directionality, aggregations, generalizations, association classes)
- Be able to create and understand object diagrams.
- System sequence diagram (purpose, notation, participants, different types of messages)

- **Requirements Analysis and Dynamic UML Modeling**

- Purpose of UML interaction diagrams (sequence and communication diagrams, and their notation)

- UML Sequence Diagram notation (lifelines, activations, messages, combined fragments)
- UML Communication Diagram Notation
- Understand the purpose of activity diagrams
- Entity vs. boundary vs. control classes; UML stereotypes
- **Be able to create a sequence diagram given a use case description and a first-cut design class diagram**
- Be able to add a view layer, data access layer and  to sequence and communication diagrams.
- Be able to convert a sequence diagram to a communication diagram and vice versa.

- **System Design**

- Design Activities
- Subsystem decomposition
- Design principles (Coupling, cohesion, separation of concerns, Indirection, object responsibility)
- What is meant by the open-close design principle?
- Common architectural styles (client/server, layered, repository, MVC, and pipe and filter). 
- Realizing design goals.
- Component and deployment diagrams (purpose and notation only)
- Be able to draw a simple deployment diagram given a system description and design goal(s).

- **Object Relational Mapping**

- Mapping classes and their attributes
- Mapping associations - multiplicity considerations
- Mapping association classes.

- **Design Patterns**

- The SOLID principles.
- What are design patterns?
- Classification of design patterns (Creational, structural and behavioral) for the included patterns: -
- Singleton pattern (Structure, applicability, and examples)
- Abstract Factory pattern (applicability, when to use)
- Factory method ((Structure, applicability, and examples)
- Decorator Pattern (Structure, applicability, and examples)
- Adapter Pattern (Structure, applicability, and examples)
- Proxy Pattern (Structure, applicability, and examples)

                     Be able to select the appropriate pattern given a problem.

Be able to explain how a design pattern supports the SOLID principle(s).

Be able to apply an appropriate design pattern to solve a specific software problem by developing a design class diagram that clearly depicts the solution structure and relationships among classes. 

- **Testing**

- Verification vs. validation
- Different types of tests
- Be able to distinguish between black-box testing and white-box testing and their testing techniques.
- Non-functional testing (Stress testing), definition, and how to apply.





<hr>


# Exam Tips/Questions

may give use case description and ask which diagram is correct? (given communication diagram options as answers)

may ask more about solid principles applied to a diagram or not?
- is there coupling between classes

won't be given problem to do from scratch

**Ex Problem:**
- be given use case description
- be given design class diagram with navigation arrows
- then draw sequence diagram

prepare all steps, then draw one thing only


**communication diagram to sequence diagram**
- comm diagram doesn't have timeline, but has links between objects if they communicate
- need the link if 2 objs sending messages to each other

2 button display


<hr>

max time
exam open for 10 minutes at beginning of class time only
More than 27 questions:
- mcq 
- ½ mutliselect
- describe design pattern
- describe the diagram
- define stress testing
- text input (written response)
- draw the diagram for the given pattern (omitted)



Ex:
- On the WWW a single clinet can access data model (diagram) as the following. what architectural dsign can we use to imporve? explain

an arch style in which multiple independent comoponents interact


Example question: an engineering analysis tool is composed on mult ind components include
- data ingestion module
- a filtering module that performs noise reduction
- a statistical analyzer that computes trends and
- a reporting engine that generates visual summaries
- - shared data structure., components operates independently and communicates only thru shared data structure.
- which acts as the central coordination point for the system?
- no direct calls are made b/w components.
  Which architectural style best fits this system and why?

- repository
	- not mvc
	- not 


Component diagram
- wont be asked to draw, but you should understand diagrams and how system is deployed
- what is assembly notation?
- provides vs requires
C1 provides interface, C2 requires/invokes method from interface
![[Drawing 2025-11-17 10.43.59.excalidraw]]

what about Deployment diagram?
- each node is hardware device
- node has link
what they represent, the structure, and the purpose


Understand mvc or multilayer or repository given diagram

- text object should be created by text decorator


design principles: separation of concerns indirection, coupling cohesion
- these are principles, not design goals

classes and interaction: cohesion, coupling, and solid
- design goals:
	- security, maintainability, etc.


- coupling, refers to components, not classes
- cohesion: relation between 2 components
- whenever increase coupling, you decrease cohesion
- low coupling is ease of maintenance
	- loosely coupled components easy to maintain
	- reusable, easy to extend
	- major for cohesion: reusablility
	- major for loose coupled component is : is easy maintenance







from Exam 1, still know the following:
- class and object diagrams
- distinguish between different process models

- know prupose of each diagram:
	- which depicts the object's at runtime and how they are linked at runtime?
	- fix the objects and how they are linked at runtime?
		- object diagram
			- shows how theyre linked
	- which diagrams depict interaction between objects?
		- communication diagram or sequence diagram.
		- not system sequence

system sequence is just a description of use case!
- what about detailed focus on messages? or time? -> sequence diagram
- which diagrams communicates with objects directly? -> object diagram
- to figure out which ones invoke which -> sequence
- which depicts how components are allocated or distributed? -> deployment
- shows different subsystems and explicity representation of interfaces between them? -> subsystem or component diagram? component, shows the wire that explicitly says WHICH interface? explicit representation?
	- not package diagram


- a module name UserProfileManagwer performs the following tasks
- - updating user detials
- sending promo emails generating user reports?
	- wat is the problem with this?
		- high coupling
		- low cohesion

- low coupling example:
	- multiple components that don't need to know the inner details of another component

- which of following object diagram sare consistent with class diagram

- rest are about class diagrams

- is sequence diagram consistent with class diagram

- question about solid principles

**multi select or multiple choice:**
- resolve quiz 1
- word document or pdf that compares RUP and Prototyping and Agile and SCRUM and Waterfall


- skip to class and diagram



**27 mcq or matching:**
1 written response:



**which diagram shows  interaction of system between system and environment or external entities?**
- Component?
	- no, this shows internal
- **Use Case diagram** is the answer


## SOME MORE STUFF ON THE TEST :

Top-Down:
- user interface first, then middle tier, then connection to database
- have to implement stops
- Focus on user interface first

Bottom-Up:
- start w/ components that show output
- testing functionality with checkout
- then see if email sent with correct price and calculations and etc
- need to implement drivers, in order to substitute params
- A better approach:

Sandwich Approach:
- connection of database is ready
- ui is ready
- check middle-tier logic
- every time you want to test some functionality, you test it with user interface and other layers

- however, if we need to ____, we need to use the following testing:
Stress testing / Performance Testing:
- testing system BEYOND its limits
- how system behaves if we exceed the limits

White vs black techniques
definition of testing and how we use it

asking to list the methods and specific class 

ex: :2BWatchDisplay (Communication diagraam)
- look for incoming input messages
	- if sequence look at all input arrows
	- if communication, look at all input messages going into it
- input messages mean we invoke it coming from x class

ex: : Patron (squence diagram)
- what are the input messages?
	- **getPatronInfo() GOING INTO Patron from checkoutHandler**

COnverting
![[Drawing 2025-11-13 09.48.56.excalidraw]]
![[Drawing 2025-11-13 09.50.31.excalidraw]]

What is the signature method of the following:
- ex: 
	- **tn := createNode(x)**
	- Answer: createNode(int x): TreeNode

Given use case description, select correct sequence diagram:
- ex:
	- Use Case Cancel Order Description:
		- given inv was reserved whne order was made, cancel an orde rinvolves that all order items in order must be canceled and their inv quantities must be updated.
	- First Cut Deisng Diagram

- cancel all items in order
- then refund
- update inv quantities
![[Drawing 2025-11-13 09.58.40.excalidraw]]
