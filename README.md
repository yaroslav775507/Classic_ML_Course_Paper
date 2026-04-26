# Predicting

Курсовая по МО — предсказание активности соединений против гриппа.

## Данные

1001 соединение, 210 молекулярных дескрипторов, три таргета: IC50, CC50, SI.

## Структура

```
├── data/
│   └── data.xlsx
├── plots/
├── 01_EDA.ipynb
├── 02_regression_IC50.ipynb
├── 03_regression_CC50.ipynb
├── 04_regression_SI.ipynb
├── 05_classification_IC50.ipynb
├── 06_classification_CC50.ipynb
├── 07_classification_SI_median.ipynb
├── 08_classification_SI_gt8.ipynb
└── report_gost.docx
```

## Что делал

Сначала посмотрел на данные — там всё сильно скошено, пришлось логарифмировать таргеты. Часть признаков оказалась константами, выкинул их. NaN заполнил медианой.

Попробовал линейные модели — Ridge, Lasso, ElasticNet — показали себя слабо, R² местами отрицательный. Ансамбли (RF, GB) справились заметно лучше, особенно после GridSearchCV.

Для классификации SI > 8 добавил SMOTE, потому что там дисбаланс ~64/36.

## Зависимости

```
pip install pandas numpy scikit-learn matplotlib seaborn imbalanced-learn openpyxl
```

## Запуск

Ноутбуки запускать по порядку из корня проекта. Файл с данными должен лежать в `data/data.xlsx`.
