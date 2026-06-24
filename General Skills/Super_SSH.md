# Super SSH
## General Skills
## Easy

**Challenge Description:**  
Using a Secure Shell (SSH) is going to be pretty important.

Can you SSH as `ctf-player` to `titan.picoctf.net` on the given port using the provided password to retrieve the flag?

---

### Solve

This challenge was an introduction to using **SSH (Secure Shell)** to remotely connect to another machine.

The challenge provided the following information:

- Host: `titan.picoctf.net`
- Port: `63890`
- Username: `ctf-player`
- Password: `6dd28e9b`

To connect to the remote server, I used the `ssh` command along with the custom port using the `-p` option.

```bash
ssh ctf-player@titan.picoctf.net -p 63890
```

Since this was my first time connecting to the server, SSH asked me to verify the server's fingerprint.

I typed:

```text
yes
```

After accepting the fingerprint, I entered the password provided in the challenge:

```text
6dd28e9b
```

Once authenticated, the server immediately displayed the flag and closed the connection.

Terminal output:

```text
$ ssh ctf-player@titan.picoctf.net -p 63890

The authenticity of host '[titan.picoctf.net]:63890 ([3.139.174.234]:63890)' can't be established.
ED25519 key fingerprint is: SHA256:4S9EbTSSRZm32I+cdM5TyzthpQryv5KudRP9PIKT7XQ
This key is not known by any other names.
Are you sure you want to continue connecting (yes/no/[fingerprint])? yes

Warning: Permanently added '[titan.picoctf.net]:63890' (ED25519) to the list of known hosts.

** WARNING: connection is not using a post-quantum key exchange algorithm.
** This session may be vulnerable to "store now, decrypt later" attacks.
** The server may need to be upgraded. See https://openssh.com/pq.html

ctf-player@titan.picoctf.net's password:

Welcome ctf-player, here's your flag:
picoCTF{s3cur3_c0nn3ct10n_5d09a462}

Connection to titan.picoctf.net closed.
```

**Flag:**

```text
picoCTF{s3cur3_c0nn3ct10n_5d09a462}
```

---

### New Learnings

- **SSH (Secure Shell)** is a protocol used to securely connect to remote systems over a network.
- The basic syntax of the SSH command is:
  ```bash
  ssh username@hostname
  ```
- If the server uses a non-default port, it can be specified using:
  ```bash
  ssh username@hostname -p PORT_NUMBER
  ```
- The first time connecting to a server, SSH asks whether to trust the server's fingerprint before adding it to the `known_hosts` file.
- After successful authentication, commands can be executed on the remote machine just like on a local Linux terminal.

---

### References

- https://www.openssh.com/manual.html
- https://linuxcommand.org/lc3_man_pages/ssh1.html
- picoCTF General Skills Challenges