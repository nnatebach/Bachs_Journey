**1. "TypeScript Syntax: Variables & Functions"** (Language Fundamentals)  
This is the core: type annotations on variables, function params, and return types. Every `.ts`/`.tsx` file in spin-hobby will use this constantly — it's non-negotiable.

**2. "TypeScript Compiler Overview" + "tsc Inputs & Outputs"** (Configuring the Compiler)  
You don't need to master every compiler flag — but understanding that `tsconfig.json` controls strictness and what gets checked is essential, because spin-hobby already ships with `tsconfig.json` and `tsconfig.node.json`. You'll be reading those, not writing them from scratch.

**3. "TypeScript Concepts Recap" lesson**  
This single recap lesson is gold for your situation — Anjana explicitly summarizes unions, interfaces, and generics in one condensed pass. Interfaces especially: React prop types in this repo will almost certainly be defined via `interface Props { ... }`, so that one concept carries disproportionate weight.

**4. "Client Application TypeScript" section**  
This is the single most relevant section in the whole course — it's the part built for exactly your use case (a React client app). This is where you'll see typed props, typed state, and typed event handlers in context. If you only have time for one full section, this is it.

### The practical 20/80 translation

Variable/function typing + interfaces + reading (not writing) a tsconfig + the Client TS section ≈ maybe 3 of the 8 hours, and it covers the large majority of what you'll actually encounter opening spin-hobby's `src` folder. Everything else (generics depth, server TS, fullstack type-sharing) you can learn later, on demand, when a specific line of code forces the question.

### Schedule
1. __Day 1 AM: Watch, don't practice yet__
	- Go through the first two sections of the TypeScript course (Introduction + Language Fundamentals, ~2 hrs) at 1.25x speed.
	- Don't pause to perfect every example — just let the shape of 'JS + types' sink in. You already know the JS underneath, so this is recognition, not new learning.
    
2. __Day 1 PM: Type 5 things, nothing more__
	- Open a blank .ts file. Practice ONLY: typing a variable, typing a function's params/return, a union type, an interface, and an array type.
	- That's it — __five reps each, then stop__. This is your entire 'fundamentals' goal. Resist the urge to also learn generics or advanced types right now.
    
3. __Day 2 AM: Open the repo with zero pressure to understand it all__
	- Open spin-hobby's src folder. Your only job: find one small, already-working component file and read it top to bottom.
	- Don't try to understand the whole app's architecture — just that one file. Notice: props get typed, components are just functions, JSX looks like HTML. That's 90% of what 'React' means for reading code.
    
4. __Day 2 PM: Make one tiny change and run it__
	- Pick the smallest possible edit — change a text string, a color, a prop value. Run it with yarn start. Watch it work.
	- This single loop (edit → run → see result) is what kills panic, because it proves the setup works and you can touch the code without breaking everything.
    
5. __Ongoing: when stuck, narrow the question__
	Panic usually comes from 'I don't understand this whole file/concept.' The fix is always to _shrink the question_: not 'what does this component do' but 'what does this ONE line do.' _Ask that narrower question_ (to docs, to Claude, to a teammate) and move one line at a time.

### Spin Hobby specifically
Write them from memory, and peek back at the course only when you're stuck.

**Setup (2 minutes):** create `practice.ts` and run it with `npx tsx practice.ts`. Use `npx tsc practice.ts` if the course had you compile. To see errors, just watch your editor's red squiggles.

**The five reps** (use your own domain, like `Pet` or `Order`):

1. **Typed variables.** Declare a `string`, a `number`, and a `boolean` with explicit types (e.g. `petName`, `age`, `isAdopted`). Then try assigning the wrong type to one and read the error.
2. **Typed function.** Write `function describePet(name, age)` with typed params and an explicit return type. Call it with a wrong argument and read the error.
3. **Union type.** Make a variable that can be a `string` or `number` (like an `id`), or a status limited to `"pending" | "shipped" | "delivered"`. Try assigning a value outside the options.
4. **Interface.** Define `interface Pet { name: string; age: number; owner?: string }`, then create an object that satisfies it. Try leaving out a required field.
5. **Array type.** Make a `Pet[]` with two or three pets, then write a function that takes the array and returns just the names (`string[]`).

**Rule:** do each one 2-3 times with different examples, then stop. The mistakes you make on purpose matter more than the correct versions, because they teach you to read TypeScript errors, which is most of the real skill.

**One flag:** your Day 2 steps are about reading the React frontend, but you told me you'll be working on the NestJS backend (`spin-hobby-server`). I'd open that repo on Day 2 instead and read one small file, like a service or controller. The "one file, one line at a time" approach works the same way.