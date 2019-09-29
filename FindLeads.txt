package week2.day2.HomeWork;
import java.util.concurrent.TimeUnit;

import org.openqa.selenium.Keys;
import org.openqa.selenium.WebElement;
import org.openqa.selenium.chrome.ChromeDriver;
import org.openqa.selenium.support.ui.Select;


public class FindLeads{

	/**
	 * @param args
	 * @throws InterruptedException
	 */
	public static void main(String[] args) throws InterruptedException {
		// TODO Auto-generated method stub
		
		System.setProperty("webdriver.chrome.driver", "./drivers/chromedriver.exe");
		
		ChromeDriver driver = new ChromeDriver();
		
		driver.get("http://leaftaps.com/opentaps");
		driver.manage().window().maximize();
		driver.manage().timeouts().implicitlyWait(30, TimeUnit.SECONDS);
		
		WebElement username = driver.findElementById("username");
		username.sendKeys("DemoSalesManager");
		driver.findElementById("password").sendKeys("crmsfa", Keys.ENTER);
		driver.findElementByLinkText("CRM/SFA").click();
		driver.findElementByXPath("//a[text()='Leads']").click();
		driver.findElementByLinkText("Find Leads").click();
		driver.findElementByXPath("(//input[@name='firstName'])[3]").sendKeys("Vignesh");
		driver.findElementByXPath("//button[text()='Find Leads']").click();
		Thread.sleep(3000);
		driver.findElementByXPath("(//div[@class='x-grid3-cell-inner x-grid3-col-firstName']//a)[1]").click();
		
		String title = driver.getTitle();
		System.out.println("Text is:" + title);
		
		if(title.contains("View Lead | opentaps CRM")) {
			System.out.println("Title is valid");
		}
			else {
				System.out.println("First Name is not valid");
			
	}
		
		driver.findElementByLinkText("Edit").click();
		driver.findElementById("updateLeadForm_companyName").clear();
		driver.findElementById("updateLeadForm_companyName").sendKeys("CompanyNameChanged");
		driver.findElementByXPath("(//input[@name='submitButton'])[1]").click();
		
			
		WebElement element = driver.findElementById("viewLead_companyName_sp");
		String text=element.getText();

		System.out.println("Text is:" + text);
		
		if(text.contains("CompanyNameChanged")) {
			System.out.println("Update successfull");
		}
			else {
				System.out.println("Update unsuccessfull");
			}
		
		driver.close();
		
	}
}


