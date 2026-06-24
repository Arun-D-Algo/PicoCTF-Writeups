# Obedient Cat
## General Skills
## Easy

**Challenge Description:**  
This file has a flag in plain sight (aka "in-the-clear").

---

### Solve

The challenge description suggested that the flag was stored directly inside the provided file without any encoding or encryption.

After downloading the file, I first checked that it existed and viewed its permissions using `ls -la`.

```bash
ls -la flag
```

Output:

```text
-rwxrwxrwx 1 arunangshu_dasgupta arunangshu_dasgupta 34 Jun 26 03:28 flag
```

Since it was a regular file, I simply displayed its contents using the `cat` command.

```bash
cat flag
```

Output:

```text
picoCTF{s4n1ty_v3r1f13d_9b8fa0bc}
```

The contents of the file were the flag itself.

**Flag:**

```text
picoCTF{s4n1ty_v3r1f13d_9b8fa0bc}
```

---

### New Learnings

- `cat` is a basic Linux command used to display the contents of a file directly in the terminal.
- `ls -la` shows detailed information about a file, including its permissions, owner, size, and modification time.
