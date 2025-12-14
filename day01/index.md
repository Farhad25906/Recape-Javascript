# 🟢 Segment 1 – Variables & Data Types (JavaScript)

This segment covers the **fundamental building blocks of JavaScript**.  
It is **interview-focused**, **conceptually deep**, and includes **practical examples**.

---

## 📌 What You Will Learn
- Difference between `var`, `let`, and `const`
- Primitive vs Reference data types
- How JavaScript handles memory
- `typeof` operator
- `null` vs `undefined` (very important for interviews)

---

## 1️⃣ Variables in JavaScript

A **variable** is a container used to store data.
Variable হলো data রাখার container।

```js
let name = "Farhad";
name → variable
```
- `name` → variable (container for data)
- `"Farhad"` → value (actual data stored in the variable)

## 2️⃣ var vs let vs const
### `var`
```js
var x = 10;
var x = 20; // allowed
```

**Features**

- Function scoped
- Re-declaration allowed
- Hoisted and initialized as undefined
- Not block scoped (problematic)

```js
if (true) {
  var a = 5;
}
console.log(a); // 5

```

**❗ Avoid using var in modern JavaScript.**

### `let`
```js
let y = 10;
y = 20; // allowed
```

**Features**

- Block scoped
- Re-declaration not allowed
- Hoisted but in Temporal Dead Zone (TDZ)
- Reassignment allowed

```js
if (true) {
  let b = 5;
}
console.log(b); // ReferenceError

```

### `const`
```js
const z = 10;
z = 20; // ❌ Error
```

**Features**

- Block scoped
- Reassignment not allowed
- Re-declaration not allowed

```js
const user = { name: "Farhad" };
user.name = "Hossen"; // ✅ allowed
```
- const prevents reassigning
- It does not prevent modifying object properties


## 3️⃣ Data Types in JavaScript

JavaScript data types are divided into two categories:

## `Primitive Data Types`
### `Characteristics`
- Immutable
- Passed by value
- Stored in stack memory

### `Types`
- string
- number
- boolean
- undefined
- null
- symbol
- bigint
```js
let a = 10;
let b = a;

b = 20;

console.log(a); // 10
console.log(b); // 20

```

## `Reference (Non-Primitive) Data Types`
### `Characteristics`
- Mutable
- Passed by reference
- Stored in heap memory

### `Types`
- Object
- Array
- Function
```js
let obj1 = { name: "Farhad" };
let obj2 = obj1;

obj2.name = "Hossen";

console.log(obj1.name); // Hossen
```

## 4️⃣ typeof Operator
The typeof operator is used to check the data type.

```js
typeof "hello";   // "string"
typeof 10;        // "number"
typeof true;      // "boolean"
typeof undefined; // "undefined"
typeof null;      // "object"

```

**❗ Why typeof null returns "object"?**
- This is a historical bug in JavaScript that has been kept for backward compatibility.

📌 Interview Answer

`"typeof null === 'object' is a known JavaScript bug from its early days."`

## 5️⃣ null vs undefined (🔥 Very Common Interview Question)

| Feature | null | undefined |
|-------|------|-----------|
| Meaning | Intentionally empty value | Variable declared but not assigned |
| Type | `object` (JavaScript bug) | `undefined` |
| Assigned by | Developer | JavaScript |

### Example
```js
let a;
console.log(a); // undefined

let b = null;
console.log(b); // null

## 6️⃣ Memory Behavior
### `Primitive → Stack Memory`
```js
let x = 5;
let y = x;
```

### `Reference → Heap Memory`
```js
let arr1 = [1, 2];
let arr2 = arr1;
```
- Primitive values copy actual value
- Reference types copy memory reference

## 7️⃣ Common Interview Questions
### `❓ Why is let preferred over var?`
- Block scoped
- Prevents accidental re-declaration
- Safer and predictable behavior

### `❓ Can a const object be modified?`
- Object properties can change
- Reference cannot be reassigned

### `❓ How to properly check for null?`
```js
value === null
```