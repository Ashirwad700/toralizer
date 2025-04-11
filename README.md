`toralizer` is a low-level C project that transparently routes socket connections through a local SOCKS4 proxy (like Tor) by hooking the `connect()` system call. It uses `LD_PRELOAD` to override the default `connect()` behavior and redirect traffic through `127.0.0.1:9050`.

---

How It Works:

The project:

- Overrides the `connect()` system call using `LD_PRELOAD`
- Connects to a SOCKS4 proxy (e.g., Tor)
- Builds and sends a SOCKS4 request to the proxy server
- If successful, uses `dup2()` to forward the original socket to the proxy socket

This allows you to anonymize or route connections through Tor **without modifying your application's source code**.

---
