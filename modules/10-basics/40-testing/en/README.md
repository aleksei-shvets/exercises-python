
Our site automatically checks your decisions. How does it work?

In the simplest case, the system just runs your code and looks at what's on the screen. And then it checks against what we "expected" from the job.

In the next, more complicated lessons, you will write functions, mini-programs that take information from the outside world and perform some operations. Checking your decisions in such cases looks a little more complicated: the system runs your decision and sends some information. The system also knows - "expects" - exactly what answer the correct function should give with this input.

For example, if your task is to write a function for adding two numbers, then the checking system will pass it different combinations of numbers and check the answer of your function against the real sums. If in all cases the answers are the same, then the solution is considered correct.

This approach is called testing, and it is used in real everyday development. Usually the programmer first writes a test, a test program, and then the program he wants to write. In the process, he is constantly running tests and seeing if he has come close to a solution.

That's why our site says "Tests passed" when you solve the problem correctly.

Here is a simple example: in a future lesson, you will need to write a function that performs calculations and gives the answer. Suppose you make a small mistake and the function gives you the wrong number. The system will answer something like this:

<pre class='hexlet-basics-output'>AssertionError: '10' != '35'</pre>

The most important thing begins after the colon: "the value of '10' is not equal to the expected value of '35'". That is, the correct function should have produced 35, but the current solution does not work correctly and produces 10.

It is also worth noting that if you see that there is already some code in the editor, and along with it the comments `BEGIN` and `END`, it usually means that you have to write your code between these very BEGIN and END! The code given to you beforehand should not be touched: it may affect the validation of the solution. To put it simply: you see lines with comments `BEGIN` and `END` — write your code between them!

---

Sometimes it will seem that you have done everything correctly, but the system is "capricious" and does not make a decision. Such behavior is practically excluded. Non-working tests simply can not get to the site, they automatically run after each change. In the vast majority of such cases, (and all of our projects have done millions of tests in total over many years), the error is contained in the solution code. It can be very subtle, instead of English letters accidentally entered the Russian, instead of upper case used lower case or forgot to display the comma. Other cases are more complicated. Your solution may work for one set of input data, but not for another. So always read the problem statement and test output carefully. There is almost certainly an error indication there.

However, if you are sure of an error or find some inaccuracy, you can always point it out. At the end of each theory, there is a link to the contents of the lesson on the githab (this project is completely open source!). By going there you can write an issue, look at the contents of the tests (you can see how your code is called) and even send a pullrequest.
