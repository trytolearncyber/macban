📘 Module 14 — Autonomous Ops Architecture (Section B)

📌 S — Scenario (Nord Bank / Banking-Specific)

Nord Bank একটা একক, বড় Automation তৈরি করেছিল যেটা Network Log Monitor করত, Anomaly বিশ্লেষণ করত, Report লিখত, এবং সরাসরি Remediation Action নিতো — সবকিছু একটা মাত্র Workflow-এর মধ্যে। একদিন Anomaly Detection অংশে একটা Bug আসে, এবং সেই ভুল তথ্য সরাসরি Remediation অংশে চলে যায়, যার ফলে একটা সম্পূর্ণ সুস্থ Device-কে ভুলভাবে Restart করে দেওয়া হয়। কারণ পুরো Logic একটা মাত্র Block-এ ছিল, সমস্যাটা কোথায় শুরু হয়েছিল তা বুঝতেও সময় লেগেছিল।

🚨 Challenge

- একটা মাত্র বড় Automation-এর ভেতরে Monitoring, Analysis, Decision, এবং Action — সবকিছু মিশে ছিল, তাই একটা অংশের ভুল সরাসরি পরের অংশকে প্রভাবিত করেছিল
- কোন অংশে সমস্যা শুরু হয়েছিল তা আলাদা করে বোঝা কঠিন ছিল, কারণ সবকিছু একসাথে চলছিল
- Remediation Action (Device Restart) কোনো Independent Verification ছাড়াই সরাসরি Execute হয়ে গিয়েছিল
- একটা অংশ Update করতে হলে পুরো বড় Automation Touch করতে হতো, যা ঝুঁকিপূর্ণ ছিল

✅ Solution

কাজটাকে আলাদা, স্বাধীনভাবে সিদ্ধান্ত নেওয়া কয়েকটা Agent-এ ভাগ করতে হবে — একটা Monitoring Agent, একটা Analysis Agent, একটা Verification Agent, এবং একটা Remediation Agent — যেখানে প্রতিটা Agent নিজের কাজ শেষে পরের Agent-কে তথ্য পাঠাবে, কিন্তু Remediation Agent কোনো Action নেওয়ার আগে Verification Agent-এর Independent Confirmation ছাড়া এগোবে না।

🎯 T — Task

Nord Bank-এর জন্য একটা Multi-Agent Autonomous Ops Architecture ডিজাইন করতে হবে যেখানে Monitoring, Analysis, Verification, এবং Remediation — প্রতিটা আলাদা Agent হিসেবে কাজ করবে এবং একে অপরকে Independently Check করবে।

👀 O — Output

একটা Autonomous Ops Architecture Document যেখানে থাকবে:
- Agent Role Definition — প্রতিটা Agent (Monitoring, Analysis, Verification, Remediation, Reporting) এর নির্দিষ্ট দায়িত্ব
- Inter-Agent Communication Design — একটা Agent আরেকটাকে কী তথ্য, কোন Format-এ পাঠাবে
- Independent Verification Gate — Remediation Agent Action নেওয়ার আগে Analysis Agent-এর সিদ্ধান্ত আলাদাভাবে Verify হবে কিনা এবং কীভাবে
- Failure Isolation Design — একটা Agent ব্যর্থ বা ভুল তথ্য দিলে তা পরের Agent পর্যন্ত সরাসরি না পৌঁছে কীভাবে আটকানো যায়

🤔 R — Reason

Section A-তে দেখা গিয়েছিল Multi-Agent System মানে শুধু কাজ ভাগ করা না, প্রতিটা Agent-এর নিজস্ব সিদ্ধান্ত নেওয়ার ক্ষমতা থাকা। Nord Bank-এর Scenario-তে দেখা যায় যে সবকিছু এক জায়গায় থাকলে একটা ভুল সরাসরি Action পর্যন্ত পৌঁছে যায়। যদি Verification একটা আলাদা, Independent Agent হয় (Analysis Agent নিজেই নিজের কাজ Verify না করে), তাহলে একটা Agent-এর ভুল ধরা পড়ার সুযোগ তৈরি হয় আরেকটা Agent-এর মাধ্যমে, বিশেষ করে Critical, Irreversible Action নেওয়ার আগে।

🏦 Real-World Use Case

Nord Bank-এর নতুন Architecture-এ, Monitoring Agent একটা Anomaly দেখে সেটা Analysis Agent-কে পাঠায়। Analysis Agent বলে "এই Device Restart দরকার।" কিন্তু Remediation Agent সরাসরি Restart না করে প্রথমে Verification Agent-কে জিজ্ঞেস করে, যে Device-এর সাম্প্রতিক Health Metric আলাদাভাবে Check করে নিশ্চিত করে যে সমস্যাটা আসলেই আছে। দুটো Agent একমত হলেই Remediation Agent Action নেয়; না মিললে, Human-কে জানানো হয়।

🧠 Memory Tip

Independent Verification Gate-কে ভাবা যেতে পারে "Two-Person Rule" (যেমন Nuclear Launch Code)-এর মতো — একজনের সিদ্ধান্তে বড়, Irreversible Action নেওয়া হয় না, দ্বিতীয় একজন আলাদাভাবে নিশ্চিত করলে তবেই এগোনো হয়।

⚠️ L — Limitation

- Independent Verification যোগ করলে Response Time বেড়ে যায় — সত্যিই জরুরি এবং সময়-সংবেদনশীল সমস্যায় এই Extra ধাপ ক্ষতিকর হতে পারে
- যদি Monitoring Agent এবং Verification Agent দুটোই একই মূল Data Source-এর উপর নির্ভর করে (যেমন একই Monitoring Tool), তাহলে সেই Source-এই ভুল থাকলে দুটো Agent-ই একসাথে ভুল করবে — Independent Verification তখন প্রকৃতপক্ষে Independent থাকে না
- একাধিক Agent-এর মধ্যে Communication ব্যর্থ হলে (Message হারিয়ে যাওয়া), পুরো Chain আটকে যেতে পারে, এবং কে দায়ী তা বোঝা কঠিন হয়ে যায়
- এই Architecture জটিলতা বাড়ায় — ছোট, কম-ঝুঁকির কাজের জন্য এতগুলো Agent এবং Verification Layer অপ্রয়োজনীয় Overhead হতে পারে

✋ Y — Your Turn

Nord Bank-এর Verification Agent যদি Monitoring Agent-এর মতোই একই Monitoring Tool থেকে তথ্য নেয় (আলাদা কোনো Source না থেকে), তাহলে এই "Independent Verification" আসলে কতটা প্রকৃত Independent বলে মনে হয়, এবং এই সমস্যা এড়াতে কী করা যেতে পারে তা ২-৩ বাক্যে লিখতে হবে।
