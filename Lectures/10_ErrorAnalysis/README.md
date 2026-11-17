# 10 · Анализ ошибок и различия dev/test / Error analysis and distribution mismatch

- [Практика RU/EN / Practice RU/EN](Practice_RU_EN.ipynb) · четыре задания по 5–10 минут / four 5–10 minute exercises.
- [ДЗ №10 RU/EN / Homework 10 RU/EN](Homework_RU_EN.ipynb) · **ERR-10**, 4 × 25 = 100.
- [Презентации и сценарии RU/EN / Slides and scripts RU/EN](https://drive.google.com/drive/folders/1104cKQeEH3Y9f8f75oDU7pKP28fIS7Xh).
- Видеолекция / Narrated video: [RU · 30:28](https://drive.google.com/file/d/1ogCVwR_DZh9MNHA1PzjlMiu2oSF3xYCL/view) · [EN · 30:01](https://drive.google.com/file/d/1NmQHTWPN6Ok95sT-kMZA6CEI-I32vkIE/view). Full HD, 37 chapters, ElevenLabs.

## Запуск / Run
Open either notebook in Colab and run top to bottom on CPU. Python, NumPy, pandas, scikit-learn, matplotlib. The notebook downloads the official UCI ZIP once and verifies SHA-256. No Google authentication or writes. / Откройте в Colab, выполняйте сверху вниз на CPU. Архив UCI скачивается один раз с проверкой SHA-256. Авторизация Google и запись оценок из ноутбука не требуются.

[Практика в Colab](https://colab.research.google.com/github/alexander-toschev/cv-course/blob/main/Lectures/10_ErrorAnalysis/Practice_RU_EN.ipynb) · [ДЗ в Colab](https://colab.research.google.com/github/alexander-toschev/cv-course/blob/main/Lectures/10_ErrorAnalysis/Homework_RU_EN.ipynb)

## Данные и протокол / Data and protocol
UCI Optical Recognition of Handwritten Digits, Alpaydin & Kaynak, DOI 10.24432/C50P49, CC BY 4.0. [Official source](https://archive.ics.uci.edu/dataset/80/optical+recognition+of+handwritten+digits). Real 8×8 handwriting, 64 values in 0…16, digit label 0…9. Official source train: 3823 images from 30 writers; official target test: 1797 images from 13 different writers. Source split 3058/765; target split 898/899; seed1010, stratified by digit. The teaching protocol repurposes official test into dev/test and is NOT a standard UCI benchmark. Writer IDs are unavailable within CSV, so target dev/test are not claimed writer-disjoint. No synthetic observations. / Реальные цифры; исходный test переиспользован для учебного dev/test, стандартный benchmark не заявляется. Разделение target по авторам не гарантируется.

## Сдача / Submission
Fill name/group, implement all four functions, Restart & Run All, save .ipynb and submit to the course folder. Deadline comes from the group matrix, not this README; practice №10 maps to ERR-10. The checker reruns solutions and the instructor applies lateness and practice penalties. / Заполните имя/группу, реализуйте функции, перезапустите и выполните весь ноутбук. Срок — из матрицы группы, практика №10 соответствует ERR-10. Преподаватель применяет штрафы после независимой проверки.

Instructor answers are stored only in private Google Drive. / Решения преподавателя находятся только в закрытом Google Drive.

## Источники курса / Course provenance
Retains error analysis, bias/variance and mismatch from the course plan and archived Task4_ErrorEstimation / Task5_Invariant. New ERR-10 is a separate 100-point contract; archived IDs and files remain unchanged. Updated: explicit source/target partitions, audit IDs, uncertainty, consistent checks, no demand that augmentation must win. / Сохранены темы исходного курса, старые задания остаются в Archive; новое ДЗ имеет отдельный контракт ERR-10.
