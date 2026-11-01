## Table of Contents

### Introduction
---
[[01. Introduction]]
[[Course Overview]]
[[What is JavaScript]]
[[Where to Write JavaScript]]

### DOM
---
[[Document Object Model]]
[[Finding Elements in a Web Page]]
[[.length & .textContent]]
[[Finding Elements Exercise]]
[[Changing a Web Page]]
[[Changing a Web Page Exercise]]

### Values & Data Types - Section Duration: 57 minutes
---
[[Values & Data Types]]
[[Values & Data Types Exercise]]
[[Strings]]
[[indexOf]]
[[Working with Strings Exercise]]

### Operators - Section Duration: 27 minutes
---
[[Operators]]
[[Operators Exercise]]
[[Comparison & Equality Operators]]

### Expressions - Section Duration: 1 hour, 9 minutes
---
[[Expressions]]
[[Declaring & Assigning Variables]]
[[const & Accessing Variables]]
[[Variables Exercise]]
[[What are Variables?]]]
[[Evaluating Code]]
[[Statements vs Expressions]]

### Arrays - Section Duration: 1 hour, 2 minutes
---
[[Arrays]]
[[Useful Array Methods]]
[[Mutability]]
[[Mutable & Immutable Data Exercise]]
[[Immutable Variables & Values]]
[[Variables & Arrays]]

### Objects - Section Duration: 58 minutes
---
[[Objects & Property Access]]
[[Visualizing Object Access]]
[[Objects Exercise]]
[[Object Methods]]
[[Object Methods Exercise]]
[[Built-In Objects]]
[[Tic Tac Toe Demo]]

### Quiz Project - Section Duration: 34 minutes
---
[[JavaScript Pop Quiz & Project Setup]]
[[DOM Exercise]]
[[Declaring & Assigning a Variable]]
[[Setting Statement Element]]

### Quiz Project Functions - Section Duration: 1 hour, 41 minutes
---
[[Functions, Parameters, & Arguments]]
[[Function Return Values]]
[[Creating Functions Exercise]]
[[Arrow Functions]]
[[Arrow Functions Exercise]]
[[Quiz Project Functions Exercise]]
[[Quiz Project Disable & Enable Solution]]
[[Quiz Project isCorrect Solution]]
[[Boolean Q&A]]
[[Scope]]
[[let & Scope]]
[[var vs let]]

### Events & Handlers - Section Duration: 26 minutes
---
[[Event Listeners]]
[[Event Object]]
[[Events Exercise]]

### Conditionals - Section Duration: 1 hour, 10 minutes
---
[[Conditionals]]
[[Conditionals Exercise]]
[[Logical & Ternary Operators]]]
[[Loops]]
[[Explanation Loop Project Exercise]]
[[Disable Loop Project Exercise]]
[[isCorrect Project Exercise]]

### Map & Filter - Section Duration: 24 minutes
---
[[map & filter]]
[[map & filter Exercise]]
[[Spread]]

### Doggos Quiz Game - Section Duration: 50 minutes
---
[[Doggos Quiz Game Setup]]
[[while Loops]]
[[Doggo Quiz while Exercise]]
[[Doggo Quiz while Solution]]
[[Doggo Quiz while Review]]
[[setTimeout]]

### Data Fetching & Promises - Section Duration: 29 minutes
---
[[APIs & fetch]]
[[Working with Promises]]
[[Using Await with Promises]]

### Destructuring Data - Section Duration: 40 minutes
---
[[Destructuring Objects & Arrays]]
[[Destructuring Exercise]]
[[Destructuring Solution: Return Breed]]
[[Destructuring Solution: Format String]]

### Async - Section Duration: 33 minutes
---
[[Async Functions]]
[[Async Function Exercise]]
[[Adding Choice Buttons Exercise]]
[[Adding Choice Buttons Solution]]
[[Render Quiz Exercise]]

### Modules - Section Duration: 1 hour, 1 minute
---
[[Modules]]
[[Modules Q&A]]
[[Debugging]]
[[Browser Debugger]]
[[try catch Error Handling]]
[[Frameworks vs. Vanilla JavaScript]]

### Wrapping Up - Section Duration: 10 minutes
---
[[Wrapping Up]]

---
---

Here's the syllabus broken down, plus the 80/20 view on what actually carries you forward into frameworks and DSA.

### The course itself — what to really lock in

**1. Functions, scope, and arrow functions** (Quiz Project Functions section)  
This is the single highest-leverage block. Understanding parameters vs. arguments, return values, closures/scope (var vs let vs const, block vs function scope), and arrow function syntax is the foundation everything else — callbacks, React components, array methods — sits on top of. Don't rush this.

**2. Arrays + Map/Filter/Spread**  
`map`, `filter`, mutability vs immutability, and the spread operator are used constantly in real code and are the direct bridge into how React/Vue handle state (never mutate, always return new arrays/objects). This is arguably the most "professional JS" section in the whole course.

**3. Async: Promises, async/await, fetch** (Data Fetching & Promises, Async sections)  
This trips up almost everyone. The mental model of pending/fulfilled/rejected, why `await` is needed, and how async functions compose is a permanent pain point for beginners and a permanent requirement in real apps (API calls, loading states, error handling). Spend real time in the Doggos Quiz Game project — it's the course's best simulation of "real" JS work (loops + async + DOM all combined).

**4. Destructuring**  
Small syntax, huge frequency. You'll see this in every framework, every codebase, forever.

**5. DOM + Events**  
Foundational but lower-leverage long-term if you're heading toward frameworks, since React/Vue abstract the DOM away. Get comfortable, don't over-invest.

Lower priority to "get a hang of" vs. just understand: strings/operators basics, the console debugging segment, modules (important conceptually, but you'll relearn the practical side once you're in a bundler-based framework project anyway).