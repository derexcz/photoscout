# PhotoScout Pro – instalovatelná verze (PWA)

Statická webová aplikace. Nepotřebuje žádný backend ani build – stačí nahrát tuhle složku na web s HTTPS a otevřít ji v telefonu.

## Co je navíc oproti verzi v Claude

- **GPS z telefonu** – tlačítko „Použít moji polohu" v záložce Scouting.
- **Živá oblačnost** z Open-Meteo (celková + nízká, střední, vysoká, 10 dní dopředu).
- **Živý Kp index** z NOAA SWPC.
- **Funguje bez signálu** – výpočty slunce, Měsíce a všechny kalkulátory běží offline, poslední stažené počasí zůstává uložené.
- **Ikona na ploše** a spuštění na celou obrazovku jako běžná aplikace.

## Jak ji dostat do telefonu

Telefon dovolí GPS a instalaci jen přes **HTTPS**. Stačí jedna z možností:

### A) Vlastní server
Nahraj obsah složky do adresáře webu, který už běží na HTTPS, například do `/photoscout/`. Všechny cesty jsou relativní, takže funguje v libovolné podsložce.

### B) GitHub Pages (zdarma)
1. Vytvoř nový repozitář a nahraj do něj obsah této složky.
2. Settings → Pages → Source: „Deploy from a branch", větev `main`, složka `/ (root)`.
3. Za minutu běží na `https://<uzivatel>.github.io/<repozitar>/`.

### C) Rychlá zkouška na počítači
```
python3 -m http.server 8080
```
a otevři `http://localhost:8080`. Na localhostu funguje GPS i instalace bez HTTPS.

## Instalace na plochu

- **Android (Chrome):** otevři adresu → menu ⋮ → „Přidat na plochu" / „Nainstalovat aplikaci".
- **iPhone (Safari):** otevři adresu → Sdílet → „Přidat na plochu".

Při prvním klepnutí na „Použít moji polohu" se telefon zeptá na svolení k poloze.

## Aktualizace

Přepiš soubory na serveru novou verzí. Aplikace si změnu stáhne při dalším otevření s připojením a použije ji při tom následujícím.

## Zdroje dat

- Oblačnost: [Open-Meteo](https://open-meteo.com/) – bez API klíče, zdarma pro nekomerční použití.
- Kp index: [NOAA SWPC](https://www.swpc.noaa.gov/).
- Slunce a Měsíc se počítají přímo v telefonu.
- Světelné znečištění (Bortle) nemá volně dostupný zdroj, u vlastní polohy se nastavuje ručně.

## Soubory

| Soubor | K čemu je |
|---|---|
| `index.html` | vstupní stránka |
| `app.js`, `app.css` | aplikace a styly |
| `sw.js` | service worker – provoz offline |
| `manifest.webmanifest` | název, barvy a ikony pro instalaci |
| `fonts/`, `icons/` | písma a ikony |
