┌─────────────────────────────────────────────────────────────────────────────┐
│                    Windows 11 + Ubuntu VM Integration                       │
├─────────────────────────────────────────────────────────────────────────────┤
│                                                                             │
│   💻 Windows 11 Host (192.168.10.1)                                        │
│   │                                                                        │
│   ├── 🎯 Mockoon (Port 3001)                                               │
│   │   ├── /api/v1/network/* → Network APIs                                 │
│   │   ├── /api/v1/security/* → Security APIs                               │
│   │   ├── /api/v1/banking/* → Banking APIs                                 │
│   │   ├── /api/v1/branches/* → Branch APIs                                 │
│   │   └── /api/v1/monitoring/* → Monitoring APIs                          │
│   │                                                                        │
│   ├── 🛠️ Postman (API Testing)                                            │
│   ├── 📐 Draw.io (Diagrams)                                                │
│   │                                                                        │
│   └──────────────┬───────────────────────────────────────────────────────  │
│                  │ Bridge Network (VMware NAT/Host-Only)                   │
│                  ▼                                                         │
│   ┌─────────────────────────────────────────────────────────────────────┐   │
│   │                                                                     │   │
│   │   🐧 Ubuntu VM (192.168.10.128)                                    │   │
│   │   │                                                                  │   │
│   │   ├── 🔄 n8n (Port 5678)                                            │   │
│   │   │   └── Workflows that CALL Mockoon APIs                         │   │
│   │   │                                                                  │   │
│   │   ├── 🐳 Docker Containers:                                         │   │
│   │   │   ├── PostgreSQL (Database)                                     │   │
│   │   │   ├── Redis (Cache)                                             │   │
│   │   │   ├── Grafana (Dashboard)                                      │   │
│   │   │   └── Prometheus (Metrics)                                      │   │
│   │   │                                                                  │   │
│   │   └── 🌐 ngrok (External Access)                                   │   │
│   │                                                                      │   │
│   └─────────────────────────────────────────────────────────────────────┘   │
│                                                                             │
└─────────────────────────────────────────────────────────────────────────────┘


📁 Windows 11 Mockoon File Location
C:\mockoon\
│
├── banking-simulation.json     # Complete Mockoon Config
├── mockoon-cli.exe              # Mockoon CLI
│
└── exports/
    ├── network-api.json         # Network APIs Export
    ├── security-api.json        # Security APIs Export
    ├── banking-api.json         # Banking APIs Export
    └── monitoring-api.json      # Monitoring APIs Export



┌─────────────────────────────────────────────────────────────────────────────┐
│                    রিয়েল ব্যাংক → ল্যাব সিমুলেশন                          │
├─────────────────────────────────────────────────────────────────────────────┤
│                                                                             │
│   রিয়েল ব্যাংক                      ল্যাব সিমুলেশন                       │
│   ═══════════════                    ════════════════                      │
│                                                                             │
│   Cisco ASR 1000 Router       →     GNS3/EVE-NG (Virtual Router)          │
│   Cisco Catalyst 9500 Switch  →     GNS3/EVE-NG (Virtual Switch)          │
│   FortiGate 3000 Firewall     →     FortiGate VM (Trial)                  │
│   Cisco Firepower IPS         →     Snort/Suricata (Open Source)          │
│   Cisco ISE (NAC)             →     FreeRADIUS + PacketFence              │
│   VMware ESXi Cluster         →     VMware Workstation (Your VM)          │
│   Dell PowerEdge Server       →     Ubuntu VM (Your VM)                   │
│   Oracle/SQL Server           →     PostgreSQL/MySQL (Docker)             │
│   T24 Core Banking            →     Mockoon API (Mock)                    │
│   Cisco CUCM (VoIP)           →     Asterisk/FreeSWITCH (Docker)          │
│   Zabbix/PRTG Monitoring      →     Zabbix/Prometheus (Docker)            │
│   Splunk/QRadar SIEM          →     Elastic Stack (Docker)               │
│   Windows AD/DNS/DHCP         →     Samba AD + Bind9 (Docker)            │
│   n8n Automation              →     n8n (Already Installed)               │
│                                                                             │
└─────────────────────────────────────────────────────────────────────────────┘

┌─────────────────────────────────────────────────────────────────────────────┐
│                    অপশন ১: মিনিমাল ল্যাব (সুপারিশকৃত)                      │
├─────────────────────────────────────────────────────────────────────────────┤
│                                                                             │
│   💻 Windows Host                                                          │
│   │                                                                        │
│   ├── 🛠️ Mockoon → Bank API Mock (T24, Payment Switch)                    │
│   ├── 🛠️ Draw.io → Architecture Diagrams                                  │
│   ├── 🛠️ Postman → API Testing                                            │
│   │                                                                        │
│   └── 🖥️ VMware Workstation                                               │
│       │                                                                    │
│       └── 🐧 Ubuntu VM (192.168.10.128) — আপনার মেইন ল্যাব               │
│           │                                                               │
│           ├── 🐳 Docker Containers:                                       │
│           │   ├── n8n → Workflow Automation ✅ Already Installed          │
│           │   ├── PostgreSQL → Database for n8n                           │
│           │   ├── Redis → Cache & Queue                                   │
│           │   ├── Grafana → Dashboard & Visualization                     │
│           │   ├── Prometheus → Metrics Collection                         │
│           │   ├── Zabbix → Network Monitoring (Simulate)                 │
│           │   ├── Graylog → Log Management                                │
│           │   ├── Elasticsearch → Log Storage                             │
│           │   ├── Kibana → Log Visualization                              │
│           │   ├── Mosquitto → MQTT Broker                                │
│           │   ├── Node-RED → IoT/Integration (Optional)                  │
│           │   └── Portainer → Docker Management                          │
│           │                                                               │
│           ├── 🌐 Services:                                               │
│           │   ├── ngrok → Expose n8n to Internet ✅ Already Installed    │
│           │   ├── Python → Custom Scripts                                │
│           │   └── Git → Version Control                                  │
│           │                                                               │
│           └── 📁 Projects:                                               │
│               ├── /opt/n8n-workflows/ → n8n Workflows                    │
│               ├── /opt/ansible/ → Ansible Playbooks                      │
│               ├── /opt/scripts/ → Python/Bash Scripts                    │
│               └── /opt/mockoon/ → Mockoon Configs                        │
│                                                                             │
└─────────────────────────────────────────────────────────────────────────────┘


┌─────────────────────────────────────────────────────────────────────────────┐
│                    অপশন ২: অ্যাডভান্সড ল্যাব                               │
├─────────────────────────────────────────────────────────────────────────────┤
│                                                                             │
│   💻 Windows Host                                                          │
│   │                                                                        │
│   ├── 🖥️ VMware Workstation                                               │
│   │   │                                                                    │
│   │   ├── 🐧 Ubuntu VM (192.168.10.128) — Automation & Services          │
│   │   │   ├── n8n, Docker Containers                                     │
│   │   │   └── All services as above                                      │
│   │   │                                                                    │
│   │   ├── 🖥️ GNS3 VM — Network Simulation                               │
│   │   │   ├── Cisco ASR 1000 (Virtual) — Core Router                     │
│   │   │   ├── Cisco Catalyst 9500 (Virtual) — Core Switch                │
│   │   │   ├── Cisco ISR 4000 (Virtual) — Branch Router                   │
│   │   │   ├── Cisco Catalyst 9300 (Virtual) — Distribution Switch        │
│   │   │   ├── Cisco Catalyst 9200 (Virtual) — Access Switch              │
│   │   │   ├── FortiGate VM — Firewall                                    │
│   │   │   └── MikroTik RouterOS (Virtual) — LTE Backup                   │
│   │   │                                                                    │
│   │   └── 🖥️ Security VM — Security Tools                               │
│   │       ├── Security Onion — IDS/IPS                                   │
│   │       ├── Snort/Suricata — IPS                                       │
│   │       └── Kali Linux — Penetration Testing                           │
│   │                                                                        │
│   └── 🛠️ Tools:                                                          │
│       ├── Mockoon → Bank API Mock                                        │
│       ├── Draw.io → Diagrams                                             │
│       └── Postman → API Testing                                          │
│                                                                             │
└─────────────────────────────────────────────────────────────────────────────┘
