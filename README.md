# SOC-Home-Lab-AI-Based-Alert-Triage-using-AIRIA
## 📌 Project Overview

This project demonstrates a SOC (Security Operations Center) home lab where network traffic is monitored, suspicious activity is detected, and alerts are automatically analyzed using an AI-powered SOC playbook (AIRIA AI Agent).

The system simulates a real-world SOC workflow:

- Detect attack traffic
- Generate alerts
- Send alerts to AI
- Receive triage recommendations
## 🏗️ Architecture Overview
![Image]()
- Attacker Machine (Ubuntu) → Generates high traffic (ICMP flood)
- Internal Server (Kali Linux) → Runs Python automation for detection
- AIRIA AI Create Agent → Processes SOC playbook
- Published AIRIA Agent → Returns analysis & recommendations
## ⚙️ Workflow Explanation (Step-by-Step)
### 🔹 1. AIRIA AI Agent Setup
- Created a project in AIRIA.ai
- Selected OpenAI 5.0 Nano model
- Generated a default AI agent
- Integrated a custom SOC playbook

The playbook defines:

- Threat classification
- Risk scoring
- MITRE mapping
- SOC response actions

After testing:

Agent was published (Private mode)
API endpoint & API key were generated
### 🔹 2. Internal Server (Python Automation – Kali Linux)

A Python-based monitoring system was developed to:

#### ✅ Key Functions:
- Capture network traffic using tshark
- Convert PCAP → CSV
- Analyze traffic volume per IP
- Detect suspicious activity using threshold
- Generate structured alert JSON
- Send alert to AIRIA API

#### 🔍 Detection Logic
- Monitors ICMP traffic to internal server
- Counts packets per source IP
- If packet count > threshold → flagged as suspicious
  
  ```python
  THRESHOLD = 40
  
#### 🚨 Alert Generation

When threshold is exceeded:

A structured JSON alert is created:

```json
{
  "alert_type": "Suspicious Network Volume",
  "indicator_value": "attacker_ip",
  "packet_count": count
}
```
### 🔹 3. Attack Simulation (Ubuntu Machine)
- Attacker machine sends high-volume ICMP requests
- Target → Kali Internal Server IP
- Simulates:
  - Network scanning / flood attack

### 🔹 4. AI-Based SOC Analysis (AIRIA)

When alert is triggered:

➡️ Python script sends alert via API
➡️ AIRIA agent processes it using SOC playbook
➡️ AI returns structured SOC response:

- Threat classification
- Risk score
- MITRE ATT&CK mapping
- Recommended actions
- Executive summary

### 🔹 5. Output
- Results displayed directly in Kali terminal
- Includes:
  - Attack analysis
  - Risk level
  - SOC recommendations
  - 
### 🔁 End-to-End Flow
```python
Attacker (Ubuntu)
        ↓
Internal Server (Kali - Python Automation)
        ↓
Alert Generated (JSON)
        ↓
AIRIA AI Agent (SOC Playbook)
        ↓
AI Response (Triage Report)
        ↓
Displayed in Kali Terminal
```

### 🧠 Key Features
✅ Real-time traffic monitoring
✅ Automated alert generation
✅ AI-driven SOC triage
✅ MITRE ATT&CK mapping
✅ Risk scoring system
✅ End-to-end automation

### 🛡️ SOC Concepts Implemented
- Network Traffic Analysis
- Alert Engineering
- SOC Playbooks
- Threat Classification
- Incident Triage
- AI in Cybersecurity

### 📊 Use Case

This project simulates how modern SOC teams can:

- Reduce manual analysis
- Automate alert triage
- Improve response time using AI

### ⚠️ Important Notes
- This is a lab environment simulation
- No real attack infrastructure used
- Designed for learning & demonstration purposes only
