# 05. Сопоставление особенностей / Feature Matching

- [Практика / Practice RU/EN](Practice_RU_EN.ipynb) · [Colab](https://colab.research.google.com/github/alexander-toschev/cv-course/blob/main/Lectures/05_FeatureMatching/Practice_RU_EN.ipynb)
- [Практика с решениями / Worked practice RU/EN](Practice_Solutions_RU_EN.ipynb) · [Colab](https://colab.research.google.com/github/alexander-toschev/cv-course/blob/main/Lectures/05_FeatureMatching/Practice_Solutions_RU_EN.ipynb)
- [ДЗ / Homework RU/EN](Homework_RU_EN.ipynb) · [Colab](https://colab.research.google.com/github/alexander-toschev/cv-course/blob/main/Lectures/05_FeatureMatching/Homework_RU_EN.ipynb)
- [Презентации, видео и тексты RU/EN / Slides, videos and scripts](https://drive.google.com/drive/folders/1CpGu_Q-neSpihA_YZs84ZY-h7kr15fvo)

SIFT, ORB, BFMatcher, ratio test, cross-check, гомография / homography, RANSAC, геометрическая проверка / geometric verification. LightGlue — факультативное продолжение / optional extension.

## Реальные данные / Real data

[Oxford Affine Covariant Features](https://www.robots.ox.ac.uk/~vgg/research/affine/), серии / sequences graf, leuven, wall, bikes. Около 33 MB, CPU. / About 33 MB, CPU.

Наблюдение — пара фотографий одной сцены. Признаки — координаты и SIFT/ORB-дескрипторы; эталон — гомография между кадрами. / Each observation is a pair of scene photographs. Features are coordinates and SIFT/ORB descriptors; the target is the reference homography.

Настройка только на graf и leuven; wall и bikes — после фиксации параметров. Кадры одной сцены не распределяются случайно между выборками. Учебная precision@3px не равна официальному Oxford benchmark. / Tune on graf and leuven; evaluate on wall and bikes after freezing settings. Keep views of each scene together. Teaching precision@3px is not the official Oxford benchmark.

Фотографии загружаются с Oxford с проверкой SHA-256; изображения в репозиторий не включены, синтетической замены нет. Авторы не указывают отдельную открытую лицензию на фотографии: сохраняйте авторство и ссылки, MIT-лицензия кода на них не распространяется. / Original photographs are downloaded from Oxford with SHA-256 checks, without a synthetic fallback. Images are not bundled. The authors do not state a separate open image license: retain attribution and links; code licensing does not cover photographs.

[Официальный код оценки](https://www.robots.ox.ac.uk/~vgg/research/affine/det_eval_files/repeatability.m) задаёт координаты от нуля: H1→j используется напрямую с OpenCV. / The official evaluation code specifies zero-based coordinates: use H1→j directly with OpenCV.

## Практика / Practice

1. SIFT и ORB: размерность, dtype, норма, число matches. / Dimensions, dtype, norm and match counts.
2. Ratio test: сравнить пороги 0.6, 0.75, 0.9. / Compare ratio thresholds.
3. RANSAC: пороги 1, 3 и 6 пикселей; inliers и независимая ошибка. / Pixel thresholds, inliers and independent error.
4. Зафиксировать конфигурацию, проверить отложенные сцены и объяснить ошибки. / Freeze the configuration, evaluate held-out scenes and explain failures.

## Отдельное ДЗ / Separate homework

ID `Feature_Matching_Autograder`, version 2, 100 raw points. Номер лекции — 5. / Lecture number: 5.

| Функция / Function | Баллы / Points |
|---|---:|
| ratio_filter | 20 |
| estimate_homography | 30 |
| transfer_errors | 25 |
| choose_config | 25 |

Сдайте заполненный .ipynb с именем и группой в [папку сдачи](https://drive.google.com/drive/folders/1wYT_P6yTIVR_ZI2cqZQQrXaPlaCfk2sm). / Submit the completed notebook with your name and group.

[Сроки по группам](https://docs.google.com/spreadsheets/d/15N5GGHujXPAzRNuyOfmooT7A7sKhXgrMfWHkUkvYYiM/edit) — источник даты сдачи. Штрафы вычисляет внешний проверяющий по подтверждённому времени сдачи; ноутбук возвращает исходный балл. При отсутствии отметки практики лекции 5 применяется ×0.9 после штрафа за опоздание, ровно один раз. / Group deadlines are authoritative. The external checker uses verified receipt timestamps; the notebook outputs raw points. Missing lecture 5 practice applies ×0.9 after lateness, once only.

Проверено: Python 3.11, NumPy 2.2.6, OpenCV 4.12.0.88, CPU. Практика проходит целиком; эталон 100, пустое решение 0; четыре ошибочных реализации не получают полный балл. Это проверка выполнения кода в локальной среде, не заявление о проверке интерфейса Colab. / Local CPU validation passes: reference 100, empty solution 0, four faulty implementations rejected. The Colab UI itself was not tested.

## Источники и обновления / Sources and updates

Сохранены темы авторских FD_SIFT, FD_ORB и OpenCV_ImageStitching, находящихся в Archive. Обновление 2026: реальные серии Oxford, проверка загрузки, независимая геометрия, разделение сцен, явная обработка неудачной оценки H и отдельное ДЗ. / Instructor topics from archived SIFT, ORB and stitching notebooks are retained. The 2026 revision adds real Oxford sequences, verified downloads, independent geometry, scene separation, explicit failure handling and separate homework.

Видеоверсии: 30 минут с явно обозначенными паузами для практики. Озвучка синтезирована согласованным голосом преподавателя; отдельные MP3 содержат только речь. / Videos run 30 minutes including labelled practice pauses. Narration uses the approved synthetic instructor voice; standalone MP3s contain speech only.

В разборе практики сохранены иллюстрации validation/test и пример RANSAC: исходные matches, inliers, отклонённые matches и выравнивание фотографий. / Worked solutions include validation/test photo previews and a RANSAC example with initial matches, inliers, rejected matches and image alignment.
