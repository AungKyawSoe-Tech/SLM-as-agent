# Running GPT-OSS-20b SLM locally!

## Introduction

I want to use a SLM, **GPT-OSS-20b** from OpenAI so that when I use VS Code. How can I use this locally stored pre-trained LLM instead of GitHub CoPilot?


## Create files and folders

We can run a local **20 B GPT‑OSS** model (or any LLM that runs on your machine) and hook it into VS Code instead of using cloud‑based GitHub Copilot.

The trick is to expose the model as an API that looks like OpenAI’s endpoint, then point a VS Code extension at that local endpoint. Below are two practical ways to do this:

1.  Run the model with a lightweight local inference engine (e.g., Ollama, vLLM, or Hugging‑Face Inference Server).
2.  Create/modify an existing VS Code extension so it talks to your local server.




| Option |  What you need |  Typical RAM / GPU |  Pros | Cons |
|----------|--------------------|--------------|-------|------|
**Ollama**  | ~12 GB VRAM (or 40 GB+ if you want low‑latency) |  Zero‑config, auto‑downloads models, supports  `chat/completions`. |  Not as fast as a fully custom vLLM deployment. |

## Install Olama and use the model

curl -fsSL https://ollama.ai/install.sh | sh

Test whether Olama is running by following command:

http://localhost:11434

ollama pull gpt-oss:20b

ollama serve

curl -X POST http://localhost:11434/api/chat/completions \
  -H "Content-Type: application/json" \
  -d '{
    "model": "gpt-oss:20b",
    "messages": [{"role":"user","content":"Explain recursion in Python."}]
  }'

## Workflow diagrams

Render UML diagrams using [Mermaid](https://mermaidjs.github.io/). For example, sequence diagram below will show workflow:

```mermaid
sequenceDiagram
Copilot->> Curl: Prompt
Curl-->>Olama:  curl -X POST http://localhost:11434/api/chat/completions \ -H "Content-Type: application/json" \ -d '{ "model": "gpt-oss-20b", "messages": [{"role":"user","content":"Explain recursion in Python."}] }'
GPT-OSS-20b--x Copilot:  GPT response to prompt "recursion in Python"

Note left of Olama: You should see a JSON response that looks just like OpenAI’s API.
