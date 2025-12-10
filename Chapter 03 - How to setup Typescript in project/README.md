# **Chapter 03: How to Set Up TypeScript in a Project**

This chapter explains how to install TypeScript globally, locally in a project, configure `tsconfig.json`, and understand how TypeScript compiles code into JavaScript.

---

## ## **1. Installing TypeScript**

TypeScript can be installed in **two ways**:

### ✅ **1️⃣ Global Installation**

Installs TypeScript CLI for the whole system.

```sh
npm install -g typescript
```

Use when:

* You want `tsc` command available everywhere.
* Useful for learning or quick testing.

### ✅ **2️⃣ Project (Local) Installation**

Recommended for real projects.

```sh
npm install -D typescript
```

`-D` means **dev dependency** → this package will NOT be shipped to production.

Why local install?

* Each project can use **its own TS version**.
* Team projects stay consistent.

---

## ## **2. tsconfig.json (TypeScript Configuration File)**

The **heart of a TypeScript project**.

Create it manually:

```sh
tsc --init
```

This generates a file with many options, most of them commented.

You can enable/disable features by uncommenting.

---

## ## **3. Important tsconfig Options**

Here are the most commonly used settings:

### 🔹 **`target`**

Decides which JavaScript version TS should output.

```json
"target": "es2017"
```

Other options: `es2016`, `es5`, `es2020`, etc.

**Recommended:** Use the default or ES2017+.

---

### 🔹 **`rootDir`**

Where your TypeScript source files live.

```json
"rootDir": "./src"
```

Useful when company projects have multiple folders.

---

### 🔹 **`outDir`**

Where compiled JavaScript files will be generated.

```json
"outDir": "./dist"
```

After compilation, `dist` folder contains:

* JS files
* `.map` files (if enabled)
* Final runnable code

---

### 🔹 **`strict`**

Enables all strict type-checking options.

```json
"strict": true
```

Recommended for best TypeScript experience.

---

### 🔹 **tsconfig Docs Website**

Official site to explore every config option:
👉 [https://www.typescriptlang.org/tsconfig](https://www.typescriptlang.org/tsconfig)

This helps understand what each option does.

---

## ## **4. How TypeScript Compilation Works**

Running:

```sh
tsc
```

TypeScript will:

1. Read `tsconfig.json`
2. Scan all TypeScript files in `rootDir`
3. Compile them into JavaScript inside `outDir` (usually `dist/`)

Example structure:

```
project/
 ├─ src/
 │   └─ index.ts
 ├─ dist/
 │   └─ index.js
 ├─ tsconfig.json
 └─ package.json
```

Now you can execute JavaScript using Node:

```sh
node dist/index.js
```

---

## ## **5. Why TypeScript is Useful for Projects**

* Teams with multiple developers get **consistent patterns**.
* Better tooling support → IntelliSense, auto-imports, error checks.
* Works beautifully with **React**, **Node.js**, **Next.js**.
* Helps companies maintain large codebases safely.

---
## **Reference Video**

**Chai aur Code – How TypeScript Works**
[https://www.youtube.com/watch?v=4O4Y1TJz3F0&list=PLu71SKxNbfoBkkr8lblqtsJvxrw3j1tWC&index=5](https://www.youtube.com/watch?v=4O4Y1TJz3F0&list=PLu71SKxNbfoBkkr8lblqtsJvxrw3j1tWC&index=5)

---

### **If you found this helpful, please star the repository!**
