# Hello world! iOS 📱

## Your first Test

```java
import org.testng.Assert;
import org.testng.annotations.Test;
import pages.testapp.home.HomePage;

public class IOSTest extends BaseTest {
    @Test
    public void addNumbers() {
        String actualSum = new HomePage(this.driver)
                .enterTwoNumbersAndCompute("5", "5")
                .getSum();

        Assert.assertEquals(actualSum, "10");
    }
}
```

## Page object

```java
package pages.testapp.home;

import core.page.BasePage;
import io.appium.java_client.AppiumDriver;
import org.openqa.selenium.By;
import org.openqa.selenium.WebElement;
import org.openqa.selenium.support.FindBy;
import org.openqa.selenium.support.PageFactory;

public class HomePage extends BasePage {

    @FindBy(name = "TextField1")
    private WebElement firstNumber;

    @FindBy(name = "TextField2")
    private WebElement secondNumber;

    @FindBy(name = "ComputeSumButton")
    private WebElement computeSumButton;

    @FindBy(name = "Answer")
    private WebElement answer;

    public HomePage(AppiumDriver driver) {
        super(driver);
        PageFactory.initElements(driver, this);
    }

    public HomePage typeFirstNumber(String number) {
        type(firstNumber, number);
        return this;
    }

    public HomePage typeSecondNumber(String number) {
        type(secondNumber, number);
        return this;
    }

    public HomePage compute() {
        click(computeSumButton);
        return this;
    }

    public String getSum() {
        waitForElementToBePresent(By.name("Answer"));
        return getText(answer);
    }

    public HomePage enterTwoNumbersAndCompute(String first, String second) {
        typeFirstNumber(first);
        typeSecondNumber(second);
        compute();
        return this;
    }
}
```
