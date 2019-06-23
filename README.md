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
