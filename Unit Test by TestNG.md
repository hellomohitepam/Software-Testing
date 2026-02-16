# Introduction of TestNG

- **TestNG** is a test management framework inspired from **JUnit** and **NUnit** but introducing some new functionalities that make it more powerful and easier to use.
- **TestNG** is designed to cover all categories of tests: unit, functional, end-to-end, integration, etc.
- `https://chatgpt.com/c/698b2e92-17e4-8321-9cd0-6915bf34b819`
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
### TestNG execution flow:
- ✅ @BeforeSuite – Runs once before the entire test suite starts.
- ✅ @BeforeTest – Runs before <test> tag execution in testng.xml.
- ✅ @BeforeClass – Runs once before the first test method in a class.
- ✅ @BeforeMethod – Runs before every @Test method.
- ✅ @Test – Actual test case execution.
- ✅ @AfterMethod – Runs after every @Test method.
- ✅ @AfterClass – Runs once after all test methods in a class.
- ✅ @AfterTest – Runs after <test> tag execution finishes.
- ✅ @AfterSuite – Runs once after the entire test suite ends.


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

### Enforce Execution Limits — timeOut
```java
@Test(timeOut = 10000)
public void youtubeSearch() {
    driver.get("https://www.youtube.com");
}
// If page load > 10 seconds → FAIL.
```

---

## dependsOnMethods
- Run this test only if another test passes else Skip.
- `@Test(dependsOnMethods = "loginTest")`

### 🔥 Important Difference
- Priority controls order.
- Dependency controls execution logic.
> Dependency overrides priority.
---

## What Are Groups?
Groups allow you to categorize tests so you can run selected tests instead of all tests.

`@Test(groups = {"smoke", "regression"})`

## dependsOnGroups
- Test method will run only after all tests in a specific group finish successfully else skip.
- `@Test(dependsOnGroups = "smoke")`

---

## What is testng.xml? (Test execution controller 🎛️)
It is a configuration file that:

- Controls which classes to run
- Controls which groups to include/exclude
- Controls parallel execution  -------------------------------------------------------------------?
- Controls test suites

### Additionally:
- CI/CD tools (Jenkins, GitHub Actions) use testng.xml
- Production frameworks always execute through XML
- Better for automation pipelines

---

`
<!DOCTYPE suite SYSTEM "https://testng.org/testng-1.0.dtd">
<suite name="Test Suite">

    <test name="Smoke Tests">
        <groups>
            <run>
                <include name="smoke"/>
            </run>
        </groups>

        <classes>
            <class name="com.tests.LoginTest"/>
            <class name="com.tests.CartTest"/>
        </classes>

    </test>

</suite>
`

## DataProvider
- **DataProviders** are used for data-driven testing, which means the same test case can be run with a different set of data.
- - Apart from **Parameters**, there is another way to achieve parameterization which is by using **DataProvider** in TestNG.
### It allows us to:
- Pass multiple sets of data
- Run the same test multiple times
- Avoid duplicate test methods

DataProvider does NOT create one big test instead of Multiple independent executions of the same test method.

``` java
@DataProvider(name = "loginData")
public Object[][] getData() {
    return new Object[][] {
        {"admin", "1234"},
        {"user1", "abcd"},
        {"guest", "xyz"}
    };
}

@Test(dataProvider = "loginData")
public void loginTest(String username, String password) {
    driver.findElement(By.id("username")).sendKeys(username);
    driver.findElement(By.id("password")).sendKeys(password);
    driver.findElement(By.id("loginBtn")).click();
}

// So internally, TestNG creates something like:
//loginTest("admin", "1234")
//loginTest("wrongUser", "wrongPass")
//loginTest("user1", "abcd")
```

`@DataProvider(name = "loginData", parallel = true)`
- 👉 Each data row iteration can run in parallel (in separate threads).

## ✅ XML vs Programmatic Data Approaches
| Feature                       | **XML Data Approach**                      | **Programmatic Data Approach**                                         |
| ----------------------------- | ------------------------------------------ | ---------------------------------------------------------------------- |
| **Definition**                | Test data passed through `testng.xml` file | Test data created inside Java code (DataProvider, loops, arrays, etc.) |
| **Where data is stored**      | External XML file                          | Inside test class or utility class                                     |
| **Flexibility**               | Good for environment/config changes        | Very flexible for dynamic data generation                              |
| **Code modification needed?** | ❌ No code change required                | ✅ Need to update code                                                 |
| **Best use case**             | Passing parameters (URL, browser, env)     | Multiple test datasets (login data, search data)                       |
| **Maintenance**               | Easier for non-developers                  | Requires coding knowledge                                              |
| **Complex data handling**     | Limited                                    | Very powerful (read Excel, DB, API)                                    |
| **Execution control**         | Strong (suite/test/class level)            | Focused mainly on test data logic                                      |
| **Real-world usage**          | Suite configuration                        | Data-driven testing                                                    |

---

## Assertions
- Assertions in TestNG are used to verify expected vs actual results.
- 
* They check conditions like:
- Is the title correct?
- Is element displayed?
- Are two values equal?
> If the condition is false → TestNG throws AssertionError.

## Hard Assertions (Default Assertions)
- Hard assertions stop execution immediately when they fail.

### ✔ assertEquals() :
```java
String actualTitle = driver.getTitle();
Assert.assertEquals(actualTitle, "YouTube");
// If not equal → test stops right there.
```

### ✔ assertTrue() :
```java
// Checks boolean condition.
WebElement logo = driver.findElement(By.id("logo"));
Assert.assertTrue(logo.isDisplayed());
```
### ✔ assertFalse() :
```java
Assert.assertFalse(driver.findElements(By.id("error")).isEmpty());
```

### ✔ assertNotEquals()
```java
Assert.assertNotEquals(actualTitle, "Google");
```

## Soft Assertions (Multiple Validations)
- Soft assertions allow multiple validations even if one fails.

```java
SoftAssert soft = new SoftAssert();

soft.assertEquals(driver.getTitle(), "YouTube");
soft.assertTrue(driver.findElement(By.id("logo")).isDisplayed());

soft.assertAll(); // VERY IMPORTANT
```
### Why assertAll() is required?
- It collects all failures and reports them at the end.
- Without it → test may PASS even if validations fail ❌

## ✅ When to Use Which? (Real Industry Practice)
* ✔ Use Hard Assert when:
- Login must succeed
- Page must load
- Critical workflow validation

* ✔ Use Soft Assert when:
- Checking multiple UI elements
- Validating layout or content
- Non-blocking checks

## ✅ What are TestNG Listeners?
- A Listener is a special interface that “listens” to test execution events and runs code automatically when something happens.

### Example events:
- Test starts
- Test passes
- Test fails
- Suite begins
- Suite ends
> You don’t call listeners manually — TestNG triggers them internally.

### 🎯 Why Use Listeners?
* Listeners help you:
- ✔ Capture screenshots when test fails
- ✔ Create custom logs
- ✔ Build HTML reports
- ✔ Send email notifications
- ✔ Track execution status
> Instead of writing code inside every test, you centralize logic.

### ✅ ITestListener — Most Common Listener

```java
public class MyListener implements ITestListener {
}
```
> Then override methods you need.

## 🔥 Important ITestListener Methods (In Depth)

* 🟢 onStart() - Runs when test execution starts.
- Initialize report
- Open log file

* 🟢 onTestStart() - Runs before each test method.
- Logging test start
- Start timer

---

* 🟢 onTestSuccess() -Runs when test passes.
- Add entry in report
- Mark test status

---

* 🔴 onTestFailure() - Runs when test fails.
- Take screenshot
- Attach logs
- Add failure message

* 🟡 onTestSkipped() - Runs when test is skipped (dependency failure).

---

🔵 onFinish() - Runs after all tests complete.
- Close report
- Generate summary

```java
import org.testng.ITestListener;
import org.testng.ITestResult;
import org.testng.ITestContext;

public class CustomListener implements ITestListener {

    public void onStart(ITestContext context) {
        System.out.println("Suite Started");
    }

    public void onTestStart(ITestResult result) {
        System.out.println("Test Started: " + result.getName());
    }

    public void onTestSuccess(ITestResult result) {
        System.out.println("Test Passed: " + result.getName());
    }

    public void onTestFailure(ITestResult result) {
        System.out.println("Test Failed: " + result.getName());
    }

    public void onFinish(ITestContext context) {
        System.out.println("Suite Finished");
    }
}
```

## ✅ How to Attach Listener
### Method 1 — Annotation (Easy)
```java
@Listeners(CustomListener.class)
public class YoutubeTest {
}
```
### Method 2 — testng.xml
```java
<listeners>
   <listener class-name="org.example.CustomListener"/>
</listeners>
```

```
onStart()
   ↓
onTestStart()
   ↓
@Test runs
   ↓
onTestSuccess() / onTestFailure()
   ↓
onFinish()

```






