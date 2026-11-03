# Podział zadań (wg ról / kolorów z legendy)

Kolory odpowiadają kropkom w prawym górnym rogu bloków w `architektura.drawio`.

| Rola (kolor) | Zadania |
|---|---|
| 🟡 **Backend / obsługa eventów** | **Mikroserwisy:** Serwis Klienta, Serwis Kuriera, Serwis dystrybuowania dostaw, Notification Service, Courier Localization Service, Access Control Service, Authentication, Authorization<br>**SBA:** PU-1…N, Processing grid, Central Server |
| 🔵 **Baza / dane + obsługa błędów bazodanowych** | **Mikroserwisy:** DB (Źródło prawdy), Cache, DB (klient), DB (kurier), Audit Log store, Analytics / Telemetry, SQLite (klient), SQLite (kurier), Sync Service, Audit Log Service<br>**SBA:** DB, Data feed grid, Data sync grid, Telemetry Service |
| 🔴 **API / Gateway i broker** | **Mikroserwisy:** API Gateway (klient), API Gateway (kurier), Message Broker, B2B API + Webhook Service<br>**SBA:** Message grid, Sending Service, Receiver |
| 🟣 **UI / UX** | **Mikroserwisy:** Klient App (+ strony), Kurier App (+ strony)<br>**SBA:** Telemetry Window |

## Legenda kolorów

| Kolor | Hex | Znaczenie |
|---|---|---|
| 🟡 Żółty | `#FFD966` | Backend — obsługa eventów |
| 🔵 Niebieski | `#1976D2` | Baza — dane + obsługa błędów bazodanowych |
| 🔴 Czerwony | `#E53935` | API / Gateway i broker |
| 🟣 Fiolet | `#8E24AA` | UI / UX |
