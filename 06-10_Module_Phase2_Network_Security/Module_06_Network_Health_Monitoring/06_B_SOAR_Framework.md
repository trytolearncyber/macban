📘 Module 06 — SOAR Framework (Section B)

📌 S — Scenario (Nord Bank / Banking-Specific)

Nord Bank-এর একটা Branch-এ একজন Attacker রাত ৩টায় বারবার VPN Login চেষ্টা করছিল। FortiGate Firewall প্রতিটা Failed Attempt Log করেছিল, কিন্তু কেউ সেই Log রাত জেগে দেখছিল না। সকালে NOC Team যখন Log Review করে, ততক্ষণে Attacker ইতিমধ্যে ৫০০+ বার Try করে ফেলেছে এবং একটা Weak Password-ওয়ালা Account Compromise হয়ে গেছে।

🚨 Challenge

- Firewall Log আসছিল ঠিকই, কিন্তু কেউ Real-Time-এ সেটা দেখছিল না
- একটা Single Failed Login আর ৫০০টা Failed Login-কে একইভাবে Treat করা হচ্ছিল — কোনো Severity Difference ছিল না
- রাতে কোনো On-Call ব্যবস্থা ছিল না, তাই Critical Alert-ও পরদিন সকাল পর্যন্ত অপেক্ষা করত
- Alert শুধু একটা Channel-এ (Email) যেত, যা রাতে কেউ Check করত না

✅ Solution

Firewall Log-কে Real-Time-এ Monitor করে, Severity অনুযায়ী Classify করে, এবং সঠিক Channel দিয়ে সঠিক ব্যক্তির কাছে Alert পাঠানোর একটা SOAR (Security Orchestration, Automation, and Response) System বসাতে হবে।

🎯 T — Task

Nord Bank-এর জন্য একটা SOAR Framework ডিজাইন করতে হবে যা Firewall এবং IPS Log Real-Time-এ Monitor করবে, Severity অনুযায়ী Classify করবে, এবং On-Call Engineer পর্যন্ত সঠিক সময়ে Alert পৌঁছে দেবে।

👀 O — Output

একটা SOAR Architecture Document যেখানে থাকবে:
- Log Ingestion Design (FortiGate/Cisco থেকে Real-Time Log আসার পথ)
- Severity Classification Matrix (P1–P4)
- Multi-Channel Alerting Strategy (Email, SMS, Slack/Teams, Phone Call)
- On-Call Rotation Integration, যাতে রাতেও সঠিক ব্যক্তি Alert পায়

🤔 R — Reason

Security Threat-এর ক্ষেত্রে সময়ই সবচেয়ে গুরুত্বপূর্ণ বিষয় — Attacker কয়েক ঘন্টার মধ্যে যা করতে পারে, তা যদি সকাল পর্যন্ত কেউ না জানে, তাহলে Detection-এর কোনো মূল্য থাকে না। Severity Classification ছাড়া প্রতিটা Alert-কে সমানভাবে Treat করলে Critical Alert Noise-এর মধ্যে হারিয়ে যায়। তাই Real-Time Detection, সঠিক Prioritization, আর সঠিক Person পর্যন্ত Alert পৌঁছানো — এই তিনটাই একসাথে দরকার।

🏦 Real-World Use Case

Nord Bank পরবর্তীতে এমন একটা System বসায় যেখানে ৫টা Failed Login-এর বেশি হলেই সেটা স্বয়ংক্রিয়ভাবে P2 (High) হিসেবে Classify হয় এবং সাথে সাথে On-Call Engineer-এর কাছে SMS যায়। ১০০+ Failed Login হলে সেটা P1 (Critical) হয়ে যায় এবং সরাসরি Phone Call Escalation Trigger হয়।

🧠 Memory Tip

SOAR-কে ভাবা যেতে পারে "একটা Hospital-এর Emergency Room Triage System"-এর মতো — প্রতিটা Patient-কে (Alert-কে) তার Severity অনুযায়ী আলাদা করে সঠিক Doctor-এর (Team-এর) কাছে পাঠানো হয়, সবাইকে একই Line-এ দাঁড় করানো হয় না।

⚠️ L — Limitation

- Severity Classification যদি ভুলভাবে Tune করা হয় (Threshold খুব কম বা খুব বেশি), তাহলে হয় False Alarm বেড়ে যাবে, নাহলে Real Threat P3/P4-এ চাপা পড়ে যাবে
- Multi-Channel Alerting-এ নির্ভরতা বাড়ে External Service-এর (SMS Provider, Slack) উপর — সেগুলো Down থাকলে Alert পৌঁছাবে না
- On-Call Rotation থাকলেও, একজন Engineer Alert না দেখলে বা Response না দিলে (Phone Silent, Internet Down) System নিজে থেকে সমস্যা সমাধান করতে পারে না
- SOAR System নিজেই একটা Attack Target হয়ে উঠতে পারে — এটাকে সুরক্ষিত না রাখলে Attacker এটাকে Disable করে দিতে পারে, যা পুরো Detection-কে অন্ধ করে দেবে

✋ Y — Your Turn

Nord Bank-এর জন্য একটা নতুন ধরনের Security Event (যেমন একটা Unusual Time-এ বড় Amount-এর Transaction Attempt) চিন্তা করে লিখতে হবে — সেটাকে P1-P4-এর মধ্যে কোন Severity-তে রাখা উচিত এবং কেন, ২-৩ বাক্যে ব্যাখ্যা করতে হবে।
