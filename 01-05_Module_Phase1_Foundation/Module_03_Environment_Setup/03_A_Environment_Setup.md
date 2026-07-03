📘 Module 03 — Production Automation Environment Setup (Section A)

📌 S — Scenario 1 (Non-Banking)

একজন freelance graphic designer প্রতিদিন client-দের কাছ থেকে Order আসার পর manually email পাঠায়, Invoice তৈরি করে, আর Google Sheet-এ hisab রাখে। এই কাজে প্রতিদিন ২ ঘন্টা সময় চলে যায়। এই কাজ automate করতে হলে একটা জায়গা দরকার হয় যেখানে automation tool (যেমন n8n) সবসময় চালু থাকবে এবং Order আসার সাথে সাথে নিজে থেকেই কাজ করবে।

📌 S — Scenario 2 (Banking, Non-Technical)

Nord Bank-এর IT Support Team-এর একজন সদস্য নতুন একটা automation idea test করতে চায় — যেমন, কোনো Device Offline হলে Team-কে notification পাঠানো। কিন্তু এই idea সরাসরি Live System-এ test করা যায় না, কারণ ভুল হলে Real Operation-এ সমস্যা হতে পারে। তাই একটা আলাদা, নিরাপদ জায়গা দরকার হয় যেখানে idea টা প্রথমে test করা যাবে।

🎯 T — Task

আজকের লক্ষ্য হলো বোঝা:
- Automation চালানোর জন্য কী ধরনের "জায়গা" (Environment) দরকার হয়
- Environment বলতে ঠিক কী বোঝায়
- কেন সবকিছু নিজের Computer-এ সরাসরি না চালিয়ে একটা Controlled জায়গায় চালানো হয়

👀 O — Output

এই Module শেষে learner বুঝতে পারবে:
- Automation Tool (যেমন n8n) চালানোর জন্য একটা Environment কেন লাগে
- Environment-এর মধ্যে কোন ধরনের উপাদান (Component) থাকে — যেমন যেখানে Tool চলবে, যেখানে Data জমা থাকবে, আর বাইরের দুনিয়ার সাথে যোগাযোগ কীভাবে হবে
- Self-Hosted আর Cloud-based Environment-এর মধ্যে সাধারণ পার্থক্য কী

🤔 R — Reason

Automation Tool যদি শুধু নিজের Laptop-এ চালানো হয়, তাহলে Laptop বন্ধ হলেই Automation বন্ধ হয়ে যাবে। এছাড়া, Testing আর Real Use একসাথে করলে ভুল হওয়ার সম্ভাবনা বেড়ে যায়। এই কারণে একটা আলাদা, সবসময় চালু থাকা Environment ব্যবহার করা হয় — যাতে Automation নির্ভরযোগ্যভাবে (Reliably) চলতে পারে এবং Testing আর Real Operation আলাদা থাকে।

🧠 Memory Tip

Environment মানে ভাবা যেতে পারে "Automation-এর নিজের বাড়ি" — যেখানে সে সবসময় থাকে, ঘুমায় না, আর কাজ করতে থাকে।

⚠️ L — Limitation

- একটা Environment তৈরি করলেই Automation নিজে থেকে নির্ভরযোগ্য হয়ে যায় না — সঠিকভাবে চালু রাখা এবং নজরদারি করা এখনও দরকার হয়
- Environment বন্ধ হয়ে গেলে বা Internet Connection চলে গেলে Automation থেমে যেতে পারে
- একটামাত্র Environment-এ সবকিছু চালালে, একটা সমস্যা পুরো System-কে প্রভাবিত করতে পারে
- Environment ধারণাটা Tool নির্বাচন বা Setup Detail নিয়ে কিছু বলে না — এটা শুধু "কেন দরকার" তা ব্যাখ্যা করে

✋ Y — Your Turn

নিজের একটা দৈনন্দিন কাজ (Non-Banking) চিন্তা করে লিখতে হবে যেটা Automate করা গেলে সময় বাঁচবে, এবং সেই কাজটার জন্য কেন একটা "সবসময় চালু থাকা জায়গা" দরকার হবে তা ২-৩ বাক্যে ব্যাখ্যা করতে হবে।
