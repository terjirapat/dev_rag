# 🧠 RAG Project

Retrieval-Augmented Generation (RAG) system that combines **Large Language Models (LLMs)** with a **vector database** to provide accurate, context-aware answers using private or domain-specific knowledge.

---

## 🎯 Objective

The goal of this project is to enable **knowledge-grounded responses** from an LLM by connecting it with your own documents or datasets.  
Instead of relying purely on the model’s internal memory, RAG allows the model to:
- Retrieve relevant information from external sources.
- Generate answers grounded in that information.
- Reduce hallucinations and improve factual accuracy.

Typical use cases:
- Company internal knowledge assistant  
- Legal, medical, or financial document Q&A  
- Academic research summarization  
- Product support chatbot  

---

## 🔁 RAG Flow

Below is the step-by-step flow of how the RAG pipeline works:

1. **Document Ingestion**
   - Raw data (PDFs, text files, web pages, etc.) are loaded.
   - Text is split into manageable chunks.
   - Each chunk is embedded into a numerical vector using an embedding model (`nomic-embed-text`).
   - These vectors are stored in a **vector database** (Chroma).

2. **Query Embedding**
   - A user asks a question.
   - The query is embedded into the same vector space as the documents.

3. **Similarity Search**
   - The vector database retrieves the top-N most similar document chunks.
   - These retrieved chunks form the **context** for the LLM.

4. **Contextual Prompting**
   - The retrieved text and the user’s question are combined into a single prompt.
   - Example system prompt:
     ```
     Answer the following question using ONLY the provided context.
     If the answer cannot be found in the context, say "I don't know".
     ```

5. **Answer Generation**
   - The LLM (e.g., Llama 3, Mistral, GPT, or Gemma) generates a grounded response using the provided context.

---

## ⚙️ Project Structure

