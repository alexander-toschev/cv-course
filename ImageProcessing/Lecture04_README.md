# Лекция 04: выделение ключевых особенностей / Lecture 04: Feature Detection

[Практика RU/EN](Lecture04_FeatureDetection_BSDS500_RU_EN.ipynb) · [Open in Colab](https://colab.research.google.com/github/alexander-toschev/cv-course/blob/main/ImageProcessing/Lecture04_FeatureDetection_BSDS500_RU_EN.ipynb)

Реальные фотографии **BSDS500**, без синтетической замены. / Real BSDS500 photographs, with no synthetic fallback.

## Что делаем / Contents

- Sobel / Scharr: знаковые производные, модуль, направление и общая шкала / signed derivatives, magnitude, orientation and shared display scale.
- Canny: явное сглаживание, пороги и текстура / explicit smoothing, thresholds and texture.
- Harris / Shi–Tomasi: одинаковые правила отбора точек / common point-selection settings.
- HoughLinesP: отрезки на фотографии здания / line segments on a building photograph.
- Precision / recall / F1: учебное взаимно-однозначное сопоставление в радиусе 2 px / teaching one-to-one matching within 2 px.
- Validation-only parameter selection and a frozen-parameter test evaluation.

## Данные / Data

[Официальный BSDS500](https://www2.eecs.berkeley.edu/Research/Projects/CS/vision/grouping/resources.html), архив около 67 MiB. Ноутбук загружает архив по HTTPS, проверяет SHA-256 и содержимое извлечённых файлов. Сам датасет в Git не включён. / Download and extracted cache are verified; dataset bytes are not redistributed in this repository.

| Split | Fixed IDs |
|---|---|
| train | 100075, 108073, 118035 |
| val | 101085, 101087, 102061 |
| test | 100007, 100039, 100099 |

[Условия исходного BSDS](https://www2.eecs.berkeley.edu/Research/Projects/CS/vision/bsds/) описывают некоммерческие исследовательские и образовательные цели. Сохраняются исходные права; это не новая лицензия на фотографии. / The original BSDS page describes non-commercial research and educational use; original rights remain in effect.

Cite: Arbelaez, Maire, Fowlkes, Malik, *Contour Detection and Hierarchical Image Segmentation*, TPAMI 2011. Dataset origins: Martin et al., ICCV 2001.

## Запуск / Run

Python 3.10+, NumPy, OpenCV, SciPy, Matplotlib. В начале ноутбука указана команда установки при необходимости. Запустить ячейки по порядку. Первый запуск требует сеть, повторный использует проверенный локальный кэш. / Run cells in order; first run needs network, later runs use the verified cache.

Полный запуск проверен 03.10.2026: Python 3.14, NumPy 2.5.3, OpenCV 5.0.0, SciPy 1.18.1. Ноутбук печатает версии текущей среды. / Full run verified with these versions; the notebook records your environment.

## Оценка / Evaluation

Это **учебная метрика**, а не официальный BSDS benchmark: максимальное число пар пикселей в радиусе 2 px, усреднение P/R/F1 отдельно по аннотаторам, затем по изображениям. Нет ODS/OIS/AP. Не сравнивайте полученные числа с таблицами публикаций. / This teaching metric is not the official BSDS evaluator or a published benchmark score.

Train используется для разбора, val для настройки; параметры фиксируются до test. Ручные карты границ не являются разметкой углов или прямых. / Human boundary maps are not corner or line labels.

## Практическое задание / Practice assignment

Сохранить `lecture04_results.json`, три иллюстрации, версии библиотек и объяснение лишних/пропущенных структур. Подробные пункты в конце ноутбука. / Save the result JSON, three figures, environment versions and an error analysis.

Это подготовка к feature matching, **не новое номерное ДЗ**. Не отправляйте этот JSON в home-work-checker как итоговую оценку: он содержит метрики эксперимента. / This is preparation for feature matching, not a new numbered homework; the JSON contains experiment metrics, not a grade for home-work-checker.

## Происхождение / Provenance

Темы и формулы из авторских `FD_Edge_Detection.ipynb`, `FD_PointsAndPatches_HARRIS.ipynb`, `FD_Shi_Tomasi_CornerDetector.ipynb`, `FD_Line_Detection_Hough.ipynb` (исходный снимок de257e7). / Original instructor topics retained.

Обновление 2026: фиксированные реальные данные, исправление интерпретации смешанной производной Sobel, явные диапазоны и сглаживание, обработка пустого списка точек, современный NumPy без `np.int0`, контролируемая оценка. / Revision: real data, corrected derivative interpretation, explicit contracts and smoothing, empty-output handling and controlled evaluation.
