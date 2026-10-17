# Лекция 06 · Основы нейросетей / Lecture 06 · Neural Network Basics

Single layer → Loss function → Learn → Backpropagation → NumPy → PyTorch.

- [Практика RU/EN / Practice RU/EN](https://colab.research.google.com/github/alexander-toschev/cv-course/blob/main/Lectures/06_NeuralNetworkBasics/Practice_RU_EN.ipynb): 8 тем, после каждой мини-задание на 5–10 минут / eight topics with a 5–10 minute mini-task after each.
- [ДЗ 06 RU/EN / Homework 06 RU/EN](https://colab.research.google.com/github/alexander-toschev/cv-course/blob/main/Lectures/06_NeuralNetworkBasics/Homework_RU_EN.ipynb): NN-06, 100 исходных баллов / raw points.
- [Презентации и видео RU/EN / Slides and narrated videos RU/EN](https://drive.google.com/drive/folders/17I7napof99mLcIdW9xF3M5DbYdVPtncQ): 20 слайдов на язык / slides per language; RU 14:02, EN 13:44.
- [Сроки по группам / Group deadlines](https://docs.google.com/spreadsheets/d/15N5GGHujXPAzRNuyOfmooT7A7sKhXgrMfWHkUkvYYiM/edit): ДЗ 06, столбец G. Дату назначает преподаватель / instructor sets the date.

Данные: UCI Optical Recognition of Handwritten Digits, Alpaydin & Kaynak (1998), [DOI](https://doi.org/10.24432/C50P49), CC BY 4.0. `sklearn.datasets.load_digits`: 1 797 реальных изображений 8×8; признаки — 64 числа 0…16; цель — цифра 0…9. / Real 8×8 digit images, 64 features in 0…16, target digit 0…9.

Учебное разбиение 1078/359/360, seed 606. Исходный loader содержит тестовую часть UCI, которую здесь повторно делим; это не официальный benchmark. Идентификаторы авторов недоступны, независимость почерков не гарантируется. Test открывается после выбора модели. / Teaching split, not the official benchmark; writer independence is not established. Open test only after model selection.

ДЗ: stable loss 20, forward 20, backward 30, SGD 10, validation selection and controlled experiment 20. Содержательные выводы проверяет преподаватель. JSON содержит исходный балл; штрафы за срок и практику применяются внешним проверяющим. / Instructor reviews substantive conclusions; raw JSON is provisional, lateness and practice are applied externally.

Переиспользовано: тематика и последовательность старого курса, NumPy/Keras и ReLU/Sigmoid из `Archive/NN_withNumpyAndKeras.ipynb`. Обновлено: реальные данные вместо синтетических, многоклассовый устойчивый loss, проверка градиентов, PyTorch и явный validation/test-протокол. / Reused original concepts and sequence; updated real-data experiment, stable multiclass loss, gradient verification, PyTorch and split protocol.

Озвучка этого выпуска: локальные синтетические голоса Milena (RU), Daniel (EN), поскольку ElevenLabs недоступен 17.10.2026. Без добавленных пауз и растягивания. / This release uses local synthetic narration because ElevenLabs was unavailable; no added exercise pauses or artificial duration padding.

Проверено на CPU: полный запуск практики, эталон 100, пустое решение 0; пять ошибочных реализаций теряют соответствующие баллы. / CPU validation: full practice run, reference 100, blank 0, five defective implementations rejected by the corresponding checks.
