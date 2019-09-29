package week2.day2.HomeWork;
import java.util.concurrent.TimeUnit;

import org.openqa.selenium.Keys;
import org.openqa.selenium.WebElement;
import org.openqa.selenium.chrome.ChromeDriver;
import org.openqa.selenium.support.ui.Select;


public class CreateLead{

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
		driver.findElementByLinkText("Create Lead").click();
		driver.findElementById("createLeadForm_companyName").sendKeys("TestLeaf");
		driver.findElementById("createLeadForm_firstName").sendKeys("Vignesh");
		driver.findElementById("createLeadForm_lastName").sendKeys("G");
		driver.findElementById("createLeadForm_firstNameLocal").sendKeys("Test");
		driver.findElementById("createLeadForm_lastNameLocal").sendKeys("leaf");
		
		driver.findElementById("createLeadForm_personalTitle").sendKeys("Testing Salutation");
		driver.findElementById("createLeadForm_generalProfTitle").sendKeys("TSalutation");
		driver.findElementById("createLeadForm_departmentName").sendKeys("CSE");
		driver.findElementById("createLeadForm_annualRevenue").sendKeys("20Cr");
		
		WebElement Dropdown1 = driver.findElementById("createLeadForm_industryEnumId");
		Select dd = new Select(Dropdown1);
		dd.selectByVisibleText("Retail");
		
		WebElement Dropdown2 = driver.findElementById("createLeadForm_ownershipEnumId");
		Select dd2 = new Select(Dropdown2);
		dd2.selectByValue("OWN_SCORP");
		
		
		driver.findElementById("createLeadForm_sicCode").sendKeys("1235");
		driver.findElementById("createLeadForm_description").sendKeys("testing");
		driver.findElementById("createLeadForm_importantNote").sendKeys("Testing Note");
		driver.findElementById("createLeadForm_primaryPhoneCountryCode").clear();
		driver.findElementById("createLeadForm_primaryPhoneCountryCode").sendKeys("91");
		driver.findElementById("createLeadForm_primaryPhoneAreaCode").sendKeys("641016");
		driver.findElementById("createLeadForm_primaryPhoneExtension").sendKeys("0422");
		
		WebElement Dropdown3 = driver.findElementById("createLeadForm_currencyUomId");
		Select dd3 = new Select(Dropdown3);
		dd3.selectByValue("INR");
		
		driver.findElementById("createLeadForm_numberEmployees").sendKeys("120");
		driver.findElementById("createLeadForm_tickerSymbol").sendKeys("ticker");
		driver.findElementById("createLeadForm_primaryPhoneAskForName").sendKeys("Nill");
		driver.findElementById("createLeadForm_primaryWebUrl").sendKeys("http://leaftaps.com/opentaps");
		driver.findElementById("createLeadForm_generalToName").sendKeys("Vignesh");
		driver.findElementById("createLeadForm_generalCity").sendKeys("Chennai");
		driver.findElementById("createLeadForm_generalAddress1").sendKeys("Annai Street");
		driver.findElementById("createLeadForm_generalPostalCode").sendKeys("641016");
		driver.findElementById("createLeadForm_generalAttnName").sendKeys("AttName");
		driver.findElementById("createLeadForm_generalAddress2").sendKeys("new Street");
		
		WebElement Dropdown4 = driver.findElementById("createLeadForm_generalStateProvinceGeoId");
		Select dd4 = new Select(Dropdown4);
		dd4.selectByValue("NY");
		
//		driver.findElementById("createLeadForm_generalStateProvinceGeoId").clear();
//		WebElement Dropdown5 = driver.findElementById("createLeadForm_generalStateProvinceGeoId");
//		Select dd5 = new Select(Dropdown5);
//		dd5.selectByValue("USA");
		
		Thread.sleep(2000);
		driver.findElementByXPath("//input[@value='Create Lead']").click();
	
		WebElement element = driver.findElementById("viewLead_firstName_sp");
		String text=element.getText();

		System.out.println("Text obtained is" + text);
		
		if(text.contains("Vignesh")) {
			System.out.println("First Name is valid");
		}
			else {
				System.out.println("First Name is not valid");
			}
		}
		
	}


