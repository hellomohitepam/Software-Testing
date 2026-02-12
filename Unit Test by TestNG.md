# Introduction of TestNG

- **TestNG** is a test management framework inspired from **JUnit** and **NUnit** but introducing some new functionalities that make it more powerful and easier to use.

- **TestNG** is designed to cover all categories of tests: unit, functional, end-to-end, integration, etc.

---

# Advantages of TestNG
- Manages test suites and test cases
- Helps in prioritizing of tests
- Supports parallel execution, grouping, dependencies
- Better test configuration
- Supports annotations
- Reporting

---

* TestNG turns the normal java method into a test case using annotations `@Test`
- Method must be public
- Must return void
- No main() method needed
* ⚠️Never rely on method order unless explicitly specified

---

<img width="1222" height="673" alt="image" src="https://github.com/user-attachments/assets/d6bbc3da-fbf7-4681-91f9-ed34316ccd27" />


```java
import org.testng.annotations.Test;
import org.testng.annotations.BeforeMethod;
import org.testng.annotations.AfterMethod;

public class BeforeAfterExample {

    @BeforeClass
    public void setup() {
        System.out.println("Login to application");
    }
    @BeforeMethod
    public void print() {
        System.out.println("New Test going to happen");
    }

    @Test
    public void addItemTest() {
        System.out.println("Add item test");
    }

    @Test
    public void removeItemTest() {
        System.out.println("Remove item test");
    }

    @AfterMethod
    public void teardown() {
        System.out.println("Logout from application");
    }
}
```
```
For addItemTest
Login to application
Add item test
Logout from application

For removeItemTest
Login to application
Remove item test
Logout from application
```

* Run Once for each test method `@BeforeMethod → @Test → @AfterMethod`
* `@BeforeClass` Runs only once before all tests in the class.
* `@AfterClass` Runs only once after all tests in the class.

---

### NOTE : (ISOLATION)
Each test prepares and cleans its own data so that execution order does not affect results.

`createUserTest → has its own user
deleteUserTest → has its own user
editUserTest → has its own user
`

---

### What is priority?
priority is an attribute of @Test used to control the order of test execution (Default priority = 0).

`@Test(priority = 1)`
- 1️⃣ Lower value runs first
- 2️⃣ Same priority → alphabetical order
- 3️⃣ No priority mentioned = priority 0

NOTE: ❌ Do NOT use priority to handle test dependencies because If one fails, others will still run.

----

## Enabling & Disabling Tests
`@Test(enabled = false)`

* Why do we need this?
- Skip unstable tests
- Ignore work-in-progress tests
- Temporarily disable tests without deleting code

---

## dependsOnMethods
- Run this test only if another test passes.
- `@Test(dependsOnMethods = "loginTest")`

### 🔥 Important Difference
- Priority controls order.
- Dependency controls execution logic.

---

## What Are Groups?
Groups allow you to categorize tests so you can run selected tests instead of all tests.

## What is testng.xml?
It is a configuration file that:

- Controls which classes to run
- Controls which groups to include/exclude
- Controls parallel execution
- Controls test suites



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

