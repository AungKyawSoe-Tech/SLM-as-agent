\# RAG 



\## Following steps are needed for configuring RAG



python3 -m venv venv312; source venv312/bin/activate;

pip install langchain\_community;

pip install langchain\_experimental;

pip install streamlit;

pip install pdfplumber;

pip install sentence-transformers;

pip install "-U" langchain-huggingface;

pip install faiss-cpu;



\## Populating with data



Populate the folder \\\\wsl.localhost\\Ubuntu\\home\\user\\Documents with books, while the cloned repo is here \\\\wsl.localhost\\Ubuntu\\home\\user\\SLM-as-agent, run as "python3 rag/train.py"



\## Reference



\[Reference](https://apidog.com/blog/rag-deepseek-r1-ollama/)





