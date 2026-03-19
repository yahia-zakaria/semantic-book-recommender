# 📚 Semantic Book Recommender

> Discover your next read using natural language. Describe the kind of book you're in the mood for—and optionally filter by genre and emotional tone—to get personalized recommendations powered by semantic search and emotion analysis.

![Python](https://img.shields.io/badge/Python-3.8+-blue.svg)
![Gradio](https://img.shields.io/badge/Gradio-Web%20UI-orange.svg)
![LangChain](https://img.shields.io/badge/LangChain-RAG-green.svg)

---

## ✨ Features

- **Semantic search** — Describe books in your own words (e.g., *"A story about forgiveness"* or *"A thrilling mystery set in Victorian London"*) and get relevant recommendations
- **Category filtering** — Narrow results by genre (Fiction, Nonfiction, Biography, History, etc.)
- **Emotional tone** — Filter by mood: Happy, Surprising, Angry, Suspenseful, or Sad
- **Interactive dashboard** — Clean Gradio UI with book covers and descriptions
- **RAG pipeline** — Uses OpenAI embeddings + Chroma for vector similarity search
- **Emotion-aware** — Book descriptions are scored for joy, sadness, fear, anger, surprise, and more via a fine-tuned DistilRoBERTa model

---

## 🛠 Tech Stack

| Component | Technology |
|-----------|------------|
| Embeddings | OpenAI `text-embedding-3-small` |
| Vector DB | Chroma |
| RAG / LLM | LangChain |
| Emotion model | `j-hartmann/emotion-english-distilroberta-base` |
| UI | Gradio |
| Data | [7k Books with Metadata](https://www.kaggle.com/datasets/dylanjcastillo/7k-books-with-metadata) (Kaggle) |

---

## 📁 Project Structure

```
book-recommender/
├── gradio-dashboard.py      # Main app — Gradio UI + semantic search
├── books_with_emotions.csv  # Processed books with emotion scores
├── books_with_categories.csv
├── books_cleaned.csv
├── tagged_description.txt   # Preprocessed descriptions for vector DB
├── data-exploration.ipynb   # Load & explore Kaggle dataset
├── text-classification.ipynb # Category simplification
├── sentiment-analysis.ipynb  # Emotion scoring pipeline
├── vector-search.ipynb       # Chroma + LangChain setup
└── .env                     # API keys (create from .env.example)
```

---

## 🚀 Quick Start

### Prerequisites

- Python 3.8+
- [OpenAI API key](https://platform.openai.com/api-keys)
- [Kaggle account](https://www.kaggle.com/) (for dataset download)

### 1. Clone & install

```bash
git clone https://github.com/YOUR_USERNAME/semantic-book-recommender.git
cd semantic-book-recommender
pip install -r requirements.txt
```

### 2. Set up environment

Create a `.env` file in the project root:

```env
OPENAI_API_KEY=your_openai_api_key_here
```

### 3. Prepare data (first-time setup)

If you don't have the processed CSVs yet:

1. Run `data-exploration.ipynb` to download the Kaggle dataset and produce `books_cleaned.csv`
2. Run `text-classification.ipynb` to add simplified categories → `books_with_categories.csv`
3. Run `sentiment-analysis.ipynb` to add emotion scores → `books_with_emotions.csv`
4. Run `vector-search.ipynb` to generate `tagged_description.txt` and build the Chroma index

### 4. Launch the app

```bash
python gradio-dashboard.py
```

Open the URL shown in the terminal (default: `http://127.0.0.1:7860`).

---

## 📖 Usage

1. **Enter a description** — e.g., *"A cozy mystery with a small-town detective"*
2. **Choose a category** (optional) — Fiction, Nonfiction, History, etc.
3. **Choose a tone** (optional) — Happy, Suspenseful, Sad, etc.
4. Click **Find recommendations** to see matching books with covers and blurbs.

---

## 📦 Dependencies

Create a `requirements.txt` with:

```
gradio
langchain
langchain-openai
langchain-community
langchain-chroma
chromadb
openai
python-dotenv
pandas
numpy
```

For the notebooks (data pipeline):

```
kagglehub
transformers
torch
tqdm
```

---

## 📜 License

MIT

---

## 🙏 Acknowledgments

- [7k Books with Metadata](https://www.kaggle.com/datasets/dylanjcastillo/7k-books-with-metadata) by Dylan Castillo
- [Emotion English DistilRoBERTa](https://huggingface.co/j-hartmann/emotion-english-distilroberta-base) by Johannes Hartmann
