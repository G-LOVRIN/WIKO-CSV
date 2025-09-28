# WIKO CSV Files with Price Range Multipliers

Automatycznie aktualizowane dane produktów WIKO z mnożnikami bazowanymi na zakresach cenowych.

## Pliki:

### `wiko-expanded.csv` - Pełny katalog produktów dla BaseLinker
**Kolumny:** produkt_sku, nazwa, zdjecie, rozmiar, material, vat, cena_brutto, cena_zakupu_brutto, stan_magazynowy, producent, opis_tekstowy, jednostka_wymiaru, szerokosc, wysokosc, ostatnia_aktualizacja

### `wiko-stany-ceny.csv` - Stany magazynowe + ceny
**Kolumny:** produkt_sku, ilosc_wiko, nazwa_produktu, cena_brutto, cena_zakupu_brutto, ostatnia_aktualizacja

### `price_multipliers_config.json` - Konfiguracja zakresów cenowych
Definiuje mnożniki dla różnych przedziałów cenowych produktów.

### `pricing-report.txt` - Raport zakresów cenowych
Szczegółowa analiza rozkładu produktów w zakresach cenowych.

### `last-update.txt` - Informacja o ostatniej aktualizacji

## System zakresów cenowych:

| Zakres cenowy | Mnożnik | Rabat |
|---------------|---------|-------|
| 0.01 - 49.99 PLN | 0.95 | 5% |
| 50 - 99.99 PLN | 0.90 | 10% |
| 100 - 199.99 PLN | 0.85 | 15% |
| 200 - 499.99 PLN | 0.80 | 20% |
| 500 - 999.99 PLN | 0.75 | 25% |
| 1000+ PLN | 0.70 | 30% |

**Zasada:** Im wyższa cena produktu, tym większy rabat na cenie zakupu.

## Przykłady obliczania cen:

- **Produkt za 25 PLN** → cena zakupu: 23.75 PLN (rabat 5%)
- **Produkt za 75 PLN** → cena zakupu: 67.50 PLN (rabat 10%)
- **Produkt za 150 PLN** → cena zakupu: 127.50 PLN (rabat 15%)
- **Produkt za 350 PLN** → cena zakupu: 280.00 PLN (rabat 20%)
- **Produkt za 750 PLN** → cena zakupu: 562.50 PLN (rabat 25%)
- **Produkt za 1500 PLN** → cena zakupu: 1050.00 PLN (rabat 30%)

## Możliwości konfiguracji:

### Edycja zakresów cenowych:
Zmień plik `price_multipliers_config.json` aby:
- Dostosować granice zakresów cenowych
- Zmienić mnożniki dla poszczególnych zakresów
- Dodać lub usunąć zakresy
- Ustawić ograniczenia min/max mnożnika

### Niestandardowy mnożnik:
Można uruchomić workflow ręcznie z niestandardowym mnożnikiem:
1. Actions → "WIKO Parser with Price Range Multipliers"
2. Run workflow → wpisz custom multiplier (np. "0.85")
3. System zastosuje ten mnożnik do wszystkich produktów

## Bezpośrednie linki:
- **BaseLinker CSV:** https://raw.githubusercontent.com/G-LOVRIN/WIKO-CSV/main/wiko-expanded.csv
- **Stany + Ceny:** https://raw.githubusercontent.com/G-LOVRIN/WIKO-CSV/main/wiko-stany-ceny.csv
- **Konfiguracja:** https://raw.githubusercontent.com/G-LOVRIN/WIKO-CSV/main/price_multipliers_config.json
- **Raport:** https://raw.githubusercontent.com/G-LOVRIN/WIKO-CSV/main/pricing-report.txt

## Automatyzacja:
- **Codziennie o 1:00** - automatyczna aktualizacja z zakresami cenowymi
- **Ręczne uruchomienie** - możliwość zastosowania custom mnożnika
- **Monitoring** - szczegółowe raporty po każdej aktualizacji

## Analiza w raportach:
Każdy raport zawiera:
- Liczbę produktów w każdym zakresie cenowym
- Średnie ceny w zakresach
- Zastosowane rabaty/narzuty
- Łączną wartość produktów w każdym przedziale
