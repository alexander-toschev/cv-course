# Lecture 03 — Image Processing / Обработка изображений

- [Practice RU/EN](Lecture03_ImageProcessing_RU_EN.ipynb)
- [Homework Task1 RU/EN](../Tasks/Task1_ImageProcessing.ipynb)
- [Deadline and penalty policy](../Tasks/Task1_2026_policy.json)

## Работа / Workflow

Python 3.10+, NumPy 2.x, OpenCV 4.x/5.x, matplotlib. Install dependencies separately; restart and run all notebook cells. Practice data is generated locally and needs no network access.

Практика охватывает dtype/range, RGB/BGR, гистограммы, границы, Gaussian/median/bilateral, FFT и пирамиды. / Practice covers dtype/range, RGB/BGR, histograms, boundaries, filtering, FFT and pyramids.

Презентации RU/EN и тексты озвучки находятся в Google Drive: `ITIS/IZBRGLAV/Лекция 03 — Обработка изображений`. / Presentations and narration scripts are in the course Google Drive folder.

## Task1

Сохранены исходные функции и шкала: median 2.5, bilateral 2.5, FFT 10; всего **15**. / Original function names and scoring retained.

Начало / Start: **27 September 2026 00:00 Moscow**. Срок / Due: **11 October 2026 23:59 Moscow (UTC+03:00)**.

`p = min(1, max(0, submitted_at - due) / (due - start))`

`final_score = raw_score * (1 - p)`

Интервалы считаются в секундах. Штраф применяет ассистент один раз по подтверждённому времени принятой версии в Google Drive. Студенческий ноутбук выводит исходный балл. / Durations are in seconds. The assistant applies the penalty once using the verified accepted version time in Google Drive. The notebook reports a raw score.

Все попытки сохраняются; в таблице остаётся лучшая одобренная оценка после штрафа. / All attempts are archived; the gradebook retains the best approved final score.

Task0 remains under its original no-penalty policy. No retrospective changes.

## Источники и изменения / Sources and changes

Topics and original tasks: `ImageProcessing.ipynb`, `Tasks/Task1_ImageProcessing.ipynb`, snapshot `5856aa5`. The original Task1 is preserved in Git history.

2026 adaptation: fixed the empty FFT slice; specified a circular high-pass mask and degenerate normalization; removed obsolete 2025 dates, sample student identity, network image dependency and local-clock penalties. Grading now checks the requested values, shape, dtype, parameters and input preservation. A repeated test run resets the score.

Sources: [OpenCV filter API](https://docs.opencv.org/4.x/d4/d86/group__imgproc__filter.html), [NumPy FFT](https://numpy.org/doc/stable/reference/routines.fft.html).

Папка сдачи / Submission folder: https://drive.google.com/drive/folders/1QXU_rDb1U6dMxVLzfoqOFzpkEA6K_cZZ
