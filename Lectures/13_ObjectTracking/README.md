# 13 · Трекинг объектов / Object tracking

## Материалы / Materials

- [Практика RU/EN](Practice_RU_EN.ipynb) · [Colab](https://colab.research.google.com/github/alexander-toschev/cv-course/blob/main/Lectures/13_ObjectTracking/Practice_RU_EN.ipynb). Четыре подробных задания по 5–10 минут с проверками / Four detailed exercises with executable checks.
- [Отдельное ДЗ 13 · TRK-13 RU/EN](Homework_RU_EN.ipynb) · [Colab](https://colab.research.google.com/github/alexander-toschev/cv-course/blob/main/Lectures/13_ObjectTracking/Homework_RU_EN.ipynb).
- [Презентации и видео RU/EN / Slides and videos](https://drive.google.com/drive/folders/1_ApZZSujyMgDlJibh3f8R-i5J3Qv_-q0).
- Выполненные решения практики и ДЗ с построчными RU/EN-комментариями — в закрытой преподавательской папке Google Drive. / Executed practice and homework solutions with line-by-line RU/EN comments are in private instructor Drive.

## Данные, протокол, темы / Data, protocol and topics

[MOT15](https://motchallenge.net/data/MOT15/): TUD-Campus и TUD-Stadtmitte; наблюдения — кадры улицы, признаки — пиксели и публичные детекции, цели — рамки и ID пешеходов. Первый запуск скачивает официальный архив 1.31 GB с SHA256, извлекает только две сцены. Данные не включены в репозиторий; соблюдайте условия оригинальных источников и указывайте MOTChallenge/TUD. / Street-video frames, image pixels and public detections, pedestrian boxes and IDs. The first run downloads the official 1.31 GB archive with SHA256 and extracts two scenes only. Respect original-source terms and attribution; data are not redistributed.

Campus — настройка, Stadtmitte — однократная итоговая оценка. Обе сцены входят в официальный train; это учебное разделение, не скрытый benchmark. Не перемешивайте соседние кадры. IoU-трекер не реализует Deep SORT, MOTA-like не равна официальному протоколу MOTChallenge. / Campus is development, Stadtmitte is held-out teaching evaluation; both belong to the official training set. Never shuffle adjacent frames. The IoU tracker is not Deep SORT, and custom MOTA-like is not the official benchmark protocol.

Эталон: gate=0.1, MOTA-like 0.4204 на Stadtmitte, 70 смен ID. KLT: 143/150 точек прошли forward-backward проверку. Это проверка согласованности, не точность относительно истинного optical flow. / Reference: gate 0.1, held-out MOTA-like 0.4204, 70 ID switches. KLT forward-backward filtering retained 143/150 points; consistency is not ground-truth flow accuracy.

Практика: детекции кадра → forward-backward KLT → IoU → смены ID; затем готовый пример трекера. ДЗ: обрезка рамок, предсказание центров, назначение с порогом, непрерывные серии трека. / Practice: frame detections, KLT consistency, IoU and ID switches, followed by a worked tracker. Homework: box clipping, centre prediction, gated assignment and consecutive track runs.

Сохранены исходные темы: KLT, Kalman/Hungarian, Deep SORT, Condensation. Обновление 2026: реальные сцены, явный lifecycle, воспроизводимые измерения и ограничения метрик, отдельное TRK-13. / Original topics retained: KLT, Kalman/Hungarian, Deep SORT and Condensation. The 2026 revision adds real scenes, explicit lifecycle, reproducible measurements, metric caveats and separate TRK-13 homework.

## Сдача / Submission

TRK-13: четыре функции × 25 = 100 баллов. Заполните ФИО и группу, выполните ноутбук сверху вниз, сдайте ipynb с выводами. Последняя ячейка выводит JSON для home-work-checker; блоки проверок независимы. / Four functions × 25 = 100 points. Enter name and group, run all cells in order, submit the notebook with outputs. Independent checks produce a final home-work-checker JSON.

[Матрица сроков / Deadlines](https://docs.google.com/spreadsheets/d/15N5GGHujXPAzRNuyOfmooT7A7sKhXgrMfWHkUkvYYiM/edit): «Сроки ДЗ», N; дату вводит преподаватель, она означает 23:59 МСК, без дополнительного запаса. Просрочка линейно снижает балл до нуля за 14 дней. Затем отсутствие отметки практики №13 («Практика», O) умножает балл на 0.9 ровно один раз. Время сдачи и штрафы определяет внешний проверяющий, не ноутбук студента. / Instructor enters the deadline in column N, 23:59 Moscow, no extra grace. Lateness reduces the score linearly to zero over 14 days; missing practice 13 in column O then multiplies it by 0.9 once. The external grader uses verified receipt time.

CPU: NumPy, SciPy, OpenCV, matplotlib; стандартная среда Colab. Нет обучения тяжёлых сетей. / Standard Colab CPU dependencies; no heavy network training. Legacy course materials remain in Archive.

Видео / Videos: [RU · 30:19](https://drive.google.com/file/d/1TxPKDu1eXhMo1DMStLtwvGGNJi6baeDy/view?usp=drivesdk) · [EN · 29:57](https://drive.google.com/file/d/1Um6pFwxZnQbFbA7YjbUI-j_9CRJl5YhT/view?usp=drivesdk).

Презентации / Slides: [RU](https://docs.google.com/presentation/d/1f6AUtMGND0f1HeT2Hd7ZvrE0Ct9p-HebEnDMQMN9JMY/edit?usp=drivesdk) · [EN](https://docs.google.com/presentation/d/15JYVLxpFrYOyc0On4vP7fotDq82RRyVdrRnEulv7PAU/edit?usp=drivesdk).
