# Parking_Calculator
Automate the  web page http://adam.goucher.ca/parkcalc.  Create a Java project using Eclipse or IntelliJ that we can execute.  
 
Requirements:
 
1.	Java project should be a Maven project.
2.	Use Selenium WebDriver and TestNG.
3.	Create necessary pages using the “Page Object Model” design pattern.
4.	Test data will be stored in a CSV file.  Data should be provided to the tests using TestNG DataProvider.  Bind the data to a Java object (POJO) and have that as a parameter to the test.
5.	Create 1 test for Short-Term and 1 test for Long-Term parking 
a.	Set the fields and calculate the cost.
b.	Verify the cost is correct. (Use AssertJ 3rd party library for this)

#### Note
Finding Xpath and CSSSelector on chrome Dev tool (no need Firebug or Firepath):

From google Dev tool, select element, right click and select 

Copy->Copy Selector (CSSSelector),

Copy JS path(for valilla Framework/Query selector),

Copy xpath (which is relative xpath finds the closed id to the dom element and generates xpath starting from that element e.g .//*[@id='answers']/h2[1]/a[1]),

Copy full xpath (An absolute xpath in HTML DOM starts with /html)

Validate xpath and CSSSelector on Chrome's console:

CSSSelector: $$("#homeval") --remove double quote after id= if exist, instead use single quote.

Xpath: $x("//*[@id='downpayment']") --remove double quote after id=, instead use single quote.

Alternatively, you can use Selenium IDE plugin on Chrome and locate Xpath and CSSSelector.
