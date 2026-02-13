#HOME #HomePage #H 

---
# TODO
```dataview
TABLE status, deadline, priority
FROM ""
WHERE status = "TODO"
SORT deadline ASC,
  choice(priority = "high", 1, 
         choice(priority = "middle", 2, 
                choice(priority = "low", 3, 99))) ASC
```
# In-progress
```dataview
TABLE status, date, deadline, priority
FROM ""
WHERE status = "in-progress"
SORT deadline ASC,
  choice(priority = "high", 1, 
         choice(priority = "middle", 2, 
                choice(priority = "low", 3, 99))) ASC
```

# Задачи
```dataview
TASK
FROM "temporary/daily"
WHERE type = "daily" AND day <= date(today)
WHERE !complited
GROUP BY day
```
## Global plan
[[plan_ml|План]]