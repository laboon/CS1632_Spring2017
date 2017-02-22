# CS 1632 - Software Quality Assurance
Spring Semester 2017

DUE 15 MAR 2017

## Deliverable 3

For this assignment, you and a partner will write a systems-level, automated black-box tests for a web app using Selenium and JUnit. 

Test code should be on GitHub and shared with the TA and myself by the beginning of class on the due date.  You 

You may work with ONE partner for this deliverable.  However, it CANNOT be the same person you worked with for Deliverable 1.  You may also opt to work by yourself, but the requirements for the assignment are the same.  

Please use the TestRunner and the included Selenium jars.  These are _not_ the latest Selenium jars, but they are guaranteed to work together.

The web app is located here: https://cs1632ex.herokuapp.com/

This is an Elixir/Phoenix application.  If you like, you may look at the source code here: https://github.com/laboon/cs1632d3ex.  However, this is NOT necessary.  I do not expect you to learn another language for this course.  It might be interesting for you to see Elixir code, though.

## Format
Everyone should have a title page with:
* The title "CS 1632 - DELIVERABLE 3"
* The names of people in the group and their GitHub usernames
* A link to the GitHub repository

For the summary, add a description of issues you faced when writing these tests and problems you would expect going forward based on your experiences.  If any tests you wrote fail (some should!), they should be included here.

After this, there should be a printout or screen shot of the test execution results.


There is no need to print out the code.  It should be shared with me and the TA (i.e., we have been added as collaborators) on GitHub BY THE BEGINNING OF CLASS.

The JUnit tests shall have a description (a few sentences at most) of what they are testing written in the comments above the particular test. See RedditTest.java in the sample_code directory for an example.

Remember these are USER-level systems tests; comments should describe tests in a way that an intelligent user of the software would understand.  Even though we are using JUnit, these are _not_ unit tests.  Remember the differences between system-level tests and unit tests!

There should be a bare minimum of twenty tests, checking various base, edge, and corner cases.  There is a maximum of thirty tests.  However, do not focus on the number of tests too heavily; I am more concerned that you cover a broad variety of cases, and ones which are focuses and still likely to find defects.

If you find yourself with more than two or three assertions in a test case, that is a code smell that it is not focused enough.

## Note on Selenium Drivers

Note that the driver I use in class, HtmlUnitDriver, is its own project and no longer included with the latest Selenium release.  You may download it separately from: https://github.com/SeleniumHQ/htmlunit-driver/releases

You may find it easier to use the last version of Selenium which includes HtmlUnitDriver.

2.52 Selenium Server jar: http://selenium-release.storage.googleapis.com/2.52/selenium-server-standalone-2.52.0.jar

2.52 Java bindings jar: http://selenium-release.storage.googleapis.com/2.52/selenium-java-2.52.0.zip

Either way is acceptable for our purposes.

## Note on Firefox / Selenium in Windows

To open the Selenium IDE from Firefox in Windows, right click the top bar of firefox, between the open tabs and the minimize button. Click "Menu Bar" so the menu bar shows up in the top left corner. Under "Tools" is "Selenium IDE".

Alternatively, "ctrl+alt+s" while in the Firefox window should also bring up the IDE.

## Requirements

Requirements for the application are listed in the requirements.md file in this directory.

Remember to check for implicit as well as explicit requirements!

You should have at least one test for each requirement, although there is no need to write a traceability matrix.

## Defects

This is another buggy product.  You should find at least three defects and report them using the standard defect template (just like in the first deliverable).  These defects should be detected by your automated tests (i.e., there should be at least _three_ failures of your tests).

You may want to do some exploratory testing first to see what kind of issues are found before writing automated tests for them.

## Grading
* Summary and Testing concerns - 5% 
* Screen shot or printout of test results - 5%
* Proper comment descriptions of tests - 10%
* JUnit Tests - 50%
* Defect reports - 30%

Please feel free to email me or come to office hours to discuss any problems you have. 
 
