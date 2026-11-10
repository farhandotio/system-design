# 2026-11-11: APIs and JSON

**Lesson:** [APIs and JSON](https://freesystemdesign.com/#/apis/learn)

## The Idea

An API is a clear agreement between programs: “Send a request in this shape, and I will reply in that shape.” A website usually sends HTML for people to look at. An API usually sends data that another program can use, such as a phone app or another service.

## REST and JSON

REST is a common way to organize an API around things called resources, such as users or orders. The URL tells us which thing we mean, and the HTTP method tells us what we want to do:

- `GET /users/42` asks for user 42.
- `POST /users` sends data to create a user.
- `PUT /users/42` replaces user 42.
- `DELETE /users/42` asks to remove user 42.

JSON is a text format often used for the data in API requests and responses. It has strings, numbers, `true` or `false`, `null`, lists, and objects with key-value pairs.

```http
GET /api/users/42
```

```http
HTTP/1.1 200 OK
Content-Type: application/json

{"id":42,"name":"Alice","posts":137}
```

If the user does not exist, the server might return `404 Not Found` with an error message in the JSON body. The status code tells me the result; the body can explain it.

## Trade-off or Failure Mode

An API is a promise to its clients. If I change the response shape without warning, apps that use it may break. JSON is easy to read and widely supported, but it can use more space than some binary formats.

## Takeaway

APIs let different programs share data through an agreed contract. REST gives common rules for URLs and HTTP methods, while JSON is a popular way to format the data. Next, I want to learn how to keep an API compatible as it changes.
