# **Chapter 04 – Type Annotations and Type Inference in TypeScript**

* What Type **Annotations** are
* What Type **Inference** is
* How TypeScript detects **syntax errors vs type errors**
* Why TS prevents mistakes that JavaScript cannot
* Real examples based on the Chai aur Code tutorial

---

# ## **1. Type Annotations**

Type Annotations mean: **You tell TypeScript the type of a variable manually.**

Example:

```ts
let channelName: string = "chai aur code";
```

Here:

* `channelName` **must always be a string**.
* If you try to assign a number → TypeScript shows an error.

```ts
channelName = 12221; // ❌ Error: number is not assignable to string
```

### Why use Type Annotations?

* To make your code more predictable
* To avoid accidental wrong values
* Useful in React, APIs, user inputs, form fields, etc.

---

# ## **2. Type Inference**

Type Inference means: **TypeScript automatically understands the type without you writing it.**

Example:

```ts
let drink = "chai";
```

TypeScript automatically infers:

```ts
drink: string
```

Now, if you try:

```ts
drink = 0;
```

❌ Error: number is not assignable to type string

TS inferred the type from the initial value.

---

### Another Example From Video

```ts
let cups = Math.random() > 0.5 ? 10 : '5';
```

TS infers:

```ts
cups: string | number
```

Why?

* Condition may return **10 (number)** or **'5' (string)**.

This is Inference at work.

---

# ## **3. Syntax Error vs Type Error**

### **Syntax Error**

The code structure itself is wrong.
Example:

```ts
let drink = "chai"
let x = // missing value ❌ Syntax error
```

### **Type Error**

The code syntax is correct, but type is wrong.
Example:

```ts
let drink = "chai";
drink = 3; // ❌ Type error
```

JS would allow it → but TS catches it.

---

# ## **4. Why TypeScript Helps**

JavaScript gives freedom but also risks.
TypeScript prevents common mistakes like:

* Assigning wrong values
* Using variables before assignment
* Wrong function arguments
* Using string where number expected

Example from video:

```ts
let channiFa: string = 'chaimasala';
channiFa = 12; // ❌ Not allowed
```

This improves safety and reduces bugs.

---

# ## **5. Combining Annotation + Inference**

### Good Example:

```ts
let drink: string = "chai";  // Annotation
let cups = 10;                // Inference
```

### When to use Annotation?

* When TS can't infer type (API, DOM, forms)
* When you want strict control over data

### When to use Inference?

* When assigning a clear initial value
* Let TS automatically decide

---
## **Reference Video**

**Chai aur Typescript – Type Annotations and Type Inference in TypeScript**
[https://www.youtube.com/watch?v=mUz7nbbZJc0&list=PLu71SKxNbfoBkkr8lblqtsJvxrw3j1tWC&index=4](https://www.youtube.com/watch?v=mUz7nbbZJc0&list=PLu71SKxNbfoBkkr8lblqtsJvxrw3j1tWC&index=4)

---

### **If you found this helpful, please star the repository!**