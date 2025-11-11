# Software Testing Fundamentals
```table-of-contents
```

## 1. Testing Heuristics
*   **Definition:** 
	* Experience-based rules of thumb or guiding principles that help testers make informed decisions, prioritize, and design tests. *They are not strict rules but valuable insights.*
*   **Example:** 
	* "The more we test, the more bugs we find."
		* (Implies thoroughness often uncovers more issues).
	* "Testing is never complete." 
		* (Acknowledges that complete bug elimination is impossible).

## 2. Black Box vs. White Box Testing

*   **Black Box Testing (Functional Testing):**
    *   **Focus:** Tests the software's *external behavior and functionality* against requirements, *without* knowledge of its internal code or structure.
    *   **Analogy:** Testing a car by driving it and checking if it accelerates, brakes, turns, etc., without looking under the hood.
    *   **Example:** Verifying if a login screen accepts valid credentials and rejects invalid ones.
	    * 

*   **White Box Testing (Structural Testing):**
    *   **Focus:** Tests the internal logic, structure, and code paths of the software, *with* knowledge of the source code.
    *   **Analogy:** A mechanic examining the car's engine, wiring, and internal components to ensure they function correctly.
    *   **Example:** Ensuring every `if-else` branch in a calculation function is executed at least once.
	    * try exceeding test cases, pushing limits of constraints, out of bound exceptions, etc.
	* **Techniques:**
		 - *Conditions coverage*
			 - 
		 - *Code coverage*
			 - 
		 - *Branch coverage*
			 - 
		 - *Path coverage*
			 - Tests Conditions, Code, and Branch coverage
			 - Best to do at Unit Testing level
			 - Looking at every path is known as **path coverage** (very expensive)

## 3. Levels of Testing

Testing is typically performed at different levels, progressing from individual code units to the complete system.

### A. Unit Testing
*   **Definition:** Tests individual, smallest testable parts of an application (e.g., a function, method, class) in isolation.
*   **Purpose:** To verify that each unit of code performs as expected.
*   **Performer:** Developers.
*   **Example:** Testing a `calculateDiscount(price, percentage)` function to ensure it returns the correct discounted price for various inputs.

### B. Component Testing
*   **Definition:** Tests a larger collection of units that form a logical component or module. These components are often integrated but still tested in isolation from the full system.
*   **Purpose:** To verify the functionality and interaction of related units within a component.
*   **Example:** Testing a "Shopping Cart" component, ensuring items can be added, removed, quantities updated, and the total calculated correctly.

### C. Integration Testing
*   **Definition:** Tests the interfaces and interactions between integrated components or modules.
*   **Purpose:** To detect faults in the interaction between integrated units or components, and ensure they work together as expected.
*   **Approaches:** "Top-down," "Bottom-up," or "Big-bang."
*   **Example:** Testing the interaction between a "Product Catalog" component and a "Shopping Cart" component to ensure products added from the catalog appear correctly in the cart.
	* Test addItemToCart
	* Simple Driver to test createCartItem
* Strategies:
	* 

- Should integrate step by step:
	- Have test cases that frontend and backend are working in correct way
	- then test the 3 components, frontend and backend and database
- In plan driven approaches, you have diff teams working on diff parts, until integration testing phase
	- frontend develops frontend parts
	- backend parts develops backend code
- In Scrum:
	- you integrate whenever

### D. System Testing
*   **Definition:** Tests the entire, fully integrated software system against the specified requirements.
*   **Purpose:** To evaluate the system's compliance with functional and non-functional requirements (e.g., performance, security, usability) in an environment that mimics production.
*   **Performer:** Independent testers or dedicated QA teams.
*   **Example:** Testing an entire e-commerce website to ensure end-to-end functionality, from user registration, browsing, adding to cart, checkout, payment processing, and order confirmation.

### E. Acceptance Testing
- **Definition:** Testing the hwole system by the client/users
- Blackbox could be used and reuse Whitebox testing

- 2 Types: *done by client/users*
	- **Alpha Testing:**
		- testing by Clients
			- *could be on Client's or Developer's site/environment*
		- but <span style="background:#fff88f">developers exist, run test, help running test</span>
	- **Beta Testing:**
		- testing on Client's own environment
		- *you test on your OWN environment* as if <span style="background:#fff88f">devs DO NOT EXIST</span>

### Bottom-Up Testing

### Top-Down Testing





- white box test cases are RAN with black box test cases
	- (document your test cases)
	- (always have you test cases ready)
- typically devs have manual white box test cases ready, and then team uses automated black box test cases
	- both testing types help each other

- we do the most coverage at unit testing since they can do white box testing (path coverage)

Final Demo:
- KNOW YOUR TEST CASES and TEST EVERYTHING during DEMO
	- Booking process
		- use not logged in, checkout, msg: "must login"
		- you know the username and password

- FINAL DEMO:
- always focus on user values first to test:
	- login, logout, registration

- dont spend so long registering


- Which techniques are white box, which techniques are black box: