- Выбора пал на CIC-IDS 2017 за полноту содержания ( не слишком много не слишком мало ) и общую популярность 
- Необходимо взять только 4 файла из 8, так как только эти файлы содержат данные о Dos DDos и PortScan
	- При необходимости можно расширить датасет, для увеличения количества Normal файлов
## Нормализация датасета. Подгонка под нашу задачу
- Необходимо разделить на 4 категории нашу заготовочку и распределить на 3 папки: train, valid, test
-  Также нужно удалить строчки с большим количеством некорректных данных
## Вычисление зависимостей
- В последствии была найдена [статья](https://habr.com/ru/articles/538296/), которая решает практически похожую задачу на том же датасете, поэтому было принято решение взять ее за пример
- Следую статье необходимо было найти зависимости среди данных, делая это при помощи Random Forest из Sikit Learn
	- Пример вычислений был найден в [статье](https://habr.com/ru/companies/ruvds/articles/488342/)
- После вычислений получили такие данные 
```py
|Features|Gini-Importance|
|---|---|
|0|Packet Length Variance|0.112954|
|1|Average Packet Size|0.077703|
|2|Total Length of Fwd Packets|0.064696|
|3|Avg Fwd Segment Size|0.046902|
|4|Bwd Packet Length Max|0.036607|
|5|Max Packet Length|0.034660|
|6|Init_Win_bytes_forward|0.033985|
|7|Packet Length Mean|0.031431|
|8|Subflow Fwd Bytes|0.030253|
|9|Total Fwd Packets|0.029212|
|10|Bwd Packets/s|0.027708|
|11|Packet Length Std|0.026690|
|12|Flow Packets/s|0.026560|
|13|Idle Max|0.026542|
|14|Avg Bwd Segment Size|0.026005|
|15|act_data_pkt_fwd|0.024998|
|16|Bwd Header Length|0.021947|
|17|Fwd IAT Max|0.020309|
|18|Fwd Packet Length Max|0.020046|
|19|Fwd Packet Length Mean|0.019213|
|20|Flow Bytes/s|0.018354|
```
- Теперь было необходимо вычислять какие из данных стоит оставить для обучения модели на настоящих кейсах
- Постаравшись сузить данные еще больше можно вычислять [[pearson correlation|корреляцию Пирсона]] 
## Вычисление ключевых особенностей
- Были удалены все коррелированные данные
- После чего пошло изучение гистограмм по ключевым фичам
- Ключевые фичи для определения
- **Fwd IAT Max** — Normal vs DoS/DDoS
- **Fwd IAT Mean** — Normal vs DoS/DDoS
- **Flow IAT Std** — Normal vs DoS/DDoS
- **Average Packet Size** _(или Packet Length Mean + Std, но не дублируй)_ — Normal vs DoS/DDoS
- **Avg Bwd Segment Size** — Normal vs DoS/DDoS
- **Flow Duration** — Normal vs DoS _(и часть PortScan)_
- **+ рекомендую добавить:** `Flow Packets/s`, `Fwd Packets/s`, `Bwd Packets/s`/`Total Bwd Packets`, `Down/Up Ratio`, `Bwd Header Length` — они «закроют» PortScan.