# 📧 Gmail LangGraph Agent — Use Case 1

An intelligent email-processing agent built with **LangGraph** that reads 
unread Gmail messages, extracts travel queries, searches the web, 
and returns AI-generated answers — all at **zero cost**.

---

## Architecture

Gmail API → Email Parser → Query Extractor → Redis Cache Check
↓              ↓
HIT           MISS
↓               ↓
Final Answer  Web Search
↓
Groq LLM
↓
Cache Write
↓
Final Answer


## ⚙️ Tech Stack

| Component | Tool | Cost |
|-----------|------|------|
| Agent Framework | LangGraph | Free |
| LLM | Groq — Llama 3.3 70B | Free tier |
| Email | Gmail API (OAuth2) | Free |
| Search | DuckDuckGo (`ddgs`) | Free |
| Cache | Redis Cloud | Free tier |
| PDF Parsing | pypdf | Free |

## 🚀 Setup

### 1. Clone the repo
```bash
git clone https://github.com/debsubhra/langgraph-agents.git
cd langgraph-agents/use_case_1_gmail_agent
```

### 2. Create virtual environment
```bash
python -m venv myenv
source myenv/bin/activate
pip install -r requirements.txt
```

### 3. Configure credentials
```bash
cp .env.example .env
# Edit .env with your Redis and Groq credentials
```

### 4. Gmail Setup
- Go to [Google Cloud Console](https://console.cloud.google.com)
- Enable Gmail API
- Download `credentials.json` → place in project root
- Add your Gmail to test users in OAuth consent screen

### 5. Run
```bash
jupyter notebook access_gmail.ipynb
```

## 🔑 Environment Variables

| Variable | Description |
|----------|-------------|
| `REDIS_HOST` | Redis Cloud hostname |
| `REDIS_PORT` | Redis Cloud port |
| `REDIS_USERNAME` | Redis username (default) |
| `REDIS_PASSWORD` | Redis password |
| `GROQ_API_KEY` | Groq API key from console.groq.com |

## 📁 Project Structure
use_case_1_gmail_agent/
├── access_gmail.ipynb    # Main notebook
├── requirements.txt      # Dependencies
├── .env.example          # Environment template
├── .gitignore            # Excluded files
└── README.md             # This file

## 👤 Author
**Debsubhra Chakraborty**  
GenAI Developer | LangGraph | LLM Engineer  
[GitHub](https://github.com/debsubhra) · 
[HuggingFace](https://huggingface.co/debsubhra)