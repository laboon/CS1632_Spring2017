## CitySim9004 Requirements

FUN-CITY-LOCS. The program shall simulate a city with four locations: Presby, Union, Sennott, and Hillman.

FUN-OUTSIDE-CITY. A fifth location, Outside City, shall stand for a driver outside the city limits.

FUN-AVENUES. The city shall have two one-way avenues, Fourth Ave and Fifth Ave.  Fourth Ave shall connect, in order, Outside City -> Presby -> Union -> Outside City.  Fifth Ave shall connect, in order, Outside City -> Hillman -> Sennott -> Outside City.

FUN-STREETS. The city shall have two two-way streets, Bill St. and Phil St.  Bill St. shall connect Presby and Sennott.  Phil St. shall connect Union and Hillman.

FUN-FIVE-DRIVERS. Five drivers, numbered 1 through 5, shall traverse the city, one after the other.

FUN-SENNOTT-COUNT. At the end of each drive, the simulation shall print out how many times that driver visited Sennott.  The format shall be "Driver `n` met with Professor Laboon `x` time(s).", where `n` is the driver number (1 through 5) and `x` is the number of times that the driver visited the Sennott location.  If a driver starts on the Sennott location, this counts as a time visiting the Sennott.  

FUN-SENNOTT-EDGES: If a driver visited Sennott three or more times, then an additional line shall be printed stating "Wow, that driver needed lots of CS help!" If a driver never visits Sennott, the additional line shall be printed stating "That student missed out!"  If a driver visisted Sennott one or two times, then no additional line shall be printed.  This shall be the last line printed out for each iteration.

FUN-START-LOC. A driver may start in any of the four locations listed in FUN-CITY-LOCS.  Drivers may not start outside of the city.

FUN-ITERATION. At each iteration, a Driver will drive from the current Location to one of the possible Locations that can be reached from the original Location.  The decision shall be made pseudorandomly based on a seed passed in from the command line, as covered by FUN-ARGS.

FUN-END. The simulation shall end if a Driver encounters the Outside City Location.

FUN-ARGS. The system shall accept an integer seed from the command line for the pseudorandom number generator.  No other arguments shall be accepted.  If no arguments are provided,  more than one argument is provided, or the single argument is not an integer, the system shall inform the user and exit.

FUN-OTHER-CITIES. If a driver exits the city via Fourth Avenue (that is, goes to the Outside City location past the Union), then the program shall display that the driver has gone to Philadelphia.  If a driver exits the city via Fifth Avenue (that is, goes to the Outside City location past the Sennott), then the program shall display that the driver has gone to Cleveland.

FUN-DASHES. After each iteration's display on the screen, a line of five dashes (i.e., `-----`) shall be printed.  This line of dashes shall occur after all information from that iteration has been printed out.

It may be easier to understand the map of the city visually.

```
City Map
	
                ---> [Presby] ----> [Union] ----> Fourth Ave. (to Philadelphia)
                      A  |          A  |
              Bill St.|  |          |  | Phil St.
                      |  V          |  V
 (to Cleveland) <--- [Sennott] <-- [Hillman] <--- Fifth Ave.
```	
