# 12 · Сегментация изображений / Image segmentation

От RGB-фотографии к маске: разметка, ignore-область, IoU/Dice, GrabCut, U-Net и честный протокол оценки. / From RGB photographs to masks: annotation, ignored regions, IoU/Dice, GrabCut, U-Net and a defensible evaluation protocol.

## Материалы / Materials

- [Практика RU/EN — четыре задания по 5–10 минут / Four practice exercises](Practice_RU_EN.ipynb) · [Colab](https://colab.research.google.com/github/alexander-toschev/cv-course/blob/main/Lectures/12_ImageSegmentation/Practice_RU_EN.ipynb).
- [Отдельное ДЗ №12 / Separate homework 12 — SEG-12](Homework_RU_EN.ipynb) · [Colab](https://colab.research.google.com/github/alexander-toschev/cv-course/blob/main/Lectures/12_ImageSegmentation/Homework_RU_EN.ipynb).
- [Дополнительная демонстрация Tiny U-Net / Optional worked Tiny U-Net demo](Demo_TinyUNet_RU_EN.ipynb). Это пример, а не пятое задание практики. / A worked example, not a fifth practice exercise.
- [Презентации, озвучка, видео RU/EN / Slides, narration and videos](https://drive.google.com/drive/folders/17BAJaRtJK-q8h6qtFgnQG6FWEHELg2BT).
- Выполненный преподавательский разбор практики с построчными RU/EN-комментариями хранится в закрытом Google Drive. / Executed instructor practice solutions with line-by-line RU/EN comments are stored in private Google Drive.

Видео / Videos: [RU · 30:22](https://drive.google.com/file/d/18GpEJZRuTxSVY6OCfT4hr4IwCuTlovjY/view) · [EN · 30:01](https://drive.google.com/file/d/1sWPzr2TgKkeACiLeNiwUSXn5CzuFEDHe/view).

Презентации / Slides: [RU](https://docs.google.com/presentation/d/1zpO1jdrwJjy8E2hzjqMyaclKsqRL6yOfXyhr4Ur1Qpk/edit) · [EN](https://docs.google.com/presentation/d/1zRn-vn0Welrk4iYWigL5RXv2iFNykq3VfhXimM5Wddc/edit).

## Реальные данные / Real data

[Oxford-IIIT Pet](https://www.robots.ox.ac.uk/~vgg/data/pets/): наблюдение — фотография кошки или собаки; вход — RGB; цель — попиксельная trimap. Значения: 1 — объект, 2 — фон, 3 — неопределённая граница. В этом занятии метка 3 исключается из loss и метрик, а не превращается в фон. / An observation is a cat or dog photograph; inputs are RGB pixels; targets are pixelwise trimaps. Labels: 1 foreground, 2 background, 3 ambiguous boundary. Label 3 is excluded from loss and metrics, not relabelled as background.

Условия источника: исследовательское использование; права на исходные фотографии сохраняются у владельцев. Ноутбук скачивает официальные архивы и проверяет MD5; данные не включены в GitHub. Первый запуск загружает около 0,8 ГБ. / Source terms: research use, respecting original image owners' rights. The notebook downloads official archives and checks MD5; data are not redistributed in this repository. The first run downloads about 0.8 GB.

Фиксированная учебная подвыборка: 40 train, 8 dev, 8 test, seed 1212; кошки и собаки поровну. Train/dev берутся из официального trainval, test — из test; идентификаторы не пересекаются. Идентичность животного не установлена: это ограничение, а не гарантия независимости особей. / Fixed teaching subset: 40 train, 8 dev, 8 test, seed 1212, balanced cats/dogs. Train/dev use the official trainval split; test uses the official test split. Image IDs are disjoint; individual-animal independence is not established.

## Протокол и результаты / Protocol and results

GrabCut: относительные отступы 0.03/0.10/0.20, три итерации, рамка строится без ground truth. Выбор по dev, затем одна оценка test. В эталонном запуске выбран 0.03, mean test IoU = 0.6903; одна из восьми масок полностью неудачна. / GrabCut uses relative insets 0.03/0.10/0.20, three iterations, and no ground truth to construct rectangles. Select on dev, then evaluate test once. Reference run: inset 0.03, mean test IoU 0.6903; one of eight masks completely fails.

Tiny U-Net: 3 721 параметр, 64×64, 40 фото, 30 эпох, Adam 0.003, masked BCE, заранее заданный порог 0.5. Loss снизился, но test foreground IoU = 0: сеть предсказала фон. Это учебный отрицательный результат, не рейтинг архитектур; методы получают разные входы и бюджеты. Настраивать модель после просмотра test нельзя. / Tiny U-Net: 3,721 parameters, 64×64, 40 photos, 30 epochs, Adam 0.003, masked BCE, predeclared threshold 0.5. Loss decreased but test foreground IoU was zero: background collapse. This is a teaching failure case, not an architecture ranking; methods have different inputs and budgets. Do not tune after inspecting test.

Эталон: Python 3.9, OpenCV 4.6, PyTorch 1.13.1, CPU. Численные результаты могут отличаться между версиями библиотек; проверки оценивают контракты функций, а не совпадение результатов обучения до последнего знака. / Reference environment: Python 3.9, OpenCV 4.6, PyTorch 1.13.1, CPU. Library versions may change numerical results; checks assess function contracts, not exact training scores.

## Сдача / Submission

SEG-12: четыре функции × 25 баллов = 100. Заполните имя, фамилию и группу, выполните весь ноутбук сверху вниз и сдайте `.ipynb` с выводами. Последняя ячейка печатает JSON для home-work-checker. / Four functions × 25 points = 100. Fill in identity and group, run the whole notebook in order, and submit the `.ipynb` with outputs. The final cell prints JSON for home-work-checker.

[Матрица сроков / Group deadline matrix](https://docs.google.com/spreadsheets/d/15N5GGHujXPAzRNuyOfmooT7A7sKhXgrMfWHkUkvYYiM/edit): «Сроки ДЗ», M; дату вводит преподаватель. Дата означает 23:59 МСК, без дополнительного запаса. Линейный штраф за просрочку достигает 100% через 14 дней. Затем отсутствие отметки практики №12 («Практика», N) уменьшает результат ещё на 10% ровно один раз. Штрафы применяет внешний проверяющий по подтверждённому времени сдачи. / Deadline: column M, entered by the instructor, 23:59 Moscow, no additional grace. Lateness reduces the score linearly to zero over 14 days. Missing practice-12 attendance (column N) then multiplies the result by 0.9 exactly once. The external grader applies penalties using verified submission time.

## Источники и обновления / Sources and revisions

Сохранены темы исходного курса: foreground/background, GrabCut, U-Net и semantic segmentation. Обновление 2026: реальные Oxford Pet, явные train/dev/test, ignore-политика, macro/pooled IoU, разбор провала модели и отдельное ДЗ SEG-12. Это новое ДЗ заменяет старую ссылку Task6_Semantic в актуальной матрице; старые материалы остаются в Archive. По сокращённому плану после №10 идёт №12, затем №13 и №14. / Inherited course topics: foreground/background, GrabCut, U-Net and semantic segmentation. The 2026 revision adds real Oxford Pet data, explicit splits, ignored-region policy, macro/pooled IoU, a failure analysis and separate SEG-12 homework. It replaces the legacy Task6_Semantic link in the active matrix; legacy materials remain in Archive. The shortened sequence is 10 → 12 → 13 → 14.

- [OpenCV GrabCut](https://docs.opencv.org/4.13.0/d3/d47/group__imgproc__segmentation.html)
- [U-Net paper](https://arxiv.org/abs/1505.04597)
- [SAM 2](https://github.com/facebookresearch/sam2) — обзор возможностей, не запущенный benchmark / overview only, not an executed benchmark.
