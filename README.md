# Drone Simulator — stap 1

Interactieve 3D-oefenapp voor leerlingen van 15 jaar in het praktijkonderwijs. Dit is **geen officieel drone-examen**.

## Installeren

1. Download en pak `Drone-Simulator.zip` uit.
2. Upload de **inhoud** van `Drone-Simulator` naar een GitHub-repository.
3. Open **Settings → Pages → Build and deployment** en kies **Deploy from a branch**, `main`, `/ (root)`.
4. Open de GitHub Pages-link zodra GitHub de site heeft gepubliceerd.
5. Een internetverbinding is nodig om Three.js van de CDN te laden. Daarna werkt de app zonder server, maar **niet gegarandeerd offline**.

Voor lokaal testen: gebruik een eenvoudige lokale webserver, bijvoorbeeld `python -m http.server 8000`, en open `http://localhost:8000`. Dubbelklikken op `index.html` werkt niet betrouwbaar met ES-modules.

## Besturing

- **Desktop:** W/S vooruit/achteruit; A/D zijwaarts; pijltje omhoog/omlaag stijgen/dalen; pijltje links/rechts of Q/E draaien; spatie foto.
- **Telefoon/tablet:** linker joystick voor hoogte en draaien; rechter joystick voor vooruit, achteruit en zijwaarts.
- **Knoppen:** Foto, Camera (volg/FPV), Lens omhoog/omlaag, RTH, Pauze.
- **RTH:** klik opnieuw om af te breken.

## Projectbestanden

`index.html` laadt de app. `css/style.css` verzorgt de opmaak. `js/main.js` koppelt alles. `world.js` bouwt de 3D-wereld, `drone.js` het toestel, `controls.js` de invoer, `missions.js` de oefeningen, `photography.js` de fotobeoordeling, `progress.js` lokale opslag en `ui.js` de menu's. Stap 2 kan losse modules toevoegen en `progress.js` hergebruiken.

## Privacy

Geen accounts, server of persoonsgegevens. Scores en maximaal acht verkleinde foto's worden lokaal bewaard in `localStorage`. De browser kan deze gegevens wissen. Bij volle opslag kunnen foto's mislukken.

## Beperkingen

Dit is een speelbare prototypeversie met vereenvoudigde vluchtfysica. Gebouwen en natuur zijn procedureel en gestileerd; niet fotorealistisch. Bruggen, molen, kerk en water hebben vereenvoudigde geometrie. De fotoanalyse controleert kijkrichting, afstand en hoek; geen echte objectherkenning of belichtingsanalyse. De veiligheidszones zijn fictief en geen actuele luchtvaartkaart. RTH heeft geen obstakelvermijding. De 30-fps-doelstelling is niet op een echt toestel gemeten. Niet alle oefeningen zijn volledig ruimtelijk gecontroleerd: sommige gebruiken vereenvoudigde criteria zoals vliegafstand. Dit is niet geschikt als officiële vliegopleiding of veiligheidsadvies.

## Stap 2 — Theorie en toetsen

Open in het hoofdmenu **Theorie en toetsen**. De uitbreiding bevat **225 zelfgeschreven oefenvragen**: 25 in elk van negen onderwerpen. Dit zijn geen officiële examenvragen. Een oefentoets kiest tien willekeurige vragen uit één onderwerp en toont direct feedback. Het proefexamen kiest 40 vragen, gebruikt een limiet van 40 minuten en toont pas na afloop antwoorden en uitleg. De oefengrens is 75%. De app geeft geen cijfers of certificaten.

### Een docent voegt vragen toe

Open `js/vragen.js` in GitHub. Elke vraag is een object in de array `QUESTIONS`. Kopieer een bestaand object en wijzig **id** (moet uniek zijn), **domain** (exacte naam van een van de negen onderwerpen), **text**, **options** (exact vier teksten), **correct** (0=A, 1=B, 2=C, 3=D), **explanation** en **flight** (een bestaande oefening-ID uit `js/missions.js`, bijvoorbeeld `3-1` voor de rode zone). Bewaar de komma tussen de objecten. De website werkt na de volgende GitHub Pages-publicatie met de nieuwe vragen. Controleer de inhoud vóór gebruik met leerlingen. Verander geen importregels of bestandsnamen.

### Punten en privacy

Twee punten per goed antwoord en tien bonuspunten voor een afgeronde toets. Deze punten tellen op bij de bestaande vliegpunten. Fouten, recente oefentoetsen en het aantal proefexamens staan alleen in `localStorage` op het gebruikte apparaat. Bij wissen van browsergegevens gaat die voortgang verloren. De knop **Wis voortgang** wist ook de theorievoortgang. Er is geen account, server of centrale registratie.

### Officiële regels controleren

Gebruik voor het echte A1/A3-examen een erkende examenaanbieder. De RDW verstrekt daarna het vliegbewijs. Controleer actuele regelgeving, zones, verzekering en registratie via RDW en Rijksoverheid. De verdeling van 40 vragen en 40 minuten is **een ontwerpkeuze van deze oefenapp**; het is geen door de RDW bevestigd identiek examenformat. De onderwerpen zijn een educatieve indeling en geen garantie dat iedere officiële examenvraag of weging wordt gedekt.
