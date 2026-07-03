📘 Module 06_B — SOAR Framework
Section B (System Architect - Banking)
📌 S — Scenario
Nord Bank-এর 50+ FortiGate Firewall এবং Cisco Firepower থেকে প্রতিদিন হাজার হাজার Log Generate হয়। Security Team manually এই Log Review করতে পারে না — এত বিপুল পরিমাণ Data-তে Critical Threat হারিয়ে যাওয়ার ঝুঁকি থাকে।
🚨 Challenge

500+ Device থেকে আসা Log manually Monitor করা সম্ভব নয়
Critical Alert এবং Low-Priority Event একসাথে মিশে থাকে — আলাদা করা কঠিন
Alert আসার পর সঠিক Team-এর কাছে পৌঁছাতে দেরি হয়, ফলে Response Time বেড়ে যায়

✅ Solution
n8n দিয়ে একটি SOAR (Security Orchestration, Automation and Response) Workflow তৈরি করা যায়, যা Log Receive করে, Severity অনুযায়ী Classify করে, এবং সঠিক Channel-এ Alert পাঠায়।

🎯 T — Task
Design: Firewall Log Monitoring System
Webhook দিয়ে Log Receive করা
FortiGate এবং Cisco Firepower-এর Syslog n8n Webhook-এ পাঠানো হবে।
Log Parse করা
Function Node দিয়ে Log-এর ভেতর থেকে দরকারি Information (Source IP, Destination IP, Message, Severity) বের করা হবে।
Suspicious Activity Check করা
IF Node দিয়ে Condition বসিয়ে Event-এর Type অনুযায়ী আলাদা Path-এ পাঠানো হবে — যেমন Port Scan হলে Critical, Malware Traffic হলে High।
Design: Security Event Severity Classification
PriorityExample EventsP1 (Critical)System Down, Security Breach, Data LossP2 (High)Performance Degradation, Suspicious Activity, Malware DetectionP3 (Medium)Failed Logins, Configuration Change, Policy ViolationP4 (Low)Informational Events, User Activity, System Audit
Design: Multi-Channel Alerting Strategy
Alert-এর Severity অনুযায়ী আলাদা Channel-এ পাঠানো হয়:

Email → P2, P3, P4 Event-এর জন্য
SMS (Twilio) → P1, P2 Event-এর জন্য
Teams/Slack → সব Event-এর জন্য
Phone Call Escalation → শুধুমাত্র P1 Event-এর জন্য

Design: On-Call Rotation Integration
PagerDuty-এর সাথে Integration করে On-Call Schedule অনুযায়ী সঠিক Engineer-এর কাছে Alert Route করা হয়।

👀 O — Output
এই Design সম্পন্ন হলে যা পাওয়া যাবে:
ComponentResultLog Monitoring500+ Device-এর Log Real-time Receive হবেClassificationপ্রতিটি Event নিজে থেকেই P1-P4 Category-তে ভাগ হবেAlertingSeverity অনুযায়ী সঠিক Team সঠিক সময়ে Notification পাবে
🤔 R — Reason
SOAR Framework ব্যবহারের কারণ:

Manual Log Review-এর সময় বাঁচে
Critical Threat দ্রুত চিহ্নিত হয়, Response Time কমে
On-Call Rotation-এর মাধ্যমে সঠিক Engineer সঠিক সময়ে জানতে পারে

📊 Simple Diagram
[FortiGate/Cisco Syslog] → [n8n Webhook] → [Function: Parse Log]
                                              │
                                    [IF: Severity Check]
                                              │
              ┌───────────────┬──────────────┼──────────────┐
              │               │               │              │
            P1              P2              P3              P4
    (Call+SMS+Slack)   (SMS+Email+Slack)  (Email+Slack)   (Slack Only)
🏦 Real-World Use Case
Nord Bank-এর NOC Team-কে আগে Firewall Log manually Review করতে দিনে ৪ ঘন্টা সময় দিতে হতো। SOAR Workflow Implement করার পর Critical Alert গড়ে ২ মিনিটের মধ্যে On-Call Engineer-এর কাছে পৌঁছায়।
🧠 Memory Tip
P1 = Phone, P2 = Pager(SMS), P3 = Post(Email), P4 = Ping(Slack) — Priority যত বাড়বে, Alert Channel তত Urgent হবে।
🔒 Security Tip: Webhook Endpoint অবশ্যই Authentication (API Key/Token) দিয়ে Secure করতে হবে, নাহলে যে কেউ Fake Alert পাঠিয়ে System Flood করতে পারে।

✋ Y — Your Turn
নিজের ভাষায় লিখুন (Copy না করে):

আপনার Organization-এ যদি একটি নতুন Severity Level (যেমন P0 — Emergency) যোগ করতে হয়, তাহলে সেটার Alert Channel Strategy কেমন হবে?
FortiGate ছাড়া অন্য কোনো Device (যেমন MikroTik) থেকে Log নিতে হলে Workflow-এ কী পরিবর্তন লাগবে বলে মনে করেন?


🎯 Deliverable: Complete Security Alerting & SOAR Architecture
📝 n8n Deliverable: Security Alert Escalation Workflow