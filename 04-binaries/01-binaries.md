# ⚙️ Bitwise Operations — DSA Cheat Sheet

## 🧩 Core Ops

| Operator | Meaning | Rule                        | Example                 | Output                  |            |
| -------- | ------- | --------------------------- | ----------------------- | ----------------------- | ---------- |
| `&`      | AND     | 1 **only if both** bits = 1 | `5 & 3 → 0101 & 0011`   | `0001 (1)`              |            |
| `        | `       | OR                          | 1 **if either** bit = 1 | `5 \| 3 → 0101 \| 0011` | `0111 (7)` |
| `^`      | XOR     | 1 **if different**          | `5 ^ 3 → 0101 ^ 0011`   | `0110 (6)`              |            |
| `~`      | NOT     | flips every bit             | `~5 → 11111010`         | `-6`                    |            |

---

## 🚀 Shift Ops

| Operator | Meaning              | Effect                   | Example     | Output       |
| -------- | -------------------- | ------------------------ | ----------- | ------------ |
| `<<`     | Left Shift           | multiply by 2 each step  | `5 << 1`    | `10`         |
| `>>`     | Right Shift          | divide by 2 (keeps sign) | `10 >> 1`   | `5`          |
| `>>>`    | Unsigned Right Shift | divide ignoring sign     | `-10 >>> 1` | `2147483643` |

---

## 💡 Common Tricks

✅ `x & (1 << k)` → check if **k-th bit** is ON
✅ `x | (1 << k)` → turn ON the **k-th bit**
✅ `x ^ (1 << k)` → toggle **k-th bit**
✅ `x & (x - 1)` → true if `x` is **power of 2**
✅ `a ^ a = 0`, `a ^ 0 = a` → base for “single number” problems

---

## ⚔️ Mental Model

* **Left Shift:** think “*boost power ×2*”
* **Right Shift:** think “*halve it*”
* **AND:** filter bits
* **OR:** combine bits
* **XOR:** detect change
* **NOT:** flip polarity
