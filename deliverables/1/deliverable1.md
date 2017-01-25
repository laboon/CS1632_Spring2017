# CS 1632 - Software Quality Assurance
Spring Semester 2017

* ASSIGNED: 18 JAN 2017

* DUE: 3 FEB 2017

## Deliverable 1

For this assignment, your group will determine a test plan for the simple simulator GoatGoatCar, based on the requirements listed.  There are several known defects in the software; you will need to find and report on at least three.  Additionally, a traceability matrix showing the mapping of test cases to requirements is required.  

Time will be given in class to group yourself into groups.  There should be two and only two members of a group.

There should be at least twice as many test cases as requirements, although I would normally expect several test cases per requirement.  If the number of test cases is more than 3x the number of requirements, you are probably overtesting.

Each requirement should have AT LEAST one test case associated with it, and each test should have EXACTLY ONE requirement associated with it.  This can easily be checked via a traceability matrix (which you should also deliver).  Note that some test cases may actually test several requirements.  You should specify the one that the test case fits best - that is, what are you really trying to test with this test case?

Test cases should mention all necessary preconditions, execution steps, and postconditions.

It is NOT necessary to make multiple test plans inside a test suite; it is enough for there to be one test plan.

I expect you to test three edge or corner cases as part of the test plan.  These should be marked in the description of the relevant test case.

It is expected that you actually execute the test plan in order to find the defects, along with some exploratory testing to determine how the system works and where defects might lie.  There are AT LEAST three defects.  Full credit will be given only to those who properly find and describe at least three.  While you are not expected to find *all* of the defects, a reasonable test plan should definitely find at least three.  This is an intentionally target-rich environment.

## Format
Please hand in the paper to me with a cover page with:
* The name of the project under test ("GoatGoatCar")
* The names of the people in the group
* The title "CS 1632 - DELIVERABLE 1: Test Plan and Traceability Matrix"

There should be a short introduction (a few paragraphs) in which you may note any concerns or difficulties you may have had or anticipate with the testing process.  You should also note why you considered certain test cases, how you thought of edge cases, etc.

This should be followed ON A NEW PAGE by the list of test cases.  You may name or number them any way you wish, but be consistent.  You should write them out in this format -

	IDENTIFIER:
	TEST CASE: 
	PRECONDITIONS:
	EXECUTION STEPS:
	POSTCONDITIONS:

The IDENTIFIER is some value which will UNIQUELY specify the test case.  It can be a number, word or any other mnemonic (e.g. TEST-INVALID-TIMES, TEST-LOW-NUM-TIMES, etc.).

ON A SEPARATE PAGE, a traceability matrix should be provided mapping the test cases with their associated requirements.  Remember that all requirements should map to AT LEAST ONE test case (but usually more), and all test cases should map to EXACTLY ONE requirement.  

Finally, ON A SEPARATE PAGE, list at least three defects found.  The defects should follow the defect reporting template:

	 SUMMARY:
	 DESCRIPTION:
	 REPRODUCTION STEPS:
	 EXPECTED BEHAVIOR:
	 OBSERVED BEHAVIOR:

Other attributes of a defect (e.g., SEVERITY or IMPACT) are not necessary.  The test case which found the defect should be listed as part of the DESCRIPTION.

## Grading
* Introduction: 10% of grade
* Test Plan: 40% of grade
* Traceability Matrix: 20% of grade
* Defects Found and Described: 30% of grade

## GoatGoatCar
GoatGoatCar is going to be our way of determining the correct answer to the "Monty Hall Problem" (https://en.wikipedia.org/wiki/Monty_Hall_problem).  The Monty Hall Problem can be summarized as follows:

_Assume you are on a game show with three closed doors.  Behind one door is a car (which you want), and behind the other two doors are goats (which you do not want - if you do want a goat, I implore you to research how difficult goat tending is).  You pick one door, which you hope has the car behind it.  The game show host - who knows where the car is, and so will not open that door - opens up one of the two doors you did not select.  Behind that door is, of course, a goat._

_The question: is the optimal strategy to switch doors to the remaining closed door, to stay with the door you've already selected, or does it not matter?_

Our program will attempt to find the solution the worst possible way - by brute force.  It will simulate a large number of these decisions and give a summary at the end of what percentage of the time switching would give you the "good item" and what percentage of the time staying would have won you the "bad" item.

The program will accept four arguments, in this order:

* __"Good" option__ - This will be the item that the player actually wants (e.g., a car).

* __"Bad" option__ - This will be the item that the player does not want (e.g., a goat)

* __Num Times__ - This is the number of rounds that will be simulated.

* __Num Threads__ - This will be the number of threads that the simulation runs in

Example command to execute.  This will use "car" as the good choice, "goat" as the bad choice, 10001 as the number of rounds to simulate, and it will do it on four threads.

```
$ java -jar GoatGoatCar.jar car goat 10001 4
```

GoatGoatCar.jar is available in this directory.  

The requirements are listed in the file requirements.md.

Please feel free to email me or come to office hours to discuss any problems you have. 
 
