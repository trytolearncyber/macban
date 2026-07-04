📘 Module 08 — Resiliency Framework (Section B)

📌 S — Scenario (Nord Bank / Banking-Specific)

Nord Bank-এর একটা Automation প্রতি রাতে সব Branch-এর Firewall Config Backup নিয়ে একটা Central Server-এ পাঠাত। একরাতে Central Server সাময়িকভাবে Full হয়ে যায় এবং Backup Save হয়নি। Automation কোনো Retry ছাড়াই ব্যর্থ হয়ে যায় এবং Silent-ভাবে থেমে যায়। প্রায় ২ সপ্তাহ পর যখন একটা Branch-এর Config Restore করার দরকার হয়, তখন জানা যায় যে গত ২ সপ্তাহের কোনো Backup আসলে হয়নি।

🚨 Challenge

- একটা সাময়িক সমস্যা (Server Full) স্থায়ী Data Loss-এ পরিণত হয়েছিল, কারণ কোনো Retry ছিল না
- Failed Backup সম্পর্কে কেউ জানত না, কারণ কোনো Alert System ছিল না
- Failed Attempt-এর কোনো Record রাখা হয়নি, তাই পরে বোঝা যায়নি কবে থেকে সমস্যা শুরু হয়েছে
- সমস্যা সমাধানের জন্য কোনো Human Escalation Path ছিল না — Automation ব্যর্থ হলে সেটা শুধু Log-এ থেকে যেত, কেউ দেখত না

✅ Solution

Automation-এ একটা Resiliency Layer যোগ করতে হবে যা Retry (ক্রমান্বয়ে বাড়তে থাকা অপেক্ষা সময়সহ), Failed Task-এর জন্য একটা আলাদা Storage (Dead-Letter Queue), Critical Failure-এর জন্য Human Notification, এবং প্রতিটা ধাপের Audit Trail নিশ্চিত করবে।

🎯 T — Task

Nord Bank-এর জন্য একটা Resiliency Framework ডিজাইন করতে হবে যা Automation ব্যর্থ হলে Data Loss প্রতিরোধ করবে এবং সঠিক সময়ে সঠিক মানুষকে জানাবে।

👀 O — Output

একটা Resiliency Architecture Document যেখানে থাকবে:
- Exponential Backoff Retry Strategy (ক্রমান্বয়ে বেশি সময় অপেক্ষা করে আবার চেষ্টা করা)
- Dead-Letter Queue Design — ব্যর্থ Task কোথায় এবং কীভাবে সংরক্ষিত থাকবে
- Human-in-the-Loop Escalation — কখন এবং কাকে জানানো হবে
- Audit Trail Design — প্রতিটা ধাপ কীভাবে Log হবে Compliance-এর জন্য

🤔 R — Reason

Banking-এ Backup এবং Config-এর মতো Critical কাজ ব্যর্থ হলে তা সাথে সাথে ধরা না পড়লে সমস্যাটা সময়ের সাথে আরও বড় হয়ে যায় — যেমন এই Scenario-তে ২ সপ্তাহের Data Loss। একটা ভালো Resiliency Framework শুধু ব্যর্থতা এড়ানোর চেষ্টা করে না, বরং ব্যর্থ হলে দ্রুত সেটা ধরতে এবং সঠিক মানুষকে জানাতে সাহায্য করে, যাতে সমস্যাটা ছোট থাকতেই সমাধান করা যায়।

🏦 Real-World Use Case

Nord Bank পরবর্তীতে এমন একটা System বসায় যেখানে Backup ব্যর্থ হলে প্রথমে ৫টা পর্যন্ত ক্রমান্বয়ে বাড়তে থাকা Wait Time দিয়ে Retry হয়। সবগুলো ব্যর্থ হলে সেই Task একটা Dead-Letter Table-এ Store হয় এবং On-Call Engineer-কে Email পাঠানো হয়। প্রতিটা Attempt (সফল বা ব্যর্থ) Database-এ Log হয়, যাতে পরে Audit-এর সময় দেখা যায় কবে কী হয়েছিল।

🧠 Memory Tip

Resiliency Framework-কে ভাবা যেতে পারে একটা "Smoke Detector + Fire Extinguisher + Emergency Call"-এর সমন্বয়ের মতো — শুধু আগুন প্রতিরোধ করার চেষ্টা না করে, আগুন লাগলে দ্রুত বোঝা, প্রাথমিকভাবে সামলানো, আর প্রয়োজনে মানুষকে জানানো — তিনটাই একসাথে থাকে।

⚠️ L — Limitation

- Retry এবং Dead-Letter Queue থাকলেও, যদি মূল সমস্যা (যেমন Server-এর Disk Full) দীর্ঘ সময় সমাধান না হয়, তাহলে সাময়িক ব্যবস্থা শেষ পর্যন্ত কাজ করবে না
- Audit Trail বেশি বিস্তারিত রাখলে Storage এবং Performance Cost বেড়ে যায় — কতটা বিস্তারিত রাখা উচিত তা একটা Trade-off
- Human-in-the-Loop Escalation থাকলেও, যদি নির্ধারিত ব্যক্তি সময়মতো সাড়া না দেয় (Phone বন্ধ, Vacation), তাহলে Escalation Chain-এ পরবর্তী ধাপ আগে থেকে ঠিক করা না থাকলে সমস্যা আটকেই থাকবে
- Critical Production System-এ (যেমন সরাসরি Core Banking Config পরিবর্তন) স্বয়ংক্রিয় Retry কখনো কখনো বিপজ্জনক হতে পারে যদি একই Action দুইবার Apply হয়ে যায় — তাই Retry Logic-এ Idempotency নিশ্চিত করা জরুরি

✋ Y — Your Turn

Nord Bank-এর একটা Automation চিন্তা করে লিখতে হবে (Backup ছাড়া অন্য কোনো কাজ) যেখানে Retry করা বিপজ্জনক হতে পারে যদি Idempotency নিশ্চিত না করা হয় — কেন বিপজ্জনক হতে পারে তা ২-৩ বাক্যে ব্যাখ্যা করতে হবে।