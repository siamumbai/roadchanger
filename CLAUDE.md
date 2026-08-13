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
- `/video/` — video portfolio (2 YouTube kartiņas: "Monk Echo" un "Iron Haya 3x3", iegultie atskaņotāji ar youtube-nocookie, headeris/footeris kā /rider/). Pārbaudīts 2026-08-13: jaunākā versija IR dzīvajā lapā; linka galvenajā navigācijā joprojām nav.
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

## Hostings un publicēšana

- **Vercel** ar custom domēnu `roadchanger.com` (apex bez www; `www` pāradresējas caur `cname.vercel-dns.com`). Pārbaudīts 2026-08-13 — lapa VAIRS NAV GitHub Pages.
- Vercel automātiski publicē no GitHub repo `siamumbai/roadchanger` `main` branch (saturs — `roadchanger/` apakšmapē).
- Tātad publicēšana = `git push` uz `main`. Nekādu papildu deploy soļu nav.

## Darba rutīna katrai sesijai

1. Sesijas sākumā izlasi šo failu un pēdējo piezīmi Obsidian vault mapē `roadchanger.com/`.
2. Pēc apstiprinātām izmaiņām Claude Code PATS izpilda: `git add` → `git commit` (īss apraksts latviski) → `git push`. Lietotājam GitHub nav jāaiztiek.
3. Sesijas beigās ieraksti piezīmi Obsidian vault `roadchanger.com/` mapē: datums, kas mainīts, kādi lēmumi pieņemti, kas palika nepabeigts.
   VAULT_CEĻŠ: `/Users/emilsasmanis/Documents/skanudarbnica/skanudarbnica/roadchanger.com/`

## Atvērtie darbi

- [x] Pārbaudīt /video/ lapu — jaunākā versija (kartiņas "Monk Echo", "Iron Haya 3x3") IR uzlikta un dzīva (pārbaudīts 2026-08-13). Links navigācijā joprojām nav pievienots — tikai ar lietotāja apstiprinājumu.
- [ ] Attēlu optimizācija: WebP, cache headers (apspriests, bet nav apstiprināts, ka izdarīts — pārbaudīt repo).
- [ ] Gala pārbaude visām lapām dažādos ekrānos un zoom līmeņos.
