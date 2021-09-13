# Hello world! Android

## Sample apps

We'll use `APIDemos` app from appium, download the apk from below

- [Sample apps](https://github.com/appium/appium/tree/master/sample-code/apps)

## Overall flow

![Appium Test flow](images/appium-test-flow.png)

## Your first test

This test performs below:

- Opens app
- Opens Log Text box and taps on Add once
- Verifies the log text is displayed

```java
public class AndroidTest extends BaseTest {
    @Test
    public void testLogText() {
        String logText = new APIDemosHomePage(this.driver)
                .openText()
                .tapOnLogTextBox()
                .tapOnAddButton()
                .getLogText();

        Assert.assertEquals(logText, "This is a test");
    }
}
```

## Driver setup in Base Test

We spin up driver instance in `BaseTest` class

```java
public class BaseTest {
    protected AppiumDriver driver;
    protected PropertiesReader reader = new PropertiesReader();

    @BeforeMethod
    public void setup(ITestContext context) {
        context.setAttribute("platform", reader.getPlatform());

        try {
            Platform platform = (Platform) context.getAttribute("platform");
            this.driver = new DriverManager().getInstance(platform);
        } catch (IOException | PlatformNotSupportException e) {
            e.printStackTrace();
        }
    }

    @AfterMethod
    public void teardown() {
        driver.quit();
    }
}
```

## Driver manager to setup Appium Driver

We use this reusable class to:

- Read capabilities JSON file based on platform
- Setup a local driver instance with these capabilities
- This class could independently evolve to setup desired driver instances, either local, in house or
  remote cloud lab

```java
public class DriverManager {
    private static AppiumDriver driver;
    String APPIUM_SERVER_URL = "http://127.0.0.1:4723/wd/hub";

    public AppiumDriver getInstance(Platform platform) throws IOException, PlatformNotSupportException {
        switch (platform) {
            case ANDROID:
                return getAndroidDriver();
            case IOS:
                return getIOSDriver();
            default:
                throw new PlatformNotSupportException("Please provide supported platform");
        }
    }

    private AppiumDriver getAndroidDriver() throws IOException {
        HashMap map = readAndMakeCapabilities("android-caps.json");
        return getDriver(map);
    }

    private AppiumDriver getIOSDriver() throws IOException {
        HashMap map = readAndMakeCapabilities("ios-caps.json");
        return getDriver(map);
    }

    private AppiumDriver getDriver(HashMap map) {
        DesiredCapabilities desiredCapabilities = new DesiredCapabilities(map);

        try {
            driver = new AppiumDriver(
                    new URL(APPIUM_SERVER_URL), desiredCapabilities);
        } catch (MalformedURLException e) {
            e.printStackTrace();
        }

        return driver;
    }
}
```

## A Simple page object with Fluent pattern

Below is an example page object class

- With 2 xpath locators annotated with `@FindBy`
- Notice we init elements in the constructor and also a BasePage class
- The test actions return either `this` or `next page object` to enable a fluent pattern

```java
public class APIDemosHomePage extends BasePage {

    @FindBy(xpath = "//android.widget.TextView[@content-desc=\"Text\"]")
    private WebElement textButton;

    @FindBy(xpath = "//android.widget.TextView[@content-desc=\"LogTextBox\"]")
    private WebElement logTextBoxButton;

    public APIDemosHomePage(AppiumDriver driver) {
        super(driver);
        PageFactory.initElements(driver, this);
    }

    public APIDemosHomePage openText() {
        click(textButton);
        return this;
    }

    public LogTextBoxPage tapOnLogTextBox() {
        waitForElementToBeVisible(logTextBoxButton);
        click(logTextBoxButton);

        return new LogTextBoxPage(driver);
    }
}
```

## Base Page (Initial)

Every page object inherits from a `BasePage` that wraps appium methods

> - This provides us an abstraction and allows us to create our own project specific reusable
>   actions and methods
> - A word of Caution ⚠️: Do not dump every method in this class, try to compose only relevant
>   actions

```java
public class BasePage {
    protected AppiumDriver driver;

    public BasePage(AppiumDriver driver) {
        this.driver = driver;
    }

    public void click(WebElement elem) {
        elem.click();
    }

    public String getText(WebElement elem) {
        return elem.getText();
    }

    public void waitForElementToBeVisible(WebElement elem) {
        WebDriverWait wait = new WebDriverWait(driver, 10);
        wait.until(ExpectedConditions.visibilityOf(elem));
    }
}
```
