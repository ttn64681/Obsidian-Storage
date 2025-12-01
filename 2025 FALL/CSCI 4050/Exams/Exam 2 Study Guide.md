## Component Diagram
- **assembly connector** (ball and socket)
	- ball - > component provides a service
	- socket - > component requires that service


# Thai Nguyen

## Activity 8: Architectural Design - Results

## Attempt 1 of 1

Written Oct 20, 2025 11:10 AM - Oct 20, 2025 11:13 AM

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
|![Unselected](https://uga.view.usg.edu/d2l/img/0/QuestionCollection.Main.radioUnchecked.svg?v=20.25.10.24356 "Unselected")|\|   \|   \|<br>\|---\|---\|<br>\|a)\|performance, security\||
|![Unselected](https://uga.view.usg.edu/d2l/img/0/QuestionCollection.Main.radioUnchecked.svg?v=20.25.10.24356 "Unselected")|\|   \|   \|<br>\|---\|---\|<br>\|b)\|security, performance\||
|![Selected](https://uga.view.usg.edu/d2l/img/0/QuestionCollection.Main.radioChecked.svg?v=20.25.10.24356 "Selected")|\|   \|   \|<br>\|---\|---\|<br>\|c)\|throughput, response time\||
|![Unselected](https://uga.view.usg.edu/d2l/img/0/QuestionCollection.Main.radioUnchecked.svg?v=20.25.10.24356 "Unselected")|\|   \|   \|<br>\|---\|---\|<br>\|d)\|response time, throughput\||

|   |   |   |
|---|---|---|
|**Question 2**|||

The main problem of of the repository architectural design is:-

|   |   |
|---|---|
|![Unselected](https://uga.view.usg.edu/d2l/img/0/QuestionCollection.Main.radioUnchecked.svg?v=20.25.10.24356 "Unselected")|\|   \|   \|<br>\|---\|---\|<br>\|a)\|Security\||
|![Unselected](https://uga.view.usg.edu/d2l/img/0/QuestionCollection.Main.radioUnchecked.svg?v=20.25.10.24356 "Unselected")|\|   \|   \|<br>\|---\|---\|<br>\|b)\|Data management is hard\||
|![Unselected](https://uga.view.usg.edu/d2l/img/0/QuestionCollection.Main.radioUnchecked.svg?v=20.25.10.24356 "Unselected")|\|   \|   \|<br>\|---\|---\|<br>\|c)\|Performance; the repository form a bottleneck on heavy load.\||
|![Incorrect Response](https://uga.view.usg.edu/d2l/img/0/Shared.Main.infIncorrect.gif?v=20.25.10.24356 "Incorrect Response")![Selected](https://uga.view.usg.edu/d2l/img/0/QuestionCollection.Main.radioChecked.svg?v=20.25.10.24356 "Selected")|\|   \|   \|<br>\|---\|---\|<br>\|d)\|Maintainability as the system components are highly coupled with the repository.\||
|![Correct Answer](https://uga.view.usg.edu/d2l/img/0/QuestionCollection.Main.infRightAnswer.gif?v=20.25.10.24356 "Correct Answer")![Unselected](https://uga.view.usg.edu/d2l/img/0/QuestionCollection.Main.radioUnchecked.svg?v=20.25.10.24356 "Unselected")|\|   \|   \|<br>\|---\|---\|<br>\|e)\|The repository is a bottleneck affecting both performance and maintainability. (both c and d are correct)\||

|   |   |   |
|---|---|---|
|**Question 3**|||

In many architectures, such as the three- and four-tier architectures, the storage of persistent objects is handled by a dedicated layer (e.g the data acess layer). In your opinion, which design goal(s) have lead to this

decision?

|   |   |
|---|---|
|![Unselected](https://uga.view.usg.edu/d2l/img/0/QuestionCollection.Main.radioUnchecked.svg?v=20.25.10.24356 "Unselected")|\|   \|   \|<br>\|---\|---\|<br>\|a)\|Maintainability\||
|![Correct Answer](https://uga.view.usg.edu/d2l/img/0/QuestionCollection.Main.infRightAnswer.gif?v=20.25.10.24356 "Correct Answer")![Unselected](https://uga.view.usg.edu/d2l/img/0/QuestionCollection.Main.radioUnchecked.svg?v=20.25.10.24356 "Unselected")|\|   \|   \|<br>\|---\|---\|<br>\|b)\|Portability and Robustness\||
|![Unselected](https://uga.view.usg.edu/d2l/img/0/QuestionCollection.Main.radioUnchecked.svg?v=20.25.10.24356 "Unselected")|\|   \|   \|<br>\|---\|---\|<br>\|c)\|Response time\||
|![Incorrect Response](https://uga.view.usg.edu/d2l/img/0/Shared.Main.infIncorrect.gif?v=20.25.10.24356 "Incorrect Response")![Selected](https://uga.view.usg.edu/d2l/img/0/QuestionCollection.Main.radioChecked.svg?v=20.25.10.24356 "Selected")|\|   \|   \|<br>\|---\|---\|<br>\|d)\|All the above\||

|   |   |   |
|---|---|---|
|**Question 4**|||

A closed multi-layer architecture hurts both response time and memory foot print.

|   |   |   |
|---|---|---|
||![Selected](https://uga.view.usg.edu/d2l/img/0/QuestionCollection.Main.radioChecked.svg?v=20.25.10.24356 "Selected")|a) True|
||![Unselected](https://uga.view.usg.edu/d2l/img/0/QuestionCollection.Main.radioUnchecked.svg?v=20.25.10.24356 "Unselected")|b) False|

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
||![Selected](https://uga.view.usg.edu/d2l/img/0/QuestionCollection.Main.radioChecked.svg?v=20.25.10.24356 "Selected")|a) True|
||![Unselected](https://uga.view.usg.edu/d2l/img/0/QuestionCollection.Main.radioUnchecked.svg?v=20.25.10.24356 "Unselected")|b) False|

|   |   |   |
|---|---|---|
|**Question 6**|||

Both the MVC and the multi-layer styles apply seperation of concerns and thus make maintainance easier.

|   |   |   |
|---|---|---|
||![Selected](https://uga.view.usg.edu/d2l/img/0/QuestionCollection.Main.radioChecked.svg?v=20.25.10.24356 "Selected")|a) True|
||![Unselected](https://uga.view.usg.edu/d2l/img/0/QuestionCollection.Main.radioUnchecked.svg?v=20.25.10.24356 "Unselected")|b) False|

|     |
| --- |
|     |