```table-of-contents
```

# Deliverable 2:

Fully Developed Use Case Description
- Use Case: Create Customer Account
- Word template given to fill out
![[Deliverable 2 use case ex.png]]

**Use case name:** Create customer account

**Scenario:**
- Create online customer account

**Triggering event:**
- New customer wants to set up account online

**Brief description:** 
- Online customer creates customer account by entering basic info and then following up with one or more addresses and a credit or debit card

**Actors:** Customer

**Related use case:**
- system invokes enter payment

**Stakeholders:**
- accounting, marketing, sales

**Preconditions:**
	customer account subsystem must be available
	credit/debit authorization services must be available

**Postconditions:**
	customer must be created and saved
	One or more addresses must be created and saved
	Credit/debit card info must be validated
	Account must be created and saved
	Address and Account must be associated w/ Customer

**Flow of activites:**

| Actor                                                                               | System                                                                                                                                                                             |
| ----------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Customer indicates desire to create customer account and enters basic customer info | System creates new customer<br>System prompts for customer addresses                                                                                                               |
| Customer enteres one or more addresses                                              | System creates addresses<br>System prompts for credit/debit card                                                                                                                   |
| Customer enters credit/debit card info                                              | System creates account<br>System verifies authorization for credit/debit card<br>System associates customer, address, and account<br>System returns valid customer account details |
- *This will help for the Sequence Diagram later....*

**Exceptions conditions:**
1. Basic customer data are incomplete
2. The address isn't valid
3. Credit/debit info isn't valid


## GUIDELINES!!!!!!!:
- DON'T use nouns instead of verb phrase to name use case
- the name should indicate what user is trying to accomplish
- Examples:
	- "Request Meeting", "Schedule Meeting", "Propose Alternate Date"
- Length
	- A use case description should not

# Deliverable 3:
- implement frontend of all pages to apply understanding of everything
- User view of Home Page (full-stack)
- Search and Filters work
- Database
	- THESE ARE ALL CREATED BY ADMINS
	- 

- Running Now or Coming Soon
	- Keep track of show times as specified by admin
## Sprint 1 Functionalities:
- Home page
	- allow users to search and filter
- search page
	- allow users to search and filter


GUIDELINE:
- do deliverable 3
- 