# Лекция 08 · Цикл ML и ортогонализация / ML Cycle and Orthogonalization

От постановки задачи к честному эксперименту: Gram–Schmidt → PCA → Ridge → validation → test. / From a question to an honest experiment: Gram–Schmidt → PCA → Ridge → validation → test.

## Материалы / Materials

- [Презентации и видео RU/EN / Slides and videos](https://drive.google.com/drive/folders/1w6vOmboM1Vbb-vCi7pn5EzsFFMD7trt0).
- [Практика RU/EN](Practice_RU_EN.ipynb) · [Open in Colab](https://colab.research.google.com/github/alexander-toschev/cv-course/blob/main/Lectures/08_MLCycle_Orthogonalization/Practice_RU_EN.ipynb).
- [Отдельное ДЗ 08 / Separate homework 08](Homework_RU_EN.ipynb) · [Open in Colab](https://colab.research.google.com/github/alexander-toschev/cv-course/blob/main/Lectures/08_MLCycle_Orthogonalization/Homework_RU_EN.ipynb).

Практика: четыре задания по 5–10 минут. Каждый блок содержит объяснение, пример, подробный контракт, ячейку решения и исполняемую проверку. Отдельный выполненный преподавательский ноутбук с содержательными RU/EN-комментариями всех непустых строк кода хранится в закрытой папке Drive; в студенческий репозиторий ответы не включены.

Practice: four 5–10 minute exercises, each with explanation, an example, a detailed contract, a student solution cell, and executable checks. A separate executed instructor notebook comments all nonempty code lines meaningfully in RU/EN and is stored in private Drive.

## Данные и протокол / Data and protocol

[UCI Optical Recognition of Handwritten Digits](https://doi.org/10.24432/C50P49), Alpaydin & Kaynak, CC BY 4.0; [sklearn load_digits](https://scikit-learn.org/stable/modules/generated/sklearn.datasets.load_digits.html). 1797 реальных изображений 8×8: наблюдение — изображение, признаки — 64 интенсивности 0…16, цель — класс 0…9. / 1,797 real 8×8 images: one image per observation, 64 intensity features in 0…16, target digit 0…9.

Деление на известную константу16; stratified seed808, train/validation/test=1078/359/360. Среднее, PCA и Ridge обучаются только на train. Выбор k∈{8,16,32,64}, alpha∈{.01,.1,1,10,100} по validation; точные ничьи: меньше k, затем больше alpha. Test оценивается после фиксации выбора. / Divide by known constant16; fit mean, PCA and Ridge on train only. Select from the declared grid on validation, ties favor smaller k then larger alpha. Evaluate test after selection is frozen.

Выполненный CPU-эксперимент: k64, alpha1; train95.08%, validation337/359=93.87%, test338/360=93.89%. Сжатие PCA не улучшило классификацию в этой сетке. Writer IDs недоступны; split не разделяет авторов. Это не официальный UCI benchmark. Данные использовались в лекциях06–07; новый seed не создаёт независимый новый test и не позволяет напрямую сравнивать с прежней CNN.

Executed CPU experiment: k64, alpha1; train95.08%, validation337/359=93.87%, test338/360=93.89%. PCA compression did not improve classification in this grid. Writer IDs are unavailable, so the split is not writer-disjoint or an official UCI benchmark. Lectures06–07 used the same underlying data; a new seed creates neither an independent new test nor a controlled comparison with the earlier CNN.

## ДЗ и оценивание / Homework and grading

ORTH-08: orthonormal_rows20 + fit_pca25 + project15 + fit_ridge25 + select_config15 = 100 исходных баллов / raw points. Независимые проверки включают зависимые строки, нулевой базис, знаконезависимый PCA-проектор, отсутствие повторного центрирования, intercept без штрафа и запрет выбора по test. / Independent checks cover dependent rows, zero input, sign-invariant PCA projectors, no batch refitting, an unpenalized intercept, and ignoring test metrics during selection.

[Матрица сроков / Deadline matrix](https://docs.google.com/spreadsheets/d/15N5GGHujXPAzRNuyOfmooT7A7sKhXgrMfWHkUkvYYiM/edit): столбец I, практика08 — J на листе «Практика». Даты заполняет преподаватель; пустая дата требует разбора. / Deadline column I; lecture08 practice is column J on the practice sheet. Dates are entered by the instructor; a blank requires review.

Итог / Final: `raw × max(0,1−late_seconds/(14×86400)) × practice_factor`; срок до23:59MSK, без дополнительного запаса; factor=1 при отметке практики, иначе0.9 ровно один раз. Время, личность и практика проверяются вне ноутбука; сохраняется лучший принятый итог. / Deadline23:59MSK with no added grace; factor1 when practice is marked complete, otherwise0.9 once. Trusted time, identity and practice are checked externally; the best approved final score is retained.

## Источники и обновление / Sources and revision

Сохранены три темы архивного [Task2_Orthogonalization](../../Archive/Tasks/Task2_Orthogonalization.ipynb): Gram–Schmidt, PCA, Ridge selection. Обновление2026: вместо Iris — реальные CV-изображения, явный ML-протокол, защита от утечки, подробные RU/EN-инструкции, отдельное ДЗ и закрытые ответы. Архивный контракт не менялся.

The three legacy topics are retained: Gram–Schmidt, PCA, and Ridge selection. The2026 revision replaces Iris with real CV images and adds an explicit ML protocol, leakage checks, detailed RU/EN instructions, separate homework and private instructor answers. The archived assignment contract is unchanged.

References: [PCA](https://scikit-learn.org/stable/modules/generated/sklearn.decomposition.PCA.html), [Ridge](https://scikit-learn.org/stable/modules/generated/sklearn.linear_model.Ridge.html), [NumPy SVD](https://numpy.org/doc/stable/reference/generated/numpy.linalg.svd.html).

Проверка / Validation: executed instructor notebook; homework reference100, blank0; five faulty implementations detected. Colab CPU dependencies: NumPy, scikit-learn, matplotlib. No synthetic replacement dataset.
