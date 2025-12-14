## 🔄 Hoisting in JavaScript (Interview Favorite Topic)

### 🔹 Hoisting কী?
**Hoisting** হলো JavaScript-এর একটি behavior যেখানে  
👉 **variable এবং function declarations কে code execute হওয়ার আগে memory-তে তুলে নেয়**।

⚠️ মনে রাখবে:  
> **Declaration hoist হয়, initialization হয় না**

---

## 🧠 Hoisting কীভাবে কাজ করে?
JavaScript code execute করার আগে **Memory Creation Phase** হয়।

এই phase-এ:
- `var` → hoist হয় এবং value হয় `undefined`
- `let` & `const` → hoist হয় কিন্তু **Temporal Dead Zone (TDZ)**-এ থাকে
- Function declaration → পুরো function hoist হয়

---

## 🟡 Hoisting with `var`
```js
console.log(a); // undefined
var a = 10;
var a;
console.log(a);
a = 10;
```
- ✔ Error দেয় না
- ❌ But value undefined

## 🟡 Hoisting with `let`
```js
console.log(b); // ❌ ReferenceError
let b = 20;
```
### `📌 কারণ:`
- let hoist হয়
- কিন্তু TDZ-এ থাকে
- Declaration এর আগে access করা যায় না

## 🟡 Hoisting with `const`
```js
console.log(c); // ❌ ReferenceError
const c = 30;
```
### `📌 Same rule as let`
- ✔ Hoisted
- ❌ Access before declaration → Error

## 🔴 Temporal Dead Zone (TDZ)
### `TDZ হলো সেই সময়টা:`
- Variable hoist হওয়ার পর
- Declaration লাইনের আগ পর্যন্ত
``` js
// TDZ starts
console.log(x); // ❌ ReferenceError
let x = 5;
// TDZ ends
```

## 🟢 Function Hoisting
### `Function Declaration (Hoisted)`

``` js
sayHello(); // Works

function sayHello() {
  console.log("Hello");
}
```
- পুরো function hoist হয়

### `Function Expression (Not Hoisted)`

``` js
sayHi(); // ❌ TypeError

var sayHi = function () {
  console.log("Hi");
};

```
- 📌 var sayHi hoist হয় (undefined)
- ❌ function body hoist হয় না
## 🧪 Interview Comparison Table – Hoisting

| Case | Hoisted | Access Before Declaration |
|------|--------|---------------------------|
| `var` | ✅ | `undefined` |
| `let` | ✅ | ❌ ReferenceError |
| `const` | ✅ | ❌ ReferenceError |
| Function Declaration | ✅ | ✅ |
| Function Expression | Partial | ❌ |

##  ❓ Common Interview Questions
### `Is let hoisted?`
- ✔ Yes, but stays in TDZ

### `Why does var return undefined?`
- Because it is initialized during hoisting

### `Best practice?`
- ✔ Use let and const
- ✔ Avoid accessing variables before declaration
