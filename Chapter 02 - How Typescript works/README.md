# **Chapter 02: How TypeScript Works**

This chapter explains the behind-the-scenes workflow of the TypeScript compiler—how your `.ts` code is processed and converted into clean JavaScript.

---

## **🔄 TypeScript Compilation Pipeline**

TS Code ➝ **Lexer** ➝ **Parser** ➝ **Binder** ➝ **Checker** ➝ **Emitter (Generator)**

Each stage plays a unique role in validating, analyzing, and generating JavaScript from TypeScript.

---

## **1. Lexer (Tokenization)**

The **lexer** scans your TypeScript code and breaks it into *tokens*. These are the smallest meaningful units of the code.

### **What Lexer Does:**

* Reads code character-by-character
* Breaks code into tokens: keywords, identifiers, operators, numbers, strings, etc.
* Detects basic syntax issues (e.g., missing semicolon)

**Example:**

```ts
let age: number = 30;
```

Lexer output → `let`, `age`, `:`, `number`, `=`, `30`, `;`

---

## **2. Parser (AST Creation)**

Parser takes the tokens created by the lexer and produces an **AST (Abstract Syntax Tree)**.

### **What Parser Does:**

* Builds a structured tree of your code
* Validates the syntactic structure
* Defines code blocks, function bodies, variables, etc.

This AST becomes the foundation for the next compiler stages.

---

## **3. Binder (Symbol Table Creation)**

The **binder** traverses the AST and assigns meaning to variables, functions, and symbols.

### **What Binder Creates:**

* Symbol Table (variables, functions, types)
* Scope relationships (parent/child)
* Link between references and declarations

### **Binder Responsibilities:**

* Scope resolution
* Handling imported/exported modules
* Data flow attachment

---

## **4. Checker (Type Checking Engine)**

This is the most important part of TypeScript — the **type checker**.

### **What Checker Does:**

* Validates types
* Verifies function signatures
* Ensures data flows correctly
* Performs structural checks
* Checks for invalid operations

### **Type Checker Workflows:**

1. **Syntax Check** → Are tokens and syntax valid?
2. **Type Check** → Are types correct and consistent?

The checker is what gives TS its superpowers by catching errors before runtime.

---

## **5. Emitter (JavaScript Generator)**

The final stage of the pipeline.

### **Emitter Responsibilities:**

* Removes all TypeScript-specific syntax (types, interfaces, generics)
* Converts `.ts` → `.js`
* Applies compiler settings (`target`, `module`, `strict`)

**Example:**

```ts
let count: number = 100;
```

Emitter output (JS):

```js
let count = 100;
```

## **Reference Video**

**Chai aur Code – How TypeScript Works**
[https://www.youtube.com/watch?v=hvbXtB52x8s&list=PLu71SKxNbfoBkkr8lblqtsJvxrw3j1tWC&index=5](https://www.youtube.com/watch?v=hvbXtB52x8s&list=PLu71SKxNbfoBkkr8lblqtsJvxrw3j1tWC&index=5)

---

### **If you found this helpful, please star the repository!**

