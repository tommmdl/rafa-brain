---
tags: [estudo, machine-learning, rag, llm, aws]
tema: RAG
fonte: AWS Docs, Anthropic, LangChain
data: 2026-04-17
status: em-andamento
---

# 📚 RAG — Retrieval-Augmented Generation

## 💡 Resumo
> RAG é uma técnica que combina recuperação de documentos relevantes com geração de texto por LLMs, permitindo que o modelo responda com base em conhecimento externo atualizado — sem precisar retreinar o modelo.

---

## 🧠 Como funciona
[Pergunta do usuário]
↓
[Embedding da pergunta]
↓
[Busca vetorial no banco de dados]
↓
[Recupera chunks relevantes]
↓
[Monta prompt: contexto + pergunta]
↓
[LLM gera resposta fundamentada]
### Os 3 componentes principais
- **Retriever** — busca os documentos mais relevantes (ex: OpenSearch, FAISS, Pinecone)
- **Embeddings** — transforma texto em vetores numéricos (ex: Titan Embeddings V2)
- **Generator** — o LLM que gera a resposta (ex: Claude 3 Haiku, GPT-4)

---

## 🔑 Conceitos-chave

### Embedding
Representação numérica (vetor) de um texto.
Textos semanticamente similares ficam próximos no espaço vetorial.

### Chunking
Divisão dos documentos em pedaços menores antes de indexar.
- Chunk muito grande → contexto irrelevante
- Chunk muito pequeno → perde contexto
- Tamanho ideal: 256~512 tokens com overlap de ~50 tokens

### Vector Store
Banco de dados otimizado pra busca por similaridade vetorial.
- AWS: **OpenSearch** com k-NN
- Open source: FAISS, Chroma, Weaviate
- Managed: Pinecone, Qdrant

### Similarity Search
Busca por cosseno ou produto interno entre vetores.
Retorna os K chunks mais próximos da query (k-NN).

---

## ☁️ RAG na AWS

| Componente | Serviço AWS |
|---|---|
| Embeddings | Bedrock — Titan Embeddings V2 |
| Vector Store | OpenSearch Serverless |
| LLM | Bedrock — Claude 3 Haiku |
| Orquestração | Lambda |
| API | API Gateway |
| Managed RAG | Bedrock Knowledge Bases |

---

## ⚡ RAG vs Fine-tuning

| | RAG | Fine-tuning |
|---|---|---|
| Custo | Baixo | Alto |
| Atualização | Tempo real | Retreinamento |
| Conhecimento | Externo (docs) | Interno (pesos) |
| Quando usar | Dados dinâmicos | Estilo/comportamento |

---

## 🔗 Relacionado com
- [[rag-mlops-aws]]
- [[AWS Bedrock]]
- [[OpenSearch]]
- [[MLOps fundamentals]]

---

## ❓ Dúvidas para pesquisar depois
- [ ] Qual a diferença entre RAG naïve e RAG avançado (HyDE, reranking)?
- [ ] Como avaliar qualidade de um pipeline RAG? (RAGAS)
- [ ] Bedrock Knowledge Bases vale mais que RAG customizado?

---

## 📎 Referências
- [AWS Bedrock RAG Docs](https://docs.aws.amazon.com/bedrock/)
- [Anthropic — Building with Claude](https://docs.anthropic.com)
- Projeto: [[rag-mlops-aws]]
