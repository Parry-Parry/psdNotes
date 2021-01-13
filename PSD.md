# PSD Notes
## Week 17
### Slides

**Test case** : The description of a set of actions to be performed on software and an expected outcome

**Test** : The execution of a test case, producing a test outcome

**Testing** : The practice of creating, maintaining, executing and evaluating test cases

**Reasons for testing:**
- Detection of defects
- Support the design and implementation of a module
- Prevent the introduction of defects
- Document the behaviour of a system
- Demonstrate that a system meets its specification

**Scales of testing:**
- Unit tests
- Integration tests
- Acceptance \(or system\) tests

_Unit tests_ : Automated tests written and run by software developers to ensure that a section of an application \(known as the "unit"\) meets its design

_Integration tests_ : Integration testing is the phase in software testing in which individual software modules are combined and tested as a group

_Acceptance tests_ : Formal description of the behavior of a software product, generally expressed as an example or a usage scenario that is then tested to show a system meets its specification

_Refer to week 17 slides for Behaviour Driven Development life-cycle diagram_

**Life-cycle for feature development:**
- Features/user stories
- \-\> Scenarios
- \-\> Steps
- \-\> Step Functions
- \-\> API
- \-\> Implemetation

_Step Functions_ : functions created in the language of the system to represent steps in a user story

**Step types in scenarios:**
- Given steps describe how to set up the test case fixture before the test case is executed
- When steps describe the actions to be taken during the test case itself
- Then steps describe the assertions that are made about the state of the system and/or output at the end of the test case

**Behaviour Driven Development** : Creation and maintenance of a requirement specification in  a structured natural language from which test cases can be automatically derived and tested

- Specification \-\> Scenario step definitions \-\> Application code
- Create tests in BDD engine
- BDD engine produces test report

**Example BDD frameworks:**
- JBehave \(Java\)
- Behave \(Python\)
- Cucumber \(Ruby, Python, Java\.\.\.\)
- Behat \(PHP\)
- Specflow

_Examples of testing can be found in week 17 slides_

**Where to implement step functions:**
- On the API
- At the 'system' interface e.g user interface or REST API

**Good practise for BDD:**
- Keep scenarios \(like any other test case\) short
- Keep individual steps short
- Comply with the AAA convention
- Write features in user domain language
- Use frameworks to cut down on redundancy
- Develop features and implementation gradually
- Work with the customer to validate features

_AAA convention_ : Arrange, Act and Assert

_AAA suggests that you should divide your test method into three sections: arrange, act and assert. Each one of them only responsible for the part in which they are named after._

So the arrange section you only have code required to setup that specific test. Here objects would be created, mocks setup (if you are using one) and potentially expectations would be set. Then there is the Act, which should be the invocation of the method being tested. And on Assert you would simply check whether the expectations were met.

### Summary 

BDD provides a means, through executable specifications, of ensuring traceability between user facing requirements and implementations.

## Video lecture

Testing can be done outwith the main development team for audit purposes showing independent testing. In modern software development we focus towards preventing defects as we work on a system.

Unit tests need to be fast as there can be many of them in a large system.

It is more expensive to automate acceptance testing than it is to run them manually.

*Specification by example* : A user story or use case example that explains what a system should be able to do, any feature should be able to be demonstrated this way

As BDD tests are generally system wide though they can detect defects it may be difficult to find the root cause of a failed test.

Features and user stories are often derived from collaborative workshops between developers and customers.

In reality BDD testing is done concurrently with implementation.
 
A BDD engine can map scenarios to step definitions in the system language.

**Backgrounds** : Grouping of repeated steps from multiple scenarios

**Parameterised steps** : Add a parameter so that the same step definition can be used across multiple scenarios e.g add x rather than add 10
 
**Step abstraction** : A more complex step composed of simple steps

**Example table** : A set of inputs with expected outputs that are all tested through a step function

## Reading: *Maintaining Behaviour Driven Development Specifications: Challenges and Opportunities*

In Behaviour-Driven Development (BDD), the behaviour of the required software is given as a collection of example interactions with the system, expressed using natural language sentences organised around a “Given-When-Then” structure.

**Issues with BDD**
- Maintenence challenges
- Duplication in specification
- Its use changes the team’s traditional approach to software development, and that can be challenging
- Its benefits are hard to quantify

_BDD is used more in private organizations than in other types of organization._

"BDD enables teams to write standard tests that are more expressive.”

**Benefits of BDD**
- Software specifications are expressed in domain-specific terms, and thus can be easily understood by end users
- Improves communication between various project stakeholders
- Specifications can be executed to confirm correctness or reveal problematic software behaviour\(s\)
- Code intention can be easily understood by maintenance developers

**Maintenance challenges**
- _Size of BDD Suites_ : To provide context for the main-tenance challenges reported, we asked for information about the typical sizes of the BDD suites used and managed by ther espondents. Clearly, the maintenance challenges reported are likely to be of less significance if typical suites contain numbers of scenarios \(i.e., examples\) that can be managed by hand
- Specifications can be hard to comprehend
- It can be hard to locate sources of faults, especially in large BDD suites
- It can be difficult to change specifications for the purpose or fault correction, accommodating new requirements, or adapting them to new environment

**Duplication challenges**
- The process of duplication detection and management canchange the desired software behaviour
- Necessitates changes in several places in the suite duringcmaintenance and evolution
- It is hard to use existing duplicate detection and management tools to detect and manage duplicates in specifications expressed in a natural language
- BDD tests are end-to-end tests that are usually strongly connected to their unit tests, and that makes the process of detecting duplicate BDD tests difficult