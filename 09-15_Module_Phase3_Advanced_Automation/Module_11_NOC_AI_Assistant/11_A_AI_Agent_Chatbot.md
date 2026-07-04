📘 Module 11 — Network Operations AI Assistant (Section A)

📌 S — Scenario 1 (Non-Banking)

একজন E-commerce Customer রাত ২টায় জানতে চায় তার Order কোথায় আছে। কোনো Human Support তখন Available না থাকলেও, একটা Chatbot সাথে সাথে তাকে Order Status জানিয়ে দেয়, কোনো অপেক্ষা ছাড়াই।

📌 S — Scenario 2 (Banking, Non-Technical)

Nord Bank-এর একজন NOC Engineer রাতের Shift-এ কাজ করার সময় দ্রুত জানতে চায় "কতগুলো Branch এখন Offline আছে?" কিন্তু এই তথ্য বের করতে তাকে আলাদা আলাদা Monitoring Dashboard খুলে Manually খুঁজতে হয়, যা সময় নষ্ট করে যখন দ্রুত সিদ্ধান্ত দরকার।

🎯 T — Task

আজকের লক্ষ্য:
- Chatbot বা AI Assistant বলতে কী বোঝায় তা বোঝা
- Intent Recognition বলতে কী বোঝায় — ব্যবহারকারী আসলে কী জানতে চাইছে তা বোঝার ধারণা
- একটা AI Assistant কীভাবে একটা প্রশ্নকে সঠিক তথ্যের Source-এর সাথে যুক্ত করে তার প্রাথমিক ধারণা

👀 O — Output

Module শেষে learner বলতে পারবে:
- একটা AI Assistant সাধারণ FAQ Bot থেকে কীভাবে আলাদা (শুধু Fixed উত্তর না দিয়ে প্রকৃত তথ্য খুঁজে আনা)
- Intent Recognition কীভাবে একটা প্রশ্নকে সঠিক Category-তে ফেলে (যেমন "Status Check" নাকি "Action Request")
- কেন একটা AI Assistant-এর জন্য সঠিক তথ্যের Source-এর সাথে সংযোগ থাকা জরুরি

🤔 R — Reason

মানুষ প্রাকৃতিক ভাষায় বিভিন্নভাবে একই জিনিস জিজ্ঞেস করতে পারে — যেমন "কয়টা Branch Down?" অথবা "কোন Branch-এ সমস্যা?" একটা ভালো AI Assistant-কে বুঝতে হয় যে দুটো প্রশ্নই আসলে একই তথ্য চাইছে, তারপর সঠিক Source থেকে সেই তথ্য এনে উত্তর দিতে হয়। এই ক্ষমতা ছাড়া AI Assistant শুধু আগে থেকে লেখা কিছু Fixed উত্তর দিতে পারবে, যা প্রকৃত প্রশ্নের জন্য যথেষ্ট না।

🧠 Memory Tip

AI Assistant-কে ভাবা যেতে পারে একটা "রাতের Duty Officer"-এর মতো — সরাসরি প্রশ্নের উত্তর দেওয়ার বদলে সে বোঝে ঠিক কী জানতে চাওয়া হচ্ছে, তারপর সঠিক জায়গা থেকে তথ্য এনে জানায়।

⚠️ L — Limitation

- AI Assistant ভুলভাবে Intent বুঝলে ভুল তথ্য দিয়ে দিতে পারে, যা NOC-এর মতো Critical জায়গায় বিভ্রান্তি তৈরি করতে পারে
- AI Assistant শুধু তথ্য "জানাতে" পারে, নিজে থেকে কোনো Action (যেমন Device Restart) নিতে পারে কিনা তা আলাদা বিষয়, এবং প্রতিটাতেই আলাদা ঝুঁকি জড়িত
- Source Data যদি পুরনো বা ভুল হয়, AI Assistant-ও ভুল তথ্য দেবে, কারণ এটা নিজে থেকে Real-Time সত্যতা যাচাই করতে পারে না
- Complex বা Ambiguous প্রশ্নে (একাধিক অর্থ হতে পারে এমন) AI Assistant ভুল Interpretation করতে পারে

✋ Y — Your Turn

NOC-এর একজন Engineer-এর জিজ্ঞাসা করা একটা সাধারণ প্রশ্ন চিন্তা করে লিখতে হবে (যেমন "সবচেয়ে বেশি Alert কোন Branch-এ?"), এবং সেই প্রশ্নের উত্তর দিতে AI Assistant-এর কোন Source-এর তথ্য দরকার হবে বলে মনে হয় তা ২-৩ বাক্যে লিখতে হবে।