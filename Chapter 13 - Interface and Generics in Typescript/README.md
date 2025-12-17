# 📘 Chapter 13 – Interface and Generics in TypeScript

This chapter covers two of the most critical topics used in real-world TypeScript projects: **Interfaces** and **Generics**. Together, they form the backbone of scalable and type-safe codebases.

---

## 🔹 1. What is an Interface?
An interface defines the structure (shape) of an object. It acts as a contract that an object or class must follow.

interface Chai {
  flavor: string;
  price: number;
}

// Any object using Chai must follow this shape:
const masalaChai: Chai = {
  flavor: "Masala",
  price: 25,
};

---

## 🔹 2. Interface vs Type (Quick Comparison)



| Feature | Interface | Type |
| :--- | :--- | :--- |
| **Best For** | Object structures & Classes | Logic, Unions, & Primitives |
| **Merging** | Supports Declaration Merging | No merging allowed |
| **Flexibility** | Specialized for objects | Highly flexible (Unions/Intersections) |
| **Standard** | Industry standard for APIs | Preferred for complex logic |

👉 **Rule of thumb:** Use `interface` for object structure and `type` for complex logic or union types.

---

## 🔹 3. Readonly Properties in Interface
You can prevent properties from being changed after they are initialized.

interface Shop {
  readonly id: number;
  name: string;
}

const s: Shop = {
  id: 1,
  name: "Chai Shop",
};

// s.id = 2; ❌ Error: Cannot assign to 'id' because it is a read-only property.

---

## 🔹 4. Function Type Interface
Interfaces can also be used to describe the shape of a function.

interface DiscountCalculator {
  (price: number): number;
}

const apply50: DiscountCalculator = (p) => p * 0.5;
// ✔ Clean, Readable, and Reusable.

---

## 🔹 5. Index Signature (Dynamic Keys)
Used when you don't know the exact property names in advance, but you know the type of data they will hold.

interface ChaiRating {
  [chaiName: string]: number;
}

const ratings: ChaiRating = {
  masala: 5,
  ginger: 4,
  lemon: 3,
};
// ✔ Useful for API responses and configuration maps.

---

## 🔹 6. Interface Merging
A unique feature of interfaces is that multiple declarations with the same name will automatically merge.

interface User {
  name: string;
}

interface User {
  age: number;
}

const u: User = {
  name: "Hitesh",
  age: 30,
};
// ❗ Note: This is NOT possible with 'type'.

---

## 🔹 7. Extending Interfaces
Interfaces can inherit from other interfaces to build complex structures cleanly.



interface BaseChai {
  flavor: string;
}

interface MasalaChai extends BaseChai {
  spiceLevel: number;
}

const chai: MasalaChai = {
  flavor: "Masala",
  spiceLevel: 2,
};

---

## 🔹 8. Generics (Templates for Types)
Generics allow you to write reusable code that works with multiple types while maintaining full type safety. Instead of fixing a type, you use a placeholder (usually `<T>`).

### 🧠 Generic Function Example
function wrapInArray<T>(item: T): T[] {
  return [item];
}

wrapInArray("Masala");           // T becomes string
wrapInArray(43);                 // T becomes number
wrapInArray({ flavor: "Ginger" }); // T becomes an object

---

## 🔹 9. Interface with Generics
This pattern is used extensively in production for handling API responses and data wrappers.



interface ApiPromise<T> {
  status: number;
  data: T;
}

const res: ApiPromise<{ flavor: string }> = {
  status: 200,
  data: { flavor: "masala" },
};

### 🔁 Generic Interface Reuse
interface Box<T> {
  value: T;
}

const stringBox: Box<string> = { value: "chai" };
const numberBox: Box<number> = { value: 100 };

---

## 🔹 10. Why Generics are Essential
Most major libraries and frameworks rely on Generics:
* **Axios:** For typed API responses.
* **React:** For Props and State definitions.
* **Redux:** For managing typed store states.
* **Utility Functions:** For writing tools that work with any data type.

---

## ❌ Common Mistakes to Avoid
1. **Using `any` instead of Generics:** `any` destroys type safety; Generics preserve it.
2. **Over-complicating Generics:** Don't use them if a simple type will suffice.
3. **Using `type` when `interface` is better:** Stick to interfaces for public API definitions and object shapes to allow for merging.

---
 ## **Reference Video**

**Chai aur Code – Interface and Generics in TypeScript**
[https://www.youtube.com/watch?v=GTyKTyw2GhI&list=PLu71SKxNbfoBkkr8lblqtsJvxrw3j1tWC]
(https://www.youtube.com/watch?v=GTyKTyw2GhI&list=PLu71SKxNbfoBkkr8lblqtsJvxrw3j1tWC)
---

### **If you found this helpful, please star the repository!**