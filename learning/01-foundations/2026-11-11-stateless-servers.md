# 2026-11-11: Stateless Servers

**Lesson:** [Stateless Servers](https://freesystemdesign.com/#/stateless/learn)

## The Idea

A stateful server keeps useful information in its own memory or disk between requests. A stateless server does not depend on information stored only on itself. It can handle a request using the information in that request or by reading shared storage.

## Why It Helps

Imagine Server 2 keeps a user's shopping cart in memory. If the next request goes to Server 1, that server cannot see the cart. Sticky sessions can keep sending that user to Server 2, but if Server 2 goes down, its local cart is gone. It can also make traffic harder to balance.

Instead, save the cart in a shared database or cache. Then any server can look it up. The same idea works for login sessions, and uploaded files can live in shared object storage instead of one server's disk. A signed token such as a JWT can also carry verified user information, but the server still needs to check the token and its permissions.

```text
Client -> Load balancer -> Any server -> Shared cart store
                                      <- read or update ->
```

## Trade-off or Failure Mode

Shared storage makes servers easier to replace, but it becomes an important dependency. It needs enough capacity and should be reliable and fast. Stateless servers also do not guarantee a no-downtime release on their own; deployment and health checks still need to be planned.

## Takeaway

If any server can handle the next request, adding or replacing servers is much simpler. Keep important user data somewhere shared, not only in one server's memory. Next, I want to learn how queues let servers handle some work later.
