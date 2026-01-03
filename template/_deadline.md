---
status: <% tp.system.suggester(
  ["TODO", "in-progress", "DONE", "archived"], 
  ["TODO", "in-progress", "DONE", "archived"]
) %>
date: <% tp.date.now("YYYY-MM-DD") %>
priority:  <% tp.system.suggester(
  ["low", "medium", "high"],
  ["low", "medium", "high"]
) %>
deadline: <% tp.system.prompt("Дедлайн (YYYY-MM-DD или пусто)", "") %>
tags: []
---

# <% tp.file.title %>

## 📌 Кратко
- 

## 📝 Основное содержание


## ✅ Задачи
- [ ] 

## 🔗 Связи
- 
<% tp.cursor %>