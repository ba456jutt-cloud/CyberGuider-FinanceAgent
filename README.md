<div align="center">
  
# 🛡️ Cyber Guider AI: Autonomous Financial Defense Agent
**Google Antigravity Hackathon Submission**

*Empowering citizens with a hyper-vigilant AI agent that intercepts, analyzes, and neutralizes financial fraud and social engineering attacks in real-time.*

</div>

---

## 🚀 The Problem
Financial fraud in Pakistan—ranging from E-Challan scams to BISP/Ehsaas program impersonations and banking OTP theft—has evolved. Scammers use highly sophisticated social engineering tactics via SMS, WhatsApp, and fake portals. Traditional rule-based detectors are too slow and rigid to catch these dynamic threats, leaving vulnerable citizens unprotected.

## 💡 Our Solution
**Cyber Guider AI** is a multi-modal, autonomous cybersecurity agent built on **Google Gemini 1.5 Flash**. Instead of just flagging a message, the agent operates in **"Hunter Mode"**. It actively thinks, investigates, extracts hidden forensic metadata, and executes protective actions autonomously. 

### ✨ Key Features
1. **Multi-Modal Cognitive Auditing**: Send it a suspicious SMS, an audio voice note, or a screenshot of an E-Challan. The Vision Engine instantly extracts the context and intent behind the media.
2. **"Antigravity" Autonomous Actions**: When a critical threat is detected, the agent synthesizes tool calls dynamically:
   - `RecommendFreeze`: Automatically simulates flagging the user's bank account to halt transactions.
   - `NotifyBank`: Dispatches forensic telemetry to the financial institution.
   - `SyncThreatIntel`: Updates a global SQLite neural blacklist so no one else falls for the same scam.
3. **Automated FIA Cybercrime FIR**: Generates a professional, legally structured English complaint (PDF) addressed to the FIA Cybercrime Wing, explicitly quoting the scammer's message and the extracted forensic evidence.
4. **Live Chain-of-Thought Telemetry**: The Android app visually streams the AI's internal reasoning (NDJSON) so the user can see exactly *why* a message is safe or dangerous in real-time.
5. **Context-Aware Safety**: It intelligently distinguishes between harmless everyday conversations ("Hello, how are you?") and malicious phishing attempts.

---

## 🏗️ Architecture Stack

*   **Android Frontend**: High-performance Jetpack Compose UI that streams the agent's thought process and renders live security outcomes.
*   **FastAPI Backend**: A highly asynchronous, zero-latency Python backend that handles image and audio streams purely in-memory.
*   **Google Gemini AI**: The core cognitive engine for text/vision processing.
*   **Dataset (SQLite)**: A sub-10ms neural cache to intercept known scams instantly before wasting API calls.

---

## ☁️ Deployment & Testing

The backend is structurally optimized for **Google Cloud Run** and **Hugging Face Spaces**. 

### 1. Run Locally
```bash
# Clone and install dependencies
git clone <repository_url>
cd CyberGuider_FinanceAgent
python -m venv venv
source venv/bin/activate
pip install -r requirements.txt

# Set your Gemini API Key
export GEMINI_API_KEY="your-api-key"

# Start the server
python run_backend.py
```

### 2. Google Cloud Run Deployment
A clean `cloud_ready` folder is provided with a dynamic `Dockerfile` that routes ephemeral storage to `/tmp`.
```bash
cd cloud_ready
gcloud run deploy cyber-guider-api \
  --source . \
  --platform managed \
  --region us-central1 \
  --allow-unauthenticated \
  --set-env-vars GEMINI_API_KEY="your-api-key"
```

Once deployed, copy the generated Service URL, place it in the Android App's `FinanceViewModel.kt` (`baseUrl`), and compile the APK.

---

## 🤝 Conclusion
Cyber Guider AI represents the next generation of proactive defense. By shifting from passive detection to active, autonomous "hunting," we provide everyday users with enterprise-grade financial security in their pockets. 
