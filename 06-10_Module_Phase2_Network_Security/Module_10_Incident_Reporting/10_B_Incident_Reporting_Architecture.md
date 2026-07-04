📘 Module 10 — Incident Reporting Architecture (Section B)

📌 S — Scenario (Nord Bank / Banking-Specific)

Nord Bank-এ একটা বড় Network Outage হওয়ার পর, Senior Management একটা Post-Incident Report চেয়েছিল — কী ঘটেছিল, কতক্ষণ স্থায়ী হয়েছিল, ব্যবসায় কী প্রভাব পড়েছিল, এবং ভবিষ্যতে কীভাবে এড়ানো যাবে। NOC Team তখন বিভিন্ন Log আর Chat History ঘেঁটে হাতে Report লিখতে বসে, যাতে প্রায় ২ দিন সময় লেগে যায়, যখন Management দ্রুত উত্তর চাইছিল।

🚨 Challenge

- Incident শেষ হওয়ার পর Report তৈরি করতে অনেক সময় লাগছিল, যখন সবচেয়ে বেশি প্রয়োজন ছিল দ্রুত উত্তরের
- বিভিন্ন Source (Log, Chat, Alert History) থেকে তথ্য জোগাড় করে সময়ানুক্রমিকভাবে (Timeline) সাজানো Manually কঠিন এবং ভুল-প্রবণ ছিল
- Impact Analysis এবং Root Cause প্রায়ই একজন ব্যক্তির স্মৃতি এবং ধারণার উপর নির্ভর করে লেখা হতো, যা Incomplete হতে পারত
- একেক Engineer একেক Format-এ Report লিখত, যার ফলে Report-গুলোর মধ্যে Consistency ছিল না

✅ Solution

Incident-এর সময় সংগৃহীত Log, Alert, এবং Timestamp থেকে স্বয়ংক্রিয়ভাবে একটা প্রাথমিক Timeline এবং Draft Report তৈরি করার একটা System বসাতে হবে, যেখানে LLM ব্যবহার করে Root Cause এবং Remediation-এর প্রাথমিক Suggestion তৈরি হবে, এবং মানুষ শুধু Review ও Finalize করবে।

🎯 T — Task

Nord Bank-এর জন্য একটা AI-Assisted Incident Reporting Architecture ডিজাইন করতে হবে, যা Incident-সংক্রান্ত তথ্য সংগ্রহ করে একটা Structured Timeline, Impact Analysis, এবং Remediation Suggestion সহ একটা Draft Report তৈরি করবে।

👀 O — Output

একটা Incident Reporting Architecture Document যেখানে থাকবে:
- Data Collection Design — কোন কোন Source (Monitoring Log, Alert History, Chat) থেকে তথ্য আসবে
- Timeline Construction Logic — Timestamp অনুযায়ী ঘটনাগুলো কীভাবে সাজানো হবে
- AI-Assisted Root Cause এবং Remediation Suggestion তৈরির Flow
- Human Review এবং Finalization Step — Draft চূড়ান্ত হওয়ার আগে কে এবং কীভাবে যাচাই করবে

🤔 R — Reason

Incident-এর পরপরই দ্রুত এবং Consistent একটা Report থাকা Management-এর সিদ্ধান্ত নেওয়ার জন্য এবং Regulatory Reporting-এর জন্য গুরুত্বপূর্ণ। Manually Timeline সাজানো এবং Root Cause বের করা সময়সাপেক্ষ ও Error-Prone, যেখানে Automation প্রাথমিক Draft তৈরি করে দিলে মানুষের কাজ কমে যায় Verify এবং Refine করাতে, যা অনেক দ্রুত এবং বেশি Consistent হয়।

🏦 Real-World Use Case

Nord Bank-এ একটা Outage হওয়ার পর, একটা Automation স্বয়ংক্রিয়ভাবে Monitoring System এবং Alert Log থেকে সব Timestamp সংগ্রহ করে একটা Draft Timeline তৈরি করে, LLM দিয়ে সম্ভাব্য Root Cause এবং Remediation Suggestion যোগ করে, এবং সেটা NOC Lead-এর কাছে Review-এর জন্য পাঠায়। Report তৈরির সময় ২ দিন থেকে কমে কয়েক ঘন্টায় নেমে আসে।

🧠 Memory Tip

AI-Assisted Incident Report-কে ভাবা যেতে পারে একটা "Court Stenographer"-এর মতো — সবকিছু যেভাবে ঘটেছে তা নির্ভুলভাবে সময়ানুক্রমে লিখে রাখে, কিন্তু চূড়ান্ত রায় (Final Decision) এখনও বিচারক (মানুষ) দেন।

⚠️ L — Limitation

- AI-Generated Root Cause Suggestion সবসময় সঠিক না — এটা Available Log-এর ভিত্তিতে একটা সম্ভাব্য ব্যাখ্যা দেয়, নিশ্চিত সত্য না
- যদি মূল Log বা Alert Data-ই Incomplete বা ভুল হয়, তাহলে তার উপর ভিত্তি করে তৈরি Timeline এবং Root Cause-ও ভুল হবে ("Garbage In, Garbage Out")
- Draft Report-কে Human Review ছাড়া সরাসরি Final হিসেবে পাঠিয়ে দিলে, ভুল Conclusion Management পর্যন্ত পৌঁছে যেতে পারে
- Regulatory বা Legal Context-এ ব্যবহৃত হতে পারে এমন Report-এ AI-Generated Content-এর Accountability কার উপর বর্তাবে তা আগে থেকে স্পষ্ট করা দরকার — Automation নিজে দায়ভার নিতে পারে না

✋ Y — Your Turn

Nord Bank-এর একটা Incident চিন্তা করে লিখতে হবে (যেকোনো ধরনের হতে পারে) — সেই Incident-এর Log Data থেকে AI যদি ভুল Root Cause Suggest করে, তাহলে Human Reviewer কীভাবে সেটা ধরতে পারবে তা ২-৩ বাক্যে ব্যাখ্যা করতে হবে।