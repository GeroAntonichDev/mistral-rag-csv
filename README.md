# Mistral RAG CSV

Agente RAG (Retrieval-Augmented Generation) con LangChain + Mistral AI para analizar datasets CSV en Google Colab.

## Descripción

Este notebook te permite:
1. **Subir un archivo CSV**
2. **Normalizarlo** (encoding, nulos, duplicados, nombres de columnas)
3. **Indexarlo** en ChromaDB con embeddings de `all-MiniLM-L6-v2`
4. **Consultarlo** en lenguaje natural usando Mistral AI (`open-mistral-7b`)

## Requisitos

1. Cuenta en [Mistral AI](https://console.mistral.ai) para obtener una API Key
2. Google Colab

## Uso

1. Abre el notebook en [Google Colab](https://colab.research.google.com)
2. Configura tu API Key en Secrets (🔑) con nombre `mistralcollab`
3. Ejecuta las celdas en orden
4. Sube tu CSV cuando se te solicite
5. Haz preguntas sobre los datos

## Stack

- **LLM:** Mistral AI (`open-mistral-7b`)
- **Embeddings:** `sentence-transformers/all-MiniLM-L6-v2`
- **Vector store:** ChromaDB
- **Framework:** LangChain + LangGraph
