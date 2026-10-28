# Zakres projektu – co realnie zrobić w 2 semestry

Analiza wymagań z `Case Study.docx` (BR-01–22, NFR-01–11) oraz `Wymagania.drawio.html`.
Założenie: zespół 4–5 osób, praca obok studiów, dwa semestry.

Całego systemu z case study nie da się zrobić – to zakres na rok pracy dużego, profesjonalnego zespołu. Da się natomiast zbudować działający, uproszczony rdzeń.

## ✅ Do zrobienia w całości

| Wymaganie | Uwagi |
|---|---|
| **BR-01, BR-03** Nadanie paczki, unikalny numer, walidacja danych | Zwykły formularz i baza danych (CRUD) |
| **BR-04** Usługi dodatkowe | Jako pola i opcje; pobranie i ubezpieczenie jako atrapa, bez prawdziwych płatności |
| **BR-05** Śledzenie statusów (lista statusów z diagramu) | Rdzeń projektu; WebSocket lub SSE spokojnie daje aktualizację poniżej 10 s |
| **BR-13** Rejestracja skanów w sortowni | Prosty panel albo endpoint „zeskanuj paczkę” |
| **BR-16** Panel konsultanta z historią paczki | Widok na tych samych danych |
| **BR-17** Reklamacje | Prosty przepływ statusów: zgłoszenie → decyzja → zamknięcie |
| **NFR-07** Kolejność zdarzeń i brak duplikatów | Dobry temat techniczny: znacznik czasu, id zdarzenia, idempotencja |
| **NFR-11** Audyt zmian | Tabela z logiem zmian |
| Role i uprawnienia (część **NFR-10**) | Klient, kurier, dyspozytor, sortownia, konsultant, admin |

## 🟡 Do zrobienia w uproszczonej wersji

| Wymaganie | Wersja uproszczona |
|---|---|
| **BR-02** Import hurtowy | Import CSV/JSON z kilkoma tysiącami pozycji jako zadanie w tle (kolejka). Działa sam mechanizm, bez skali 500 tys. |
| **BR-06, BR-11** Mapa kurierów, ETA | Mapa Leaflet/OSM z pozycjami z **symulatora**; ETA liczone prosto: dystans / średnia prędkość |
| **BR-07** Powiadomienia | E-mail, ewentualnie push w przeglądarce; SMS pominąć albo zrobić jako atrapę |
| **BR-08** API dla sklepów | REST API z kluczem i webhookami – dobrze wypada na prezentacji |
| **BR-09, BR-10** Planowanie tras | Gotowa biblioteka (np. Google OR-Tools albo OSRM/VROOM) i ponowne przeliczenie na żądanie; bez pisania własnego optymalizatora |
| **BR-12** Aplikacja kuriera | PWA albo prosta aplikacja mobilna: lista zadań, potwierdzenie dostawy, zdjęcie. Tryb offline z synchronizacją jest ambitny, ale wykonalny i dobrze łączy się z NFR-07 |
| **BR-14** Panel sortowni | Liczniki paczek oczekujących; prognoza jako prosta średnia z historii |
| **BR-18, BR-19** Rozliczenia | Raport z dostarczonych paczek na kuriera i sklep, z kontrolą duplikatów |
| **BR-20** Dashboard KPI | Kilka wskaźników z wykresami |
| **NFR-01–03, NFR-05** Wydajność | Bez obietnic 48 mln zdarzeń; **test obciążeniowy** (k6 lub Locust) w zmniejszonej skali, z wynikami i wnioskami |

## ❌ Poza zasięgiem – tylko jako opis w dokumentacji

- **NFR-04, NFR-08** – dostępność 99,95%, odporność regionów, odtworzenie po awarii w 15 min: wymagają infrastruktury produkcyjnej w kilku strefach.
- **NFR-01** w pełnej skali (48 mln zdarzeń dziennie, 6000 zapytań/s): brak środowiska, na którym dałoby się to uruchomić i przetestować.
- **NFR-09** – retencja na 7 lat i archiwizacja.
- **BR-15, BR-22** – prognozy i wykrywanie zatorów z ML: bez prawdziwych danych to pusta ozdoba. Opcjonalnie na koniec, jeśli zostanie czas.
- **BR-21** – analityka z 24 miesięcy w osobnej hurtowni danych.
- Prawdziwe integracje: płatności, SMS, ruch drogowy, wielowalutowość i wiele języków.
- Pełna zgodność z RODO (procedury, prawa osób) – kontrola dostępu tak, procesy prawne nie.

## Proponowany podział na semestry

### Semestr 1 – MVP

- Nadanie paczki, statusy i zdarzenia
- Śledzenie paczki na żywo
- Panel sortowni ze skanami
- Role i uprawnienia
- Prosta aplikacja kuriera
- **Symulator zdarzeń** – generator pozycji kurierów i skanów, zastępujący sprzęt z założeń (punkt 8 case study)

### Semestr 2 – rozbudowa

- Mapa kurierów i planowanie tras
- API i webhooki dla sklepów
- Import hurtowy
- Powiadomienia
- Reklamacje
- Rozliczenia
- Dashboard KPI
- Tryb offline aplikacji kuriera
- Testy obciążeniowe
- Dokumentacja architektury: jak system skalowałby się do pełnych NFR

> **Wskazówka:** symulator zdarzeń to najważniejszy element pomocniczy. Bez niego nie ma skąd brać zdarzeń; z nim da się pokazać zarówno działanie „na żywo”, jak i wydajność.
