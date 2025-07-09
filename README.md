
# 📘 JavaScript Event Loop Quiz Explanation (from BFE.dev)

## 🧠 Code:
```js
console.log(1)
const promise = new Promise((resolve) => {
  console.log(2)
  resolve()
  console.log(3)
})

console.log(4)

promise.then(() => {
  console.log(5)
}).then(() => {
  console.log(6)
})

console.log(7)

setTimeout(() => {
  console.log(8)
}, 10)

setTimeout(() => {
  console.log(9)
}, 0)
```

---

## 📝 Explanation in Hinglish:

1. `console.log(1)` => Direct synchronous execution → prints `1`

2. `new Promise(...)` ke andar ka code **immediately run hota hai**:
   - `console.log(2)` → prints `2`
   - `resolve()` → promise ko resolve karta hai
   - `console.log(3)` → prints `3`

3. `console.log(4)` → Synchronous → prints `4`

4. `promise.then(...).then(...)` → Ye microtasks queue me chala jata hai.
   - Pehle `console.log(5)` execute hoga jab microtask phase aayega
   - Uske baad `console.log(6)`

5. `console.log(7)` → Synchronous → prints `7`

6. `setTimeout(..., 10)` and `setTimeout(..., 0)` → Ye dono **macrotasks** queue me jaate hain.
   - Even if delay 0 ms hai, setTimeout always runs **after microtasks**.

---

## 🧾 Final Output (line-by-line):
```
1
2
3
4
7
5
6
9
8
```

---

## 🔁 Timeline (Event Loop):

1. All synchronous code runs: `1 2 3 4 7`  
2. Microtasks queue executes: `5 6`  
3. Macrotasks (timers):  
   - `setTimeout(..., 0)` → `9`  
   - `setTimeout(..., 10)` → `8`

---

## ✅ Notes:
- `promise.then` callbacks always run after all sync code (microtask queue)
- `setTimeout` callbacks run later (macrotask queue)
- Order of `9` and `8` depends on delay (0ms timer usually fires before 10ms timer)

📌 Ideal for revision later.