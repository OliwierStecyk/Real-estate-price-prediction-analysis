# Real-estate-price-prediction-analysis

```markdown
# 🏠 Przewidywanie cen nieruchomości: Regresja Liniowa vs XGBoost

Projekt analityczny porównujący skuteczność klasycznych metod statystycznych oraz nowoczesnych algorytmów uczenia maszynowego w zadaniu wyceny nieruchomości (zbiór danych Boston Housing).

## 📋 O projekcie
Celem projektu było zbudowanie modelu predykcyjnego, który na podstawie szeregu cech (np. liczba pokoi, przestępczość w okolicy, dostępność infrastruktury) oszacuje wartość rynkową nieruchomości.

Projekt stanowi część pracy inżynierskiej i kładzie duży nacisk na:
*   Rygorystyczną analizę statystyczną (badanie współliniowości).
*   Świadomy dobór cech.
*   Optymalizację hiperparametrów.

## 🛠️ Wykorzystane technologie
*   **Python** (analiza danych)
*   **Pandas / NumPy** (manipulacja danymi)
*   **Scikit-Learn** (Regresja Liniowa, GridSearchCV, metryki)
*   **XGBoost** (zaawansowany model gradient boosting)
*   **Statsmodels** (analiza VIF)
*   **Matplotlib / Seaborn** (wizualizacja danych)

## ⚙️ Metodologia (Workflow)

### 1. Eksploracyjna Analiza Danych (EDA)
*   Analiza rozkładów zmiennych.
*   Badanie korelacji (mapa ciepła) w celu wstępnej identyfikacji zależności.

### 2. Selekcja Cech i Eliminacja Multikolinearności (VIF)
Zastosowano analizę **VIF (Variance Inflation Factor)** w celu wykrycia zmiennych silnie skorelowanych ze sobą (multikolinearność), co mogłoby zaburzyć stabilność modelu regresji.
*   Zidentyfikowano zmienne o VIF > 5.
*   Iteracyjnie usunięto zmienne powodujące szum informacyjny, co poprawiło interpretowalność modelu.

### 3. Modelowanie
Zastosowano podejście porównawcze:
*   **Model Bazowy (Baseline):** Regresja Liniowa (OLS). Służy jako punkt odniesienia dla bardziej złożonych metod.
*   **Model Docelowy:** XGBoost Regressor. Algorytm oparty na drzewach decyzyjnych i wzmocnieniu gradientowym.

### 4. Optymalizacja (GridSearchCV)
Dla modelu XGBoost przeprowadzono strojenie hiperparametrów przy użyciu przeszukiwania siatką (Grid Search) z walidacją krzyżową (Cross-Validation). Optymalizowano parametry takie jak:
*   `learning_rate`
*   `max_depth`
*   `n_estimators`
*   `colsample_bytree`

## 📊 Wyniki
Porównanie skuteczności modeli na zbiorze testowym:

| Metryka | Regresja Liniowa (Baseline) | XGBoost (Po tuningu) |
| :--- | :---: | :---: |
| **R2 Score** | [WPISZ WYNIK, np. 0.71] | **[WPISZ WYNIK, np. 0.89]** |
| **MSE** (Błąd średniokwadratowy) | [WPISZ WYNIK] | **[WPISZ WYNIK]** |

> **Wniosek:** Model XGBoost osiągnął znacząco lepsze wyniki, redukując błąd predykcji i lepiej odwzorowując nieliniowe zależności w danych.

## 🚀 Jak uruchomić projekt?

1. Sklonuj repozytorium:
   ```bash
   git clone https://github.com/TWOJA-NAZWA-UZYTKOWNIKA/real-estate-price-prediction-analysis.git
   ```
2. Zainstaluj wymagane biblioteki:
   ```bash
   pip install pandas numpy scikit-learn xgboost statsmodels matplotlib seaborn
   ```
3. Uruchom notatnik Jupyter/Colab:
   `Analiza_Boston_Housing.ipynb`

---
*Autor: [Twoje Imię i Nazwisko]*
```
