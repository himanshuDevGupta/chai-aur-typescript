# 📘 Chapter 11 – OOP Concepts in TypeScript

TypeScript supports Object-Oriented Programming (OOP) just like JavaScript, but with better safety, readability, and tooling. This chapter explains how and why we use OOP features in TypeScript with real examples, not theory.

---

## 🔹 Why OOP in TypeScript?
* Better code structure
* Strong type safety
* Easy scaling for large projects
* Cleaner business logic
* Helps teams work together

TypeScript does not change OOP rules, it just makes them safer and clearer.

---

## 1️⃣ Classes in TypeScript
A class is a blueprint for creating objects.
```ts
class Chai {
  flavour: string;
  price: number;

  constructor(flavour: string, price: number) {
    this.flavour = flavour;
    this.price = price;
  }
}
const masalaChai = new Chai("Masala", 20);
```
👉 this always refers to the current object instance.

---

## 2️⃣ Access Modifiers (public, private, protected)

✅ public (default)
Accessible everywhere.
```ts
class Chai {
  public flavor: string = "Masala";
}

🔒 private (keyword)
Accessible only inside the class.

class Chai {
  private secretIngredient = "Cardamom";

  reveal() {
    return this.secretIngredient; // ✅ allowed
  }
}
```
❌ Cannot access from outside.

🔐 private using # (JavaScript + TypeScript)
This is true private, even at runtime.
```ts
class Wallet {
  #balance = 100;

  getBalance() {
    return this.#balance;
  }
}
const w = new Wallet();
// w.#balance ❌ error
```
👉 Recommended for secure data.

---

## 3️⃣ readonly Properties
A property that can be assigned only once.
```ts
class Cup {
  readonly capacity: number;

  constructor(capacity: number) {
    this.capacity = capacity;
  }
}
const cup = new Cup(250);
// cup.capacity = 300 ❌ not allowed
👉 Useful for constants like ID, capacity, config values.
```
---

## 4️⃣ Getters and Setters
Used to control access to private data.
```
class ModernChai {
  private _sugar = 2;

  get sugar() {
    return this._sugar;
  }

  set sugar(value: number) {
    if (value > 5) {
      throw new Error("Too sweet!");
    }
    this._sugar = value;
  }
}
const chai = new ModernChai();
chai.sugar = 3;   // ✅
```
👉 Helps with validation & encapsulation.

---

## 5️⃣ protected Members
Accessible in class + subclasses only.
```
class Shop {
  protected shopName = "Chai Code Cafe";
}
class Branch extends Shop {
  getName() {
    return this.shopName; // ✅ allowed
  }
}
```
❌ Not accessible outside classes.

---

## 6️⃣ Static Members
Belong to the class, not object instance.
```
class Cafe {
  static brand = "Chai Aur Code";
}
console.log(Cafe.brand);
👉 Used for shared values, helpers, constants.
```
---

## 7️⃣ Abstract Classes
Abstract classes cannot be instantiated. They are used as base rules.


```ts
abstract class Drink {
  abstract make(): void;

  serve() {
    console.log("Serving drink");
  }
}
class Tea extends Drink {
  make() {
    console.log("Making tea");
  }
}
```
👉 Use when you want structure but no direct object.

---

## 8️⃣ Inheritance & Polymorphism
Same method name, different behavior.


```ts
class Chai {
  brew() {
    console.log("Brewing chai");
  }
}
class GreenTea extends Chai {
  brew() {
    console.log("Brewing green tea");
  }
}
```
👉 Polymorphism works same as JS, but safer.

---

## 9️⃣ Composition (Better than Inheritance)
Instead of extending, use another class inside.
```ts
class Heater {
  heat() {
    console.log("Heating...");
  }
}
class ChaiMaker {
  constructor(private heater: Heater) {}

  make() {
    this.heater.heat();
    console.log("Chai ready");
  }
}
```

---
 ## **Reference Video**

**Chai aur Code –  Arrays, Tuples & Enums in TypeScript**
[https://www.youtube.com/watch?v=B_eCW0umzjA&list=PLu71SKxNbfoBkkr8lblqtsJvxrw3j1tWC&index=4]
(https://www.youtube.com/watch?v=B_eCW0umzjA&list=PLu71SKxNbfoBkkr8lblqtsJvxrw3j1tWC&index=4)
---

### **If you found this helpful, please star the repository!**