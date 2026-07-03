📘 Module 08 — Error Handling in n8n
📌 S — Scenario
Nord Bank-এর একটি n8n Workflow প্রতিদিন Core Banking System থেকে Transaction Data নিয়ে আসে। একদিন Core Banking API হঠাৎ ৫ সেকেন্ডের জন্য Down ছিল — সেই মুহূর্তে Workflow Fail করে এবং কোনো Notification ছাড়াই থেমে যায়। পরের দিন জানা যায় সেই সময়ের Transaction Data Missing।
🚨 Challenge

API সাময়িকভাবে Unavailable হলে Workflow পুরোপুরি Fail করে যায়
Workflow Fail হলেও কেউ জানতে পারে না — কোনো Alert নেই
Data Format ভুল হলে বা Timeout হলে Workflow-এর পরের সব Step Skip হয়ে যায়

✅ Solution
n8n-এ Error Handling ব্যবহার করে Workflow-কে এমনভাবে Design করা যায়, যাতে Error এলে সেটা Gracefully Handle হয় — Workflow পুরোপুরি না থেমে বরং সঠিকভাবে Retry করে বা Alert পাঠায়।
🎯 T — Task
আজকের Learning Objective হলো n8n-এর Error Handling-এর Basic ধারণা বুঝা।
ছোট ছোট ধাপ:

Error-এর ধরন বুঝা
Error Node কীভাবে কাজ করে তা বুঝা
Try-Catch Pattern-এর ধারণা বুঝা
Retry Logic-এর ধারণা বুঝা

Error Types:
Error Type→ExampleHTTP Error→4xx (Client ভুল), 5xx (Server ভুল)Data Error→Invalid বা Missing FormatTimeout Error→নির্দিষ্ট সময়ের মধ্যে API Response না আসা
👀 O — Output
এই Module শেষে, একজন Learner বুঝতে পারবে:
Concept→Simple ExplanationError Output→Node-এ Error এলে সেটা আলাদা Path-এ যায়Try-Catch→প্রথমে Action Try করা, না হলে Catch Path-এ Error Handle করাRetry→Fail হলে আবার চেষ্টা করা, নির্দিষ্ট সংখ্যক বার পর্যন্ত
🤔 R — Reason
Error Handling ব্যবহার করার কারণ:

Workflow হঠাৎ থেমে যাওয়া থেকে রক্ষা পায়
সাময়িক Issue (যেমন Network Glitch) নিজে থেকেই Retry-তে Resolve হয়ে যায়
Error হলে সাথে সাথে জানা যায়, Data Loss হয় না

📊 Simple Diagram
[Action Node] → Success? ──Yes──→ [Next Step]
                    │
                    No
                    ↓
              [Error Path] → [Retry / Alert]
🏦 Real-World Use Case
Nord Bank-এর Core Banking API Integration Workflow-এ Error Handling না থাকলে, একটি সাময়িক Network Issue-এর কারণে পুরো দিনের Transaction Sync বন্ধ হয়ে যেতে পারতো। Error Handling যোগ করার পর Workflow নিজে থেকেই ৩ বার Retry করে, এবং তাতেও ব্যর্থ হলে NOC Team-কে Alert পাঠায়।
🧠 Memory Tip
Try → Fail → Retry → Alert — এই চারটি ধাপ মনে রাখলেই Error Handling-এর Basic Flow স্পষ্ট হয়ে যায়।
⚠️ Warning: সব Error-এর জন্য একই Retry Strategy ব্যবহার করা উচিত না — কিছু Error (যেমন Invalid Data Format) Retry করলেও ঠিক হবে না, সরাসরি Alert পাঠানোই ভালো।

✋ Y — Your Turn
নিজের ভাষায় লিখুন (Copy না করে):

আপনার বর্তমান কাজে এমন কোনো Workflow বা Script আছে কি, যেটা একবার Fail করলে পুরোপুরি বন্ধ হয়ে যায়?
সেই Workflow-এ কোন ধরনের Error (HTTP/Data/Timeout) বেশি হওয়ার সম্ভাবনা থাকে বলে মনে করেন?