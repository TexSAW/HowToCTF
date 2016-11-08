# Creating Challenges

With teams setup the next task is to create challenges.  This process is somewhat dependent on what type of CTF is being run.  For the Jeopardy-board style CTF that is in use at TexSAW and increasingly at other competitions, we use the following workflow:

1. With everyone in the same room, create a new spreadsheet.  On the first sheet in the workbook, create the Jeopardy board itself with categories in the left most column and points going across the top.  In each square the group should come up with a challenge and write down its title, making a note of the problem specifics elsewhere.  We track problem specifics in a second sheet within the same workbook where problems are listed one to a line with grouping by category on the left side.  This initial meeting occurs for our teams around 5 weeks before the CTF is expected to go live.  Some good categories to start with are:
  * Trivia
  * Reversing
  * Crypto
  * Pwnables
  * Forensics
  * Web
  * Potpourri
2. Once the problems are decided on, split up the responsibilities for who will work on which problems.  This is a crucial step and the people who claim problems should be able to speak with confidence that they can complete any problem that they have taken on.
3. Set a due date for problems to be handed off to the infrastructure team.  The due date should be at minimum 2 weeks before the CTF is expected to go live to account for the time needed to load problems into the system as well as time needed to revise any problems that are found to be defective.
4. Load all the problems into CTFd and confirm that they are displayed correctly and with all information present.
5. Setup backend infrastructure for any problems that require it.  This can range from servers being provisioned to host exploitable executables or even printing out a physical flag.


## A note on problem difficulty

Its a good idea to carefully consider the problem difficulty scaling when building out the initial list of problems.  A good CTF will have around 60% of the problems solvable by everyone, 30% being solvable by around half the contestants, and 10% of problems that are more difficult than most contestants are expected to solve.  The last 10% is in place to slow down anyone who comes in with an exceptional amount of knowledge beforehand and to break ties if any exist.
