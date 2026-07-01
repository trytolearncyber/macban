📘 Module 03 — Production Automation Environment Setup
Section A: Setting Up Your Automation Environment (n8n self-hosted/cloud)

📌 S — Scenario

Nord Bank-এর Automation Engineer Concept বোঝার পর এখন প্রশ্ন করছে — "n8n আসলে কোথায় Install করবো? নিজের Server-এ, নাকি Cloud-এ?" কোনো স্পষ্ট ধারণা ছাড়া শুরু করলে ভুল Environment বেছে নেওয়ার ঝুঁকি থাকে।

🎯 T — Task

n8n চালানোর জন্য কোন কোন Environment Option আছে তা বোঝা হবে:

- n8n Self-Hosted (Docker/NPM)
- n8n Cloud
- Docker ও Docker Compose-এর ভূমিকা
- প্রথম Login ও Basic Setup ধারণা

👀 O — Output

এই Section শেষে থাকবে:

- Self-Hosted vs Cloud-এর মধ্যে পার্থক্যের ধারণা
- Docker কেন ব্যবহার করা হয় তার বোঝাপড়া
- n8n Environment Setup Checklist সম্পন্ন করার যোগ্যতা

🤔 R — Reason

Concept Explanation

n8n চালানোর দুটি প্রধান উপায় আছে।

| Option | → | Simple Explanation |
|---|---|---|
| Self-Hosted | → | নিজের Server বা Computer-এ n8n Install করে চালানো, Data সম্পূর্ণ নিজের নিয়ন্ত্রণে থাকে |
| n8n Cloud | → | n8n-এর নিজস্ব Cloud Server-এ Account খুলে ব্যবহার করা, Setup করতে হয় না কিন্তু Data বাইরে যায় |

Docker কী এবং কেন প্রয়োজন

Docker → Application-কে আলাদা Container-এ চালানোর Tool। n8n-কে Docker-এ চালালে এটি অন্য কোনো System-এর সাথে Conflict করে না এবং একটি Server থেকে আরেকটিতে সহজেই সরানো যায়।

Docker Compose → একাধিক Container (যেমন n8n + Database) একসাথে পরিচালনা করার Tool।

কেন Self-Hosted Banking-এর জন্য গুরুত্বপূর্ণ?

Banking Data কখনোই বাইরের Server-এ যাওয়া উচিত নয় (Module 02-এ আলোচিত Data Sovereignty মনে আছে?)। তাই বেশিরভাগ Bank Self-Hosted Option বেছে নেয়, Docker ব্যবহার করে।

📊 Simple Diagram
n8n setup choice

Self-hosted via Docker
Data stays on bank servers
Preferred for banking

n8n cloud
Data leaves bank servers
Not preferred for banking


🏦 Real-World Use Case

Nord Bank-এর Network Team নিজেদের Data Center-এ একটি Ubuntu Server-এ Docker দিয়ে n8n চালায়। ফলে কোনো Transaction বা Network Log কখনোই বাইরের কোনো Server-এ যায় না, যা Bangladesh Bank-এর Compliance Requirement পূরণ করে।

🧠 Memory Tip

**Self-Hosted = নিজের ঘর** (Control নিজের হাতে)
**Cloud = ভাড়া বাসা** (Setup সহজ, কিন্তু Control কম)

✋ Y — Your Turn

নিজের ভাষায় ৩-৪ লাইনে ব্যাখ্যা করুন (Example কপি না করে):

একটি Bank যদি n8n Cloud ব্যবহার করে Customer Transaction Workflow চালায়, তাহলে কী কী ঝুঁকি তৈরি হতে পারে? Self-Hosted Option কীভাবে এই ঝুঁকি কমাতে পারে?

🎯 Deliverable: Environment Setup Checklist সম্পন্ন করা

---
ℹ️ Note: এই Default Mode-এ শুধু Concept আলোচনা করা হয়েছে। Docker Installation Command, Configuration, এবং Step-by-Step Setup-এর জন্য `/answer` Mode ব্যবহার করতে পারেন।