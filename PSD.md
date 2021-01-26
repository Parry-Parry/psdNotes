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

## Week 18: Evaluating Test Suites
### Slides
#### Effectiveness and Efficiency of Tests

- Testing any system requires effort
- Even if test cases are automated
 - they still need to be developed and maintained
- Each line of test case code should therefore considered as an on\-going cost for a development team
 - just like the on\-going cost of maintaining a line of application code, or paying a monthly fee to keep servers online
- A software team therefore needs to be able to judge what return on investment they are likely to make on testing effort
- Given that the purpose of a test suite is to prevent the introduction of defects, there are two useful properties to consider
 - The effectiveness of a test suite
 - The efficiency of a test suite

- Effectiveness concerns the ability of a test suite to prevent a defect being introduced into an application
- Highly effective test suites will ensure that the probability of a defect being introduced into a system undetected is very low
 - as there is a high probability that the defect will cause one or more test cases to fail

- Efficiency concerns the cost of maintaining the test suite
- In practice, there is a trade off between:
 - maximising the test coverage of a system to increase the number of defects discovered
 - minimising the cost of conducting testing per defect discovered
- The easiest way to implement an efficient test suite is to remove all the test cases
- Equally, whenever a test case is added to a test suite to increase coverage
 - it increases the probability of redundancy
 - reducing the efficiency

_A software team needs to work to find the compromise between the two for their project._

#### Useful Metrics

- Effectiveness:
 - Post release reported defects
 - LoC reached during test suite execution \(Also Efficiency\)
- Efficiency:
 - Test suite execution time
 - Failed tests per defect
 - Test Suite LoC

#### Test Suite Run Time

- Test suite run time is an important efficiency metric
- Unit test suites in particular should run very quickly
- Some guidance, such as Fowler in his book on continuous integration advocate a run time for a build and test process to be less than 10 minutes
- This is usually acceptable for a build process for an overall system
- However, it is useful for the test suite for a single class or package to be executable within a few seconds, so that a developer can:
 - incorporate them into their development workflow
 - importantly, ensure that they pass before changes to the module are committed to the change management system

- Test suites that take too long to be executed \(particularly unit test suites\) may well fall into disuse
- Tools like profilers can be used to evaluate the run time of test suites and also identify bottle necks
- A common cause is the inclusion of IO interactions in unit tests which should be eliminated using some form of test double, such as a mock

#### Test Code Coverage

- One way of measuring the efficiency and effectiveness is to track how different parts of a target application are exercised during the execution of a test suite
 - This is often measured in terms of lines of code ‘touched’ during execution
 - A more precise measure would be in terms of statements executed, or even expressions evaluated
 - This is because a line of code may contain conditional expressions that cause only parts of the line to be fully evaluated
- Regardless of the unit of measurement adopted \(but assuming LoC\)
 - Effectiveness can then calculated as the unique LoC that were touched during the execution of the test suite, divided by the total LoC in the application
 - Efficiency is the total LoC in the application, divided by the total non\-unique LoC executed, plus the total number of unique lines. So, as the total LoC executed increases efficiency declines
- Both the efficiency and effectiveness metrics can be adjusted

_Notice that test code coverage is a form of dynamic code analysis._

#### Using LoC

- It may make sense to ignore certain types of lines of code when evaluating test code coverage
- Note that method definitions are usually included 
 - as the declaration is assumed to have been ‘executed’ when the method is called, even though this isn’t strictly true

**Can ignore:**  
- Declarations such as import statements
- Parentheses
- White space
- Source code documentation
- ‘Uninteresting’ methods, such as accessors and mutators

#### Limits of test code coverage

- Although quite simple to implement, test code coverage can be misleading
 - primarily because it doesn’t directly measure anything to do with defects
- Effectively, test code coverage assumes that defects could be uniformly introduced into any line of code in the code base
- In addition, test code coverage assumes that exercising a line of code, statement or expression is sufficient to expose any defects it might contain
 - This is not necessarily a very safe assumption, as it depends on the quality of the test suite

_A more common problem is that where test code coverage is emphasised over defect coverage, developers may be tempted to implement tests that increase coverage, but lack assertions, effectively gaming the metric._

#### Mutation testing

- A more sophisticated measure of test suite effectiveness is the extent to which the test suite will detect the introduction of defects as a software system is changed
- The aim of this technique, called mutation testing, is to estimate the likelihood that a change to a software system will be detected by one or more failing test cases

- The technique works by representing the introduction of defects into a system as combinations of small\-scale code mutations of the target system’s code
- The ability of the test case to act as a detection system for the presence of these mutants is considered to be analogous to its effectiveness in detecting the introduction of defects

#### Mutation Operators

- The key concept in mutation testing is that of a mutation operation
 - These are small legal alterations to a program’s logic that could potentially have an affect on it’s behaviour
- Mutation operations are small and well defined
 - so they can be applied automatically in a wide variety of combinations to generate a large number of mutant programs
 - In addition, mutation operations should always result in viable mutants e.g no syntax errors

#### Types of Mutations

Replacing:  
- conditional operators with their boundary counterparts
- infix mathematical operators with other operations
- member field values with default or other values
- variable values with default values
- constructor calls with null assignments
- returned values with default values
- method call results with default values

#### Mutation Tetsing Process

- The process begins with a baseline version of the software system and accompanying suite of test cases
 - The baseline system is said to be 'green'
 - This means that the system passes all the tests in the suite, and as far as the test suite can determine, is free of defects
- Next, a large number of of the target system are generated by applying random combinations of mutation operations to the system’s code
 - These mutants can be applied to the system source code, binaries or any intermediates as most appropriate for the target programming language

#### Classifying Mutants after Testing

- The test original test harness is then applied to each of the mutants in turn
- Each mutant is then labelled according to the outcome:
 - Killed mutants are successfully detected by the test suite
 - Survivor mutants successfully pass all tests and are undetected
 - Undetermined mutants are programs that do not halt
- A survivor may indicate some aspect of program logic that isn’t covered by a test, or the mutant may be functionally equivalent to the original baseline
- Undetermined mutants may be due to a runtime runtime error, or if the test run breaches a timeout threshold caused due to a mutant loop\-continue condition, for example

#### Mutation Tesing Metrics

- Efficiency can be calcuated as the number of killed mutants divided by the number of failed tests during the execution of a test suite
 - Ideally, there should be a 1\-1 relationship between mutants and failed tests
 - If a single mutant causes a large number of tests to fail, it may indicate that the test cases overlap
- One disadvantage of this approach is that it doesn’t address the converse issue of redundant tests that never fail \(but still need to be maintained\)
- An alternative approach is therefore to calculate the size of the minimal test case set
 - For a given set of mutants, this is the smallest set of test cases that can cover all defects
 - Unfortunately, finding the minimal test case set is a hard search problem, so tools that provide this feature usually, do so as an approximation

#### Configuration space and optimisation mutation testing

- **Choice of mutant operations**
 - These will have a significant impact on the type of defects simulated
 - Conditional mutant operators simulate off\-by\-one programming errors, for example
- **Number and combination of mutation operators applied to a program to produce mutants**
 - The more mutants created, the richer the set of defects to be evaluated, but also the greater the risk of redundant mutants
- **Timeout period for completing a test case**
 - Mutations may lead to mutants that don’t terminate
 - It isn’t possible to determine which mutants won’t terminate
 - Therefore, mutation testing needs to set a timeout for each test
 - This can be configured to be similar to the timeout for the green test suite
 - However, this may not allow for mutants that cause extra \(but not infinite\) loop cycles to run etc
- **Scope of test suite for each mutant**
 - Some tools like PiTest determine the coverage of each test before undertaking mutation testing
 - This can be useful to:
  - limit the selection of test cases that need to be applied to a mutant
  - help to avoid running tests if their scope hasn’t changed since a previous run

#### Comparing mutation test results across applications

- These metrics are often tuned to take into account the nature of the target application
- Consequently, it is important to be wary when comparing mutation testing metrics across projects
- This is because:
 - Two different configurations for different projects will have different affects on the performance of the underlying test suite
 - Two projects may have very different characteristics, that are better tested using very different configurations

#### Limitations of mutation testing

- Although often more informative than test coverage, it is also important to be aware of the limitations of mutation testing:
 - The effectiveness of the mutation testing process is dependent on careful configuration of the process
 - Mutation operations \(or their random combination\) may not be representative of the types of defect that are introduced into a project
 - Mutation testing takes a long time to run, because the entire test suite must be executed on each mutant
- Precision defects may not be manifested by mathematical mutations, for example
- Similarly, external dependency defects may not be captured unless mutations are applied to a build script

#### Tools for Mutation Testing

- PiTest for Java
- Mutpy
- Stryker

#### Summary

Evaluating test suites is an important component of a quality assurance process.

## Week 19
### Slides
#### Non-functional requirements
- Emergent characteristics or properties of the overall system that must be measured to be satisfied rather than observed as a provided feature as for functional requirements
- Consequently, non\-functional requirements cannot typically be checked for in unit tests or through static analysis
- They can only be tested once an implementation of a system has been realised
- The implementation tested may be the final system, or a prototype
- Alternatively, it may be possible to build a model from which the characteristics of the final system can be approximated
- An advantage of testing non\-functional requirements is that they may act as an aggregate for more complex functional properties that are too complex to test individually

#### Information needed for testing non\-functional properties

- The tester formulates a hypothesis concerning the system under test \(the requirement\)
- then constructs an experiment to determine whether the hypothesis is satisfied

_A well formulated non-functional requirement should describe the:_
- property of the system to be measured
- metric to be used
- operating conditions in which the requirement must be satisfied
- threshold the system behaviour must exceed to satisfy the requirement

#### Safety critical environments

- The operation of many systems occurs in conditions which are potentially harmful to the system or to humans who operate or depend on the system
- These dangers may arise from an adverse environment in which the system operates, or the nature of the system itself, should it malfunction

_Examples of software used in safety critical contexts include:_
- Automatic pilots for transportation, such as aeroplanes
- Equipment used in the operation of particle beam radio–therapy equipment
- Space based technology, such as satellites, space craft and planetary rovers
- Nuclear power station management systems

These systems are called safety critical because a principle concern for the system design and evaluation process is to gain confidence that the operation of the system will not cause the system or its users harm.

Testing the safety of a system is concerned with the development of test cases which demonstrate that harm will not be caused in the adverse environment in which the system will be used.

#### Reliability testing

The reliability of a system is the extent to which a system performs according to its specification. 

_Metrics include:_
- Probability of failure on demand : an estimate of the probability of failure each time a system is accessed
- Mean time to failure : how long it takes for a software system to fail from initiation, or the average time between failures
- Down time : how much time can be lost to system outages over a year

_This is useful for high demand, continuous use systems, such as high volume transaction processing._

#### Methods for testing system safety

- **Model driven development** allows implementation software and test suites to be generated automatically from platform independent models
- Test cases are derived from assertions about legal and illegal states for the software model

**Cleanroom development** : automated and statistical methods to select test cases for execution, and is used to calculate an estimate of a software system’s PFD, and a confidence in the estimate

**Hazard and Operability Study (HAZOPS)** : used to identify flows of information between software components

Questions can then be asked about the flows of information, such as what happens when the information is incorrect, or arrives too early.

- The emphasis in the use of formal methods for testing is to gain accurate measurements as to the reliability of a system, to provide input into a safety case
- Safety cases are justifications that a system meets its safety requirements
- In contrast, the purpose of a HAZOPS is to explore the consequences of a failure in one or more components for the rest of an information system

#### Systems operating in hostile environments

- electronic voting systems : threatened by agents who wish to subvert the political result of an election
- friend\-or\-foe detection systems : threatened by enemies who wish to trick them into firing on friendly aircraft, or not firing on hostile aircraft
- digital rights management systems : threatened by copyright ‘pirates’ who wish to make unauthorised copies of digital media for re-sale
- network security systems : threatened by attackers who wish to gain unauthorised access to vulnerable services on remote servers 
- authentication systems : threatened by attackers who wish gain unauthorised access to information resources

Distributed systems in particular \(or their components\), are often considered to operate in hostile environments, because some or all of the other network participants are not known to the system itself.

#### Security testing metrics

- System threats actively search for defects in the system
- Consequently, it is necessary in these contexts to conduct tests to gain assurance that the system is resistant to such attacks

_Metrics Include:_
- attacker capabilities or knowledge required to penetrate the system
- time and resources to penetration
- unpatched vulnerabilities per line of code
- patches issued per year
- successful penetrations per year
- attack surface exposure

- Note that time and resources to penetration, giving an estimate of how long it would take an adversary, and how much resource would need to be applied in order to penetrate a system.
- The idea comes from assessments used for physical safes which are given a time and resource rating

#### Security testing methods

_Vulnerability testing including:_
- SQL injection testing
- port scanning
- Fuzz testing : in which a software system is supplied with unusual or malformed \(fuzzed\) inputs that may cause the system to behave in unexpected \(and insecure\) ways

_Fuzz testing is an effective means of detecting buffer-overflow vulnerabilities._

- Penetration testing : in which a red team or attack team is tasked with gaining unauthorised access to the resources protected by a system

_Penetration testers may concentrate on technical vulnerabilities or also engage in social engineering to gain access to a system._

#### Performance testing

Performance testing is concerned with assessing how a system copes with different rates of input:
- throughput : the amount of transactions that the system can process in a given time
- the maximum rate of transactions that the system can process
- response time : the average or maximum length of time taken to respond to a transaction request

Once a property and metric has been selected, there are two types of test that can be performed with respect to the threshold:
- Limit testing is concerned with demonstrating that a system behaves normally within a required limit

Limit testing is used to demonstrate that a system behaves as expected within required operating limits.

- Stress testing is concerned with discovering what happens when a particular limit is breached

Stress testing is used to discover how a system behaves beyond the operating limits specified.

#### Scaling effects in system testing

- In system tests, and to a certain extent, integration tests, we are concerned with demonstration that a system as a whole is functioning correctly
- This means that we shouldn’t really use test doubles because we can’t be sure that the intended behaviour that we assign to them reflect the actual implementation

- Effectiveness tells us how good a test suite is at preventing the introduction of defects
- Efficiency tells us about the cost of maintaining the test suite per defect prevented

One problem however, is that as the size of a software system increases \(measured in terms of number of components, lines of code, users or any other metric\), the number of tests required to achieive a given level of effectiveness increases exponentially.

This is because the number of possible paths through a program, or states that the program can be in increases exponentially as the size of the system increases linearly.

#### Dimensions of scale

Scale can affect many different characteristics of software systems and consequently have different impacts on their testing.

_For example:_
- number of lines of code
- number of software modules and inter\-dependencies
- number of software platforms
- variations in build and configuration of deployments
- duration and variation in inputs
- software development team\(s\) size, locations and experience
- number of geographic locations and network connections
- number and variation in users

- Increasing any one of these may cause an exponential increase in the complexity of the system and the number of potential system states
- Ultimately, this means that performing system tests at scale can be very expensive, sometimes bordering on the infeasible
- As a consequence, development teams need to develop a system test suite that carefully prioritises the most important properties, features or use cases of a system

#### Social\-technical systems

- Socio\-technical systems, sometimes called computer\-based systems incorporate both computer software and hardware, the computer system’s users, and the surrounding organisational and cultural practices
- Consequently, the system boundary is drawn around the organisation as a whole: the software and hardware systems are just some of the components to be considered in the overall system
- This perspective introduces socio\-technical issues of scale and complexity for testing a system

- From a socio\-technical perspective, the organisation as a whole must be tested when a new software system is introduced, and not just the software itself
- Introducing a new software system will cause the rest of the organisation to evolve in response
- Consequently, the whole system must be tested for potential ‘defects’ which have been introduced by the system evolution

_Unfortunately, testing socio\-technical systems effectively is challenging for several reasons:_
- The members of the organisation may not be available to take part in tests
- Obtaining realistic test scenarios may not be practical
- Identifying and covering the real working practices may prove difficult
- The organisation may evolve independently of the system

#### Systems of Systems

- systems of systems represent the extreme end of the scale for challenges in software testing
- A system of system represents multiple heterogeneous semi-autonomous systems that cooperate or are coordinated to produce emergent effects

_Examples include:_
- electronic stock exchanges
- military coordination systems 
- air traffic control systems
- supply chain control systems

- a system of systems is not under the control or any real coordination of any one actor
- Individual systems may evolve independently of neighbouring systems and the overall system of systems

_Testing a system of systems is extremely challenging because:_
- Each of the member systems will have different cultures and practices
- The system cannot be isolated or configured for a test
- One of the member systems may evolve during a test
- The expected outputs for the system are not easy to define

#### Getting feedback from the wild

- Due to the difficulty of running acceptance tests many development teams have augmented their applications with mechanisms for gathering information from their users
- These can either be automated submissions of crash reports, including information like stack traces and heap state, or facilities for manually submitting defect reports from within an application
- The approach effectively turns the user base for a system into its testers, leveraging the scaling effect to mitigate the problems of large scale system testing
- The approach is dependent on having an audience of users who are willing to cooperate as \(often unpaid\) testers
- Mature systems that have already gained acceptance amongst a large user base will recieve the greatest benefit in terms of test coverage of features
- Conversely, newer systems, that might benefit from user testing lack the audience

_There are two ways of partitioning the user base for user testing purposes:_

**Beta\-testing**

- release new features for an existing system to a sub-set of the system’s users
- The advantage from the users’ perspective is that they receive advance notice of new features that are nearing completion
- From the development team’s point of view, beta-testing helps to control risk during the staged release of new features

**A/B testing**

- Can be used to evaluate different candidates for a new feature
- The development team release two different versions of the same feature to different subsets of the user base
- The users may be partitioned by a particular strategy \(such as geography\), or randomly
- Metrics are then gathered about user behaviour to decide which of the two variants is more effective

_Due to the ease of distributing new features, A B testing is commonly used in web application development._

#### Summary

Increasing scale in a software or computer based system reduces the coverage and effectiveness of testing efforts, even if a proportionate number of resources are applied to testing.


