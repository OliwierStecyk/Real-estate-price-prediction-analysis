# Real-estate-price-prediction-analysis


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
W ramach projektu przetestowano dwa algorytmy na danych surowych oraz po transformacji logarytmicznej zmiennej docelowej (ceny). Pozwoliło to sprawdzić, jak rozkład danych wpływa na różne rodziny modeli.

| Model | Wariant Danych | MSE (Mniej = Lepiej) | RMSE | R2 Score (Więcej = Lepiej) |
| :--- | :--- | :---: | :---: | :---: |
| **XGBoost** | **Dane Oryginalne** | **9.50** | **3.08** | **0.8705** 🏆 |
| Regresja Liniowa | Transformacja Log | 19.46 | 4.41 | 0.7346 |
| XGBoost | Transformacja Log | 24.99 | 5.00 | 0.6592 |
| Regresja Liniowa | Dane Oryginalne | 26.47 | 5.14 | 0.6390 |

### 📝 Analiza i Wnioski

1.  **Dominacja XGBoost:** Najlepszy uzyskany wynik to **R2 = 0.87** dla modelu XGBoost na danych oryginalnych. Błąd średni (RMSE) wynosił tylko ok. **3.08 tys. $**, co jest znaczącą poprawą względem modelu bazowego (5.14 tys. $).
2.  **Wpływ transformacji danych:**
    *   **Dla Regresji Liniowej:** Zastosowanie transformacji logarytmicznej znacznie poprawiło wynik (wzrost R2 z 0.64 na 0.73). Potwierdza to teorię, że modele liniowe działają lepiej, gdy zmienna celowa ma rozkład zbliżony do normalnego (ceny nieruchomości są naturalnie prawoskośne).
    *   **Dla XGBoost:** Transformacja nie przyniosła korzyści, a wręcz pogorszyła wynik. Wynika to z natury drzew decyzyjnych, które opierają się na progowaniu (split points) i są inwariantne na monotoniczne przekształcenia zmiennych. Najlepsze podziały zostały znalezione na danych surowych.

**Ostateczna decyzja:** Do wdrożenia rekomendowany jest model **XGBoost trenowany na danych oryginalnych**, ze względu na najwyższą predykcję i najmniejszy błąd średniokwadratowy.

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

   ```
   *Autor: Oliwier Stecyk*
   ```
