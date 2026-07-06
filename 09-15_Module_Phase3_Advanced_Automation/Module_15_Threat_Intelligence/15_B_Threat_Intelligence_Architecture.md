📘 Module 15 — Threat Intelligence Architecture (Section B)

📌 S — Scenario (Nord Bank / Banking-Specific)

Nord Bank-এর Security Team Global Threat Feed (নতুন Malware, Attack Pattern) নিয়মিত পড়ে, কিন্তু প্রতিটা Threat Bank-এর জন্য প্রাসঙ্গিক কিনা তা বোঝা কঠিন — কারণ Global Feed-এ হাজারো Threat আসে, যার বেশিরভাগ Nord Bank-এর নিজস্ব Infrastructure-এর সাথে সম্পর্কিতই না। একবার একটা সত্যিই গুরুত্বপূর্ণ Threat (একটা নির্দিষ্ট Firewall Model-এর Vulnerability) Feed-এ ছিল, কিন্তু Volume-এর মধ্যে হারিয়ে যায় এবং ২ সপ্তাহ পর Bank নিজেই সেই Vulnerability-র শিকার হয়।

🚨 Challenge

- Global Threat Feed-এ Volume অনেক বেশি, কিন্তু তার মধ্যে Bank-এর জন্য প্রাসঙ্গিক অংশ খুব কম
- Threat Feed আর Bank-এর নিজস্ব Device Inventory (কোন Firewall Model ব্যবহার হচ্ছে) আলাদাভাবে রাখা ছিল, তাই মেলানো Manually করতে হতো
- গুরুত্বপূর্ণ Threat দ্রুত ধরা না পড়লে, তার Countermeasure নেওয়ার আগেই Bank ঝুঁকিতে পড়ে যায়
- Analyst-দের Capacity সীমিত, তারা প্রতিদিন সব Threat Feed পড়ে Analyze করতে পারে না

✅ Solution

একটা Multi-Agent Threat Intelligence System তৈরি করতে হবে যেখানে একটা Agent Threat Feed মনিটর করবে, আরেকটা Agent সেই Threat-কে Bank-এর নিজস্ব Device Inventory-র সাথে Cross-Reference করে Relevance যাচাই করবে, এবং শুধু প্রাসঙ্গিক Threat-ই Countermeasure Suggestion-সহ Analyst পর্যন্ত পৌঁছাবে।

🎯 T — Task

Nord Bank-এর জন্য একটা Threat Intelligence Multi-Agent Architecture ডিজাইন করতে হবে যেখানে Global Threat Feed মনিটরিং, Bank-এর নিজস্ব Infrastructure-এর সাথে Relevance Matching, এবং Countermeasure Suggestion — এই তিনটা কাজ আলাদা কিন্তু সমন্বিত Agent হিসেবে কাজ করবে।

👀 O — Output

একটা Threat Intelligence Architecture Document যেখানে থাকবে:
- Threat Feed Monitoring Agent Design — কোন কোন Source থেকে Threat তথ্য আসবে
- Relevance Matching Agent Design — কীভাবে একটা Threat-কে Bank-এর CMDB (Module 09.3-এ তৈরি করা Device Inventory)-এর সাথে মিলিয়ে বোঝা হবে এটা প্রাসঙ্গিক কিনা
- Confidence Scoring — Relevance Match কতটা নিশ্চিত (Exact Model Match বনাম আংশিক মিল) তার ভিত্তিতে Priority ঠিক করা
- Countermeasure Suggestion Agent Design — প্রাসঙ্গিক Threat পাওয়া গেলে কী ধরনের প্রাথমিক পদক্ষেপ Suggest করা হবে
- Human Review Gate — Countermeasure Suggestion সরাসরি Apply না হয়ে, Analyst-এর কাছে যাবে Review-এর জন্য

🤔 R — Reason

এই Architecture-এর মূল সুবিধা হলো CMDB-র সাথে সংযোগ — Module 09.3-এ তৈরি করা Device Inventory যদি Up-to-Date থাকে, তাহলে একটা নতুন Threat আসার সাথে সাথেই স্বয়ংক্রিয়ভাবে বোঝা সম্ভব এটা Bank-এর জন্য প্রাসঙ্গিক কিনা, Manually প্রতিটা Threat Check না করেই। এতে Analyst-দের সীমিত সময় শুধু সত্যিই প্রাসঙ্গিক Threat-এ Focus করতে পারে।

🏦 Real-World Use Case

Nord Bank-এর Threat Feed Monitoring Agent একটা নতুন Vulnerability Report পায় একটা নির্দিষ্ট FortiGate Firmware Version নিয়ে। Relevance Matching Agent সেটা CMDB-তে Check করে দেখে Nord Bank-এর ৩টা Branch-এ ঠিক এই Firmware Version চলছে। যেহেতু এটা Exact Match, Confidence Score High হয়, এবং সাথে সাথে একটা High-Priority Alert Analyst-এর কাছে যায় Countermeasure Suggestion সহ (Firmware Update বা সাময়িক Rule পরিবর্তন)।

🧠 Memory Tip

এই Architecture-কে ভাবা যেতে পারে একটা "Airport Security Watchlist Match"-এর মতো — হাজারো Passenger-এর মধ্যে থেকে শুধু Watchlist-এর সাথে মেলা নামগুলো আলাদা করে Flag করা হয়, বাকিদের আলাদা করে দেখতে হয় না।

⚠️ L — Limitation

- CMDB যদি Up-to-Date না থাকে (Module 09.3-এ দেখা সমস্যা — কিছু Device Auto-Discovery Miss করতে পারে), তাহলে Relevance Matching ভুল হবে — একটা সত্যিকারের ঝুঁকিপূর্ণ Device "প্রাসঙ্গিক না" হিসেবে ভুলভাবে বাদ পড়ে যেতে পারে
- Threat Feed-এ Device Model বা Version স্পষ্টভাবে উল্লেখ না থাকলে (শুধু "কিছু Firewall"), Exact Matching করা কঠিন হয়ে যায়, Confidence Score কম থাকবে
- একটা Threat "প্রাসঙ্গিক না" হিসেবে ভুলভাবে Filter হয়ে গেলে, Analyst সেটা কখনো দেখতেই পাবে না — Aggressive Filtering নিজেই একটা নতুন ঝুঁকি
- Countermeasure Suggestion ভুল হলে (যেমন ভুল Firmware Version Suggest করা), এবং Analyst তাড়াহুড়ো করে Review করলে, ভুল Suggestion Apply হয়ে যেতে পারে

✋ Y — Your Turn

Module 09.3-এর CMDB-তে যদি কোনো Device Miss হয়ে থাকে (Isolated Segment-এর কারণে), তাহলে এই Threat Intelligence System সেই Device-এর জন্য আসা একটা সত্যিকারের Threat-কে কীভাবে ভুলভাবে "অপ্রাসঙ্গিক" হিসেবে Treat করতে পারে তা ২-৩ বাক্যে লিখতে হবে।