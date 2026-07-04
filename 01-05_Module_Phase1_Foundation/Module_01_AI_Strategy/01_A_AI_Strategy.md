📘 Module 01 — AI Strategy & System Architecture Foundation (Section A)

📌 S — Scenario 1 (Non-Banking)

একজন Restaurant Owner প্রতিদিন Table Booking, Order Tracking, আর Inventory Check আলাদা আলাদা Notebook-এ Manually লিখে রাখে। সে জানে যে AI বা Automation দিয়ে কিছু একটা করা যায়, কিন্তু ঠিক কোন কাজটা কোন ধরনের Tool দিয়ে সহজ হবে তা তার কাছে পরিষ্কার না।

📌 S — Scenario 2 (Banking, Non-Technical)

Nord Bank-এর একজন IT Manager শুনেছে যে AI Agent দিয়ে অনেক কাজ Automate করা যায়, কিন্তু "AI Agent" বলতে ঠিক কী বোঝায় এবং সব AI Agent কি একইভাবে কাজ করে কিনা তা নিয়ে তার কাছে স্পষ্ট ধারণা নেই।

🎯 T — Task

আজকের লক্ষ্য:
- AI Automation বলতে সাধারণভাবে কী বোঝায় তা বোঝা
- AI Agent-এর প্রধান ধরনগুলো চেনা — Simple Reflex, Model-Based, Goal-Based, Utility-Based
- একটা কাজ দেখে বোঝার চেষ্টা করা সেটা কোন ধরনের Agent দিয়ে ভালোভাবে সামলানো যেতে পারে

👀 O — Output

Module শেষে learner বলতে পারবে:
- চারটা Agent Type-এর মধ্যে মূল পার্থক্য কী
- Simple Reflex Agent কেন শুধু সহজ, সরাসরি Rule-ভিত্তিক কাজে ভালো
- Goal-Based বা Utility-Based Agent কেন জটিল, একাধিক বিকল্পের মধ্যে সিদ্ধান্ত নেওয়ার কাজে বেশি উপযোগী

🤔 R — Reason

সব ধরনের Automation Task একইভাবে সমাধান করা যায় না। একটা সহজ, সবসময় একই Rule মেনে চলা কাজের জন্য জটিল Agent ব্যবহার করা অপ্রয়োজনীয়, আবার জটিল, পরিস্থিতি-নির্ভর সিদ্ধান্তের কাজে খুব সাধারণ Agent যথেষ্ট না। তাই Agent Type-এর পার্থক্য বোঝা থাকলে সঠিক Tool বা Approach বেছে নেওয়া সহজ হয়।

🧠 Memory Tip

Simple Reflex = "লাইট জ্বললে গাড়ি থামা" (সরাসরি Rule)
Model-Based = "রাস্তার আগের Condition মনে রেখে চালানো"
Goal-Based = "গন্তব্যে পৌঁছানোর জন্য রাস্তা বেছে নেওয়া"
Utility-Based = "সবচেয়ে কম সময় বা কম খরচের রাস্তা বেছে নেওয়া"

⚠️ L — Limitation

- বাস্তবে অনেক System এই চারটা Type-এর কোনো একটাতে পুরোপুরি পড়ে না — অনেক সময় এগুলোর মিশ্রণ ব্যবহার হয়
- একটা Agent-কে ভুল Category-তে ফেলে সেই অনুযায়ী Design করলে, Task-এর জন্য ভুল Approach বেছে নেওয়া হয়ে যেতে পারে
- Agent Type চেনা মানেই এই না যে কীভাবে সেটা বাস্তবে Build করতে হয় তা জানা হয়ে গেল — এটা শুধু একটা Conceptual Framework
- এই ধারণা এখনও কোনো নির্দিষ্ট Tool (n8n, Langflow) দিয়ে কীভাবে এই Agent-গুলো তৈরি করা হয় তা নিয়ে কিছু বলে না

✋ Y — Your Turn

নিজের একটা দৈনন্দিন কাজ চিন্তা করে লিখতে হবে, এবং সেটা এই চারটা Agent Type-এর মধ্যে কোনটার সাথে সবচেয়ে বেশি মিলে যায় বলে মনে হয় তা ২-৩ বাক্যে যুক্তিসহ ব্যাখ্যা করতে হবে।
