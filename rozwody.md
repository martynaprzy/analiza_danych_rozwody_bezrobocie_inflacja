# Projekt Zaliczeniowy: Analiza wpływu sytuacji gospodarczej na liczbę rozwodów w Polsce

## 1. Definicja problemu
Celem projektu jest zbadanie zależności między kondycją polskiej gospodarki a liczbą orzekanych rozwodów.
Decyzja o zakończeniu małżeństwa jest złożona, jednak czynniki ekonomiczne (stres finansowy, bezrobocie, inflacja)
mogą być istotnym katalizatorem rozpadu pożycia.
**Hipoteza:** Pogorszenie wskaźników makroekonomicznych wpływa na wzrost liczby rozwodów z opóźnieniem czasowym.

### Dlaczego ten problem?
W literaturze socjologicznej i ekonomicznej często stawia się pytanie: czy kryzysy gospodarcze cementują
rodziny (wspólne przetrwanie trudności), czy je niszczą (stres, kłótnie o pieniądze)?
Analiza danych historycznych pozwoli nam odpowiedzieć na to pytanie w kontekście Polski.

### Hipoteza badawcza
**"Pogorszenie wskaźników makroekonomicznych (wzrost stopy bezrobocia, wzrost inflacji) wpływa na wzrost liczby rozwodów z zauważalnym opóźnieniem czasowym."**

Zakładamy, że efekt nie jest natychmiastowy – utrata pracy lub inflacja generują napięcia,
które dopiero po pewnym czasie (np. roku lub dwóch) prowadzą do finalizacji rozwodu w sądzie.
Dlatego do weryfikacji tej hipotezy użyjemy modelu **VAR (Vector Autoregression)** oraz analizy
**IRF (Impulse Response Function)**, co pozwoli zmierzyć reakcję zmiennej `rozwody` na impuls (szok)
ze zmiennej `bezrobocie`.

Dane pochodzą z: https://bdl.stat.gov.pl/

## Dane
Analizę przeprowadzono na danych rocznych z **GUS (Bank Danych Lokalnych)** za lata **2004–2024**.
* **Zmienna celu:** Liczba rozwodów (ogółem).
* **Zmienne objaśniające:** Stopa bezrobocia rejestrowanego (%) oraz Inflacja CPI (r/r).

## Metodologia
Wykorzystano model wektorowej autoregresji (**VAR**) do badania dwukierunkowych zależności między zmiennymi.
* **Stacjonarność:** Test Dickeya-Fullera (ADF) wykazał niestacjonarność zmiennych, dlatego zastosowano **pierwsze różnicowanie** (analiza zmian rok-do-roku).
* **Opóźnienia:** Model, na podstawie kryterium AIC, dobrał rząd opóźnień **3 lata**. Oznacza to, że decyzje rozwodowe reagują na szoki gospodarcze w długim horyzoncie czasowym.

## Kluczowe wnioski
* **Reakcja na impuls (IRF):** Szok w postaci nagłego wzrostu bezrobocia lub inflacji wywołuje **falową reakcję** w liczbie rozwodów. Nie jest to prosta zależność liniowa, lecz proces destabilizacji trwający ok. 3–5 lat od wystąpienia szoku.
* **Opóźniony zapłon:** Problemy ekonomiczne nie niszczą małżeństw natychmiast – stres finansowy kumuluje się przez lata.

## Walidacja modelu
Model charakteryzuje się bardzo wysoką precyzją dopasowania:
* **MAE (Średni błąd bezwzględny):** ok. 1631 rozwodów.
* **Błąd względny:** 2.6% (w stosunku do średniej liczby rozwodów).
Wniosek: Zmienne makroekonomiczne są silnym predyktorem dynamiki rozwodów w Polsce.