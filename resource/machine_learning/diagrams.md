---
status: in-progress
date: 2026-02-21
priority: medium
deadline: 2026-02-22
tags: []
---

# diagrams

## 📝 Основное содержание


## ✅ Задачи

## 🔗 Связи
- 
## Одномерный анализ
### Исчисляемые признаки
#### Гистограмма
- С помощью нее можно узнать распределение данных (Guassian, exponential, etc.)
- ![../../_images/58bd2389ddae4b6025aa07ea9d72a69790fbeaee4eb1f9964900206372b42352.svg](https://mlcourse.ai/_images/58bd2389ddae4b6025aa07ea9d72a69790fbeaee4eb1f9964900206372b42352.svg)
- Используется как метод для pandas.DataFrame
- **Пример**:
	  ```
	features = ["Total day minutes", "Total intl calls"]
	df[features].hist(figsize=(10, 4));
	  ```
- Собирает данные в группы по банкам (bins)
#### Density plot
- Используется также для определения распределения данных, но является более сглаженной версией ядра
- ![../../_images/93a6637f95a2e5752556c6597d58e0998fb36699a08cb048238d95969b83893b.svg](https://mlcourse.ai/_images/93a6637f95a2e5752556c6597d58e0998fb36699a08cb048238d95969b83893b.svg)
- 
#### KDE (Kernal density estimate)
- Является как добавочным свойством, с оценкой плотности ядра, 
- ![../../_images/91bd1bb9f7f256d0e4a75b1319fc5b9e5dd42cd4d99ee381847d617374ab70cd.svg](https://mlcourse.ai/_images/91bd1bb9f7f256d0e4a75b1319fc5b9e5dd42cd4d99ee381847d617374ab70cd.svg)
- **Пример:**
```py
  sns.histplot(df["Total intl calls"], kde=True, stat="density");
```
- Здесь высота гистограммы нормированная и показывает плотность а не количество каждого показателя
#### Box plot
- Показывает распределение данных в рамках теории вероятности
- Используется для определения выбросов и рассмотрения медианных и других значений данных 
- ![../../_images/c4a91fba4b12d448dd14f4ec7af069cf79bfe2759e10ac0c75c5a351be2c632e.svg](https://mlcourse.ai/_images/c4a91fba4b12d448dd14f4ec7af069cf79bfe2759e10ac0c75c5a351be2c632e.svg)
- [![Box plot](https://cdn1.byjus.com/wp-content/uploads/2020/10/Box-Plot-and-Whisker-Plot-2.png)
- **Пример**:
	- `sns.boxplot(x="Total intl calls", data=df);`
- *Более сложный пример:*
```py
top_platforms = df.Platform.value_counts().sort_values(ascending = False).head(5).index.values
sns.boxplot(y="Platform", x="Critic_Score", data=df[df.Platform.isin(top_platforms)], orient="h"
```
#### Violin plot
- Тот же самый boxplot только при это теперь показывает распределение данных по своей площади
- ![../../_images/3b08eeb72e9c950cac9a3c57d1a906f7d329f9b38627c2df2b5482ff1c706842.svg](https://mlcourse.ai/_images/3b08eeb72e9c950cac9a3c57d1a906f7d329f9b38627c2df2b5482ff1c706842.svg)
- **Пример**
	  `sns.violinplot(data=df["Total intl calls"])`
### Категориальные и бинарные признаки
#### Bar plot
- Показывает распределение категорий в признаках
- ![../../_images/369ff8ec3619ede0cf5ca93c37f215a1f353f4552f502ce302a4bf73b6862102.svg](https://mlcourse.ai/_images/369ff8ec3619ede0cf5ca93c37f215a1f353f4552f502ce302a4bf73b6862102.svg)
- Похож чем то на гистограмму, но имеет другие свойства
- Он показывает количество объектов принадлежащих той или иной категории
- **Пример:**
	- `sns.countplot(x="Churn", data=df)`
## Многомерные графики
### Численные и численные
#### Матрица корреляции
- Используется только для численных признаков
- *Показывает корреляцию между признаками*
	- Если корреляция высокая, то цвет будет ярче и наоборот
- ![../../_images/42c9429fe8edd07352c78deaa413a16eb8a9d70e1823c0c66afa761aa70a0cf4.svg](https://mlcourse.ai/_images/42c9429fe8edd07352c78deaa413a16eb8a9d70e1823c0c66afa761aa70a0cf4.svg)
- **Пример:**
```py
corr_matrix = df[numerical].corr()
sns.heatmap(corr_matrix);
```
#### Scatter plot 
  - Используется для *нахождения зависимостей между двумя признаками*
  - На диаграмме рассеяния значения двух числовых переменных отображаются в виде декартовых координат в двумерном пространстве.
  - Также *возможны диаграммы рассеяния в трехмерном пространстве*.
  - ![../../_images/74db51dfcb0ab6af357666cae41bc00a9992bd6e982f81f4d2c4ba5198888781.svg](https://mlcourse.ai/_images/74db51dfcb0ab6af357666cae41bc00a9992bd6e982f81f4d2c4ba5198888781.svg)
  - **Пример:**
	  - `plt.scatter(df["Total day minutes"], df["Total night minutes"]);`
  - Можно найти зависимости, например линейных экспоненциальных или данные собираются вместе в одну область
#### Join plot
- Тот же самый scatter plot, только теперь добавляется еще и *распределение данных по каждому признаку* по гистограммам
- ![../../_images/8ece6f1afb6673bc18445d0de8739fa27a3f80c8eaffb4f4961076966949c83d.svg](https://mlcourse.ai/_images/8ece6f1afb6673bc18445d0de8739fa27a3f80c8eaffb4f4961076966949c83d.svg)
- **Пример:**
`sns.jointplot(x="Total day minutes", y="Total night minutes", data=df, kind="scatter");`
- Также можно использовать *KDE* в joint plot, чтобы получить *сглаженную версию*
- ![../../_images/8626cf938df379593cb9720f6680de81f68ebb8b9e1627d0a225331f80d5c01b.svg](https://mlcourse.ai/_images/8626cf938df379593cb9720f6680de81f68ebb8b9e1627d0a225331f80d5c01b.svg)
##### Scatterplot matrix
- Это уже большая диаграмма, которая строит scatter plot каждого признака с каждым
- ![../../_images/45ae6d2f67d0dbbf61718730587ea5930a39db27fb305c2bbbf91b9b01363233.png](https://mlcourse.ai/_images/45ae6d2f67d0dbbf61718730587ea5930a39db27fb305c2bbbf91b9b01363233.png)
- **Пример:**
	- `sns.pairplot(df[numerical]);`
### Численные с категориальными
#### Lmplot
- График, который можно использовать для определения распределения категориальных признаков в двух численных 
- ![../../_images/c1a6e33d7dbd866c6d3bffc57dc5680aaa527da5d768f83442ec329c12839126.svg](https://mlcourse.ai/_images/c1a6e33d7dbd866c6d3bffc57dc5680aaa527da5d768f83442ec329c12839126.svg)
- **Пример:**
```
sns.lmplot(
    x="Total day minutes", y="Total night minutes", data=df, hue="Churn", fit_reg=False
);
```
- Используется параметр hue для категориального признака
#### Box plot
- Используется как обычный box plot
	- Но теперь есть еще разграничение по категориям (как по оси x)
- ![../../_images/68f7bf2eb3a99b4b326349e538ffe99617d1d8a03b62cdcf7a06edbfce7b804b.svg](https://mlcourse.ai/_images/68f7bf2eb3a99b4b326349e538ffe99617d1d8a03b62cdcf7a06edbfce7b804b.svg)
### Категоричный и категоричный
#### Bar plot
- Используется для определения количества уже по двум категориальным признакам
- ![../../_images/0495c1f180944f3f493599528b875186e49b946741a495b8f90641309dc5a3d9.svg](https://mlcourse.ai/_images/0495c1f180944f3f493599528b875186e49b946741a495b8f90641309dc5a3d9.svg)
- По параметру `hue` можно добавить новый признак
- **Пример:**
- `sns.countplot(x="Customer service calls", hue="Churn", data=df);`
- 