## Table of Contents

### Introduction - Section Duration: 11 minutes
---
- [
    
    ![Introduction](https://static.frontendmasters.com/thumb/savage-a/2025/11/03/1-90.jpg)](https://frontendmasters.com/courses/getting-started-javascript-v3/introduction/)
    
    ### [Introduction](https://frontendmasters.com/courses/getting-started-javascript-v3/introduction/)
    
    [00:00:00 - 00:11:10](https://frontendmasters.com/courses/getting-started-javascript-v3/introduction/)
    
    Kyle will be conducting a workshop on getting started with JavaScript, aiming to simplify complex topics and help participants build applications confidently. He highlights the challenges of learning JavaScript due to its constant evolution and abundance of information, emphasizing the importance of hands-on practice. Kyle recommends tools like a web browser, Node.js, and Visual Studio Code, along with extensions like Live Server and Prettier to enhance the development experience. The workshop focuses on beginner concepts to empower learners to write applications and debug effectively in JavaScript.
    

### Running JavaScript

Section Duration: 20 minutes

- [
    
    ![Running Your First JavaScript Code](https://static.frontendmasters.com/thumb/savage-a/2025/11/03/2-90.jpg)](https://frontendmasters.com/courses/getting-started-javascript-v3/running-your-first-javascript-code/)
    
    ### [Running Your First JavaScript Code](https://frontendmasters.com/courses/getting-started-javascript-v3/running-your-first-javascript-code/)
    
    [00:11:11 - 00:22:13](https://frontendmasters.com/courses/getting-started-javascript-v3/running-your-first-javascript-code/)
    
    Kyle explains that JavaScript is commonly used for web development, running on both the front end (browser) and back end (server) to make sites interactive and handle behind-the-scenes processes like payments. Less common uses include desktop and mobile applications, with frameworks like Electron and React Native/Ionic enabling JavaScript usage. JavaScript is a scripting language that is interpreted, dynamic, and high-level, making it easier to work with for web development tasks. Kyle also provides guidance on setting up VS code, running JavaScript in the browser or Node.js, and using comments for code documentation.
    
- [
    
    ![Loading JavaScript in the Browser](https://static.frontendmasters.com/thumb/savage-a/2025/11/03/3-90.jpg)](https://frontendmasters.com/courses/getting-started-javascript-v3/loading-javascript-in-the-browser/)
    
    ### [Loading JavaScript in the Browser](https://frontendmasters.com/courses/getting-started-javascript-v3/loading-javascript-in-the-browser/)
    
    [00:22:14 - 00:31:34](https://frontendmasters.com/courses/getting-started-javascript-v3/loading-javascript-in-the-browser/)
    
    Kyle explains how JavaScript is loaded in a browser. Initially, the browser downloads the HTML file, then parses it to build the Document Object Model (DOM) representing the site's structure. When encountering a script tag, the browser pauses HTML parsing to download and execute the JavaScript, impacting website loading speed. Kyle discusses methods like async and defer attributes to optimize JavaScript loading, highlighting defer as a preferred choice for predictable execution order and efficient parallel downloading without interrupting HTML parsing.
    

### Variables, Functions, & Scope

Section Duration: 1 hour, 25 minutes

- [
    
    ![Primitive Types & Operations](https://static.frontendmasters.com/thumb/savage-a/2025/11/03/4-90.jpg)](https://frontendmasters.com/courses/getting-started-javascript-v3/primitive-types-operations/)
    
    ### [Primitive Types & Operations](https://frontendmasters.com/courses/getting-started-javascript-v3/primitive-types-operations/)
    
    [00:31:35 - 00:42:06](https://frontendmasters.com/courses/getting-started-javascript-v3/primitive-types-operations/)
    
    Kyle has covered the basics of JavaScript types, focusing on numbers, strings, and Booleans as the main primitive types. He explained how to work with these types, including operations like addition for numbers, concatenation for strings, and logical operations like AND and OR for Booleans. Kyle also discussed comparisons between different types and demonstrated how to determine the type of a variable using the type of keyword.
    
- ![Variables](https://static.frontendmasters.com/thumb/savage-a/2025/11/03/5.2-90.jpg)
    
    ### [Variables](https://frontendmasters.com/courses/getting-started-javascript-v3/variables/)
    
    [00:42:07 - 00:53:08](https://frontendmasters.com/courses/getting-started-javascript-v3/variables/)
    
    Kyle explained the concept of variables in JavaScript, comparing them to labeled boxes that store values. He demonstrated creating variables using the "let" keyword, updating variable values, and discussed naming conventions. Kyle also introduced "const" for creating variables that don't change, highlighted the differences between "null" and "undefined" for representing nothing, and shared best practices for using them. Additionally, he provided insights on when to use "let" versus "const" based on personal preference and common industry standards.
    
- ![Functions](https://static.frontendmasters.com/thumb/savage-a/2025/11/03/6-90.jpg)
    
    ### [Functions](https://frontendmasters.com/courses/getting-started-javascript-v3/functions/)
    
    [00:53:09 - 01:06:06](https://frontendmasters.com/courses/getting-started-javascript-v3/functions/)
    
    Kyle discussed the basics of defining variables in JavaScript and introduced the concept of functions as a way to store and reuse logic. Functions help avoid repetitive code by encapsulating logic in a single place, making it easier to maintain and update. He demonstrated how to create functions, pass parameters, return values, and highlighted common errors to watch out for when working with functions.
    
- ![Passing Functions as Variables](https://static.frontendmasters.com/thumb/savage-a/2025/11/03/7-90.jpg)
    
    ### [Passing Functions as Variables](https://frontendmasters.com/courses/getting-started-javascript-v3/passing-functions-as-variables/)
    
    [01:06:07 - 01:11:56](https://frontendmasters.com/courses/getting-started-javascript-v3/passing-functions-as-variables/)
    
    Kyle explains the concept of passing functions to other functions in JavaScript, highlighting that functions are a special type of variable that can be passed around like any other variable. He demonstrates how functions can be stored and called within other functions, emphasizing the importance of not using parentheses when passing a function to be used later. Kyle also clarifies common mistakes, such as accidentally calling the function instead of passing it along, and introduces the term "callback" for this common practice in programming.
    
- ![Function Callbacks Exercise](https://static.frontendmasters.com/thumb/savage-a/2025/11/03/8-90.jpg)
    
    ### [Function Callbacks Exercise](https://frontendmasters.com/courses/getting-started-javascript-v3/function-callbacks-exercise/)
    
    [01:11:57 - 01:16:15](https://frontendmasters.com/courses/getting-started-javascript-v3/function-callbacks-exercise/)
    
    Kyle explains the concept of callbacks in JavaScript, highlighting how they add flexibility by allowing the same function to perform different actions based on the callback function passed to it. He provides a practice exercise involving creating functions that utilize callbacks to manipulate data. Kyle demonstrates the solution, emphasizing how callbacks work by passing and returning values within functions, and clarifies that "callback" is not a reserved word in JavaScript.
    
- ![Arrow Functions](https://static.frontendmasters.com/thumb/savage-a/2025/11/03/9-90.jpg)
    
    ### [Arrow Functions](https://frontendmasters.com/courses/getting-started-javascript-v3/arrow-functions/)
    
    [01:16:16 - 01:27:02](https://frontendmasters.com/courses/getting-started-javascript-v3/arrow-functions/)
    
    Kyle explains the concept of arrow functions in JavaScript as an alternative way to define functions. He demonstrates how to convert a normal function to an arrow function by replacing the function keyword with const, using parameters, and the arrow syntax. Kyle also highlights unique features of arrow functions, such as optional parentheses for single parameters and single-line return shortcuts, emphasizing their use in passing functions as callbacks. Additionally, he discusses common mistakes and personal preferences in choosing between arrow functions and normal functions based on simplicity and code readability.
    
- ![Scope](https://static.frontendmasters.com/thumb/savage-a/2025/11/03/10-90.jpg)
    
    ### [Scope](https://frontendmasters.com/courses/getting-started-javascript-v3/scope/)
    
    [01:27:03 - 01:41:37](https://frontendmasters.com/courses/getting-started-javascript-v3/scope/)
    
    Kyle explains the concept of scope in JavaScript, which determines the accessibility of variables and functions in code. He demonstrates how JavaScript uses scope to prioritize variables with the same name based on their location within different scopes. Kyle covers global scope, function scope, and block scope, emphasizing the importance of minimizing global variables to avoid confusion and potential conflicts. He also discusses how modules in JavaScript can help manage variable scope across different files and environments like the browser and Node.js.
    
- ![Hoisting](https://static.frontendmasters.com/thumb/savage-a/2025/11/03/11-90.jpg)
    
    ### [Hoisting](https://frontendmasters.com/courses/getting-started-javascript-v3/hoisting/)
    
    [01:41:38 - 01:48:35](https://frontendmasters.com/courses/getting-started-javascript-v3/hoisting/)
    
    Kyle introduces the concept of hoisting in JavaScript, explaining how functions are hoisted to the top of the scope, allowing them to be used before they are defined in the code. He discusses how hoisting makes code more flexible by enabling important functions to be placed at the top for easier readability, while less crucial details can be placed at the bottom. Kyle also clarifies that arrow functions, being defined with const or let, do not get hoisted like traditional functions, providing insight into the rationale behind this design decision.
    
- ![Closures](https://static.frontendmasters.com/thumb/savage-a/2025/11/03/12-90.jpg)
    
    ### [Closures](https://frontendmasters.com/courses/getting-started-javascript-v3/closures/)
    
    [01:48:36 - 01:57:37](https://frontendmasters.com/courses/getting-started-javascript-v3/closures/)
    
    Kyle introduces the concept of closures in JavaScript, explaining how they work by demonstrating examples of functions accessing variables outside their scope. He discusses the idea of closures keeping track of dynamic variables and accessing outer scope variables, emphasizing how closures allow functions to remember values even after the outer function has finished executing. Kyle then walks through a practical example of nested functions, showcasing how inner functions retain access to variables from their outer scope, ultimately highlighting closures as a fundamental aspect of how functions interact with scope in JavaScript.
    

### Advanced Variables

Section Duration: 1 hour, 4 minutes

- ![Creating Variables with var](https://static.frontendmasters.com/thumb/savage-a/2025/11/03/13-90.jpg)
    
    ### [Creating Variables with var](https://frontendmasters.com/courses/getting-started-javascript-v3/creating-variables-with-var/)
    
    [01:57:38 - 02:02:21](https://frontendmasters.com/courses/getting-started-javascript-v3/creating-variables-with-var/)
    
    Kyle explains the differences between the var keyword and let/const in JavaScript. He highlights that var uses function scope, gets hoisted, and allows variable redeclaration without throwing errors, making it confusing and less preferred compared to let and const. Kyle advises against using var in modern code and suggests understanding it for encountering older codebases or tricky interview questions.
    
- ![Type Coercion](https://static.frontendmasters.com/thumb/savage-a/2025/11/03/14-90.jpg)
    
    ### [Type Coercion](https://frontendmasters.com/courses/getting-started-javascript-v3/type-coercion/)
    
    [02:02:22 - 02:09:08](https://frontendmasters.com/courses/getting-started-javascript-v3/type-coercion/)
    
    Kyle discussed type coercion in JavaScript, where variables can be converted from one type to another. Type coercion can be explicit, where the programmer specifies the conversion using functions like parseInt or parseFloat, or implicit, where JavaScript automatically converts types during operations like addition. Kyle emphasized the importance of understanding and controlling type conversions to avoid unexpected behaviors in code.
    
- ![NaN: Not a Number](https://static.frontendmasters.com/thumb/savage-a/2025/11/03/15-90.jpg)
    
    ### [NaN: Not a Number](https://frontendmasters.com/courses/getting-started-javascript-v3/nan-not-a-number/)
    
    [02:09:09 - 02:11:38](https://frontendmasters.com/courses/getting-started-javascript-v3/nan-not-a-number/)
    
    Kyle explains the concept of "not a number" (N-A-N) in JavaScript, which is returned when trying to convert a non-numeric string to a number using parseInt. He clarifies that NaN is a special reserved keyword in JavaScript, representing a value that cannot be converted to a number. Kyle also discusses the confusion around NaN, including how NaN is of type number, but comparisons with NaN always return false, necessitating the use of the isNAN function to check for NaN. Additionally, Kyle touches on implicit type coercion in JavaScript, highlighting the differences between using double equals (==) and triple equals (===) for equality checks, emphasizing how JavaScript automatically coerces types with double equals.
    
- ![Equality Type Comparison](https://static.frontendmasters.com/thumb/savage-a/2025/11/03/16-90.jpg)
    
    ### [Equality Type Comparison](https://frontendmasters.com/courses/getting-started-javascript-v3/equality-type-comparison/)
    
    [02:11:39 - 02:17:53](https://frontendmasters.com/courses/getting-started-javascript-v3/equality-type-comparison/)
    
    Kyle explains the difference between double equals (==) and triple equals (===) in JavaScript. Double equals performs type coercion, converting values to the same type before comparison, while triple equals strictly checks both value and type. Kyle recommends using triple equals for strict comparisons to avoid confusion caused by automatic type coercion, except when comparing null and undefined where double equals can be used to check for either value.
    
- ![Arrays](https://static.frontendmasters.com/thumb/savage-a/2025/11/03/17-90.jpg)
    
    ### [Arrays](https://frontendmasters.com/courses/getting-started-javascript-v3/arrays/)
    
    [02:17:54 - 02:27:48](https://frontendmasters.com/courses/getting-started-javascript-v3/arrays/)
    
    Kyle explains the concept of arrays in JavaScript, which allow storing multiple values in a single variable. Arrays are created using square brackets and can hold various data types. He demonstrates creating, accessing, and modifying arrays, including adding elements using the push method and accessing elements based on zero-based indexing. Kyle also discusses nested arrays, array length, and provides a practical example to reinforce understanding.
    
- ![Objects](https://static.frontendmasters.com/thumb/savage-a/2025/11/03/18-90.jpg)
    
    ### [Objects](https://frontendmasters.com/courses/getting-started-javascript-v3/objects/)
    
    [02:27:49 - 02:38:24](https://frontendmasters.com/courses/getting-started-javascript-v3/objects/)
    
    Kyle explains the concept of objects in JavaScript, highlighting how they store related data using key-value pairs. Objects are created using curly brackets and properties are accessed using dot notation. Kyle also demonstrates nesting objects and arrays within objects, and adding functions to objects. He emphasizes the importance of understanding and practicing object creation in JavaScript.
    
- ![Reference vs Value](https://static.frontendmasters.com/thumb/savage-a/2025/11/03/19-90.jpg)
    
    ### [Reference vs Value](https://frontendmasters.com/courses/getting-started-javascript-v3/reference-vs-value/)
    
    [02:38:25 - 02:47:38](https://frontendmasters.com/courses/getting-started-javascript-v3/reference-vs-value/)
    
    Kyle explains the concept of reference versus value in JavaScript. He clarifies that value types, like primitive types, store actual values, while reference types, like arrays and objects, store references to memory locations. He uses an analogy of hotel rooms to illustrate how copying variables works differently for value and reference types, emphasizing that changing a reference type affects all variables pointing to the same memory location. Kyle also discusses how const works with reference types, highlighting that it prevents reassigning the variable but allows modifying the content within the memory location it references.
    
- ![String Template Literals](https://static.frontendmasters.com/thumb/savage-a/2025/11/03/20-90.jpg)
    
    ### [String Template Literals](https://frontendmasters.com/courses/getting-started-javascript-v3/string-template-literals/)
    
    [02:47:39 - 02:52:06](https://frontendmasters.com/courses/getting-started-javascript-v3/string-template-literals/)
    
    Kyle explains the use of backticks as an alternative way to create strings in JavaScript, allowing for easier embedding of variables using string template literals. He demonstrates how to use backticks to define strings with dynamic variables and execute JavaScript code within them. Additionally, Kyle touches on the importance of understanding the `this` and `new` keywords in JavaScript, providing a surface-level explanation of their significance in real-world JavaScript applications.
    
- ![this Keyword & Classes](https://static.frontendmasters.com/thumb/savage-a/2025/11/03/21-90.jpg)
    
    ### [this Keyword & Classes](https://frontendmasters.com/courses/getting-started-javascript-v3/this-keyword-classes/)
    
    [02:52:07 - 03:02:19](https://frontendmasters.com/courses/getting-started-javascript-v3/this-keyword-classes/)
    
    Kyle explains the concept of the "this" keyword in JavaScript, highlighting its different meanings based on context, such as referencing the global object in the browser or specific properties within objects. He then introduces classes in JavaScript, demonstrating how to create a class resembling an object structure, including the use of constructors and the "new" keyword to instantiate objects. Kyle emphasizes the convention of capitalizing class names and briefly touches on the utility of classes in JavaScript programming.
    

### Conditions & Loops

Section Duration: 1 hour, 5 minutes

- ![If Statements](https://static.frontendmasters.com/thumb/savage-a/2025/11/03/22-90.jpg)
    
    ### [If Statements](https://frontendmasters.com/courses/getting-started-javascript-v3/if-statements/)
    
    [03:02:20 - 03:14:35](https://frontendmasters.com/courses/getting-started-javascript-v3/if-statements/)
    
    Kyle explained the concept of control flow in JavaScript, focusing on if statements to conditionally run code based on true or false conditions. He demonstrated how to use if, if-else, and else if statements to control program flow based on different conditions. Kyle also discussed combining conditions with logical operators like AND, OR, and NOT, and provided examples of nested if statements and guard clauses as alternatives to improve code readability. Additionally, he highlighted the use of single-line if statements and guided through a practical exercise to practice writing if statements to check for driver's license eligibility based on age and completion of driver's education.
    
- ![Ternary Operator](https://static.frontendmasters.com/thumb/savage-a/2025/11/03/23-90.jpg)
    
    ### [Ternary Operator](https://frontendmasters.com/courses/getting-started-javascript-v3/ternary-operator/)
    
    [03:14:36 - 03:18:54](https://frontendmasters.com/courses/getting-started-javascript-v3/ternary-operator/)
    
    Kyle discusses ternary operators as a condensed way to write simple if-else checks in JavaScript. Ternary operators consist of a question mark and a colon symbol, representing the true and false outcomes, respectively. He emphasizes that ternaries return a value based on the condition, making them useful for simple conditions with two outputs, but advises against chaining them excessively for code readability.
    
- ![Switch Statements](https://static.frontendmasters.com/thumb/savage-a/2025/11/03/24-90.jpg)
    
    ### [Switch Statements](https://frontendmasters.com/courses/getting-started-javascript-v3/switch-statements/)
    
    [03:18:55 - 03:28:20](https://frontendmasters.com/courses/getting-started-javascript-v3/switch-statements/)
    
    Kyle explains the concept and implementation of switch statements in JavaScript as an alternative to complex if-else conditions. He demonstrates how to structure a switch statement, handle cases, use the break keyword, and provides examples comparing switch statements to if-else statements. Kyle emphasizes the importance of including break statements to control the flow of execution within switch cases and highlights potential issues with variable scoping in switch statements.
    
- ![For Loops](https://static.frontendmasters.com/thumb/savage-a/2025/11/03/25-90.jpg)
    
    ### [For Loops](https://frontendmasters.com/courses/getting-started-javascript-v3/for-loops/)
    
    [03:28:21 - 03:39:12](https://frontendmasters.com/courses/getting-started-javascript-v3/for-loops/)
    
    Kyle explains the concept of for loops in JavaScript, detailing the syntax and components of a for loop, including the variable, condition, and update sections. He demonstrates how to loop through arrays using for loops and discusses nesting for loops, early exit with break, and skipping iterations with continue. Kyle also introduces alternatives like for of loops for arrays and for in loops for objects, highlighting common mistakes such as infinite loops and off by one errors. Finally, he provides an exercise to create an array of even numbers and calculate their sum using separate for loops.
    
- ![While Loops](https://static.frontendmasters.com/thumb/savage-a/2025/11/03/26-90.jpg)
    
    ### [While Loops](https://frontendmasters.com/courses/getting-started-javascript-v3/while-loops/)
    
    [03:39:13 - 03:44:36](https://frontendmasters.com/courses/getting-started-javascript-v3/while-loops/)
    
    Kyle explains the concept of while loops in JavaScript, highlighting that while loops run until a specified condition becomes false, making them suitable for situations where the number of iterations is unknown. He contrasts while loops with for loops, emphasizing that while loops are preferred for scenarios like user input handling or nested data structures where the endpoint is uncertain. Kyle also briefly mentions the less commonly used do while loop, which always executes the loop code at least once before checking the condition.
    
- ![Recursion](https://static.frontendmasters.com/thumb/savage-a/2025/11/03/27-90.jpg)
    
    ### [Recursion](https://frontendmasters.com/courses/getting-started-javascript-v3/recursion/)
    
    [03:44:37 - 03:53:45](https://frontendmasters.com/courses/getting-started-javascript-v3/recursion/)
    
    Kyle introduces the concept of recursion, explaining how a function can call itself and demonstrates with an example of a function called print numbers. He walks through the code, showing how the function recursively prints numbers from one to ten, emphasizing the importance of having a base case to prevent infinite loops. Kyle then discusses the use of recursion in solving problems with tree-like structures, highlighting that recursion, for loops, and while loops can all be used interchangeably based on preference and problem complexity.
    
- ![Short Circuit Evaluation](https://static.frontendmasters.com/thumb/savage-a/2025/11/03/28-90.jpg)
    
    ### [Short Circuit Evaluation](https://frontendmasters.com/courses/getting-started-javascript-v3/short-circuit-evaluation/)
    
    [03:53:46 - 04:00:27](https://frontendmasters.com/courses/getting-started-javascript-v3/short-circuit-evaluation/)
    
    Kyle introduces the concept of short circuit evaluation in JavaScript, explaining how the AND and OR operators work. He demonstrates how JavaScript skips evaluating the second operand if the result can be determined from the first operand, optimizing code execution. Kyle also discusses modern alternatives like nullish coalescing and optional chaining to handle default values and nested object properties more efficiently.
    
- ![Array Methods](https://static.frontendmasters.com/thumb/savage-a/2025/11/03/29-90.jpg)
    
    ### [Array Methods](https://frontendmasters.com/courses/getting-started-javascript-v3/array-methods/)
    
    [04:00:28 - 04:08:09](https://frontendmasters.com/courses/getting-started-javascript-v3/array-methods/)
    
    Kyle introduces various array methods to the students, explaining how they can be used to manipulate arrays efficiently. He discusses the forEach method, demonstrating how it loops through each value in an array and executes a callback function for each item. Kyle then moves on to explain the map method, showing how it transforms each value in an array to create a new array with updated values based on a specified transformation. Finally, he walks through the reduce method, illustrating how it accumulates values from an array by applying a specified function to each element, ultimately producing a single output.
    

### The DOM

Section Duration: 39 minutes

- ![Window and Document](https://static.frontendmasters.com/thumb/savage-a/2025/11/03/30-90.jpg)
    
    ### [Window and Document](https://frontendmasters.com/courses/getting-started-javascript-v3/window-and-document/)
    
    [04:08:10 - 04:11:32](https://frontendmasters.com/courses/getting-started-javascript-v3/window-and-document/)
    
    Kyle introduces the concept of the DOM, explaining that it stands for the Document Object Model used in JavaScript within the browser. He discusses the two fundamental objects in the browser, the window object, and the document object, highlighting their global accessibility and usage in JavaScript. Kyle demonstrates how global functions and variables are accessed through the window object, emphasizing that the window object serves as a massive global reference in the browser environment.
    
- ![Selecting Elements](https://static.frontendmasters.com/thumb/savage-a/2025/11/03/31-90.jpg)
    
    ### [Selecting Elements](https://frontendmasters.com/courses/getting-started-javascript-v3/selecting-elements/)
    
    [04:11:33 - 04:21:12](https://frontendmasters.com/courses/getting-started-javascript-v3/selecting-elements/)
    
    Kyle introduces different methods to retrieve specific elements in JavaScript. He explains how getElementByID returns a single element based on its ID, while getElementsByClassName retrieves multiple elements with a specific class. He then discusses the advantages of using querySelector and querySelectorAll, which allow for more flexible CSS selector usage to obtain single or multiple elements.
    
- ![Event Listeners](https://static.frontendmasters.com/thumb/savage-a/2025/11/03/32-90.jpg)
    
    ### [Event Listeners](https://frontendmasters.com/courses/getting-started-javascript-v3/event-listeners/)
    
    [04:21:13 - 04:34:14](https://frontendmasters.com/courses/getting-started-javascript-v3/event-listeners/)
    
    Kyle introduces event listeners as a core concept in DOM manipulation, explaining how they make web pages interactive by allowing code to run based on user actions like clicking buttons or typing in input fields. He demonstrates adding a click event listener to a button, showing how multiple event listeners can be added without overwriting each other, and then discusses the process of removing event listeners, emphasizing the importance of passing a reference to a function for successful removal. Finally, he explores the event object passed to event listeners, highlighting properties like e.target and e.current target to differentiate between the element interacted with and the element being listened to.
    
- ![Event Delegation](https://static.frontendmasters.com/thumb/savage-a/2025/11/03/33-90.jpg)
    
    ### [Event Delegation](https://frontendmasters.com/courses/getting-started-javascript-v3/event-delegation/)
    
    [04:34:15 - 04:40:15](https://frontendmasters.com/courses/getting-started-javascript-v3/event-delegation/)
    
    Kyle introduces the concept of event delegation in JavaScript, explaining how events flow through the DOM. He demonstrates with a simple HTML example, showing how clicking on one element triggers events on multiple nested elements. Kyle then discusses the three-step process of event propagation - capture, target, and bubble phases - and illustrates how to manipulate this behavior using stop propagation and capture phase.
    
- ![DOM Traversal](https://static.frontendmasters.com/thumb/savage-a/2025/11/03/34-90.jpg)
    
    ### [DOM Traversal](https://frontendmasters.com/courses/getting-started-javascript-v3/dom-traversal/)
    
    [04:40:16 - 04:47:36](https://frontendmasters.com/courses/getting-started-javascript-v3/dom-traversal/)
    
    Kyle introduces DOM traversal in the lesson. He explains how to move around the DOM structure using concepts like parent elements, children, and siblings. He demonstrates how to use methods like querySelector, next/previous element sibling, and closest to efficiently navigate through the DOM tree. Kyle emphasizes the importance of using flexible methods like closest and querySelector over parent element and children for more robust code that adapts to changes in the HTML structure.
    

### Debugging

Section Duration: 50 minutes

- ![Common JavaScript Errors](https://static.frontendmasters.com/thumb/savage-a/2025/11/03/35-90.jpg)
    
    ### [Common JavaScript Errors](https://frontendmasters.com/courses/getting-started-javascript-v3/common-javascript-errors/)
    
    [04:47:37 - 04:59:22](https://frontendmasters.com/courses/getting-started-javascript-v3/common-javascript-errors/)
    
    Kyle introduces the concept of debugging in JavaScript, explaining the three main types of errors: syntax errors, runtime errors, and logical errors. He discusses how syntax errors are the easiest to find, often indicated by red squiggly lines in the code editor, while runtime errors occur when code crashes during execution, and logical errors result in code running without errors but not producing the expected outcome. Kyle then demonstrates how to interpret error messages, breaking down the components such as error type, message, and stack trace to effectively locate and resolve bugs in the code.
    
- ![Browser Developer Tools](https://static.frontendmasters.com/thumb/savage-a/2025/11/03/36-90.jpg)
    
    ### [Browser Developer Tools](https://frontendmasters.com/courses/getting-started-javascript-v3/browser-developer-tools/)
    
    [04:59:23 - 05:09:20](https://frontendmasters.com/courses/getting-started-javascript-v3/browser-developer-tools/)
    
    Kyle introduces the various panels available in the browser developer tools, explaining their functions and how to access them. He walks through the elements, console, network, application, sources, and performance tabs, detailing their purposes and demonstrating how to utilize them effectively. Kyle also provides tips on navigating the tools, such as selecting elements on the page, toggling between mobile and non-mobile views, and customizing the layout of the developer tools for optimal usage.
    
- ![Debugging with the Console](https://static.frontendmasters.com/thumb/savage-a/2025/11/03/37-90.jpg)
    
    ### [Debugging with the Console](https://frontendmasters.com/courses/getting-started-javascript-v3/debugging-with-the-console/)
    
    [05:09:21 - 05:18:06](https://frontendmasters.com/courses/getting-started-javascript-v3/debugging-with-the-console/)
    
    Kyle introduces advanced console debugging techniques to the students. He explains the different levels of logging available, such as errors, warnings, debug information, and info. He demonstrates how to use console.group to organize logs into collapsible groups, console.table to display data in a table format, and console.assert for conditional error logging.
    
- ![Source Debugger](https://static.frontendmasters.com/thumb/savage-a/2025/11/03/38-90.jpg)
    
    ### [Source Debugger](https://frontendmasters.com/courses/getting-started-javascript-v3/source-debugger/)
    
    [05:18:07 - 05:32:19](https://frontendmasters.com/courses/getting-started-javascript-v3/source-debugger/)
    
    Kyle introduces the sources tab, explaining how it allows students to step through their code line by line for detailed debugging. He demonstrates adding breakpoints using both the debugger text and the debugger tool, showing how to manage and remove them. Kyle then discusses the importance of managing breakpoints and explains the options for handling errors within the code using checkboxes for uncaught and caught exceptions.
    
- ![VS Code Debugging](https://static.frontendmasters.com/thumb/savage-a/2025/11/03/39-90.jpg)
    
    ### [VS Code Debugging](https://frontendmasters.com/courses/getting-started-javascript-v3/vs-code-debugging/)
    
    [05:32:20 - 05:38:01](https://frontendmasters.com/courses/getting-started-javascript-v3/vs-code-debugging/)
    
    Kyle introduces the process of setting up debugging directly inside VS Code, explaining the steps to create a launch.json file and configure it for debugging a web app using Chrome. He demonstrates how to run the application, pause at breakpoints, inspect variables, and manipulate the call stack, providing a seamless debugging experience within VS Code. Kyle also discusses the similarities and differences between debugging in VS Code versus the browser, highlighting the convenience and personal preference involved in choosing the preferred debugging environment.
    

### Wrapping Up

Section Duration:

- ![Wrapping Up](https://static.frontendmasters.com/thumb/savage-a/2025/11/03/40-90.jpg)
    
    ### [Wrapping Up](https://frontendmasters.com/courses/getting-started-javascript-v3/wrapping-up/)
    
    [05:38:02 - 05:38:58](https://frontendmasters.com/courses/getting-started-javascript-v3/wrapping-up/)
    
    Kyle introduces the importance of revisiting challenging sections and rewatching videos to deepen understanding. He emphasizes the value of actively engaging with the code by writing it out, playing around with it, and experimenting to enhance learning. Kyle reassures students that feeling overwhelmed is normal given the rapid pace and complexity of the topics covered, but encourages them to persist and build confidence in their JavaScript skills.