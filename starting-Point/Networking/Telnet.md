**Related:** [[SSH]] 

---

## What is Telnet?

Telnet <span style="color:rgb(192, 0, 0)">(Teletype Network)</span> is a **network protocol** that allows you to remotely connect to and control another machine over a network using a **command-line interface**.

It was created in **1969** and was the standard way to remotely manage systems before SSH existed.

> [!warning] Security Problem Telnet sends **everything in plaintext** — including usernames and passwords.  
> Anyone on the network can intercept and read it with a tool like Wireshark.  
> **It has been largely replaced by SSH** for this reason.

---

## How Telnet Works

1. Client opens a TCP connection to the target on **port 23**
2. Server responds and presents a login prompt
3. User types commands — they are sent and executed on the remote machine
4. All traffic flows back and forth in **plain, unencrypted text**

```
Your Machine ──── TCP (port 23) ────► Remote Machine
             ◄─── plaintext data ────
```

> [!info] OSI Layer Telnet operates at **Layer 7 (Application)** of the OSI model,  
> but uses **TCP at Layer 4** for the connection.

---

## Basic Usage

### Connect to a remote host

```bash
telnet [hostname or IP] [port]
```

### Example — connect to a machine on port 23

```bash
telnet 192.168.1.1
```

### Example — connect to a web server on port 80

```bash
telnet example.com 80
```

Then manually type an HTTP request:

```
GET / HTTP/1.1
Host: example.com
```

This is useful for **testing services manually** — a common trick in CTFs and pentesting.

---

## Telnet as a Port Testing Tool

> [!tip] Useful Trick You can use Telnet to check if a **specific port is open** on a target,  
> even if you're not using Telnet for remote access.

```bash
telnet 192.168.1.1 80    # test if HTTP port is open
telnet 192.168.1.1 22    # test if SSH port is open
telnet 192.168.1.1 25    # test if SMTP (email) port is open
```

If it connects → port is **open**  
If it times out or refuses → port is **closed or filtered**

---

## What You See in Wireshark

Because Telnet is plain-text, capturing Telnet traffic in Wireshark shows:

- The **username** typed during login
- The **password** typed during login
- Every **command** executed on the remote machine
- Every **output** returned by the server

> [!danger] This is why Telnet is dangerous A single packet capture on the same network is enough to steal credentials.

---

## Common Ports to Know Around Telnet

|Port|Protocol|Notes|
|---|---|---|
|**23**|Telnet|Default Telnet port — flag this as vulnerable if found open|
|**22**|SSH|Secure replacement for Telnet|
|**80**|HTTP|Can be tested manually with Telnet|
|**25**|SMTP|Can be tested manually with Telnet|

---

## In a Pentest / CTF Context

When you find **port 23 open** during an Nmap scan:

1. Flag it as a **critical vulnerability** (unencrypted remote access)
2. Try connecting with Telnet
3. Attempt **default credentials** (admin/admin, root/root, etc.)
4. If on a CTF — it often leads directly to a flag or shell

```bash
# Nmap scan that reveals Telnet
nmap -sV 192.168.1.1

# Output example:
# 23/tcp  open  telnet  Linux telnetd

# Connect immediately
telnet 192.168.1.1
```
