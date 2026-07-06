📘 Module 12 — Enterprise RAG Architecture (Section B)

📌 S — Scenario (Nord Bank / Banking-Specific)

Nord Bank-এর NOC Team-এর কাছে বছরের পর বছর ধরে জমে থাকা Troubleshooting Document, SOP (Standard Operating Procedure), এবং Incident Report আছে — কয়েকশো Page। কোনো নতুন সমস্যা এলে, Engineer-রা প্রায়ই জানে না যে একই Problem আগেও একবার হয়েছিল এবং তার Solution ইতিমধ্যে Document করা আছে, কারণ সবকিছু আলাদা আলাদা Folder-এ ছড়িয়ে আছে এবং Keyword দিয়ে খুঁজলেও সঠিক Document পাওয়া কঠিন।

🚨 Challenge

- Institutional Knowledge (আগের Incident-এর Solution) Document আকারে থাকলেও, সহজে খুঁজে পাওয়া যাচ্ছিল না
- সাধারণ Keyword Search প্রায়ই কাজ করত না, কারণ Engineer যেভাবে প্রশ্ন করে (যেমন "VPN বারবার Disconnect হচ্ছে") আর Document-এ যেভাবে লেখা আছে (যেমন "IKE Phase 2 Renegotiation Failure") তার Wording আলাদা
- নতুন Engineer-রা পুরনো Solution সম্পর্কে না জেনে একই সমস্যা নতুন করে Debug করত, সময় নষ্ট করে
- Document আপডেট হলে পুরনো Version এবং নতুন Version গুলিয়ে ফেলার ঝুঁকি ছিল

✅ Solution

একটা Enterprise RAG System বসাতে হবে যেখানে সব SOP, Troubleshooting Guide, এবং Past Incident Report একটা Vector Database-এ সংরক্ষিত থাকবে, এবং Engineer Natural Language-এ প্রশ্ন করলে Semantic Search-এর মাধ্যমে সবচেয়ে প্রাসঙ্গিক অংশ খুঁজে বের করে LLM সেই তথ্যের ভিত্তিতে উত্তর তৈরি করবে।

🎯 T — Task

Nord Bank-এর জন্য একটা Enterprise RAG Architecture ডিজাইন করতে হবে যেখানে Retriever (Vector Search) এবং Generator (LLM) আলাদা, স্পষ্টভাবে সংজ্ঞায়িত Component হিসেবে কাজ করবে।

👀 O — Output

একটা Enterprise RAG Architecture Document যেখানে থাকবে:
- Document Ingestion Pipeline — SOP/Incident Report কীভাবে সংগ্রহ, Chunk (ছোট অংশে ভাগ), এবং Embed করে Vector Database-এ Store হবে
- Retriever Component Design — Engineer-এর প্রশ্নের সাথে সবচেয়ে কাছাকাছি অর্থের Document Chunk কীভাবে খুঁজে বের করা হবে
- Generator Component Design — Retrieve হওয়া Chunk-গুলো LLM-কে দিয়ে কীভাবে একটা সরাসরি, বোধগম্য উত্তর তৈরি করানো হবে
- Source Attribution — উত্তরের সাথে কোন Document/Section থেকে তথ্য এসেছে তা দেখানো, যাতে Engineer মূল Document গিয়ে Verify করতে পারে
- Document Freshness Handling — পুরনো Document Update বা Retire হলে Vector Database-এ কীভাবে Reflect হবে

🤔 R — Reason

NOC Environment-এ একই সমস্যা বারবার ঘটে, কিন্তু প্রতিবার নতুন করে Solve করা সময় এবং Effort নষ্ট করে। RAG ব্যবহার করলে Engineer-এর প্রশ্নের Wording ঠিক Document-এর ভাষার সাথে না মিললেও (Semantic Search-এর কারণে), সঠিক Past Solution খুঁজে পাওয়া সম্ভব হয় — যা Keyword Search দিয়ে সম্ভব ছিল না। Retriever এবং Generator-কে আলাদা রাখলে, কোনো ভুল উত্তর এলে ঠিক কোন অংশে সমস্যা হয়েছে (ভুল Document Retrieve হয়েছে, নাকি LLM ভুল ব্যাখ্যা করেছে) তা আলাদা করে বোঝা সহজ হয়।

🏦 Real-World Use Case

Nord Bank-এর একজন Engineer জিজ্ঞেস করে "VPN বারবার Disconnect হচ্ছে, কী করব?" RAG System Vector Database থেকে ৬ মাস আগের একটা Incident Report খুঁজে বের করে যেখানে ঠিক এই সমস্যা "IKE Phase 2 Renegotiation Failure" নামে Document করা ছিল। LLM সেই Document পড়ে সহজ ভাষায় উত্তর দেয় এবং সাথে জানায় "Source: Incident Report #INC-2024-118", যাতে Engineer চাইলে মূল Report-ও পড়তে পারে।

🧠 Memory Tip

RAG Architecture-কে ভাবা যেতে পারে একটা "Librarian + Answering Clerk" টিমের মতো — Librarian (Retriever) সঠিক বই-এর সঠিক পাতা খুঁজে বের করে দেয়, আর Answering Clerk (LLM/Generator) শুধু সেই পাতা পড়ে সহজ ভাষায় উত্তর লেখে, নিজে থেকে অন্য কিছু অনুমান করে না।

⚠️ L — Limitation

- Document Chunking ভুলভাবে করলে (যেমন একটা গুরুত্বপূর্ণ Warning Sentence মাঝপথে কেটে ফেলা), Retriever সঠিক Chunk খুঁজে পেলেও তার Context Incomplete থাকতে পারে
- Semantic Search মাঝে মাঝে "কাছাকাছি অর্থের" ভুল Document তুলে আনতে পারে, যা দেখতে প্রাসঙ্গিক মনে হলেও আসলে ভিন্ন সমস্যার সমাধান
- Source Attribution থাকলেও, Engineer যদি Verify না করেই সরাসরি Suggestion Follow করে, ভুল Retrieve হওয়া তথ্যের উপর ভিত্তি করে ভুল Action নিতে পারে
- Vector Database নিয়মিত Update না করলে, নতুন Incident-এর Solution পুরনো, Outdated Document-এর সাথে মিশে গিয়ে বিভ্রান্তি তৈরি করতে পারে

✋ Y — Your Turn

Nord Bank-এর RAG System যদি একটা Incident Report থেকে ভুল Section Retrieve করে (Context বাদ পড়ে গিয়ে), Engineer কীভাবে বুঝবে যে উত্তরটা ভুল হতে পারে — Source Attribution ছাড়া আর কী Check করা উচিত তা ২-৩ বাক্যে লিখতে হবে।

---

**Extra (তোমার 12A-এর Critique-এর ধারাবাহিকতায় যোগ করা হলো):**

12A-তে "Open-Book Exam" Memory Tip-এর সমস্যা ছিল Student এক Actor হিসেবে Retrieve আর Generate দুটোই করছিল বলে মনে হচ্ছিল। এই 12B Document-এ Task, Output, Reason, এবং Memory Tip — সব জায়গাতেই Retriever আর Generator-কে সচেতনভাবে আলাদা, নামযুক্ত Component হিসেবে রাখা হয়েছে (Librarian vs Clerk), যাতে 12A-এর Concept-লেভেল ভুলটা 12B-এর Architecture-লেভেলে গিয়ে আবার না ছড়ায়। যদি মনে হয় 12A-এর Memory Tip-টাও এখন retroactively ঠিক করা দরকার (যেহেতু 12B-তে সঠিক Version আছে), সেটা একটা আলাদা Fix হিসেবে বলতে পারো।
