---
tags: [ferramenta, obsidian, produtividade, setup]
tema: Obsidian
fonte: Setup pessoal
data: 2026-04-17
status: concluido
---

# Obsidian — Setup e Configuracao

## Resumo
> Obsidian e um editor de notas baseado em Markdown que armazena tudo localmente. Usado como segundo cerebro para consolidar conhecimento de estudos, projetos e trabalho.

---

## Instalacao

- Download: https://obsidian.md
- Versao instalada: 1.7.7
- Instalador: `Obsidian-1.7.7.exe`
- Tipo: App desktop Windows

---

## Vault

- Nome: `rafa-brain`
- Caminho: `C:\Users\rafael.santiago\Documents\Obsidian\rafa-brain`
- Repositorio GitHub: https://github.com/tommmdl/rafa-brain (privado)

---

## Estrutura PARA

Metodologia de organizacao de conhecimento:

```
rafa-brain/
├── 00 - Inbox/          # Dump rapido, processa depois
├── 01 - Projects/       # Projetos ativos com prazo/objetivo
│   ├── rag-mlops-aws/
│   ├── finops-portal/
│   ├── taro-luminar/
│   └── encora-interview/
├── 02 - Areas/          # Responsabilidades continuas
│   ├── e-Core/
│   ├── carreira/
│   ├── financas/
│   └── saude/
├── 03 - Resources/      # Conhecimento de referencia
│   ├── machine-learning/
│   ├── mlops/
│   ├── aws/
│   ├── devops/
│   ├── finops/
│   ├── python/
│   └── ingles/
├── 04 - Archives/       # Projetos concluidos
│   ├── cbmm/
│   └── bit-pagg/
└── 05 - Templates/      # Templates de notas
```

---

## Comandos de inicializacao Git

```bash
cd /mnt/c/Users/rafael.santiago/Documents/Obsidian/rafa-brain

git init
git remote add origin git@github.com:tommmdl/rafa-brain.git

echo ".obsidian/workspace.json" >> .gitignore
echo ".obsidian/workspace-mobile.json" >> .gitignore
echo ".obsidian/plugins/" >> .gitignore
echo ".obsidian/cache" >> .gitignore

git add .
git commit -m "feat: init rafa-brain vault"
git branch -M main
git push -u origin main
```

---

## Relacionado com
- [[Obsidian - Plugins]]
- [[Obsidian - Workflow Diario]]

---

## Referencias
- https://obsidian.md
- https://github.com/tommmdl/rafa-brain
