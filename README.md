# Openclaw Agent Worker

A production-safe MVP for Railway + long-running worker + agent.

## ✅ Features

- ✅ Deploy successfully on Railway
- ✅ Container stays alive (long-running worker)
- ✅ Agent + tools + memory ready
- ✅ Easy to extend with RAG later
- ✅ No need to fork any official repo

## 📁 Repository Structure

```
agent-worker/
├── main.py           # FastAPI server (long-running worker)
├── crew.py           # Agent + Tools + Memory
├── Dockerfile        # Railway-compatible container
├── requirements.txt  # Python dependencies
└── README.md         # This file
```

## 🚀 Quick Start

### Prerequisites

- Python 3.11+
- Docker (for Railway deployment)
- API keys for OpenAI and SerperDev

### Local Development

1. Install dependencies:
```bash
pip install -r requirements.txt
```

2. Set environment variables:
```bash
export OPENAI_API_KEY=your_key
export SERPER_API_KEY=your_key
```

3. Run the server:
```bash
uvicorn main:app --reload
```

4. Test the health endpoint:
```bash
curl http://localhost:8000/health
```

5. Run the agent:
```bash
curl -X POST http://localhost:8000/run
```

## 🐳 Railway Deployment

1. Push this repo to GitHub
2. Connect your repo to Railway
3. Set environment variables in Railway dashboard:
   - `OPENAI_API_KEY`
   - `SERPER_API_KEY`
4. Deploy! Railway will automatically use the Dockerfile

## 📦 Dependencies

- **fastapi** - Web framework
- **uvicorn** - ASGI server (keeps container alive)
- **crewai** - Agent framework
- **crewai-tools** - Built-in tools
- **chromadb** - Vector database (for RAG)
- **python-dotenv** - Environment management
- **openai** - LLM provider

## 🔄 Memory & Tools

✅ Tools enabled (SerperDev for web search)
✅ Memory enabled for agent context
✅ RAG-ready (chromadb vector DB included)

## 🛠️ Extending

### Add More Agents

Edit `crew.py` to add new agents:
```python
new_agent = Agent(
    role="Your Role",
    goal="Your goal",
    backstory="Your backstory",
    tools=[your_tools],
    verbose=True,
)
```

### Add Custom Tools

```python
from crewai_tools import tool

@tool
def my_custom_tool(input_string):
    """Tool description"""
    return "Tool result"
```

## 📝 License

MIT