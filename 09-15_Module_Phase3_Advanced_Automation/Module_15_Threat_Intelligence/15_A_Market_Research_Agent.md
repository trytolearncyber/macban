📘 Module 15 — Threat Intelligence Multi-Agent System (Section A)

📌 S — Scenario 1 (Non-Banking)

একজন Small Investor Stock Market-এর সিদ্ধান্ত নেওয়ার আগে তিনটা আলাদা কাজ করে — প্রথমে বিভিন্ন News Source থেকে তথ্য জোগাড় করে, তারপর সেই তথ্য বিশ্লেষণ করে বোঝার চেষ্টা করে ভালো না খারাপ, আর শেষে একটা Summary Report লেখে নিজের জন্য। এই তিনটা কাজ আলাদা হলেও, একটা আরেকটার উপর নির্ভরশীল — প্রথমটা ছাড়া দ্বিতীয়টা সম্ভব না।

📌 S — Scenario 2 (Banking, Non-Technical)

Nord Bank Global Security Threat সম্পর্কে জানতে চাইলে, একজন Analyst-কে প্রথমে বিভিন্ন Source থেকে Threat News সংগ্রহ করতে হয়, তারপর সেটা Bank-এর নিজস্ব Log-এর সাথে মিলিয়ে দেখতে হয় সেই Threat আসলেই প্রাসঙ্গিক কিনা, আর শেষে একটা Report তৈরি করতে হয়। প্রতিটা ধাপ আলাদা দক্ষতা চায়, এবং একা একজনের পক্ষে সব ধাপ প্রতিদিন করা কঠিন।

🎯 T — Task

আজকের লক্ষ্য:
- একটা Multi-Step, Multi-Agent কাজে প্রতিটা Agent কীভাবে আলাদা ধরনের কাজ করে (Data Collection, Data Analysis, Report Generation) তা বোঝা
- কেন এই কাজগুলো Sequential (একটার পর একটা) — একটা Agent-এর Output আরেকটা Agent-এর Input হয়
- একটা Agent-এর ভুল কীভাবে পরের Agent-এর কাজে প্রভাব ফেলতে পারে তার ধারণা পাওয়া

👀 O — Output

Module শেষে learner বলতে পারবে:
- Data Collection Agent, Data Analysis Agent, এবং Report Generation Agent-এর মধ্যে দায়িত্বের পার্থক্য কী
- কেন একটা Agent-এর কাজ শেষ না হলে পরের Agent শুরু করতে পারে না (Sequential Dependency)
- এই ধরনের Chain-এ একটা ভুল কীভাবে পরের ধাপে ছড়িয়ে যেতে পারে (Module 14-তে শেখা "ভুলের Chain Propagation"-এর একটা বাস্তব উদাহরণ)

🤔 R — Reason

জটিল কাজ (যেমন Threat Intelligence তৈরি করা) একসাথে অনেকগুলো ভিন্ন ধরনের দক্ষতা দাবি করে — তথ্য খোঁজা, বিশ্লেষণ করা, এবং গুছিয়ে উপস্থাপন করা। এই কাজগুলো একটা Agent-চেইনে ভাগ করলে প্রতিটা অংশ তার নির্দিষ্ট কাজে মনোযোগ দিতে পারে, কিন্তু এর মানে এই না যে চেইনটা নির্ভুল — প্রথম ধাপে ভুল তথ্য জোগাড় হলে, পরের প্রতিটা ধাপ সেই ভুলের উপর ভিত্তি করেই এগোবে।

🧠 Memory Tip

এই ধরনের Agent Chain-কে ভাবা যেতে পারে একটা "Assembly Line"-এর মতো — প্রতিটা Station একটা নির্দিষ্ট কাজ করে পরের Station-এ পাঠায়, কিন্তু প্রথম Station-এই যদি ভুল Part বসানো হয়, শেষ Station পর্যন্ত সেই ভুল বহন হতে থাকে।

⚠️ L — Limitation

- Sequential Chain-এ প্রতিটা ধাপ আগেরটার উপর নির্ভরশীল বলে, একটা ধাপ ধীর হলে পুরো Chain ধীর হয়ে যায়
- Data Collection Agent যদি Incomplete বা Biased তথ্য সংগ্রহ করে, Analysis এবং Report — দুটোই সেই Incomplete তথ্যের উপর ভিত্তি করে তৈরি হবে, কেউ সেটা ধরতে পারবে না যদি আলাদা Check না থাকে
- প্রতিটা ধাপ আলাদা হওয়ায়, সমস্যা হলে ঠিক কোন ধাপে হয়েছে তা বোঝা সহজ হলেও, ঠিক করতে পুরো Chain আবার চালাতে হতে পারে
- এই ধারণা এখনও একটা ধাপের ভুল কীভাবে ধরা এবং আটকানো যায় (Verification) তা নিয়ে বিস্তারিত বলে না — এটা Section B-এর বিষয়

✋ Y — Your Turn

Stock Market Investor-এর উদাহরণে, যদি প্রথম ধাপে (News সংগ্রহ) কোনো গুরুত্বপূর্ণ News Miss হয়ে যায়, তাহলে দ্বিতীয় এবং তৃতীয় ধাপে (Analysis, Report) তার প্রভাব কেমন হতে পারে তা ২-৩ বাক্যে লিখতে হবে।

