# what's a net cat?
## General Skills
## Easy

**Challenge Description:**  
Using netcat (`nc`) is going to be pretty important. Can you connect to the given host and port to retrieve the flag?

---

### Solve

This challenge introduced the use of **Netcat (`nc`)**, a command-line networking utility used to establish TCP or UDP connections to remote hosts.

The challenge provided the following information:

- Host: `fickle-tempest.picoctf.net`
- Port: `64346`

To connect to the remote server, I used the `nc` command followed by the hostname and port number.

```bash
nc fickle-tempest.picoctf.net 64346
```

After establishing the connection, the server immediately returned a short message followed by the flag.

Terminal output:

```text
$ nc fickle-tempest.picoctf.net 64346

You're on your way to becoming the net cat master
picoCTF{nEtCat_Mast3ry_f20a728c}
```

**Flag:**

```text
picoCTF{nEtCat_Mast3ry_f20a728c}
```

---

### New Learnings

- **Netcat (`nc`)** is a networking utility used to create TCP or UDP connections between systems.
- The basic syntax is:
  ```bash
  nc hostname port
  ```
- Unlike SSH, Netcat does not authenticate or provide a remote shell by default. It simply opens a network connection and allows data to be sent and received.
- Netcat is commonly used in CTFs for interacting with remote challenge servers, testing network services, transferring files, and debugging network connections.
