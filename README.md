# 🤖 AI Prompt Generator

An internal Streamlit tool built by **SSA & Company** to generate structured AI adoption training prompts for enterprise practitioners. Supports multiple AI agents across 16 industry verticals and exports fully formatted Word documents using official SSA templates.

---

## 📋 Overview

The AI Prompt Generator helps AI adoption teams quickly create two types of practitioner training exercises:

- **Daily Prompts (`DP##`)** — Practical, skill-building exercises grounded in real industry workflows
- **Friday Fun Prompts (`FP##`)** — Engaging, playful exercises that spark curiosity about AI capabilities

Each generated prompt includes a full AI prompt, team email message, learning objective, demonstrated AI capability, example test response, and an optional AI-generated sample attachment file — all exported as formatted `.docx` files using official SSA & Company Word templates.

---

## ✨ Features

| Feature | Detail |
|---|---|
| **Multi-agent support** | Claude AI, ChatGPT, GitHub Copilot, Gemini |
| **16 industry verticals** | See full list below |
| **Prompt types** | Daily only, Friday only, or both |
| **Daily prompts** | Up to 31 per run |
| **Friday Fun prompts** | Up to 5 per run |
| **Smart batching** | Prompts generated in batches of 3 to prevent API token limit errors |
| **Difficulty levels** | Beginner, Intermediate, Advanced, Mixed |
| **Custom topic instructions** | Optional free-text field to guide topics and focus areas |
| **Sample attachments** | AI generates realistic sample files (reports, forms, data) for exercises that require input documents |
| **Word export** | Each prompt fills the official SSA Daily or Friday `.docx` template |
| **Individual download** | Download any single prompt as a `.docx` |
| **Bulk ZIP download** | Download all prompts and attachments in one `.zip` file |
| **Restricted access** | Work email domain authentication |
| **Persistent domain management** | SSA admins can add/remove authorized partner domains — saved permanently to file |

---

## 🗂️ Project Structure

```
Digital-Prompts-Generator/
├── app.py                           # Main Streamlit application
├── requirements.txt                 # Python dependencies
├── README.md                        # This file
├── data_storage/
│   └── authorized_domains.json     # Persistent authorized email domains
└── templates/
    ├── Daily_Prompt_Template.docx   # Word template for Daily Prompts
    └── Friday_Prompt_Template.docx  # Word template for Friday Fun Prompts
```

---

## 🚀 Getting Started

### Prerequisites

- Python 3.10+
- pip

### Installation

```bash
# Clone the repository
git clone https://github.com/okerdeniz/Digital-Prompts-Generator.git
cd Digital-Prompts-Generator

# Create and activate a virtual environment
python -m venv .venv
.venv\Scripts\activate        # Windows
source .venv/bin/activate     # macOS / Linux

# Install dependencies
pip install -r requirements.txt
```

### Running Locally

```bash
streamlit run app.py
```

The app opens at `http://localhost:8501`.

---

## 🔑 API Keys

Each AI agent requires its own API key, entered at runtime in the sidebar. Keys are **never stored**.

| Agent | Key Format | Where to Get It |
|---|---|---|
| Claude AI | `sk-ant-...` | [console.anthropic.com](https://console.anthropic.com) |
| ChatGPT | `sk-proj-...` | [platform.openai.com](https://platform.openai.com) |
| Gemini | `AIza...` | [aistudio.google.com](https://aistudio.google.com) |
| GitHub Copilot | `ghp_...` or `github_pat_...` | GitHub → Settings → Developer Settings → Personal Access Tokens (enable `copilot` scope) |

---

## 🏭 Supported Industries

Industry-Agnostic · Healthcare · Finance & Banking · Legal · Technology · Manufacturing · Retail & E-Commerce · Education · Government & Public Sector · Real Estate · Consulting & Professional Services · Marketing & Advertising · Logistics & Supply Chain · Insurance · Energy & Utilities · Non-Profit

---

## ⚙️ Configuration Options

All settings are in the sidebar:

| Setting | Options |
|---|---|
| **AI Agent** | Claude AI, GitHub Copilot, ChatGPT, Gemini |
| **API Key** | Entered per session, never saved |
| **Industry** | 16 options |
| **Prompt Type** | Daily Prompts Only · Friday Fun Prompts Only · Both |
| **Number of Daily Prompts** | 1–31 |
| **Number of Friday Fun Prompts** | 1–5 |
| **Topic Instructions** | Optional free-text guidance (focus areas, audience, tone) |
| **Difficulty Level** | Beginner · Intermediate · Advanced · Mixed |

---

## 🔐 Access Control

Access is restricted to **SSA & Company employees and authorized partner organizations**.

- Users sign in with their **work email address**
- The `@ssaandco.com` domain is always authorized and cannot be removed
- SSA admins (`@ssaandco.com` users) see a **🔑 Access Management** panel in the sidebar to add or remove partner domains
- Domain changes are **saved permanently** to `data_storage/authorized_domains.json` and survive app restarts

---

## 📄 Output Format

### Prompt Document Fields

Each generated prompt contains the following fields, mapped into the Word template:

| Field | Description |
|---|---|
| **Prompt ID** | Sequential ID, e.g. `DP01`, `DP02`, `FP01` |
| **AI Prompt** | The exercise prompt to run in the selected AI tool |
| **E-Mail Message** | Ready-to-send team communication contextualising the exercise |
| **Learning Objective** | What practitioners will learn from the exercise |
| **Demonstrated AI Capability** | e.g. Summarization, Data Analysis, Draft Generation |
| **Test Response** | Realistic example AI output, rendered with native markdown formatting |
| **Attachment** | Description of required sample file, or "None required" |

### File Naming Convention

```
DP01 - Prompt Topic - Data Analysis.docx          ← Prompt document
DP01 - Sample Attachment - Q3 Claims Report.docx   ← Standalone sample file
```

### ZIP Download Structure

```
AI_Prompts_Claude_AI_Insurance_20250224_143022.zip
├── DP01 - Prompt Topic - Data Analysis.docx
├── DP01 - Sample Attachment - Q3 Claims Report.docx
├── DP02 - Prompt Topic - Draft Generation.docx
├── DP03 - Prompt Topic - Research.docx
└── FP01 - Prompt Topic - Creative Brainstorming.docx
```

---

## ☁️ Deployment (Streamlit Cloud)

The app is deployed on **Streamlit Community Cloud** connected to this GitHub repository.

To deploy updates, push to the `main` branch:

```bash
git add .
git commit -m "Describe your change"
git push
```

Streamlit Cloud detects the push and redeploys automatically within ~1 minute.

---

## 📦 Dependencies

```
streamlit>=1.35.0
python-docx>=1.1.0
anthropic>=0.25.0
openai>=1.30.0
google-generativeai>=0.5.0
python-dotenv>=1.0.0
```

Install with:

```bash
pip install -r requirements.txt
```

---

## 📬 Contact & Access Requests

This tool is restricted to SSA & Company employees and authorized partners.  
For access requests or technical issues, contact your **SSA & Company representative**.
