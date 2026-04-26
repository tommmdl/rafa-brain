---
tags: [estudo, aws, bedrock, llm, machine-learning, genai]
tema: AWS Bedrock
fonte: AWS Docs
data: 2026-04-17
status: em-andamento
---

# AWS Bedrock

## Resumo
> Amazon Bedrock e um servico gerenciado da AWS que oferece acesso a modelos fundacionais (FMs) de diversos provedores via API unificada, sem necessidade de gerenciar infraestrutura de ML.

---

## O que oferece

- Acesso a FMs via API (Claude, Titan, Llama, Mistral, Cohere)
- Bedrock Knowledge Bases (RAG gerenciado)
- Bedrock Agents (agentes autonomos)
- Fine-tuning de modelos
- Model evaluation
- Guardrails (seguranca e compliance)

---

## Modelos disponiveis

| Provedor | Modelos | Uso ideal |
|---|---|---|
| Anthropic | Claude 3 Haiku, Sonnet, Opus | Chat, RAG, agents |
| Amazon | Titan Text, Titan Embeddings V2 | Embeddings, geracao |
| Meta | Llama 3 | Open source, fine-tuning |
| Mistral | Mistral 7B, Mixtral | Custo-beneficio |
| Cohere | Command, Embed | Embeddings, reranking |

---

## Modelos usados no rag-mlops-aws

| Funcao | Modelo | Motivo |
|---|---|---|
| Embeddings | Titan Embeddings V2 | Nativo AWS, 1024 dimensoes |
| Geracao | Claude 3 Haiku | Custo-beneficio, rapido |

---

## Como chamar via Python (Boto3)

```python
import boto3
import json

bedrock = boto3.client("bedrock-runtime", region_name="us-east-1")

# Geracao de texto — Claude 3 Haiku
response = bedrock.invoke_model(
    modelId="anthropic.claude-3-haiku-20240307-v1:0",
    body=json.dumps({
        "anthropic_version": "bedrock-2023-05-31",
        "max_tokens": 1000,
        "messages": [
            {"role": "user", "content": "Explique RAG em 3 linhas."}
        ]
    })
)

result = json.loads(response["body"].read())
print(result["content"][0]["text"])
```

```python
# Geracao de embeddings — Titan Embeddings V2
response = bedrock.invoke_model(
    modelId="amazon.titan-embed-text-v2:0",
    body=json.dumps({
        "inputText": "O que e RAG?",
        "dimensions": 1024,
        "normalize": True
    })
)

result = json.loads(response["body"].read())
embedding = result["embedding"]  # lista de 1024 floats
```

---

## Bedrock Knowledge Bases vs RAG customizado

| | Knowledge Bases | RAG customizado |
|---|---|---|
| Configuracao | Console AWS, sem codigo | Lambda + OpenSearch + Bedrock |
| Flexibilidade | Baixa | Alta |
| Custo | Maior (serverless OpenSearch) | Controlavel (t3.small) |
| Controle do pipeline | Nenhum | Total |
| Quando usar | POC rapido, time sem ML | Producao, requisitos especificos |

No `rag-mlops-aws` usamos RAG customizado para ter controle total do pipeline.

---

## IAM permissions necessarias

```json
{
  "Effect": "Allow",
  "Action": [
    "bedrock:InvokeModel",
    "bedrock:ListFoundationModels"
  ],
  "Resource": "*"
}
```

---

## Relacionado com
- [[RAG - Retrieval-Augmented Generation]]
- [[OpenSearch - Vector Store]]
- [[rag-mlops-aws]]

---

## Duvidas para pesquisar depois
- [ ] Como funciona o Bedrock Agents na pratica?
- [ ] Bedrock Guardrails — como configurar filtros de conteudo?
- [ ] Fine-tuning no Bedrock vs SageMaker — quando usar cada um?

---

## Referencias
- https://docs.aws.amazon.com/bedrock/
- https://docs.aws.amazon.com/bedrock/latest/userguide/titan-embedding-models.html
- Projeto: [[rag-mlops-aws]]
