# 2026-11-11: Anatomy of a Web Request

**Lesson:** [Anatomy of a Web Request](https://freesystemdesign.com/#/request/learn)

## The Idea

When I type a website address and press Enter, the browser has a few jobs before the page appears. It finds the server, connects to it, asks for the page, and turns the reply into something I can see. A page load is a chain of steps, not just one request.

## The Steps

1. **Find the server.** The browser starts with a name like `twitter.com`, but computers use IP addresses. DNS helps find the address. If the answer is not cached, a resolver asks DNS servers and then remembers the result for a while.
2. **Make a connection.** For HTTP/1.1 and HTTP/2, the browser usually opens a TCP connection. HTTP/3 uses QUIC instead. Distance matters because messages take time to travel.
3. **Secure the connection.** With HTTPS, TLS checks the website's certificate and encrypts the connection, so people watching the network cannot read or change the page contents.
4. **Ask for the page.** The browser sends an HTTP request, often with a method such as `GET`, a path, and headers. The server may check who I am and get data from a cache or database before sending a response.
5. **Show the page.** The browser reads the response and may request more files, such as images, styles, and scripts. That means one page load can involve many requests.

```text
Website name -> DNS -> Connection -> HTTPS -> HTTP request
             -> Server work -> Response -> Browser renders page
```

## What Can Slow It Down?

Each trip across the network takes time. DNS, connection setup, distance, server work, and extra page files can all add delay. Caches and CDNs can help by keeping answers or files closer to the user.

## Takeaway

A web page has to travel through several steps before it appears. If any step is slow, the whole page can feel slow. Next, I want to understand the HTTP messages used in this process.
