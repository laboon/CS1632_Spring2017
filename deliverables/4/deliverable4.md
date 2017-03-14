# CS 1632 - Software Quality Assurance
Spring Semester 2017

## Deliverable 4

For this assignment, you and a partner will profile a Befunge-93 interpreter, and improve its performance by refactoring three methods (to be determined by the results of the profiling), as well as writing appropriate pinning tests for each of them.  This will consist of several parts:

1. Profiling and timing (before) to determine which methods are the most CPU-intensive
2. Adding at least three pinning tests (in the form of unit tests) to each modified method to show that the functionality is unchanged by your modifications
3. Refactoring the method to be more performant (from a CPU / time perspective)
4. Profiling and timing (after) showing that your rewrite helped make your method more performant

There is an existing test suite which will help you, although it has gaps!  This is a common problem with legacy code...

Code will be on Github (https://github.com/laboon/CS1632_Befunge).  Please _duplicate_ (https://help.github.com/articles/duplicating-a-repository/) it and create your own repository, which should be private and shared with me (laboon) and the TA (mBarrenSQA).  

## Befunge

Befunge is a two-dimensional, stack-based language.  It does not have such bourgeois concepts as "variables", "functions", "floating-point values", or even "including numbers with more than one digit directly in the code".  Nevertheless, given a large enough address space, it is Turing-complete, which means that anything that can be computed can be computed as a Befunge program!

Befunge consists of a Program Area (the program itself), a Program Cursor (PC) which indicates the current location of execution, an integer stack, and output.  Input can be given one integer or one character at a time (via the commands `&` and `~`, respectively).

Befunge commands are all one character, e.g. `$`, `.`, or `4`.  

Let's run through a simple Befunge program.  This will count down from 9 to 1.

```
0123456789>:#._@
```

The PC starts in the upper-left and is initially going left-to-right.  It sees a `0`, and places it on the stack.  Then a `1`, and it is placed on the stack, etc., until we get to the `9`.  The `>` tells us to set the direction of the PC to RIGHT, which is already doing.  We now have a stack consisting of `[0, 1, 2, 3, 4, 5, 6, 7, 8, 9]` with 9 being the top of the stack.

The `:` command make a copy of the top element of the stack (so now our stack has an additional 9 in the front of it).  The `#` command means "jump over the next command", i.e., ignore it.  This jumps over the `.` command to the `_` command.  This is the "horizontal if" statement.  It pops the value off the stack and if it is 0, the PC starts going RIGHT; if it is nonzero, it goes LEFT.  Since the top value is 9 (which is not zero), it goes LEFT.  to the `.` command, which prints out the value 9 (remember we copied it with the `:` command, so there are two 9's).  Now we jump over the `:` to the `>`, which change our PC's direction to RIGHT.  This makes a copy of the 8 at the top of the stack, jumps over the `.` command, and `_` checks if the top value is equal to 0.  Since it is not, we continue the process for numbers 8 through 1.

Finally, once we get to the 0 (which acts as a "terminal" value), we make a copy of the 0, jump over the `.`, and check to see if 0 == 0.  It does, so direction continues RIGHT.  It then hits the `@` command which stands for "end program".  Our final output is this:

```
987654321
```

You will note that we can change the direction of execution!  This can also be done vertically.  It can get really fun from there.  This is an example of an infinite loop:

```
             >v
v"Bill Rules" <
9
1
+
> ,,,,,,,,,,, ^
```

The PC starts at the upper-left, and goes right until it hits `>`.  This tells us to keep going right.  Then the `v` command says to start executing downwards, and the `<` command means start going LEFT.  The `"` command pushes us into string-entry mode, which will read in characters as their ASCII elements until it hits another `"` to get us out of string-entry mode.  So we read in the ASCII values for "seluR lliB" (`[115, 101, 108, 117, 82, 32, 108, 108, 105, 66]`), then start going DOWN (the `v` commmand).

I wanted to put a carriage return (ASCII 10) but I cannot enter multiple-digit values directly.  So instead, I will put the value 9 on the stack, then 1, then add them together.  So now I have a CR at the top of my stack.

I reach the `>` command, then start going RIGHT again.  The `,` command pops the top value off the stack and renders it as a character.  Thus, I will pop the CR off, then the B, then the i, then the l, etc. until the output looks like this:

```

BILL RULES!
```

Once this is done I hit the `^` command and start going UP.  I ignore any spaces and eventually the PC hits the `<` command, which starts the loop over again.  This will continue until the heat death of the universe, the computer breaks down, or the user presses Ctrl-C.

```

BILL RULES!
BILL RULES!
BILL RULES!
BILL RULES!
... 
```

Although you can play around with the various programs, and even write your own, for this deliverable, we will work with my FizzBuzz implementation.

```
0v       v    <
 >91+91+*>:1-:|
              $    >"zziF",,,,v
              >:3%!|v         <
                         >"zzuB",,,,v           @
                   >>:5%!|v         <    >91+,:!|
                               >$        ^      
                         >>:3%!|    >$   ^ 
                               >:5%!|
                                    >.   ^            
              ^                                 <
```

Understanding the details is left as an exercise for the reader.

Any performance issues you find will NOT be the result of the Befunge code itself.

## Compilation and Execution

### Compilation of Source and Tests

1. Let's start by compiling the program itself.  `cd` to the `./src` subdirectory
2. Type the command `javac ./com/laboon/*.java`
3. This will have generated the class files in the appropriate directory.
4. `cd ..` to return to the root directory
5. Now compile the existing test suite.  `cd` to the `./test` subdirectory.
6. Type the command `javac -cp .:../src:./junit-4.12.jar:./hamcrest-core-1.3.jar ./com/laboon/*.java`  Note that Windows users may have to replace colons (`:`) with semicolons (`;`).
7. Test classes and a test runner should now exist in the correct (`./com/laboon`) subdirectory.

### Execution of Source and Tests

1. From the ./src subdirectory, type `java com.laboon.JBefunge` to run the program.
2. Copy and paste (or type your own Befunge program!) in the uppermost textbox (the "Program Area").
3. Click the `Run` button to execute the program.  Note that if you have an infinite loop or other defect, you may have to kill the program from the command line (Ctrl-C on Linux, OS X or Windows).  The current stack will appear in the `Stack:` textbox and the output from the program in the `Output` textbox.
4. Now to execute tests.  Go to the `./test` subdirectory.
5. Type `java -cp .:../src:./junit-4.12.jar:./hamcrest-core-1.3.jar com.laboon.TestRunner`.  This will execute the TestRunner.  When you first clone the repo, all tests should pass.

## Format
Every assignment should have a title page with:
* The name of the students in the group
* The title "CS 1632 - DELIVERABLE 4: Performance Testing Using VisualVM"

There is no need to print out the code.  It should be available on GitHub or a similar code-sharing site BY THE BEGINNING OF CLASS.

In order to determine the "hot spots" of the application, you will need to run a profiler such as VisualVM (download at https://visualvm.java.net/).  Using a profiler, determine a method you can use to measurably increase the speed of the application without modifying behavior.  

For the summary, describe how you profiled the application and determined the methods to refactor, and why you changed what you did.  The summary should not be more than a few paragraphs - definitely less than a page. 

After this, include screenshots of VisualVM (or another profiler, if you use that) both before and after the refactor.  These screenshots should include the relevant sections that let you see what method to refactor.

As part of this assignment, you should create "pinning tests".  Pinning tests are unit tests which should check that the behavior of a modified method was not changed by your refactor (see the chapter on testing legacy code in AFIST for examples).  This program should work EXACTLY the same as before, except it should be faster and take up less CPU time.  The only exception is if you come across an error and fix it - no points will be taken off as long as you note it in your summary.

There should be at least three pinning tests per method modified (check different edge cases).  

You should execute at least three runs of the FizzBuzz.bf program before and after your changes, and list all of these along with their arithmetic mean ("average") time.  

## Grading
* Summary - 10%
* VisualVM (or other profiler) screenshots (before and after) - 10%
* Initial and final times (>= 3 of each + mean) included - 10%
* Method choice and refactoring - 40%
* Pinning Tests - 30%

Please feel free to email me or come to office hours to discuss any problems you have. 
 
