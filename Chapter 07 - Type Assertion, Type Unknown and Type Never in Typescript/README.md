@ -0,0 +1,164 @@
# ⭐ Chapter 07: Type Assertion, `unknown`, and `never` in TypeScript

In this chapter, we explore **three powerful TypeScript features** used for type safety, validation, and exhaustive error checking.

---

## 🔹 1️⃣ Type Assertion

Type Assertion allows you to **inform** TypeScript what the type of a value should be, even if TypeScript cannot infer it.

> ✨ Basically: “Hey TypeScript — trust me, I know what I'm doing!”

### ✔ Syntax
```ts
value as Type
// or
<Type>value  // (older JSX-conflicting syntax)
```

> ❗ Type Assertion does **not** convert the value at runtime — it only affects TypeScript type checking.

---

### 💡 Example: DOM Element (Most Common Use Case)
```ts
const inputEl = document.getElementById("username") as HTMLInputElement;
inputEl.value = "Himanshu";
```

Why needed?

➡ `getElementById()` returns `HTMLElement | null`  
➡ `HTMLElement` does not always have `.value`

---

### ⚠️ Type Assertion Can Fail

If you make a wrong assumption, type assertion won’t save you ⛔

```ts
const res: any = "42";
(res as number).toFixed(2); 
// ❌ Runtime Error — “res” is actually a string
```

Also:

```ts
const response: any = "42";
const length = (response as number).len; 
// ❌ undefined — TypeScript didn’t warn due to "any"
```

🚨 `any` disables type safety  
Try to avoid unnecessary assertions with `any`.

---

### Real Example: Admin / Super Admin Role
```ts
type Role = "admin" | "user" | "superadmin";

const roleFromApi: string = "superadmin";
const role = roleFromApi as Role;

function redirect(role: Role) {
  if (role === "admin") console.log("Admin Dashboard");
  if (role === "user") console.log("User Dashboard");
  if (role === "superadmin") console.log("Superadmin Dashboard");
}
redirect(role);
```

✔ Use type assertion **only when you are confident** the data is correct.

---

## 🔹 2️⃣ `unknown` Type

`unknown` is **safer** than `any`.

➤ You must **check** the type before using the value.

```ts
let value: unknown = "Hello";

// value.toUpperCase(); // ❌ Error
if (typeof value === "string") {
  console.log(value.toUpperCase()); // ✅ Safe
}
```

➤ Enforces proper validation — great for input handling.

---

### Real-world Example: Environment Variables
```ts
const portFromEnv: unknown = process.env.PORT;

if (typeof portFromEnv === "string") {
  const port = Number(portFromEnv);
  console.log("Server running at:", port);
} else {
  throw new Error("PORT must be a string");
}
```

✔ Prevents hidden runtime crashes

---

## 🔹 3️⃣ `never` Type

Represents **no possible value**.  
Used in cases where a function **never returns** or code should be **unreachable**.

### ❌ Function that never returns
```ts
function throwError(msg: string): never {
  throw new Error(msg);
}
```

Execution stops after the error — no value returned.

---

### Exhaustive Checking Example

Useful when handling **all** possible states in a `switch`:

```ts
type Role = "admin" | "user" | "superadmin";

function handleRole(role: Role) {
  switch (role) {
    case "admin":
      console.log("Admin");
      break;
    case "user":
      console.log("User");
      break;
    case "superadmin":
      console.log("Superadmin");
      break;
    default:
      const _never: never = role; // ⛔ If new role added, build error
      throw new Error("Unhandled Role!");
  }
}
```

✨ If a new role like `"guest"` is added later → TypeScript alerts you.

 ## **Reference Video**

**Chai aur Code – Type Assertion, Type Unknown and Type Never in Typescript**
[https://www.youtube.com/watch?v=npYs6HMBIG0&list=PLu71SKxNbfoBkkr8lblqtsJvxrw3j1tWC&index=1](https://www.youtube.com/watch?v=npYs6HMBIG0&list=PLu71SKxNbfoBkkr8lblqtsJvxrw3j1tWC&index=1)

---

### **If you found this helpful, please star the repository!**