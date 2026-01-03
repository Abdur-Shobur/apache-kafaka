# Event-Driven Architecture

Event-Driven Architecture = “ঘটনা ঘটলে জানাও, কে কী করবে সেটা সে নিজে ঠিক করবে”

- কোনো ঘটনা (event) ঘটলেই সিস্টেম নিজে নিজে react করবে
- এক সিস্টেম অন্যটাকে ডাকবে না
- বরং event ছুড়ে দেবে, যে দরকার সে শুনবে

# Event কী?

- User signup করলো
- Order place হলো
- Payment successful
- Product out of stock

```js
OrderCreated
{
  orderId: 101,
  userId: 5,
  amount: 1200
}

```

# Traditional (Request-Driven) vs Event-Driven

**Traditional system**

```
Order Service
   → Payment Service
      → Email Service
         → Inventory Service

```

**সমস্যা:**

- Tight coupling
- একটা service down = সব down
- Slow

**Event-Driven system**

```
Order Service
   → Kafka (OrderCreated event)
        ├→ Payment Service
        ├→ Email Service
        └→ Inventory Service

```

- Order Service কাউকে চেনে না
- শুধু event publish করে

**Kafka এখানে কী করে?**

- Event receive করে
- Store করে
- Multiple consumer-কে দেয়
- Kafka = Event Backbone

# Event-Driven Architecture এর সুবিধা

- Loose coupling
- Easily scalable
- Fault tolerant
- Real-time processing
- New service যোগ করা সহজ

# Real-life analogy

Courier system

- তুমি parcel পাঠাও (event)
- কে receive করবে জানো না
- যে দরকার সে collect করে

# Kafka ছাড়া vs Kafka সহ

| Without Kafka      | With Kafka           |
| ------------------ | -------------------- |
| Direct API call    | Event publish        |
| Service dependency | Independent services |
| Hard to scale      | Easy to scale        |
