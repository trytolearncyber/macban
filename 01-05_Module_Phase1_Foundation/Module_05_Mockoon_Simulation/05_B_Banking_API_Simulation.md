📘 Module 04 — Banking API Architecture (Section B)

📌 S — Scenario (Nord Bank / Banking-Specific)

Nord Bank-এর একটা নতুন Mobile Banking Feature Launch করার কথা ছিল, যেখানে Customer সরাসরি App থেকে Loan Apply করতে পারবে। Development Team T24 Core Banking System-এর সাথে সরাসরি Direct Database Connection ব্যবহার করে Feature টা তৈরি করেছিল, কোনো API Layer ছাড়াই। Launch-এর কয়েকদিন পর Core Banking System-এ Slowdown শুরু হয়, কারণ Mobile App-এর প্রতিটা Request সরাসরি Core Database-এ গিয়ে আঘাত করছিল, এবং কোনো Rate Limit বা Access Control ছিল না।

🚨 Challenge

- Core Banking System-এর সাথে Direct Integration করার ফলে কোনো Isolation Layer ছিল না
- একটা Buggy Mobile App Release পুরো Core System-কে Slow করে দিতে পারত
- কোনো Rate Limiting না থাকায় Unusual Traffic Core System-কে Overload করতে পারত
- একাধিক External System (SWIFT, RTGS, NPSB) কে আলাদাভাবে Direct Access দেওয়া Security Risk বাড়িয়ে দিচ্ছিল

✅ Solution

Core Banking System এবং External/Internal Application-এর মাঝখানে একটা API Gateway Layer বসাতে হবে, যা Traffic Control, Authentication, এবং Isolation নিশ্চিত করবে।

🎯 T — Task

Nord Bank-এর জন্য একটা Banking API Integration Architecture ডিজাইন করতে হবে, যেখানে Core Banking (T24/Finacle), SWIFT, RTGS, এবং NPSB — সবগুলো System একটা Central API Gateway-এর মাধ্যমে Access হবে।

👀 O — Output

একটা API Architecture Document যেখানে থাকবে:
- Core Banking API Integration Layer-এর Design (T24 / Finacle)
- SWIFT MT/MX Message Handling-এর জন্য আলাদা Integration Path
- RTGS এবং NPSB-এর জন্য Real-Time Processing Consideration
- API Gateway-এর Role: Rate Limiting, Authentication, Error Isolation

🤔 R — Reason

Core Banking System হলো Bank-এর সবচেয়ে Critical System — এটা যদি Slow হয় বা Down হয়, পুরো Bank-এর Operation থেমে যায়। তাই কোনো External বা Internal Application-কে সরাসরি Core System-এর সাথে যুক্ত করা উচিত না। একটা API Gateway মাঝখানে থাকলে, একটা Application-এর সমস্যা Core System পর্যন্ত পৌঁছাতে পারে না — এটা একটা Buffer হিসেবে কাজ করে।

🏦 Real-World Use Case

Nord Bank পরবর্তীতে API Gateway বসিয়ে প্রতিটা External Request-এ Rate Limit (100 requests/minute) বসায় এবং Idempotency Check যোগ করে, যাতে একই Transaction ভুলবশত দুইবার Process না হয়। এর ফলে Mobile App-এর কোনো Bug থাকলেও তা আর Core Banking System-কে সরাসরি প্রভাবিত করতে পারে না।

🧠 Memory Tip

API Gateway-কে ভাবা যেতে পারে "Bank-এর Front Desk"-এর মতো — Customer সরাসরি Vault-এ ঢুকতে পারে না, প্রথমে Front Desk-এর মাধ্যমে যেতে হয়, যেখানে Identity Verify হয় এবং সীমা নির্ধারণ করা থাকে।

⚠️ L — Limitation

- API Gateway যোগ করলে একটা নতুন Component তৈরি হয়, যেটা নিজেও একটা Single Point of Failure হতে পারে যদি এর নিজের HA Design না থাকে
- SWIFT এবং RTGS-এর মতো System-এর নিজস্ব Strict Timing এবং Format Requirement থাকে, যা একটা Generic API Gateway সবসময় ভালোভাবে Handle করতে পারে না — অনেক সময় Specialized Middleware দরকার হয়
- Rate Limiting ভুলভাবে Configure করলে বৈধ High-Volume Transaction (যেমন Month-End Settlement) ভুলবশত Block হয়ে যেতে পারে
- Regulatory Body (Bangladesh Bank)-এর সাথে সরাসরি সংযোগে (RTGS/NPSB) কিছু Configuration Change Bank একাই Decide করতে পারে না — External Approval লাগে

✋ Y — Your Turn

Nord Bank-এর একটা নতুন Internal Application (ধরা যাক HR System) যদি Core Banking System থেকে শুধু Employee-দের Salary Account Balance পড়তে চায়, তাহলে API Gateway-তে কী ধরনের Access Restriction (কী পড়তে পারবে, কী পারবে না) বসানো উচিত তা ২-৩ বাক্যে লিখতে হবে।
