# 🖥️ MACBan Lab Environment

Windows Host
│
├── VMware Workstation
│
└── Ubuntu VM (192.168.10.128)
    │
    ├── Docker
    ├── Docker Compose
    ├── n8n
    ├── ngrok
    │
    └── Future
        ├── ChromaDB
        ├── Redis
        ├── Langflow
        ├── Prometheus
        └── Grafana


## Windows Host (Direct Install)

| Software | Purpose |
|----------|---------|
| Mockoon Desktop | Fake Bank API |
| Draw.io Desktop | Architecture Diagram |
| Postman | API Testing |
| VMware Workstation | Run Ubuntu VM |


# 🐧 VMware Ubuntu VM
## VM Specifications

| Item | Details |
|------|---------|
| OS | Ubuntu (GNS3 VM) |
| RAM | 12 GB  |
| IP Address | 192.168.10.128 |
| Username | gns3 |
| Home Directory | `/home/gns3` |


# 📁 Docker Compose Location

~/macban/
├── docker-compose.yml
└── .env
```

---

# 📄 docker-compose.yml
services:

  n8n:
    image: n8nio/n8n
    restart: unless-stopped
    ports:
      - "5678:5678"
    environment:
      - N8N_HOST=${NGROK_DOMAIN}
      - N8N_PROTOCOL=https
      - WEBHOOK_URL=${NGROK_URL}/
      - N8N_EDITOR_BASE_URL=${NGROK_URL}
      - GENERIC_TIMEZONE=Asia/Dhaka
      - TZ=Asia/Dhaka
      - N8N_SECURE_COOKIE=false
    volumes:
      - n8n_data:/home/node/.n8n

  ngrok:
    image: ngrok/ngrok:latest
    restart: unless-stopped
    ports:
      - "4040:4040"
    environment:
      - NGROK_AUTHTOKEN=${NGROK_AUTH_TOKEN}
    command: http n8n:5678 --domain=${NGROK_DOMAIN}
    depends_on:
      - n8n

volumes:
  n8n_data:
```

---

# 📄 .env
NGROK_DOMAIN=subheader-agreeable-coffee.ngrok-free.dev
NGROK_URL=https://sub.......ngrok-free.dev
NGROK_AUTH_TOKEN=YOUR_NGROK_AUTH_TOKEN
```
---

# 🚀 Running Services

| Container | Port | URL |
|-----------|------|-----|
| macban-n8n-1 | 5678 | http://192.168.10.128:5678 |
| macban-ngrok-1 | 4040 | http://192.168.10.128:4040 |

---

# 🌍 Public Access

| Service | URL |
|---------|-----|
| n8n Public | https://sub.........ngrok-free.dev |
| ngrok Dashboard | http://192.168.10.128:4040 |

