# Producer

- Producer = ডেটা পাঠানোর সিস্টেম বা অ্যাপ্লিকেশন
- Kafka-তে message তৈরি করে topic-এ পাঠায়

উদাহরণ:

```
User Service → sends "UserLoggedIn" event → Kafka
```

Producer বৈশিষ্ট্য:

- Async বা sync হতে পারে
- অনেকগুলো message একসাথে পাঠাতে পারে (batch)
- Kafka brokers-এর load কমানোর জন্য compression ব্যবহার করতে পারে

# Topic

- Topic = ডেটা রাখার ক্যাটাগরি / নাম
- সমস্ত message একটি topic-এ organize হয়

উদাহরণ:

```
"user-login", "orders", "payments"
```

Producer বৈশিষ্ট্য:

- Durable → Disk-এ লেখা থাকে
- Multiple producer পাঠাতে পারে
- Multiple consumer পড়তে পারে

# Partition

- Partition = Topic-এর ভেতরের ভাগ
- Scalability ও parallelism বাড়ায়

উদাহরণ:

```
Topic: orders
Partitions: P0, P1, P2
```

Producer বৈশিষ্ট্য:

- প্রতিটি partition ordered
- Partition → Single broker host করতে পারে
- High throughput দেয় কারণ multiple partition একসাথে read/write করা যায়

# Broker

- Broker = Kafka server
- একটি Kafka cluster-এ অনেক broker থাকতে পারে
- Broker = message store + topic management

উদাহরণ:

```
Broker 1 → Partition 0
Broker 2 → Partition 1
Broker 3 → Partition 2
```

Producer বৈশিষ্ট্য:

- Replication করে data loss কমায়
- Consumer requests serve করে

# Consumer

- Consumer = message পড়ে এবং process করে
- এক বা একাধিক consumer হতে পারে

উদাহরণ:

```
Email Service reads "OrderCreated" event → send confirmation email

```

Producer বৈশিষ্ট্য:

- Pull-based → নিজে চাইলে message নেয়
- Offset ধরে রাখে → পুনরায় start করা যায়

# Consumer Group

- Consumer Group = একাধিক consumer মিলে কাজ করে
- Group-এর প্রতিটি consumer unique partition পড়ে
- এক group → message একবার read করে
- এক message একাধিক group → multiple times read হতে পারে

উদাহরণ:

```
Group 1 (Payment Service) → reads partitions P0, P1
Group 2 (Analytics Service) → reads same partitions P0, P1
```

```
Producer → Topic "orders" → Partitions [P0, P1, P2] → Broker Cluster
                                      ↓
                                Consumer Group 1 → Payment Service
                                Consumer Group 2 → Analytics Service

```

Producer বৈশিষ্ট্য:

- Pull-based → নিজে চাইলে message নেয়
- Offset ধরে রাখে → পুনরায় start করা যায়

**Producer → message পাঠায়**
**Topic → message রাখে**
**Partition → topic ভাগ করে throughput বাড়ায়**
**Broker → server যা store করে**
**Consumer → message পড়ে**
**Consumer Group → একাধিক consumer মিলে কাজ করে**
