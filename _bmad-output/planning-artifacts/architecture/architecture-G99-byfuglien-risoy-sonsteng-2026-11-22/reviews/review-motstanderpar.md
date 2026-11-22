# Reviewer Gate – motstanderpar (Architecture Spine, Sambandet v1)

- **Gjennomgått:** `ARCHITECTURE-SPINE.md` (utkast 2026-11-22)
- **Kontekst:** PRD (2026-11-11), EXPERIENCE.md (utkast 2026-11-13)
- **Metode:** For hvert område er det konstruert to enheter ett nivå ned (epics/stories) som hver følger alle AD-er og konvensjoner bokstavelig, men som likevel bygger noe som ikke passer sammen. Hvert slikt par er et hull. For hvert hull foreslås den minste AD-en eller konvensjonen som tetter det, i en størrelse som passer en lokal app laget av tre studenter.
- **Dato:** 2026-11-22
- **Reviewer:** uavhengig agent (Reviewer Gate). Spinen er ikke endret.

## Konklusjon

Spinen er god på grenser: hvor kode bor, hvem som kaller Anthropic, hva som er hemmelig og hva som lagres. Den er tynn på **formene som krysser grensene**. AD-6 sier at «svarskjemaet» bor i `shared/`, men sier ikke *hvilket* skjema. Det finnes minst to: det leverandøren returnerer, og det klienten får. Forespørsels- og svarformer for aktiviteter og fullføring er heller ikke definert. I tillegg er normaliseringen og tegntellingen beskrevet så åpent at to korrekte implementasjoner gir ulike svar. Ett hull, standardgrensen på 100 kB for request body i Express, får sensors demo-flyt til å feile på et helt vanlig .docx-dokument.

**Vurdering:** Ikke klar for Reviewer Gate ennå, men nær. Tre nye AD-er (AD-16 til AD-18) og omtrent seks nye linjer i Consistency Conventions tetter alle de alvorlige hullene. Ingen av endringene krever ny teknologi.

## Funn: motstanderpar

Alvorlighetsgrad: **Høy** = sannsynlig feil i kjerneflyt eller demo. **Middels** = feil i kanttilfeller eller integrasjonsarbeid som må gjøres om. **Lav** = uklarhet som typesjekken eller en kort prat fanger opp.

### H1 – Demo-adapter mot Anthropic-adapter: hvilket «svarskjema»? (Høy)

- **Enhet A (demo-adapter, AD-10/11):** Fasitfilene skrives i formen klienten skal vise: med `feltstatus` som allerede inneholder `ugyldig`, og med kildeutdrag som `{ tekst, verifisert: true }`. «Samme svarskjema som Anthropic-adapteren» er oppfylt fordi begge returnerer `Aktivitetsforslag`.
- **Enhet B (Anthropic-adapter + kjernens FR-17/FR-28-steg, AD-8):** Adapteren returnerer modellens rådata. Kjernen setter `ugyldig`, mapper kategori og verifiserer.
- **Konflikt:** Kjøres demo-fasiten gjennom FR-17/FR-28-steget, kan den feile valideringen eller bli verifisert to ganger. Hopper demo-veien over steget, er FR-30 («verifiseres på samme måte») brutt i stillhet, og demo tester ikke den samme koden som skal testes mot fasit. AD-8 sier «Det er appen, ikke modellen, som setter status *ugyldig*», men forbyr ikke at en fasitfil gjør det.
- **Tiltak – ny AD-16 (to skjemaer, ett eierskap):** `shared/` definerer to navngitte zod-skjemaer:
  - `RaattForslag` – porten `AnalysisProvider` returnerer bare denne formen. Hvert felt er `{ verdi: string | null, status: 'ok' | 'usikker' | 'manglende' }`, og `kildeutdrag` er `string[]`. Kategori er fri tekst her.
  - `Aktivitetsforslag` – bare kjernen lager denne formen, og den er det eneste `POST /api/analyze` returnerer. Den har `feltstatus` med alle fire verdiene og `kildeutdrag: { tekst: string, verifisert: boolean }[]`.

  Demo-fasit lagres som `RaattForslag` og går gjennom akkurat det samme FR-17/FR-28-steget som modellsvaret.

### H2 – Manuelt aktivitetsskjema (F4) mot fullføring av gjennomgang (F8): kropper som ikke er definert (Høy)

- **Enhet A (F4 + `POST/PUT /api/activities`):** Sender `{ tittel, …, merknader: null }` når merknaden er tom. PUT sender også `id` i kroppen. Svaret er den lagrede aktiviteten.
- **Enhet B (F7/F8 + `POST /api/review/commit`):** Sender hele forslagsobjektene fra klienttilstanden, med `feltstatus`, `kildeutdrag` og et klientgenerert forslags-id, i en ren liste. Merknader er `""` eller mangler. Svaret er `204`.
- **Begge følger AD-ene:** AD-4 sier bare hva en *lagret* aktivitet har. AD-7 sier at serveren validerer med «den samme koden», men ikke om ukjente felt skal fjernes eller avvises. Spinen definerer ikke formen på kroppene.
- **Konflikt:** Serverens skjema avviser enten fullføringen (ukjente nøkler) eller fjerner dem i stillhet. Det siste er bare trygt for FR-23 («kildeutdrag lagres ikke») hvis noen faktisk fjerner dem. `merknader` kan bli både `null`, `""` og manglende i planfilen. F8 trenger lagrede datoer for meldingen «hvilke kalenderår de gjelder» og får dem ikke ved `204`. `GET /api/activities` kan være en liste eller `{ aktiviteter }`.
- **Tiltak – ny AD-17 (API-kontrakten er typet i `shared/`):** Alle forespørsels- og svarkropper defineres som zod-skjemaer i `shared/api.ts`. Både rutene og klientens fetch-hjelper bruker dem. Minimum:
  - `AktivitetInput` = de seks domenefeltene uten `id`. Det er `.strict()`, slik at ukjente felt gir `VALIDATION_FAILED` og ingenting fjernes i stillhet. Det brukes av POST, PUT (der `id` bare kommer fra stien) og fullføring.
  - `merknader` er alltid `string`, og tom merknad er `""`.
  - Fullføring: `{ aktiviteter: AktivitetInput[] }`. Klienten kopierer de seks feltene ut av hvert godkjent forslag, slik at forslags-id og kildeutdrag aldri sendes.
  - Svar: `GET` gir `{ aktiviteter: Aktivitet[] }`, POST og PUT gir `Aktivitet`, og fullføring gir `{ aktiviteter: Aktivitet[] }` med de lagrede aktivitetene.
  - `id` er en streng fra `crypto.randomUUID()`, laget i `server/core`. Forslags-id er klientens eget anliggende, for eksempel indeksen i listen, og sendes aldri til serveren.

### H3 – Klientens validering i F7 mot serverens FR-17-status: hvem eier feltstatus etter redigering? (Middels–Høy)

- **Enhet A (F7 gjennomgangs-UI):** Viser og sperrer godkjenning ut fra `feltstatus` slik den kom fra `/api/analyze`, og kjører `shared`-validering når et felt forlates. Statusen `usikker` blir stående.
- **Enhet B (F4-gjenbruk i F7):** Regner status bare ut fra FR-2-valideringen av verdien. `usikker` forsvinner.
- **Konflikt:** FR-22 sier at KI-statusen ikke gjelder lenger når brukeren har endret feltet. Det er ikke definert hvordan dette gjøres. Den ene enheten viser «? Kontroller» etter at brukeren har rettet feltet. Den andre mister `usikker` allerede ved første omtegning. Dermed finnes det to eiere av `ugyldig`: kjernen (AD-8) og klienten (AD-7).
- **Tiltak – konvensjon «Feltstatus i gjennomgang»:**
  - `shared/` eksporterer én funksjon, `valider(aktivitetsutkast) → Record<felt, 'manglende' | 'ugyldig' | null>`. Den er den eneste kilden til `manglende` og `ugyldig`, både i kjernens FR-17-steg, i F4, i F7 og i serverens validering av skrivinger.
  - Klienten holder `kiStatus` per felt og flagget `endret` per felt. Vist status = `valider(…)[felt] ?? (endret ? 'ok' : kiStatus)`.
  - Godkjenning sperres bare av resultatet fra `valider`.

### H4 – Tekstuttrekk og hash (AD-11) mot verifisering av kildeutdrag (FR-28): normaliseringen er underspesifisert (Høy)

- **Enhet A (normalisering, story 1):** Gjør CRLF om til `\n`, gjør `/[ \t]+/` om til `' '`, gjør `/\n+/` om til `'\n'` og trimmer. Det følger konvensjonen bokstavelig: «sekvenser av mellomrom og linjeskift slås sammen».
- **Enhet B (verifisering, story 2):** Antar at «slås sammen» betyr at alt hvitt rom blir ett mellomrom, og bruker `includes`.
- **Konflikt og huller:**
  1. Et kildeutdrag der modellen har gjort et linjeskift om til et mellomrom, blir *ikke verifisert* med enhet A. Det bryter FR-28: «avviker bare i mellomrom eller linjeskift → verifisert».
  2. Ikke-brytende mellomrom (U+00A0), som er vanlig i .docx og PDF, er ikke dekket av `[ \t]`. Teksten ser lik ut, men blir ikke verifisert.
  3. Unicode-form er ikke nevnt. En PDF kan gi `å` som `a` + kombinerende ring (NFD), mens modellen svarer i NFC. Teksten ser lik ut, men blir ikke verifisert.
  4. Et tomt kildeutdrag (`""` eller bare mellomrom) blir *verifisert*, fordi `tekst.includes('')` alltid er sant.
- **Tiltak – stram inn konvensjonen «Tekstnormalisering» til to navngitte funksjoner i `shared/`:**
  - `rensTekst(s)` = `s.normalize('NFC')`, gjør `\r\n?` om til `\n` og trimmer. Brukes på uttrukket tekst før grensesjekken på 100 000 tegn og før teksten sendes til modellen, slik at avsnitt beholdes.
  - `sammenligningsnokkel(s)` = `rensTekst(s).replace(/\s+/gu, ' ')`. JavaScript-`\s` dekker også NBSP. Brukes på begge sider i FR-28 og som grunnlag for SHA-256 i AD-11.
  - Et kildeutdrag med tom `sammenligningsnokkel` forkastes i kjernen. Det vises ikke som verifisert.
  - Én enhetstest med NBSP, NFD, linjeskift og tomt kildeutdrag.

### H5 – Teller for merknader i F4 mot serverens validering: 5 000 mot 5 001 tegn (Middels)

- **Enhet A (F4-skjema):** `<textarea maxLength={5000}>` og en teller basert på `value.length`. Det ser ut til å følge AD-12.
- **Enhet B (server):** `[...merknader].length <= 5000`, altså kodepunkter, slik AD-12 sier.
- **Konflikt:**
  1. `maxLength` og `.length` teller UTF-16-enheter, ikke kodepunkter. En emoji teller da 2 i klienten og 1 på serveren.
  2. `maxLength` kutter innlimt tekst i stillhet. Det bryter FR-6, som sier at merknader aldri forkortes automatisk, og gjør grensetesten 5 000 mot 5 001 umulig i F4.
  3. AD-12 sier «linjeskift teller som ett», men ikke hvor `\r\n` gjøres om. Kommer en merknad med CRLF (for eksempel en KI-merknad eller lim inn fra Windows), teller klient og server ulikt.
  4. Det er ikke definert om merknader trimmes ved lagring.
- **Tiltak – konvensjon «Tegntelling og fritekst»:**
  - `shared/tellTegn(s) = [...s.replace(/\r\n?/g, '\n')].length`. Dette er den eneste tellingen, og den brukes av teller, validering og tester.
  - Ingen `maxLength` på felt som har en tegngrense.
  - Ved lagring trimmes `tittel` og `ansvarsomrade`. `merknader` lagres uendret, bortsett fra at CRLF blir `\n`, og en merknad med bare mellomrom blir `""`.
  - Normaliseringen gjøres i `AktivitetInput`-skjemaet (zod-transform), så den skjer likt for POST, PUT og fullføring.

### H6 – Opplasting i klienten (F6) mot opplastingsruten: header-koding og grenser for kroppsstørrelse (Høy)

- **Enhet A (F6-klient):** `fetch('/api/analyze', { body: file, headers: { 'X-File-Name': file.name, 'Content-Type': file.type } })`. Det følger konvensjonen «filnavn og type i header».
- **Enhet B (rute):** `express.raw({ type: '*/*' })` og en sjekk av `Content-Type` mot docx- og PDF-MIME.
- **Konflikt:**
  1. Et filnavn med tegn utenfor Latin-1, for eksempel «Årsplan – 2027.docx» med tankestrek (U+2013), får `fetch` til å kaste `TypeError` før kallet sendes. Tegn som `æøå` blir latin1/UTF-8-mojibake på serveren.
  2. `file.type` er ofte tom for .docx på Windows, så gyldige filer avvises.
  3. **Standardgrensen i `express.raw` og `express.json` er 100 kB.** En vanlig .docx med logo er større, så analysen feiler med Express sin egen HTML-feilside i stedet for `{ code, message }`. Det samme gjelder fullføring av mange forslag med lange merknader (15 × 5 000 tegn ≈ 75–150 kB).
- **Tiltak – stram inn konvensjonen «Opplasting»:**
  - Filnavnet sendes som `encodeURIComponent(name)` og dekodes på serveren. Det brukes bare til meldinger.
  - Formatet avgjøres av filinnholdet: `PK` gir .docx, og `%PDF` gir PDF. Headeren avgjør ikke formatet.
  - Kroppsgrensen er `express.raw` 10 MB + 1 kB og `express.json` 1 MB.
  - Én global feilhåndterer gjør `entity.too.large` om til `FILE_TOO_LARGE`, og ukjente feil om til `INTERNAL`. Alle feil går alltid som `{ code, message }`.

### H7 – Demo-adapteren mot klientens resultattilstander: FR-18, FR-19 og FR-20 blandes (Middels)

- **Enhet A (demo-adapter):** For et ukjent dokument returneres `[]`. Det er riktig etter AD-10, fordi det er samme skjema og ingen forslag.
- **Enhet B (F6-klient):** Viser FR-19 («Fant ingen aktiviteter») for `forslag: []`.
- **Konflikt:** Brukeren får feil melding, mens FR-18 krever en egen melding. I tillegg legger både server og klient på FR-20-teksten om demo-modus, så den vises to ganger. Feilkodene er ikke listet, så klient og tester gjetter.
- **Tiltak – konvensjon «Analyseutfall og feilkoder»:**
  - `200 { forslag: [≥1] }` gir gjennomgang. `200 { forslag: [] }` gir FR-19. Alt annet er en feil.
  - Fast kodeliste i `shared/feilkoder.ts`: `UNSUPPORTED_FORMAT`, `FILE_TOO_LARGE`, `NO_TEXT` (for eksempel skannet PDF), `TEXT_TOO_LONG`, `DEMO_UNKNOWN_DOCUMENT`, `ANALYSIS_FAILED`, `ANALYSIS_TIMEOUT`, `INVALID_MODEL_RESPONSE`, `VALIDATION_FAILED`, `NOT_FOUND`, `STORE_UNREADABLE`, `INTERNAL`.
  - Serverens `message` er hele brukerteksten, inkludert eventuell demo-henvisning, og klienten legger ikke til noe.
  - `VALIDATION_FAILED` kan ha den valgfrie listen `felt?: { indeks?: number, felt: string }[]`.

### H8 – Anthropic-adapter mot kjernens frist og nye forsøk: tre lag som prøver på nytt (Middels)

- **Enhet A (adapter):** Bruker `new Anthropic()` med standardinnstillinger. SDK-en har da `maxRetries: 2` og et eget tidsavbrudd på 10 minutter. Det følger AD-9.
- **Enhet B (kjernen, AD-12):** Én frist på 120 s og «høyst ett nytt forsøk», implementert i pipelinen.
- **Konflikt:** Det blir opptil 2 × 3 = 6 kall i stedet for 2. Klienten i F6 kan dessuten ha sin egen `AbortController` på 120 s som løser ut før serveren rekker å svare med `ANALYSIS_TIMEOUT`. Brukeren får da en generell nettverksfeil i stedet for FR-20-meldingen.
- **Tiltak – presisering i AD-12:**
  - Adapteren lager klienten med `maxRetries: 0` og tar imot et `AbortSignal` fra kjernen.
  - Bare kjernen prøver på nytt: én gang, bare ved nettverksfeil, 429, 5xx eller overbelastning, og ikke ved 401, 400 eller ugyldig skjema.
  - Klienten har ingen egen frist under 130 s, og et tidsavbrudd i klienten vises med samme tekst som `ANALYSIS_TIMEOUT`.

### H9 – Kategorikoder: strukturert utdata i adapteren mot FR-17-mapping i kjernen (Middels–Lav)

- **Enhet A (adapter):** Bruker et verktøy- eller JSON-skjema med `enum` over de ni kodene, så modellen ikke kan svare med en ukjent kategori.
- **Enhet B (kjernen og demo-fasit):** Forventer fri tekst og mapper den. Fasitfiler bruker «Øvelser og oppdrag» eller `O`.
- **Konflikt:** FR-17-regelen «ukjent kategori → manglende» blir død kode i én vei og vanlig i den andre. Demo-fasiten matcher ikke, fordi den bruker `O` i stedet for `Ø`. I tillegg sier konvensjonen «uten æøå», mens verdien `Ø` *er* en æøå-verdi. Det er greit, men det bør stå eksplisitt.
- **Tiltak – konvensjon:**
  - `RaattForslag.kategori.verdi` er fri tekst.
  - `shared/tilKategorikode(s)` godtar bare en eksakt kode etter `rensTekst` og `toUpperCase`. Alt annet gir `manglende`.
  - Kodene lagres som de står i EXPERIENCE.md (`Ø`, `U`, `S`, `M`, `P`, `L`, `E`, `F`, `A`). Regelen «uten æøå» gjelder nøkkelnavn, ikke verdier.
  - Om adapteren bruker `enum`, er et valg i prompten. Kjernen må tåle begge deler.

### H10 – F4 og F8 oppdaterer klientens planliste ulikt, og samtidige skrivinger i samme prosess (Lav–Middels)

- **Enhet A (F4):** Fletter svaret fra POST eller PUT inn i lokal tilstand.
- **Enhet B (F8):** Henter planen på nytt med `GET`.
- **Konflikt:** To måter å endre tilstanden på, som kan gi ulik sortering eller utdaterte data i F1/F2 (FR-8: «oppdatert uten omstart»). På serveren er `PlanStore` lese–endre–skrive. To raske kall, som et dobbeltklikk eller en fullføring mens en PUT pågår, kan da miste en skriving i *samme* prosess. Det gjelder også med bare én fane, så «siste skriving vinner» under Deferred dekker ikke dette tilfellet.
- **Tiltak:**
  - Klienten har én plan-hook (`usePlan`) som eier listen og henter den på nytt med `GET` etter hver vellykket endring.
  - `PlanStore` kjører operasjoner i serie med en enkel løftekø (cirka 10 linjer, ingen låsefil).

### H11 – Ugyldig dato fra modellen mot datovelgeren i F7 (Lav)

- **Konflikt:** Kjernen markerer `"30.02.2027"` som `ugyldig` (FR-17) og sender verdien videre. En `<input type="date">` i F7 kan ikke vise den, så feltet blir tomt. Brukeren ser da «manglende» i praksis og mister det modellen faktisk foreslo (FR-21: «alle feltene vises»). Datoregelen kan også implementeres med `new Date(...) <` i én enhet og strengsammenligning i en annen.
- **Tiltak – presisering i AD-5:**
  - En ugyldig rå datoverdi beholdes som tekst og vises i statusmeldingen («Ugyldig dato fra analysen: «30.02.2027»»).
  - `shared/erGyldigDato` bruker regex og rundtur gjennom `new Date(y, m − 1, d)`.
  - Datoregelen sammenligner `ÅÅÅÅ-MM-DD`-strenger direkte.

### H12 – Validering og id: HTTP-laget mot kjernen (Lav)

- **Konflikt:** AD-7 sier at «serveren validerer», mens laget `server/http/` har «inn/ut-validering» og `server/core/` har «regler». Én story validerer bare i ruten, mens en annen kaller kjernen direkte fra en test eller et skript og får ingen validering. På samme måte kan id lages både i kjernen og i `PlanStore`.
- **Tiltak – én setning i AD-7:**
  - Ruten parser formen med `AktivitetInput`.
  - Kjernens skriveoperasjoner kaller `valider` (FR-2) uansett og lager `id`.
  - `PlanStore` laster og lagrer bare `{ schemaVersion: 1, aktiviteter: Aktivitet[] }` og kjenner ingen regler.

## Samlet forslag (minimalt)

| Nr. | Type | Innhold | Tetter |
| --- | --- | --- | --- |
| AD-16 | Ny AD | `RaattForslag` (port-utdata, også demo-fasit) og `Aktivitetsforslag` (API-utdata) i `shared/`. Bare kjernen lager `Aktivitetsforslag`. | H1, H9 |
| AD-17 | Ny AD | Alle API-kropper som zod-skjemaer i `shared/api.ts`, med `AktivitetInput` `.strict()`, `merknader: string`, envelope-former, UUID-id og fullføring som `{ aktiviteter }` uten forslags-id eller kildeutdrag | H2, H12 |
| AD-18 | Ny AD | Én valideringsfunksjon `valider()` i `shared/` eier `manglende` og `ugyldig`. KI-status gjelder til feltet er endret. | H3 |
| Konvensjon | Stramming | Tekstnormalisering: `rensTekst` og `sammenligningsnokkel` (NFC, `\s+` inkl. NBSP), og tomt kildeutdrag forkastes | H4 |
| Konvensjon | Ny | Tegntelling: `tellTegn` (kodepunkter etter CRLF → LF), ingen `maxLength`, og trimregler per felt | H5 |
| Konvensjon | Stramming | Opplasting: URI-kodet filnavn, format etter innhold, kroppsgrenser og global feilhåndterer | H6 |
| Konvensjon | Ny | Analyseutfall og fast feilkodeliste i `shared/`, der serveren eier hele meldingen | H7 |
| AD-12 | Presisering | SDK `maxRetries: 0`, bare kjernen prøver på nytt, og klienten venter i minst 130 s | H8 |
| AD-5 | Presisering | Ugyldig rå dato vises som tekst, datoregelen bruker strengsammenligning, og `erGyldigDato` | H11 |
| Konvensjon | Ny | Én `usePlan` som henter på nytt etter endring, og `PlanStore` som kjører i serie | H10 |

Til sammen er dette tre korte AD-er og cirka seks tabellrader. Ingen nye pakker, ingen ny teknologi.

## Det som holder

- Avhengighetsretningen og porter/adaptere er tydelige, og `client/` kan ikke importere fra `server/`.
- AD-1 (nøkkel og `127.0.0.1`), AD-2 (gjennomgang bare i minnet) og AD-3 (rename-skriving, nekte skriving ved skadet fil) gir ingen konfliktpar på eget nivå.
- AD-10 (serveren melder modus, ingen automatisk overgang) og AD-13 (ren tekst) er presise nok.
- AD-14 gir de injiseringspunktene som trengs for å teste H4, H5 og H8 deterministisk.
