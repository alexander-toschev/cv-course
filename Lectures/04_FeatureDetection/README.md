# 04. Выделение ключевых особенностей / Feature Detection

- [Практика / Practice RU/EN](Practice_RU_EN.ipynb) · [Colab](https://colab.research.google.com/github/alexander-toschev/cv-course/blob/main/Lectures/04_FeatureDetection/Practice_RU_EN.ipynb)
- [ДЗ / Homework RU/EN](Homework_RU_EN.ipynb) · [Colab](https://colab.research.google.com/github/alexander-toschev/cv-course/blob/main/Lectures/04_FeatureDetection/Homework_RU_EN.ipynb)
- [Презентации и видеолекции RU/EN / Slides and video lectures](https://drive.google.com/drive/folders/1tlu7th5LYJrTUFQvCuAe7oh_d9cvM_MW)

Идентификатор проверки / Grading ID: `FD-04`. Номер папки — номер лекции; старые ID сохранены для совместимости с учётом оценок. / The folder number identifies the lecture; existing grading IDs are retained for gradebook compatibility.

[Сроки по группам / Group deadlines](https://docs.google.com/spreadsheets/d/15N5GGHujXPAzRNuyOfmooT7A7sKhXgrMfWHkUkvYYiM/edit). Текущая матрица сроков имеет приоритет перед историческими датами внутри ранее выпущенных материалов. / The current deadline matrix takes precedence over historical dates in previously released materials.

[Сдача / Submission folder](https://drive.google.com/drive/folders/1wYT_P6yTIVR_ZI2cqZQQrXaPlaCfk2sm). Сдайте заполненный .ipynb с именем и группой. / Submit the completed notebook with your name and group.

## BSDS500
Реальные фотографии и человеческая разметка границ. / Real photographs and human boundary annotations.
[Источник / Source](https://www2.eecs.berkeley.edu/Research/Projects/CS/vision/grouping/resources.html).
Практика: Sobel/Scharr, Canny, Harris/Shi–Tomasi, HoughLinesP, оценка границ. / Practice: derivatives, edges, corners, lines and boundary evaluation.
ДЗ №4: модуль и направление (20), Canny (30), оценки угла (25), выбор конфигурации на validation (25). / Homework 4: magnitude and direction (20), Canny (30), corner scores (25), validation selection (25).
Всего 100 исходных баллов; штраф рассчитывается отдельно по времени принятой сдачи. / 100 raw points; lateness is applied separately using the accepted submission timestamp.
Учебная метрика не равна официальному BSDS benchmark. / The teaching metric is not the official BSDS benchmark.

Темы исходных материалов преподавателя сохранены. Обновления 2026: фиксированный реальный датасет, проверяемая загрузка, корректные производные, современный API и разделение validation/test. / Instructor topics are retained. 2026 updates add fixed real data, verified downloads, correct derivatives, current APIs and validation/test separation.
