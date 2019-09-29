package week2.day2.HomeWork;
import java.util.List;

import org.openqa.selenium.Keys;
import org.openqa.selenium.WebElement;
import org.openqa.selenium.chrome.ChromeDriver;


public class DeleteLead{

	public static void main(String[] args) throws InterruptedException {
		// TODO Auto-generated method stub
		
		System.setProperty("webdriver.chrome.driver", "./drivers/chromedriver.exe");
		
		ChromeDriver driver = new ChromeDriver();
		
		driver.get("http://leaftaps.com/opentaps");
		driver.manage().window().maximize();
		
		WebElement username = driver.findElementById("username");
		username.sendKeys("DemoSalesManager");
		driver.findElementById("password").sendKeys("crmsfa", Keys.ENTER);
		driver.findElementByLinkText("CRM/SFA").click();
		driver.findElementByXPath("//a[text()='Leads']").click();
		driver.findElementByLinkText("Create Lead").click();
		driver.findElementByXPath("//a[text()='Find Leads']").click();
		driver.findElementByXPath("(//ul[@class='shortcuts']//a)[3]").click();
		driver.findElementByXPath("//span[text()='Phone']").click();
		driver.findElementByXPath("//input[@name='phoneNumber']").sendKeys("12", Keys.TAB);
		driver.findElementByXPath("//button[text()='Find Leads']").click();
		Thread.sleep(3000);
		
		WebElement leadid = driver.findElementByXPath("(//a[@class='linktext'])[4]");
		String text=leadid.getText();
		
		driver.findElementByXPath("(//div[@class='x-grid3-cell-inner x-grid3-col-partyId']//a)[1]").click();
		driver.findElementByClassName("subMenuButtonDangerous").click();
		driver.findElementByXPath("(//ul[@class='shortcuts']//a)[3]").click();
		driver.findElementByXPath("(//label[text()='Lead ID:']/following::input)[1]").sendKeys(text);
		
		driver.findElementByXPath("//button[text()='Find Leads']").click();
		
		List<WebElement> rows = driver.findElementsByXPath("//table[@class='x-grid3-header-offset']//td/parent::tr");
//		System.out.println(rows.size());
		if(rows.size() == 0) {
			System.out.println("No records to display in the Lead List");
		}
			else {
				System.out.println("First Name is not valid");
			}
		
		
		
		
		
		
	}

}
