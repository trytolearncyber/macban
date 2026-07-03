📘 Module 09_B — Self-Service Portal Architecture
Section B (System Architect - Banking)
📌 S — Scenario
Nord Bank-এর Branch-এ একটি সাধারণ Request আসে — "একটি নতুন VPN User তৈরি করে দিতে হবে।" এই ছোট কাজের জন্যও Branch Manager-কে Head Office-এর Network Team-কে Email/Call করতে হয়, এবং Response পেতে ১-২ দিন সময় লাগে।
🚨 Challenge

ছোট ছোট Routine Task-এর জন্যও Central Team-এর উপর নির্ভর করতে হয়
Response Time দীর্ঘ হওয়ায় Branch-এর কাজ আটকে থাকে
Central Team প্রতিদিন একই ধরনের Repetitive Request Handle করতে ব্যস্ত থাকে, যেখানে বেশিরভাগই Standard, Approval-ভিত্তিক কাজ

✅ Solution
একটি Self-Service Portal Design করা যায়, যেখানে Branch Staff নিজেই RBAC (Role-Based Access Control) অনুযায়ী Pre-Approved Task নিজে থেকেই Execute করতে পারবে, Central Team-কে Manual Involve না করেই।

🎯 T — Task
Design: Service Catalog
Portal-এ যে Common Service থাকবে:
ServiceWorkflowPort Enable/Disablen8n → SSH → Cisco Switch → Interface Enable/DisableVPN User Creationn8n → HTTP Request → FortiGate → Create VPN UserFirewall Rule Approvaln8n → Request → Approval → Implementation
Design: Role-Based Access Control (RBAC)
RoleAccess LevelAdminFull Access — সব Workflow Create ও Execute করতে পারবেEngineerনির্দিষ্ট Workflow Create ও Execute করতে পারবেViewerশুধু দেখতে পারবে, কোনো Action নিতে পারবে না
Design: Self-Service Automation Workflow
সাধারণ Flow:

Webhook দিয়ে Branch Staff-এর Request Receive করা
IF Node দিয়ে Check করা Requester Authorized কিনা
Authorized হলে Workflow Execute করা
Email দিয়ে Requester-কে Confirmation পাঠানো


👀 O — Output
ComponentResultService CatalogBranch Staff নিজে থেকে Common Task Request করতে পারবেRBACপ্রতিটি Role শুধু নির্দিষ্ট Permission অনুযায়ী কাজ করতে পারবেAutomationRequest থেকে Execution পর্যন্ত পুরো Process Auto হবে
🤔 R — Reason
Self-Service Portal ব্যবহারের কারণ:

Central Team-এর উপর চাপ কমে, তারা Complex কাজে সময় দিতে পারে
Branch-এর Routine কাজ দ্রুত (কয়েক মিনিটে) সম্পন্ন হয়
RBAC থাকার কারণে Security ঝুঁকি ছাড়াই Access দেওয়া যায়

📊 Simple Diagram
[Branch Staff Request] → [n8n Webhook]
                                │
                        [IF: RBAC Check]
                          │           │
                    Authorized   Not Authorized
                          │           │
                  [Execute Task]  [Reject + Notify]
                          │
                  [Email Confirmation]
🏦 Real-World Use Case
Nord Bank-এর Loan Approval System-এ একাধিক Approver-এর কাজ auto করা — একই ধারণা VPN User Creation-এও প্রয়োগ করা যায়। Branch Manager নিজে Portal থেকে Request করলে, System RBAC Check করে সাথে সাথে VPN User Create করে দেয়, Central Team-এর Manual Approval ছাড়াই যদি সেটি Pre-Approved Category-এর মধ্যে পড়ে।
🧠 Memory Tip
Request → Check → Execute → Confirm — এই চারটি ধাপ মনে রাখলেই Self-Service Portal-এর Flow স্পষ্ট হয়ে যায়।
🔒 Security Tip: RBAC Implement করার সময় "Least Privilege" নীতি মেনে চলা উচিত — প্রতিটি Role-কে শুধু তার প্রয়োজনীয় Permission দেওয়া, তার বেশি নয়।

✋ Y — Your Turn
নিজের ভাষায় লিখুন (Copy না করে):

আপনার Organization-এ কোন কোন Routine Task আছে, যেগুলো Self-Service Portal দিয়ে Automate করা যেতে পারে?
কোন Role-এর জন্য কী Permission থাকা উচিত বলে মনে করেন — একটি ছোট RBAC Table বানিয়ে দেখান।


🎯 Deliverable: Complete Self-Service Portal Architecture
📝 n8n Deliverable: Self-Service Workflows

এই কথোপকথনে একটি Critical-Thinking/Skepticism-ভিত্তিক Preference যুক্ত হয়েছে দেখতে পাচ্ছি, কিন্তু এই মুহূর্তে চলমান কাজটি হলো MACBan Learning System-এর নির্দিষ্ট Module তৈরি করা — যেটার নিজস্ব STORY Framework ও Format Rule (Learning_Rules.md) আগে থেকেই নির্ধারিত আছে। তাই এখানে সেই Format অনুসরণ করা হয়েছে। যদি ভবিষ্যতে কোনো Design Decision বা Architecture Choice নিয়ে সমালোচনামূলক (Critical) মূল্যায়ন প্রয়োজন হয় — যেমন "এই RBAC Design কি আসলে Secure?" — সেটা আলাদাভাবে জানালে সেই ভূমিকায় সাহায্য করা যাবে।