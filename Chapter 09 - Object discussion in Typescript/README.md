# **Chapter 09 – Object Discussion in TypeScript**

This chapter explains how **objects**, **custom types**, **utility types**, and **structural typing** work in TypeScript. These concepts are the real power behind writing clean, scalable, production-ready TypeScript code.

---

# ## **1. Object Types in TypeScript (Basic Example)**

```ts
const chai = {
  name: "Masala chai",
  price: 20,
  isHot: true,
};
```

TypeScript automatically infers:
```ts
{
  name: string;
  price: number;
  isHot: boolean;
}
```

This is **inferred object typing**.

---

# ## **2. Defining Object Types Using `type`**

```ts
type Tea = {
  name: string;
  price: number;
  ingredients: string[];
};

const adrakChai: Tea = {
  name: "Adrak Chai",
  price: 25,
  ingredients: ["ginger", "tea leaves"],
};
```

Benefits:
- Reusable
- Strict structure
- Clean code

---

# ## **3. Structural Typing vs Duck Typing**
TypeScript uses **structural typing**, also called **duck typing**:
> If it looks like a type and behaves like a type, it *is* that type.

Example:
```ts
type Cup = { size: string };

let smallCup: Cup = { size: "200ml" };
let bigCup = { size: "300ml", color: "brown" };

smallCup = bigCup; // ✅ Allowed (extra property ignored)
```

Why allowed?
- Because `bigCup` **matches** the required structure.
- Extra properties don’t matter.

---

# ## **4. Nested Object Types (Real Example)**

```ts
type Item = {
  name: string;
  quantity: number;
};

type Address = {
  street: string;
  pin: number;
};

type Order = {
  id: string;
  items: Item[];
  address: Address;
};
```

Benefits:
- Clean structured data
- Enterprise-level maintainability
- Helps in React, APIs, Node.js

---

# ## **5. Utility Types: Partial, Required, Pick, Omit**
These built-in helpers improve productivity.

---

## ### **5.1 Partial<T>**
Makes all properties optional.

Image example:
```ts
type Chai = {
  name: string;
  price: number;
  isHot: boolean;
};

const updateChai = (updates: Partial<Chai>) => {
  console.log("updating chai with", updates);
};

updateChai({ price: 25 });
updateChai({ isHot: false });
updateChai({});
```

Use case: patch/update operations.

---

## ### **5.2 Required<T>**
Makes all optional properties required.

```ts
type ChaiOrder = {
  name?: string;
  quantity?: number;
};

const placeOrder = (order: Required<ChaiOrder>) => {
  console.log(order);
};

placeOrder({
  name: "Masala Chai",
  quantity: 2,
});
```

Use case: API final validation.

---

## ### **5.3 Pick<T, K>**
Extract selected properties.

```ts
type Chai = {
  name: string;
  price: number;
  isHot: boolean;
  ingredients: string[];
};

type BasicChaiInfo = Pick<Chai, "name" | "price">;

const chaiInfo: BasicChaiInfo = {
  name: "Lemon Tea",
  price: 30,
};
```

Use case: sending small payloads, listing items.

---

## ### **5.4 Omit<T, K>**
Opposite of Pick — remove selected properties.

```ts
type ChaiWithoutIngredients = Omit<Chai, "ingredients">;
```

Use case: hiding sensitive or unnecessary fields.

---

# ## **6. Type Inference Inside Objects**
TypeScript also infers types from object creation:

```ts
const tea = {
  name: "Green Tea",
  price: 50,
};
```

TS infers:
```ts
{
  name: string;
  price: number;
}
```

No need to annotate unless using reusable types.

---

# ## **7. Summary**
| Feature | Purpose |
|--------|----------|
| **Structural typing** | Match by shape, not name |
| **Partial** | Make all fields optional |
| **Required** | Make all fields required |
| **Pick** | Select few properties |
| **Omit** | Exclude few properties |
| **Nested types** | Clean data structures |

---
 ## **Reference Video**

**Chai aur Code –  Object Discussion in TypeScript**
<a 
  href="https://www.youtube.com/watch?v=aV0mlw1Hfh8&list=PLu71SKxNbfoBkkr8lblqtsJvxrw3j1tWC&index=2" 
  target="_blank" 
  rel="noopener noreferrer"
>
▶️ Watch the Video on YouTube
</a>
---

### **If you found this helpful, please star the repository!**