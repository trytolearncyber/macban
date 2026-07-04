📘 Module 08 — Error Handling Basics (Section A)

📌 S — Scenario 1 (Non-Banking)

একজন Online Store Owner-এর Automation প্রতিদিন একটা External Shipping Service-কে জিজ্ঞেস করে Package কোথায় আছে। কিন্তু মাঝে মাঝে সেই Shipping Service-এর Website সাময়িকভাবে সাড়া দেয় না, আর তখন পুরো Automation থেমে যায়, কোনো Notification ছাড়াই। Owner পরে জানতে পারে যে সারাদিন ধরে কোনো Update Customer-দের কাছে যায়নি।

📌 S — Scenario 2 (Banking, Non-Technical)

Nord Bank-এর একটা Automation প্রতিদিন সকালে একটা External System-কে জিজ্ঞেস করে Exchange Rate নিয়ে আসে। একদিন সেই External System সাময়িকভাবে Slow ছিল, এবং Automation কোনো Response না পেয়ে থেমে যায়। কেউ খেয়াল না করা পর্যন্ত সারাদিন পুরনো Exchange Rate ব্যবহার হতে থাকে।

🎯 T — Task

আজকের লক্ষ্য:
- Error কী এবং Automation-এ Error কখন হতে পারে তা বোঝা
- একটা Automation Error হলে কী হওয়া উচিত তার সাধারণ ধারণা পাওয়া
- Retry (আবার চেষ্টা করা) ধারণাটা বোঝা — কেন একবার ব্যর্থ হলেই সাথে সাথে হাল ছেড়ে দেওয়া ঠিক না

👀 O — Output

Module শেষে learner বলতে পারবে:
- একটা Automation-এ Error কোথা থেকে আসতে পারে (যেমন External Service সাড়া না দেওয়া)
- একটা Automation Error হলে চুপচাপ থেমে যাওয়া কেন সমস্যাজনক
- Retry Logic বলতে কী বোঝায় — একবার ব্যর্থ হলে আবার চেষ্টা করার ধারণা

🤔 R — Reason

Automation প্রায়ই এমন External System-এর উপর নির্ভর করে যা সবসময় Available নাও থাকতে পারে। যদি একটা ছোট, সাময়িক সমস্যায় পুরো Automation চুপচাপ থেমে যায় এবং কেউ না জানে, তাহলে Automation-এর উপর নির্ভর করাই বিপজ্জনক হয়ে দাঁড়ায়। তাই Error হলে কী হবে তা আগে থেকে চিন্তা করে রাখা জরুরি — শুধু "সব ঠিক থাকলে কী হবে" তা চিন্তা করলেই চলে না।

🧠 Memory Tip

Error Handling-কে ভাবা যেতে পারে একটা "Backup Plan"-এর মতো — যেমন কেউ বাইরে যাওয়ার আগে ভাবে "যদি বৃষ্টি হয়, তাহলে কী করব", ঠিক তেমনি Automation তৈরি করার সময় ভাবতে হয় "যদি এই ধাপে ব্যর্থ হয়, তাহলে কী হবে"।

⚠️ L — Limitation

- Retry করলেই সব সমস্যার সমাধান হয় না — যদি External System দীর্ঘ সময় ধরে Down থাকে, তাহলে বারবার Retry করা লাভজনক না, বরং অতিরিক্ত চাপ তৈরি করতে পারে
- কিছু Error আসলে Retry করার মতো না — যেমন ভুল তথ্য পাঠানোর কারণে হওয়া Error বারবার চেষ্টা করলেও ঠিক হবে না
- Error Handling যোগ করলে Automation একটু জটিল হয়ে যায়, যা নতুনদের জন্য বোঝা কঠিন হতে পারে
- এই ধারণা এখনও নির্দিষ্ট কতবার Retry করা উচিত, বা কতক্ষণ অপেক্ষা করা উচিত তা নিয়ে কিছু বলে না

✋ Y — Your Turn

একটা Automation চিন্তা করে লিখতে হবে যেটা কোনো External Service-এর উপর নির্ভর করে, এবং সেই External Service সাময়িকভাবে সাড়া না দিলে Automation-এর কী করা উচিত (থেমে যাওয়া, আবার চেষ্টা করা, নাকি কাউকে জানানো) তা ২-৩ বাক্যে ব্যাখ্যা করতে হবে।