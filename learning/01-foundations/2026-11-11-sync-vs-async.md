# 2026-11-11: Sync vs Async

**Lesson:** [Sync vs Async](https://freesystemdesign.com/#/async_concept/learn)

## The Idea

With **sync** work, I start a task and wait for it to finish before moving on. With **async** work, I start something and carry on while it finishes in the background. Async does not make the task itself faster; it means the user may not have to wait for it.

## Example: Checkout

The app needs to check and charge a payment before it can say the order succeeded. Sending a confirmation email can happen afterward. The server can put an email job on a queue and return the checkout result; a worker sends the email later.

```text
Sync:  request -> check payment -> save order -> send email -> reply

Async: request -> check payment -> save order -> queue email -> reply
                                                  |
                                                  v
                                           worker sends email
```

## When It Is Useful

Use sync work when the user needs the answer right away, such as whether a password or payment is valid. Async work is useful for things like emails, notifications, analytics, or file processing. A queue can also hold work during a traffic spike, and workers can retry jobs that fail.

## Trade-off or Failure Mode

The email still takes time to send; the user just does not wait for it. Queues and workers add moving parts, and a job might run more than once after a failure. The system should handle duplicates safely, retry carefully, and make failed jobs visible so they are not silently lost.

## Takeaway

Use sync when the caller needs the result now; use async when the work can finish later. Next, I want to learn how queues store and deliver jobs reliably.
