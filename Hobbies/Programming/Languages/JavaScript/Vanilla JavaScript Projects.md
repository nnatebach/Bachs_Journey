### The 80/20 of this course

**1. Closures + Higher-order functions** (Object Oriented Programming section)  
This is the concept that separates "knows JS syntax" from "understands JS." Closures explain how React hooks work, how event handlers keep state, how modules encapsulate data. If one lesson deserves a rewatch, it's this one.

**2. Classes, `extends`/`super`, and prototypes**  
You won't write much class-based code in modern React (hooks replaced that), but you'll see OOP everywhere in the wider JS ecosystem, and understanding prototypes demystifies _why_ JS behaves the way it does (this matters a lot for debugging later). Don't skip the prototype chain lesson even though it feels abstract — it pays off when weird bugs show up.

**3. The event loop + async timing**  
This course goes deeper than the first one (setTimeout/setInterval, why async code doesn't block). This is one of the most commonly misunderstood JS topics in interviews and in real debugging (race conditions, stale state in async callbacks). Worth truly internalizing, not just following along.

**4. The Selfie Cam + Meme Me projects (Vite, modules, npm, deployment)**  
This is the highest real-world-transfer part of the course. Vite, `npm install`, ES modules, ESLint/Prettier, GitHub Actions deployment — this is literally the exact toolchain you'll use on day one of any React/Vue project. Don't rush through this to get to "more JS" — this _is_ the professional workflow.

**5. Iterables/generators**  
Lower priority for you right now. Good to understand conceptually (`for...of`, iterator protocol) but you'll rarely hand-write a generator as a junior dev. Don't over-invest here.

### How this maps to what's next

- **Frameworks (React/Vue):** closures, higher-order functions, array methods (map/filter from course 1), and the Vite/npm/modules workflow are your direct prerequisites. OOP/classes matter less in React (hooks era) but matter more in Vue's older Options API and in Angular if you go there.
- **DSA:** the event loop and closures show up constantly in JS-specific interview questions (debounce/throttle implementations, memoization via closures). Beyond that, DSA is language-agnostic — arrays, objects, recursion, and Big-O thinking, which you can start layering in now using what you already know (arrays/objects from course 1) rather than waiting.