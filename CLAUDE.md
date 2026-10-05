# CLAUDE.md — roadchanger.com

Šis fails ir obligāti jāizlasa katras sesijas sākumā. Te ir projekta noteikumi un konteksts.

## Valoda un komunikācija

- Atbildi latviski. Lietotājs raksta latviski, bieži bez garumzīmēm — tas ir normāli.
- Ja lietotājs saka **"nekode"** — tikai analizē / atbildi, NEMAINI kodu.
- Lietotājs bieži sūta screenshotus — vispirms uzmanīgi apskati tos, tad apraksti, ko redzi, un tikai tad labo.
- Nekad neizdomā un nepievieno tekstus, kurus lietotājs nav teicis. Lapas tekstus maina TIKAI ar viņa precīzo formulējumu.
- Strādā mazos, konkrētos soļos — viena izmaiņa, parādi rezultātu, gaidi apstiprinājumu.

## Repo struktūra

- Viss lapas saturs dzīvo repo apakšmapē **`roadchanger/`** (t.i., `roadchanger/index.html`, `roadchanger/dj/index.html` utt.). Repo sakne satur tikai šo mapi un CLAUDE.md.
- Lokālais klons: `/Users/emilsasmanis/Documents/roadchanger`. GitHub: `siamumbai/roadchanger` (branch `main`).

## Svētie dizaina noteikumi

1. **Fluid dizains.** Visi teksti, rindkopas, paddingi un izkārtojums saglabājas VIZUĀLI IDENTISKI jebkurā ekrāna izmērā un jebkurā zoom līmenī. Līdzekļi: `clamp()`, `rem`, `vw`, `aspect-ratio`, procenti. Jebkura izmaiņa nedrīkst salauzt šo principu.
2. **"Pārkārto secībā: 1, 2, 3"** nozīmē: katra bilde pārvietojas KOPĀ ar savu numuru un savu izmēru (nevis tikai numuri/labels mainās vietām). Bilžu kopējās kolāžas izmērs paliek nemainīgs.
3. **Katrs fails vienmēr saucas `index.html`** un dzīvo savā mapē (sakne, `dj/`, `fire/`, `rider/`, `lights/`, `video/`, `thanks/`). URL bez `.html`.
4. **Mobile labojumi tikai media query iekšienē** — desktop skats paliek neskarts, ja nav teikts citādi.
5. Kad labo "Get in touch" formu vai jebko ar to saistītu — to pašu izmaiņu veic VISĀS lapās, kur forma ir (main, dj, fire).

## Dizaina sistēma

- Fonti: **Libre Baskerville** (virsraksti, serif) + **Lato** (pamatteksts, sans), Google Fonts.
- Krāsas:
  - Fons (krēms): `#FFFBF5`
  - Alternatīvais gaišais fons (dzeltenīgs): `#FDF5E6` (arī `#FEF9F2`)
  - Tumšā sadaļa (booking) un tumšais teksts: `#2C2416`
  - Brūnais akcents (links, pogas, izcēlumi): `#B07320`
  - Brūnā svītra (divider): `#C4A06A` — galvenajā lapā tai jāiet NO MALAS LĪDZ MALAI bez atstarpēm; tā atdala balto fonu (augšā) no dzeltenīgā "The artist" fona (apakšā)
  - Apmales: `#E0CCA4`, headera apakšlīnija `#EAD9B8`
  - Pieklusinātais teksts: `#6B5035`, `#7A5C38`
  - Footer fons: `#1E1810`, footer augšlīnija `#3D3020`
- Sekciju paddings desktopā: `5rem 3rem`. Footer: `padding: 2rem 3rem; margin: 0` (tieši pēc booking sadaļas, bez baltas atstarpes apakšā).
- Lapām ir `zoom: 0.9` (vienāds visās lapās — main, dj, fire).
- Kartiņu stils: noapaļoti stūri (8–12px), `border: 0.5px solid #E0CCA4`, viegla ēna `rgba(44,36,22,~0.07)`.
- Media query lūzumpunkti: `768px` (un vietām `480px`).

## Lapu struktūra (stāvoklis 2026-08)

- `/` — galvenā lapa. Hero ("DJ. Saxophone. One performance.", hero.jpg, "Riga, Latvia") → **Six experiences** (01 DJ with live saxophone → WATCH VIDEO uz /dj/; 02 Roadchanger Fire Show → /fire/; 03 Piano lounge) → **My Creative Collaborators** (04 Live Roses; 05 Live Eyes; 06 Live Painting) → **Need Sound and Lights?** (SEE MORE → /lights/) → brūnā svītra → **The artist** (Emīls Ašmanis aka DJ Roadchanger, about.jpg) → **Get in touch** (tumšā sadaļa) → footer.
- `/dj/` — DJ lapa ("DJ Set with Saxophone", video, "Tech Rider" poga → /rider/, sava Get in touch sadaļa).
- `/fire/` — fire show lapa (6 bilžu režģis + lielā bilde `bigfire1.jpg`, Get in touch).
- `/rider/` — "Technical Rider": headeris tikai ar Roadchanger logo (→ /), virsraksts, bilde `rider1.jpg`, zem bildes centrēts "If you have any questions please call +371 20031578" (zvanāms `tel:` links).
- `/lights/` — aparatūras lapa (Sound System, lights, smoke machines, DJ table, wireless microphones).
- `/video/` — video portfolio (2 YouTube kartiņas: "Monk Echo" un "Iron Haya 3x3", iegultie atskaņotāji ar youtube-nocookie, headeris/footeris kā /rider/). **SLĒPTA lapa pēc lietotāja lēmuma (2026-08-26): nav linka navigācijā, `noindex` meta, izslēgta no sitemap, aizliegta robots.txt.** Lietotājs to sūta klientiem pats kā privātu portfolio — nekad nelikt navigācijā un neindeksēt.
- `/review/` — **īsā saite atsauksmēm.** Pāradresē uz Google atsauksmes formu ar **HTTP 307** (`roadchanger/vercel.json`). `review/index.html` paliek kā rezerves slānis (meta refresh + poga + JS), ja konfigurācija kādreiz pazustu — Vercel redirects nostrādā pirms failiem, tāpēc parasti to nemaz nepasniedz. `noindex`, nav sitemap. Šo saiti lietotājs sūta klientiem pēc pasākuma.
- `/reviews/` — atlasītas Google atsauksmes kā **statisks HTML** + poga uz pilno Google profilu + poga uz `/review/`.
- `/projects/` — projektu saraksts; katrs projekts savā mapē `/projects/<slug>/index.html`.
- `/kalendars/` — **privāts kalendārs sadarbības māksliniekiem** (uzlikts 2026-10-02). `noindex`, robots.txt aizliegts, nav sitemap, nav navigācijā. Sk. sadaļu "Kalendārs" zemāk.
- `/scenarijs/` — **privāti pasākumu scenāriji klientiem** (uzlikts 2026-10-02/03: paroles logs, Admin, scenārija tabula ar karti un kategorijām; PDF vēl nav). `noindex`, robots.txt aizliegts, nav sitemap, nav navigācijā. Sk. sadaļu "Scenārijs" zemāk.
- `/thanks` — pateicības lapa pēc formas nosūtīšanas ("Thanks! The form was submitted successfully..." + Go back poga uz galveno lapu).

## Navigācija (galvenā lapa)

Logo "Roadchanger" → `/` · DJ sets → `/dj/` · Fire show → `/fire/` · About → `#about` · Book now → `#booking`. Apakšlapās relatīvie ceļi (`../#services` utt.).

## Get in touch forma

- Formspree: `https://formspree.io/f/mnjwzwrq`, `method="POST"`, forma `id="booking-form"`.
- Sūtīšana caur JS `submitForm(event)` fetch ar `Accept: application/json`; pēc veiksmes redirect uz `https://roadchanger.com/thanks`.
- Lauki: vārds, e-pasts, "Type of event" (Wedding / Corporate event / Private party / Club / Other), ziņa; poga "Send enquiry".

## Kontakti un rekvizīti

- Emīls Ašmanis aka DJ Roadchanger, Rīga, Latvija
- e.asmanis@gmail.com · +371 20031578
- Footer: `SIA Mumbai · PVN Nr: LV40203627024 · Reģ. Nr: 40203627024`

## Bildes (`roadchanger/images/` mape)

hero.jpg · ddj1.jpg · m-ddj1.1.jpg · m-ddj1.2.jpg · ddj2.jpg · fire1.jpg · fire3.jpg · piano1.jpg · piano2.jpg · characters1.jpg · characters2.jpg · eyes1.jpg · eyes2.jpg · paint1.jpg · paint2.jpg · about.jpg · rider1.jpg · bigfire1.jpg
Jaunām bildēm nosaukumus dod lietotājs — vienmēr pajautā vai apstiprini precīzu faila nosaukumu.

## SEO un AI redzamība (uzlikts 2026-08-26)

- Katrai lapai `<head>` daļā: pilnvērtīgs `<title>`, canonical, Open Graph tagi; galvenajai lapai arī JSON-LD (`LocalBusiness`). Redzamo dizainu un tekstus tas nemaina.
- Saknē: `robots.txt` (atļauj visus rāpuļus + atsevišķs nosaukts bloks AI rāpuļiem — GPTBot, ClaudeBot, PerplexityBot u.c.; aizliedz /video/ un /thanks), `sitemap.xml` (visas lapas bez /video/ un /thanks), `llms.txt` (faktu kopsavilkums AI rīkiem).
- `/video/` un `/thanks` ir `noindex` — tā tam jāpaliek.
- Google Search Console verifikācijas meta tags ir galvenajā, /dj/ un /fire/ lapā.

## Atsauksmes un projekti (uzlikts 2026-08-28)

**Princips: vākt Google, rādīt savā lapā.** Visas oriģinālās atsauksmes dzīvo Google
Business Profile. roadchanger.com tās tikai atkārto, lai Google, ChatGPT, Claude un
Perplexity tās var izlasīt.

- **NEKAD neizmantot iegultus Google/Trustpilot widgetus.** Tie ielādējas caur JS iframe,
  un AI rāpuļi tos neredz. Atsauksmju teksts vienmēr ir tiešs HTML `/reviews/index.html` failā.
- Atsauksmes tekstu kopē no Google **burtiski** — nelabot, nesaīsināt, netulkot.
- Vecā `reviews.html` (Firebase + Google sign-in + izdomātas demo atsauksmes) ir **izdzēsta**
  2026-08-28. Neatjaunot — pašbūvēta atsauksmju sistēma AI acīs sver mazāk nekā viena
  īsta Google atsauksme, un izdomātas atsauksmes dzīvajā lapā ir risks.

### Google saites (atrisinātas 2026-08-28)

| Kur | Saite |
|---|---|
| Atsauksmes forma | `https://g.page/r/CZjQXSVaRA0PEBM/review` — **4 vietas:** `roadchanger/vercel.json` (307, galvenais ceļš) + `review/index.html` 3 vietas (meta refresh, poga, JS — rezerves slānis). Mainot saiti, jāmaina visas 4. |
| Profils | `https://www.google.com/maps?cid=1084598239230808216` — `reviews/index.html` 3 vietas (JSON-LD `sameAs`, atsauksmes šablona avota links, CTA poga) un `llms.txt`. |

Place ID (ftid): `0x683462df9b5d4397:0xf0d445a255dd098` → CID decimālā: `1084598239230808216`.

Profila saitei lieto `maps?cid=` formu, nevis `share.google/...` īsinājumu: `cid` ir kanonisks
un pastāvīgs, īsinājums ir redirect. Abi noved uz to pašu profilu.

### Kā pievienot atsauksmi

1. `roadchanger/reviews/index.html` → atrast komentāru "ATSAUKSMJU SARAKSTS", nokopēt šablonu,
   aizpildīt (vārds, amats/uzņēmums, pasākums, zvaigznes, teksts, datums).
2. Izņemt `<p class="reviews-empty">…</p>`, kad ir vismaz viena atsauksme.
3. Tajā pašā failā `<head>` JSON-LD blokā pievienot `review` ierakstu un atjaunot
   `aggregateRating` (ratingValue + reviewCount) **atbilstoši īstajam Google profilam**.

### Kā pievienot projektu

1. `mkdir roadchanger/projects/<slug>` un nokopēt tur `_project-template.html` kā `index.html`
   (šablons ir **repo saknē**, netiek publicēts — pārbaudīts, Vercel publicē tikai `roadchanger/`).
2. Aizvietot visas `<...>` vietas ar īsto saturu. Tekstus dod lietotājs — neizdomāt.
3. Atjaunot 4 vietas: `projects/index.html` (kartiņa + ItemList JSON-LD), `sitemap.xml`, `llms.txt`.

## Kalendārs `/kalendars/` (uzlikts 2026-10-02)

- Viens fails `roadchanger/kalendars/index.html` (HTML + JS, Firebase JS SDK no gstatic CDN).
- **Firebase projekts `roadchanger-kalendars`** (atsevišķs no skanudarbnica), Firestore `eur3`, bezmaksas Spark plāns.
  Repo saknē (netiek publicēts): `firebase.json`, `.firebaserc`, `firestore.rules`, `firestore.indexes.json`.
  Noteikumu publicēšana: `npx firebase-tools deploy --only firestore:rules` (no repo saknes).
- Pieteikšanās: Google vai e-pasta saite (bez parolēm). Admin = tikai `e.asmanis@gmail.com` — pārbaude **Firestore noteikumos**, ne tikai UI.
- Dati:
  - `users/{e-pasts mazajiem burtiem}`: `name`, `view[]` (kalendāri, ko redz), `edit[]` (kuros raksta). Bez `view` = "Gaida".
  - `calendars/{id}`: `name`, `color`, `order`. Sākuma 6: Uguns šovs, Dzīvie tēli, Arfa, DJ, Darbnīca, Skaņa/Gaisma. Jaunus pievieno Admin sadaļā.
  - `calendars/{id}/events/{eventId}`: pasākums ar vairākiem kalendāriem = **kopija katra kalendāra mapē ar vienu ID** (`cals[]` lauks). Tā noteikumi piekļuvi pārbauda pēc mapes ceļa.
  - Statusi: `interese`, `rezervets` (oranži), `apstiprinats` (zaļš).
  - Dzēšana ir "mīkstā" (`deleted: true`); Admin sadaļā "Dzēstie" var atjaunot 30 dienas, vecākos Admin atverot izdzēš pavisam.
- Labot pasākumu var tikai tas, kam ir "rakstīt" tiesības **visos** tā kalendāros; citiem forma ir tikai lasāma.
- Lietotājam bez rakstīšanas tiesībām tukšas dienas klikšķis rāda "Lūdz atļauju pievienot pasākumu." (lietotāja teksts).
- Kalendāra skats: **mēneši viens zem otra, ritināmi** (ritinot pievienojas vēl). Katrs mēnesis ar savu virsrakstu un TIKAI savām dienām — tukšās vietas pirms 1. datuma bez līnijām, nākamā mēneša dienas nerāda. Augšā sticky josla ar ‹ mēnesis › un "Šodien".
- Admin: ķekši bloķēti, kamēr rindā nav nospiests **"Labot"** (tad poga = "Gatavs"). Dzēst e-pastu: klikšķis uz e-pasta → parādās **"Izdzēst"**. "Dzēstie (30 dienas)" salocīti ar ķeksi.
- Piekļuves noņemšana neko neizdzēš — ieraksti glabājas kalendārā, ne pie cilvēka; atdodot piekļuvi, viss atkal redzams.
- (2026-10-03) Izkārtojums 3 kolonnās: **kreisajā** kalendāru filtri vertikāli + "Nākošie pasākumi" (līdz 15, no šodienas); **vidū** mēneši; **labajā** vienmēr rezervēta vieta formai. Augšā mēnešu pogas no šī mēneša uz priekšu — tik, cik ietilpst rindā līdz malai (telefonā ritina uz sāniem). Bultas, mēneša nosaukums un "Šodien" noņemti. Kalendāru ķekši filtros visi melni kā "Visi" ("Aizņemts" sarkans).
- Šodiena tikai iekrāsota (bez kvadrāta); pagājušās dienas viegli pārsvītrotas pa diagonāli.
- Pasākumam var būt vairākas dienas: lauks `dateEnd` (tukšs = viena diena). Formā "Datums no – līdz"; kalendāri un statuss divās kolonnās.
- Pasākumu krāsas kalendārā (bez punktiņiem): **dzeltens** = Interesējas, **oranžs** = Rezervēts, **zaļš** = Apstiprināts, **sarkans** = Aizņemts. Ja atzīmēts tikai "Aizņemts", statusa kolonna paslēpta (saglabā kā `apstiprinats`).
- Formas secība: Kalendāri | Statuss → Datums no – līdz → Laiks → Vieta (`place`) → **Adrese** (`address`) → **Apraksts** (`notes`). Lauki tukši, bez parauga teksta. "Nosaukums" (`title`) noņemts 2026-10-04 (vecās vērtības saglabājas datos).
- Labās puses forma (datorā) sniedzas līdz ekrāna apakšai bez iekšējās ritināšanas: augstums `--panelh` aprēķināts JS (`measureSticky`, ņem vērā `zoom`), "Piezīmes" aizpilda atlikušo vietu; "Pievienoja/Labots" rindiņa zem virsraksta.
- Telefonā (2026-10-04): secība "Nākošie pasākumi" → kalendārs → "Aizņemts" + kalendāri (vertikāls saraksts). Kalendārs rāda **vienu mēnesi**, pārslēdz ar bultām ‹ Mēnesis Gads ›; neritinās. Mēnesim vienmēr 6 rindas fiksētā augstumā, lai saraksts zem tā nelēkā. Klikšķis "Nākošajos pasākumos" neatver formu — aizved uz kalendāru un iekrāso datumu (`hlDate`); formu atver klikšķis uz pasākuma kalendārā.
- Logo "Roadchanger" kalendāra lapā ved uz `/kalendars/` (Kalendārs cilne, šis mēnesis), nevis uz galveno lapu.
- "Aizņemts" rindā poga "Labot" pa labi, treknā rakstā; ieslēgtā režīmā "Gatavs" sarkans un visa rinda viegli sarkana.
- Filtrs (2026-10-03): var izvēlēties **tikai vienu** kalendāru; atkārtots klikšķis vai "Visi" → redzami visi.
- **"Aizņemts" ir personīgs katram e-pastam** (2026-10-04): `busy/{e-pasts}/days/{YYYY-MM-DD}` (`{date, at}`). Redz un maina tikai pats; admins var lasīt. Filtros virs svītras, ieslēgts pēc noklusējuma, rādās kopā ar jebkuru kalendāru — **tikai sarkans dienas fons**, bez joslas; "Nākošajos pasākumos" nav. Pogu **"Labot"** (tad "Gatavs") — klikšķis uz dienas atzīmē/atbrīvo; šajā režīmā citus pasākumus pievienot nevar. Vecais kopīgais "Aizņemts" kalendārs (`c3ctw0kt2yPFC9hqyzMC`) pārnests uz personīgajiem un izdzēsts.
- **Admins: labajā pusē (kad forma aizvērta) visu e-pastu saraksts** (vārds vai e-pasts). Klikšķis → kalendārs tieši tā, kā to redz šis e-pasts (viņa kalendāri + viņa "Aizņemts", bez "Labot"). Pirmais saraksta ieraksts = tavs skats. Telefonā saraksts paslēpts.
- **Citu aizņemtie datumi (2026-10-05):** Admin tabulā pie katra e-pasta poga **"Pievienot"** atver visu reģistrēto e-pastu ķekšus → `users/{e-pasts}.seeBusy[]` (+ `seeNames{}` vārdiem). Šim e-pastam labajā pusē (telefonā zem kalendāriem) parādās saraksts "Aizņemts": viņš pats + atļautie; klikšķis rāda **tikai** tā cilvēka aizņemtos datumus — savu kalendāru pasākumi paslēpti, ķekši paliek vietā ļoti bāli un neaktīvi (lai "Nākošie pasākumi" nepārvietojas), izvēlētais e-pasts sarkans, "Labot" paslēpts; "Nākošie pasākumi" nemainās. Klikšķis uz sevis atgriež parasto skatu. Noteikumi: `busy` lasīt drīkst arī, ja īpašnieks ir lasītāja `seeBusy`. Labās puses sarakstā: **vārds uzvārds** (no Admin) un zem tā e-pasts. Admin tabulas augšā rinda tev pašam (tikai vārds → `users/e.asmanis@gmail.com.name`). Mainot vārdu, tas automātiski atjaunojas visu `seeNames`. Kreisajā pusē **virs "Aizņemts" ir vārds uzvārds** tam, kura aizņemtie datumi rādīti: sākumā pieteiktā e-pasta vārds, izvēloties citu labajā pusē — viņējais (bez vārda — e-pasts).

## Scenārijs `/scenarijs/` (uzlikts 2026-10-02)

- Viens fails `roadchanger/scenarijs/index.html`, tas pats Firebase projekts `roadchanger-kalendars`.
- Ieeja tikai ar paroli (Firebase **anonīmā** pieteikšanās + Firestore noteikumi). Paroles nav reģistrjutīgas.
- **Admin parole: `pasmaidi`.** Noteikumos glabājas tikai tās SHA-256 (repo ir publisks). Mainot: jauns hash `firestore.rules` → `scnAdmins` + deploy.
- Katram projektam 2 pamata paroles: `rw` lasīt/rakstīt, `ro` tikai lasīt (redzamas kartiņā) + pēc izvēles **parole katrai kategorijai**
  (zem "Labot"): lasīt visu + rakstīt tikai rindas ar šo kategoriju. Parolēm jābūt unikālām visos projektos.
- **Vēsture:** projektus nedzēš — "Labot" → "Pārnest uz vēsturi" (paroļu rādītāji izdzēsti, klienti izmesti, redz tikai admins);
  no vēstures "Pārnest uz aktuālajiem" paroles atjauno. Dzēšanas pogas projektiem nav.
- Jaunam scenārijam uzreiz 4 tukšas rindas. Laiku izvēlas ar klikšķiem (stundas 00–23, minūtes ik pa 5), bez rakstīšanas.
- Dati: `scenarios/{sid}` (name, lang, place, address, lat, lng, cats[]), `scenarios/{sid}/keys/main` ({rw, ro, cats:{catId: parole}}, lasa tikai admins),
  `scenarios/{sid}/members/{uid}` (kas ar kuru paroli ienācis), `scenarios/{sid}/rows/{rid}`, `scnIndex/{sha256('scn:'+parole)}` → {sid, role: rw|ro|cat, cat?}, `scnAdmins/{uid}`.
- Scenārija skats: kreisajā kolonnā virsraksts (`title`, piem. "Printful Event"), Vieta (`place`, bez uzraksta — "Vieta" tikai kā pelēks teksts tukšā laukā), Apraksts (`desc`),
  "Viesi ierodas" `guests` – `end` (divi laiki ar svītru, beigām sava uzraksta nav);
  labajā kolonnā Pilsēta (`city`), Adrese virs kartes ("Atrast kartē" meklē "adrese, pilsēta") (Leaflet + OpenStreetMap, adreses meklēšana caur Nominatim, vai klikšķis kartē). Karte VIENMĒR atveras ar visu Latviju — pietuvina paši,
  tabula Laiks | Notikums | Komentārs (rindas `order` secībā, labojas reālā laikā), labajā pusē kategorijas.
  Uzspiežot kategoriju: tās rindas oranžas, pārējās blāvas; rakstītāji ar apli rindas sākumā atzīmē/noņem.
  "Labot" atklāj rindu un kategoriju dzēšanu (×, vienmēr ar "Izdzēst? Jā / Nē"). "+" rindas labajā pusē ieliek tukšu rindu zem tās.
  **Izvēloties kategoriju:** virs tabulas tās "Ierašanās laiks" + komentārs (`catinfo/{catId}`), tabulā papildu kolonna
  "Komentārs · <kategorija>" (`rows.catNotes.<catId>`), un jebkuru šūnu var iekrāsot ar kvadrātiņu tās stūrī (`rows.marks.<catId>`,
  rinda pati tiek pievienota kategorijai). Rinda kategorijā = oranža svītra kreisajā malā (nevis pilns fons).
  Kategorijas parole: ienākot sava kategorija jau izvēlēta; drīkst rakstīt savu ierašanās laiku un savu komentāru kolonnu jebkurā rindā.
  Laika logā tukšai rindai iekrāsots (gaiši oranžs) iepriekšējās rindas laiks un tas ir noklusējums.
  Scenārija teksti (LV/EN) — `T` objekts failā; kategoriju sākuma nosaukumi pēc projekta valodas.
- **Sadaļas** (cilnes virs tabulas): `scenarios.sections` [{id,name}], sākumā Uzbūve · Scenārijs (EN Setup · Scenario).
- **Backstage** NAV cilne: tā ir labajā pusē zem kategorijām (poga, atverot kompakta tabula laiks + teksts; rindas ar `sec: 'backstage'`).
  Kamēr Backstage atvērts, labā puse nav "sticky" (citādi garas tabulas apakša nav sasniedzama).
- "Labot" režīmā rindām ↑ ↓ (pārvieto, samainot `order` ar kaimiņu) — gan tabulā, gan Backstage.
- Karte: **Esri World Light Gray** (Base + Reference slānis), bez API atslēgas. CARTO Positron NEDER — kopš 2026-10 prasa API atslēgu ("API KEY REQUIRED"). Punkts oranžs.
  Katrai sava tabula (`rows.sec`; rindas bez `sec` = `scenarijs`). Atverot vienmēr aktīvs **Scenārijs**, to dzēst nevar.
  "+" pievieno sadaļu; "Labot" režīmā × dzēš sadaļu kopā ar tās rindām (ar apstiprinājumu). Tukšai sadaļai, atverot rakstītājam, izveidojas 4 rindas.
- Mainot paroli, Admin izmet visus, kas ienāca ar veco. Valodu (`lang`) maina tikai admins.
- Lietotāja lēmumi: iekrāsošana pagaidām oranža visiem; rindai var būt vairākas kategorijas; kategorijas var pievienot/dzēst (dzēst — paslēpts aiz "Labot");
  PDF: galvenais + 1 kategorija; valoda katram projektam, maina tikai admins.

## Favikons (uzlikts 2026-08-28)

Avots: `~/Desktop/Google Business bildes/diskobumba.jpg` — spoguļbumba, ChatGPT ģenerēta,
PNG ar caurspīdīgu fonu (neskatoties uz `.jpg` nosaukumu). Oriģināls repo netiek glabāts.

Saknē: `favicon.ico` (16+32+48), `icon-192.png`, `icon-512.png`, `apple-touch-icon.png` (180).
Visās HTML lapās `<head>` pēc viewport meta ir trīs `<link>` tagi.

Ģenerēšanas nianses, ja kādreiz jāpārtaisa:
- Attēls apgriezts tieši uz bumbas malu, tad uzlikta **cieta apļa alfa maska** — oriģināla
  mala ir mīksta un mazajos izmēros izplūst.
- Izmēriem ≤48 px kontrasts palielināts ×1.45; bez tā 32 px kļūst par pelēku plankumu.
- `apple-touch-icon` ir ar **necaurspīdīgu `#2C2416` fonu** un 14 px rezervi — iOS caurspīdīgumu
  pārvērš melnā, tāpēc fons jāuzliek apzināti.
- 16 px izskatās vāji jebkurā variantā; tas ir pieņemts apzināti, jo retina ekrāni ņem 32 px avotu.
- `site.webmanifest` NAV likts apzināti — `theme_color` un `display` mainītu redzamo uzvedību
  Android pārlūkā. Ikonas strādā arī bez tā.

## Hostings un publicēšana

- **Vercel** ar custom domēnu `roadchanger.com` (apex bez www; `www` pāradresējas caur `cname.vercel-dns.com`). Pārbaudīts 2026-08-13 — lapa VAIRS NAV GitHub Pages.
- Vercel automātiski publicē no GitHub repo `siamumbai/roadchanger` `main` branch (saturs — `roadchanger/` apakšmapē).
- Tātad publicēšana = `git push` uz `main`. Nekādu papildu deploy soļu nav.
- **`vercel.json` dzīvo `roadchanger/vercel.json`, NE repo saknē.** Vercel Root Directory ir
  `roadchanger/` — saknē liktu failu Vercel vienkārši neredzētu (pārbaudīts: roadchanger.com/CLAUDE.md → 404).
- Tajā ir tikai `redirects` (nekādu `cleanUrls`/`trailingSlash` — tie mainītu esošo URL uzvedību).
- Atsauksmju pāradresācija ir **307**, nevis 301/308. Pastāvīgu pāradresāciju pārlūki kešo ilgi:
  ja Google saite kādreiz mainītos, klienti ar iekešotu 301 uz jauno vairs netiktu.

## Darba rutīna katrai sesijai

1. Sesijas sākumā izlasi šo failu un pēdējo piezīmi Obsidian vault mapē `roadchanger.com/`.
2. Pēc apstiprinātām izmaiņām Claude Code PATS izpilda: `git add` → `git commit` (īss apraksts latviski) → `git push`. Lietotājam GitHub nav jāaiztiek.
3. Sesijas beigās ieraksti piezīmi Obsidian vault `roadchanger.com/` mapē: datums, kas mainīts, kādi lēmumi pieņemti, kas palika nepabeigts.
   VAULT_CEĻŠ: `/Users/emilsasmanis/Documents/skanudarbnica/skanudarbnica/roadchanger.com/`

## Atvērtie darbi

**Aktuālais saraksts dzīvo Obsidian vault, jaunākajā piezīmē** — šobrīd
`2026-09-07 Booking forma, pasts un DNS.md`. Šeit tikai tas, kas skar kodu:

- [ ] `roadchanger/api/booking` funkcija (Vercel + Resend), lai forma neietu caur Formspree.
      Formspree NEIZSLĒGT, kamēr jaunais nav pārbaudīts dzīvajā.
- [ ] Navigācijas linki uz `/reviews/` un `/projects/` — REDZAMA izmaiņa visās lapās,
      vajag lietotāja apstiprinājumu. Bez tiem abas lapas ir nesasniedzamas.
- [ ] Atsauksmju teksti `/reviews/` lapā + JSON-LD `review` / `aggregateRating`.
- [ ] Projektu lapas `/projects/<slug>/` no `_project-template.html`.
- [ ] Attēlu optimizācija: WebP, cache headers (sens, neapstiprināts).

**Forma STRĀDĀ** — Formspree Reply-To ir pareizs, pārbaudīts ar īstu klientu 2026-08-31.
Problēma bija tikai paziņojuma vēstules izskats, nevis funkcionalitāte. Nesākt to "labot".
