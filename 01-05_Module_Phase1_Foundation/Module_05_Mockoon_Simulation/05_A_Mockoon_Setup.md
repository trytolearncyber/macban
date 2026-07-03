📘 Module 05 — Mockoon Banking API Simulation (Section A)

📌 S — Scenario 1 (Non-Banking)

একজন Online Bookstore Owner চায় যে কেউ Book Order করলে সাথে সাথে একটা Thank You Email চলে যাক, কোনো Manual কাজ ছাড়াই। কিন্তু তার কোনো Programming Background নেই, তাই সে Code লিখে এটা করতে পারে না। এমন একটা উপায় দরকার যেখানে Box আঁকার মতো করে ধাপগুলো সাজিয়ে একটা Automation তৈরি করা যায়।

📌 S — Scenario 2 (Banking, Non-Technical)

Nord Bank-এর একজন IT Support সদস্য একটা ছোট কাজ Automate করতে চায় — কোনো Alert আসলে সেটা Email-এ Forward করা। কিন্তু সে আগে কখনো কোনো Automation Tool ব্যবহার করেনি। প্রথম কাজ হলো একটা Workflow-এর ভেতরের ধাপগুলো (Steps) কেমন দেখতে হয় এবং কীভাবে একটার সাথে আরেকটা যুক্ত হয়, তা বোঝা।

🎯 T — Task

আজকের লক্ষ্য:
- n8n-এর Interface-এ কী কী মূল অংশ থাকে তা চেনা (Node, Canvas, Execution)
- একটা Workflow আসলে কী দিয়ে তৈরি হয় তা বোঝা
- Node একে অপরের সাথে কীভাবে যুক্ত হয় (Connect) সেই ধারণা পাওয়া

👀 O — Output

Module শেষে learner বুঝতে পারবে:
- Node কী — একটা একক কাজের একক (Unit)
- Canvas কী — যেখানে Node-গুলো সাজানো হয়
- একটা Workflow "Run" করা মানে কী
- Manual Trigger আর Scheduled Trigger-এর মধ্যে concept-গত পার্থক্য কী

🤔 R — Reason

Visual Builder ব্যবহারের মূল কারণ হলো, Code না জেনেও একজন মানুষ ধাপে ধাপে চিন্তা করে একটা Automation সাজাতে পারে। প্রতিটা Node একটা নির্দিষ্ট কাজ করে, আর Node-গুলো যুক্ত করলে পুরো Process একটা Flow হিসেবে দাঁড়ায় — ঠিক যেমন একটা Assembly Line-এ প্রতিটা Station একটা করে কাজ করে।

🧠 Memory Tip

Node = একটা Assembly Line-এর একটা Station
Canvas = পুরো Assembly Line-এর Floor
Trigger = Line Start করার Button (কে চাপবে — মানুষ, নাকি সময়)

⚠️ L — Limitation

- Visual Builder দিয়ে সহজ Workflow তৈরি করা যায়, কিন্তু খুব জটিল Logic (Complex Condition, Loop) অনেক সময় Visual-এ Manage করা কঠিন হয়ে যায়
- একটা Workflow দেখতে সহজ মনে হলেও, ভেতরে ভুল Configuration থাকলে সেটা বোঝা নতুনদের জন্য কঠিন হতে পারে
- শুধু Node সাজিয়ে দিলেই Workflow নির্ভরযোগ্য হয়ে যায় না — Error Handling এবং Testing আলাদাভাবে দরকার হয়
- এই ধারণা এখনও কোনো Real API বা Real Data নিয়ে কাজ করে না — এটা শুধু Structure বোঝার জন্য

✋ Y — Your Turn

একটা দৈনন্দিন কাজ চিন্তা করে লিখতে হবে যেটাকে ৩টা Step-এ ভাগ করা যায় (যেমন: কিছু ঘটলো → কিছু Check করা হলো → একটা Action নেওয়া হলো), এবং প্রতিটা Step-কে একটা করে "Node" হিসেবে কল্পনা করে ২-৩ বাক্যে বর্ণনা করতে হবে।
