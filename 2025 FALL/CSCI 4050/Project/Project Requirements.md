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

Deliverable 7:
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