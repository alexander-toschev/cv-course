# Лекция 09 · Цели проекта и метрики / Project Goals and Metrics

Установка целей проекта и Human-level performance. / Project goals and human-level performance.

## Материалы / Materials

- [Презентации и видео RU/EN / Slides and videos](https://drive.google.com/drive/folders/1I5QcwDqJ3WXhSC2duCKGleIbI3Ja3LS8).
- [Практика / Practice](Practice_RU_EN.ipynb) · [Colab](https://colab.research.google.com/github/alexander-toschev/cv-course/blob/main/Lectures/09_ProjectGoals_Metrics/Practice_RU_EN.ipynb).
- [ДЗ 09 / Homework 09](Homework_RU_EN.ipynb) · [Colab](https://colab.research.google.com/github/alexander-toschev/cv-course/blob/main/Lectures/09_ProjectGoals_Metrics/Homework_RU_EN.ipynb).

Четыре подробных задания практики по 5–10 минут: confusion matrix, precision/recall/F1, выбор порога, анализ ошибок по классам. Каждый блок содержит пример и исполняемую проверку. Выполненные преподавательские ответы с комментариями RU/EN каждой непустой строки хранятся только в закрытом Google Drive.

Four detailed 5–10 minute practice exercises cover confusion counts, precision/recall/F1, threshold selection and class-level error analysis. Each block includes an example and executable checks. Executed instructor solutions with RU/EN comments on every nonempty code line remain in private Google Drive.

## Данные / Data

[Официальный CIFAR-10 / Official CIFAR-10](https://www.cs.toronto.edu/~kriz/cifar.html), Alex Krizhevsky. Наблюдение — реальное RGB-изображение 32×32. Классы: cat=0; dog/frog=1. Это учебная задача распознавания животных, не датасет модерации контента. / Each observation is a real 32×32 RGB image; cat=0, dog/frog=1. This is an animal classification exercise, not a content moderation dataset.

Из официального train берём первые 1000 фотографий каждого класса, stratified seed909: train2250/validation750. Из официального test — первые 200 каждого класса (600). Изображения преобразуются в 192 средних интенсивности блоков 4×4. Scaler и LogisticRegression обучаются только на train. Порог выбирается только по validation; при равенстве выбираем больший порог. Test не участвует в выборе. Загружается официальный архив (~163MiB), проверяется MD5. Источник описывает условия использования и происхождение изображений; собственную лицензию на фотографии мы не заявляем.

Select the first 1,000 official training images per class and stratify with seed909 into 2,250 train and 750 validation images. Use the first 200 official test images per class (600). Features are 192 spatial block means. Fit scaling and logistic regression only on train; select thresholds only on validation, breaking ties toward the larger threshold. Test never selects the rule. The official ~163MiB archive is MD5-verified. Consult the dataset source for usage and provenance; no new image license is claimed here.

Ограничения: маленькие изображения, искусственная пропорция классов, неизвестные группы источников, возможные близкие дубликаты. Это учебная подвыборка, не полный benchmark. / Limitations: low resolution, deliberately selected class balance, unavailable source groups and possible near-duplicates. This is a teaching subset, not the full benchmark.

## ДЗ и проверка / Homework and grading

MET-09: 100 исходных баллов, пять групп проверок (20+20+25+20+15). Реализуются confusion_counts, binary_metrics, choose_threshold, slice_errors. Подробные контракты в ноутбуке. Отчёт включает выбор порогов, сравнение с константой, цену ошибок, срезы, четыре реальные ошибочные фотографии и протокол оценки человеком. Автоматические тесты оценивают функции; отчёт требует содержательного разбора преподавателем.

MET-09: 100 raw points across five check groups (20+20+25+20+15). Implement confusion_counts, binary_metrics, choose_threshold and slice_errors using the notebook contracts. The report covers thresholds, a constant baseline, error costs, slices, four real error images and a human evaluation protocol. Automated tests assess functions; the instructor reviews the report.

[Матрица сроков / Deadline matrix](https://docs.google.com/spreadsheets/d/15N5GGHujXPAzRNuyOfmooT7A7sKhXgrMfWHkUkvYYiM/edit): сроки J, практика09 K на листе «Практика». Даты вводит преподаватель. / Deadline column J; practice09 column K on the practice sheet. The instructor enters dates.

Итог / Final: `raw × max(0, 1 − late_seconds/(14×86400)) × practice_factor`. Срок до23:59MSK; factor1 для сданной практики, иначе0.9 один раз. При неизвестной дате или личности требуется разбор. Проверяющий использует доверенное время и живой лист практики, сохраняет лучшую принятую попытку. / Deadline23:59MSK; practice factor1 if complete, otherwise0.9 once. Unknown deadlines or identity require review. The checker uses trusted timestamps and live attendance, retaining the best approved attempt.

## Источники и обновления / Sources and revision

Из плана курса сохранены цели проекта и Human-level performance; из Archive/Tasks/Task3_NSFW.ipynb — бинарная задача cat против dog/frog, логистическая регрессия и F1-порог. Обновление2026: разделение официального test, явная цена ошибок, сравнение с константой, срезы и протокол измерения человека. Человеческая точность не измерялась и не выдумана.

The course plan supplies project goals and human-level performance. Archive/Tasks/Task3_NSFW.ipynb supplies the animal binary task, logistic regression and F1 threshold. The2026 revision separates official test data and adds costs, constant baselines, slices and a human measurement protocol. No human accuracy was measured or fabricated.

[Precision–recall documentation](https://scikit-learn.org/stable/modules/generated/sklearn.metrics.precision_recall_curve.html).

Проверки / Validation: instructor notebook executed; homework reference100, empty0; four faulty implementations lose points. CPU-compatible NumPy, scikit-learn and matplotlib.
