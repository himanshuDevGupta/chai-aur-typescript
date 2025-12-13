# **Chapter 08 – Types and Interfaces in TypeScript**

👉 **Types vs Interfaces**

Don’t worry — TypeScript is actually **very simple** once you understand *why* and *when* to use each.

---

# ## **1. Why We Need Types / Interfaces**

Look at this function:

```ts
function makeChai(order: { type: string; sugar: number; strong: boolean }) {
  console.log(order);
}
```

This works, but:

* It is **hard to read**
* It is **not reusable**
* Real projects become messy

So we extract the structure.

---

# ## **2. Using `type` for Object Shape**

```ts
type ChaiOrder = {
  type: string;
  sugar: number;
  strong: boolean;
};

function makeChai(order: ChaiOrder) {
  console.log(order);
}
```

✅ Cleaner
✅ Reusable
✅ Used everywhere in real projects

---

# ## **3. Literal Types (Union Types)**

```ts
type CupSize = "small" | "large";

function orderCup(size: CupSize) {
  console.log(size);
}
```

Now `size` can only be:

* `"small"`
* `"large"`

This prevents invalid values.

---

# ## **4. Why `type` Is NOT Enough for Classes**

❌ This is **not valid**:

```ts
class Chai implements CupSize {}
```

Because:

* `type` is for **data shapes**
* `class` needs a **contract**

That contract is **interface**.

---

# ## **5. What is an Interface?**

An **interface** defines a structure that a **class must follow**.

```ts
interface TeaRecipe {
  water: number;
  milk: number;
}
```

---

# ## **6. Using Interface with Class**

```ts
interface Cup {
  size: "small" | "large";
}

class Chai implements Cup {
  size: "small" | "large" = "large";
}
```

✅ Interfaces work perfectly with classes

---

# ## **7. Type vs Interface (Important Rule)**

| Feature          | type    | interface |
| ---------------- | ------- | --------- |
| Object shape     | ✅       | ✅         |
| Union types      | ✅       | ❌         |
| Intersection     | ✅       | ❌         |
| Class implements | ❌       | ✅         |
| Extendable       | Limited | ✅         |

👉 **Rule of thumb:**

* Use **type** for data & unions
* Use **interface** for classes & contracts

---

# ## **8. Union Types with `type`**

```ts
type Response = { ok: true } | { ok: false };
```

This is **not possible with interface**.

---

# ## **9. Intersection Types**

```ts
type BaseChai = { teaLeaves: number };
type Extra = { masala: number };

type MasalaChai = BaseChai & Extra;

const cup: MasalaChai = {
  teaLeaves: 2,
  masala: 1,
};
```

Intersection = combine multiple types

---

# ## **10. Literal Types with Functions**

```ts
type TeaType = "m" | "g" | "l";

function orderChai(t: TeaType) {
  console.log(t);
}
```

Now `t` only accepts 3 values.

---

# ## **11. Optional Properties**

```ts
type ChaiOptions = {
  sugar?: number;
  strong?: boolean;
};
```

Optional (`?`) helps when:

* Some values may not come
* Partial updates

---

# ## **12. Real Project Recommendation**

✔ Use **type** for:

* API responses
* Union & intersection types
* Utility types

✔ Use **interface** for:

* Classes
* React props
* Public contracts

---
 
 ## **Reference Video**

**Chai aur Code –  Object Discussion in TypeScript**
[https://www.youtube.com/watch?v=kwcBi3S4bHU&list=PLu71SKxNbfoBkkr8lblqtsJvxrw3j1tWC&index=3](https://www.youtube.com/watch?v=kwcBi3S4bHU&list=PLu71SKxNbfoBkkr8lblqtsJvxrw3j1tWC&index=3)

---

### **If you found this helpful, please star the repository!**