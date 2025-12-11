# **Chapter 05 – Type Narrowing & Type Guards in TypeScript**

JavaScript programmers normally "run the code and check later" — but **TypeScript prevents bugs even before running**.

This chapter explains:

* What is Type Narrowing?
* Types of Narrowing (typeof, truthy, equality, `in`, `instanceof`)
* User-defined Type Guards
* Replacing `any` with `unknown`
* Real Chai examples (Masala Chai, Ginger Chai, Kulhad Chai, Cutting Chai)

---

# ## **1. What is Type Narrowing?**

Type Narrowing = **reducing** a variable from a wide type → to a more specific type.

Example:

```ts
function getChai(kind: string | number) {
    if (typeof kind === 'string') {
        return `Making ${kind} chai...`;
    }

    return `Chai order number ${kind}`;
}
```

Here:

* `kind` starts as `string | number`
* Inside the `if`, TypeScript *narrows* it to `string`

This is called **narrowing**.

---

# ## **2. Why Not Use `any`? Why Use `unknown` Instead?**

`any` disables TypeScript — it allows anything.

`unknown` is safer:

```ts
let data: unknown = "chai";

data.toUpperCase(); // ❌ Error (good)

if (typeof data === 'string') {
    data.toUpperCase(); // ✅ Safe
}
```

With `unknown`, you **must narrow** the type.

---

# ## **3. Built‑in Narrowing Techniques**

### ### **3.1 typeof Narrowing**

```ts
function getChai(kind: string | number) {
    if (typeof kind === 'string') {
        return `Making ${kind} chai...`;
    }
    return `Chai order number: ${kind}`;
}
```

### ### **3.2 Truthy Narrowing**

```ts
function serveChai(msg?: string) {
    if (msg) {
        return `Serving: ${msg}`;
    }
    return "Serving fresh chai";
}
```

### ### **3.3 Equality Narrowing**

```ts
function orderChai(size: 'small' | 'medium' | 'large' | number) {
    if (size === 'small') return 'Small Chai ready!';

    if (size === 'medium' || size === 'large') {
        return 'Make extra chai!';
    }

    return 'Chai order received'; // Exhaustive check
}
```

---

# ## **4. Using Objects for Type Narrowing**

When working with object types, we can narrow using:

* `in` operator
* `instanceof`

### ### **4.1 `in` Operator Narrowing**

```ts
type MasalaChai = { spiceLevel: number };
type GingerChai = { ginger: boolean };

function brew(order: MasalaChai | GingerChai) {
    if ("spiceLevel" in order) {
        return `Brewing Masala Chai with spice ${order.spiceLevel}`;
    }

    return `Brewing Ginger Chai`;
}
```

---

# ## **5. Class-based Narrowing (`instanceof`)**

Example from the video:

```ts
class KulhadChai {
    serve() {
        return "Serving Kulhad Chai";
    }
}

class Cutting {
    serve() {
        return "Serving Cutting Chai";
    }
}

function serveChaiType(order: KulhadChai | Cutting) {
    if (order instanceof KulhadChai) {
        return order.serve();
    }
    return order.serve();
}
```

---

# ## **6. User‑Defined Type Guards**

Sometimes TypeScript cannot narrow automatically.
So we create our own guard.

### Example: Check if input is a string array

```ts
function isStringArray(arr: unknown): arr is string[] {
    return Array.isArray(arr) && arr.every(item => typeof item === "string");
}

const result = isStringArray(["masala", "ginger"]); // true
```

Here:

* `arr is string[]` tells TypeScript what the function guarantees.

---

# ## **7. Extra Example – Full Practical Chai Order System**

```ts
type MasalaChai = { spiceLevel: number };
type GingerChai = { ginger: boolean };
type DefaultChai = { type: "masala" | "ginger" | "default" };

function makeChai(order: unknown) {
    if (typeof order === 'string') {
        return `Making chai: ${order}`;
    }

    if (typeof order === 'number') {
        return `Order number received: ${order}`;
    }

    if (order && typeof order === 'object' && "spiceLevel" in order) {
        return `Masala level ${order.spiceLevel}`;
    }

    if (order && typeof order === 'object' && "ginger" in order) {
        return `Ginger Chai ready`;
    }

    return "Default Chai served";
}
```

This example combines:

* typeof narrowing
* in‑operator narrowing
* unknown type handling

---
## **Reference Video**

**Chai aur Typescript – Understanding Union Types & Any in TypeScript**
[https://www.youtube.com/watch?v=TdejZsExjws&list=PLu71SKxNbfoBkkr8lblqtsJvxrw3j1tWC&index=4](https://www.youtube.com/watch?v=TdejZsExjws&list=PLu71SKxNbfoBkkr8lblqtsJvxrw3j1tWC&index=4)

---

### **If you found this helpful, please star the repository!**