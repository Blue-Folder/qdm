# QDM – kontext projektu

Osobní projekt Barbory ze studia Blue Folder (GitHub organizace `Blue-Folder`, kam budou patřit i další appky): webová appka na telefon (PWA) „quick decision maker“, která pomáhá rozhodnout se v maličkostech, když je mozek po práci unavený. Nejde do App Storu ani Google Play. Hostuje se na GitHub Pages a lidé si ji přidají na plochu. Barbora se na projektu zároveň učí, jak to celé funguje: vysvětluj jí změny srozumitelně, česky a bez zbytečného žargonu.

Komunikace: česky.

## Jak appka funguje
- Úvod: dvě dlaždice s ikonami, **Jo / Ne** a **Tohle / Tamto**. Vpravo nahoře přepínač světlý/tmavý režim (bílý a černý puntík).
- Obrazovka s otázkou: nadpis „Ahoj, co řešíš?“ na jednom řádku.
  - Jo/Ne: jedno pole s nápovědou „Dát si čokoládu?“ (placeholder, ne předvyplněná hodnota).
  - Tohle/Tamto: dvě pole s nápovědou „1. Tohle“ a „2. Tamto“, mezi nimi „nebo“.
  - Pole: po klepnutí nápověda zmizí. Když je v poli text, ukáže se křížek na vymazání. Vpravo je mikrofon na namlouvání (Web Speech API, cs-CZ).
- Koule: canvas s ~4200 modrými tečkami. V klidu je to vznášející se oblak (inspirace videem, kde se částice skládají do koule). Po klepnutí nebo zatřesení se tečky srazí do tečkované koule, rychle se roztočí, koule se „naplní“ lesklou modrou (inspirace plakátem se skleněnou modrou koulí) a z ní se barva rozlije přes celou obrazovku. Pak se ukáže odpověď. Celé to trvá ~0,7 s a má být rychlé.
- Pod koulí je nápis „KLEPNI NEBO ZATŘES“.

## Pravidla odpovědí
- Poměr je vždy **40 % jo / tohle, 40 % ne / tamto, 20 % neutrál** (neutrál = „dej si 5 minut oraz a zkus to znovu“ apod.).
- Odpovědi mají být fresh, krátké, vtipné, trochu drzé a fakt náhodné. Stejná odpověď nepadne dvakrát po sobě.
- Každá odpověď má velký text a menší doplněk (např. „Ne.“ + „A nesmlouvej.“).

## Vizuální pravidla
- Všechno v jedné barvě. Světlý režim: kobaltově modrá `#1E3BD8` na krémovém `#F4EFE4`. Obrazovka s odpovědí je modrá s krémovým textem.
- Tmavý režim: pozadí `#0B0E20`, text a tečky `#8C9BFF`. Obrazovka s odpovědí zůstává **tmavá** (`#121842` s textem `#8C9BFF`), protože je to šetrné k očím. V tmavém režimu nikdy nepřepínat na sytě modrou.
- Font: Bricolage Grotesque (Google Fonts).
- Barvy jsou v CSS jako proměnné (`--bg`, `--ink`, `--flood`, `--on-flood`…). Nové prvky barvi přes ně, aby fungovaly v obou režimech.

## Technika
- Všechno je v jednom souboru `index.html` (HTML + CSS + JS, bez knihoven a bez build kroku).
- `sw.js`: offline režim a aktualizace. HTML se načítá nejdřív ze sítě (vždy čerstvá verze), ostatní soubory z cache. Při změně ikon nebo manifestu zvyš `VERSION` v `sw.js`.
- `manifest.webmanifest` + `icons/`: instalace na plochu.
- Mikrofon a zatřesení fungují jen na skutečné https adrese, ne v náhledech.
- Web: https://blue-folder.github.io/qdm/ (GitHub Pages z větve `main`), repozitář `Blue-Folder/qdm`.
- Commity podepisuj jako `barbaritta <barbaritta@users.noreply.github.com>`, ne celým jménem ani osobním e-mailem.
