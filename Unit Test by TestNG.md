# Introduction of TestNG

- **TestNG** is a testing framework inspired from **JUnit** and **NUnit** but introducing some new functionalities that make it more powerful and easier to use.

- **TestNG** is designed to cover all categories of tests: unit, functional, end-to-end, integration, etc.

# Advantages of TestNG

- Manages test suites and test cases
- Helps in prioritizing of tests
- Helps in grouping of tests
- Parallel execution
- Reporting

in testNG we do not have a main method

# Topics

- What is TestNG XML file? Usage.
- How to create TestNG XML?
- How to run tests from XML file
- TestNG Report

# Annotations in TestNG

- We can control the sequence and priority of the methods, which allows us to execute Java code before and after a certain point.
- Annotations are placed over the method with the symbol `@`.

```java
@Annotations
public void Test1() {
    // java code
}
```
<img width="1222" height="673" alt="image" src="https://github.com/user-attachments/assets/d6bbc3da-fbf7-4681-91f9-ed34316ccd27" />


# Topics

- Prioritizing Tests
- Disabling Tests
- Dependency Tests in TestNG
- AlwaysRun property
- Grouping Tests
- Assertion in TestNG
- Assert.assertTrue() & Assert.assertFalse()
- Assert.assertEquals()
- Parameter in TestNG
- Data Provider

while automating you testcases you need to put verification point or check points
we can pass the parameter at suit level class level 


# Data Provider

- Apart from **Parameters**, there is another way to achieve parameterization which is by using **DataProvider** in TestNG.

- **DataProviders** are used for data-driven testing, which means the same test case can be run with a different set of data. It is a very powerful feature of TestNG and is effectively used during framework development. There are a few points you should know about DataProvider:

- It marks methods for supplying the data to other methods.

- Annotated methods return an array of Object, i.e. `Object[][]`.

- DataProvider can have a name, and it will be used in other methods by using its name.

- DataProvider can be implemented in the same class or a different class.

- A Data Provider is a method annotated with `@DataProvider`.

