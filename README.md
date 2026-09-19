# AgriVision-AI
AgriVision AI ("One Plant, One AI Assistant") is a mobile-first web app. A farmer photographs a sick plant. The app diagnoses the problem, then gives advice that accounts for the local weather. The farmer can keep asking questions by voice.
<div align="center">

# 🌱 AgriVision AI

### One Plant, One AI Assistant

**An AI companion that sees, understands, and speaks with every farmer, instantly.**

![Status](https://img.shields.io/badge/status-hackathon%20MVP-green)
![React](https://img.shields.io/badge/frontend-React.js-61DAFB?logo=react&logoColor=white)
![Tailwind](https://img.shields.io/badge/style-Tailwind%20CSS-38B2AC?logo=tailwindcss&logoColor=white)
![FastAPI](https://img.shields.io/badge/backend-FastAPI-009688?logo=fastapi&logoColor=white)
![MongoDB](https://img.shields.io/badge/database-MongoDB-47A248?logo=mongodb&logoColor=white)
![Gemini](https://img.shields.io/badge/AI-Google%20Gemini-4285F4?logo=google&logoColor=white)

**Team NEXVION · HACKFRONT INDIA · Track: AgriTech**

</div>

---

## 📖 Table of Contents

- [About the Project](#-about-the-project)
- [The Problem](#-the-problem)
- [Our Solution](#-our-solution)
- [Key Features](#-key-features)
- [How It Works: the SUAA Framework](#-how-it-works-the-suaa-framework)
- [System Architecture](#-system-architecture)
- [Tech Stack](#-tech-stack)
- [Project Structure](#-project-structure)
- [Getting Started](#-getting-started)
- [Environment Variables](#-environment-variables)
- [API Overview](#-api-overview)
- [How We Compare](#-how-we-compare)
- [Roadmap](#-roadmap)
- [Impact and Beneficiaries](#-impact-and-beneficiaries)
- [Research and References](#-research-and-references)
- [Limitations](#-limitations)
- [Team](#-team)
- [Contributing](#-contributing)
- [License](#-license)

---

## 🌾 About the Project

**AgriVision AI** is an AI-powered plant diagnosis and farmer advisory app. A farmer photographs a sick plant with a smartphone. The app identifies the plant and its problem, then gives advice based on the **real-time local weather**. The farmer can then keep asking questions **by voice**.

Our goal is to turn any smartphone into a personal agronomist.

> **Track / Domain:** AgriTech: AI-Powered Crop Health & Advisory (Software)
> **Hackathon:** HACKFRONT INDIA

---

## ⚠️ The Problem

| Challenge | What farmers face today |
|---|---|
| **Delay** | Days of waiting for an expert, a lab result, or an agronomist visit |
| **Generic advice** | One-size-fits-all guidance that ignores local conditions |
| **Accessibility** | Apps that are hard to use without literacy or technical skill |
| **Expert shortage** | India's extension worker-to-farmer ratio is far below recommended levels |

---

## 💡 Our Solution

AgriVision AI answers each of these challenges:

- **Days of waiting** → multi-image diagnosis in seconds, with no lab needed.
- **Generic advice** → recommendations grounded in each farmer's real-time local forecast.
- **Hard to use** → natural voice conversation that works at every literacy level.

---

## ✨ Key Features

- 📸 **Instant multi-image diagnosis:** upload 3–5 plant photos to identify the species and visible symptoms.
- 🌦️ **Weather-aware recommendations:** advice adapts to the live local forecast, not seasonal guesses.
- 🎙️ **Voice-first and simple:** conversational voice interaction (speech-to-text and text-to-speech).
- 🔁 **Continuous conversation:** follow-up questions keep the context of the diagnosis.
- 🗂️ **Session history:** every diagnosis session is stored for history, trends, and improvement.
- 📚 **Knowledge-base grounding:** recommendations draw on agricultural best practices.

---

## 🔄 How It Works: the SUAA Framework

Every interaction follows one consistent loop: **See → Understand → Act → Ask**.

| Step | Stage | What happens |
|:---:|---|---|
| 01 | **SEE** | The farmer captures 3–5 images of the plant through the camera-first interface. |
| 02 | **UNDERSTAND** | The AI engine identifies the species and analyzes visible health symptoms. |
| 03 | **ACT** | Weather and knowledge-base context shape a clear, actionable recommendation. |
| 04 | **ASK** | The farmer follows up by voice, in natural language, for deeper guidance. |

**Pipeline:** `Capture (3–5 images)` → `Analyze (AI fuses visuals + live weather + knowledge base)` → `Respond (actionable advice by voice or text)`

**Example:**

```
Scanning leaf …
Diagnosis:      Early Blight Detected
Confidence:     93%
Recommendation: Spray copper fungicide
Follow-up:      "Ask a follow-up …"
```

---

## 🏗️ System Architecture

Three layers work together: capture, compute, and reason.

```
┌───────────────────────────────────────────────────────────┐
│  EXPERIENCE LAYER: React.js + Tailwind CSS                │
│  Camera capture · Voice UI · Diagnosis & chat screens     │
└───────────────────────────┬───────────────────────────────┘
                            │ REST (JSON)
┌───────────────────────────▼───────────────────────────────┐
│  SERVICE LAYER: Python + FastAPI + MongoDB                │
│  Request handling · Session storage · Orchestration       │
└───────┬───────────────────┬───────────────────┬───────────┘
        │                   │                   │
┌───────▼───────┐   ┌───────▼────────┐   ┌──────▼─────────┐
│ Weather API   │   │ Knowledge Base │   │ INTELLIGENCE   │
│ Live local    │   │ Agricultural   │   │ LAYER          │
│ forecast      │   │ best practices │   │ Gemini + TTS/  │
└───────────────┘   └────────────────┘   │ STT            │
                                         └────────────────┘
```

**Data flow**

1. The farmer's phone sends 3–5 images (and later voice or text) to the FastAPI backend.
2. The backend fetches the live weather and relevant knowledge-base content.
3. Gemini analyzes the images and fuses them with the weather and knowledge context (the *AI reasoning core*).
4. The advice is returned as text or voice.
5. The full session is stored in MongoDB.

---

## 🧰 Tech Stack

| Layer | Technologies | Purpose |
|---|---|---|
| **Frontend** | React.js, Tailwind CSS | Camera capture, voice UI, and results display |
| **Backend** | Python, FastAPI, REST APIs | API layer and orchestration of external services |
| **Database** | MongoDB | Stores every diagnosis session for history and improvement |
| **AI Engine** | Google Gemini (multimodal), TTS / STT | Multi-image analysis, reasoning, and voice |
| **External data** | Weather API, Agricultural Knowledge Base | Live forecast and best-practice context |

**Design choice:** we combine proven AI and API technologies instead of training models from scratch, which keeps the MVP achievable and low-cost.

---

## 📁 Project Structure

> Adjust this to match your actual repository layout.

```
agrivision-ai/
├── frontend/                # React + Tailwind app
│   ├── src/
│   │   ├── components/      # Camera, DiagnosisCard, VoiceChat, History
│   │   ├── pages/
│   │   └── services/        # API client
│   └── package.json
├── backend/                 # FastAPI app
│   ├── app/
│   │   ├── main.py
│   │   ├── routes/          # diagnose, chat, sessions
│   │   ├── services/        # gemini, weather, knowledge_base, speech
│   │   ├── models/          # Pydantic schemas
│   │   └── db.py            # MongoDB connection
│   └── requirements.txt
├── docs/                    # Slides, diagrams, screenshots
├── .env.example
└── README.md
```

---

## 🚀 Getting Started

### Prerequisites

- **Node.js** 18+ and **npm**
- **Python** 3.10+
- A **MongoDB** instance (local or MongoDB Atlas)
- A **Google Gemini API key**
- A **Weather API key**

### 1. Clone the repository

```bash
git clone https://github.com/<your-username>/agrivision-ai.git
cd agrivision-ai
```

### 2. Set up the backend

```bash
cd backend
python -m venv venv
source venv/bin/activate        # Windows: venv\Scripts\activate
pip install -r requirements.txt
cp ../.env.example .env         # then fill in your keys
uvicorn app.main:app --reload
```

The API will be available at `http://localhost:8000`, with interactive docs at `http://localhost:8000/docs`.

### 3. Set up the frontend

```bash
cd frontend
npm install
npm run dev
```

Open the URL printed in the terminal (typically `http://localhost:5173`).

---

## 🔐 Environment Variables

Create a `.env` file in the backend folder (never commit it):

```env
GEMINI_API_KEY=your_gemini_api_key
WEATHER_API_KEY=your_weather_api_key
MONGODB_URI=mongodb://localhost:27017/agrivision
```

---

## 🔌 API Overview

> Endpoint names are a planned design. Update them to match your implementation.

| Method | Endpoint | Description |
|---|---|---|
| `POST` | `/api/diagnose` | Upload 3–5 plant images and location; returns diagnosis and recommendation |
| `POST` | `/api/chat` | Send a follow-up question (text or voice) with a `session_id` |
| `GET` | `/api/sessions/{id}` | Retrieve a single diagnosis session |
| `GET` | `/api/sessions` | List past sessions |

**Example diagnosis response**

```json
{
  "session_id": "abc123",
  "species": "Tomato",
  "condition": "Early Blight",
  "confidence": 0.93,
  "recommendation": "Spray copper fungicide during a dry window. Avoid spraying if rain is forecast within 24 hours."
}
```

---

## ⚔️ How We Compare

| Capability | AgriVision AI | Typical apps |
|---|:---:|:---:|
| Personalized plant diagnosis | ✅ | ❌ |
| Weather-aware recommendations | ✅ | ❌ |
| Voice-first, conversational UX | ✅ | ❌ |
| Built for non-technical users | ✅ | ❌ |

---

## 🗺️ Roadmap

- [ ] **Phase 1: Hackathon MVP.** Build and demo the core AI diagnosis flow with voice interaction.
- [ ] **Phase 2: Pilot with farmers.** Test with real farmers, gather feedback, and refine accuracy.
- [ ] **Phase 3: Scale and localize.** Expand crop coverage and add regional languages nationwide.

---

## 🎯 Impact and Beneficiaries

| Group | Benefit |
|---|---|
| **Farmers** | Instant, expert-level diagnosis and guidance the moment symptoms appear |
| **Agricultural extension officers** | AI helps fill the gap created by a shortage of field advisors |
| **NGOs and government agri programs** | A scalable, low-cost channel to reach farmers |
| **Agri-retailers and cooperatives** | Better-informed farmers make more accurate input purchase decisions |
| **Students and agri-researchers** | Session history builds a growing dataset of real field diagnoses |

---

## 📚 Research and References

The problem and the approach are backed by published research:

- **Smartphone diagnosis works.** A model trained on 54,306 leaf images (14 species, 26 diseases) reached **99.35% accuracy** in published research. This is a result from the cited paper, not a measured accuracy of AgriVision AI.
- **Expert advice doesn't reach everyone.** India's extension worker-to-farmer ratio is about **1 : 5,000** against a recommended **1 : 750**.
- **Informal advice dominates.** Around **95%** of farmers rely on informal advice rather than trained experts.
- **Weather-aware advice changes outcomes.** A randomised trial in Odisha found that weather-responsive digital advisory reduced severe crop loss and raised yields.

**References**

1. Mohanty, Hughes & Salathé (2016). *Using Deep Learning for Image-Based Plant Disease Detection.* Frontiers in Plant Science.
2. NAAS (2025). *Repurposing Agricultural Extension in India.* Policy Note.
3. Cole, Goldberg, Harigaya & Zhu (2025). *Customised agricultural advice at scale.* VoxDev.
4. Anantam IAS (2025). *Importance of Agricultural Extension.*
5. Google AI. *Gemini API Documentation.* https://ai.google.dev

**Acronyms:** SUAA (See, Understand, Act, Ask) · MVP (Minimum Viable Product) · TTS (Text-to-Speech) · STT (Speech-to-Text) · KB (Knowledge Base) · RCT (Randomised Controlled Trial) · UX (User Experience) · API (Application Programming Interface)

---

## ⚠️ Limitations

- AgriVision AI gives **decision support, not a substitute for a qualified agronomist**. For serious or uncertain cases, consult a local agriculture officer.
- Diagnosis quality depends on **photo quality** (lighting, focus, angle).
- Confidence values are the model's own estimate and are **not calibrated probabilities**.
- Always **follow the product label and local regulations** when applying any pesticide or fungicide.
- The MVP covers a limited set of crops and languages. Wider coverage is on the roadmap.

---


---

## 📄 License

This project is licensed under the **MIT License**. See the [LICENSE](LICENSE) file for details.

> Replace this with the license you choose, and add a `LICENSE` file to the repository.

---

<div align="center">

**AgriVision AI turns every smartphone into a personal agronomist.** 🌱

*Team NEXVION · HACKFRONT INDIA*

</div>
