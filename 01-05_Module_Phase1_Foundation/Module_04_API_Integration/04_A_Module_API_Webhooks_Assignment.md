📘 Module 04 — Banking API Integration Architecture (Section A)

📌 S — Scenario 1 (Non-Banking)

একজন Food Delivery App ব্যবহারকারী Order দেওয়ার পর দেখে যে Order Status "Preparing" থেকে "On the Way"-তে নিজে থেকেই Update হয়ে যাচ্ছে, কোনো Manual Refresh ছাড়াই। এটা সম্ভব হয় কারণ Delivery App আর Restaurant System একে অপরের সাথে সরাসরি Data আদান-প্রদান করে।

📌 S — Scenario 2 (Banking, Non-Technical)

Nord Bank-এর একজন Customer Mobile App-এ Balance Check করলে সাথে সাথে সঠিক Amount দেখতে পায়, যদিও Transaction টা মাত্র কয়েক সেকেন্ড আগে অন্য একটা Branch থেকে হয়েছে। Mobile App আর Bank-এর মূল System আলাদা হলেও, দুটো System একসাথে কাজ করে বলেই এটা সম্ভব হয়।

🎯 T — Task

আজকের লক্ষ্য:
- API কী তা বোঝা — দুটো System কীভাবে একে অপরের সাথে কথা বলে
- Webhook কী এবং এটা API থেকে কীভাবে আলাদা
- কেন আধুনিক System-গুলো একে অপরের সাথে Connected থাকে

👀 O — Output

Module শেষে learner বলতে পারবে:
- API মানে কী এবং এটার basic কাজ কী
- Webhook কীভাবে "নিজে থেকে খবর পাঠানো"র কাজ করে
- API (Pull) আর Webhook (Push)-এর মধ্যে মূল পার্থক্য কী

🤔 R — Reason

আগে প্রতিটা System আলাদা আলাদা ভাবে কাজ করত, আর Data একটা থেকে আরেকটায় নিতে Manual কাজ লাগত। API এবং Webhook এই সমস্যা দূর করে — একটা System সরাসরি আরেকটা System-এর কাছে Data চাইতে পারে (API), অথবা একটা System নিজে থেকেই ঘটনা ঘটলে অন্য System-কে জানিয়ে দিতে পারে (Webhook)। এর ফলে Manual কাজ কমে এবং তথ্য দ্রুত Update হয়।

🧠 Memory Tip

API = "চাহিদা মতো জিজ্ঞেস করা" (তুমি জিজ্ঞেস করলে উত্তর পাবে)
Webhook = "কিছু ঘটলেই নিজে থেকে জানানো" (তুমি জিজ্ঞেস না করলেও খবর আসবে)

⚠️ L — Limitation

- API এবং Webhook দুটোই কাজ করার জন্য দুই পাশের System-কেই সঠিকভাবে Connected এবং Available থাকতে হয় — একপাশ বন্ধ থাকলে যোগাযোগ ব্যর্থ হয়
- Webhook একবার না পৌঁছালে (Network সমস্যায়) সেই খবর হারিয়ে যেতে পারে, যদি না আলাদাভাবে Retry ব্যবস্থা থাকে
- শুধু API বা Webhook থাকলেই Security নিশ্চিত হয় না — কে Access করছে তা যাচাই করার আলাদা ব্যবস্থা দরকার হয়
- এই ধারণা এখনও Authentication, Rate Limit, বা Error Handling নিয়ে কিছু বলে না — এগুলো Implementation Level-এর বিষয়

✋ Y — Your Turn

দৈনন্দিন ব্যবহার করা একটা App চিন্তা করে লিখতে হবে, যেখানে মনে হয় API ব্যবহার হচ্ছে (তুমি জিজ্ঞেস করলে Update পাও) এবং একটা জায়গা যেখানে মনে হয় Webhook ব্যবহার হচ্ছে (App নিজে থেকেই Notification পাঠায়) — দুটো Example ২-৩ বাক্যে ব্যাখ্যাসহ লিখতে হবে।
