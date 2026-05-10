# _claude/log.md — Хронология изменений
# Log — append-only хронология

> Формат: `## [YYYY-MM-DD] <тип> | <заголовок>`
> Типы: ingest | review | schedule | lint | note | skip

---

## [2026-05-09] skip | Нет дневника
## [2026-05-09] note | Инициализация системы

Создана структура `_claude/`: roadmap.md, log.md, index.md, notes.md.
Обновлён CLAUDE.md: актуальная структура vault, исправлены цели (убран Avito).
Проведён первичный аудит vault.

**Найдено:**
- Файлы в корне вне структуры: `Adam (Adaptive Moments).md`, `Newton-Gauss method.md`, `RMSProp 1.md`, `Без названия.md` → требуют перемещения в `resource/machine_learning/`
- `temporary/daily/` — дневник. Один файл: 2026-03-04.md
- `resource/machine_learning/` — 50+ конспектов, хорошее покрытие оптимизаторов и базовых алгоритмов
- `resource/CV/` — 6 файлов, базовое покрытие
- `resource/prob&stats/` — 4 файла, слабое покрытие для ШАД-уровня
- `resource/algorithms/` — 2 файла, критически мало для CP-целей
- Нет конспектов по: Gradient Boosting, Transformer (детально), CNN архитектурам

## [2026-05-09] schedule | Добавлены учебные блоки в Google Calendar (неделя 11–17 мая)

Добавлено X событий. См. детали в чате.

## [2026-05-09] review | sparse-review | ~2-3ч (factual today) + backup-debt | BFS, DFS, heap; backup: GLM/GAM/Newton-Raphson/CV-filtring/decision-tree/MLE-move

Diary отсутствует. Calendar учебных событий не имел. Git: 23+4 файла, 2 коммита.
Реально написано сегодня: BFS, DFS, heap (algorithms).
Остальное — backup апрельских конспектов (GLM, GAM, Newton-Raphson, filtring, decision_tree_heuristic, etc.).
Notes Audit: image_convolution.md пустой; models.md заглушка; filtring.md имеет опечатку в имени и битую дату; decision_tree_heuristic обрывается; стандарт конспектов расходится с CLAUDE.md §5.
См. _claude/review/2026-05-09.md.

## [2026-05-10] skip | Нет дневника
