# Warmed Up
## General Skills
## Easy

**Challenge Description:**  
What is **0x3D (base 16)** in **decimal (base 10)**?

---

### Solve

This challenge required converting a hexadecimal number into its decimal equivalent.

Instead of converting it manually, I used **CyberChef**.

I entered the hexadecimal value:

```text
3D
```

Then I applied the following operation:

```text
From Hex
```

and selected the output as **Decimal (Base 10)**.

CyberChef returned:

```text
61
```

The hint mentioned that the answer should be wrapped in the picoCTF flag format.

**Flag:**

```text
picoCTF{61}
```

---

### New Learnings

- **Hexadecimal (Base 16)** uses the digits `0–9` and the letters `A–F`, where:
  - `A = 10`
  - `B = 11`
  - `C = 12`
  - `D = 13`
  - `E = 14`
  - `F = 15`
- The prefix `0x` indicates that a number is written in hexadecimal.
- CyberChef can quickly convert values between different number bases, making it a useful tool for CTF challenges involving encoding and data representation.
