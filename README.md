Package tests;		
import io.github.bonigarcia.wdm.WebDriverManager;		
import org.openqa.selenium.WebDriver;		
import org.openqa.selenium.chrome.ChromeDriver;		
import pages.*;		
public class orangHRMTest{		
public static void main(string[]  args){		
WebDriverManager.chromedriver().setup();		
webDriver  driver = new  ChromeDriver();		
driver. get("https://opensource-demo.orangehrmlive.com/web/index.php/auth/login");		
driver.manage().window().maximize();		
LoginPage loginPage=new LoginPage(driver);		
loginPage.login("Admin","admin123");			
DashboardPage  dashboardPage =new DashboardPage(driver);		
dashboardPage .goToPIM();				
PIMPage pimPage=new PIMPage(driver);		
String[] names={"Alice Smith","Bob Taylor","Carol Johnson"};		
for (String fullnames : names){		
String[] parts=fullName.split(" ");		
pimpPage.addEmployee(parts[0],parts[1]);		
}			
pimPage.goToEmployeeList();		
for (String  name : names){		
pimPage.verifyEmployee(name);		
}				
driver.quit();		
}		
}		

