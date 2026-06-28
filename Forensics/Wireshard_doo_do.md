# Wireshark doo dooo do doo...
## Forensics
## Medium

**Challenge Description:**  
Can you find the flag?

---

### Solve

The challenge provided a packet capture (`shark1.pcapng`) that needed to be analyzed using **Wireshark**.

Initially, most of the traffic consisted of **encrypted WinRM/WSMAN HTTP** packets. Following these HTTP streams only displayed encrypted SOAP payloads, which did not contain any useful information.

After scrolling through the packet list, I found an **unencrypted HTTP GET request** with an HTTP **200 OK** response.

I right-clicked the packet and selected:

```text
Follow → HTTP Stream
```

The stream contained the following response:

```text
Gur synt vf cvpbPGS{c33xno00_1_f33_h_qrnqorrs}
```

The text looked like a **ROT13** cipher because it contained recognizable patterns such as `Gur` (`The`) and `cvpbPGS` (`picoCTF`).

I decoded the string using a **ROT13 decoder** (CyberChef's **ROT13** operation also works), which produced:

```text
The flag is picoCTF{p33kab00_1_s33_u_deadbeef}
```

The flag was therefore:

**Flag:**

```text
picoCTF{p33kab00_1_s33_u_deadbeef}
```

---

### New Learnings

- Not every HTTP stream in a packet capture is useful; encrypted traffic may not contain directly readable information.
- **Follow → HTTP Stream** is an effective way to reconstruct the complete HTTP request and response.
- Packet captures can contain multiple independent HTTP conversations, so it is important to inspect different streams rather than assuming the first one is relevant.
- **ROT13** is a simple substitution cipher that rotates each alphabetic character by 13 positions and is commonly encountered in beginner CTF challenges.
- When analyzing packet captures, looking for **unencrypted application-layer traffic** can often reveal hidden flags or encoded messages.