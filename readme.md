# Apache Kafka কী?

- Apache Kafka হলো একটি distributed event streaming platform
- এটি রিয়েল-টাইমে অনেক বড় পরিমাণ ডেটা publish, store, এবং process করতে ব্যবহৃত হয়
- Kafka একটি মেসেজিং সিস্টেম, কিন্তু খুবই দ্রুত, স্কেলেবল এবং নির্ভরযোগ্য
- এক সিস্টেম থেকে অন্য সিস্টেমে ডেটা পাঠাতে ব্যবহৃত হয়
- Netflix, LinkedIn, Uber, Spotify-এর মতো বড় কোম্পানিগুলো ব্যবহার করে

---

# Kafka কেন ব্যবহার করা হয়?

- Real-time data streaming
- Log collection & analysis
- Event-driven architecture
- High throughput & low latency
- Microservices communication

---

# Kafka-র মূল অংশগুলো

- Producer
  -- ডেটা পাঠায় (message produce করে)
- Topic
  --ডেটা রাখার ক্যাটাগরি (যেমন: user-login, orders)
- Partition
  -- Topic-এর ভেতরের ভাগ (scalability বাড়ায়)
- Broker
  -- Kafka server
- Consumer
  -- ডেটা পড়ে (consume করে)
- Consumer Group
  -- একাধিক consumer মিলে কাজ করে

--

# Kafka কোথায় বেশি ব্যবহৃত হয়?

- Website activity tracking
- Chat / Notification system
- IoT data processing
- Big Data pipelines
- Real-time analytics
