
# What is ICMP

## ICMP — Internet Control Message Protocol

ICMP is a **network-layer protocol** used by network devices routers, servers, and hosts to send **error messages and operational information** about the network. It's defined in **RFC 792** and works alongside IP (Internet Protocol).

Unlike TCP or UDP, ICMP is **not used to exchange data between applications**. Its main purpose is **network diagnostics and control**.

### What ICMP does:

- Reports errors like **"destination unreachable"**, **"time exceeded"**, or **"network congested"**
- Helps routers communicate problems back to the source of a packet
- Carries **diagnostic messages** used by tools like `ping` and `traceroute`

# What is ping

## Ping — Packet Internet Groper

`ping` is a **command-line diagnostic tool** that uses ICMP to test whether a host is reachable on a network and to measure **round-trip time (RTT)**.

### How it works, step by step:

```
Your Machine  ──── ICMP Echo Request ────►  Target Host
Your Machine  ◄─── ICMP Echo Reply   ────   Target Host
```

1. Your machine sends an **ICMP Echo Request** (type 8) to the target IP
2. If the target is alive and reachable, it replies with an **ICMP Echo Reply** (type 0)
3. `ping` measures the time between sending and receiving → that's the **RTT (latency)**

### Example output :

```bash
$ ping google.com

PING google.com (142.250.185.46)
64 bytes from 142.250.185.46: icmp_seq=1 ttl=118 time=12.4 ms
64 bytes from 142.250.185.46: icmp_seq=2 ttl=118 time=11.9 ms
```

|Field|Meaning|
|---|---|
|`icmp_seq`|Sequence number of the packet|
|`ttl`|Time To Live — hops remaining|
|`time`|Round-trip latency in milliseconds|
