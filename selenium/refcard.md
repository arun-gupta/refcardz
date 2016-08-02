# What Is Selenium?

[Selenium](http://seleniumhq.org) is a free and open-source browser automation library used by millions of people for testing purposes as well as automation of repetitive web-based administrative tasks. It has the support of the largest browser vendors who have taken (or are currently taking) steps to make Selenium a native part of their browser. It is also the core technology in countless other browser automation tools, APIs and frameworks.

It is effectively the de facto standard for automating web browsers. WebDriver (the API to automate browsers, maintained by the Selenium project) is currently going through [a W3C (World Wide Web Consortium) specification](https://www.w3.org/TR/webdriver/). Once the specification becomes ratified, Selenium will become the official standard for automating web browsers.

# Getting Started

There are Selenium language bindings for multiple programming languages. The officially supported ones (in order of use) are:

- Java
- JavaScript
- Python
- Ruby
- C#

In order to start writing tests you, first need to install the bindings for your preferred programming language.

## Java (With Maven)

In your test project, add the following to your `pom.xml`. Once done, you can either let your IDE (Integrated Development Environment) use Maven to import the dependencies or open a command-prompt, `cd` into the project directory, and run `mvn clean test-compile`.

```java
<!-- https://mvnrepository.com/artifact/org.seleniumhq.selenium/selenium-java -->
<dependency>
    <groupId>org.seleniumhq.selenium</groupId>
    <artifactId>selenium-java</artifactId>
    <version>LATEST</version>
    <scope>test</scope>
</dependency>
```

__Note:__ You will need to have [the Java Development Kit](http://www.oracle.com/technetwork/java/javase/downloads/index.html) (version 7+, or 8+ for 3.x versions of Selenium) and [Maven](https://maven.apache.org/) installed on your machine. For more information on the Selenium Java bindings, check out [the API documentation](http://seleniumhq.github.io/selenium/docs/api/java/index.html).

## JavaScript (npm)

Type the following command into a command-prompt to install the JavaScript bindings for Selenium.

```javascript
npm install selenium-webdriver
```

__Note:__ You will need to have [Node.js](https://nodejs.org) and [NPM](https://www.npmjs.org/) installed on your machine. For more information about the Selenium JavaScript bindings, check out [the API documentation](http://seleniumhq.github.io/selenium/docs/api/javascript/index.html).

## Python

Type the following command to install the Python bindings for Selenium.

```python
pip install selenium
```

__Note:__ You will need to [install Python](https://wiki.python.org/moin/BeginnersGuide/Download), [pip](https://pypi.python.org/pypi/pip/), and [setuptools](https://pypi.python.org/pypi/setuptools) in order for this to work properly. For more information on the Selenium Python bindings, check out [the API documentation](http://seleniumhq.github.io/selenium/docs/api/py/).

## Ruby

Type the following command to install the Selenium Ruby bindings.

```ruby
gem install selenium-webdriver
```

__Note:__ You will need to install a current version of Ruby which comes with RubyGems. You can find instructions for that on [the Ruby project website](https://www.ruby-lang.org/en/documentation/installation/). For more information on the Selenium Ruby bindings, check out [the API documentation](http://seleniumhq.github.io/selenium/docs/api/rb/).

## C# (With NuGet)

Use the following commands from [the Package Manager Console window](https://docs.nuget.org/consume/package-manager-console) in Visual Studio to install the Selenium C# bindings.

```csharp
Install-Package Selenium.WebDriver
Install-Package Selenium.Support
```

__Note:__ You will need to install [Microsoft Visual Studio](https://www.visualstudio.com/) and [NuGet](https://www.nuget.org/) to install these libraries and build your project. For more information on the Selenium C# bindings, check out [the API documentation](http://seleniumhq.github.io/selenium/docs/api/dotnet/).

__Note:__ The remaining examples will show Java demonstrations.

# Launching a Browser

With Selenium you have the ability to launch any major browser on any major operating system. Depending on the browser, there may be some configuration required in order to get it running locally.

## Firefox

FirefoxDriver comes built into the Selenium language bindings. It's a simple matter of requesting a new instance of it.

```java
WebDriver driver = new FirefoxDriver();
```

__Note:__ For more information about FirefoxDriver, check out [the Selenium project Wiki page for FirefoxDriver](https://github.com/SeleniumHQ/selenium/wiki/FirefoxDriver.

## Chrome

In order to use Chrome, you need to download [the ChromeDriver binary for your operating system](http://chromedriver.storage.googleapis.com/index.html) (pick the highest number for the latest version). You either need to add it to your System Path or specify its location as part of your test setup.

```java
System.setProperty("webdriver.chrome.driver", "/path/to/chromedriver");
driver = new ChromeDriver();
```

__Note:__ For more information about ChromeDriver, check out [the Selenium project Wiki page for ChromeDriver](https://github.com/SeleniumHQ/selenium/wiki/ChromeDriver.

## Internet Explorer

For Internet Explorer on Windows, you need to download [IEDriverServer.exe](http://selenium-release.storage.googleapis.com/index.html) (pick the highest number for the latest version) and either add it to your System Path or specify its location as part of your test setup.

```java
WebDriver driver = new InternetExplorerDriver("/path/to/IEDriverServer.exe");
```


__Note:__ As of July 19, 2016 Internet Explorer 8 and older are no longer supported by the Selenium project. Also, if you're trying to run Windows 11, then you will need to add a registry key to your system. For more information about this and other InternetExplorerDriver details, check out [the Selenium project Wiki page for InternetExplorerDriver](https://github.com/SeleniumHQ/selenium/wiki/InternetExplorerDriver).

## Edge

In order to use Microsoft Edge, you need to have access to Windows 10. You can download a free virtual machine with it from Microsoft for testing purposes from [Microsoft's Modern.IE developer portal](https://developer.microsoft.com/en-us/microsoft-edge/tools/vms/). After that, you need to download the appropriate `Microsoft WebDriver` server for your build of Windows. To find that, go to `Start` > `Settings` > `System` > `About` and locate the number next to `OS Build` on the screen. Then it's just a simple matter of requesting a new instance of Edge.

```java
WebDriver driver = new EdgeDriver();
```

__Note:__ Currently Edge is only supported in the C#, Java, and JavaScript bindings. For more information about EdgeDriver, check out [the main page on the Microsoft Developer portal](https://developer.microsoft.com/en-us/microsoft-edge/platform/documentation/dev-guide/tools/webdriver/) and [the download page for the EdgeDriver binary](https://developer.microsoft.com/en-us/microsoft-edge/tools/webdriver/).

## Safari

Safari on OS X works without having to download a browser driver. But you do need to download and install a SafariDriver browser extension which you can get from [this direct download link from the Selenium project](http://selenium-release.storage.googleapis.com/2.48/SafariDriver.safariextz).

```java
WebDriver driver = new SafariDriver();
```

__Note:__ There is no Selenium support for Safari on Windows. For more information about SafariDriver, check out [the Selenium project Wiki page for SafariDriver](https://github.com/SeleniumHQ/selenium/wiki/SafariDriver.

## Opera

Versions 15 and newer of Opera are built from the same rendering engine as Chrome. So if you run your tests with ChromeDriver then you are essentially testing Opera too.

There are some slight differences with it though. So if you have a business need to test with Opera, be sure to check out the [OperaChromiumDriver](https://github.com/operasoftware/operachromiumdriver) for current versions of Opera and the [OperaPrestoDriver](https://github.com/operasoftware/operaprestodriver) for older versions of Opera.

# Commands & Operations

The most common operations you'll end up doing in Selenium are navigating to a page and finding an element (or a set of elements). Once found, you can perform actions with those elements (e.g., click, type text, etc.), ask questions about them (e.g., is it clickable? is it displayed?), or pull information out of the element (e.g., the text of an element or the text of a specific attribute within an element).

## Visit a Page

```java
driver.get("http://the-internet.herokuapp.com");
```

## Find an Element

```java
// find just one, the first one Selenium finds
WebElement element = driver.findElement(locator);

// find all instances of the element on the page
List<WebElement> elements = driver.findElements(locator);
```

## Work With a Found Element

```java
// chain actions together
driver.findElement(locator).click();

// store the element and then click it
WebElement element = driver.findElement(locator);
element.click();
```

## Perform Multiple Commands

```java
element.click();                  // clicks an element
element.submit();                 // submits a form
element.clear();                  // clears an input field of its text
element.sendKeys("input text");   // types text into an input field
```

## Ask a Question

Each of these returns a Boolean.

```java
element.isDisplayed();    // is it visible to the human eye?
element.isEnabled();      // can it be selected?
element.isSelected();     // is it selected?
```

## Retrieve Information

Each of these returns a String.

```java
// directly from an element
element.getText();

// by attribute name
element.getAttribute("href");
```

__Note:__ For more information about working with elements, check out [the Selenium WebElement API Documentation](https://seleniumhq.github.io/selenium/docs/api/java/org/openqa/selenium/WebElement.html.

## Complex User Gestures

Selenium's Actions Builder enables more complex keyboard and mouse interactions. Things like drag-and-drop, click-and-hold, double-click, right-click, hover, etc.

```java
// a hover example
WebElement avatar = driver.findElement(By.name("target"));
(new Actions(driver)).moveToElement(avatar).build().perform();
```

__Note:__ For more details about the Action Builder, check out [the Actions API documentation](http://seleniumhq.github.io/selenium/docs/api/java/org/openqa/selenium/interactions/Actions.html).

# Locators

In order to find an element on the page, you need to specify a locator. There are several locator strategies supported by Selenium (listed alphabetically):

| By Locator        | Example (Java)                                              |
| -----------------:| :-----------------------------------------------------------|
| Class             | `driver.findElement(By.className("dues"));`                 |
| CSS Selector      | `driver.findElement(By.cssSelector(".flash.success"));`     |
| ID                | `driver.findElement(By.id("username"));`                    |
| Link Text         | `driver.findElement(By.linkText("Link Text"));`             |
| Name              | `driver.findElement(By.name("elementName"));`               |
| Partial Link Text | `driver.findElement(By.partialLinkText("nk Text"));`        |
| Tag Name          | `driver.findElement(By.tagName("td"));`                     |
| XPath             | `driver.findElement(By.xpath("//input[@id='username']"));`  |

__Note:__ Good locators are unique, descriptive, and unlikely to change. So it's best to start with ID and Class locators. These are the most performant locators available and the most likely ones to be helpfully named. If you need to access something that doesn't have a helpful ID or Class, then use CSS selectors or XPath. But be careful when using these approaches, since you can write very brittle locators that will not perform well. Alternatively, talk with a developer on your team when the app is hard to automate. Tell them what you're trying to automate and work with them to get more semantic markup added to the page. This will make the application more testable and make your tests far easier to write and maintain.

## CSS Selectors

| Approach          | Locator                                  | Description                                   |
| -----------------:| :-------------                           | :--------------                               |
| ID                | `#example`                               | `#` denotes an ID                             |
| Class             | `.example`                               | `.` denotes a Class                           |
| Classes           | `.flash.success`                         | use `.` in front of each class for multiple   |
| Direct child      | `div > a`                                | finds the element in the next child           |
| Child/subschild   | `div a`                                  | finds the element in a child or child's child |
| Next sibling      | `input.username + input`                 | finds the next adjacent element               |
| Attribute values  | `form input[name='username']`            | a great alternative to id and class matches   |
| Attribute values  | `input[name='continue'][type='button']`  | can chain multiple attribute filters together |
| Location          | `li:nth-child(4)`                        | finds the 4th element only if it is an li     |
| Location          | `li:nth-of-type(4)`                      | finds the 4th li in a list                    |
| Location          | `*:nth-child(4)`                         | finds the 4th element regardless of type      |
| Sub-string        | `a[id^='beginning_']`                    | finds a match that starts with (prefix)       |
| Sub-string        | `a[id$='_end']`                          | finds a match that ends with (suffix)         |
| Sub-string        | `a[id*='gooey_center']`                  | finds a match that contains (substring)       |
| Inner text        | `a:contains('Log Out')`                  | an alternative to substring matching          |

__Note:__ Older browsers (e.g. Internet Explorer 8) don't support CSS Pseudo-classes, so some of these locator approaches won't work on them (e.g., Location matches and Inner text matches).

For more info see one of the following resources:

+ [CSS Selectors Reference](https://www.w3.org/TR/CSS/#selectors)
+ [XPath Syntax Reference](https://www.w3.org/TR/xpath/#location-paths)
+ [CSS & XPath Examples by Sauce Labs](http://bit.ly/cssxpathexamples)
+ [CSS vs. XPath Selenium benchmarks](http://bit.ly/seleniumbenchmarks)
+ [The difference between nth-child and nth-of-type](http://css-tricks.com/the-difference-between-nth-child-and-nth-of-type/)
+ [How To Verify Your Locators](http://se.tips/verifyinglocators)
+ [CSS Selector Game](http://bit.ly/locatorgame)


# An Example Test

To tie all of these concepts together, here is a simple test that demonstrates using Selenium to exercise common functionality (e.g. login) by launching a browser, visiting the target page, interacting with the necessary elements, and verifying the page is in the correct place.

```java
import org.junit.Test;
import org.junit.Before;
import org.junit.After;
import static org.junit.Assert.*;
import org.openqa.selenium.By;
import org.openqa.selenium.WebDriver;
import org.openqa.selenium.firefox.FirefoxDriver;

public class TestLogin {

    private WebDriver driver;

    @Before
    public void setUp() {
        driver = new FirefoxDriver();
    }

    @After
    public void tearDown() {
        driver.quit();
    }

    @Test
    public void succeeded() {
        driver.get("http://the-internet.herokuapp.com/login");
        driver.findElement(By.id("username")).sendKeys("tomsmith");
        driver.findElement(By.id("password")).sendKeys("SuperSecretPassword!");
        driver.findElement(By.cssSelector("button")).click();
        assertTrue("success message not present",
                driver.findElement(By.cssSelector(".flash.success")).isDisplayed());
    }

}
```

# Page Objects

Rather than write your test code directly against your application, you can model the behavior of it into simple objects and write your tests against them instead. That way, when your application changes and your tests break, you only have to update your test code in one place to fix it. With this approach we not only get the benefit of controlled chaos, but we also get reusable functionality across our suite of tests and more readable tests.

Let's create a page object for the login example shown before and update the test from before to use it.

```java
// import statements omitted for brevity
public class Login {

    private WebDriver driver;
    By loginFormLocator = By.id("login");
    By usernameLocator  = By.id("username");
    By passwordLocator  = By.id("password");
    By submitButton     = By.cssSelector("button");
    By successMessageLocator = By.cssSelector(".flash.success");

    public Login(WebDriver driver) {
        this.driver = driver;
        driver.get("http://the-internet.herokuapp.com/login");
        assertTrue("The login form is not present",
                driver.findElement(loginFormLocator).isDisplayed());
    }

    public void with(String username, String password) {
        driver.findElement(usernameLocator).sendKeys(username);
        driver.findElement(passwordLocator).sendKeys(password);
        driver.findElement(submitButton).click();
    }

    public Boolean successMessagePresent() {
        return driver.findElement(successMessageLocator).isDisplayed();
    }

}
```

By storing the page's locators and behavior in a central place, we are able to easily reuse it in multiple tests and extend it for future use cases. This also enables us to pull all of our Selenium commands and locators out of our tests, making our tests more concise and easier to construct. We also have the advantage of doing additional things like verifying that the page is in a ready state before letting the test proceed (e.g., like we're doing in the constructor by asserting that the login form is present).

```java
// import statements omitted for brevity
public class TestLogin {

    private WebDriver driver;
    private Login login;

    @Before
    public void setUp() {
        driver = new FirefoxDriver();
        login = new Login(driver);
    }

    @After
    public void tearDown() {
        driver.quit();
    }

    @Test
    public void succeeded() {
        login.with("tomsmith", "SuperSecretPassword!");
        assertTrue("success message not present",
                login.successMessagePresent());
    }

}
```

Page objects should always return some piece of information (e.g., a predicate method like the one used in this example, or a new page object that represents the page the login took you to). How you write your Page Objects may vary depending on your preference/experience. The example demonstrated above is a simple approach. Here are some additional resources to consider as your usage of Page Objects grows:

+ [Page Objects documentation from the Selenium project](https://github.com/SeleniumHQ/selenium/wiki/PageObjects)
+ [Page Factory](https://github.com/SeleniumHQ/selenium/wiki/PageFactory) (a Page Object generator/helper built into Selenium)
+ [HTML Elements](https://github.com/yandex-qatools/htmlelements) (a simple open-source Page Object framework)

# Waiting

The notion of waiting for the page to finish loading is a thing of the past. In order to make your tests work in an asynchronous, JavaScript-heavy world, we need to tell Selenium how to wait for things intelligently. There are two types of function for this built into Selenium--implicit waits and explicit waits. The recommended approach from the Selenium project is to only use Explicit Waits.

## Implicit Waits

+ Only needs to be configured once at test setup
+ Tells Selenium to wait for a specified amount of time before raising an exception (typically a [`NoSuchElementException`](https://seleniumhq.github.io/selenium/docs/api/java/org/openqa/selenium/NoSuchElementException.html))
+ Less flexible than explicit waits
+ Known to cause transient test failures

```java
driver.manage().timeouts().implicitlyWait(5, TimeUnit.SECONDS);
```

__Note:__ This is not a recommended approach for waiting with Selenium. The recommended approach is to use Explicit Waits.

## Explicit Waits

+ Recommended approach to wait in your tests
+ Specify an amount of time and a Selenium action
+ Selenium will try that action repeatedly until either:
  + the action can be accomplished, or
  + the amount of time specified has been reached, throwing a [`TimeoutException`](https://seleniumhq.github.io/selenium/docs/api/java/org/openqa/selenium/TimeoutException.html)

```java
WebDriverWait wait = new WebDriverWait(driver, timeout);
wait.until(ExpectedConditions.visibilityOfElementLocated(locator));
```

__Note:__ For more info, check out [the case against using Implicit and Explicit Waits together](http://stackoverflow.com/questions/15164742/combining-implicit-wait-and-explicit-wait-together-results-in-unexpected-wait-ti#answer-15174978) and [Explicit vs. Implicit Waits](http://elementalselenium.com/tips/47-waiting).

# Screenshots on Failure

Selenium has the ability to take screenshots of the browser viewport window. The most common way to leverage this functionality is when there is a test failure. In JUnit, this is simple to accomplish with [a `TestWatcher` Rule](https://github.com/junit-team/junit4/wiki/Rules#testwatchmantestwatcher-rules).

```java
@Rule
public TestRule watcher = new TestWatcher() {
    @Override
    protected void failed(Throwable throwable, Description description) {
        File scrFile = ((TakesScreenshot)driver).getScreenshotAs(OutputType.FILE);
        try {
            FileUtils.copyFile(scrFile,
                    new File("failshot_"
                            + description.getClassName()
                            + "_" + description.getMethodName()
                            + ".png"));
        } catch (IOException exception) {
            exception.printStackTrace();
        }
    }
```

# Selenium Remote

In order to run your tests on a myriad of browser and operating system combinations, you need a way to run them at scale. With Selenium Remote, you can point your tests at a Selenium Grid that you maintain or someone else's Grid (e.g. Sauce Labs), which they maintain and you pay for usage.

## Selenium Grid

There are two main elements to Selenium Grid--a hub, and nodes. First you need to stand up a hub. Then you can connect (or "register") nodes to that hub. Nodes are where your tests will run, and the hub is responsible for making sure your tests end up on the right node (e.g., the machine with the operating system and browser you specified in your test setup).

Selenium Grid comes built into the Selenium Standalone Server, which you can download [here](http://selenium-release.storage.googleapis.com/index.html) (pick the highest number for the latest version).

Then start the hub.

```sh
> java -jar selenium-server-standalone.jar -role hub
19:05:12.718 INFO - Launching Selenium Grid hub
...
```

After that, we can register nodes to the hub.

```sh
> java -jar selenium-server-standalone.jar -role node -hub http://ip-address-or-dns-name-to-your-hub:4444/grid/register
19:05:57.880 INFO - Launching a Selenium Grid node
...
```

__Note:__ To span nodes across multiple machines, you will need to place the standalone server on each machine and launch it with the same registration command (providing the IP Address or DNS name of your hub, and specifying additional parameters as needed).

Then it is a simple matter of connecting to the Grid Hub in our test setup.

```java
DesiredCapabilities capabilities = DesiredCapabilities.firefox();
String url = "http://ip-address-or-dns-name-to-your-hub:4444/wd/hub";
driver = new RemoteWebDriver(new URL(url), capabilities);
```

__Note:__ Selenium Grid is a great option for scaling your test infrastructure, but it doesn't give you parallelization for free. It can handle as many connections as you throw at it (within reason), but you still need to find a way to execute your tests in parallel (with your test framework, for instance). Also, if you are considering standing up your own grid, be sure to check out [docker-selenium](https://github.com/seleniumhq/docker-selenium), [Selenium-Grid-Extras](https://github.com/groupon/Selenium-Grid-Extras), and [SeleniumGridScaler](https://github.com/mhardin/SeleniumGridScaler).

## Selenium Service Providers

Rather than take on the overhead of a standing up and maintaining a test infrastructure, you can easily outsource things to a third-party cloud provider (a.k.a. someone else's Grid) like [Sauce Labs](https://saucelabs.com/).

__Note:__ You'll need an account to use Sauce Labs. Their [free trial](https://saucelabs.com/signup/trial) offers enough to get you started. And if you're signing up because you want to test an open-source project, then be sure to check out their [Open Sauce account](https://saucelabs.com/opensauce).

```java
DesiredCapabilities capabilities = new DesiredCapabilities();
capabilities.setCapability("browserName", "firefox");
capabilities.setCapability("version", "33");
capabilities.setCapability("platform", "Windows XP");
String sauceUrl = String.format("http://%s:%s@ondemand.saucelabs.com:80/wd/hub",
        sauceUser, sauceKey);
driver = new RemoteWebDriver(new URL(sauceUrl), capabilities);
```

__Note:__ You can see a full list of Sauce Labs' available platform options [here](https://saucelabs.com/platforms/). There's also [a handy configuration generator](https://docs.saucelabs.com/reference/platforms-configurator/) that will tell you what values to plug into your test. Be sure to check out Sauce Labs' [documentation portal](https://wiki.saucelabs.com/) for more details.

# Mobile Support

Within the WebDriver ecosystem, there are a few mobile testing solutions for both iOS and Android, most notably:

+ [Appium](https://github.com/appium/appium) (both iOS and Android)
+ [Selendroid](https://github.com/selendroid/selendroid) (Android)
+ [WebDriverAgent](https://github.com/facebook/webdriveragent) (iOS)

__Note:__ If you're interested in Appium, then be sure to check out [the Appium Bootcamp](https://saucelabs.com/resources/articles/appium-bootcamp-chapter-1).