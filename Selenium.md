# Introduction of Selenium

Selenium is an automation tool used to control a web browser (Chrome, Firefox, Edge) and simulate real user actions like:

- Opening a website
- Clicking buttons
- Typing text
- Submitting forms

## WebDriver is the core interface that allows you to automate web browsers directly by controlling them the same way a real user would.
- Talks to the browser
- Sends commands (open URL, click, type)
- Receives responses

## Key points about WebDriver
- It communicates directly with the browser, not through JavaScript (unlike Selenium RC)
- Supports multiple browsers
- Works with many languages (Java, Python, C#, JavaScript, etc.)
- Follows the W3C WebDriver standard

`
Think of it as:
  Selenium = brain
  WebDriver = hands controlling the browser 🖱️
`

```java
public class SeleniumWithTestNG {

    // we never open & close the browser inside the test method.
    WebDriver driver;       // WebDriver is an interface

    @BeforeMethod
    public void setup() {
        driver = new ChromeDriver();
        driver.get("https://www.google.com");
    }

    @Test
    public void searchTest() {
        driver.findElement(By.name("q")).sendKeys("Selenium");
    }

    @AfterMethod
    public void teardown() {
        driver.quit();     //Closes all browser windows & Ends WebDriver session.
    }
}
```
## Locating Elements

`findElement()` is used to locate a web element (textbox, button, link) on a web page.

`driver.findElement(By.locatorType("value"));`

| Locator | Example                           |
| ------- | --------------------------------- |
| id      | `By.id("username")`               |
| name    | `By.name("email")`                |
| xpath   | `By.xpath("//input[@id='user']")` |

### 👉 Best practice:
- id > name > className > xpath
- Locate → Act

`Keys.ENTER` simulates pressing the Enter key on the keyboard, also faster and Useful when button is hidden or dynamic.

### 🔹 Why Do We Need Waits?
- Web pages load dynamically
- Elements may not be available immediately `NoSuchElementException`
- Selenium is faster than the browser

### Types of Waits
- 1️⃣ Implicit Wait (easy, global) : Wait for a certain time before throwing an error if element is not found.

`driver.manage().timeouts().implicitlyWait(Duration.ofSeconds(10));`
- If element appears in 2 seconds → continues immediately
- Applied to all findElement calls

- 2️⃣ Explicit Wait (recommended, advanced) : waits for a specific condition to be met for a specific element.

### Unlike implicit wait:
- It is not global
- It waits only where you tell it to wait

## 🔹 Why Explicit Wait is Better?

Because sometimes:

- Element is present but not clickable
- Element is visible but not interactable
- Page loads partially

## Implicit wait only waits for:
- ✔ Element to be present in the DOM

## Explicit wait can wait for: (a SPECIFIC CONDITION you define)
- ✔ Visibility       `ExpectedConditions.visibilityOfElementLocated(By.id("loginBtn"))`
- ✔ Clickable        `ExpectedConditions.elementToBeClickable(By.id("loginBtn"))`
- ✔ Text to appear   `ExpectedConditions.textToBePresentInElementLocated(By.id("status"),"Success")`
- ✔ Alert to appear  `ExpectedConditions.alertIsPresent()`
- ✔ URL change       `ExpectedConditions.urlContains("dashboard")`

`
WebDriverWait wait = new WebDriverWait(driver, Duration.ofSeconds(10));
wait.until(ExpectedConditions.visibilityOfElementLocated(By.id("username")));
`























