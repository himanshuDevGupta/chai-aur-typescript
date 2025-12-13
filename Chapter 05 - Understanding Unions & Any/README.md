# **Chapter 05 – Understanding Union Types & Any in TypeScript**

# ## **1. What Are Union Types?**

A **Union Type** lets you define a variable that can store values of **multiple specific types**.

Example:

```ts
let subs: number | string = "1m";
subs = 10;     // ✅ allowed
subs = "2m";   // ✅ allowed
```

TypeScript ensures only these allowed types can be assigned.

---

# ## **2. Where Are Union Types Used in Real Projects?**

Union types are extremely useful in:

* API request status
* UI state machines
* Form validation
* Role-based access

### Example: API Request Status

```ts
let apiReqStatus: "success" | "pending" | "error" = "pending";

apiReqStatus = "success"; // ✅
apiReqStatus = "done";    // ❌ invalid value
```

Why useful?

* Prevents mistakes
* Restricts values to valid options
* Helps in large team projects

---

# ## **3. Airline Seat Example (From Video)**

```ts
let airlineSeat: "aisle" | "window" | "middle" = "aisle";

airlineSeat = "window";   // ✅
airlineSeat = "crew";      // ❌ not allowed
```

This ensures only 3 valid seat choices exist.

---

# ## **4. Why Not Just Use Strings?**

Bad (JavaScript way):

```js
let seat = "aisle";
seat = "pizza"; // 🤦‍♂️ allowed in JS
```

Good (TypeScript way):

```ts
let seat: "aisle" | "window" | "middle";
```

This prevents invalid data.

---

# ## **5. Understanding the `any` Type**

`any` means:

> "I don't know the type, and I don't care."

It **disables all TypeScript checking**.

Example:

```ts
let currentOrder: any;

for (let order of orders) {
  if (order === "28") {
    currentOrder = order;
    break;
  }
}

currentOrder = 42; // ❌ no error, but logically wrong
```

### Why `any` is dangerous?

* No type safety
* No IntelliSense suggestions
* Bugs become harder to find

---

# ## **6. When Should You Use `any`?**

Use `any` only in rare cases:

* Unknown API response
* Third-party JS library without TypeScript support
* Temporary prototyping

But avoid using it as a habit.

---

# ## **7. Better Alternatives to `any`**

### ✔ Use Union Types

```ts
let order: string | number;
```

### ✔ Use Custom Types

```ts
type Status = "success" | "pending" | "error";
```

### ✔ Use `unknown` when unsure (safer)

```ts
let data: unknown;
```

`unknown` forces you to check type before using.

## **Reference Video**

**Chai aur Typescript – Understanding Union Types & Any in TypeScript**
[https://www.youtube.com/watch?v=fFs17LZhicg&list=PLu71SKxNbfoBkkr8lblqtsJvxrw3j1tWC&index=4](https://www.youtube.com/watch?v=fFs17LZhicg&list=PLu71SKxNbfoBkkr8lblqtsJvxrw3j1tWC&index=4)

---

### **If you found this helpful, please star the repository!**

