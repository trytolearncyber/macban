📘 Module 07 — AI Troubleshooting Architecture (Section B)

📌 S — Scenario (Nord Bank / Banking-Specific)

Nord Bank-এর একটা Branch-এ VPN বারবার Disconnect হচ্ছিল। Junior Engineer Log দেখে বুঝতে পারছিল না সমস্যাটা কোথায় — IKE Phase 1-এ, নাকি Phase 2-এ, নাকি সম্পূর্ণ আলাদা কোনো কারণে। Senior Engineer তখন Available ছিল না, এবং Customer-রা বারবার Complaint করছিল। Team চেয়েছিল এমন একটা System যা Log দেখে অন্তত প্রাথমিক দিকনির্দেশনা দিতে পারে, যাতে Junior Engineer একা প্রথম ধাপগুলো নিতে পারে।

🚨 Challenge

- সব সময় Senior Engineer Available থাকে না, বিশেষ করে রাতে বা ছুটির দিনে
- Junior Engineer-দের Pattern Recognition তৈরি হতে বছরের পর বছর অভিজ্ঞতা লাগে
- Sensitive Log (IP, Account-সম্পর্কিত তথ্য) সরাসরি বাইরের কোনো Public AI Service-এ পাঠানো Bank-এর জন্য Compliance Risk
- ভুল LLM Selection করলে Data Bank-এর বাইরে চলে যেতে পারে, যা Regulatory সমস্যা তৈরি করতে পারে

✅ Solution

একটা AI-Powered Troubleshooting Layer বসাতে হবে যা Log গ্রহণ করে, Sensitive Information Mask/Remove করে, তারপর একটা যথাযথভাবে নির্বাচিত LLM-এর কাছে পাঠিয়ে প্রাথমিক Analysis নিয়ে আসবে। Data Sensitivity অনুযায়ী LLM Option (Local vs Cloud) বেছে নিতে হবে।

🎯 T — Task

Nord Bank-এর জন্য একটা AI-Powered Network Troubleshooting Architecture ডিজাইন করতে হবে, যেখানে LLM Selection, Log Analysis Pipeline, এবং Root Cause Suggestion — সবকিছু Compliance বজায় রেখে কাজ করবে।

👀 O — Output

একটা Architecture Document যেখানে থাকবে:
- LLM Selection Criteria (Cloud vs Local, Data Sensitivity অনুযায়ী)
- Log Analysis Pipeline Design (Log Collection → Sanitization → LLM Analysis → Result)
- Root Cause Suggestion Flow
- Resolution Step Generation-এর জন্য Knowledge Base সংযোগ ধারণা

🤔 R — Reason

Banking Environment-এ Speed এবং Compliance দুটোই সমান গুরুত্বপূর্ণ। দ্রুত Troubleshooting দরকার, কিন্তু Sensitive Data বাইরে পাঠানো যাবে না। তাই এমন একটা Architecture দরকার যা দ্রুত Analysis দেয়, কিন্তু Data Sensitivity অনুযায়ী সঠিক LLM Option (Local বা Enterprise-Secured Cloud) ব্যবহার করে।

🏦 Real-World Use Case

Nord Bank একটা Function তৈরি করে যা Log-এ থাকা IP Address এবং Account Number Mask করে দেয়, তারপর Masked Log-টা LLM-এ পাঠিয়ে Root Cause জানতে চায়। LLM যে উত্তর দেয় তা দিয়ে Junior Engineer প্রথম ধাপ নিতে পারে, আর জটিল হলে Senior Engineer-কে Escalate করে।

🧠 Memory Tip

AI Troubleshooting Layer-কে ভাবা যেতে পারে একজন "Translator"-এর মতো যে একই সাথে দুটো কাজ করে — Sensitive তথ্য আড়াল করা, আর জটিল Log-কে সহজ ভাষায় রূপান্তর করা।

⚠️ L — Limitation

- LLM-এর দেওয়া Root Cause Suggestion সবসময় সঠিক না — এটা একটা Starting Point, চূড়ান্ত সিদ্ধান্ত না
- Log Sanitization (Sensitive Data Mask করা) ভুলভাবে করা হলে হয় গুরুত্বপূর্ণ তথ্য হারিয়ে যাবে, নাহলে Sensitive তথ্য ফাঁক দিয়ে বের হয়ে যেতে পারে
- Local LLM ব্যবহার করলে Data Privacy বাড়ে, কিন্তু সাধারণত Cloud LLM-এর তুলনায় কম Accurate এবং বেশি Infrastructure Cost লাগে
- Critical Production Change (যেমন Config সরাসরি পরিবর্তন) LLM Suggestion-এর ভিত্তিতে Automation নিজে থেকে করতে পারবে না — এখনও Human Approval লাগবে

✋ Y — Your Turn

Nord Bank-এর একটা Log Line কল্পনা করে লিখতে হবে যেখানে Customer Account Number আছে — সেই Log LLM-এ পাঠানোর আগে কী কী তথ্য Mask/Remove করা উচিত এবং কেন, ২-৩ বাক্যে লিখতে হবে।
