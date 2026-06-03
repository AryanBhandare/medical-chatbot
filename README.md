# Medical Chatbot

A RAG-based medical chatbot powered by Google Gemini, LangChain, Pinecone, and Flask.

## Tech Stack

- **LLM** - Google Gemini 2.5 Flash
- **Embeddings** - HuggingFace `all-MiniLM-L6-v2`
- **Vector Store** - Pinecone
- **Web App** - Flask
- **CI/CD** - GitHub Actions + AWS ECR + EC2

## Setup

```bash
git clone <this-repo>
pip install -r requirements.txt
cp .env.example .env  # add your keys
python store_index.py # run once
python app.py
```

Open `http://localhost:8080`

## Environment Variables

```
PINECONE_API_KEY=your_pinecone_key
GOOGLE_API_KEY=your_google_key
```
