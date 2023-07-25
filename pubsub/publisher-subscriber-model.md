---
description: Event-driven services explained
---

# 👻 Publisher Subscriber Model

<figure><img src="../.gitbook/assets/image (59).png" alt=""><figcaption><p>PubSub</p></figcaption></figure>

Let's say S1 wanted to send a message to both S0 and S1, the usual approach when using a Request/Response model would be to send them asynchronously.

This works fine until service ends up having to wait.

### <mark style="color:red;">Strong Coupling</mark>

Consider S2 sending requests to both S3 and S4, even asynchronously it has to wait until both has finished executing.

### <mark style="color:green;">Failure Latency</mark>

Imagine S4 failed for some reason, you have to S2 waiting for it to complete. After a certain period of time, it sends a timeout to S1 which in turn sends a timeout to the Client. \
All this adds up to the time takes for a request to fail.

### <mark style="color:yellow;">Inconsistent Data</mark>

S1 executed properly and made some changes to the data, S2 did not and its data is stale.\
What happens when S1 receives another request?\
You have S1 making changes to its data but the data with S2 would be inconsistent with the rest.



## Enter the PubSub Model

<figure><img src="../.gitbook/assets/image (4).png" alt=""><figcaption><p>Message Brokers</p></figcaption></figure>

Conflicts due to requests not going through can be handled by an intermediary. Let's call it a Message Broker. A popular example of which would be Kafka.

Instead of us following a Request/Response model Kafka would do it for us.

One thing we note here is <mark style="color:blue;">message persistence</mark>, the broker persists the message until it goes through.

<mark style="color:green;">Fault Tolerance</mark> and <mark style="color:orange;">Abstraction</mark> is an advantages of using a broker. S1 doesn't need to worry about who subscribes to its message. You can have S5 subscribe to the broker and receive its messages.\
The broker persists a message until it is received by a Service hence you don't have worry about it timing out and leading the problems we mentioned before.



