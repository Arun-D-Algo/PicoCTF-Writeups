# Bases
## General Skills
## Easy

**Challenge Description:**  
What does this `bDNhcm45fdGgzX3lwcDM1` mean? I think it has something to do with bases.

---

### Solve

The challenge provided a string that appeared to be encoded rather than encrypted.

The presence of uppercase letters, lowercase letters, and numbers suggested that it was **Base64** encoded.

Instead of decoding it manually, I used **CyberChef**.

I entered the following string:

```text
bDNhcm5fdGgzX3lwcDM1
```

Then I applied the **From Base64** operation.

CyberChef decoded the string to:

```text
l3arn_th3_r0p35
```

The challenge hint stated that the decoded text should be wrapped in the picoCTF flag format.

**Flag:**

```text
picoCTF{l3arn_th3_r0p35}
```

---

### New Learnings

- **Base64** is an encoding scheme used to represent binary data as printable ASCII characters.
- Base64 strings often consist of uppercase letters, lowercase letters, numbers, `+`, `/`, and sometimes end with `=` padding characters.
- CyberChef's **From Base64** operation can quickly decode Base64-encoded data, making it a valuable tool for CTF challenges involving encoded strings.
- Encoding is different from encryption because encoded data can be reversed without requiring a secret key.
