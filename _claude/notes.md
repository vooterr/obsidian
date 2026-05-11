# Notes — наблюдения Claude

> Здесь фиксирую паттерны, риски, флаги без запроса.
> Обновляется при каждой значимой сессии.

---

## [2026-05-09] Первичный аудит

### Сильные стороны vault
- `resource/machine_learning/` хорошо покрывает оптимизаторы (SGD, Adam, AdaGrad, RMSProp, momentum) и базовые алгоритмы (SVM, kNN, RF, деревья). Это соответствует ШАД-уровню для классических моделей.
- Есть конспекты по SVD, KKT, VC-теории — хорошая математическая база.
- CV раздел покрывает классические фильтры и свёртки.

### Критические пробелы (по приоритетам)

**Приоритет A — ШАД:**
- `resource/prob&stats/` слаб: нет σ-алгебры, условного матожидания, ЗБЧ/ЦПТ. Для ТВ-семинара по четвергам это риск.
- Нет конспекта по выпуклой оптимизации (dual problem, субградиент) — нужен для ШАД.

**Приоритет B — ML/CV:**
- Нет детального Transformer конспекта (есть `language_transformer.md` и `scaled_dot_product_attention.md` — проверить глубину).
- Нет: Gradient Boosting, ResNet/EfficientNet, YOLO, mAP/IoU.

**Приоритет C — CP:**
- `resource/algorithms/` почти пуст (2 файла). Для ICPC-уровня это проблема.

### Структурные замечания
- 4 файла в корне vault вне структуры — требуют перемещения.
- `plan_ml.md` в resource/machine_learning/ описывает старый план (data analyst / Avito). Устарел. Архивировать или удалить.
- `plan on 27.03.md`, `plan_on_07.04.2026.md`, `plan_on_2026_20_03.md` — старые планы, захламляют папку.

### Рекомендации (очередь)
1. Перенести корневые файлы в правильные папки.
2. Сделать конспекты по prob&stats до следующего ТВ-семинара (чт).
3. Создать `resource/algorithms/` структуру для CP.
4. Архивировать старые plan-файлы.

---

## [2026-05-10] TODO из ревью 2026-05-09

### Структурные фиксы (выполнено 2026-05-10)
- ✅ `resource/CV/image_convolution.md` — создан каркас по шаблону, содержание — TODO Vildan'а.
- ✅ `resource/CV/filtring.md` → `filtering.md`, дата `2026-13-04` → `2026-04-13`, добавлены связи.
- ✅ `resource/machine_learning/decision_tree_heuristic.md` — опечатки исправлены, `## Ускорение` помечена `<!-- TODO -->`.
- ✅ `resource/algorithms/Без названия.md` — удалён.
- ✅ `resource/CV/image_.md` — удалён (пустой, имя-обрубок).
- ✅ `resource/CV/models.md` — содержимое перенесено сюда (см. ниже), файл удалён.

### Темы для CV-конспектов (из бывшего models.md)
- FCOS — anchor-free детектор
- RepNet — повторяющиеся действия в видео (или RepVGG?)
- WQuatNet — **уточнить**: возможно опечатка от `WaveNet` или `QuatNet` (кватернионные сети)
- MobileNet — лёгкие сети для мобильных устройств

### Содержательные пробелы (требуют контента от Vildan'а)
- `resource/machine_learning/decision_tree_heuristic.md` — раздел `## Ускорение` пустой. См. TODO-комментарий в файле.
- `resource/CV/image_convolution.md` — каркас создан, основное содержание пусто. См. TODO в файле.
- `resource/prob&stats/MLE.md` — `## 📝 Основное содержание` пуст, материал есть только в `## Определение`. **Старый MLE.md содержал precision/recall** — этот материал, по всей видимости, мигрировал в `resource/metrics/precision_recall_auc.md` (проверено: там есть Precision/Recall, ROC-AUC).

### Несогласованность шаблона
- 🔁 **CLAUDE.md §5** требует секции `Выжимка / Формулы / Примеры / Связанные`, но фактически все новые ML-конспекты используют `📝 Основное содержание / ✅ Задачи / 🔗 Связи`. Решить с Vildan'ом, какой формат канонический, и обновить либо CLAUDE.md, либо template/.

### Битые/непроверенные ссылки
- `[[splines]]` (упомянут в GAM.md) — файла нет.
- `[[Newton-Gauss method]]` — был в корне vault, проверить миграцию.
- `[[L-BFGS]]`, `[[IRLS]]`, `[[Метод Холецкого]]` — упоминаются в Newton-Raphson, проверить наличие.

### Систематика
- 📌 Backup-долг по git: апрельские конспекты впервые попали в индекс только 2026-05-09. Если коммитить раз в месяц — git перестаёт быть валидным сигналом для daily-review. Рекомендовать ежедневные backup-коммиты (можно через cron).
- 📌 Calendar 2026-05-09 не содержал учебных блоков, но фактически работа велась. Проверить ту же ситуацию за 2026-05-07 / 2026-05-08 — если паттерн (3+ дня), то Calendar нужно перестроить.

---

## [2026-05-10] TODO из ревью 2026-05-10

### Критические фактические ошибки (срочный приоритет — материал ШАД/собеседование)
- ❌ `resource/CV/filtering.md` (Gaussian blur): формула `G(x,y) = (1/2πσ²) · exp((x²+y²)/(2σ²))` — **отсутствует знак минус** в экспоненте. Правильно: `exp(-(x²+y²)/(2σ²))`.
- ❌ `resource/CV/filtering.md` (Bilateral): `G_{σs}(x,y) = exp((-||x-y||)/(2σs))` — отсутствует **квадрат нормы** и **квадрат σ_s**, лишняя скобка. Правильно: `exp(-||x-y||²/(2σ_s²))`.
- ❌ `resource/CV/filtering.md` (Sobel): `Gx = I · Kx` — обозначено умножением вместо свёртки. Должно быть `G_x = I * K_x` или `I ⊗ K_x`.
- ❌ `resource/CV/image_presentation.md` (Grayscale): "Rec. 609" — **не существует**. Должно быть **Rec. 601** (ITU-R BT.601, коэффициенты 0.299/0.587/0.114). Это распространённая опечатка, критичная на ШАД-собеседовании.
- ❌ `resource/CV/image_presentation.md` (HSV, формула H): "Если $H = (H + 360) \mod 360$" — пропущено условие "если H < 0".
- 📝 `resource/CV/image_presentation.md`: раздел HSL обрывается строкой "**HSL** -", без определения.
- ❌ `resource/algorithms/DFS.md`: классификация рёбер: Tree edge и Back edge записаны с одинаковым условием `color[v] == 0`. Правильно: Tree edge → color[v]==0 (белый); Back edge → color[v]==1 (серый, в стеке рекурсии).
- 🏷️ `resource/algorithms/DFS.md`: "узел j является дочерним к j" — должно быть "к i"; "colo[v]" — опечатка `colo` без `r`.
- ❌ `resource/machine_learning/Newton-Gauss method.md`: запись псевдообратной "$J^+ = (J^\top J)^{-1} J^\top$" приведена в контексте "когда $J^\top J$ вырождена". Противоречие: при вырождении $(J^\top J)^{-1}$ не существует. Эта запись корректна **только при полном ранге столбцов**.

### Блокирующие пустоты
- 📝 `resource/CV/image_convolution.md` — каркас, "📝 Основное содержание" пуст. На него ссылается filtering.md для Sobel/Gaussian. **Без определения свёртки CV-цепочка повисает.**
- 📝 `resource/CV/image-smapling.md`, `image-quantisation.md`, `image_presentation.md` — раздел "📝 Основное содержание" пуст у всех.

### Структурные фиксы (vault hygiene)
- 🏷️ **Опечатка в имени файла**: `resource/CV/image-smapling.md` → переименовать в `image-sampling.md`. Обновить wikilinks в `filtering.md`, `image_convolution.md` (используют `[[image-smapling|...]]`).
- 🏷️ `resource/machine_learning/Newton-Gauss method.md` — имя с пробелом. Унифицировать (всюду в vault либо `Name with spaces.md`, либо snake_case).
- 🔀 Терминология "Дискретизация" (в файле image-smapling.md) vs "Сэмплирование" (label в wikilinks из filtering.md). Принять один термин.
- 📝 `resource/algorithms/DFS.md`, `heap.md`, `quick_sort.md`: секция "🔗 Связи" — пустые (только дефис). Минимум: DFS↔BFS, heap→priority_queue, quick_sort→другие сортировки.
- 🏷️ `resource/algorithms/quick_sort.md`: "Lamuto" → каноническое "Lomuto" (Nico Lomuto).

### Систематика
- 🔁 **Diary не заполнен 2 дня подряд** (2026-05-09, 2026-05-10). Если 11 мая снова — добавить напоминание (Calendar-событие 21:55 "diary").
- 🔁 **Calendar 3 дня подряд (08–10 мая) не содержит учебных блоков**, при этом фактическая работа была. OP-2: перестроить Calendar под реальный ритм Vildan'а вместо фиктивных слотов.
- 🔁 Опечатки в именах файлов (`filtring`, `image-smapling`, пробелы) — рекомендую pre-commit hook на проверку kebab-case + словарь технических терминов.

### Содержательные пробелы (требуют контента от Vildan'а)
- `image-interpolation.md`: нет Lanczos/Mitchell-Netravali/spline-методов; нет явных систем уравнений для Bilinear/Cubic.
- `image-quantisation.md`: нет uniform/non-uniform формул, JPEG quantisation tables, vector quantization.
- `image_presentation.md`: нет CMYK, sRGB vs linear (γ-коррекция).
- `image-smapling.md`: нет теоремы Котельникова, aliasing, anti-aliasing prefilter (перед ТВ-семинаром в чт обязательно).
- `decision_tree_heuristic.md`: раздел "## Ускорение" пуст (продолжение с 2026-05-09).
- `quick_sort.md`: Hoar partition не реализован (TODO стоит).
