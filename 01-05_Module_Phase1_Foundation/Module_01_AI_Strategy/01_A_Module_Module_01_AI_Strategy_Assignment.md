# 📘 Module 01 — AI Strategy & System Architecture Foundation

## Section A: 01_Introduction to AI Automation & Agents

---

## 📌 S — Scenario

Nord Bank-এর NOC (Network Operations Center) Team প্রতিদিন সকালে ৫০০+ Device-এর Status manually check করে। প্রতিটা Device আলাদা করে Login করে দেখতে হয় — Router online আছে কিনা, Firewall ঠিকমতো কাজ করছে কিনা। এই কাজে প্রতিদিন ৪ ঘন্টা সময় লাগে, এবং Engineer ক্লান্ত হয়ে গেলে কোনো Device miss করার সম্ভাবনা থাকে।

---

## 🎯 T — Task

আজকে শেখা হবে AI Automation এবং AI Agent আসলে কী, এবং কীভাবে এগুলো এই ধরনের Repetitive কাজ সমাধান করতে পারে। চারটি প্রধান Agent Type বোঝা হবে।

---

## 👀 O — Output

এই Module শেষে স্পষ্ট ধারণা থাকবে:

- AI Automation কী এবং কেন এটি ব্যবহার করা হয়
- চারটি AI Agent Type-এর পার্থক্য
- কোন Banking Scenario-তে কোন Agent Type উপযুক্ত

---

## 🤔 R — Reason

### Concept Explanation

AI Automation হলো এমন একটি পদ্ধতি যেখানে System নিজে থেকেই Decision নিতে পারে এবং Action নিতে পারে, মানুষের বার বার হস্তক্ষেপ ছাড়াই। এর ভিত্তি হলো AI Agent।

### চারটি AI Agent Type

| Agent Type | Simple Explanation |
|------------|--------------------|
| Simple Reflex Agent | শুধু বর্তমান অবস্থা দেখে সাথে সাথে react করে, কোনো History মনে রাখে না |
| Model-Based Agent | বর্তমান অবস্থার সাথে আগের অবস্থাও মনে রাখে, তুলনা করে Decision নেয় |
| Goal-Based Agent | একটি নির্দিষ্ট Goal অর্জনের জন্য বিভিন্ন পথ চিন্তা করে |
| Utility-Based Agent | একাধিক Option-এর মধ্যে সবচেয়ে ভালো Option বেছে নেয় (Cost, Speed ইত্যাদি বিবেচনা করে) |

### কেন এই পদ্ধতি ব্যবহার করা হয়?

Manual Process-এ Human Error হওয়ার সম্ভাবনা থাকে এবং সময় বেশি লাগে। AI Agent ব্যবহার করলে কাজ দ্রুত, সঠিক, এবং ২৪/৭ চলতে পারে।

---

## 📊 Simple Diagram

```text
  ::view-transition-group(*),
  ::view-transition-old(*),
  ::view-transition-new(*) {
    animation-duration: 0.25s;
    animation-timing-function: cubic-bezier(0.19, 1, 0.22, 1);
  }

Vvisualize
Vvisualize show_widget
```

---

## 🏦 Real-World Use Case

Nord Bank-এর Network Fault Prediction এ Goal-Based Agent ব্যবহার করা যায় — যার Goal হলো **"99.9% Uptime বজায় রাখা"**। এই Agent Nagios/Zabbix থেকে Device Status নিয়ে, যখনই কোনো Pattern দেখবে যে Device Down হওয়ার সম্ভাবনা আছে, তখনই Proactive Action নেবে।

---

## 🧠 Memory Tip

- **Reflex** = এখন দেখি, এখন করি
- **Model** = আগে দেখেছি, মনে রাখি
- **Goal** = কোথায় পৌঁছাতে চাই
- **Utility** = কোনটা সবচেয়ে ভালো

---

## ✋ Y — Your Turn

নিচের তিনটি Banking Scenario পড়ে প্রতিটার জন্য সঠিক Agent Type বেছে নিন (**Simple Reflex / Model-Based / Goal-Based / Utility-Based**):

1. ATM-এ Cash কম থাকলে সাথে সাথে **"Cash Low" Alert** পাঠানো
2. একটি Branch-এর VPN গত ৩ বার Disconnect হয়েছে, তাই এখন Pattern দেখে Predict করা যে আবার Disconnect হতে পারে
3. একটি Security Incident-এ Email, SMS, এবং Phone Call — এই তিনটার মধ্যে কোনটা পাঠানো হবে তা Severity অনুযায়ী ঠিক করা
