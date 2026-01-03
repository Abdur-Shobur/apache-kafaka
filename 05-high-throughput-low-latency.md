# Throughput

Throughput = নির্দিষ্ট সময়ে কতগুলো message process করা যায়

**উদাহরণ:**

- 1 second এ 1,000 message
- 1 second এ 1,000,000 message
- বেশি message = High throughput

# Latency

Latency = message পাঠানো থেকে process শুরু হওয়া পর্যন্ত সময়

**উদাহরণ:**

- 5 ms
- 50 ms
- 500 ms
- কম সময় = Low latency

# Kafka-তে High Throughput কীভাবে আসে?

1.  Partitioning

- Topic কে অনেক partition-এ ভাগ করা
- Parallel write & read হয়

```
Topic
├─ Partition 1
├─ Partition 2
└─ Partition 3

```

2.  Sequential Disk Write

- Random write নয়
- Disk-এ এক লাইনে লেখা → খুব fast

3. Batch Processing

- একটার পর একটা না
- অনেক message একসাথে পাঠানো

4. Zero-copy

- OS level optimization
- CPU কম ব্যবহার হয়

# Low Latency কীভাবে আসে?

Producer side

- Async send
- Batch + compression

Consumer side

- Pull-based model
- Offset control

# Throughput vs Latency একসাথে কেন গুরুত্বপূর্ণ?

| শুধু throughput | শুধু latency |
| --------------- | ------------ |
| Fast bulk       | Fast single  |
| Real-time না    | Scale হয় না  |

# Kafka

High throughput = একসাথে অনেক ডেটা
Low latency = খুব দ্রুত response
Kafka = দুটোই একসাথে
