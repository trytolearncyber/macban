📘 Module 11 — NOC AI Assistant Architecture (Section B)

📌 S — Scenario (Nord Bank / Banking-Specific)

Nord Bank-এর NOC-এ রাতের Shift-এ মাত্র ২ জন Engineer থাকে, যেখানে দিনে ৮ জন থাকে। রাতে একটা সমস্যা হলে, এই ২ জনকে একাধিক Dashboard (Monitoring, Firewall, VPN) আলাদা আলাদা করে Check করতে হয় প্রশ্নের উত্তর বের করতে, যা সময় নষ্ট করে এবং Response Time বাড়িয়ে দেয়।

🚨 Challenge

- রাতের Shift-এ কম Staff থাকার কারণে প্রতিটা প্রশ্নের উত্তর বের করতে বেশি সময় লাগে
- তথ্য একাধিক আলাদা System-এ ছড়িয়ে আছে (Monitoring, Firewall, VPN, Database), একটা একক জায়গা থেকে সবকিছু জানার উপায় নেই
- Count Query ("কয়টা Down"), List Query ("কোন কোনটা"), এবং Trend Query ("Throughput কেমন যাচ্ছে") — প্রতিটার জন্য আলাদা Data Source এবং Logic দরকার
- ভুল বা Ambiguous প্রশ্ন হলে AI Assistant ভুল Category-তে Match করে ভুল উত্তর দিতে পারে, যা Critical মুহূর্তে বিপজ্জনক

✅ Solution

একটা NOC AI Assistant Architecture তৈরি করতে হবে যেখানে প্রতিটা প্রশ্নের ধরন (Count, List, Trend, Action-Request) আলাদাভাবে চেনা হবে এবং সঠিক Data Source-এর সাথে সংযুক্ত করা হবে, এবং Uncertain Intent-এর ক্ষেত্রে AI Assistant অনুমান না করে স্পষ্টীকরণ চাইবে।

🎯 T — Task

Nord Bank-এর জন্য একটা NOC AI Assistant Architecture ডিজাইন করতে হবে যা Monitoring, Firewall, VPN, এবং Database System থেকে তথ্য নিয়ে Count, List, এবং Trend ধরনের প্রশ্নের সঠিক উত্তর দিতে পারবে।

👀 O — Output

একটা NOC AI Assistant Architecture Document যেখানে থাকবে:
- Intent Classification Design — প্রশ্নকে Count/List/Trend/Action-Request-এ কীভাবে আলাদা করা হবে
- Data Source Mapping — প্রতিটা Intent Type কোন System থেকে তথ্য নেবে (Monitoring, Firewall, VPN)
- Ambiguity Handling — Intent স্পষ্ট না হলে AI Assistant কীভাবে Clarifying Question জিজ্ঞেস করবে, অনুমান করবে না
- Response Format Design — Count Query-র উত্তর একটা Number, List Query-র উত্তর একটা তালিকা, Trend Query-র উত্তর একটা Summary বা Graph হওয়া উচিত

🤔 R — Reason

Section A-তে দেখা গিয়েছিল যে "কয়টা" আর "কোনটা" জিজ্ঞেস করা আসলে দুই ধরনের আলাদা Intent — একটা Count, আরেকটা List। বাস্তব NOC Environment-এ এরকম আরও অনেক ধরনের প্রশ্ন আসে (Trend, Action-Request), এবং প্রতিটার জন্য ভুল Response Format দিলে (যেমন Count-এর জায়গায় List দেওয়া) Engineer বিভ্রান্ত হয়ে যেতে পারে, বিশেষ করে রাতের Shift-এ যখন দ্রুত এবং সঠিক সিদ্ধান্ত দরকার।

🏦 Real-World Use Case

Nord Bank-এর NOC AI Assistant-কে "কয়টা Branch Down?" জিজ্ঞেস করলে এটা Monitoring Database Query করে একটা সংখ্যা ফেরত দেয় (Count Intent)। "কোন কোন Branch Down?" জিজ্ঞেস করলে এটা একই Database থেকে একটা তালিকা ফেরত দেয় (List Intent)। আর "Firewall Throughput কেমন যাচ্ছে গত ঘন্টায়?" জিজ্ঞেস করলে এটা একটা Trend Summary দেয় (Trend Intent) — প্রতিটা প্রশ্নের জন্য আলাদা Logic এবং Response Format ব্যবহৃত হয়।

🧠 Memory Tip

NOC AI Assistant-কে ভাবা যেতে পারে একটা "Hospital Triage Nurse"-এর মতো — প্রথমেই বোঝে রোগীর সমস্যাটা ঠিক কী ধরনের (জ্বর, ব্যথা, না জরুরি অবস্থা), তারপর সেই অনুযায়ী সঠিক Department-এ পাঠায়, সব রোগীকে একই Treatment দেয় না।

⚠️ L — Limitation

- Intent Classification যত ভালোই হোক, একদম নতুন ধরনের প্রশ্ন (যা আগে কখনো আসেনি) ভুল Category-তে পড়ে যেতে পারে
- Clarifying Question জিজ্ঞেস করা মানে সময় লাগা — জরুরি মুহূর্তে যদি Assistant বারবার স্পষ্টীকরণ চায়, তাহলে এটা নিজেই একটা Bottleneck হয়ে দাঁড়াতে পারে
- একাধিক Data Source থেকে তথ্য একত্র করে উত্তর দিলে, একটা Source যদি সাময়িকভাবে Unavailable থাকে, তাহলে Answer Incomplete বা ভুল হতে পারে, কিন্তু Assistant হয়তো সেটা স্পষ্টভাবে জানাবে না যদি না আলাদাভাবে ডিজাইন করা হয়
- এই Architecture Critical Action (যেমন Device Restart করা) নিজে থেকে নেওয়ার অনুমতি দেয় না — শুধু তথ্য দেওয়ার মধ্যেই সীমাবদ্ধ, Action নেওয়ার জন্য আলাদা Approval Layer দরকার হবে

✋ Y — Your Turn

Nord Bank-এর NOC AI Assistant-কে যদি এমন একটা প্রশ্ন করা হয় যা Count নাকি List তা স্পষ্ট না (যেমন "Branch Status কেমন?"), তাহলে Assistant-এর কী করা উচিত — অনুমান করে একটা উত্তর দেওয়া, নাকি Clarify করা — তা ২-৩ বাক্যে যুক্তিসহ লিখতে হবে।