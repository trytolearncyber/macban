📘 Module 09 — Self-Service Portal Architecture (Section B)

📌 S — Scenario (Nord Bank / Banking-Specific)

Nord Bank-এর একটা Branch Staff-এর Password Reset দরকার হলে, তাকে একটা Ticket খুলতে হয়, তারপর IT Team সেটা Manually Verify করে Reset করে দেয়। প্রতিদিন এরকম ৩০-৪০টা Simple, একই ধরনের Ticket আসে, যার প্রতিটাতে IT Team-এর ৫-১০ মিনিট সময় যায়। এই ছোট কাজগুলোর জন্য পুরো IT Team-এর একটা বড় অংশ সময় ব্যয় হয়ে যায়, যেখানে জটিল সমস্যা সমাধানে দেওয়ার মতো সময় কমে যায়।

🚨 Challenge

- Simple, Repetitive Request (Password Reset)-এর জন্যও IT Team-এর Manual Time ব্যয় হচ্ছিল
- Staff-দের অপেক্ষা করতে হচ্ছিল, যদিও কাজটা নীতিগতভাবে তাৎক্ষণিক হওয়া উচিত ছিল
- কে কী Request করতে পারবে তার কোনো স্পষ্ট Boundary ছিল না — সবাই একইভাবে যেকোনো Ticket খুলতে পারত
- Approval ছাড়া Sensitive Action (যেমন VPN Access দেওয়া) Self-Service-এ দিলে Security Risk তৈরি হতে পারত

✅ Solution

একটা Self-Service Portal তৈরি করতে হবে যেখানে নির্দিষ্ট, Low-Risk Request (যেমন Password Reset) Staff নিজেই সম্পন্ন করতে পারবে, কিন্তু Sensitive Request (যেমন VPN Access) এখনও Approval-এর মধ্য দিয়ে যাবে — সবকিছু Role-Based Access Control (RBAC) দিয়ে নিয়ন্ত্রিত থাকবে।

🎯 T — Task

Nord Bank-এর জন্য একটা Self-Service Portal Architecture ডিজাইন করতে হবে যেখানে একটা Service Catalog থাকবে, RBAC দিয়ে Access নিয়ন্ত্রিত হবে, এবং Sensitive Action Approval Workflow দিয়ে সুরক্ষিত থাকবে।

👀 O — Output

একটা Self-Service Portal Architecture Document যেখানে থাকবে:
- Service Catalog Design — কোন কোন Request Self-Service-এ থাকবে (Password Reset, Port Enable/Disable, VPN User Creation)
- RBAC Model — Admin, Engineer, Viewer Role-এর জন্য আলাদা Permission
- Low-Risk vs High-Risk Request-এর জন্য আলাদা Path — একটায় সরাসরি Execute, অন্যটায় Approval দরকার
- Confirmation ও Logging Design — প্রতিটা Self-Service Action কীভাবে Track হবে

🤔 R — Reason

সব IT Request একই গুরুত্বের না। Password Reset-এর মতো Low-Risk, Well-Defined কাজে Manual Approval Process যোগ করা অপ্রয়োজনীয় Delay তৈরি করে, কিন্তু VPN Access-এর মতো Sensitive কাজে Approval ছাড়া Direct Self-Service দিলে Security Risk বাড়ে। তাই একটা ভালো Self-Service Design Risk অনুযায়ী আলাদা Path তৈরি করে — সবকিছুকে এক করে ফেলে না।

🏦 Real-World Use Case

Nord Bank একটা Portal তৈরি করে যেখানে Staff নিজে Password Reset করতে পারে সাথে সাথে, কিন্তু VPN Access Request করলে সেটা প্রথমে তার Manager-এর কাছে Approval-এর জন্য যায়, Approve হলেই তবে Automation FortiGate-এ VPN User তৈরি করে। প্রতিটা Action, Approve হোক বা না হোক, একটা Log-এ Record হয়।

🧠 Memory Tip

Self-Service Portal-কে ভাবা যেতে পারে একটা "ATM Booth"-এর মতো — সাধারণ Cash Withdrawal নিজে থেকেই করা যায়, কিন্তু বড় Amount-এর Transaction বা বিশেষ Request-এর জন্য এখনও Branch-এ গিয়ে Staff-এর Approval লাগে।

⚠️ L — Limitation

- Low-Risk বলে চিহ্নিত করা একটা Request আসলে সবসময় Low-Risk না-ও হতে পারে — যেমন একটা Compromised Account থেকে করা "নিরীহ" Password Reset Request Attacker-কে Account Lock করে দেওয়ার সুযোগ দিতে পারে
- RBAC ঠিকভাবে Maintain না করলে (যেমন কারো Role Change হওয়ার পরও পুরোনো Permission থেকে যাওয়া) সময়ের সাথে Access Control দুর্বল হয়ে যায়
- Approval Workflow-এ Manager Available না থাকলে (Vacation, Leave), Legitimate Sensitive Request-ও আটকে থাকতে পারে যদি Backup Approver আগে থেকে ঠিক করা না থাকে
- Self-Service Portal নিজেই একটা Attack Surface — এটার নিজের Login এবং Session Security দুর্বল হলে পুরো Portal-ই একটা নতুন ঝুঁকি হয়ে দাঁড়াতে পারে

✋ Y — Your Turn

Nord Bank-এর জন্য আরেকটা IT Request (যেমন New Employee Laptop Access বা Printer Access) চিন্তা করে লিখতে হবে — সেটা Low-Risk (সরাসরি Self-Service) নাকি High-Risk (Approval দরকার) হওয়া উচিত, এবং কেন, ২-৩ বাক্যে ব্যাখ্যা করতে হবে।
