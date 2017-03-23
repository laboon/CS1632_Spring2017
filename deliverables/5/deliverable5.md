# CS 1632 - Software Quality Assurance
Spring Semester 2017

DUE 5 APR 2017

## Deliverable 5

For this assignment, you and a partner will use static analysis to improve the Befunge interpreter that you worked on for Deliverable 4.  So for those of you who wrote the code poorly, beware!

If you are working with somebody different for this deliverable, you may use either person's previous deliverable.  

This project will consist of the following steps:

1. Use findbugs to statically analyze your code
2. Use checkstyle with the included configuration file (google_checks_modified.xml) to find any style issues with your code and fix them.
3. Fix *all* of the errors found by findbugs (with the exception of "Dead store to local variables" issues)
4. Ensure that you did not cause any regression failures, by:
  1. Running your test suite
  2. Running findbugs a final time
  3. Running checkstyle a final time

Your final version should have no bugs found by findbugs and no violations reported by checkstyle.

The checkstyle jar file is in this directory.  Checkstyle is a static analysis tool which acts as a linter - that is, it will tell you if there are style issues with your code which would not ordinarily impact compilation and execution, but may indicate errors, poor commenting, style violations, or simply difficult-to-read code.

We are using a modified Google style guide (also included in this directory).

You will also use findbugs, as described in class, to find possible bugs in your code and fix them.  FindBugs is available here: http://findbugs.sourceforge.net/

Note that findbugs has a known issue with the "Dead store to local variable" analysis.  You may ignore any errors of this kind (you can filter them out or just mentally ignore them).  

Run checkstyle using the included google_checks_modified.xml configuration file on all of your code.  Fix all of the issues so that the style is in line with the modified Google code guidelines (these are actual Google Java style guidelines, btw, with some small modifications by yours truly).  Before turning this in, your checkstyle run should show _no_ issues.

Checkstyle Usage Example:
```
java -jar ~/checkstyle/checkstyle-7.0-all.jar -c ./google_checks_modified.xml ~/pitt/CS/*.java
```

For the summary, include a listing of how you went about fixing the code issues found by the static analysis tools, and any issues you experienced.  This should not be more than a few paragraphs.  You do not need to detail each individual issue discovered, but discuss general ideas.

Include screenshots of both the FINAL findbugs and checkstyle output.

## Format
Every assignment should have a title page with:
* The name of the students in the group
* The title "CS 1632 - DELIVERABLE 5: Static Analysis"
* The URL for your git repository

There is no need to print out the code.  It should be available on GitHub or a similar code-sharing site BY THE BEGINNING OF CLASS.

## Grading
* Summary - 5%
* Screenshots of Findbugs and checkstyle output - 5%
* All issues from checkstyle fixed - 30%
* All issues from FindBugs fixed - 35%
* No regressions (all tests still pass; functionality works as before): 25%

Please feel free to email me or come to office hours to discuss any problems you have. 
 
