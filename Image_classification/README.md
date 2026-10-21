# MNIST: MLP i CNN

Główny notebook: **MNIST_MLP_CNN.ipynb**. Opisy i interpretacje są po polsku.

## Uruchomienie

1. Otwórz notebook w Jupyter, VS Code lub Google Colab.
2. Zainstaluj pakiety z `requirements.txt` (lub odkomentuj komórkę `%pip install` i zrestartuj kernel).
3. Wybierz kernel środowiska z TensorFlow i Optuną.
4. Uruchom wszystkie komórki od góry. Domyślne ustawienie `PROFILE="full"` wykonuje pełny eksperyment; przy pierwszym użyciu Keras pobierze MNIST.

Lokalnie przygotowano środowisko `Image_classification/.venv`. Można wskazać jego interpreter jako kernel w VS Code. Dla pełnego treningu zalecane jest GPU; czas zależy od sprzętu. Brak GPU nie uniemożliwia działania.

## Zawartość

- MNIST z Keras, przykładowe cyfry, skalowanie do [0,1], one-hot.
- Wspólny, stratyfikowany podział 50 000 trening / 10 000 walidacja / 10 000 test.
- MLP bazowy i 12 prób Optuny.
- CNN bazowa oraz porównanie 2 i 4 warstw splotowych z GlorotUniform i HeUniform dla trzech ziaren.
- 20 prób Optuny dla CNN, z Dropout, BatchNorm i augmentacją, oraz powtórzenia zwycięskiej konfiguracji.
- Końcowe accuracy, cross-entropy, macro-F1, przedziały Wilsona, liczba parametrów i czas treningu.
- Predykcje, macierz pomyłek, błędy o dużej pewności, mapy cech, intuicyjne wyjaśnienie MLP/CNN.

Modele `.keras`, CSV, konfiguracja i historie zapisywane są w `wyniki_mnist/<profil>/` względem katalogu uruchomienia. Aby powtórzyć eksperyment bez nadpisania, skopiuj poprzedni katalog wyników.

## Weryfikacja

Profil `smoke` używa 2000 przykładów treningowych, 1000 walidacyjnych, 2 epok, po 2 prób Optuny i jednego ziarna; test nadal zawiera 10 000 obrazów. Służy wyłącznie do weryfikacji technicznej. Wszystkie 13 komórek kodu przeszło kontrolę bez błędów; wygenerowano 11 wykresów. Wersja `MNIST_MLP_CNN_smoke.ipynb` zawiera wykonane komórki i wyniki tej kontroli. Wersje bibliotek zapisano w `requirements-tested.txt`. Pełne wyniki jakościowe wymagają uruchomienia głównego notebooka w profilu `full`.
