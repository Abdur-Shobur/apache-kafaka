# এটি রিয়েল-টাইমে অনেক বড় পরিমাণ ডেটা publish, store, এবং process করতে ব্যবহৃত হয়

# Publish

- Publish মানে হলো → ডেটা পাঠানো / ইভেন্ট পাঠানো

**উদাহরণ:**

- একজন ইউজার login করলো
- একজন ইউজার order দিলো
- কোনো সেন্সর temperature পাঠালো
  - এই ঘটনাগুলোকে বলে event
  - এই event-গুলো Producer Kafka-তে পাঠায় (publish করে)

```
User Login → Producer → Kafka Topic

```

---

# Store

- Kafka শুধু ডেটা পাঠায় না,
- এটা ডেটা সংরক্ষণও করে (store)।
  - ডেটা disk-এ লেখা থাকে
  - ঘণ্টা, দিন, এমনকি মাস পর্যন্ত রাখা যায়
  - পরে চাইলে আবার পড়া যায়
- তাই Kafka শুধু “পাইপ” না,
- এটা একটা durable log storage system

---

# Process

- Process মানে → ডেটার ওপর কাজ করা

**উদাহরণ:**

- Order আসলে total হিসাব করা
- Login হলে notification পাঠানো
- Fraud detect করা
- Real-time dashboard আপডেট করা
  - Consumer অ্যাপ্লিকেশনগুলো এই কাজ করে
  - Kafka নিজে খুব কম processing করে
  - কিন্তু এটি processing করার সুযোগ তৈরি করে
- (যেমন: Kafka Streams, Flink, Spark)

---

# রিয়েল-টাইম

- ডেটা আসছে
- সাথে সাথে process হচ্ছে
- delay খুবই কম (milliseconds)
- User order দিলো → 10–50 ms এর মধ্যে system জানলো

---

# অনেক বড় পরিমাণ ডেটা

Kafka handle করতে পারে:

- প্রতি সেকেন্ডে লাখ / কোটি message
- TB থেকে PB পরিমাণ ডেটা

- এই জন্যই একে বলে high throughput system

**Kafka রিয়েল-টাইমে ইভেন্ট পাঠায় (publish),**
**সেগুলো নিরাপদে রাখে (store),**
**এবং অন্য সিস্টেমকে সাথে সাথে কাজ করতে দেয় (process)**
