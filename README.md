# aws-sqs-dlq-processor
Gracefullt process SQS DLQ messages.


## Idea

- Cli accepts:
  - queue-url
  - dlq-url (get it from queue url if not provided?)
  - n (size of batch)
- Read n messages from the dlq and print it on terminal?
- Prompt user to send to main queue or stop while providing the number of messages remaining and already sent
- Repeat until no more messages remaining in dlq or user stops

Additional Features?
- Ability to purge all messages or specific messages from dlq?
- Ability to cherry pick messages to reprocess?


## Mockups

```bash
dlq-processor --queue-url https://sqs.us-east-1.amazonaws.com/123456789012/MyQueue

Fetching 10 messages from DLQ https://sqs.us-east-1.amazonaws.com/123456789012/MyQueue-dlq...

Message 1: {"order_id": 123, "status": "failed"}
Message 2: {"order_id": 124, "status": "failed"}
Message 3: {"order_id": 125, "status": "failed"}
Message 4: {"order_id": 126, "status": "failed"}
Message 5: {"order_id": 127, "status": "failed"}
Message 6: {"order_id": 128, "status": "failed"}
Message 7: {"order_id": 129, "status": "failed"}
Message 8: {"order_id": 130, "status": "failed"}
Message 9: {"order_id": 131, "status": "failed"}
Message 10: {"order_id": 132, "status": "failed"}

Processed 10 messages. 0 messages sent so far.
Send messages to main queue? (yes/no): yes

Sending messages to main queue...
Deleting messages from DLQ...
10 messages sent successfully.

Fetching 10 messages from DLQ https://sqs.us-east-1.amazonaws.com/123456789012/MyQueue-dlq...

No more messages to process.
Total messages sent: 10

dlq-processor --queue-url https://sqs.us-east-1.amazonaws.com/123456789012/MyQueue --n 5

Fetching 5 messages from DLQ https://sqs.us-east-1.amazonaws.com/123456789012/MyQueue-dlq...

Message 1: {"order_id": 201, "status": "failed"}
Message 2: {"order_id": 202, "status": "failed"}
Message 3: {"order_id": 203, "status": "failed"}
Message 4: {"order_id": 204, "status": "failed"}
Message 5: {"order_id": 205, "status": "failed"}

Processed 5 messages. 0 messages sent so far.
Send messages to main queue? (yes/no): no

Stopping processing.
Total messages sent: 0

dlq-processor --queue-url https://sqs.us-east-1.amazonaws.com/123456789012/MyQueue --n 3

Fetching 3 messages from DLQ https://sqs.us-east-1.amazonaws.com/123456789012/MyQueue-dlq...

Message 1: {"order_id": 301, "status": "failed"}
Message 2: {"order_id": 302, "status": "failed"}
Message 3: {"order_id": 303, "status": "failed"}

Processed 3 messages. 0 messages sent so far.
Send messages to main queue? (yes/no): yes

Sending messages to main queue...
Deleting messages from DLQ...
3 messages sent successfully.

Fetching 3 messages from DLQ https://sqs.us-east-1.amazonaws.com/123456789012/MyQueue-dlq...

Message 1: {"order_id": 304, "status": "failed"}
Message 2: {"order_id": 305, "status": "failed"}
Message 3: {"order_id": 306, "status": "failed"}

Processed 3 messages. 3 messages sent so far.
Send messages to main queue? (yes/no): yes

Sending messages to main queue...
Deleting messages from DLQ...
3 messages sent successfully.

Fetching 3 messages from DLQ https://sqs.us-east-1.amazonaws.com/123456789012/MyQueue-dlq...

Message 1: {"order_id": 307, "status": "failed"}
Message 2: {"order_id": 308, "status": "failed"}
Message 3: {"order_id": 309, "status": "failed"}

Processed 3 messages. 6 messages sent so far.
Send messages to main queue? (yes/no): yes

Sending messages to main queue...
Deleting messages from DLQ...
3 messages sent successfully.

Fetching 3 messages from DLQ https://sqs.us-east-1.amazonaws.com/123456789012/MyQueue-dlq...

No more messages to process.
Total messages sent: 9

```
