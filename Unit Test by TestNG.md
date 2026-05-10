
- **TestNG** is designed to cover all categories of tests: unit, functional, end-to-end, integration, etc.

* TestNG turns the normal java method into a test case using annotations `@Test`
- Method must be public
- Must return void
- No main() method needed
* ⚠️Never rely on method order unless explicitly specified


---

### NOTE : (ISOLATION)
Each test prepares and cleans its own data so that execution order does not affect results.

```
createUserTest → has its own user
deleteUserTest → has its own user
editUserTest → has its own user
```

# Testng.xml Additionally:
- CI/CD tools (Jenkins, GitHub Actions) use testng.xml
- Production frameworks always execute through XML
- Better for automation pipelines

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


# ✅ When to Use Which Assertion? (Real Industry Practice)
* ✔ Use Hard Assert when:
- Login must succeed
- Page must load
- Critical workflow validation

* ✔ Use Soft Assert when:
- Checking multiple UI elements
- Validating layout or content
- Non-blocking checks


- You don’t call listeners manually — TestNG triggers them internally.

### 🎯 Why Use Listeners?
* Listeners help you:
- ✔ Capture screenshots when test fails
- ✔ Create custom logs
- ✔ Build HTML reports
- ✔ Send email notifications
- ✔ Track execution status
> Instead of writing code inside every test, you centralize logic.


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






