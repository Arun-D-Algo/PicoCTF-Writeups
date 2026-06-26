# information
## Forensics
## Easy

**Challenge Description:**  
Files can always be changed in a secret way. Can you find the flag?

---

### Solve

The challenge title and hint ("Look at the details of the file") strongly suggested that the flag was hidden inside the image metadata rather than inside the image itself.

The provided file was `cat.jpg`.

First, I verified that the file was actually a JPEG image.

```bash
file cat.jpg
```

Output:

```text
cat.jpg: JPEG image data, JFIF standard 1.02, aspect ratio, density 1x1, segment length 16, baseline, precision 8, 2560x1598, components 3
```

Since it was a normal JPEG, I inspected its metadata using `exiftool`.

```bash
exiftool cat.jpg
```

Output:

```text
ExifTool Version Number         : 13.50
File Name                       : cat.jpg
Directory                       : .
File Size                       : 878 kB
File Modification Date/Time     : 2026:06:20 14:46:33+00:00
File Access Date/Time           : 2026:06:21 21:38:31+00:00
File Inode Change Date/Time     : 2026:06:21 11:45:10+00:00
File Permissions                : -rwxrwxrwx
File Type                       : JPEG
File Type Extension             : jpg
MIME Type                       : image/jpeg
JFIF Version                    : 1.02
Resolution Unit                 : None
X Resolution                    : 1
Y Resolution                    : 1
Current IPTC Digest             : 7a78f3d9cfb1ce42ab5a3aa30573d617
Copyright Notice                : PicoCTF
Application Record Version      : 4
XMP Toolkit                     : Image::ExifTool 10.80
License                         : cGljb0NURnt0aGVfbTN0YWRhdGFfMXNfbW9kaWZpZWR9
Rights                          : PicoCTF
Image Width                     : 2560
Image Height                    : 1598
Encoding Process                : Baseline DCT, Huffman coding
Bits Per Sample                 : 8
Color Components                : 3
Y Cb Cr Sub Sampling            : YCbCr4:2:0 (2 2)
Image Size                      : 2560x1598
Megapixels                      : 4.1
```

The **License** field immediately stood out because it contained what looked like a Base64-encoded string:

```text
cGljb0NURnt0aGVfbTN0YWRhdGFfMXNfbW9kaWZpZWR9
```

I copied this value into CyberChef and applied the **From Base64** operation.

Decoded result:

```text
picoCTF{the_m3tadata_1s_modified}
```

**Flag:**

```text
picoCTF{the_m3tadata_1s_modified}
```

---

### New Learnings

- Images often contain hidden **metadata** (EXIF, IPTC, XMP) in addition to the visible image.
- `exiftool` is one of the best tools for viewing and analyzing image metadata.
- If metadata contains random-looking text, it is often encoded (commonly Base64, hexadecimal, or URL encoding).
- CyberChef is extremely useful for quickly decoding and analyzing encoded data.
