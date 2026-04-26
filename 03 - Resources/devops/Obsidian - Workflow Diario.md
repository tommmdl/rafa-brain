---
tags: [ferramenta, obsidian, workflow, produtividade]
tema: Obsidian Workflow
fonte: Setup pessoal
data: 2026-04-17
status: em-andamento
---

# Obsidian — Workflow Diario

## Resumo
> Fluxo de uso do vault rafa-brain para consolidar conhecimento de forma consistente e organizada.

---

## Fluxo principal

```
Capturou algo rapido
        |
    00 - Inbox
        |
   Processou depois
        |
   +-----------+----------+
   |           |          |
Estudo      Projeto    Trabalho
03-Resources 01-Projects 02-Areas
```

---

## Quando usar cada pasta

| Situacao | Pasta | Template |
|---|---|---|
| Aprendeu algo novo | `03 - Resources` | Template - Estudo |
| Iniciou projeto | `01 - Projects` | Template - Projeto |
| Reuniao ou cliente | `02 - Areas/e-Core` | Template - Cliente FinOps |
| Ideia rapida | `00 - Inbox` | Nenhum |
| Reflexao do dia | `00 - Inbox` | Template - Nota Diaria |
| Projeto encerrado | `04 - Archives` | — |

---

## Atalhos essenciais

| Acao | Atalho |
|---|---|
| Paleta de comandos | `Ctrl+P` |
| Inserir template | `Ctrl+P` -> Modelos: Inserir modelo |
| Copilot Chat | `Ctrl+P` -> Copilot: Open Copilot Chat |
| Commit manual Git | `Ctrl+P` -> Git: Commit-and-sync |
| Graph View | `Ctrl+P` -> Graph: Abrir visualizacao em grafico |
| Nova nota | `Ctrl+N` |
| Busca global | `Ctrl+Shift+F` |

---

## Links entre notas

Sempre linkar notas relacionadas usando `[[nome da nota]]`.
Quanto mais links, mais rico fica o Graph View.

Exemplo em uma nota de estudo:
```
- Relacionado com: [[RAG - Retrieval-Augmented Generation]]
- Projeto: [[rag-mlops-aws]]
- Servico AWS: [[AWS Bedrock]]
```

---

## Dashboard central

Abre `HOME.md` para ver:
- Projetos ativos
- Estudos em andamento
- Tarefas pendentes
- Notas recentes

---

## Relacionado com
- [[Obsidian - Setup e Configuracao]]
- [[Obsidian - Plugins]]
