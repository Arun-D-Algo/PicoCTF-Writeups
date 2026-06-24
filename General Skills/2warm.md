# 2warm
## General Skills
## Easy

**Challenge Description:**  
Can you convert the number **42 (base 10)** to **binary (base 2)**?

---

### Solve

This challenge tested basic number system conversion by asking for the binary representation of the decimal number **42**.

To convert a decimal number to binary, repeatedly divide the number by **2** and record the remainder after each division.

The process for **42** is:

```text
42 ÷ 2 = 21 remainder 0
21 ÷ 2 = 10 remainder 1
10 ÷ 2 = 5  remainder 0
5  ÷ 2 = 2  remainder 1
2  ÷ 2 = 1  remainder 0
1  ÷ 2 = 0  remainder 1
```

Reading the remainders from **bottom to top** gives:

```text
101010
```

The hint stated that the answer should be wrapped in the picoCTF flag format.

**Flag:**

```text
picoCTF{101010}
```

---

### New Learnings

- Binary is a **base-2** number system that uses only the digits **0** and **1**.
- Decimal numbers can be converted to binary by repeatedly dividing by **2** and reading the remainders in reverse order.
- Binary numbers are normally written **without leading zeros** unless a fixed bit-width (such as 8-bit or 16-bit) is specifically required.
