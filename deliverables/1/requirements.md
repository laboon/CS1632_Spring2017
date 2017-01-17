FUN-BASIC-CALC - The system shall calculate the results of switching or staying, according to the defined Monty Hall problem, for "number of times" iterations.  

FUN-THREADS - The system shall allocate all work proportionally to threads.  That is, the number of iterations per thread should never have a difference of more than one iteration compared to any other thread. The number of iterations allocated to each thread shall be displayed to the user before calculating.

FUN-DISPLAY-RESULTS - After calculating, the system shall display this information to the user after calculating, using percentages with up to three places after the decimal, and then stop execution.  This display shall print out the passed-in String versions of the "good" and "bad" options as defined in the arguments.

FUN-ARGS-NUMBER - The system shall accept four arguments from the command line, in the following order: good option, bad option, number of times, number of threads.  If there are fewer or more than four arguments, the system will display the usage information for the program and shut down..

FUN-ARGS-INVALID - If an argument is invalid for any reason (specifically, the number of times or number of threads cannot be parsed as a positive integer), then the system shall explain the reason that it cannot run and will shut down.

FUN-SMALL-NUM - If the "number of times" argument is less than 100, the system shall issue a warning and ask the user if they wish to continue.

FUN-SMALL-NUM-CONT - When asking the user if they wish to continue, the system shall be case-insensitive.  That is, the user may enter either "Y" or "y" to indicate yes, or either "N" or "n" to indicate no.  If invalid input (i.e., anything other than "Y", "y", "N", or "n") is entered, the user shall be asked again to enter their selection.  This shall be repeated as many times as necessary until the user enters valid input.

NF-PERFORMANCE - For any given number of threads n, the system shall run faster (that is, shall complete execution and display results in a smaller amount of time), with a higher n.
