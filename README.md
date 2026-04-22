# VectorDB-CPP — Custom Vector Database with RAG (C++)

A hands-on implementation of a **Vector Database built from scratch in C++**, designed to understand how modern semantic search systems actually work internally.

This project combines **multiple search algorithms (HNSW, KD-Tree, Brute Force)** with a **Retrieval-Augmented Generation (RAG)** pipeline powered by a local LLM using Ollama.

---

## 🚀 Why I Built This

Most developers use tools like Pinecone or Weaviate without understanding what happens behind the scenes.
I built this project to explore:

* How high-dimensional vector search works
* Why HNSW is used in production systems
* How embeddings + retrieval + LLMs form a complete RAG pipeline

---

## ✨ Key Features

* 🔍 **Multiple Search Algorithms**

  * HNSW (fast, scalable)
  * KD-Tree (exact search)
  * Brute Force (baseline comparison)

* 📏 **Distance Metrics**

  * Cosine Similarity
  * Euclidean Distance
  * Manhattan Distance

* 📊 **Visualization**

  * 2D PCA scatter plot to visualize semantic clustering

* 🧠 **Real Embeddings**

  * Uses `nomic-embed-text` via Ollama (768D vectors)

* 🤖 **RAG Pipeline**

  * Ask questions on your own documents
  * Retrieves relevant chunks using HNSW
  * Generates answers using a local LLM

* 🌐 **REST API**

  * Insert, delete, search, benchmark
  * Document ingestion + question answering

---

## 🧠 System Flow

```
User Input (Text)
      ↓
Embedding (Ollama)
      ↓
Vector Representation (768D)
      ↓
HNSW / KD-Tree Search
      ↓
Top-K Similar Results
      ↓
LLM (Ollama - llama3.2)
      ↓
Final Answer (RAG)
```

---

## 🛠️ Tech Stack

* **C++ (Core Engine)**
* **HNSW / KD-Tree / Brute Force Algorithms**
* **Ollama (Local LLM + Embeddings)**
* **cpp-httplib (HTTP Server)**
* **HTML + JS (Frontend UI)**

---

## ⚙️ Setup (Windows)

### 1. Install Dependencies

* MSYS2 (for g++)
* Git
* Ollama

### 2. Install Compiler

```bash
pacman -S mingw-w64-ucrt-x86_64-gcc
```

### 3. Install Models

```bash
ollama pull nomic-embed-text
ollama pull llama3.2
```

---

## ▶️ Run the Project

```bash
g++ -std=c++17 -O2 main.cpp -o db -lws2_32
./db
```

Open in browser:

```
http://localhost:8080
```

---

## 🧪 How to Use

### 🔍 Search

Try queries like:

* "binary tree"
* "pizza"
* "football"

Compare algorithms and see how results differ.

---

### 📄 Add Documents

* Paste any text (notes, articles)
* System converts into embeddings
* Stored in vector index

---

### 🤖 Ask AI (RAG)

* Ask questions based on inserted documents
* System retrieves relevant chunks
* LLM generates contextual answers

---

## 📁 Project Structure

```
VectorDB-CPP/
├── main.cpp
├── httplib.h
├── index.html
└── README.md
```

---

## ⚡ Key Learnings

* HNSW enables near O(log N) search in high dimensions
* KD-Tree struggles with high-dimensional data
* Vector search + LLM = powerful AI systems
* RAG improves accuracy by grounding responses in real data

---

## ⚠️ Common Issues

* Ollama not running → `ollama serve`
* Port 8080 busy → kill process
* Slow responses → use smaller model (`llama3.2:1b`)

---

## 📌 Future Improvements

* User authentication
* Persistent storage (disk-based index)
* React frontend
* Deployment (cloud + Docker)

---

