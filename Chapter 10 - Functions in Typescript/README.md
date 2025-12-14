# **Chapter 10 – Functions in TypeScript**

Functions are one of the most powerful features of TypeScript because TS allows us to define:

* parameter types
* return types
* optional parameters
* default values
* object-type parameters

This gives us **predictable, type‑safe function behavior**.

---

# ## **1. Why Functions in TypeScript Are Better than JavaScript**

In JavaScript you can write:

```js
function getChaiPrice() {
  return "25 rupees";
}
```

But JavaScript **does not warn** if the function returns the wrong value.

In TypeScript:

```ts
function getChaiPrice(): number {
  return 25; // must return number
}
```

If you try:

```ts
return "25 rupees";
```

TS ❌ error: *string is not assignable to number*

This is why we define return types.

---

# ## **2. Function Return Types**

### **Return a Number**

```ts
function getChaiPrice(): number {
  return 25;
}
```

### **Return nothing (void)**

```ts
function logChai(): void {
  console.log("Chai is ready");
}
```

`void` → function does not return anything.

---

# ## **3. Optional Parameters**

Two ways to make parameters optional:

### **Method 1 – `?` Operator**

```ts
function orderChai(type?: string) {
  console.log(`Ordering: ${type}`);
}
```

`type` can be:

* string
* undefined

### **Method 2 – Default Parameter**

(Default parameters must be at the **end**.)

```ts
function orderChai(type: string = "Masala Chai") {
  console.log(`Ordering: ${type}`);
}
```

If user does not pass a value → default is used.

---

# ## **4. Function with Object Parameters**

We can structure object inputs with strict typing.

### Example:

```ts
function createChai(order: {
  type: string;
  sugar: number;
  size: "small" | "large";
}): number {
  console.log(order);
  return 1; // return something like order ID
}
```

This is simple and readable.

TypeScript makes object parameters predictable and safe.

---

# ## **5. Why Object Params Are Useful**

* Great for APIs
* Great for React component props
* Avoid positional parameter confusion

Example bad JS:

```js
makeChai("masala", 2, false);
```

What is 2? What is false?

Better TS:

```ts
makeChai({ type: "masala", cups: 2, isHot: true });
```

Clear, structured, predictable.

---

# ## **6. Full Example From Video**

```ts
function makeChai(type: string, cups: number) {
  console.log(`Making ${cups} cups of ${type}`);
}

makeChai("Masala", 2);

function getChaiPrice(): number {
  return 25;
}

function logChai(): void {
  console.log("Chai is ready");
}

function orderChai(type: string = "Elaichi") {
  console.log(`Order placed for ${type}`);
}

function createChai(order: {
  type: string;
  sugar: number;
  size: "small" | "large";
}): number {
  console.log(order);
  return 1001; // example order ID
}
```

---
 ## **Reference Video**

**Chai aur Code –  Functions in TypeScript**
[https://www.youtube.com/watch?v=hVMD8imCBrE]
(https://www.youtube.com/watch?v=hVMD8imCBrE)
---

### **If you found this helpful, please star the repository!**
