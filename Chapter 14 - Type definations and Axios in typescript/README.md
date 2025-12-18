# 📘 Chapter 14 – Type Definitions and Axios in TypeScript

This chapter explains how TypeScript understands JavaScript libraries and how we use type definition (`.d.ts`) files, especially while working with Axios and external packages. This is a critical skill for real-world production environments.

---

## 🔹 1. What are Type Definitions?
TypeScript itself does not run code; it only understands types. For JavaScript libraries (which don't have types), TypeScript needs a "translator."

👉 **These files tell TypeScript:**
* What functions exist
* What arguments they accept
* What they return



---

## 🔹 2. What is a .d.ts File?
`.d.ts` stands for **Declaration File**. It contains only type information, no actual logic.

// example.d.ts
declare function makeChai(type: string): number;

* **✔ No implementation:** Only the signature of the function.
* **✔ Only types:** Helps the compiler understand existing JS code.
* **✔ Tooling:** Provides hints and prevents errors in your editor.

---

## 🔹 3. How TypeScript Gets Types Automatically
When you install modern libraries like **Axios**, TypeScript automatically gets type definitions because Axios ships with its own `.d.ts` files.

Command: `npm install axios`

**You immediately get:**
1. Auto-completion (IntelliSense)
2. Type checking
3. Instant error detection

---

## 🔹 4. Built-in Declaration Files
TypeScript includes many default declaration files to understand the environment you are coding in (Browser or Node.js).

**Examples:**
* `lib.dom.d.ts` (For `document`, `window`, `addEventListener`)
* `lib.es2020.d.ts` (For `Promise`, `Map`, `Set`)

👉 This is why you don't need to define what `fetch()` or `console.log()` is—TypeScript already knows.

---

## 🔹 5. When a Library Has NO Types
Some older JavaScript libraries do not include types. In this case, you install them from the **DefinitelyTyped** repository using the `@types` prefix.

**Example for Lodash:**
1. `npm install lodash` (Installs the logic)
2. `npm install -D @types/lodash` (Installs the type definitions)

---

## 🔹 6. If Types Do Not Exist (Custom Declarations)
If a library is very obscure and has no `@types` package, you can create a `custom.d.ts` file to stop TypeScript from complaining:

// custom.d.ts
declare module "some-library";

// Or define a minimal structure:
declare module "some-library" {
  export function doSomething(): void;
}

---

## 🔹 7. Axios with TypeScript (Generics)
Axios is most powerful when used with **Generics** to define the shape of API data.



### 1️⃣ Defining API Response Shape
interface Todo {
  userId: number;
  id: number;
  title: string;
  completed: boolean;
}

### 2️⃣ Axios Generic Response
import axios, { AxiosResponse } from "axios";

const fetchData = async () => {
  const response: AxiosResponse<Todo> = await axios.get(
    "https://jsonplaceholder.typicode.com/todos/1"
  );

  // ✔ response.data is now fully typed as 'Todo'
  console.log(response.data.title); 
};

---

## 🔹 8. Error Handling with Axios
In TypeScript, the `catch` block defaults to `unknown` or `any`. Axios provides a helper to handle this safely.

try {
  await axios.get("/api/data");
} catch (error) {
  if (axios.isAxiosError(error)) {
    // TypeScript now knows 'error' is an AxiosError
    console.log("Status Code:", error.response?.status);
    console.log("Message:", error.message);
  } else {
    console.log("An unexpected error occurred", error);
  }
}

---

## 🔹 9. Why Declaration Files Matter
* **Without .d.ts:** No IntelliSense, no type safety, and more runtime bugs.
* **With .d.ts:** Compile-time safety, better Developer Experience (DX), and cleaner code.

---

## 📌 Best Practices
* **✔ Built-in Types:** Always prefer libraries that come with built-in types.
* **✔ Avoid `any`:** Never use `any` for API responses; always create an `interface`.
* **✔ Use DevDependencies:** Always install `@types/*` packages with the `-D` (save-dev) flag.
* **✔ Safe Errors:** Always use `axios.isAxiosError()` to check errors before accessing properties.

---
 ## **Reference Video**

**Chai aur Code –  Type Definitions and Axios in TypeScript**
[https://www.youtube.com/watch?v=GTyKTyw2GhI&list=PLu71SKxNbfoBkkr8lblqtsJvxrw3j1tWC]
(https://www.youtube.com/watch?v=GTyKTyw2GhI&list=PLu71SKxNbfoBkkr8lblqtsJvxrw3j1tWC)
---

### **If you found this helpful, please star the repository!**