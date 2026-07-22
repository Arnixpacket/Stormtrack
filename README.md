# STORMWATCH · Śledzenie bojowe

Aplikacja w przeglądarce do używania **w aucie**. Bierze Twoją pozycję GPS na żywo,
namierza komórki burzowe na radarze (RainViewer), liczy ich wektor ruchu i przewiduje:
**czy komórka w Ciebie uderzy, za ile minut i z jaką siłą**. Alarm tylko gdy burza
realnie się zbliża — nie przy każdym echu, które akurat oddala się w drugą stronę.

## Co robi

- **INICJALIZACJA ŚLEDZENIA** — ekran startowy z animacją, potem prosi o zgodę na GPS
- **Scope** — okrągły radar, Ty na środku, echa wokół w promieniu 150 km
- **Werdykt** na żywo:
  - `CZYSTO` — nic w zasięgu
  - `ODDALA SIĘ` — komórka jest, ale ucieka — brak alarmu
  - `ZBLIŻA SIĘ` / `OTRZE SIĘ` — idzie w Twoją stronę, ale prawdopodobnie minie
  - `UDERZENIE` — realne zagrożenie, z odliczaniem `T-XX MIN` i siłą (ulewa / silna burza / możliwy grad / grad-nawałnica)
- **Syrena + wibracje** na telefonie przy `UDERZENIE`
- **Push na ntfy** (ten sam kanał co reszta STORMWATCH) przy zbliżającej się burzy

## Włączenie — krok po kroku

### 1. Załóż publiczne repozytorium
Na github.com → **New repository** → nazwa np. `tracker` → zaznacz **Public**
(GitHub Pages na darmowym koncie działa tylko na publicznych repo) → **Create repository**.

### 2. Wrzuć plik
W repo → **Add file → Upload files** → przeciągnij `tracker.html` → **Commit changes**.

### 3. Włącz GitHub Pages
W repo → **Settings → Pages** (menu z lewej) → sekcja **Build and deployment**:
- Source: **Deploy from a branch**
- Branch: **main**, folder **/ (root)**
→ **Save**.

Odczekaj ~1-2 minuty. Odśwież tę stronę (Settings → Pages) — na górze pojawi się
zielony pasek z adresem, coś w stylu:
```
https://TWOJ_LOGIN.github.io/tracker/tracker.html
```

### 4. Dodaj do ekranu głównego telefonu
Otwórz ten adres w **Chrome** na telefonie → menu (⋮) → **Dodaj do ekranu głównego**.
Od teraz masz ikonkę jak zwykła aplikacja.

### 5. Odpal w aucie
Tapnij ikonkę → **▶ INICJALIZACJA ŚLEDZENIA** → zgódź się na lokalizację.
Trzymaj ekran włączony (blokada wygaszania włącza się sama) — i jedź.

## Ważne, żeby wiedzieć

- **Repo jest publiczne** — każdy może zobaczyć kod i, jeśli zna adres, otworzyć stronę.
  W polu "temat ntfy" na stronie wpisany jest Twój prawdziwy kanał (`stormwatch_x6QQ62-BU5`).
  Jeśli wolisz nie zostawiać go w publicznym kodzie, przed wgraniem pliku wyczyść to pole
  w kodzie (szukaj `value="stormwatch_x6QQ62-BU5"`) i wpisuj temat ręcznie po otwarciu strony.
- **GPS wymaga HTTPS** — dlatego zwykły plik na dysku czy artefakt w czacie nie zadziała,
  musi być hostowany (stąd GitHub Pages).
- **Radar odświeża się co 5 minut** — RainViewer tyle ma opóźnienia, to nie jest wina aplikacji.
- **Bateria** — trzymanie GPS + ekranu włączonego w aucie zużywa baterię szybciej niż zwykle;
  warto mieć ładowarkę samochodową.
- Jeśli coś nie działa (np. GPS nie łapie), sprawdź czy przeglądarka ma zgodę na lokalizację
  w ustawieniach systemowych telefonu, nie tylko w samej stronie.

