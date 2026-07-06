📘 Module 13 — Branch Support Architecture (Section B)

📌 S — Scenario (Nord Bank / Banking-Specific)

Nord Bank-এর ৩০০+ Branch থেকে প্রতিদিন গড়ে ৫০টার বেশি IT Ticket আসে — বেশিরভাগই একই ধরনের সমস্যা (Internet Slow, POS Machine Connection, VPN Down)। IT Team-এর মাত্র ১০ জন সদস্য এই সব Ticket সামলায়, ফলে সহজ সমস্যাও সমাধান পেতে ঘন্টার পর ঘন্টা লেগে যায়, যখন Branch-এ Customer অপেক্ষা করছে।

🚨 Challenge

- Ticket Volume-এর তুলনায় IT Team-এর Size অনেক ছোট
- বেশিরভাগ Ticket আসলে Repetitive এবং একই Troubleshooting Step দিয়ে সমাধানযোগ্য, কিন্তু প্রতিটাই Manually Handle করা হচ্ছিল
- Branch Staff-দের Technical জ্ঞান কম, তাই তারা নিজে থেকে Basic Troubleshooting Step-ও Try করতে পারত না
- Escalation-এর কোনো স্পষ্ট নিয়ম ছিল না — কোন সমস্যা IT Team পর্যন্ত পাঠানো উচিত তা নির্ভর করত Branch Staff-এর ব্যক্তিগত সিদ্ধান্তের উপর

✅ Solution

একটা Tier-1 Support Automation Bot তৈরি করতে হবে যা Branch Staff-এর সাথে সরাসরি কথা বলে সাধারণ সমস্যার জন্য Step-by-Step Troubleshooting Guide দেবে, এবং সমাধান না হলে স্বয়ংক্রিয়ভাবে সঠিক তথ্যসহ IT Team-এর কাছে Escalate করবে।

🎯 T — Task

Nord Bank-এর জন্য একটা Branch IT Support Automation Architecture ডিজাইন করতে হবে যা Common Issue-এর জন্য Bot-ভিত্তিক Tier-1 Support দেবে এবং জটিল সমস্যা IT Team-এর কাছে সঠিকভাবে Escalate করবে।

👀 O — Output

একটা Branch Support Architecture Document যেখানে থাকবে:
- Common Issue Catalog — কোন কোন সমস্যা (Internet Slow, POS Connection, VPN Down) Bot নিজে Handle করবে
- Troubleshooting Step Design — প্রতিটা Issue-এর জন্য কী কী ধাপ Bot Suggest করবে
- Escalation Trigger — কোন শর্তে (যেমন ৩টা ধাপ Try করার পরও সমাধান না হলে) Bot IT Team-কে জানাবে
- Escalation Payload Design — Escalate করার সময় IT Team-কে কী কী তথ্য (Branch, Issue Type, ইতিমধ্যে কী Try করা হয়েছে) দেওয়া হবে, যাতে তাদের আবার প্রথম থেকে জিজ্ঞেস করতে না হয়

🤔 R — Reason

IT Team-এর সীমিত সময় সবচেয়ে বেশি মূল্যবান হওয়া উচিত জটিল সমস্যায়, সহজ Repetitive সমস্যায় না। একটা Bot যদি প্রথমেই Common Issue-এর জন্য Guided Troubleshooting দেয়, তাহলে অনেক সমস্যা IT Team পর্যন্ত পৌঁছানোর আগেই সমাধান হয়ে যায়। আর যেগুলো সমাধান হয় না, সেগুলো যদি প্রয়োজনীয় Context (কী Try করা হয়েছে) সহ Escalate হয়, তাহলে IT Team সময় নষ্ট করে না একই প্রশ্ন আবার জিজ্ঞেস করে।

🏦 Real-World Use Case

Nord Bank-এর একটা Branch-এ POS Machine Connect না হলে, Staff Bot-কে জিজ্ঞেস করে। Bot ধাপে ধাপে জিজ্ঞেস করে Cable ঠিকমতো লাগানো আছে কিনা, Router Restart করা হয়েছে কিনা। যদি এই ধাপগুলোর পরেও সমস্যা থাকে, Bot IT Team-কে জানায় যে "Branch X-এ POS Connection সমস্যা, Cable এবং Router Restart ইতিমধ্যে Try করা হয়েছে, এখনও সমাধান হয়নি" — যাতে IT Team সরাসরি পরের ধাপ থেকে শুরু করতে পারে।

🧠 Memory Tip

Tier-1 Support Bot-কে ভাবা যেতে পারে একটা "Emergency Room-এর Triage Nurse"-এর মতো — প্রাথমিক পরীক্ষা এবং সহজ চিকিৎসা নিজে করে, কিন্তু জটিল কেস হলে ইতিমধ্যে করা পরীক্ষার ফলাফলসহ Doctor-এর কাছে পাঠায়, শূন্য থেকে শুরু করায় না।

⚠️ L — Limitation

- Bot-এর Troubleshooting Step যদি Branch-এর Actual Hardware/Network Setup-এর সাথে না মেলে (প্রতিটা Branch হয়তো একই রকম না), তাহলে দেওয়া Step কার্যকর নাও হতে পারে
- Escalation Trigger খুব কড়া (Strict) হলে, IT Team অপ্রয়োজনীয়ভাবে বেশি Ticket পাবে; খুব Loose হলে, Staff অনেকক্ষণ ধরে Bot-এর সাথে আটকে থাকবে সমাধান না পেয়ে
- Bot নিজে থেকে কোনো Physical Action (যেমন Cable ঠিক করা) নিতে পারে না — এটা শুধু Instruction দিতে পারে, Staff নিজে Follow করতে হবে, যা ভুলভাবে করা হতে পারে
- একই সমস্যা যদি একসাথে অনেক Branch-এ হয় (যেমন একটা Central ISP Outage), Bot প্রতিটাকে আলাদা, Unrelated Ticket হিসেবে Treat করতে পারে, যেখানে আসলে এটা একটা একক, বড় সমস্যা

✋ Y — Your Turn

Nord Bank-এর একটা নতুন সমস্যা (যেমন ATM Card Reader কাজ করছে না) চিন্তা করে লিখতে হবে — এই সমস্যার জন্য Bot কতগুলো Troubleshooting Step Try করার পর Escalate করা উচিত বলে মনে হয়, এবং কেন, তা ২-৩ বাক্যে লিখতে হবে।