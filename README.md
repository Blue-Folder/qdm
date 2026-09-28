# QDM – quick decision maker

Malá appka na telefon, která za tebe rozhodne maličkosti. Máš dvě možnosti: **Jo / Ne**, nebo **Tohle / Tamto**. Klepneš na kouli (nebo zatřeseš telefonem) a dostaneš náhodnou odpověď:

- 40 % jo / tohle
- 40 % ne / tamto
- 20 % neutrál („Pět minut oraz.“)

## Co je v repozitáři

| Soubor | K čemu je |
|---|---|
| `index.html` | Celá appka: vzhled (CSS), obrazovky (HTML) i logika a animace koule (JavaScript). Tady probíhá většina úprav. |
| `manifest.webmanifest` | „Občanka“ appky pro telefon: název, ikona, barvy. Díky ní jde QDM přidat na plochu a otevře se bez lišty prohlížeče. |
| `sw.js` | Service worker. Běží na pozadí, díky němu appka funguje i offline a stahuje nové verze. |
| `icons/` | Ikony na plochu (tečkovaná koule). |
| `.nojekyll` | Prázdný soubor, který říká GitHub Pages, ať soubory nijak neupravuje. |

## Jak to běží na internetu

Appku hostuje **GitHub Pages** zdarma. Zapíná se jednou: **Settings → Pages → Build and deployment → Source: Deploy from a branch → Branch: `main`, složka `/ (root)` → Save**.

Po minutě je appka na adrese **https://barboracabalka.github.io/qdm/**.

## Jak si ji dát na plochu

- **iPhone:** otevři odkaz v Safari → tlačítko Sdílet → Přidat na plochu.
- **Android:** otevři odkaz v Chromu → menu ⋮ → Přidat na plochu / Nainstalovat aplikaci.

## Jak probíhají úpravy

1. Změníš soubor (nejčastěji `index.html`) a uložíš změnu na GitHub (commit + push).
2. GitHub Pages web do minuty sám aktualizuje.
3. Lidem s QDM na ploše se nová verze stáhne při dalším otevření appky (když mají internet).

Když změníš ikony nebo manifest, zvyš v `sw.js` číslo verze (`qdm-v1` → `qdm-v2`), aby se staré uložené soubory smazaly.

## Co funguje jen na skutečném webu

Namlouvání přes mikrofon a zatřesení telefonem v náhledech (třeba v Claude) nejdou, protože tam prohlížeč přístup k čidlům blokuje. Na https adrese z GitHub Pages fungují:

- **Mikrofon:** Chrome na Androidu i Safari na iPhonu se při prvním použití zeptají na povolení.
- **Zatřesení:** iPhone se na povolení zeptá po prvním klepnutí v appce.
