## Relationship Client/Server & P2P
- Problem statement "Clients can be servers and servers can be clients"
- Which model is correct?
- Model 1: "a peer can be either a client or a server"
- Model 2: "a peer can be both a client and a server"
	- inheritance : "either-or"
	- ![[Drawing 2025-10-09 10.29.35.excalidraw]]



Activity 8:

## Thai Nguyen

## Activity 8: Architectural Design

![](https://uga.view.usg.edu/d2l/img/0/Quizzes.Main.submissionCompleteCheckIcon.svg?v=20.25.9.24045)

## Your work has been saved and submitted

Your work has been saved and submitted

Written Oct 20, 2025 11:10 AM - Oct 20, 2025 11:13 AMAttempt 1 of 1

[Activity 15 Solution.pdf](https://uga.view.usg.edu/d2l/common/dialogs/quickLink/quickLink.d2l?ou=3706957&type=coursefile&fileId=Activity+15+Solution.pdf)

Released Sep 9, 2025 11:59 AM

|   |   |
|---|---|
|Attempt Score|7 / 11|
|Overall Grade (Highest Attempt)|7 / 11|

|   |   |   |
|---|---|---|
|**Question 1**|||

select the answer that fills the blanks below correctly (in order)

Older compilers were designed according to a pipe and filter architecture, in which each stage would transform its input into an intermediate representation passed to the next stage. Modern development environments, including compilers integrated into interactive development environments with syntactical text editors and source-level debuggers, use a repository architecture. Identify the design goals that may have triggered the shift from pipe and filter to repository architecture.

The Design goal of the old compilers (designed according to the pipe and filter) is ____________, while the design goal of modern IDEs is_________.

|   |   |
|---|---|
|![Unselected](https://uga.view.usg.edu/d2l/img/0/QuestionCollection.Main.radioUnchecked.svg?v=20.25.9.24045 "Unselected")|\|   \|   \|<br>\|---\|---\|<br>\|a)\|performance, security\||
|![Unselected](https://uga.view.usg.edu/d2l/img/0/QuestionCollection.Main.radioUnchecked.svg?v=20.25.9.24045 "Unselected")|\|   \|   \|<br>\|---\|---\|<br>\|b)\|security, performance\||
|![Selected](https://uga.view.usg.edu/d2l/img/0/QuestionCollection.Main.radioChecked.svg?v=20.25.9.24045 "Selected")|\|   \|   \|<br>\|---\|---\|<br>\|c)\|throughput, response time\||
|![Unselected](https://uga.view.usg.edu/d2l/img/0/QuestionCollection.Main.radioUnchecked.svg?v=20.25.9.24045 "Unselected")|\|   \|   \|<br>\|---\|---\|<br>\|d)\|response time, throughput\||

|   |   |   |
|---|---|---|
|**Question 2**|||

The main problem of of the repository architectural design is:-

|   |   |
|---|---|
|![Unselected](https://uga.view.usg.edu/d2l/img/0/QuestionCollection.Main.radioUnchecked.svg?v=20.25.9.24045 "Unselected")|\|   \|   \|<br>\|---\|---\|<br>\|a)\|Security\||
|![Unselected](https://uga.view.usg.edu/d2l/img/0/QuestionCollection.Main.radioUnchecked.svg?v=20.25.9.24045 "Unselected")|\|   \|   \|<br>\|---\|---\|<br>\|b)\|Data management is hard\||
|![Unselected](https://uga.view.usg.edu/d2l/img/0/QuestionCollection.Main.radioUnchecked.svg?v=20.25.9.24045 "Unselected")|\|   \|   \|<br>\|---\|---\|<br>\|c)\|Performance; the repository form a bottleneck on heavy load.\||
|![Incorrect Response](https://uga.view.usg.edu/d2l/img/0/Shared.Main.infIncorrect.gif?v=20.25.9.24045 "Incorrect Response")![Selected](https://uga.view.usg.edu/d2l/img/0/QuestionCollection.Main.radioChecked.svg?v=20.25.9.24045 "Selected")|\|   \|   \|<br>\|---\|---\|<br>\|d)\|Maintainability as the system components are highly coupled with the repository.\||
|![Correct Answer](https://uga.view.usg.edu/d2l/img/0/QuestionCollection.Main.infRightAnswer.gif?v=20.25.9.24045 "Correct Answer")![Unselected](https://uga.view.usg.edu/d2l/img/0/QuestionCollection.Main.radioUnchecked.svg?v=20.25.9.24045 "Unselected")|\|   \|   \|<br>\|---\|---\|<br>\|e)\|The repository is a bottleneck affecting both performance and maintainability. (both c and d are correct)\||

|   |   |   |
|---|---|---|
|**Question 3**|||

In many architectures, such as the three- and four-tier architectures, the storage of persistent objects is handled by a dedicated layer (e.g the data acess layer). In your opinion, which design goal(s) have lead to this

decision?

|   |   |
|---|---|
|![Unselected](https://uga.view.usg.edu/d2l/img/0/QuestionCollection.Main.radioUnchecked.svg?v=20.25.9.24045 "Unselected")|\|   \|   \|<br>\|---\|---\|<br>\|a)\|Maintainability\||
|![Correct Answer](https://uga.view.usg.edu/d2l/img/0/QuestionCollection.Main.infRightAnswer.gif?v=20.25.9.24045 "Correct Answer")![Unselected](https://uga.view.usg.edu/d2l/img/0/QuestionCollection.Main.radioUnchecked.svg?v=20.25.9.24045 "Unselected")|\|   \|   \|<br>\|---\|---\|<br>\|b)\|Portability and Robustness\||
|![Unselected](https://uga.view.usg.edu/d2l/img/0/QuestionCollection.Main.radioUnchecked.svg?v=20.25.9.24045 "Unselected")|\|   \|   \|<br>\|---\|---\|<br>\|c)\|Response time\||
|![Incorrect Response](https://uga.view.usg.edu/d2l/img/0/Shared.Main.infIncorrect.gif?v=20.25.9.24045 "Incorrect Response")![Selected](https://uga.view.usg.edu/d2l/img/0/QuestionCollection.Main.radioChecked.svg?v=20.25.9.24045 "Selected")|\|   \|   \|<br>\|---\|---\|<br>\|d)\|All the above\||

|   |   |   |
|---|---|---|
|**Question 4**|||

A closed multi-layer architecture hurts both response time and memory foot print.

|   |   |   |
|---|---|---|
||![Selected](https://uga.view.usg.edu/d2l/img/0/QuestionCollection.Main.radioChecked.svg?v=20.25.9.24045 "Selected")|a) True|
||![Unselected](https://uga.view.usg.edu/d2l/img/0/QuestionCollection.Main.radioUnchecked.svg?v=20.25.9.24045 "Unselected")|b) False|

|   |   |
|---|---|
||   |

|   |   |
|---|---|
||   |
|||
|## Feedback<br><br>A closed multi-layer architecture requires method invocations across each layer boundary and often also copying data betweeneach layer. This hurts both response time and memory f|   |

|   |   |   |
|---|---|---|
|**Question 5**|||

An information system with a central database is an example of a client/server architectural style.

|   |   |   |
|---|---|---|
||![Selected](https://uga.view.usg.edu/d2l/img/0/QuestionCollection.Main.radioChecked.svg?v=20.25.9.24045 "Selected")|a) True|
||![Unselected](https://uga.view.usg.edu/d2l/img/0/QuestionCollection.Main.radioUnchecked.svg?v=20.25.9.24045 "Unselected")|b) False|

|   |   |   |
|---|---|---|
|**Question 6**|||

Both the MVC and the multi-layer styles apply seperation of concerns and thus make maintainance easier.

|   |   |   |
|---|---|---|
||![Selected](https://uga.view.usg.edu/d2l/img/0/QuestionCollection.Main.radioChecked.svg?v=20.25.9.24045 "Selected")|a) True|
||![Unselected](https://uga.view.usg.edu/d2l/img/0/QuestionCollection.Main.radioUnchecked.svg?v=20.25.9.24045 "Unselected")|b) False|

|     |
| --- |
|     |








<hr>

# Activity 11
**Question 1 options:**
*   **The system shall be configured with one of multiple families of products.**
    *   **3. Abstract Factory**
*   **Your program must support switching among several different email libraries, but each one has a slightly different interface.**
    *   **5. Adapter**
*   **The system shall support "lazy creation" - a component is created only if, and when, the client demonstrates an interest in it.**
    *   **6. Proxy**
*   **The system shall create objects without exposing the creation logic to the client**
    *   **4. Factory Method**
*   **A single instance shall be created and shall be initialized only if, and when, it is accessed.**
    *   **1. Singleton**
*   **Components shall be extensible at run-time. The client should be able to add behaviors at run-time.**
    *   **7. Decorator**
*   **The system shall provide a simple interface to a complex subsystem.**
    *   **2. Facade**







Operation Mapping:
- PaymentProcessor.process() → LegacyPaymentGateway.charge()

Translation:
- process() receives PaymentRequest object
- Extracts parameters: amount (converted to cents), cardNumber, cvv, expiryMMYY
- Calls charge() with these parameters
- Converts return value: 0 → PaymentResult, nonzero → PaymentException



I used Google Search / Google Gemini to clarify technical details and verify my existing answers. For Part A, I asked it to verify if my reasoning about the Adapter pattern was correct, and it made minor corrections regarding how the adapter converts between interfaces. I further tested my knowledge by giving it analogies to see if my understanding was correct.

For Part B, I asked about UML notation, specifically how to represent constructor parameters in class diagrams. The AI suggested a <<constructor>> stereotype, but I verified this against UML standards and found that constructors are simply shown in the operations section with the class name, which I then implemented correctly.

For Part C, I asked what data type would be best for representing currency amounts. The AI suggested BigDecimal instead of float, explaining it's more precise for financial calculations. I verified this recommendation and implemented the suggestion.

After reviewing the AI's output, I verified all suggestions against assignment requirements and authoritative sources. I learned that AI is useful for clarifying concepts, but it's important to verify its suggestions, as it can sometimes provide non-standard information that needs to be validated.