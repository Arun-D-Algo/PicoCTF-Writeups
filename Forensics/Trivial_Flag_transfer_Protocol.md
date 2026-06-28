# Trivial Flag Transfer Protocol
## Forensics
## Medium

**Challenge Description:**  
Figure out how they moved the flag.

---

### Solve

The provided `.pcapng` file contained **TFTP (Trivial File Transfer Protocol)** traffic.

I opened the capture in **Wireshark** and noticed several TFTP requests. To recover the transferred files, I exported the TFTP objects by navigating to:

```text
File → Export Objects → TFTP
```

This extracted the following files:

```text
instructions.txt
picture1.bmp
picture2.bmp
picture3.bmp
plan
program.deb
```

Opening the `plan` file revealed an encoded message:

```text
VHFRQGURCEBTENZNAQUVQVGJVGU-QHRQVVTRAPR.PURPXBHGGURCUBGBF
```

I decoded it using **ROT13**, resulting in:

```text
I USED THE PROGRAM AND HID IT WITH DUE DILIGENCE. CHECK OUT THE PHOTOS
```

The clue suggested that:

- `program.deb` contained the steganography program used.
- The hidden flag was embedded inside one of the BMP images.
- The passphrase was likely **DUEDILIGENCE**.

I used `steghide` to inspect the images:

```bash
steghide info picture1.bmp
steghide info picture2.bmp
steghide info picture3.bmp
```

`picture3.bmp` reported an embedded file:

```text
embedded file "flag.txt"
```

I then extracted the hidden file:

```bash
steghide extract -sf picture3.bmp
```

When prompted for the passphrase, I entered:

```text
DUEDILIGENCE
```

The extraction succeeded and created `flag.txt`.

Finally, I viewed the file:

```bash
cat flag.txt
```

Which revealed the flag:

```text
picoCTF{h1dd3n_1n_pLa1n_51GHT_18375919}
```

**Flag:**

```text
picoCTF{h1dd3n_1n_pLa1n_51GHT_18375919}
```

---

### New Learnings

- **TFTP (Trivial File Transfer Protocol)** transfers files without encryption, making it easy to recover transferred files from packet captures.
- Wireshark can directly export transferred files using **File → Export Objects → TFTP**.
- Challenge clues may be hidden in transferred text files and encoded using simple ciphers like **ROT13**.
- **Steghide** is a steganography tool used to hide files inside images or audio files.
- The command `steghide info <image>` checks whether an image contains embedded data, while `steghide extract -sf <image>` extracts it using the correct passphrase.
- Steganography often combines multiple techniques, such as hidden files, encoded clues, and password-protected extraction.