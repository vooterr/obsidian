{{date:YYYY-MM-DD}} {{time:HH:mm}} 
---
#### Результаты недели


___
#### ✔Выполненные задачи 
```dataview 
TASK FROM "Periodic/Daily" 
WHERE completed
WHERE file.cday >= date("___") - dur(6 day) AND file.cday <= date("___")
GROUP BY file.link 
``` 
