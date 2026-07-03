📘 Module 08_B — Resiliency Framework
Section B (System Architect - Banking)
📌 S — Scenario
Nord Bank-এর একটি Core Banking Integration Workflow-এ একবার API Call Fail হওয়ার পর কোনো Retry Mechanism ছিল না। ফলে সেই একটি Failed Transaction চিরতরে হারিয়ে যায় — কোনো Log নেই, কোনো Trace নেই, এবং Audit-এর সময় কেউ ব্যাখ্যা দিতে পারেনি কী হয়েছিল।
🚨 Challenge

একবার Fail হলে Transaction চিরতরে হারিয়ে যায়, কোনো Recovery Path নেই
Critical Failure হলেও কেউ তৎক্ষণাৎ জানতে পারে না — Manual Intervention দরকার হলেও কোনো Mechanism নেই
Compliance Audit-এর সময় কী হয়েছিল তার কোনো Trail (রেকর্ড) পাওয়া যায় না

✅ Solution
একটি Complete Resiliency Framework Design করা যায়, যেখানে চারটি স্তরে সুরক্ষা থাকবে: Exponential Backoff Retry, Dead-Letter Queue, Human-in-the-Loop, এবং Audit Trail।

🎯 T — Task
Design: Retry Logic with Exponential Backoff
সাধারণ Retry-তে প্রতিবার একই সময় Wait করা হয়, কিন্তু Exponential Backoff-এ Wait Time প্রতিবার বাড়তে থাকে:
AttemptWait TimeAttempt 12 সেকেন্ডAttempt 24 সেকেন্ডAttempt 38 সেকেন্ডAttempt 416 সেকেন্ডAttempt 532 সেকেন্ড5 বারের পরও FailAlert পাঠানো
Design: Dead-Letter Queue
যে Message বারবার চেষ্টা করেও Process করা যায়নি, সেটাকে সরাসরি বাতিল না করে একটি আলাদা জায়গায় (Dead-Letter Queue) সংরক্ষণ করা হয়:

Failed Message → Dead-Letter Queue-তে যাবে
Storage হিসেবে PostgreSQL বা Redis ব্যবহার করা যায়
Admin-কে Notification পাঠিয়ে Manual Review করতে বলা হয়

Design: Human-in-the-Loop for Critical Failures
সাধারণ Failure Auto-Retry দিয়ে সামলানো যায়, কিন্তু Critical Failure-এর ক্ষেত্রে মানুষের Involvement প্রয়োজন হয়:

Critical Failure হলে On-Call Engineer-কে Email পাঠানো হবে
৩০ মিনিট অপেক্ষা করা হবে Manual Fix-এর জন্য
৩০ মিনিটেও কোনো Action না হলে পরবর্তী Level-এ Escalate করা হবে

Design: Audit Trail Implementation
প্রতিটি Workflow Step Database-এ Log করা হয়, যাতে পরবর্তীতে Compliance Report তৈরি করা যায়:

প্রতিটি ধাপের জন্য Timestamp, User, Action, Status রেকর্ড রাখা হয়
Compliance Reporting-এর সময় এই Log Query করে ব্যবহার করা যায়


👀 O — Output
ComponentResultRetry Logicসাময়িক Failure নিজে থেকেই সমাধান হবেDead-Letter Queueকোনো Transaction চিরতরে হারাবে নাHuman-in-LoopCritical Issue সঠিক সময়ে সঠিক ব্যক্তির কাছে পৌঁছাবেAudit TrailCompliance Audit-এর সময় সম্পূর্ণ History পাওয়া যাবে
🤔 R — Reason
এই Framework ব্যবহারের কারণ:

Banking System-এ একটি Transaction হারিয়ে যাওয়া মানে সরাসরি আর্থিক ক্ষতি বা Compliance Violation
Regulatory Body (Bangladesh Bank) Audit Trail ছাড়া কোনো System Approve করে না
Human-in-the-Loop থাকলে Automation পুরোপুরি Uncontrolled হয়ে যায় না, Critical Decision-এ মানুষ জড়িত থাকে

📊 Simple Diagram
[Transaction Request]
        │
        ▼
[Try: API Call] ──Success──→ [Complete + Audit Log]
        │
      Fail
        │
        ▼
[Retry: 2s→4s→8s→16s→32s]
        │
      Still Fail
        │
        ▼
[Dead-Letter Queue] + [Critical? → Human-in-Loop]
        │
        ▼
[Audit Trail: সব ধাপ রেকর্ড]
🏦 Real-World Use Case
Nord Bank-এর SWIFT Payment Workflow-এ Resiliency Framework Implement করার পর, একটি Network Glitch-এর কারণে Fail হওয়া Payment Message Retry-তে ৩ বারের মধ্যেই Success হয়ে যায়। যেগুলো তাতেও Fail হয়, সেগুলো Dead-Letter Queue-তে জমা থেকে Payment Officer-এর Manual Review-এর অপেক্ষায় থাকে — কোনো Payment হারিয়ে যায় না।
🧠 Memory Tip
Retry → Queue → Human → Audit — চারটি স্তর, প্রতিটি স্তর আগেরটা Fail করলে পরেরটা Activate হয়।
🔒 Security Tip: Dead-Letter Queue-তে থাকা Data-তে যদি Sensitive Information (Account Number, Amount) থাকে, তাহলে সেটাও Encryption দিয়ে সুরক্ষিত রাখতে হবে — Failed Data মানে Unprotected Data নয়।

✋ Y — Your Turn
নিজের ভাষায় লিখুন (Copy না করে):

আপনার মতে, কোন ধরনের Failure-কে "Critical" বলে Classify করা উচিত, যেখানে Human-in-the-Loop বাধ্যতামূলক হবে?
Dead-Letter Queue-তে জমে থাকা Message কতদিন পর্যন্ত রাখা উচিত বলে মনে করেন, এবং কেন?


🎯 Deliverable: Complete Error Handling & Resiliency Framework
📝 n8n Deliverable: Error Recovery Workflow