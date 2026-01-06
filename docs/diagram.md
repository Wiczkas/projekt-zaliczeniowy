# Diagram przepływu

```mermaid
flowchart TD
  START([Start]) --> APP[Uruchom aplikację]
  APP --> AUTH{Zalogowany?}
  AUTH -- Tak --> PANEL[Panel]
  AUTH -- Nie --> LOGIN[Logowanie / Rejestracja]
  LOGIN --> CHECK{Dane poprawne?}
  CHECK -- Tak --> PANEL
  CHECK -- Nie --> LOGIN

  PANEL --> AVAIL[Sprawdź dostępność miejsc]
  AVAIL --> FREE{Są wolne miejsca?}
  FREE -- Nie --> INFO[Komunikat: brak miejsc]
  INFO --> END([Koniec])

  FREE -- Tak --> PICK[Wybierz miejsce]
  PICK --> TIME[Wybierz czas rezerwacji]
  TIME --> CONFIRM{Miejsce nadal wolne?}
  CONFIRM -- Tak --> SAVE[Zapisz rezerwację]
  SAVE --> OK[Potwierdzenie]
  OK --> END
  CONFIRM -- Nie --> BACK[Powrót do listy]
  BACK --> AVAIL
