# Лекция 02 / Lecture 02: Image Formation

[Практика RU/EN / Bilingual notebook](Lecture02_ImageFormation_RU_EN.ipynb)

Проекция куба, фокус и глубина, внешние параметры камеры, выпрямление плоского документа и согласованный resize/crop. Все изображения создаются локально. Сеть нужна только для первоначальной установки библиотек.

Cube projection, focal scale and depth, camera extrinsics, planar document rectification and consistent resize/crop. All images are generated locally. Network access is only needed to install dependencies initially.

## Запуск / Run

Из корня репозитория, Python 3.12 или новее. Проверено на Python 3.14. / From the repository root, use Python 3.12 or newer. Tested with Python 3.14.

```sh
python3 -m venv .venv
source .venv/bin/activate
python -m pip install -r ImageProcessing/lecture02-requirements.txt
python -m ipykernel install --user --name cv-lecture02 --display-name "CV Lecture 02"
```

Откройте ноутбук в Jupyter или VS Code, выберите ядро **CV Lecture 02**, затем Restart Kernel and Run All. / Open the notebook in Jupyter or VS Code, choose **CV Lecture 02**, then Restart Kernel and Run All.

Файл зависимостей устанавливает вычислительные библиотеки и ядро. Интерфейс Jupyter/VS Code устанавливается отдельно. После установки практика работает офлайн. `opencv-python-headless` не открывает GUI-окна, все иллюстрации выводятся через Matplotlib.

The dependency file installs the numerical libraries and kernel. Install the Jupyter/VS Code interface separately. The practice then runs offline. `opencv-python-headless` does not open GUI windows, and Matplotlib displays all figures.

## Соглашения / Conventions

- Камера: X вправо, Y вниз, Z вперёд. / Camera: X right, Y down, Z forward.
- Формулы используют столбцы, NumPy хранит точки строками. / Equations use column vectors, NumPy stores points as rows.
- `R,t` переводят мир в камеру, `t = -R @ C`. / `R,t` map world to camera, with camera centre `C`.
- Проекция отклоняет точки с неположительной глубиной. / Projection rejects nonpositive depth.
- Resize использует соглашение центров пикселей OpenCV linear resize. / Resize uses the OpenCV linear resize pixel-centre convention.

## Источники и адаптация / Sources and adaptation

Темы и последовательность опираются на [ImageFormation_fixed](ImageFormation_fixed.ipynb) и [PerspectiveTransform](../PerspectiveTransform.ipynb). Исходные ноутбуки сохранены без изменений.

Topics and sequence follow those original notebooks. They remain unchanged.

Адаптация 2026: явная проверка глубины, сравнение с `cv2.projectPoints`, согласованный угол поворота, синтетический документ вместо внешних загрузок, проверки углов гомографии и пересчёт K после resize/crop.

2026 adaptation: explicit depth validation, comparison with `cv2.projectPoints`, consistent rotation angle, a synthetic document instead of external downloads, homography corner checks and camera matrix updates after resize/crop.

`lecture02_data` содержит воспроизводимые результаты: `doc.png` (исходный), `photo.png` (перспектива), `rectified.png` (выпрямление). Ноутбук не зависит от этих файлов. / These reproducible sample outputs are optional: the notebook regenerates them.

## Домашняя работа / Homework

Упражнения в конце ноутбука относятся к практике. Текущее ДЗ: [Task0_Numpy](../Tasks/Task0_Numpy.ipynb). Task1_ImageProcessing выдаётся после лекции о фильтрации. Эта практика не добавляет новых сроков или баллов.

The final exercises are lecture practice. The current assignment is Task0_Numpy. Task1_ImageProcessing follows the filtering lecture. This practice introduces no additional deadline or grading scale.
