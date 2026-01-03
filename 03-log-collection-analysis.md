# Log

- Log মানে হলো → সিস্টেমে যা যা ঘটছে তার লেখা রেকর্ড।
  উদাহরণ:
- User login সফল / ব্যর্থ
- API request আসলো
- Error ঘটলো
- Database query চললো

# Log Collection

- বিভিন্ন জায়গা থেকে log এক জায়গায় জড়ো করা

```
App Server 1 ┐
App Server 2 ├→ Kafka → Log System
App Server 3 ┘

```

- সব log Kafka topic-এ জমা হয়

# Kafka এখানে কী করে?

- Log গুলো real-time এ receive করে
- Store করে (দিন/সপ্তাহ/মাস)
- একাধিক system কে একই log পড়তে দেয়

# Log Analysis

- কতগুলো error হচ্ছে?
- কোন API সবচেয়ে slow?
- কোন user বেশি fail করছে?
- কোন server বেশি problem দিচ্ছে?
- এই কাজগুলো করে:
  - ELK Stack (Elasticsearch + Logstash + Kibana)
  - Splunk
  - Grafana
  - Custom analytics service
- Kafka শুধু মাঝখানের pipeline

# Real-world flow (simple)

```
Application
   ↓
Kafka Producer (logs পাঠায়)
   ↓
Kafka Topic (log store)
   ↓
Consumers
   ├→ Elasticsearch (search)
   ├→ Alert system (email/SMS)
   └→ Dashboard (metrics)

```

# Kafka কেন log collection-এ এত জনপ্রিয়?

- High volume handle করে
- Real-time processing
- Log হারায় না
- Multiple consumer support
- Scalable
- Log collection = সব log এক জায়গায় আনা
- Log analysis = সেই log দেখে সমস্যা ও ট্রেন্ড বোঝা
- Kafka = এই দুটোর মাঝের শক্তিশালী backbone
