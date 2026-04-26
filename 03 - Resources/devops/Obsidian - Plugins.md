---
tags: [ferramenta, obsidian, plugins, produtividade]
tema: Obsidian Plugins
fonte: Setup pessoal
data: 2026-04-17
status: concluido
---

# Obsidian — Plugins

## Resumo
> Plugins instalados e configurados no vault rafa-brain para backup automatico, dashboards e integracao com IA.

---

## Plugins instalados

### 1. Git (por Vinzent)
Backup automatico do vault no GitHub.

**Configuracao:**
- Auto commit-and-sync interval: `10` minutos
- Auto commit-and-sync after stopping file edits: ativado
- Pull on startup: ativado
- Push on commit-and-sync: ativado
- Pull on commit-and-sync: ativado
- Commit message: `vault backup: {{date}}`

**Commit manual:**
`Ctrl+P` -> `Git: Commit-and-sync`

---

### 2. Dataview (por Michael Brenan)
Queries tipo SQL nas notas do vault. Usado no `HOME.md` para dashboards dinamicos.

**Exemplo de query:**
```dataview
TABLE status, tecnologias, prazo
FROM "01 - Projects"
WHERE status = "ativo"
SORT file.mtime DESC
```

---

### 3. Copilot (por Logan Yang)
Chat com IA dentro do Obsidian usando API da Anthropic.

**Configuracao:**
- Provider: Anthropic
- Modelo padrao: claude-haiku-4-5
- API Key: console.anthropic.com

**Como usar:**
- `Ctrl+P` -> `Copilot: Open Copilot Chat`
- Com a nota aberta, o Copilot usa o contexto automaticamente
- Usar `@vault` para buscar em todo o vault

---

### 4. Modelos (nativo)
Templates de notas para padronizar criacao de conteudo.

**Configuracao:**
- Pasta de modelos: `05 - Templates`
- Formato de data: `YYYY-MM-DD`
- Formato de hora: `HH:mm`

**Como usar:**
`Ctrl+P` -> `Modelos: Inserir modelo` -> escolhe o template

---

## Templates disponiveis

| Template | Uso |
|---|---|
| Template - Estudo | Notas de aprendizado tecnico |
| Template - Projeto | Projetos ativos |
| Template - Nota Diaria | Log diario de atividades |
| Template - Cliente FinOps | Clientes da e-Core |

---

## Relacionado com
- [[Obsidian - Setup e Configuracao]]
- [[Obsidian - Workflow Diario]]
