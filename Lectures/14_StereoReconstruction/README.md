# 14 · Стереозрение и 3D / Stereo vision and 3D

## Материалы / Materials

- [Практика RU/EN](Practice_RU_EN.ipynb) · [Colab](https://colab.research.google.com/github/alexander-toschev/cv-course/blob/main/Lectures/14_StereoReconstruction/Practice_RU_EN.ipynb). Четыре подробных задания по 5–10 минут с проверками / Four detailed exercises with executable checks.
- [Отдельное ДЗ 14 · ST3D-14 RU/EN](Homework_RU_EN.ipynb) · [Colab](https://colab.research.google.com/github/alexander-toschev/cv-course/blob/main/Lectures/14_StereoReconstruction/Homework_RU_EN.ipynb).
- [Презентации и видео RU/EN / Slides and videos](https://drive.google.com/drive/folders/14-Jn22aopc8-xKLTRez8u9R-5kp1pywI).
- Выполненные решения практики и ДЗ с построчными RU/EN-комментариями — в закрытой преподавательской папке Google Drive. / Executed practice and homework solutions with line-by-line RU/EN comments are in private instructor Drive.

## Данные, протокол, темы / Data, protocol and topics

[Middlebury 2014 Motorcycle](https://vision.middlebury.edu/stereo/data/scenes2014/), [официальная копия scikit-image](https://scikit-image.org/docs/stable/api/skimage.data.html#skimage.data.stereo_motorcycle): ректифицированные RGB-фото 500×741, эталон disparity и калибровка. Наблюдение — соответствующие пиксели камер; признаки — яркость и текстура; цель — disparity и метрические 3D-координаты. Загрузка около 2.5 MB, версия и SHA256 закреплены. Middlebury разрешает использование/публикацию с цитированием Scharstein et al., GCPR 2014. / Rectified RGB photographs, reference disparity and calibration. Observations are corresponding pixels, features are intensity and texture, targets are disparity and metric 3D. About 2.5 MB, pinned version and SHA256. Cite the original work and respect source terms.

Одна сцена, фиксированные настройки SGBM до оценки. Это демонстрация геометрии, не проверка обобщения. Случайное разбиение пикселей не даёт независимый test; для сравнения моделей нужны дополнительные сцены. / One scene, SGBM configuration fixed before evaluation. This is a geometry demonstration, not a generalization benchmark. Pixel shuffling does not yield an independent test; model comparisons require additional scenes.

Калибровка уменьшенных изображений: f=994.978 px, cx=311.193, cy=254.877, doffs=31.086 px, B=0.193001 m. Z=fB/(d+doffs); X вправо, Y вниз, Z вперёд. GT исключает NaN/inf и неположительные значения; отсутствие предсказания считается ошибкой при Bad2 по всему GT. / Downsampled calibration; camera axes right/down/forward. Exclude nonfinite/nonpositive GT; missing predictions count as failures in all-GT Bad2.

Эталон CPU: coverage=0.7930, MAE по валидным ответам=1.0442 px, Bad2 по всему GT=0.2537. / CPU reference results; OpenCV versions can change numerical output.

Практика: формат disparity → честные метрики → глубина → облако точек. ДЗ: масштабирование калибровки, Bad-pixel отчёт, триангуляция, ошибка репроекции. / Practice: disparity representation, metrics, depth and point clouds. Homework: calibration scaling, bad-pixel report, triangulation and reprojection error.

Сохранены исходные темы: калибровка, эпиполярная геометрия, stereo/SfM и реконструкция. Обновление 2026: реальные Middlebury, учёт doffs и масштаба, проверяемая геометрия, обзор NeRF/Gaussian Splatting; последние два не выдаются за выполненный эксперимент. / Original calibration, epipolar geometry, stereo/SfM and reconstruction topics retained. The 2026 revision adds real Middlebury data, offset/scale handling, executable geometry and an overview of NeRF/Gaussian Splatting, not an executed experiment.

## Сдача / Submission

ST3D-14: четыре функции × 25 = 100 баллов. Заполните ФИО и группу, выполните ноутбук сверху вниз, сдайте ipynb с выводами. Последняя ячейка выводит JSON для home-work-checker; блоки проверок независимы. / Four functions × 25 = 100 points. Enter name and group, run all cells in order, submit the notebook with outputs. Independent checks produce a final home-work-checker JSON.

[Матрица сроков / Deadlines](https://docs.google.com/spreadsheets/d/15N5GGHujXPAzRNuyOfmooT7A7sKhXgrMfWHkUkvYYiM/edit): «Сроки ДЗ», O; дату вводит преподаватель, она означает 23:59 МСК, без дополнительного запаса. Просрочка линейно снижает балл до нуля за 14 дней. Затем отсутствие отметки практики №14 («Практика», P) умножает балл на 0.9 ровно один раз. Время сдачи и штрафы определяет внешний проверяющий, не ноутбук студента. / Instructor enters the deadline in column O, 23:59 Moscow, no extra grace. Lateness reduces the score linearly to zero over 14 days; missing practice 14 in column P then multiplies it by 0.9 once. The external grader uses verified receipt time.

CPU: NumPy, SciPy, OpenCV, matplotlib; стандартная среда Colab. Нет обучения тяжёлых сетей. / Standard Colab CPU dependencies; no heavy network training. Legacy course materials remain in Archive.

Видео / Videos: [RU · 31:32](https://drive.google.com/file/d/1C0l9gSUEY27X5HbRRseKDu4_l9Fqw6oZ/view?usp=drivesdk) · [EN · 31:37](https://drive.google.com/file/d/1rePWdtWa_5eGKwqZOxqwOgVUkVkmN-HS/view?usp=drivesdk).

Презентации / Slides: [RU](https://docs.google.com/presentation/d/1TKg_N-Vyr1WI6ltcuUMMC1vTgkKesCGc6z3KrkMf930/edit?usp=drivesdk) · [EN](https://docs.google.com/presentation/d/1nh5VfmyKoZlfgDklobURT7ksRgcDjQhlBqsiU3TTKDI/edit?usp=drivesdk).
