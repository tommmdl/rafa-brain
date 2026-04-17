# 🧠 rafa-brain

> Segundo cérebro do Rafa — Cloud & MLOps Engineer

---

## 🚀 Projetos ativos

```dataview
TABLE status, tecnologias, prazo
FROM "01 - Projects"
WHERE status = "ativo"
SORT file.mtime DESC
```

---

## 📚 Estudos em andamento

```dataview
TABLE tema, fonte, status
FROM "03 - Resources"
WHERE status = "em-andamento"
SORT file.mtime DESC
```

---

## ✅ Tarefas pendentes

```dataview
TASK
FROM "01 - Projects" OR "02 - Areas"
WHERE !completed
SORT file.mtime DESC
```

---

## 📝 Notas recentes

```dataview
TABLE file.mtime AS "Modificado"
FROM ""
WHERE file.name != "HOME"
SORT file.mtime DESC
LIMIT 10
```

---

## 📅 Notas diárias recentes

```dataview
TABLE file.mtime AS "Data"
FROM "00 - Inbox"
SORT file.mtime DESC
LIMIT 7
```
