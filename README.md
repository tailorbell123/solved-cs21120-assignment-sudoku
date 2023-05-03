Download Link: https://assignmentchef.com/product/solved-cs21120-assignment-sudoku
<br>
Introduction

This assignment will test your ability to implement a depth-first recursive algorithm to solve a puzzle and think about aspects of its performance in terms of Big-O complexity. It will also test your ability to write this code to conform to existing interfaces – much programming in the real world requires this. You will need to show that you can test your code: while some basic tests are provided, you should write more. You should also be able to say why you wrote the tests as you did.

Finally, you will need to write a report describing how you went about implementing each part of the assignment, including why you wrote the algorithms the way you did and what the complexities of the different algorithms are. Each task has a description of what you should write in the report.

<h1>Problem Description</h1>

For this assignment, you will be writing a program to solve Sudoku puzzles. These puzzles consist of a 9×9 grid of numbers divided into 3×3 sub-grids, with only some of the numbers provided. Here’s an example:

<table width="261">

 <tbody>

  <tr>

   <td width="28"> </td>

   <td width="29"> </td>

   <td width="29"> </td>

   <td width="29"> </td>

   <td width="29"> </td>

   <td width="29"> </td>

   <td width="29"> </td>

   <td width="29"> </td>

   <td width="28"> </td>

  </tr>

  <tr>

   <td width="28"> </td>

   <td width="29"> </td>

   <td width="29"> </td>

   <td width="29"> </td>

   <td width="29"> </td>

   <td width="29"> </td>

   <td width="29"> </td>

   <td width="29"> </td>

   <td width="28"> </td>

  </tr>

  <tr>

   <td width="28"> </td>

   <td width="29"> </td>

   <td width="29"> </td>

   <td width="29"> </td>

   <td width="29"> </td>

   <td width="29"> </td>

   <td width="29"> </td>

   <td width="29"> </td>

   <td width="28"> </td>

  </tr>

  <tr>

   <td width="28"> </td>

   <td width="29"> </td>

   <td width="29"> </td>

   <td width="29"> </td>

   <td width="29"> </td>

   <td width="29"> </td>

   <td width="29"> </td>

   <td width="29"> </td>

   <td width="28"> </td>

  </tr>

  <tr>

   <td width="28"> </td>

   <td width="29"> </td>

   <td width="29"> </td>

   <td width="29"> </td>

   <td width="29"> </td>

   <td width="29"> </td>

   <td width="29"> </td>

   <td width="29"> </td>

   <td width="28"> </td>

  </tr>

  <tr>

   <td width="28"> </td>

   <td width="29"> </td>

   <td width="29"> </td>

   <td width="29"> </td>

   <td width="29"> </td>

   <td width="29"> </td>

   <td width="29"> </td>

   <td width="29"> </td>

   <td width="28"> </td>

  </tr>

  <tr>

   <td width="28"> </td>

   <td width="29"> </td>

   <td width="29"> </td>

   <td width="29"> </td>

   <td width="29"> </td>

   <td width="29"> </td>

   <td width="29"> </td>

   <td width="29"> </td>

   <td width="28"> </td>

  </tr>

  <tr>

   <td width="28"> </td>

   <td width="29"> </td>

   <td width="29"> </td>

   <td width="29"> </td>

   <td width="29"> </td>

   <td width="29"> </td>

   <td width="29"> </td>

   <td width="29"> </td>

   <td width="28"> </td>

  </tr>

  <tr>

   <td width="28"> </td>

   <td width="29"> </td>

   <td width="29"> </td>

   <td width="29"> </td>

   <td width="29"> </td>

   <td width="29"> </td>

   <td width="29"> </td>

   <td width="29"> </td>

   <td width="28"> </td>

  </tr>

 </tbody>

</table>

Solving the puzzle involves working out how to complete the grid, which must obey the following rules:

<ul>

 <li>Each row contains each digit once only</li>

 <li>Each column contains each digit once only</li>

 <li>Each 3×3 sub-grid contains each digit once only</li>

</ul>

A valid solution for the puzzle above is:

<table width="277">

 <tbody>

  <tr>

   <td width="30"> </td>

   <td width="31"> </td>

   <td width="31"> </td>

   <td width="31"> </td>

   <td width="31"> </td>

   <td width="31"> </td>

   <td width="31"> </td>

   <td width="31"> </td>

   <td width="30"> </td>

  </tr>

  <tr>

   <td width="30"> </td>

   <td width="31"> </td>

   <td width="31"> </td>

   <td width="31"> </td>

   <td width="31"> </td>

   <td width="31"> </td>

   <td width="31"> </td>

   <td width="31"> </td>

   <td width="30"> </td>

  </tr>

  <tr>

   <td width="30"> </td>

   <td width="31"> </td>

   <td width="31"> </td>

   <td width="31"> </td>

   <td width="31"> </td>

   <td width="31"> </td>

   <td width="31"> </td>

   <td width="31"> </td>

   <td width="30"> </td>

  </tr>

  <tr>

   <td width="30"> </td>

   <td width="31"> </td>

   <td width="31"> </td>

   <td width="31"> </td>

   <td width="31"> </td>

   <td width="31"> </td>

   <td width="31"> </td>

   <td width="31"> </td>

   <td width="30"> </td>

  </tr>

  <tr>

   <td width="30"> </td>

   <td width="31"> </td>

   <td width="31"> </td>

   <td width="31"> </td>

   <td width="31"> </td>

   <td width="31"> </td>

   <td width="31"> </td>

   <td width="31"> </td>

   <td width="30"> </td>

  </tr>

  <tr>

   <td width="30"> </td>

   <td width="31"> </td>

   <td width="31"> </td>

   <td width="31"> </td>

   <td width="31"> </td>

   <td width="31"> </td>

   <td width="31"> </td>

   <td width="31"> </td>

   <td width="30"> </td>

  </tr>

  <tr>

   <td width="30"> </td>

   <td width="31"> </td>

   <td width="31"> </td>

   <td width="31"> </td>

   <td width="31"> </td>

   <td width="31"> </td>

   <td width="31"> </td>

   <td width="31"> </td>

   <td width="30"> </td>

  </tr>

  <tr>

   <td width="30"> </td>

   <td width="31"> </td>

   <td width="31"> </td>

   <td width="31"> </td>

   <td width="31"> </td>

   <td width="31"> </td>

   <td width="31"> </td>

   <td width="31"> </td>

   <td width="30"> </td>

  </tr>

  <tr>

   <td width="30"> </td>

   <td width="31"> </td>

   <td width="31"> </td>

   <td width="31"> </td>

   <td width="31"> </td>

   <td width="31"> </td>

   <td width="31"> </td>

   <td width="31"> </td>

   <td width="30"> </td>

  </tr>

 </tbody>

</table>

There are many Sudoku (or Su Doku) generators online, for example <a href="https://www.sudokuweb.org/">https://www.sudokuweb.org/</a>– if you’re unfamiliar with the puzzle I recommend trying a few by hand to see the challenge involved.

<h1>Solving the Puzzle</h1>

For the assignment, you will be writing an in-order recursive backtracking depth-first search for solutions:

<ul>

 <li><strong>In-order</strong>: the algorithm will try to fill each cell in turn, working from top-left to bottom-right, and trying each digit from 1 up to 9.</li>

 <li><strong>Recursive: </strong>the algorithm works by finding a single valid digit to place, and then calling the algorithm on the resulting grid (which is a simpler version of the puzzle because it has an extra cell filled in).</li>

 <li><strong>Backtracking:</strong> if the algorithm can’t find a valid digit to place in the next cell, the digit it placed previously must be incorrect, so we need to go back a step (up a level in the recursion) and try the next digit in the previous cell. If that fails, we go up another level still. If this fails up to the top level, there is no solution.</li>

 <li><strong>Depth-first: </strong>If you consider the possible ways to fill in the grid as a tree (see the next page), the tree will be explored in a depth-first manner, moving along each branch as far as possible before finding a solution or backtracking.</li>

</ul>




Look at the diagram below, which shows part of the tree of possible solutions. Grids which are invalid are greyed out.

<table width="72">

 <tbody>

  <tr>

   <td width="8"> </td>

   <td width="8"> </td>

   <td width="8"> </td>

   <td width="8"> </td>

   <td width="8"> </td>

   <td width="8"> </td>

   <td width="8"> </td>

   <td width="8"> </td>

   <td width="8"> </td>

  </tr>

  <tr>

   <td width="8"> </td>

   <td width="8"> </td>

   <td width="8"> </td>

   <td width="8"> </td>

   <td width="8"> </td>

   <td width="8"> </td>

   <td width="8"> </td>

   <td width="8"> </td>

   <td width="8"> </td>

  </tr>

  <tr>

   <td width="8"> </td>

   <td width="8"> </td>

   <td width="8"> </td>

   <td width="8"> </td>

   <td width="8"> </td>

   <td width="8"> </td>

   <td width="8"> </td>

   <td width="8"> </td>

   <td width="8"> </td>

  </tr>

  <tr>

   <td width="8"> </td>

   <td width="8"> </td>

   <td width="8"> </td>

   <td width="8"> </td>

   <td width="8"> </td>

   <td width="8"> </td>

   <td width="8"> </td>

   <td width="8"> </td>

   <td width="8"> </td>

  </tr>

  <tr>

   <td width="8"> </td>

   <td width="8"> </td>

   <td width="8"> </td>

   <td width="8"> </td>

   <td width="8"> </td>

   <td width="8"> </td>

   <td width="8"> </td>

   <td width="8"> </td>

   <td width="8"> </td>

  </tr>

  <tr>

   <td width="8"> </td>

   <td width="8"> </td>

   <td width="8"> </td>

   <td width="8"> </td>

   <td width="8"> </td>

   <td width="8"> </td>

   <td width="8"> </td>

   <td width="8"> </td>

   <td width="8"> </td>

  </tr>

  <tr>

   <td width="8"> </td>

   <td width="8"> </td>

   <td width="8"> </td>

   <td width="8"> </td>

   <td width="8"> </td>

   <td width="8"> </td>

   <td width="8"> </td>

   <td width="8"> </td>

   <td width="8"> </td>

  </tr>

  <tr>

   <td width="8"> </td>

   <td width="8"> </td>

   <td width="8"> </td>

   <td width="8"> </td>

   <td width="8"> </td>

   <td width="8"> </td>

   <td width="8"> </td>

   <td width="8"> </td>

   <td width="8"> </td>

  </tr>

  <tr>

   <td width="8"> </td>

   <td width="8"> </td>

   <td width="8"> </td>

   <td width="8"> </td>

   <td width="8"> </td>

   <td width="8"> </td>

   <td width="8"> </td>

   <td width="8"> </td>

   <td width="8"> </td>

  </tr>

 </tbody>

</table>

Our algorithm should do the following:

<ol>

 <li>Try to put a 1 in the first available place. That’s invalid, there’s a 1 in the same row.</li>

 <li>Try to put a 2 in the same place. That’s fine, try to solve the resulting puzzle by recursing:

  <ol>

   <li>Try to put a 1 in the first available place. That’s invalid, there’s a 1 in the same column.</li>

   <li>Try a 2 in the same place. Invalid, there’s already a 2 in the same column.</li>

   <li>Try a 3 in the same place. Invalid, there’s a 3 in the same row.</li>

   <li>Try a 4 in the first available place. That’s valid, so try to solve that puzzle.

    <ol>

     <li>Try a 1 in the first available place. Invalid, there’s a 1 in the same row.</li>

     <li>Try a 2 in the same place. Invalid, there’s a 2 in the same row.</li>

    </ol></li>

  </ol></li>

</ol>

<ul>

 <li>Try a 3 in the same place. Invalid, there’s a 3 in the same sub-grid. iv. Try a 4 in the same place. Invalid, there’s a 4 in the same column.</li>

</ul>

<ol>

 <li>Try a 5 in the same place. Invalid, there’s a 5 in the same row.</li>

 <li>Try a 6 in the same place. That’s valid, so try to solve that puzzle. Eventually this path leads to a solution – we never get as far as step 3.</li>

</ol>

The small portion of the tree shown above doesn’t show most of the possible digits and doesn’t show any backtracking. This happens when all the possible digits are invalid in a position, meaning that puzzle can’t be solved. To fix this, we go up to the previous level, remove the digit created there, and try a different one.

This video shows the process in full detail – you can see that backtracking doesn’t start to happen until the fourth row: <a href="https://www.youtube.com/watch?v=e9y7nHuHrEs">https://www.youtube.com/watch?v=e9y7nHuHrEs</a>

<h1>The Algorithm</h1>

The algorithm itself is as follows, in pseudocode. Make sure you understand the logic behind it and follow the indenting carefully. <strong>(This is the corrected algorithm.) </strong>

Function <strong>solve</strong>, which returns a boolean (true if it solved the puzzled, false if it failed):

<ul>

 <li>For each grid cell:</li>

</ul>

o If the cell is empty:

&#x25aa;    For each digit 1-9:

<ul>

 <li>Insert the digit into the cell If the resulting grid is valid:</li>

</ul>

o Result=<strong>solve()</strong> (i.e. try to recursively solve the new grid with a digit filled in) o If result is true, return true (we solved it!)

<ul>

 <li>set the cell to empty</li>

 <li>return false – we tried all the digits, none led to a solution. It’s a dead end.</li>

</ul>

<ul>

 <li>No empty cell was found, return true – we solved the grid!</li>

</ul>

<h1>Provided Code</h1>

You are provided with a Zip archive containing two packages:

<ul>

 <li><strong>ac.aber.cs21120.interfaces </strong>contains the interfaces you must implement in your solution. If you do not implement these interfaces, or write code which does not conform to them, your solution will fail my marking tests.</li>

 <li><strong>ac.aber.cs21120.tests </strong>contains classes which test your program. The <em>GridTests </em>class can be included once you have written <em>Grid, </em>and the <em>SolverTest</em> class can be included once you have written <em>Solver. </em>It also contains <em>Examples:</em> a utility class with 400 example puzzles to solve.</li>

</ul>

These are in two folders inside the archive called <strong>interfaces </strong>and <strong>tests. </strong>When prompted by the assignment, copy the files into packages of the correct names inside your project.

<strong> </strong>




<h1>Tasks</h1>

<h2>Setting Up</h2>

Before starting work, set up a new empty project and create three packages:

<ul>

 <li><strong>ac.aber.cs21120.solution</strong></li>

 <li><strong>ac.aber.cs21120.interfaces</strong></li>

 <li><strong>ac.aber.cs21120.tests</strong></li>

</ul>

<h2>Task 1: The Grid Class</h2>

Your first task is to create a class for the grid. This encapsulates the underlying 9×9 grid, and also handles checking the grid for validity. This must be created in the <strong>uk.ac.aber.cs21120.solution </strong>package, and should implement the <strong>IGrid </strong>interface provided in the <strong>uk.ac.aber.cs21120.interfaces </strong>package.

Before you start work, copy the files from the provided <strong>uk.ac.aber.cs21120.interfaces</strong> package into the same package in your program. Leave the remaining packages empty for now.

Now create a <strong>Grid</strong> class inside your solutions package which implements <em>IGrid</em> with the following methods:

<ul>

 <li><strong>public int get(int x, int y) throws IGrid.BadCellException</strong> o this returns the value of the cell at x,y in the grid as an integer from 1-9, or 0 if the cell is empty. If x or y are out of range, <strong>BadCellException </strong>(an exception nested inside <em>IGrid</em>) should be thrown.</li>

 <li><strong>public void set(int x, int y, int digit) throws IGrid.BadCellException, IGrid.BadDigitException</strong> o this sets the cell at x,y in the grid to an integer from 1-9, or 0 for empty. If x or y are out of range, <strong>BadCellException </strong>(an exception nested inside <em>IGrid</em>) should be thrown. If the value itself is not in the range 0-9, <strong>IGrid.BadDigitException </strong>should be thrown.</li>

 <li><strong>public boolean isValid()</strong> o This returns true if the grid is valid. In a valid grid, each (non-zero) digit must only appear once in each row, each column and each 3×3 sub-grid (see the rules in the problem description above). Note that zero cells are empty and do not count. Your grid class must also have a constructor</li>

 <li><strong>public Grid()</strong></li>

</ul>

This is not specified in the interface (because Java does not permit that), but my tests will not run without it. Also, note that the two exceptions I have defined are subclasses of <em>RuntimeException</em> – this means that you don’t have to provide try/catch blocks every time you use <em>get()</em> and <em>set(). </em>The most difficult part of this task is the <em>isValid() </em>method for checking the grid according to the rules.

<h3>Testing</h3>

I have added a fairly comprehensive set of tests to the <strong>uk.ac.aber.cs21120.tests </strong>package to help you debug. Copy only the <strong>GridTests</strong> class into your <em>tests</em> package as you work on this task – if you copy other files your solution will not compile at this stage (as these require a solver).

<h3>In Your Report</h3>

Your report should describe how your <em>isValid() </em>method works in some detail. You should also talk about how easy or difficult you found the task, and how you went about solving it.

<h2>Task 2: The Solver Class</h2>

This task involves writing the actual Sudoku solver class, <strong>Solver. </strong>This class must be in the <strong>uk.ac.aber.cs.21120.solution </strong>package, and must implement the <strong>ISolver </strong>interface. The interface describes the following single method:<em>  </em>

<ul>

 <li><strong>public boolean solve() </strong>will attempt to solve the grid passed into the constructor. It will modify this grid as it does so, and will call itself recursively to solve simpler versions of the grid. If it succeeds, it will return true and the grid will be complete. If it fails, this grid cannot be solved and the solver must backtrack.</li>

</ul>

See the algorithm described above for more details. Your class must also provide a constructor of the form

<ul>

 <li><strong>public Solver(IGrid g)</strong></li>

</ul>

which again is not specified in the interface itself but is required for testing. This should simply store the grid in a member variable, which <em>solve() </em>can then modify as it runs.

To help with debugging, you may find it useful to write a method which outputs the grid as a string. Here is a simple example you can use:

<strong>public</strong> String <strong>toString</strong>(){

StringBuilder b = <strong>new</strong> StringBuilder();         <strong>for</strong>(<strong>int</strong> y=<strong>0</strong>;y&lt;<strong>9</strong>;y++){             <strong>for</strong>(<strong>int</strong> x=<strong>0</strong>;x&lt;<strong>9</strong>;x++){

b.append(get(x,y));

}

b.append(‘
’);         }

<strong>return</strong> b.toString();

}




I would also suggest adding some <em>System.out.println() </em>messages to show the progress of the algorithm. It might also be helpful to add an <em>int depth </em>member variable, which is incremented whenever <em>solve() </em>is entered and decremented when it returns. You can then print out the depth of the recursion with your other messages. Finally, note that the algorithm usually finishes very quickly, but if a lot of backtracking is required it can take a little while to solve a puzzle.

<h3>Testing</h3>

Inside the <strong>uk.ac.aber.cs21120.tests </strong>package you will find a class called <strong>SolverTests </strong>which you should copy into your own <em>tests</em> package and run. This tests progressively more difficult puzzles, starting from those with just one or two digits to fill in, then some with three or four gaps which require backtracking, before testing puzzles with 20 and 40 gaps. I will be using these tests to mark your assignment.

You will find also find an <strong>Examples</strong> class which you can copy into your <em>tests</em> package. This class contains 400 example puzzles, with a varying number of empty cells: low numbered examples have fewer empty cells, which vary from 30 for example 0 up to 69 for example 399. This class requires that you have a working <em>Grid</em> in your solution.




<em>Examples</em> has the following public static methods:

<ul>

 <li><strong>public static int getGapCount(int n)</strong>: return the number of empty cells in puzzle <em>n</em></li>

 <li><strong>public static IGrid getExample(int n)</strong>: return an <em>IGrid </em>containing puzzle <em>n</em> ready to be solved. Note that the object itself will be an instance of your own <em>Grid </em></li>

</ul>

<strong>These are static methods </strong>which don’t require an <em>Examples </em>object, so to call them use (for example)

Examples.getExample(100)

If you write your own test make sure to add them to your copy of the <em>tests</em> package and submit them as part of the assignment.

<h3>In Your Report</h3>

You should describe the problems you had, how you tested the code, and give a worst case Big-O complexity in terms of <em>n</em> where <em>n</em> is the number of empty spaces (hint: it’s the same as for a bruteforce search – just consider how many branches the algorithm must explore).

For flair marks, can you think of any ways to make the algorithm more efficient? Hint: the way <em>isValid() </em>is used isn’t very efficient, and there is a better way to do it. There are also better ways to pick the next cell to try to put a digit into, rather than just the next empty one. You don’t need to write any code for this part, just write down your ideas and the thinking behind them.

You are encouraged to research algorithms on the Internet or elsewhere for this task – but remember to include your references when you discuss your ideas. Not doing so counts as unfair academic practice!

<h2>Task 3: Solving Puzzles</h2>

Add a <strong>Main </strong>class to your <em>solution</em> package, with a <em>main</em> method. This should try to solve all 400 examples in the <em>Examples </em>class (in the <em>tests</em> package). For each puzzle, record the number of gaps and how long each puzzle took to solve. This may take a few minutes to run, and possibly several tens of minutes.

You can time the puzzles by making use of the <strong>System.currentTimeMillis() </strong>method, which returns the current time in milliseconds as a long:

<strong>long</strong> start = System.currentTimeMillis();

// do something in here

<strong>long</strong> timeTaken = System.currentTimeMillis()-start;




The easiest way to record the times is simply to print <em>puzzlenumber,gaps,time </em>using

<em>System.out.println() </em>or <em>System.out.format(). </em>Then cut and paste into Excel or a text file. Please don’t include the table in your report, it will be quite big!

Can you see a pattern in the results? Does it confirm your Big-O from task 2? For flair marks, include a plot of the results (time against number of gaps) – this may show the pattern more clearly, particularly if you plot the log of the time rather than just the time.

Task 4: Generating Puzzles

How could you use your Sudoku solver, combined with a random number generator, to write a program for generating Sudoku puzzles? Write a few lines of pseudocode to describe your ideas – or for flair marks actually write a class to do it and include it in your assignment. Again, you are free to research puzzle generators on the Internet, but remember to cite your references.

Writing the report

Your report should be around 1000-1500 words, containing the following sections:

<ul>

 <li>Task 1: The Grid Class</li>

 <li>Task 2: The Solver Class</li>

 <li>Task 3: Solving Puzzles</li>

 <li>Task 4: Generating Puzzles</li>

 <li>Self-evaluation: a paragraph describing which parts you found difficult and why, which parts you think you did well, and what mark you expect to get</li>

</ul>

Before writing the first two sections remember to read the “In Your Report” part of each task. Sections 1-4 should contain descriptions of how you went about the task and descriptions of any complex algorithms not described in this assignment brief.




<strong>The report must be provided as a PDF document. </strong>


