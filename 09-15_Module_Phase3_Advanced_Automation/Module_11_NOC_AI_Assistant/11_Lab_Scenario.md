# 🧪 Lab 11 — Complete NOC AI Assistant (11A + 11B in One Workflow)

## 📌 Scenario

একজন NOC Engineer Query:

| # | Query                          | Intent                                 |
| - | ------------------------------ | -------------------------------------- |
| 1 | "কয়টা Branch Down?"           | Count জানতে চাওয়া হয়                 |
| 2 | "কোন কোন Branch Down?"         | List জানতে চাওয়া হয়                  |
| 3 | "Firewall Throughput কেমন?"    | Trend জানতে চাওয়া হয়                 |
| 4 | "Branch Status?"               | অস্পষ্ট Query → Clarification প্রয়োজন |
| 5 | "Dhanmondi Router Restart করো" | Action Request → Approval প্রয়োজন     |

---

## ✅ AI Assistant Flow

| Query                          | AI Assistant Process                                                                                     |
| ------------------------------ | -------------------------------------------------------------------------------------------------------- |
| "কয়টা Branch Down?"           | Count Query শনাক্ত করা হয় → Data আনা হয় → "৪ টি Down" উত্তর প্রদান করা হয়                             |
| "কোন কোন Branch Down?"         | List Query শনাক্ত করা হয় → Data আনা হয় → Branch List প্রদান করা হয়                                    |
| "Firewall Throughput কেমন?"    | Trend Query শনাক্ত করা হয় → Data আনা হয় → Trend Summary প্রদান করা হয়                                 |
| "Branch Status?"               | Query অস্পষ্ট হিসেবে শনাক্ত করা হয় → Clarifying Question করা হয়                                        |
| "Dhanmondi Router Restart করো" | Action Request শনাক্ত করা হয় → Approval Request পাঠানো হয় → Approval পাওয়ার পর Action Execute করা হয় |

---

## 🎯 Workflow Components

| Feature                |    11A (Information)    | 11B (Action) |
| ---------------------- | :---------------------: | :----------: |
| Webhook                |            ✅            |       ✅      |
| AI Agent               |            ✅            |       ✅      |
| Model + Memory         |            ✅            |       ✅      |
| Inventory Tool         |    ✅ (Cisco ASR 1000)   |       -      |
| Branches Tool          | ✅ (Cisco Catalyst 9500) |       -      |
| Action Tool            |            -            |  ✅ (Restart) |
| Create Request         |            -            |       ✅      |
| Approval Email         |            -            |       ✅      |
| Wait + Check           |            -            |       ✅      |
| Success / Reject Email |            -            |       ✅      |

---

## 📊 Complete Workflow Structure

```text
┌─────────────────────────────────────────────────────────────────────────────┐
│                 COMPLETE NOC AI ASSISTANT (11A + 11B)                      │
├─────────────────────────────────────────────────────────────────────────────┤
│                                                                             │
│   🌐 Webhook (/webhook/chat)                                                │
│   └── Body: { "query": "কয়টা Branch Down?" }                              │
│        │                                                                    │
│        ▼                                                                    │
│   🤖 AI Agent                                                               │
│   ├── System Prompt                                                         │
│   ├── Model (Mistral)                                                       │
│   ├── Memory                                                                │
│   └── Tools                                                                 │
│       ├── HTTP Request (Inventory)                                          │
│       ├── HTTP Request (Branches)                                           │
│       └── HTTP Request (Action)                                             │
│        │                                                                    │
│        ▼                                                                    │
│   🔀 Check Action Request                                                   │
│        │                                                                    │
│   ┌────┴─────────────────────────────┐                                      │
│   ▼                                  ▼                                      │
│ Information Flow                Action Flow                                 │
│ Count / List / Trend            ├── Create Request                          │
│                                 ├── Approval Email                          │
│                                 ├── Wait                                    │
│                                 ├── Check Status                            │
│                                 ├── Approve / Reject                        │
│                                 ├── Execute Action                          │
│                                 ├── Success / Reject Email                  │
│                                 └── Format Response                         │
│             │                     │                                          │
│             └───────────┬─────────┘                                          │
│                         ▼                                                    │
│                  🧹 Clean Output                                             │
│                         │                                                    │
│                         ▼                                                    │
│                 📤 Respond to Webhook                                       │
│                                                                             │
└─────────────────────────────────────────────────────────────────────────────┘
```

---

## 🧠 Key Points

* **One Workflow → Everything is Handled**
* **Information Request → Direct Response**
* **Action Request → Approval → Execution**

---

## 🎯 Summary

একটি Workflow-এর মধ্যেই **Information Query** এবং **Action Request** উভয়ই পরিচালনা করা হয়।

Information Query-এর ক্ষেত্রে **Intent Recognition**, **Data Source Selection**, এবং **Response Generation** সম্পন্ন করা হয়।

Action Request-এর ক্ষেত্রে **Confirmation**, **Approval**, এবং **Execution** ধাপে ধাপে সম্পন্ন করা হয়।

ফলে একটি AI Assistant-এর মাধ্যমে তথ্য সংগ্রহ এবং Operational Action একই Workflow-এর মধ্যে সম্পন্ন করা যায়।

---

## 🚀 Lab Goal

এই Lab-এর শেষে একটি **Complete NOC AI Assistant Workflow** তৈরি করা হবে, যেখানে Information Query এবং Action Request একই Workflow-এর মাধ্যমে পরিচালিত হবে।
vv