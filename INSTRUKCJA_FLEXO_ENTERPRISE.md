# 🏭 Flexo PRO Enterprise - Instrukcja Obsługi

## Spis Treści
1. [Wprowadzenie](#wprowadzenie)
2. [Uruchomienie](#uruchomienie)
3. [Import Danych](#import-danych)
4. [Widoki i Funkcje](#widoki-i-funkcje)
5. [Parser Emaili](#parser-emaili)
6. [FAQ i Rozwiązywanie Problemów](#faq)

---

## Wprowadzenie

**Flexo PRO Enterprise** to zaawansowany system zarządzania produkcją dla całej firmy, obsługujący **10 maszyn** i **4 brygady**.

### Funkcjonalności:
- ✅ Inteligentny parser emaili od brygadzistów
- ✅ Zarządzanie 10 maszynami (M1-M6, Soma 1-3, Novoflex 1)
- ✅ 4 brygady z automatycznymi harmonogramami
- ✅ Dashboard z KPI i statystykami
- ✅ Raporty i analizy
- ✅ Przechowywanie danych w przeglądarce (localStorage)
- ✅ Responsywny design (działa na telefonie)
- ✅ Tryb ciemny/jasny

---

## Uruchomienie

### Metoda 1: Bezpośrednio w przeglądarce
1. Otwórz plik `flexo-enterprise.html` w przeglądarce Chrome/Firefox/Edge
2. Aplikacja załaduje się automatycznie
3. Gotowe! 🎉

### Metoda 2: Lokalny serwer (opcjonalnie)
```bash
cd /home/user/produkcja
python3 -m http.server 8000
```
Następnie otwórz: http://localhost:8000/flexo-enterprise.html

---

## Import Danych

### Krok po kroku:

#### 1. Otrzymaj email od brygadzisty
Email zawiera dane w formacie:
```
Data: 20.11.2025
Zmiana: 1
Brygada: MICHALAK
Ilość pracowników: 17

M1: Zadrukowano: 1245, Pobrano: 875, Zlecenia: 2, Klient: valsemolen
M2: Zadrukowano: 1204, Pobrano: 1263, Zlecenia: 2, Klient: tienen
...
```

#### 2. Skopiuj cały email
- Zaznacz cały tekst emaila
- Naciśnij **Ctrl+C** (lub Cmd+C na Mac)

#### 3. Przejdź do zakładki "📝 Import Danych"
- Kliknij na zakładkę "Import Danych" w górnym menu

#### 4. Wklej dane
- Kliknij w duże pole tekstowe
- Naciśnij **Ctrl+V** (lub Cmd+V na Mac)

#### 5. Parsuj dane
- Kliknij przycisk **"🔍 Parsuj dane"**
- Aplikacja automatycznie wyciągnie wszystkie wartości

#### 6. Sprawdź i popraw
- **Parser** wypełnił wszystkie pola automatycznie
- **Sprawdź** każdą wartość
- **Popraw** jeśli coś jest źle (czerwone pola = błąd)

#### 7. Zapisz
- Kliknij **"✅ Zatwierdź i zapisz"**
- Dane zapisane! ✅

---

## Widoki i Funkcje

### 📊 Dashboard
**Funkcje:**
- KPI miesiąca (suma zadruku, pobrane, zlecenia, odpady)
- Top 3 maszyny 🏆
- Podsumowanie dla aktywnych brygad
- Prognoza miesięczna

**Kiedy używać:**
Szybki przegląd stanu produkcji

---

### 📝 Import Danych
**Funkcje:**
- Wklejanie emaili od brygadzistów
- Automatyczne parsowanie danych
- Edycja przed zapisem
- Walidacja wartości

**Kiedy używać:**
Gdy otrzymasz email z danymi produkcyjnymi

---

### 📈 Raport Produkcji
**Funkcje:**
- Tabelaryczny widok wszystkich wpisów
- Filtrowanie po miesiącu
- Wszystkie maszyny w jednej tabeli
- Przycisk "Szczegóły" dla każdego wpisu

**Kiedy używać:**
Przeglądanie historycznych danych, kontrola jakości

**Nawigacja:**
- **◀ / ▶** - przełączanie miesięcy
- **👁️ Szczegóły** - pokaż pełne informacje o wpisie

---

### 🏭 Maszyny
**Funkcje:**
- 10 podzakładek (jedna dla każdej maszyny)
- Kalendarz produkcji tylko dla "Zadrukowano"
- Statystyki: suma, średnia, dni pracy
- Historia produkcji

**Jak używać:**
1. Kliknij zakładkę "🏭 Maszyny"
2. Wybierz maszynę z menu (M1, M2, M3... Soma 1... Novoflex 1)
3. Zobacz kalendarz produkcji dla tej maszyny

**Co widzisz:**
- Data
- Brygada (z kolorowym paskiem)
- Zmiana (☀️ rano / 🌆 popołudnie / 🌙 noc)
- Zadrukowano (kg)
- Zlecenia
- Klient

---

### 📦 Suma
**Funkcje:**
- Agregacja ze WSZYSTKICH maszyn
- Suma zadruku, pobrane, zlecenia
- Ranking maszyn (% udziału)
- Porównanie brygad
- Średnia na wpis

**Kiedy używać:**
Analiza całościowa firmy, porównania między maszynami

**Co pokazuje:**
- **Suma według maszyn** - która maszyna produkuje najwięcej
- **Suma według brygad** - która brygada najbardziej efektywna

---

### 🔍 Analityka
**Status:** 🚧 W budowie

**Planowane funkcje:**
- Wykresy trendów
- Analiza efektywności
- Częstotliwość awarii
- Analiza odpadów

---

## Parser Emaili

### Jak działa parser?

Parser to **inteligentny algorytm**, który automatycznie rozpoznaje strukturę emaila i wyciąga dane.

#### Rozpoznawane sekcje:

1. **Nagłówek**
   - Data: `DD.MM.YYYY`
   - Zmiana: `1`, `2`, lub `3`
   - Brygada: `MICHALAK`, `GAJDA`, `WRONKA`, `SMANDZIK`
   - Ilość pracowników: liczba

2. **Dane maszyn** (dla każdej z 10 maszyn)
   - Zadrukowano (kg)
   - Pobrano (kg)
   - Ilość zleceń
   - Klient

3. **Odpady** (3 kategorie)
   - Papier biały
   - PE/folia
   - Opakowanie szare/papier szary

4. **Adnotacje**
   - Awarie
   - Problemy
   - Uwagi

5. **Nieobecności**
   - Lista nieobecnych pracowników

### Format wejściowy

Parser jest **elastyczny** i radzi sobie z różnymi formatami:

#### Format 1: Szczegółowy
```
M1
Zadrukowano: 1245
Pobrano: 875
Ilość zleceń: 2
Klient: valsemolen
```

#### Format 2: Zwięzły
```
M1: Zadrukowano: 1245, Pobrano: 875, Zlecenia: 2, Klient: valsemolen
```

#### Format 3: Bez etykiet (parser użyje kolejności)
```
M1: 1245, 875, 2, valsemolen
```

### Co jeśli parser się pomyli?

**Nie ma problemu!** Po parsowaniu:
1. Wszystkie pola są **edytowalne**
2. Możesz **poprawić** każdą wartość
3. Aplikacja **nie zapisze** dopóki nie klikniesz "Zatwierdź"

---

## Harmonogramy Brygad

### Automatyczne obliczanie zmian

Aplikacja **automatycznie** wie, która brygada pracuje w danym dniu!

**Cykl zmianowy** (16 dni):
```
[1, 1, 1, 1, 0, 3, 3, 3, 3, 0, 0, 2, 2, 2, 2, 0]

1 = Rano ☀️
2 = Popołudnie 🌆
3 = Noc 🌙
0 = Wolne 🏠
```

### Daty startu brygad:

| Brygada | Data startu | Odniesienie |
|---------|-------------|-------------|
| **MICHALAK** | 2025-01-04 | Jak Kamil |
| **GAJDA** | 2025-01-16 | Jak Igor |
| **WRONKA** | 2025-01-08 | Jak Wowa |
| **SMANDZIK** | 2025-01-12 | Jak Jarek |

### Kolory brygad:

- 🟢 **MICHALAK** - zielony (`#7bed9f`)
- 🟠 **GAJDA** - pomarańczowy (`#ffa502`)
- 🔴 **WRONKA** - czerwony (`#ff6348`)
- 🔵 **SMANDZIK** - niebieski (`#70a1ff`)

---

## Struktura Danych

### LocalStorage

Wszystkie dane zapisywane są w przeglądarce w formacie JSON.

**Klucz zapisu:**
```
{data}-{zmiana}-{brygada}
Przykład: 2025-11-20-1-MICHALAK
```

**Struktura pojedynczego wpisu:**
```javascript
{
  "date": "2025-11-20",
  "shift": 1,
  "brigade": "MICHALAK",
  "workers": 17,
  "machines": {
    "M1": {
      "zadrukowano": 1245,
      "pobrano": 875,
      "zlecenia": 2,
      "klient": "valsemolen"
    },
    "M2": { ... },
    ...
  },
  "waste": {
    "M1": {
      "bialy": 139,
      "folia": 0,
      "szary": 6
    },
    ...
  },
  "notes": "Przelaczanie zasilania M3...",
  "timestamp": "2025-11-20T14:30:00.000Z"
}
```

### Backup danych

**Eksport:** (planowane)
```
Ustawienia → Eksport danych → Pobierz JSON
```

**Import:** (planowane)
```
Ustawienia → Import danych → Wybierz plik JSON
```

---

## FAQ

### ❓ Czy mogę używać aplikacji offline?
✅ **TAK!** Aplikacja działa w 100% offline. Dane przechowywane są w przeglądarce.

### ❓ Co się stanie jeśli zamknę przeglądarkę?
✅ **Nic!** Wszystkie dane są zapisane w localStorage i pozostaną nawet po zamknięciu.

### ❓ Czy mogę używać na telefonie?
✅ **TAK!** Aplikacja jest w pełni responsywna i działa na mobile.

### ❓ Parser źle odczytał dane. Co robić?
✅ Po kliknięciu "Parsuj", **WSZYSTKIE** pola są edytowalne. Po prostu popraw wartości ręcznie.

### ❓ Jak usunąć błędny wpis?
⚠️ Funkcja usuwania jest w budowie. Na razie możesz:
1. Otworzyć DevTools (F12)
2. Console → wpisać: `localStorage.clear()` (usuwa WSZYSTKIE dane)

### ❓ Czy dane są synchronizowane między przeglądarkami?
❌ **NIE.** Obecnie każda przeglądarka ma swoje własne dane (localStorage jest per-przeglądarka).

**Rozwiązanie:** W przyszłości dodamy Firebase sync (tak jak w poprzedniej aplikacji).

### ❓ Mogę mieć duplikaty wpisów?
⚠️ **TAK**, ale klucz zapisu to `{data}-{zmiana}-{brygada}`, więc jeśli zapiszesz dwa razy te same dane, **nadpiszą** się.

### ❓ Parser nie rozpoznał maszyny "SOMA 1"
🔧 **Możliwe przyczyny:**
- W emailu brakuje danych dla tej maszyny
- Format jest niestandardowy

**Rozwiązanie:** Po parsowaniu ręcznie uzupełnij pola dla tej maszyny.

### ❓ Jak zmienić datę startu brygady?
📝 Edytuj plik `flexo-enterprise.html`, sekcja:
```javascript
brigades: {
  'MICHALAK': { startDate: '2025-01-04', ... },
  ...
}
```

### ❓ Jak dodać nową maszynę?
📝 Edytuj plik `flexo-enterprise.html`, sekcja:
```javascript
machines: ['M1', 'M2', ..., 'TWOJA_NOWA_MASZYNA']
```

---

## Rozwiązywanie Problemów

### Problem: Parser nie wyciąga żadnych danych
**Sprawdź:**
1. Czy email zawiera słowa kluczowe: "Data", "Zmiana", "Brygada"?
2. Czy format daty to `DD.MM.YYYY`?
3. Otwórz DevTools (F12) → Console → sprawdź błędy

**Rozwiązanie:**
- Spróbuj ręcznie wypełnić pola
- Wyślij mi przykładowy email (maskując dane wrażliwe)

### Problem: Aplikacja nie zapisuje danych
**Sprawdź:**
1. Czy localStorage jest włączony w przeglądarce?
2. Czy masz wystarczająco miejsca (localStorage max ~5-10 MB)?
3. Otwórz DevTools → Application → Local Storage

**Rozwiązanie:**
- Wyczyść stare dane: `localStorage.clear()`
- Spróbuj innej przeglądarki

### Problem: Widzę błąd "Quota exceeded"
**Przyczyna:** localStorage jest pełny (max 5-10 MB)

**Rozwiązanie:**
1. Eksportuj dane (jeśli masz dużo)
2. Wyczyść: `localStorage.clear()`
3. Zaimportuj z powrotem tylko potrzebne dane

### Problem: Nie widzę żadnych danych w Dashboard
**Przyczyna:** Brak danych dla bieżącego miesiąca

**Rozwiązanie:**
- Zaimportuj dane dla obecnego miesiąca
- Lub zmień miesiąc w Raporcie/Sumie

---

## Skróty Klawiszowe

| Skrót | Akcja |
|-------|-------|
| `Ctrl+V` | Wklej email w polu Import |
| `Enter` | Zatwierdź (w niektórych polach) |
| `F12` | Otwórz DevTools |
| `Ctrl+Shift+I` | Otwórz DevTools (alternatywnie) |

---

## Testowanie z Przykładowymi Danymi

Plik `test-email-data.txt` zawiera przykładowe dane z Twojego emaila.

**Jak przetestować:**
1. Otwórz plik `test-email-data.txt`
2. Zaznacz cały tekst (`Ctrl+A`)
3. Skopiuj (`Ctrl+C`)
4. Otwórz aplikację → Import Danych
5. Wklej (`Ctrl+V`)
6. Kliknij "Parsuj"
7. Sprawdź czy wszystkie wartości są poprawne!

---

## Roadmapa (Przyszłe Funkcje)

### v2.0 (planowane)
- [ ] Firebase sync (synchronizacja między urządzeniami)
- [ ] Eksport/Import danych (JSON, Excel)
- [ ] Generowanie raportów PDF
- [ ] Edycja i usuwanie wpisów
- [ ] Wykresy w Analytics (Chart.js)
- [ ] Powiadomienia o brakujących wpisach
- [ ] Konfiguracja maszyn i brygad przez UI
- [ ] Cele produkcyjne dla brygad/maszyn
- [ ] Analiza efektywności w czasie rzeczywistym

### v3.0 (future)
- [ ] Wersja PWA (Progressive Web App)
- [ ] Praca offline z sync po powrocie online
- [ ] Multi-user (różne role: admin, kierownik, brygadzista)
- [ ] API dla integracji z innymi systemami
- [ ] Automatyczne emaile z raportami
- [ ] Machine Learning dla predykcji awarii

---

## Kontakt i Wsparcie

**GitHub Issues:**
- Zgłoś błąd
- Zaproponuj funkcję
- Zadaj pytanie

**Email:** (uzupełnij)

---

## Licencja

© 2025 Flexo PRO Enterprise
Użytek wewnętrzny dla firmy.

---

**Wersja aplikacji:** v1.0.0
**Data aktualizacji instrukcji:** 2025-11-20

---

# 🎉 Miłego użytkowania!

**Wskazówki:**
- Zapisuj dane regularnie
- Sprawdzaj Dashboard codziennie
- Używaj widoku "Suma" do analiz miesięcznych
- Zgłaszaj problemy jak najszybciej

**Pytania? Problemy? Sugestie?**
Skontaktuj się z administratorem systemu.
