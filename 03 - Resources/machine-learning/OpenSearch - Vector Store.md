---
tags: [estudo, machine-learning, opensearch, vector-store, aws]
tema: OpenSearch
fonte: AWS Docs, OpenSearch Docs
data: 2026-04-17
status: em-andamento
---

# OpenSearch — Vector Store

## Resumo
> OpenSearch é um motor de busca e analytics open source (fork do Elasticsearch) usado como vector store no contexto de RAG. Na AWS, disponivel como servico gerenciado (Amazon OpenSearch Service) e serverless.

---

## Como funciona como Vector Store
[Documento indexado]
|
[Embedding gerado (ex: Titan V2)]
|
[Armazenado como campo knn_vector no indice]
|
[Query chega como vetor]
|
[k-NN search retorna os K vizinhos mais proximos]
|
[Chunks retornados como contexto pro LLM]
---

## Conceitos-chave

### k-NN (k-Nearest Neighbors)
Algoritmo de busca por similaridade vetorial.
Retorna os K vetores mais proximos do vetor de query.
OpenSearch suporta 3 engines: `nmslib`, `faiss`, `lucene`.

### Indice com knn_vector
Campo especial no mapping do indice que armazena vetores.
```json
{
  "mappings": {
    "properties": {
      "embedding": {
        "type": "knn_vector",
        "dimension": 1536
      }
    }
  }
}
```

### Dimensao do vetor
Depende do modelo de embedding usado.
- Titan Embeddings V2: 1024 dimensoes
- OpenAI text-embedding-3-small: 1536 dimensoes

---

## OpenSearch na AWS

| Modalidade | Uso ideal | Free tier |
|---|---|---|
| OpenSearch Service | Producao, controle total | t3.small.search |
| OpenSearch Serverless | Escala automatica, sem gerenciar | Nao tem |

No projeto `rag-mlops-aws` usamos **t3.small** dentro do free tier.

---

## Configuracao tipica no projeto RAG

```python
from opensearchpy import OpenSearch

client = OpenSearch(
    hosts=[{"host": OPENSEARCH_ENDPOINT, "port": 443}],
    http_auth=awsauth,
    use_ssl=True,
    verify_certs=True
)

# Busca k-NN
query = {
    "size": 5,
    "query": {
        "knn": {
            "embedding": {
                "vector": query_embedding,
                "k": 5
            }
        }
    }
}

response = client.search(index="rag-index", body=query)
```

---

## OpenSearch vs alternativas

| | OpenSearch | Pinecone | FAISS | Chroma |
|---|---|---|---|---|
| Managed AWS | Sim | Nao | Nao | Nao |
| Free tier | t3.small | Sim (limitado) | Local only | Local only |
| Producao | Sim | Sim | Nao | Nao |
| Integracao Bedrock | Nativa | Via Lambda | Via Lambda | Via Lambda |

---

## Relacionado com
- [[RAG - Retrieval-Augmented Generation]]
- [[AWS Bedrock]]
- [[rag-mlops-aws]]

---

## Duvidas para pesquisar depois
- [ ] Qual a diferenca entre nmslib, faiss e lucene engine no k-NN?
- [ ] Como funciona o OpenSearch Serverless com Bedrock Knowledge Bases?
- [ ] Como monitorar performance do indice k-NN?

---

## Referencias
- [Amazon OpenSearch Service Docs](https://docs.aws.amazon.com/opensearch-service/)
- [k-NN plugin OpenSearch](https://opensearch.org/docs/latest/search-plugins/knn/)
- Projeto: [[rag-mlops-aws]]
