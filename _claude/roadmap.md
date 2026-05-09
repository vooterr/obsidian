# Learning Roadmap — Vildan

> Актуально: 2026-05-09 | Следующее ревью: воскресенье

---

## Горизонт и цели

| Цель | Срок | Статус |
|------|------|--------|
| Успешно пройти ШАД | Текущий момент → | 🔴 Активно |
| ML + CV навыки уровня junior/mid | 12–18 мес | 🟡 В процессе |
| Магистратура ETH Zürich / UZH | ~2029 | 🟢 Долгосрок |

**Нет в целях:** Avito, data analyst трек, A/B тесты как цель.

---

## Приоритет A — ШАД (выжить и вырасти)

**Логика:** ШАД — это и есть подготовка к ETH. Строгая математика + ML на уровне реализации — именно это смотрят в топ-магистратурах.

### Математика (ШАД core)
- [ ] Линейная алгебра: SVD, PCA, псевдообратная, проекции
- [ ] Матанализ: градиент, Гессиан, теорема Лагранжа, МНК
- [ ] Теория вероятностей: σ-алгебра, условное матожидание, ЗБЧ, ЦПТ
- [ ] Математическая статистика: MLE/MAP, критерии, доверительные интервалы
- [ ] Оптимизация: выпуклая оптимизация, KKT, двойственность

### ML теория (ШАД уровень)
- [x] Linear/Logistic regression (MLE, Gauss-Markov)
- [x] SVM, kernel trick, KKT
- [x] Ensemble methods, Random Forest
- [ ] Gradient Boosting: functional gradient descent
- [ ] Bayesian ML: prior/posterior, GP
- [ ] PAC-learning, VC-dimension

---

## Приоритет B — ML / CV для работы

**Логика:** Портфолио + понимание архитектур до уровня "реализую и объясню на интервью".

### Computer Vision
- [x] Классические фильтры (Gaussian, Sobel, Canny, Bilateral, Laplacian)
- [x] Свёртки, нормализация (BatchNorm, LayerNorm, GroupNorm)
- [ ] CNN: ResNet, EfficientNet, ViT
- [ ] Object Detection: YOLO, DETR, Faster R-CNN
- [ ] Segmentation: Mask R-CNN, SAM
- [ ] Evaluation: mAP, IoU, COCO metrics
- [ ] GradCAM, интерпретируемость

### Deep Learning
- [x] Backpropagation, chain rule
- [x] SGD, Adam, RMSProp, AdaGrad, AdamW
- [ ] Dropout, L1/L2, early stopping
- [ ] Архитектуры: MLP → CNN → RNN → Transformer
- [ ] Attention: multi-head, cross-attention, self-attention
- [ ] Transformer: encoder-decoder, positional encoding

### LLM / GenAI
- [ ] Transformer архитектура изнутри
- [ ] Fine-tuning: LoRA, QLoRA, PEFT
- [ ] Diffusion models: DDPM, score matching
- [ ] Multimodal: CLIP, BLIP, LLaVA

### Frameworks
- [x] PyTorch: базовый уровень
- [ ] PyTorch: custom layers, hooks, distributed
- [ ] HuggingFace: Trainer, datasets, tokenizers
- [ ] OpenCV для CV pipeline

---

## Приоритет C — Алгоритмы / CP

**Логика:** ICPC — сильный сигнал для ETH admission. Поддерживать форму.

- [ ] 2–3 задачи/нед (Codeforces Div2 C–D, Div1 A–B)
- [ ] Графы: Dijkstra, BFS/DFS, MST, топ-сорт
- [ ] DP: knapsack, bitmask, interval
- [ ] Структуры: segment tree, BIT, DSU
- [ ] Строки: KMP, Z-функция, суффиксный массив

---

## Приоритет D — ETH Application

**Логика:** ETH требует проектов, не только знаний.

### Портфолио (к 2028)
- [ ] CV проект: emotion recognition / medical imaging (GitHub + readme)
- [ ] ML pipeline от данных до деплоя
- [ ] Kaggle: топ-% в одном соревновании
- [ ] Соавторство или лабораторный опыт

### Академические требования
- [ ] GPA ≥ 8.0 (ШАД + HSE)
- [ ] Английский C1+ (в процессе)
- [ ] SOP черновик — за 1.5 года до подачи (к 2027-03)

---

## Недельный бюджет

| Приоритет | Ч/нед |
|-----------|--------|
| A: ШАД математика | 8–10 ч |
| B: ML/CV практика | 8–10 ч |
| C: CP | 2–3 ч |
| D: ETH проекты | 3–5 ч |
| Университет (ТВ + право) | 2 ч |
| **Итого** | **23–30 ч** |

---

## Milestones

| Дата | Milestone |
|------|-----------|
| 2026-09 | ШАД: первый семестр без долгов |
| 2026-12 | CV: объектный детектор (пет-проект) |
| 2027-06 | ML/CV junior: готов к работе |
| 2027-09 | Поиск работы в ML/CV |
| 2028-01 | Черновик SOP для ETH |
| 2028-09 | Подача в ETH/UZH |
| 2029    | Начало магистратуры |

---

_Обновляется каждое воскресенье._
_Последнее обновление: 2026-05-09_
