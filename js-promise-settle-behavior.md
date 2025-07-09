
# 🧩 JavaScript Quiz: Promise Resolve & Reject Behavior (from BFE.dev)

## 🔢 Code:
```js
new Promise((resolve, reject) => {
  resolve(1)
  resolve(2)
  reject('error')
}).then((value) => {
  console.log(value)
}, (error) => {
  console.log('error')
})
```

---

## 🧾 Output:
```
1
```

---

## 📖 Explanation (Hinglish):

- Jab `new Promise(...)` create hota hai, uska executor function turant execute hota hai.

1. `resolve(1)` call hota hai → isse promise **fulfilled** ho jata hai with value `1`.
2. `resolve(2)` and `reject('error')` **ignore** kiya jata hai kyunki promise sirf ek baar settle hota hai — pehle hi settle ho chuka hai `resolve(1)` ke saath.
3. `then()` ke first callback ko value milti hai: `1` → `console.log(value)` chalega.

🔁 Second `resolve(2)` aur `reject('error')` ka koi effect nahi hota.

---

## 🧠 Concepts Covered:
- Promise immutability after first resolve/reject
- Only the first call to `resolve` or `reject` is effective
- `then(successCallback, errorCallback)` ka use

---

## ✅ Notes:
- Promise once settled (fulfilled or rejected), fir usko change nahi kar sakte.
- Yahan `resolve(1)` ke baad kuch bhi likha ho, wo ignore hoga.

📌 Useful for interviews where Promise behavior ka detailed knowledge test kiya jata hai.
