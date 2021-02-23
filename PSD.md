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

## Week 20 (Kindly done by Marc @csboomboom)
### Software Architecture:

- **Software components:**

o  A software component refers to a software bundle of self-contained state and
behaviours with well-defined interfaces.
o Some components can perform their function, but others depend on information
and functions provided by other components.
o Component-oriented system: collection of interacting components that have been
combined to realize some wider purpose.
o  Components are useful because they allow us to reason about the large scale sub-
systems within an overall architecture, without worrying about the behaviour of
individual objects or their implementation in code.
o “A component is a physical manifestation of an object that has a well-defined
interface and a set of implementations for the interface” (Hopkins 2000).
o  “A coherent package of software artifacts that can be independently developed and
delivered as a unit and that can be composed, unchanged, with other components
to build something larger” (D’Souza and Wills 1999).
o “Components extend [object oriented] principles by strengthening the role of the
interface and by a separate notion of component specification. Components must
conform to a component standard” (Cheesman and Daniels 2001).
•  **Component based software system:**
o Example: an airline reservation system.

- Booking management, payment processor, boarding pass issuer, etc. may all
    be isolated or connected components.
- Booking would probably be separate from other components, but payment
    processor might be used elsewhere.
- Boarding pass issuing might be reliant on booking management component
    though, etc.
- **Distinguishing between objects and components:**

o  A component is a self-contained, self-controlled and evolving bundle of smaller
scale objects.

- Long lived entities that are generally deployed for the full lifetime of a
    software system.
- Objects may be created and destroyed throughout lifetime.

o  A component oriented system can be distinguished by a middleware framework to
mediate interactions between components.
o The middleware can incorporate an interface definition language (IDL) that is used
to define the published interfaces of each component in the system.

- Components in component oriented system, might be distributed between
    different environments and hosted on physically different hardware systems.
- Can't interact as a result directly with component implementation, in the
    same way as with an object.
o Components are orchestrated by defining an assembly either during system
initialisation or dynamically at run time.
- Assembly is distinct from implementation, specifies which components will
satisfy the required dependencies for each component in spec.
- Normally identified by type and a release version.
o Components in the same component oriented system may be implemented in
several different programming languages.
- All provide support for the same middleware and IDL.
- Each interface provided by a component may be realized by a different
object within the component.


```
o BOTH are software runtime entities with an address, state and behaviour.
```
- Component has a specification like objects have an associated class.
- **Given we know that loose coupling is good, so why not make every object in the
system a component?**
o Mediating component interactions through a middleware imposes additional
communication costs on top of that required for direct object to object interactions.
- This is because messages must be encoded, transmitted and then decoded by
the middleware.

o  There are additional development costs associated with exposing an object as a
component, since it forms part of the system’s published API.

- The documentation for all of the interfaces to a component need to be
    maintained, as it should be expected that others will need to understand how
    to use them.
- The interface specifications of a component cannot be readily changed
    without disrupting the implementation of other components in the system or
    infrastructure, which may be implemented and maintained by other software
    teams.

o  Component specification and design should be maintained as part of the system
documentation.

- Making every object a component -> system documentation effectively
    duplicates the underlying language documentation.
o The decision about which objects to treat as components will, to a certain extent,
be specific to the software system under development.
- Role of the component engineer -> which are the right objects to make
components of.
- **General purpose and application specific components:**
o **General purpose components:**
- Provide common functionality that is intended for reuse in many different
applications.
- Example: the card payment processing component in the reservation system
could also be used to collect payments for duty-free shopping in an airport or
on a plane, pay for meals in the airport restaurant, etc.
- Are normally very well documented and stored in a component repository.

o  **Application specific components:**

- Implement the problem specific functionality and business logic of the
    application.
- The component developed to issue boarding passes at check-in for example,
    will contain business logic specific to the job of converting the airline’s
    reservation data into a boarding pass.
- Are often called the application glue, because they do the job of orchestrating
    the behaviour of the general purpose components to realise application
    specific needs.
o Robert Glass (2001) argued that software engineering is very good at developing
and managing general purpose components (such as the card payment processing
system), but quite bad at translating components that contain business logic into
reusable components.
- For example, the reservation component could, in principle, be adapted to
other uses, such as booking restaurant tables, travel on buses or cinema
tickets. However, there are often subtle technical (and socio-technical)
reasons why the business logic of reservation booking in one domain doesn’t
work in another context.


- **How much functionality to expose?**
    o For components they write themselves, a component engineer will need do decide
       how much functionality will be provided by each component under development.

o  Combining lots of functionality in a component complicate use and maintenance
of the component:

- Changing the component may effect the use of the component by many other
    different systems.
- The interactions between the different component interfaces will also need to
    be carefully documented.
o Making components very simple complicates the interaction of the component.
- Lots of simple component tasks have to be orchestrated to achieve some
useful functionality for the application.

o  One way of mitigating this dilemma is to nest simpler components within more
complex ones.

- Then some of the functionality of a component is encapsulated (and
    replaceable) with other sub-components.
- This approach can also help minimise the management of interactions
    between components at any given level of decomposition in the system.
- **Component diagram notation:**
o UML component diagrams are a useful notation for sketching the high level
architectures of software systems
- Expressing their major sub-systems as components and the interconnections
between them as bound interfaces.
- The figure illustrates the basic wiring notation for component diagrams.
▪ In the diagram, a component is represented by a box with a ‘plug’
widget stereotype. Each component has a label (in this case, A and B.
▪ In addition, component A is providing an interface I, which is shown as
a facet (but looks like a lollipop) stereotype attached to the component.

▪  In addition, the figure shows that component B requires interface I,
denoted by a connector, called a receptacle drawn around the facet.
o Take careful note of the way the provision of and requirement for interfaces is
expressed.

- Facets indicate provision and receptacles indicate a requirement.
- You may find this counter-intuitive, if for example, you think of the
    arrangement as like an electric plug and socket, since the notation is
    reversed. A plug (the requirer) fits into the socket (the provider) rather than
    the other way round.
o Notice that this has implications for what an interface means in this context
compared to an interface in a programming language like Java.
- An interface on a component in an assembly is more like a network port on a
server.
- The interface is actively being consumed. The interface is an actual entity with
an endpoint address or identifier, just like a component. This means that if a
component is denoted as exposing two interfaces of the same type, they will
have different endpoint addresses at run time.


- **Separation of concerns for component systems:**
    o A component has a clearly defined responsibility for some function.

o  A component should not be affected by changes to the implementation details of
other components.
•  **Design by contract:**
o In this approach, the interface definition for a component constitutes a ‘contract’
between the provider and the supplier of some functionality.

- Meyer, who developed the Eiffel programming language, called the interface
    documentation a ‘contract’ because it should describe the:
       ▪ Benefits of using the interface that are offered by the providing
          component.
       ▪ Obligations imposed on the component that proposes to use the
          interface.

o  Meyer also defined the term ‘design by contract’ to describe the process that works
with these very precisely documented interfaces to compose software systems.

- **Preparing a component interface contract:**
    o Document for interface can include:
       - Visible component state.

▪  Realized by the providing component.

- Invariants.
    ▪ Describe the legal states of the providing component.
- For each method in the interface:
    ▪ A signature.
       - Method identifier, argument identifiers and types, method return
          type and any exceptions that might be raised as a result of
          improperly invoking the method.
    ▪ Pre-conditions.
       - Describe the required state of the providing component before the
          method can be invoked and any restrictions on supplied
          arguments that cannot be expressed in the method signature.
    ▪ Post-conditions.
       - Describe the state of the providing component after the method
          invocation has been completed and constraints on any values
          returned to the calling component that cannot be expressed by the
          IDL’s type system.
    ▪ Semantics.
       - For example the correct sequence that methods should be invoked
          in.

▪  The visibility of each method.

- To other components in the system.
o Different parts of a contract can be expressed in different ways:


- Method signatures are normally expressed formally in an interface definition
    language.
- Invariants, pre-conditions and post-conditions (collectively known as
    *constraints) and semantics can be documented informally using source code
    comments, but can also be expressed formally.
       ▪ Example formal notations include the javax.validation package
          annotations and the OCL constraint language.
- **Checking component contracts:**

o  Statically at compile time.
o Using test frameworks such as JUnit.
o Within the program logic at runtime.
o By the component middleware at runtime.

- **Software failures caused by incompatible components:**

o  Why is all this additional documentation so important?

- It certainly reinforces the argument that software engineers should be very
    careful about choosing which objects should be treated as components, given
    the extra overheads of documentation that seem to be involved.
- Precise, accurate interface documentation is important to prevent the misuse
    of components when they are reused in different assemblies.
o The Ariane 5 disaster is commonly referenced as an example of the consequences
of poor component specification.
- A simple casting overflow (64 bit to 16 bit) in inertial reference software was
reported as data to the flight control system (rather than as diagnostic
information) causing the loss of the European Space Agencies $500 million
launch system (Lions 1996).
- **The problem of leaky abstractions:**
o The Ariane 5 failure was caused by the problem of leaky abstractions, noted by
Joel Spolsky.

o  In component terms, this means that whenever two component implementations (a
provider and a requirer of an interface) are wired together in an assembly, their
future evolution is influenced by assumptions about:

- The way that a providing interface will be utilised.
- The way that the providing interface is realised.

o  Spolsky originally argued that the leak comes from the underlying implementation
through the abstraction.

- The developer of the requiring component demands to know more about the
    underlying provider implementation in order to build a better system.
- However, the leakage of information goes both ways, because the provider of
    an interface becomes constrained by assumptions as to how it is
    implemented.
- I was at a presentation by a Google engineer once, who suggested that "every
    observable implementation detail of your system is your contract.
       ▪ Examples of where assumptions might be made about incidental
          implementation details include:
             - The ordering of objects received from an integrator over an-
                unordered set.
             - The behaviour and structure of a database system - knowing how
                queries will be evaluated can have a big impact on performance.

▪  So, despite a determination to separate the interface to a component
from its implementation, we find that they become coupled, because
the semantics of a component’s design become part of the interface.


```
▪ In effect, the distinction between what an interface provides and how it
provides it is not clear cut because often how the interface is provided
matters to the requiring component.
```
▪  Consequently, safe component composition is an area of active
research in software engineering.

- **Architectural patterns:**
    o As was covered in OOSE, design patterns address design problems at the scale of
       class interactions.

o  However, they are less suited to addressing larger-scale design problems that
concern the overall architecture of a software system that may be distributed
across many different computers or environments.
o Now let's take a look at a number of architectural patterns, sometimes called
architectural styles, that show reusable solutions to architecture level problems.

- Model view control.
- Client server.
- Peer to peer.
- Message oriented architecture.
- Pipe and filter.
- Plugin architecture.

•  **Separating concerns in user interface design:**
o Let’s consider how this principle applies to the design of interactions between a
software system and its user.

- A typical information system will be responsible for:

▪  Storing user data: (text, images, video, audio, relations...)
▪ Presenting different views of data: (tables, graphs, previews,
thumbnails, samples, streams, downloads)
▪ Changing the data: creation, deletion, editing, duplication...).
o
o The diagram illustrates the model-view-control architectural pattern which
embodies this approach using a component diagram.


- Architectural patterns are often easier to describe using a component diagram,
    rather than a class diagram, as they represent the arrangement of long-lived
    assemblies in a system, rather than the logical organisation of a small number
    of classes.
- The pattern is primarily concerned with a separation of concerns between:
    ▪ The internal representation of data held in a Store and presented as a
       Model interface.

▪  The different perspectives on that (potentially complex) data model
presented to the outside world via the View
▪ The transformations that can be applied to the data model by the
Control.

- Notice that both the Model interface, as shown by the associations with the
    port on the UserInterface boundary.

▪  However, the Store has no dependency on the other components.

- A key benefit of this approach is that each of the components has a clear
    responsibility and can be changed without affecting the other components.
       ▪ The component that realises the View and Control can be altered
          without changing the underlying data representation.

▪  Similarly, the implementation of the Store component can be changed
independently of the UserInterface, so long as the replacement Store
still provides the same Model interface.

- Typically (but not necessarily) the View and Control components are collated
    into a single top level UserInterface component, as shown on the diagram.

▪  This reflects a common situation where the user interface is constructed
using a framework or toolkit such as Swing or GTK.
▪ In fact, the MVC pattern is so prevalent in user-interface toolkits, that it
often isn’t necessary to consciously think about arranging the
interaction between a user and a system in this way: the design of the
framework enforces the conventions for you.

- One consequence of this convention is that the View and Control components
    are often coupled together.
       ▪ Changing the Control may also mean changing how some of the model
          is presented to the user in the View, and vice-versa.

o  **Adapting the MVC pattern:**

- Beyond system organisation, the pattern leaves considerable flexibility as to
    how the internal implementation details of components and interactions
    between components are arranged.
- Options include, for example:

▪  The retention of some model information in the View.
▪  The View can be updated as a result of notifications from the model
that something has changed or by the View polling the model.
▪ The View and Control interact directly with the system’s user at the
system boundary.

- This can be useful if parts of the model don’t change very often and repeatedly
    refreshing the view causes unnecessary work.
- Polling can occur either as a consequence of user action or periodically.
- The View and Control interact directly with the system’s user at the system
    boundary.

▪  This may be a human, or another software system.
▪  The mode of interaction could be textual, graphical, video and so on.
•  **Building a distributed system:**


```
o Distributed architectural patterns are concerned with the organisation of services
within a distributed system in accordance with the particular design considerations
that affect that system.
```
o  There are several reasons that a distributed system might be adopted:

- Desirable to access services from different locations.
- Infeasible to store and process data on a single computer.
- Composed of many different software components from different
    organisations

o  Patterns:

- Client-to-server.
- Peer-to-peer.
- **Benefits of centralising information storage and service provision:**

o  The management and organising of data can be maintained (and controlled) in a
single, consistent structure.
o The problem of ensuring consistency between multiple copies of the same data
item is avoided.
o The approach provides a single, globally known, point of access to users.
o  The management of changes to service functionality is can be undertaken in the
server rather than in multiple clients.
o We have seen similar benefits when applying the increase data cohesion design
principle and the abstraction–occurrence design pattern:

- In both cases we were concerned with reducing the costs of managing
    unnecessary duplication of data or software.
- **Client-Server architectural pattern:**

```
o
```
```
o The client-server pattern embodies this philosophy at an architectural level by
collating the management of information and services into a centralised server.
The diagram shows a snapshot of the state of a client server system using a
component diagram.
```
o  Responsibility in the system is organised as follows:

- The server is responsible for providing access to information or services it
    hosts to one or more clients through a common interface. The server is also


```
responsible for ensuring the integrity of the information it stores by
validating change requests from clients.
```
- The client is responsible for presenting information gathered from the server to
    end-users and for issuing commands to the server. The end-users may be
    people or other software components.
- **Protocols, sessions and APIs:**
o Let’s take a closer look at how the communication works between a server and a
client.

o  Communication between clients and servers is regulated by the definition of an
application level protocol describing the legal messages that can pass between
clients and servers.
o In a component oriented system, the protocol is defined by the server’s application
programming interfaces (APIs).
o  In a client-server system, there are two interfaces.

- The first interface is used by the client to indicate that it wishes to establish a
    new connection with the server in order to communicate.
- The server exports a second type of interface, the main API.

▪  This interface specifies the messages that can be sent once a connection
has been established between client and server.
▪ A separate session is established each time a client connects to the
server.
▪ This arrangement allows the server to handle multiple connections from
many clients simultaneously.
▪  The state of a connection (as perceived by the server) is maintained by
the session responsible for that connection.
o This arrangement is reflected in the figure.

- The API is provided by the server through a port, but the actual behaviour is
    realised by Session components nested inside the Server.
- There is one Session component per Client, each realising an API interface
    through a port at a different endpoint.
- Clients a and b have already established connections and are wired to their
    respective Session components in the assembly.
- The InitConnection interface is provided by and realised directly by the
    Server and is used to create new Session components.

▪  Client n is wired to the InitConnection interface and a new Session has
just been established ready to be consumed by n’s required interface.

- **Examples client-server application-email:**
    o World wide web, the subversion version control system, instant messenger
       applications such as Skype, the FTP protocol and the public key infrastructure that
       supports the implementation of secure communications are all examples.


o 
o  The diagram illustrates the architecture of a typical email system using the client-
server pattern.

- The pattern is applied between EmailClients (Thunderbird or Outlook, for
    example) and EmailServer components. The server actually provides two
    separate services to the client, with each following the client-server pattern
    and implemented by sub-components:

▪  **The Retrieval component** : provides facilities for the client to access
and download emails stored on the server via the IMAP interface, an
email retrieval protocol.
▪  **The Transport component:** allows the client to submit emails for
delivery to other users, via the SMTP interface, an email transport
protocol.

- The rest of the email system architecture is transparent to the client.
    ▪ A separate SMTP interface provided by a remote Mail Transfer Client
       (MTA) is used to forward submitted emails to their intended recipient
       via a relay mechanism.
    ▪ Another MTA makes use of a third SMTP interface to deliver emails to
       the server from other users of the system.
    ▪ From the perspective of these external MTAs, the email server is just
       another mail transport client.
- Notice also that it makes sense to compose these two separate functions
    (retrieval and delivery) into a single server component, because both rely on
    access to the internal email storage component.
- **Thin vs Fat clients:**
o **Thin client architectures:**
- Classical or purists approach to the client server pattern.
- The clients in this arrangement are sometimes referred to as dumb clients or
terminals, because they contain very little program logic.
- All information and as much functionality as possible is collected into the
server.
- The client has very limited functionality and is responsible only for issuing
instructions to the server and displaying results.
- Even decisions about how to present information to the user may be
controlled by the server.
o **Fat client architectures:**
- Take the reverse approach, devolving much more responsibility for
information management, validation, processing and storage to the clients
themselves.


- Fat client architectures can be useful because they can reduce the amount of
    communication required between the client and the server by caching some
    information in the client.
- In addition, some of the processing is delegated to the clients, reducing
    computational demands on the server.
o There is a trade-off to be made between a thin or fat client architecture for a
system.
- Devolving responsibility to the clients reduces load on the server, but risks
introducing inconsistencies in stored data and means that the clients have to
be updated more frequently as software defects are discovered.
- Fat client architectures have become more popular as processing capabilities
of client environments have improved.

▪  This has enabled the development of richer and more interactive client
user interfaces, which often need to cache more information.
•  **Limitations of client-server pattern:**
o There are a number of limitations to the client-server pattern:

- Communication between servers and clients may suffer from unacceptable
    latency.

▪  This means that it takes too long for the server to receive commands, or
for the client to receive a response.

- This problem can be mitigated by the clients caching some of the
    information received from the server (see the description of fat
    clients above).
- The scalability of the architecture is bounded by the physical resources
(computational power, network bandwidth, memory) available to the server.
▪ This limitation is inevitable because the server acts as a single point of
reference for all clients: the demands on the server grow as the number
of clients increase.

▪  This problem is exhibited by the ease with which websites can be
disabled by denial of service attacks.
▪ In the simplest case, an attacker directs as many clients as
possible to request the same webpage from a site at the same
time.

- The single point of reference in the architecture (the server) is also a single
    point of failure.
       ▪ If the server is disabled, then the entire system ceases to function.
       ▪ This problem can be mitigated by preparing fall-back servers, however,
          this then re-introduces the problem of ensuring consistency between
          multiple copies of the same data items or services.

o  As a consequence, other architectural patterns have been developed that provide
for greater scalability and redundancy.

- **Peer-to-peer architecture pattern:**


```
o
```
```
o A key problem with the client-server architecture is the difficulty of scaling
resources available to the server as the number of clients grows.
```
- The fat client architecture is one approach to managing this problem by
    moving more functionality into the clients.
- The peer-to-peer architectural pattern extends this approach by moving all
    services and data in the system into the clients themselves so that every peer
    is both a client and a server.

o  Responsibility for hosting and managing services is shared amongst all the clients.

- As the demand for resources grows due to an increase in clients, there is an
    equivalent increase in the resources available for servers, because each peer
    fulfils both roles.

o  A peer-to-peer architecture is particularly useful when a system has responsibility
for extensive computational processing, or hosting large amounts of information,
but is constrained by the physical capabilities of the hardware.
•  **Example peer-to-peer application: Tor:**
o Many people are familiar with peer-to-peer applications as a result of the
proliferation of file sharing applications such as Knutella and the various
implementations of the BitTorrent protocol.
o  The Third Generation Onion Routing (Tor) project is another example of a system
that leverages the peer-to-peer architectural pattern.

- The system is used to support anonymous and untraceable communication
    between participants on a network that the user suspects is being monitored
    by an attacker.
- Unlike communications sent directly over an Internet connection, Tor
    messages are sent via a random selection of peer nodes in the Tor network.
- Messages are wrapped in a series of layers of encryption (hence onion
    routing) by a sender.
- Each time a message passes through a Tor node one layer of encryption is
    removed so that an observer of the node cannot match incoming and
    outgoing messages.
- Eventually all the layers of encryption are removed and the message is
    delivered to the final recipient.
- As more messages pass through a Tor network, it becomes increasingly
    difficult for an observer to work out who the recipient of the message is.


```
o One key challenge in peer-to-peer architectures is service distribution and
discovery: if services are distributed to any available or participating node, how do
you know where to look for other peers offering the same service.
```
o  In addition, if anyone can participate in a peer-to-peer system, how do you
determine which of the potential peers to trust?

- **Peer discovery:**
    o There are several adaptations that can be made to the peer-to-peer pattern to
       accommodate these problems, including:
          - Using a globally known registry to record the addresses of peers in the
             system:
                ▪ In this approach, a peer first queries the registry to discover what other
                   peers are available.

▪  The registry effectively acts as a super-peer, to which all other peers
refer first for resource discovery.
▪ Each peer maintains its own registry of known other peers that have
previously contacted it to request resources.

- Searches across the peer based network:

▪  When this happens the requesting peer also reports the resources it has
available.
▪ When one peer performs a search for resources held by another peer it
asks all the peers it knows for the resource.
▪ These peers then pass on the request to their known peers until the
resource is discovered or the request times out.

- A hybrid of both patterns:
    ▪ In this approach, several registries are deployed, each of which contains
       a list of available peers. Each registry attempts to maintain an
       independent and up-to-date list of available peers by querying the other
       registries.

o  All of these styles involve trade-offs.
o The use of a globally known registry shares some of the limitations of the client-
server pattern:

- If the registry becomes unavailable then none of the peers will be able to
    discover new peers that might have the resources they need.

o  On the other hand, the peer based search has no guarantee of finding the required
resources if the search times out before the right peer is reached.
o The hybrid approach mitigates but does not eliminate the disadvantages of the
other two approaches while introducing significant additional architectural
complexity.

- **Information processing patterns:**

o  Information processing patterns address challenges of efficient information
management within a system.
o This may be for processing large amounts of data or for supporting effective
coordination between components.
o  The patterns we will look at are:

- Message oriented architecture.
- Pipe and filter.
- **Disadvantages of synchronous communication mechanisms:**
o We have ignored issues of how messages are passed between components, leaving
this detail to the component middleware.

o  We have also assumed that message passing is largely synchronous and
instantaneous.


```
o Sometimes these assumptions are inappropriate for inter-component
communication because:
```
- Underlying communication channels may be unreliable or subject to delays
    that disrupt the expected flow of computation in a component.
- The client must choose which components will provide information for a
    computation before processing begins.
       ▪ Only a single request can be made at a time.

▪  This means that the minimum time for the computation is typically a
factor of the number of information requests made.

- Components are forced to request information from other components in a
    pre-determined sequence because they need to wait for a response from each
    component in turn.

▪  However, some applications may not need responses from every
request, provided a sufficient number of responses are obtained.

- The overall system design cannot exploit computational parallelism to
    improve response time.
       ▪ A component may be unnecessarily idle while it waits for a message to
          be delivered to another component.

▪  It could be handling messages received from other components, for
example.
o In summary, synchronous communication can unnecessarily constrain design
flexibility for certain types of computation.
o  Consider, for example a component developed to search for the best possible price
for a home insurance premium, given some constraints (property value, contents
value, minimum excess, whether the purchaser wants legal cover and so on).
o The component needs to contact a large number of insurance providers and request
a quotation according to the specifications of the customer.
o  The component will then select the top five quotations and present them to the
customer for review.
•  **Synchronous vs asynchronous communication: example:**
o 
o  The diagram illustrates the communication between the client component and the
insurance providers if the client makes its requests using synchronous
communication.


```
o The time taken to identify the best quotation will be equal to the sum of times
taken by each of the individual insurance providers polled.
```
o  In addition, if any of the providers are unable to provide a response (due to
network failure, for example) additional time is added to the duration of the
computation without benefit.
o The synchronous communication also means that the component cannot deal with
other quotation requests until the first one is completed.
o
o Alternatively, the quotation component could contact each of the brokers
asynchronously, as illustrated in the diagram.
o In this arrangement, the client sends a request to each insurance provider without
waiting for an immediate reply.
o  Once all the requests have been sent, the quotation component then waits for a
minimum number of insurance providers to respond with a quotation and then
sends an initial estimate to the customer.
o As further quotations arise the estimate can be updated as required.

- **Message oriented architecture pattern:**

o  The Message Oriented architectural (MOA) pattern provides a basis for general
asynchronous communication between components.

- In the pattern, all communication occurs as discrete messages that pass
    through a message bus. The bus routes messages to the appropriate client
    based on a routing policy.
- This pattern is known by two other names, depending on which parts of the
    architecture are most significant for the design problem:
       ▪ The Message Driven pattern because all internal computation in a
          component is the result of receiving a message from another
          component.

▪  The Message Broker pattern, because a broker is responsible for
deciding which component receives which message.


## •

o  The diagram illustrates the pattern. The message bus is modelled as a single
component that provides two interfaces to clients:

- IBroker is used to send messages to other clients via the bus.
- IQueue is used to read messages from the bus that have been sent specifically
    to the client by other clients.

o  The use of standard interfaces ensures that all messages sent via the bus comply
with a prescribed format.

- This means that every client will know how to parse the structure of a message,
    even though it may not be able to interpret the content.
o The figure also shows the internal structure of the MessageBus component.
- Messages for individual clients are stored in a Queue such that there is one
Queue maintained per client.
- Each queue realises the IQueue interface provided to the appropriate client by
the MessageBus.
- Typically, the client will consume and process messages from the Queue as
quickly as it can, using the Queue as a buffer when it experiences a heavy
load of messages.
- The Client will also normally block once it has processed all available
messages in its Queue.
o Separately, clients can send messages using the IBroker interface.
- This interface is realised by the Broker sub-component.
- When a message arrives at the interface the Broker decides which Queue the
message should be added to, normally, based on the intended end client.
- The broker may not be able to deliver a message, if a queue is full, for
example, or because the message does not have a valid destination.


- In this situation, the broker is responsible for handling the message, either by
    dropping the message, or by notifying the client that the message wasn’t
    valid (by leaving a message in the sender’s queue).
- **Configuring message oriented architectures:**
o There is considerable flexibility in influencing the behaviour of a message oriented
architecture through two mechanisms:
- The relationships between queues and clients:

▪  Several clients may be connected to the same queue, for example, if the
number of messages added to the queue is typically too much for a
single client to handle.
▪ Alternatively, a client may listen for messages on several different
queues.
▪  For example, a client may maintain separate queues for normal
and exception messages.

- The policy applied by the broker to distributing messages:
    ▪ The broker may choose between different queues depending on
       different factors.

▪  The broker might choose the queue based on a specific intended
recipient, the queue containing the least messages, or the message
type, for example.

- You may have noticed that the broker pattern is structurally similar to the
    Load Balancing enterprise pattern, except that the broker decides where to
    send a request based on load.
- **Example: Stock control system:**

```
o
```
o  Let’s consider an example application of the pattern: a stock control system for a
large supermarket chain.
o The diagram illustrates the flow of stock between the different geographical
locations managed by the stock control system.
o The supermarket chain has a large number of stores, each with a limited capacity
for holding stock.


```
o The diagram illustrates the architecture of the message oriented stock control
system.
```
o  The architecture shouldn’t come as too much of a surprise: every component,
regardless of whether it is handling store, distribution centre or supplier
functionality.
o The chain maintains a number of regional distribution centres for holding larger
amounts of stock on behalf of the stores in their area.
o  When the stock of some particular item drops below a certain level in store, the
store management requests additional supplies from the distribution centre.
o The distribution centres receive stock directly from suppliers.

- In some situations stock cannot be sent directly from a supplier to the
    appropriate distribution centre.
- In this case, stock is requested from the distribution centre that can receive
    stock from the available supplier.

o Each component has it’s own queue of messages maintained by the MessageBus.
o In addition, each component can send a message to any other component via the
broker. In practice, only the following messages are required:

- The system ensures that stock is delivered to stores through message passing:
    ▪ Store to RDC requests for new supplies.
    ▪ RDCs to Suppliers requests for new stock to be manufactured and
       delivered.

▪  Suppliers to RDCs notifications when the requested products will be
delivered.
▪ Between RDCs requesting stock to be transferred as available and
notifications when that stock will be delivered.

- **Advantages of the message-oriented architecture:**

o  Communications security is centralised by ensuring that all messages pass through
secured channels on the message bus.


```
o The broker can be configured dynamically to route messages according to the state
of the application.
```
o  The message bus provides a central location for monitoring inter-component
communication.

- This is useful for logging interactions between components for debugging or
    auditing, for example.
- The structure also makes it easier to identify bottle necks or faulty
    components, since this is typically indicated by congested queues.
- **Sequential data processing applications:**
o Many software applications are required to process large volumes of data,
applying a number of transformations between input and output. Examples
include:
- Video and audio media transcoding, where video is decoded, potentially re-
formatted (size, colour model etc.) and then encoded.
- Textual analysis, where prose is checked for spelling and grammar errors in
one language before being translated into another.
- Inter-bank payment processing, where very large numbers of small scale
currency transfers must undergo a series of validations before being
approved.
- Processing and synthesising data gathered from scientific instruments.
▪ Raw instrument data often needs considerable re-processing and
integration before it can be used in analyses.

▪  Weather and climate data (temperature, pressure, humidity and so on),
for example, is gathered from a variety of sources and using a
heterogeneous range of instruments.

- **Design problems:**
    o These related applications present several design problems:
       - Each of the steps in the transformation can take a variable amount of
          processing time for a given data item:
             ▪ This can result in one or more of the steps becoming an bottleneck
                which limits the performance of the application as a whole.
             ▪ For example, video data compression may need significant amounts of
                buffered frame data before it can begin, even though other processes
                such as frame re-sizing finish more quickly.
       - Steps may need to replaced or re-ordered as the application is adapted to
          different needs:
             ▪ For example, a generic translation application might need to translate
                text from French to English, English into Mandarin and so on. In
                addition, there are different standards for correcting language grammar
                and punctuation.
       - It may be desirable to have a convenient means of re-using some functions in
          combination:
             ▪ In the translation application describe above, for example, French to
                English and English to Mandarin components could be composed to
                produce a French to Mandarin function.

•  **The pipe and filter architectural pattern:**
o The pipe and filter architectural pattern addresses these design problems by
leveraging the homogeneous format of the data being processed.
o  The diagram illustrates the basic form of the pattern.


```
o
```
o  Each transformation that must be applied to the data is implemented as a single
component called a filter.
o Each filter provides and implements the same interface, sometimes called the pipe.
o The filters are then wired into a single sequential assembly called the pipeline,
with each successive component obtaining data from a component on the left and
passing output to the component on the right.
o Two special components bound the pipeline.

- A data source component provides input on the right and requires the pipe
    interface.

▪  Similarly, a data sink component provides the pipe interface on the
right to accept the system’s output on the right.

- Finally, a Scheduler component is responsible for deciding which of the other
    components should execute at anyone time.
       ▪ The Scheduler’s job is to manage load between the other components
          so that no one component causes a bottleneck in the pipeline.

▪  The Scheduler controls each component via the Control interface.
o  The pattern satisfies the design problems described above because:

- Processor time is allocated to the different filters based on load. This ensures
    an even flow of data through the pipeline.
- All of the filters provide and require exactly one pipe interface, so can be re-
    ordered and composed as necessary.
- **Variants to the basic pipe and filter model:**
o Push or pull driven data flows.
o Sequential or concurrent data processing filters.
o Re-orderable or inter-changeable filters.

o  Branching data filters.

- **Push or pull data flow:**
    o The push or pull driven data flows reflect two different controlling processes for
       moving data to the pipeline, as illustrated in Figure the diagram.
    o **Push:**


- In the push model, data is driven into the system by an active DataProvider,
    which submits the data to FilterA for processing.
- The DataProvider will continue to supply data to the filter, until the Filter is
    blocked by a full buffer.
- FilterA will process the data and then pass the results on to FilterB.
- This process continues until the data is written out to a passive DataSink by
    the last filter.

o  **Pull:**

- The pull model is the reverse of this situation.
- The DataRequester actively polls the last filter, FilterC for data.
- FilterC polls FilterB in turn and the process continues until the last filter
    polls the DataSource for data to process.
- The results are then passed back along the request pipeline.
o The choice of which data model to employ depends on the system for which the
application is to be used:
- A push data model is appropriate when the data to be processed is being
continually generated in an unpredictable or continual way by the Provider.
- This means that the data is fed into the pipeline as and when it becomes
available.
▪ Multi-media format conversion of an entire media file, or of a continual
live stream is a good example of this situation.
- A pull data model is more appropriate when data needs to be processed as a
result of some external event in the data Requester.
▪ The Requester only initiates the pipeline when it needs the data to be
processed.


```
▪ Execution of a scientific experiment that integrates a large collection of
diverse data sets is a good example of this situation.
```
- **Sequential or concurrent data processing:**

o  The data can also be processed in different ways within each individual filter.
o The diagram illustrates the two variants using a push-style pipeline, as described
above.
o
o In a sequential pipeline, all the data submitted to the pipeline is processed by each
filter in turn, before the data is passed on to the next filter.
o  This means that processing is serialised: the total time taken to process.
o
o  In a concurrent pipeline, small amounts of data (often called chunks for text, or
blocks for raw bytes) are fed into the pipeline as soon as they become available.
o This means that the data sink receives the first blocks of data as soon as they are
processed by the last filter.
o  At first glance, it might seem that the concurrent model is always better, since it
means that data begins arriving at the data sink earlier and if the system is
distributed on a number of processing nodes the overall computation should end
more quickly.
o This may be important for certain applications that require a constant stream of
data to be written to the data sink (live video streaming for example).
o  However, there are many applications where it is better to process larger blocks of
data in one go.


```
o Compression algorithms, for example, generally achieve a greater compression
ratio (the size relationship between the raw and uncompressed data) if they are
executed on larger blocks of data.
```
o  footnote{Informally, this is because the probability of redundancy (repeated data)
increases as the size of the data block increases.

- In practice, this means that there is a trade-off between speed of execution and
    performance, made in terms of the size of data block operated on in the
    pipeline.
- **Re-orderable vs. inter-changeable filters:**

```
o
```
```
o Another decision to made when designing a pipeline architecture or framework is
the extent of flexibility that will be permitted to a pipeline constructor. Two
possible variants are re-orderable or inter-changeable filters:
```
- The most flexible option is to allow the filters to be re-ordered as desired by
    the software architect. To enable this arrangement, every single filter must
    provide and require the same interface.
- This flexibility means that the overall processing pipeline can be optimised by
    re-ordering processing activity.
- For example, in a video processing application it is quicker to crop each video
    frame and then convert them to grey scale, as shown in the diagram.
- If the reverse configuration is employed, computation time is wasted
    converting regions of each frame to grey scale that will be removed anyway.

```
o A more restrictive option is to fix the ordering of filters and only permit the inter-
change of filter implementations.
o In this case, each filter can provide and require different interfaces.
```
o  Any filter can be replaced by another filter implementation that provides and
requires the same interfaces.
o However, the heterogeneous nature of the filter interfaces means that they cannot
generally be re-ordered.
o Consider, for example, an application for converting a scanned image of a page of
book into audible speech in another language, as shown in the diagram.
o  The filters of the system might be: optical character recognition; spell check;
grammar check; text translation; and speech synthesizer.


```
o These components cannot be re-ordered and each filter requires a different form of
input data.
```
o  However, the implementation of each component can be swapped as required.
o  Again, it is possible to compromise between these two architectures, so that some
parts of the pipeline can be re-ordered, while others require set sequences of filter
types.

- **Branching filters in pipelines:**

```
o
```
```
o A final variant is to allow the use of branching filters in the pipeline, as shown in
the diagram.
```
o  A branching filter can do one of two things with incoming data: replicate the data
stream to the out-going filters; or filter each data item into one of the out-going
branches.
o Branches can be useful in pipelines for several reasons:

- Performing ancillary functions on exact copies of data, e.g. logging
    intermediate versions of a data set during a computation for debugging,
    verification or auditing purposes. This means that these functions do not have
    to be built into the filters themselves.
- Applying two different transformations to the same incoming data source
    simultaneously.
       ▪ A video stream might need to be encoded for high and low quality
          distribution, for example.
- Separating data items into different categories for alternative processing. A
    data stream might contain words in two different languages that need to be
    separated and processed differently, for example.
- **Motivation for a plugin architecture:**

o  It can be difficult to predict all the required functionality for an application,
beyond a core set of features. This may be because:

- It is anticipated that new features may need to be added over time as
    requirements change.
- Different users of the application have different requirements:

▪  Providing all the required features to all users would result in an overly
complex system and user interface.

- It is anticipated that some users will want to develop their own functionality
    for the system:
       ▪ Tailoring it’s features to suit their personal needs.
- The application will run on a variety of different platforms:


```
▪ Some of which will not be able to support all the application’s
functionality, or will do so in different ways.
```
o  A plugin architecture provides a flexible mechanism for extending the
functionality of a software system.
o In the pattern, an application is able to dynamically search for and load
components that contain additional functionality into the main system.

- **Plugin architectural pattern:**

o  The diagram illustrates the key components in the plugin architectural pattern.
o 
o The main component in the in architecture is the Registry that stores the
specification of all plugins available to the system.
o  A plugin component normally provides a standard interface that complies with the
requirements of the plugin architecture. This can provide:

- Details of how to instantiate the plugin in the application; and/or
- Details of how the component can be used in the application.

o  The main Application can query the registry for available plugin specifications of
a particular type.
o When an appropriate plugin is located, a Loader component is used to instantiate
and configure the component for use by the main application, using the
specification supplied by the Registry.
o  The plugin’s functionality can then be accessed via the specified interface, just like
any other component in the system.
o A plugin architecture is similar to a software framework that exhibits hooks and
slots.

- However, the purpose of the two are different.
- A software framework is not an application.

▪  It is a collection of utilities, libraries and infrastructures for building
applications in a particular architectural style, or for a particular
purpose.


- **How flexible should a plugin architecture be?**
    o A plugin architecture is useful for extending the functionality of a specific
       application, not for building the whole application.

o  Consequently, the range of ways in which a plugin can extend the application’s
functionality and purpose should be tightly constrained.

- An application that is built purely from plugins is in serious danger of
    exhibiting the inner platform effect.

o  Another way of expressing this is to observe that this process simply re-invents the
Java language’s primitive mechanism of instantiating classes as objects using the
new keyword.
o To a certain extent this is correct, except that the programmer does not need to
know what class will be instantiated as a plugin at runtime.
o  In addition, creating an instance via the newInstance method is computationally
much more expensive.
o So, it is important to choose which classes will be implemented as plugins because
they are better suited to being loosely coupled components, and which are core
parts of the main application.

- **Summary:**

o  Software architecture helps developers to reason about the high level structure and
key components of a software system.
o Cheesman, John, and John Daniels. 2001. UML Components a Simple Process for
Specifying Component-Based Software. Component Computer software Series.
Pearson Education Inc: Addison-Wesley.
o  D’Souza, Desmond Francis, and Alan Cameron Wills. 1999. Objects, Components
and Frameworks with Uml: The Catalysis Approach. Object Technology Series.
Reading, MA: Addison Wesley.
o Hopkins, J. 2000. “Component Primer.” Communications of the ACM 43 (10):
27 – 30.
o  Lions, J.L. 1996. “ARIANE 5 Flight 501 Failure Report by the Inquiry Board.”
[http://www.di.unito.it/~damiani/ariane5rep.html.](http://www.di.unito.it/~damiani/ariane5rep.html.)


## Week 22

### Maintaining source code and system design

* Software is easier to alter to respond to changes in the system environment, if the source code has been carefully maintained
* Characteristics of well\-maintained software source code include:
	* effective use of a version control system
	* an automated test suite
	* a clear architecture and design
	* a simple and consistent coding style, enforced through automation where possible
	* appropriate use of comments and other documentation

### Defining software refactoring

* A key discipline for maintaining the structure of a software system as it evolves is refactoring
* Refactoring should be an on\-going process in a software development project, alongside the introduction of new features
* Fowler defines a refactoring as:
	``Refactoring (noun): a change made to the internal structure of software to make it easier to understand and cheaper to modify without changing its observable behaviour.``  
* and goes on to define the verb form \(to refactor\) as the application of a series of refactorings
* As we will see, refactoring often causes changes in the non\-functional properties of a system, and indeed, can also causes changes in the functional behaviour or specification

### The refactoring process

* Refactoring can be thought of as a form of source code cleanup, with the addition of a well defined process for performing the change
* The process begins with the identification of opportunities to refactor
* Fowler calls indicators of these opportunities ‘bad smells’ in the program source code
	* A ‘bad smell’ is a pattern in the source code indicating poor structure or inappropriate coupling between modules
* Once an opportunity to refactor is identified, it is important to create tests for the affected classes, using an automated test harness framework, such as JUnit
* The test cases are important because they will be used to show that the functional behaviour of the refactored code has not changed as a result of applying any refactorings
* Of course, in well maintained code, a class or package will already have a well established suite of tests that can be used for this purpose

* Next the refactoring is planned, based on the guidance provided by the bad smells
* Once the revised design has been established, it can be applied, often using automatic refactoring tools that are provided as part of many Integrated Development Environments \(IDEs\) such as Eclipse

* At this point, the tests that were developed previously should be rerun
* If the tests are successful, then it is appropriate to commit the new design and source code to the main project
* This may involve merging the change into the main development trunk of the project source code repository
* Having completed the refactoring, new opportunities for improving the design may also be identified
	* For example, if extract method is applied to a method with a large body, it may then also be appropriate to move that new method to another class

* If one or more of the tests fail, this indicates that the refactoring\(s\) have altered the functional behaviour of the altered class
* It is necessary here to back out of \(reverse\) the changes 
* Additional planning and analysis can then take place to understand what unexpected effect the refactoring\(s\) had
* Once the slip has been established, the revised refactoring\(s\) can be applied
* This process continues iteratively, until a refactored system passes the pre\-prepared tests

### When to refactor

* The first step in the refactoring process is to identify opportunities for refactoring
* Refactoring should be treated as a parallel on\-going process, that occurs alongside other software development activities
* This means that you should be looking for opportunities to refactor when you are:
	* implementing new functionality
	* correcting a defect
	* doing a code review
	* when you are trying to understand how a software artifact works
* While you undertake these tasks, you should also be observant for examples of poor software design in the source code

### Fowler's 'Bad Smells'

#### Cloning 

Duplicate code : Source code that has been cloned rather than reused makes maintenance harder. If you find a bug in the original, you have to fix all the clones as well.

#### complex structures

* long method : The behaviour of long sequences of instructions is harder to understand, because all of the details of the implementation are presented to the reader at once. In general, methods that can’t be read on a few lines in an editor are too long

* large class : Indicates that too many responsibilities have been allocated to a single class. It is also possible that the large class contains duplicate code

#### variables and parameters

* long parameter list : Imposes stamp coupling on the design of the method, because each time the parameter list changes, every call of the method must also be changed. A long parameter list also indicates that a method that is used in different ways, depending on how it is called

* feature envy : Indicates that a method is in the wrong class, because it obtains most of its data from another class. If either the data or the accessing method change, then so will the other

* data clumps : Occurs when the same, independently sourced, data is used together in different locations in a system. This might be identifiable from duplicate parameter lists for methods, or from duplicate blocks of query method calls. Both of these examples are also indicators of cloning

* primitive obsession : Indicated by a preference for using primitive data types for representing more complex values with additional semantics. This is problematic because the semantics and supplementary properties of a data type is not explicit when it is represented as a primitive value, and has to be maintained independently of the data. A date in the Gregorian calendar could be represented by three integers, for example \(one each for day, month and year\). However, this means the relationships between these values has to be maintained elsewhere in the system

* temporary field : These are fields that are used as variables in method bodies, but aren’t always needed. Fields should only be used to record information about an object’s state that must persist between method calls

#### making changes

* divergent change : Another indicator that a class has too many responsibilities, identifiable when a single class must be altered in different ways to respond to different changes in the system’s environment. This suggests that the class has two or more different sets of responsibilities

* shotgun surgery : The opposite of divergent change, identifiable when a change in the environment necessitates a number of different changes in several different classes in a system. This makes maintenance more time consuming, and easier to get wrong

* parallel inheritance hierarchies : Identifiable by dependencies between two inheritance hierarchies, such that a change in one hierarchy causes a change in another, increasing coupling and maintenance costs

#### control structures and polymorphism

* switch statements : Indicates a reluctance to exploit object oriented polymorphism and increases maintenance costs, because each time a new option is introduced into the system, a flag and additional line must be added to the switch

* refused bequest : Sometimes a sub\-class doesn’t need all of the operations provided by a super class. This means that all the methods of the super class are unnecessarily coupled to the sub\-class

* alternative classes with different interfaces This is a 'smell' because it means that the benefits of object\-oriented polymorphism cannot be exploited. The two or more classes must be manually selected for use in the code

#### design uncertainty 

* lazy class : This can be a difficult smell to identify, given that many of the smells are about classes that do too much. However, lazy classes, that have insufficient independent responsibilities can be unnecessarily expensive to maintain

* speculative generality : Although abstracting over concrete implementation details is generally a good idea, it can be tempting to attempt to move all design decisions into the configuration for a software system. At its most extreme, this phenomenon is known as the inner platform anti\-pattern, because the system is designed as a software platform that must be configured, on top of an existing software platform

* incomplete library class : This is less of a smell, than a potential causes of other smells. It occurs when it is discovered that a class from a library doesn’t support all the operations needed by the client. In addition, the library class can’t be altered, because it is used in many other projects

#### delegation

* message chains : Occurs when a message one object accesses a data item through a series of intermediary objects. The requesting object is therefore bound to all the other objects in the chain

* middle man : Occurs when one object acts as an information broker to another object, but doesn’t actually provide any information itself. There may be good reasons for this, if the broker is a proxy, for example. If the object is just passing on information, however, it may be better for the communication to occur directly

* inappropriate intimacy : Also known as the object-orgy anti\-pattern. This smell is the opposite of accessing information via middlemen or chains. Instead, all objects freely interact with the properties of other objects, causing an 'orgy’ of couplings between them

* data class : Classes should generally have behavioural responsibilities as well as data items. If a class lacks behaviour, this is often because the behaviour has been implemented somewhere else


Many of the bad smells and refactoring remedies are illustrative of the principles of good design. These principles embody the adage ''good design has low coupling and high cohesion''. Unsurprisingly, refactoring is concerned with reducing the coupling and increasing the cohesion in a software application.

### Excessive comments vs. self documenting code

* A final bad smell described by Fowler is the excessive use of comments to explain unnecessarily complex source code
* The comments are indicative of poor structure that can be improved through the application of refactoring\(s\)
* This process helps to create self documenting code
* Once the code has been refactored, its purpose and functionality become much more self-evident, reducing the need for supplementary documentation
* This excessive documentation can be largely removed when the refactoring process is complete

### Types of refactoring

#### fixing methods

* extract method ←→ inline method
* replace method with method object

#### moving functionality

* move method, move field
* extract class ←→ inline class

#### organising data

* encapsulate field
* replace data value with object
* replace magic number with symbolic constant

#### simplifying method calls

* parameterise method ←→remove parameter
* use parameter object

#### simplifying conditions

* decompose conditional
* consolidate duplicate conditional fragments
* replace conditional with polymorphism

#### reorganising classes

* pull up method ←→ push down method
* pull up field ←→ push down field
* extract superclass
* extract subclass
* collapse hierarchy

### Smells to refactoring

| Smell           | Strategies |

* duplicated code : extract method → \(pull up method, form template method\) or substitute algorithm 
* long method : extract method → \(introduce parameter object, replace temp with query\) or replace method with method object → extract method 
* large class : extract class, extract subclass 
* long parameter list : replace parameter with method, preserve whole object 
* divergent change : extract class 
* shotgun surgery  : move method, move field, inline class 
* feature envy  : move method, extract method 
* data clumps :  extract class → \(introduce parameter object,preserve whole object\)          
* primitive obsession : replace data value with object, replace type code with class, extract class, introduce parameter object
* switch statements : replace type code with subclasses → replace conditional with polymorphism
* parallel inheritance hierarchies : move method, move field
* lazy class : collapse hierarchy, inline class
* speculative generality : collapse hierarchy, inline class, remove parameter, rename method
* temporary field : extract class, introduce null object
* message chains : hide delegate, extract method → move method
* middle man : remove middle man, inline method
* inappropriate intimacy : move method, move field, extract class, hide delegate, change bidirectional association to unidirectional, replace inheritance with delegation
* alternative classes with different interfaces : rename method, move method, extract superclass
* incomplete library class : introduce foreign method, introduce local extension
* data class : encapsulate field, extract method, move method, hide method
* refused bequest : push down method, push down field, replace inheritance with delegation

### Automated refactoring

Many software tools, such as IDEs have integrated tool support for automatic refactoring. Eclipse, for example, supports \(contextualised\) operations for automatically:

* Rename
* Move
* Extract Interface
* Extract Superclass
* Pull Up
* Push Down
* Extract Class
* Change Method Signature
* Inline
* Introduce Parameter Object
* Introduce Indirection
* Infer Generic Type Arguments
* Generalise Declared Type
* Encapsulate Field

### Limits of refactoring

* the refactoring process is a powerful mechanism for managing design quality as a software application evolves
* However, refactorings can themselves cause the software evolve and consequently can and do alter the observable behaviour of software systems
* Refactorings can cause observable changes to a software system in either the:
	* non\-functional properties
	* the application programming interface \(API\) of a system
* Refactorings which causes changes to non\-functional properties may be either beneficial or detrimental
* A refactoring might decrease a system’s overall memory footprint, whilst simultaneously reducing the system’s response time
* This may happen because the refactoring reduces the amount of cloning in a software system
* Unfortunately, this may increase the number of method calls that must be made, increasing execution time for a transaction
* These considerations are particularly important for mobile, embedded or realtime applications in which computing resources may be limited
* However, a clear design is usually easier to tune, so that over the long term, the required non\-functional properties of a system are easier to achieve

### Refactorings that alter APIs

* In addition to changing non\-functional behaviour, some refactorings require that an application programming interface \(API\) to a software module be altered
* The API is the set of public operations and attributes of one module that can be accessed by other modules in a system at runtime
* In object\-oriented systems, every object has an API defined by the public members \(operations and attributes\) of its class
* Changes to an API happens when:
	* a class member is moved
	* a class member is renamed
	* the visibility of a class member is changed
	* the list of parameters to an operation is changed
	* the return type of an operation is changed
	* the exceptions that may be raised are changed
* This may not be a significant problem if the API is for a class that is only accessed within a software system
* However, some APIs must be exposed to users of the system
* Fowler refers to these as published interfaces, because they have been exposed and documented for use by external clients of the entire software system
* Consequently, every user of the software system is coupled to the API specification
* The version of the system used is said to be a dependency for all its users

