# Лекция 07 · Свёрточные сети / Convolutional Networks

От локального окна NumPy к обученной CNN в PyTorch. / From a NumPy local window to a trained PyTorch CNN.

## Материалы / Materials

- [Презентации, видео, сценарии RU/EN / Slides, videos and scripts](https://drive.google.com/drive/folders/11myHqGJ6uaC-2waMXGserxIV8OOFDVDh).
- [Практика / Practice](Practice_RU_EN.ipynb) · [Colab](https://colab.research.google.com/github/alexander-toschev/cv-course/blob/main/Lectures/07_ConvolutionalNetworks/Practice_RU_EN.ipynb).
- [Решения практики / Worked solutions](Practice_Solutions_RU_EN.ipynb) · [Colab](https://colab.research.google.com/github/alexander-toschev/cv-course/blob/main/Lectures/07_ConvolutionalNetworks/Practice_Solutions_RU_EN.ipynb).
- [ДЗ 07 / Homework 07](Homework_RU_EN.ipynb) · [Colab](https://colab.research.google.com/github/alexander-toschev/cv-course/blob/main/Lectures/07_ConvolutionalNetworks/Homework_RU_EN.ipynb).

Практика содержит семь тем и подробные мини-задания на 5–10 минут: входные данные, шаги, ожидаемый результат и критерии проверки. В отдельном выполненном ноутбуке решений каждая исполняемая строка прокомментирована на русском и английском. / Seven practice topics include detailed 5–10 minute mini-tasks: inputs, steps, deliverables and acceptance checks. The separate executed solutions notebook comments every executable line in Russian and English.

## Данные и протокол / Data and protocol

[UCI Optical Recognition of Handwritten Digits](https://archive.ics.uci.edu/dataset/80/optical+recognition+of+handwritten+digits), Alpaydin & Kaynak, CC BY 4.0; загрузка / loading: sklearn.datasets.load_digits. 1797 реальных изображений 8×8; признаки — интенсивности 0…16, цель — цифра 0…9. / 1,797 real 8×8 images; features are intensities 0…16, target is digit 0…9.

Train/validation/test = 1078/359/360; stratified seed 707. Нормировка на известный диапазон 16. Настройка по validation, test только после выбора. Writer IDs недоступны: split не разделяет авторов. Это учебный эксперимент, не официальный benchmark. Данные уже использовались в лекции 06; новый seed не создаёт независимый новый test. / Normalize by the known range 16. Tune on validation and evaluate test after selection. Writer IDs are unavailable, so this is not writer-disjoint or an official benchmark. Lecture 06 used the same underlying data; a new seed does not create a fresh independent test.

CNN: 1→8→16 channels, two 3×3 convolutions and 2×2 pools, Linear(64,10), 1,898 parameters. Adam, 25 epochs, batch 64; lr candidates 0.001 and 0.003. CPU run: selected lr 0.003, test 345/360 = 95.83%; no claim of superiority over MLP.

## ДЗ и проверка / Homework and grading

CNN-07: correlate2d (25), pool2d (20), build_cnn (20), evaluate (20), select_best (15): 100 raw points. Полные контракты и тесты находятся в ноутбуке. / Full contracts and tests are in the notebook.

[Матрица сроков / Group deadline matrix](https://docs.google.com/spreadsheets/d/15N5GGHujXPAzRNuyOfmooT7A7sKhXgrMfWHkUkvYYiM/edit): столбец H / column H. Даты заполняет преподаватель; пусто не означает автоматическую просрочку. / Dates are entered by the instructor; blank does not imply lateness.

Штраф после срока до 23:59 MSK: raw × max(0, 1 − late_seconds / (14×86400)); затем ×0.9 ровно один раз, если практика лекции 7 не отмечена. Связь имени и группы и живой лист практики проверяются преподавателем. / After the deadline at 23:59 MSK: raw × max(0, 1 − late_seconds / (14×86400)), then ×0.9 exactly once if lecture 7 practice is not marked complete. Identity and the live practice sheet are verified externally. Ноутбук выводит исходный балл, не назначает штраф по локальным часам. / The notebook reports raw points and never assigns penalties from the local clock.

## Переиспользование и обновления / Reuse and updates

Сохранены темы convolution, stride, padding, pooling и dense из Archive/numpy/Cifar_CNN.ipynb; основы forward/backward связаны с Archive/ml/CNN_hands_only.ipynb. Обновление 2026: PyTorch, реальные Digits, явный протокол разбиения, независимые проверки и двуязычные подробные решения. / Convolution, stride, padding, pooling and dense topics are retained from Archive/numpy/Cifar_CNN.ipynb; forward/backward foundations connect to Archive/ml/CNN_hands_only.ipynb. The 2026 revision adds PyTorch, real Digits, an explicit split protocol, independent tests and detailed bilingual solutions.

Проверено / Verified: полный CPU-запуск практики и решений / full CPU execution; reference 100, blank 0; five faulty implementations detected. Видео / videos: RU 15:46, EN 13:30, без искусственных пауз / without artificial pauses.
