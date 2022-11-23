## Introduction

In this lab you will be creating a JavaScript application that runs in a web browser. 

While typically JavaScript is used to manipulate elements with in a webpage, in this lab we will be using the JavaScript console (viewed through browser development tools) to output results rather than manipulating a webpage.  This will allow you to write and debug the JavaScript code itself, rather than needing to know how to access webpage elements.

Work on the lab is to be done ***individually***.  You are welcome to collaborate with class members, but the project must be your own work.

## Outcomes

By the end of this lab you will be able to:

- Create a JavaScript program, have it be loaded and executed by the web browser
- Use the browser's debugger to find and fix errors in your JavaScript program
- Compare the performance of Java (run via the Java interpreter) and JavaScript (run via a web browser)

## Background

When the HTML page is loaded into a browser, a linked JavaScript program executes.  In this assignment, the JavaScript application acquires user input, and generates output via the browser debugging console.

This lab requires the use of your browser's debug console.  The process for opening the debug console is different depending on which browser you are using.  This site has information that can help: [https://balsamiq.com/support/faqs/browserconsole/](https://balsamiq.com/support/faqs/browserconsole/)

More information on different browsers' debug consoles:

- Chrome Console - [https://developer.chrome.com/docs/devtools/console/](https://developer.chrome.com/docs/devtools/console/)
- Microsoft Edge Console - [https://learn.microsoft.com/en-us/microsoft-edge/devtools-guide-chromium/console/](https://learn.microsoft.com/en-us/microsoft-edge/devtools-guide-chromium/console/)
- Firefox Console - [https://firefox-source-docs.mozilla.org/devtools-user/browser_console/index.html](https://firefox-source-docs.mozilla.org/devtools-user/browser_console/index.html)
- Safari Developer Tools Overview - [https://support.apple.com/guide/safari-developer/safari-developer-tools-overview-dev073038698/mac](https://support.apple.com/guide/safari-developer/safari-developer-tools-overview-dev073038698/mac)
- Opera Developer Tools - [https://help.opera.com/en/opera36/explore-advanced-features/#developerTools](https://help.opera.com/en/opera36/explore-advanced-features/#developerTools)

In a future lab, you will use HTML elements to retrieve and validate user input using a web page.

## Lab Project

For this project, you will create a JavaScript application based on a functioning Java application.  JavaScript programs generally run in the context of a web page, so you will also have to create an HTML page to host the JavaScript program. 

Download and execute this [Java application](CoinFlipper.java), adapted directly from an example in chapter 9 of the textbook ["Introduction to Programming with Java: A Problem Solving Approach"](https://www.mheducation.com/highered/product/introduction-programming-java-problem-solving-approach-dean-dean/M9781259875762.html).

The application simulates flipping a number of coins (e.g. 10) a given number of times (e.g. 1,000,000). Each coin flip results in some combination of heads and tails - anywhere from no heads to all heads.  Over 1,000,000 flips, some finite number of flips with 0 heads will occur, some finite number with 10 heads will occur, and others with 1, 2, 3, 4, 5, 6, 7, 8, and 9 heads will also occur.  The program displays the number of heads that occur over all flips as a histogram and finally prints out the amount of time it took to simulate all the coin flips.

A sample output for 10 coins flipped 1,000,000 times might look like this:

```text
Number of times each head count occurred in 1000000 flips of 10 coins:
 0  1038  
 1  9710  *
 2  43957  ****
 3  117606  ************
 4  204795  ********************
 5  246025  *************************
 6  204986  ********************
 7  117218  ************
 8  43843  ****
 9  9871  *
 10  951  
Coin Flipper Time: 195ms
```

Run the Java program on your workstation about 10 times.  You will have to run it repeatedly to get a good feeling for the average time of execution.  Record the times it takes to execute.  For capturing results, have the program flip 10 coins 1,000,000 times.

The Java program uses the random number generator from the Math class to randomly generate heads or tails for each coin's flip, so the results will vary each time the program executes.

The Java program also uses the ```System.currentTimeMillis()``` method to compute the amount of time to simulate the coin flips.

The Java example is written such that the number of coins and number of flips appear in a histogram that is written to ```System.out```.  As with any Java application, there is a main class (CoinFlipper) containing a ```main()``` method along with a constructor and various worker methods.

For this project, you need to translate the Java application to equivalent JavaScript.  In converting the application, you'll have to make some adaptations:

- Looping and conditional statements are similar between the two languages
- Function declarations in JavaScript and method declarations in Java are different and will need to be 'translated'
- You are ***not*** required to use JavaScript classes
- You will have to figure out how to generate random numbers.  The JavaScript core API includes a Math object that is similar to Java's Math class (see [JS Math Random](https://www.w3schools.com/js/js_random.asp))
- You will have to figure out how to determine the amount of time the simulation took.  The JavaScript core API includes a Performance class for sampling timings (see [JS Performance Class](https://developer.mozilla.org/en-US/docs/Web/API/Performance/now))
- You will have to replace the Java code that uses System.out.print with equivalent JavaScript calls to the console object (see [JS console.log](https://www.w3schools.com/Jsref/met_console_log.asp))
- You will have to replace the Java code that uses the Scanner with equivalent JavaScript calls to the console object (see [JS prompt](https://www.w3schools.com/jsref/met_win_prompt.asp))

### Getting Started

Download the [CoinFlipper.html](CoinFlipper.html) and [CoinFlipper.js](CoinFlipper.js) files and import them into a WebStorm project.  These two files contain code to get you started with your Java to JavaScript translation.

You must implement your JavaScript in the CoinFlipper.js file.  For this lab, translate the Java functions into JavaScript directly.  You are welcome to create additional 'helper' functions as needed.  Your final JavaScript should have the following functions at a minimum:

- ```run``` - the entry point for the simulation
- ```flipCoins``` - simulates the flipping of coins a number of times
- ```flipCoinsOneTime``` - simulates a single flipping of the coins
- ```printHistogram``` - prints the histogram

The above JavaScript functions should implement the same functionality as their corresponding Java functions.

The ```run``` function should also clear the debugging console of the browser (it is not automatically cleared), and reinitialize all variables and arrays (test running your solution multiple times to make sure everything is initialized correctly with each run).

When your application is working correctly, it should generate output in the JavaScript console similar to the following:

```text
Number of times each head count occurred in 30 flips of 8 coins:
0 0 
1 0 
2 3 **********
3 6 ********************
4 7 ***********************
5 7 ***********************
6 5 *****************
7 2 *******
8 0 
Coin Flipper Time: ??? ms
```

Here's another example:

```text
Number of times each head count occurred in 1000000 flips of 10 coins:
0 991 
1 9681 *
2 44048 ****
3 117339 ************
4 205143 *********************
5 246452 *************************
6 204831 ********************
7 117267 ************
8 43817 ****
9 9461 *
10 970 
Coin Flipper Time: ??? ms
```

Of course, your implementation will output the actual time in place of the "???" above.

NOTE: that ```console.log``` adds a new line automatically by default.  You will need to figure out a way to translate the behavior of ```System.print``` (which does not print a newline).

## Development Requirements

- You will need to validate user input (0 coins, 0 flips, negative numbers, other characters that aren't numbers).  For incorrect input send a message to the user using an [alert box](https://www.w3schools.com/jsref/met_win_alert.asp) then quit without flipping any coins
  - The input ranges for coins and flips is also limited; make sure to give an appropriate error message for values outside the range
  - The number of coins must be between 1 and 10 (inclusive) - (e.g. 1 and 10 are valid inputs as well as any integer in between)
  - The number of flips must be between 1 and 1000000 (inclusive)
- Within the run function, do ***NOT*** time the code that generates the histogram (it takes a LONG time to do console I/O compared to the time required for mathematical computations).
- Run the application in at least 2 browsers, for instance: Chrome & Firefox, Chrome and Edge, etc. You may also use other browsers (e.g. Opera, Safari) if you have them.
- Your results, including the elapsed time, will vary - you will have run the application several times to get a good feel for the average execution time for each browser.
- Running your JavaScript application with the debugger open can also have significant affects on the timing.  Make sure you close your debug window prior to loading the page.  Then open it after the CoinFlipper finishes to see the output.
- For capturing timing results, flip 10 coins 1,000,000 times.  However, you should also repeatedly test your implementation using other input (e.g. flip 1 coin 1 time, 10 coins 1 time, etc.) to make sure the results are correct.

Capture a single console output containing the times it takes to execute the JavaScript version of the application on each browser and include the output in your report (see deliverables).

## Helpful Hint

You are required to create a helpful error message for each type of input error. 

- The input must contain some text (e.g. not blank)
- Input values must be a positive integer (e.g. greater than 0, not negative, not a floating point number, should not contain characters)
- Input values must be inside the allowed range(s)
  - 1 to 10 (inclusive) for number of coins 
  - 1 to 1000000 (inclusive) for number of flips

TIP: How do I check for input text that is not a number?  Use the ```isNaN``` function 

TIP: How do I check for an integer input?  You can use a trick using the ```isInteger``` function combined with the ```parseFloat``` function.

Putting it all together you get:

```javascript
const isInputAnInteger = (value) => {
    // Make sure the input string is a number
    if(isNaN(value)) {
        return false;
    }
    // We now know the string contains a number, but is it an integer?
    // Parse the string to a float (decimal with precision) and then verify that it is an integer
    if(!Number.isInteger(parseFloat(value))) {
        return false;
    }
    // The input string is a number and an integer
    return true;
}
```

## Deliverables

Include all HTML and JS file(s) in your submission.  Make sure your name, lab name, and section number are in comments on ALL HTML and JS file(s).

ALSO, include a text file report containing:

- Introduction - a description of the lab in your own words
- Analysis - a description of your experimental results
  - Was JavaScript faster or slower than Java? Why do you think this is the case? 
  - What browsers did you use in your evaluation?  Which one was the fastest, slowest?
  - Research your browsers JavaScript execution engine to determine why you got those execution speeds? Do not forget to cite your resources. 
- Summary - a reflection of what you learned in this lab 
- Suggestions - a list of suggestions for improvement and/or what you enjoyed about this lab

Make sure your JavaScript code is commented thoroughly.  Create a zip file of all files and submit to Canvas before the due date.

NOTE: do NOT include any WebStorm specific files (e.g. your .idea directory).  Only submit the files as specified.

NOTE: If/when using resources from material outside what was presented in class (e.g., Google search, Stack Overflow, etc.) document the resource used in your submission.  Include exact URLs for web pages where appropriate.

Create a zip file of all files and submit before the due date.

## Grading Criteria

- (25 Points) Report
    - (5 Points) Introduction - a description of the lab in your own words
    - (10 Points) Experimental Results - Observations and explanation of results
    - (5 Points) Summary - a reflection of what you learned in this lab
    - (5 Points) Suggestions - a list of suggestions for improvement and/or what you enjoyed about this lab
- (5 Points) Correct Submission - Followed submission instructions (e.g. IDE project files are not submitted)
- (10 Points) Code Structure - Correct code/file structure - implementation of functions as described
- (25 Points) Functionality - Correct implementation of required functionality
- (20 Points) Error Checking - Comprehensive error checking for "bad" input (0, negative, or alphabetic input values must not be allowed)