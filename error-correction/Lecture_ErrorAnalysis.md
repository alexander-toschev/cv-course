
# 🧠 Лекция: Анализ и работа над ошибками нейросети

## 🎯 Цель лекции
Научиться интерпретировать метрики качества модели, понимать ошибки, выявлять bias и variance, и строить план улучшения модели.

---

## 1. 🧠 Bayes Error и Avoidable Bias

### ❓ Что такое Bayes Error

**Bayes Error** — это теоретически минимально возможная ошибка классификации, которую можно достичь, даже если бы у нас был идеальный классификатор. Она обусловлена **неустранимым шумом** в данных.

#### 💡 Аналогия:
Представь, ты смотришь на размытое изображение и не можешь точно сказать — это "кот" или "собака". Даже эксперт иногда ошибётся. Это и есть **Bayes Error**.

### 📐 Как можно оценить Bayes Error?

1. **Оценка по человеку**: ошибка человека ≈ Bayes Error
2. **Повторная разметка**: используем разногласия разметчиков
3. **Simulated noise**: шумим данные и смотрим минимальную ошибку
4. **Confidence Calibration**: уверенность модели vs ошибки

### Формула общей ошибки:

```
Общая ошибка = Bayes Error + Avoidable Bias + Variance + Data Mismatch
```

### Таблица:

| Компонент ошибки     | Значение                            | Решение                                |
|----------------------|-------------------------------------|-----------------------------------------|
| **Bayes Error**      | Неустранимый шум                    | Никак — принять как факт                |
| **Avoidable Bias**   | Модель слабовата                    | Лучшая архитектура, больше данных       |
| **Variance**         | Переобучение                        | Регуляризация, больше данных            |
| **Data Mismatch**    | dev/test распределения разные       | Domain adaptation, выравнивание данных  |

---

## 2. 📈 Performance Analysis: Bias vs Variance

### Метрики анализа:

- Train error vs Bayes error → Bias
- Dev error vs Train error → Variance
- Test error vs Dev error → Data mismatch

### Пример:

| Метрика         | Значение | Комментарий         |
|-----------------|----------|---------------------|
| Ошибка человека | 1%       | ≈ Bayes Error       |
| Ошибка train    | 5%       | Высокий Bias        |
| Ошибка dev      | 8%       | Variance            |
| Ошибка test     | 9%       | Data mismatch       |

### Выводы:

- Высокий Bias → улучшить модель, данные
- Высокая Variance → регуляризация
- Data mismatch → выравнивание доменов

---

## 3. 📊 Интерпретация Train / Dev / Test / Human

- Модель vs Человек
- Train vs Dev (обобщаемость)
- Dev vs Test (устойчивость)
- Ошибки по классам, категориям

### График обучения (словами):
Train - низкая ошибка, Dev - выше, Test - ещё выше = проблема в generalization и mismatch

---

## 4. 🧩 Confusion Matrix

### Что это:

Таблица, показывающая сколько реальных примеров каждого класса были отнесены к какому предсказанному классу.

### Пример для 2 классов:

|               | Предсказано: Кошка | Предсказано: Собака |
|---------------|--------------------|----------------------|
| Было: Кошка   | TP                 | FN                   |
| Было: Собака  | FP                 | TN                   |

- **TP**: True Positive
- **FP**: False Positive
- **FN**: False Negative
- **TN**: True Negative

### Метрики:

- Accuracy = (TP + TN) / Total
- Precision = TP / (TP + FP)
- Recall = TP / (TP + FN)
- F1 = 2 * (P * R) / (P + R)

### Пример кода:

```python
from sklearn.metrics import confusion_matrix, ConfusionMatrixDisplay

y_true = ['cat', 'dog', 'cat', 'fox']
y_pred = ['cat', 'cat', 'cat', 'fox']

cm = confusion_matrix(y_true, y_pred, labels=['cat', 'dog', 'fox'])
disp = ConfusionMatrixDisplay(confusion_matrix=cm, display_labels=['cat', 'dog', 'fox'])
disp.plot()
```

---

## 🧪 Практика

1. У вас есть модель с ошибкой: train = 5%, dev = 8%, test = 9%, ошибка человека = 1%. Найдите: bias, variance, mismatch.
2. Постройте confusion matrix, найдите слабые классы.
3. Придумайте 2 улучшения.

---

## 🏁 Домашнее задание

1. Получите confusion matrix вашей модели
2. Найдите тип ошибки (bias/variance/mismatch)
3. Предложите улучшения

