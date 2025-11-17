quiz will be extra credit

Nonfunctional:
- Security:
	- encrypted credit card info and password
- Authentication/Authorization:

Deliverable 4 (Domain Class Diagram):
- should take like 2 days, since done in class

Deliverable 5 (Object relational Mapping) and 6 (Sprint 2 Stories):
- database schema
- promotions
- non promotions
- Database design doc
- Demonstrate database and deliverable 6 (registration, login, logout)

Deliverable 8:
**admin functionality**
- implement 
	- home page -> manage movies, promos, users, (showtimes also on homepage perhaps)
	- manage movies:
		- add movie
		- NOT REQUIRED: if edit/delete, can't delete currently showing
	- add promotion, send promotion:
		- promotion automatically sent to users enrolled
		- CANNOT MODIFY PROMO, cannot scam users
			- if you do, you need confirmation for destructive actions you cannot undo
	- manage showtimes:
		- maintain usability + performance of system
		- admin assigns showtime to specific movie:
			- DO NOT retrieve all movies from database to choose a movie
			- Search button for movie instead
				- Maybe search for "Coming Soon" movie
				- Maybe search for "Now Playing" movie
		- Scheduling easy -
			- choose room
			- then choose available (non-taken) dates + times
			- then choose movie
		- 3 rooms for testing


**Deliverable 7**:

Who What When

one person implementing the facade



"We will be using a singleton to connect to the database"

"What design patterns we will implement?"

"Proposed design patterns?"

Deliverable 7:
1. what stack and arch design
	- MVC model, etc.
2.  System decomposition: brekadown of components and interactions
	1. Frontend: 
		1. Axios to make API calls to EXpress server
	2. Backend: API Handling and Logic
	3. Middleware: Node.js
3. Design Patterns:
	1. Facade:
		1. Problem:
		2. Solution: we made simple cohesive ethods such as fetchScheduledShows to encapsulate complex operations allowed more focus on user interactions
	2. Singleton:
		1. Problem:
		2. Solution: singular database connection which is our mongoose connection that all of our routes depend on.
4. SOLID Principles Reflection (need to be specific, like discuss the proxy pattern you are implementing, this is the structure of the proxy (include class diagrams)):
	- include class diagrams or else you will lose points
	1. S.
	2. O.
	3. L.
	4. I.
	5. D.
5. Design Goals
	- Maintainability:
		- Separation of components w/in our code and the use of MVC architecture
	- Usability:
		- By designing out website similar to that of common movie ticketing booking websites such as AMC, users should be able to book a ticket on our website w/in 15 mins of accessing the website
	- Security:
		- Password encryption


Package Diagram + Class Diagrams
- Try to keep slides light

- hybrid design, Repository Design
- Admin portal and user portal are connected to repository

- Example of service file
- specific router files per module
- service files to reduce coupling


Pattern 1: Facade allows for SRP, etc.etc.


Instead of code snippets we should have class diagrams


Pattern 3: Proxy, we implement a protect proxy
- only allow admin to access
- Achieves SRP
	- skeleton handles indicating loading movies

View Layer, Controller Layer, Schedule Layer, Service Layer, Repository Layer
- React frontend
- restful api springboot backedn which are controllers

- handles http requests and responses 
- the facade


- Decorator:
	- movie cards come w/ different buttons depending on context
	- explosion of movie card classes
	- wrap movie card w/ button decorations

- Class Diagram


- Facade
	- dependency inversion



you are decorating what?

- design/class diagram
- multilayer mvc

- im doing facade
- draw diagram

- factory for tickets
- draw diagraam

- proxy or adapter
- draw diagram

- mvc or multilayer

- package diagram

view layer
domain layer
data access layer

- Facade Design Pattern
	- problem
	- solution
	- coding

- Guideline is deliverable itself

- The programming languages and any frameworks used
	- mongodb react
- architectural design
	- we use mvc or mukti
		- system decomposition ℗ckage diagram or component diagram or )
		- depict architectural design (a)

- avoid including code
- "this controller interacts with this"
- just to show you have interfaces and facades
- show/explain interaction of : 
	- model to view to controller




- Deliverable 8 due 25th