# Code Review Standards #

This is a high-level listing of common things to check as part of a code review. This list is not meant to be exhaustive but rather a list of things that can be checked within 10 or 15 minutes.

- [Code Review Standards](#code-review-standards)
  - [Basics](#basics)
  - [Unit Testing](#unit-testing)
  - [Logging](#logging)
  - [Libraries](#libraries)
  - [Constants](#constants)
  - [Other](#other)

## Basics ##

- **Is there any repetition in the code?** – this is the DRY (don’t repeat yourself) principle. Sometimes a bit of a judgment call, the goal is to the limit repetitions of any code if there’s an opportunity to consolidate the repetitions in some kind of method. Even 2-3 lines of code can be worth this consolidation if those 2-3 lines appear 3-4 times.
- **Are there any Eclipse warnings or SonarLint warnings?** – I tend to prioritize the SonarLint warnings quite a bit less unless they’re easily fixable (e.g. – adding transient to non-serializable fields). Any of the Eclipse warnings that come out from the EDS ruleset really should be reviewed and suppressed if the team deems it appropriate or refactored if not. This may require checking out the branch and building in Eclipse to see these (is there an automated way?).
- **Is the code formatted with the EDS ruleset?** - see [here](https://github.nwie.net/Nationwide/EDS-Apps/wiki/Workspace-Setup#eclipse-configuration) for setup instructions.
- **Access modifier standards** - prefer more privacy than less, i.e. `private` > `package private` (no modifier, ideal for unit tests) > `protected` (only use if overriding in a child class) > `public`.

## Unit Testing ##

- **Are new branches of code covered with unit tests?** – typically, POJOs are excluded from this check if they don’t implement any logic outside of getters/setters. My personal expectation is usually one unit test per branch of code, where an example of a branch of code would be an if/else block, where the if is covered by one test and the else by another.
- **Are unit tests using `EasyMockSupport` when mocking objects?** - this is a nice convenience base class that supplies mock methods as well as `replayAll` and `verifyAll`, which cleans up test code quite a bit.
- **Remove Spring test cases and replace with EasyMock** – Another personal opinion—we don’t really get any benefit from creating a test Spring context when testing our apps. These test cases should generally be avoided and replaced with setting EasyMock mocks on the tested objects.
- **Are unit tests clearly stating what’s being tested?** – while it makes sense to keep normal class method names a bit concise and to the point of what they’re trying to do, test method names should be longer and more verbose to describe which branch of a method is being tested. Ideally, this gives other developers some idea of where to look when that specific test breaks. Example: `isEligibileForOnlineAccountShouldReturnTrueIfUserHasCommercialAgreements`. More generally, `methodNameShouldDoSomethingIfSomeCondition`.

## Logging ##

- **Are exception stacktraces being logged?** – Outside of the other EDS logging standards, all exceptions should be logged to include the stacktrace, meaning the exception should be the second argument of any log method: `LOG.error(ex.getMessage(), ex)`
- **Prefer a string formatter to string concatenation** - this makes these strings a lot more readable. e.g. - `java.text.MessageFormat.format("param 1: {0}, param 2: {1}", param1, param2);`
- **General log levels** - `INFO` for general app information or customer data (REST request/response). `WARN` for errors that do not break the app. `ERROR` for all other errors.
- For more in-depth logging standards, see the [logging standards page](https://github.nwie.net/Nationwide/EDS-Apps/wiki/Logging-Standards).

## Libraries ##

- **If there are new libraries, why were they brought in?**
- **Was the version brought in compatible with the JDK version the app build with?**
- **Is there any library already in the project that provides the same functionality?** – this may be harder to tackle if you (the reviewer) are not familiar with all the dependencies being pulled in. The expectation is not that you’re familiar with every single one but to at least have an idea of a lot of the common libraries being pulled in and what they provide (e.g. – apache commons, struts, spring, Jackson/gson, guava)

## Constants ##

- **Is there a logical grouping of any new constants that should be Enums instead?** – constants files are not the best way to handle constant values, especially when there’s a logical grouping of limited values for a given concept. For example, there is a finite number of values for preference names used by PCAPI, so it’s better to encapsulate this in a PreferenceName enum than a list of constants in a Constants.java file.
- **Are constant values always on the left side of a .equals call?** – we covered this in our group code review, but to recap, this is an easy way to prevent NullPointerExceptions in that a constant can never be null, whereas a value from an end consumer or other calling class could be any value. Example: `“someValue”.equals(person.getValue())` will always resolve whereas `person.getValue().equals(“someValue”)` can fail if person is null. As of Java 8, `Object::equals` or `Object::isNull` are preferable, null-safe alternatives.

## Other ##

- **Folder Structure** – another rather personal opinion—when structuring a project, it’s easier to consume and support if related classes are grouped by business function rather than by IT function. When browsing a project, I have a much better idea what classes in the “registration” package are doing as opposed to classes in a “model” or ”services” package. This even applies to something like defect support: if login is broken, there’s a good chance it’s from a class in the “login” package, which can be a good starting place during debugging of issues.
- **Can classes > 500 lines be split?** – this number could be any sufficiently large value; the idea is that if it’s a huge class, it’s probably doing too much and breaking the “Single Responsibility” principle of clean coding.
- **Can methods > 50 lines be split?** – same as above.
- **Prefer streams over for loops** – streams are a design pattern type of solution for for loops and should be used when JDK8+ is available.
- **Are POJOs using the builder pattern** - this results is more readable code, and is really easy with the [Spark Builder Generator](https://github.nwie.net/Nationwide/EDS-Apps/wiki/Workspace-Setup#eclipse-plugins) Eclipse plugin.
- **Are any documentation updates needed?** - if there were any changes to project setup, or available resources of an app, there may need to be an update to the wiki/README/OAS of the app.