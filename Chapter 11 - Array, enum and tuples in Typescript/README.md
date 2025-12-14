# **Chapter 11 – Arrays, Tuples & Enums in TypeScript**
 

# ## **1. Arrays in TypeScript**

Arrays in TypeScript are strongly typed. You can control **what kind of data** an array can hold.

### **Basic Array Types**

```ts
const chaiFlavours: string[] = ["Masala", "Adrak"];
const chaiPrice: number[] = [10, 20];
```

Alternative generic syntax:

```ts
const rating: Array<number> = [4.5, 5.0];
```

---

# ## **2. Array of Objects**

```ts
type Chai = {
  name: string;
  price: number;
};

const menu: Chai[] = [
  { name: "Masala", price: 15 },
  { name: "Adrak", price: 25 },
];
```

This is very common in real projects (menus, products, lists).

---

# ## **3. Readonly Arrays**

Readonly arrays **cannot be modified**.

```ts
const cities: readonly string[] = ["Delhi", "Jaipur"];

// cities.push("Pune") ❌ Error
```

Useful when:

* Data should not change
* Config or constant values

---

# ## **4. Multidimensional Arrays**

```ts
const table: number[][] = [
  [1, 2, 3],
  [4, 5, 6],
];
```

Used in:

* Matrix data
* Grid layouts

---

# ## **5. Tuples in TypeScript**

Tuples are **fixed-length arrays** with a fixed order and type.

```ts
let chaiTuple: [string, number];
chaiTuple = ["Masala", 20]; // ✅
chaiTuple = [20, "Masala"]; // ❌ Wrong order
```

Order and type **both matter**.

---

# ## **6. Optional Elements in Tuples**

```ts
let userInfo: [string, number, boolean?];
userInfo = ["hitesh", 100];
```

---

# ## **7. Readonly Tuples**

Readonly tuples prevent modification.

```ts
const location: readonly [number, number] = [28.32, 77.21];
```

---

# ## **8. Named Tuples (Better Readability)**

```ts
const chaiItem: [name: string, price: number] = ["Masala", 25];
```

This improves code clarity.

---

# ## **9. Enums in TypeScript**

Enums define a **fixed set of named constants**.

---

## ### **9.1 Numeric Enum**

```ts
enum CupSize {
  SMALL,
  MEDIUM,
  LARGE,
}

const size = CupSize.LARGE;
```

---

## ### **9.2 Custom Numeric Values**

```ts
enum Status {
  PENDING = 100,
  SERVER,
  CANCELED,
}
```

Values auto-increment.

---

## ### **9.3 String Enums (Recommended)**

```ts
enum ChaiType {
  MASALA = "masala",
  GINGER = "ginger",
}
```

✅ Better debugging
✅ Clear values

---

## ### **9.4 ❌ Bad Practice – Mixed Enums**

```ts
enum RandomEnum {
  ID = 1,
  NAME = "chai",
}
```

Avoid mixing string & number enums.

---

# ## **10. Enum Best Practices**

* Enum names should be **CAPITAL_CASE**
* Prefer **string enums**
* Avoid mixed enums
* Use enums only when values are fixed

---

# ## **11. Common Pitfall – Arrays vs Tuples**

```ts
let t: [string, number] = ["chai", 10];
t.push("extra"); // ⚠️ Allowed at runtime
```

Why dangerous?

* Tuple size can break
* Debugging becomes hard

👉 Use **readonly tuples** when possible.

---
 ## **Reference Video**

**Chai aur Code –  Arrays, Tuples & Enums in TypeScript**
[https://www.youtube.com/watch?v=Ekkrf65uZL4]
(https://www.youtube.com/watch?v=Ekkrf65uZL4)
---

### **If you found this helpful, please star the repository!**
 
