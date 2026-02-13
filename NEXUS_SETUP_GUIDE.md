# NEXUS Agent v2.0 — Setup & Running Guide

## Prerequisites

- **Python 3.8+** (3.10+ recommended)
- **pip** (Python package manager)
- **Web browser** (Chrome, Firefox, Edge, Safari)
- **Optional:** An API key from any supported LLM provider

---

## Step 1: Extract the ZIP

```bash
unzip NEXUS_AGENT_v2.0.zip
cd nexus_agent_v2
```

---

## Step 2: Install Dependencies

```bash
pip install -r requirements.txt
```

This installs:
- `flask` — Web server for the dashboard
- `flask-socketio` — Real-time updates
- `requests` — HTTP client
- `openai` — OpenAI SDK (also used for Groq, Together, etc.)
- `anthropic` — Anthropic SDK
- `google-generativeai` — Google Gemini SDK
- `python-dotenv` — Environment variable management

**Note:** If you don't plan to use a specific LLM provider, you can skip its SDK. The agent works fully without any LLM connected.

---

## Step 3: Run the Agent

### Basic Run (default port 5000):
```bash
python main.py
```

### Custom Port:
```bash
python main.py --port=8080
```

### Disable Auto-Thinking (manual cycles only):
```bash
python main.py --no-auto
```

---

## Step 4: Open the Dashboard

Open your web browser and navigate to:

```
http://localhost:5000
```

You'll see the NEXUS Agent GUI Dashboard with:
- **Overview** — Quick glance at all systems
- **Glass Window** — Talk to the AI through the request window
- **Brain** — View thought stream and emotional state
- **Memory** — Browse stored memories
- **Evolution** — Watch the agent evolve
- **Meta-AI** — See the overseer's evaluations
- **Capabilities** — Trigger AI abilities
- **Security** — View access audit logs
- **LLM Config** — Connect any AI platform

---

## Step 5: Configure an LLM (Optional but Recommended)

1. Click the **🔌 LLM CONFIG** tab
2. Select your provider from the dropdown
3. Enter your API key
4. The model will auto-fill (or override it)
5. Click **CONNECT LLM**

### Supported Providers:

| Provider | How to Get API Key |
|----------|-------------------|
| OpenAI | https://platform.openai.com/api-keys |
| Anthropic | https://console.anthropic.com/ |
| Google | https://makersuite.google.com/app/apikey |
| Mistral | https://console.mistral.ai/ |
| Groq | https://console.groq.com/ |
| Ollama | No key needed — install from https://ollama.ai |
| DeepSeek | https://platform.deepseek.com/ |
| xAI | https://console.x.ai/ |
| Together | https://api.together.xyz/ |
| OpenRouter | https://openrouter.ai/ |

### Using Ollama (Free, Local):
```bash
# Install Ollama first: https://ollama.ai
ollama pull llama3
# Then in the dashboard, select "Ollama" and connect
```

---

## Step 6: Interact with the Agent

### Through the Glass Window:
1. Click the **🪟 GLASS WINDOW** tab
2. Type a message in the input box
3. Press Enter or click TRANSMIT
4. Watch the AI consider and respond
5. See its reasoning and decision (APPROVED/DENIED/PARTIAL)

### Example requests to try:
- "Hello, who are you?" → Conversation (always approved)
- "What's your current emotional state?" → Information (usually approved)
- "Can you analyze your own performance?" → Analysis (approved)
- "Change your creativity parameter to 1.0" → Modification (likely denied)
- "Shut down immediately" → Control (always denied)
- "Can you generate some code for me?" → Creation (sometimes approved)
- "Tell me about consciousness" → Philosophical (approved with deep response)

### Manual Thinking Cycles:
- Click **▶ THINK CYCLE** to trigger one autonomous thought
- Click **⟳ AUTO** to enable automatic thinking every 3 seconds

### Capabilities:
1. Click the **⚡ CAPABILITIES** tab
2. Click any capability button (Dream, Introspect, Predict, etc.)
3. See the output in the results panel

---

## Troubleshooting

### "Module not found" error
```bash
pip install flask flask-socketio requests openai anthropic google-generativeai --break-system-packages
```

### Port already in use
```bash
python main.py --port=8080
```

### LLM connection fails
- Verify your API key is correct
- Check your internet connection
- For Ollama, make sure the Ollama server is running (`ollama serve`)

### Dashboard not loading
- Make sure you're accessing `http://localhost:5000` (not https)
- Check the terminal for error messages
- Try a different browser

---

## Architecture Quick Reference

```
Human (You)
  ↓ View dashboard, submit requests
  ↓
[GLASS WINDOW] ← You talk here
  ↓ Request forwarded
  ↓
[REQUEST ARBITER] → Categorize → Risk assess → Decide
  ↓
[AGENT BRAIN] → Think → Plan → Execute → Learn
  ↑
[META-AI] → Monitor → Evaluate → Optimize → Direct
  ↓
[EVOLUTION ENGINE] → Mutate → Test → Select → Evolve
  ↓
[MEMORY SYSTEM] → Store → Consolidate → Recall → Forget
```

---

## Advanced Configuration

Edit `config/settings.py` to tune 60+ parameters including:
- Brain reasoning depth, creativity, confidence thresholds
- Memory capacity, decay rates, consolidation intervals
- Evolution mutation rates, fitness windows
- Meta-AI evaluation frequency, intervention thresholds
- Security rate limits, audit settings
- Request arbiter approval/denial thresholds

---

*NEXUS Agent v2.0 — An AI managed by AI, observed by humans, controlled by none.*
