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
