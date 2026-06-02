# Build-a-Complete-Medical-Chatbot-with-LLMs-LangChain-Pinecone-Flask-AWS

A RAG-based medical chatbot powered by **Google Gemini**, LangChain, Pinecone, and Flask. Ask medical questions and get concise, context-aware answers grounded in the medical book knowledge base.

## Tech Stack

| Component | Technology |
|-----------|------------|
| LLM | Google Gemini 1.5 Flash (`langchain-google-genai`) |
| Embeddings | HuggingFace `sentence-transformers/all-MiniLM-L6-v2` |
| Vector Store | Pinecone |
| Framework | LangChain (RAG chain) |
| Web App | Flask |
| Knowledge Base | Medical_book.pdf |

## Setup

### 1. Clone & install

```bash
git clone <this-repo>
cd Build-a-Complete-Medical-Chatbot-with-LLMs-LangChain-Pinecone-Flask-AWS
pip install -r requirements.txt
```

### 2. Configure environment variables

Copy `.env.example` to `.env` and fill in your keys:

```bash
cp .env.example .env
```

```
PINECONE_API_KEY=your_pinecone_api_key
GOOGLE_API_KEY=your_google_api_key    # from https://aistudio.google.com/apikey
```

### 3. Create the Pinecone index & ingest data

Run this **once** to load the PDF, split it into chunks, embed them, and store in Pinecone:

```bash
python store_index.py
```

This creates a Pinecone index named `medical-chatbot` with 384-dimension cosine vectors.

### 4. Run the app

```bash
python app.py
```

Open `http://localhost:8080` in your browser.

## Project Structure

```
├── app.py              # Flask app + RAG chain (Gemini LLM)
├── store_index.py      # One-time PDF ingestion → Pinecone
├── src/
│   ├── helper.py       # PDF loader, text splitter, HuggingFace embeddings
│   └── prompt.py       # System prompt for the medical assistant
├── data/
│   └── Medical_book.pdf
├── templates/
│   └── chat.html
├── static/
│   └── style.css
├── requirements.txt
└── .env.example
```

## Getting a Google API Key

1. Go to [Google AI Studio](https://aistudio.google.com/apikey)
2. Click **Create API key**
3. Copy the key into your `.env` as `GOOGLE_API_KEY`

The free tier of Gemini 1.5 Flash is sufficient for development and testing.
