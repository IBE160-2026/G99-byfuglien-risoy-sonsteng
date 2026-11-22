# Reviewer Gate – rubrikkgjennomgang av ARCHITECTURE-SPINE.md

- **Gjennomgått:** `ARCHITECTURE-SPINE.md` (utkast 2026-11-22), Sambandet v1
- **Målt mot:** PRD (FR-1–FR-30, NFR-1–NFR-10, C-1–C-8, OQ-6/7/8), EXPERIENCE.md og DESIGN.md (utkast 2026-11-13)
- **Rolle:** uavhengig rubrikkgjennomgang. Spinen er ikke endret. `.memlog.md` finnes ikke i denne klonen, så begrunnelser er ikke kontrollert.
- **Dato:** 2026-11-22

## Konklusjon

**Godkjent med endringer.** Spinen har riktig nivå og omfang for et lite lokalt prosjekt med tre studenter. Den er ikke overdimensjonert: tre porter, én JSON-fil, ingen router-, state- eller UI-bibliotek. Alle FR-, NFR- og C-krav har en plass, eller dekkes av UX. Stack-versjonene er reelle og gjeldende. Ingen funn er kritiske. To funn er **høye** og bør rettes før gruppevedtaket. Begge gjelder steder der to stories eller to maskiner kan ende ulikt: `--env-file` kan stoppe oppstart uten `.env`, og utfallene av analysen og feilkodene er ikke fastsatt. Resten er medium og lav og kan som regel løses med én setning i en eksisterende AD eller konvensjon.

## Rubrikk

| Kriterium | Vurdering | Kommentar |
| --- | --- | --- |
| Fastsetter de reelle avvikspunktene for nivået under | Delvis | Kjernen er dekket: lagring, datoer, delt domene, validering, pipeline og demo. Mangler: utfall og feilkoder for analysen (F1), størrelsesgrense for JSON-kroppen (F3) og hvordan kategorilisten kommer inn i KI-instruksjonene (F5). |
| Hver AD-regel kan håndheves og hindrer avviket den nevner | Stort sett | AD-3 hindrer ikke samtidige skrivinger i samme prosess (F4). AD-12 «høyst ett nytt forsøk» holder ikke hvis SDK-ens egne nye forsøk står på (F6). |
| Ingenting i Deferred kan gi avvik mellom enheter | Ja, med ett forbehold | «Samtidige faner: siste skriving vinner» forutsetter at PlanStore utfører én operasjon om gangen. Det står ikke (F4). Øvrige punkter er trygge. |
| Navngitt teknologi er kontrollert og gjeldende | Ja | Alle 14 pakkeversjoner finnes i npm-registeret og er `latest` per 2026-11-22. Peer-krav og engines passer sammen (unpdf og Vitest krever Node ≥24 / ^24). Små merknader i F10. |
| PRD-dekning (FR/NFR/C) | Ja | Se dekningstabellen. NFR-4, NFR-5, NFR-6, C-1 og C-5–C-8 mangler egen rad i kapabilitetskartet (F11). |
| Driftsrammen (miljøer, lokal kjøring, CI) er avgjort | Delvis | Skript, port, konfigurasjon og CI er beskrevet. `--env-file` er feil valg (F2). CI bygger ikke klienten, som er sensors vei (F9). Det står ikke at Express serverer den bygde klienten i `demo`/`start` (F9). |
| Stille motsigelser mot PRD/UX eller krav som har falt ut | Små | Stikkprøvene i Firefox og Safari fra eierens OQ-8-vedtak er falt ut (F12). NFR-8 krever at nettleserne står i README. Det er ikke nevnt (F12). |

## Funn

### F1 – Utfall og feilkoder for `POST /api/analyze` er ikke fastsatt · **høy**

- **Sted:** Consistency Conventions › Feilformat i API, Structural Seed › API-kontrakt, AD-8/AD-10/AD-11
- **Problem:** Feilformatet `{ code, message }` er fastsatt, men verken kodene eller utfallene er det. Klienthistorien (F6/F7) og pipelinehistorien må enes om minst disse utfallene:
  - for stor fil (NFR-2)
  - ikke støttet format (FR-15)
  - PDF uten tekst (FR-15)
  - for lang tekst (AD-12)
  - ukjent dokument i demo-modus (FR-18)
  - ingen aktiviteter funnet (FR-19)
  - tidsavbrudd (NFR-3)
  - leverandørfeil eller manglende/ugyldig nøkkel (FR-20)
  - ugyldig modellsvar (FR-20)
  - planfilen er skadet (AD-3)
  - lagringsfeil (NFR-1)

  Det er heller ikke avgjort om FR-19 er en feil eller et vellykket svar med tom liste. UX gir dem ulike flater: FR-20-meldingen skal nevne demo-modus, FR-18 skal ikke. Uten en fast liste blir resultatet ulike strenger og ulik HTTP-status, og NFR-4-gjennomgangen kan ikke sjekkes mot én liste.
- **Tiltak:** Legg til i konvensjonen: «Alle feilkoder er én `const`-union i `shared/` (`ErrorCode`). Server og klient importerer den. Ingen andre koder brukes.» List kodene og tilhørende HTTP-status i spinen. Fastsett at FR-19 er `200` med `forslag: []`, og at klienten viser FR-19-meldingen. Fastsett at bare FR-20-kodene får demo-setningen.

### F2 – `.env` lastes med `--env-file`, så appen starter ikke når `.env` mangler · **høy**

- **Sted:** Consistency Conventions › Konfigurasjon, Lokal kjøring (`npm start`, `npm run demo`), AD-10
- **Problem:** `node --env-file=.env` avslutter med feil når filen ikke finnes. Kontrollert med Node 22: `node: .env: not found`, exit 9. Det bryter AD-10 («uten nøkkel i vanlig modus starter appen normalt»). Bruker `demo`-skriptet det samme flagget, stopper også sensors vei (C-5) på en ren klone.
- **Tiltak:** Bruk `--env-file-if-exists=.env` (Node ≥22.9, dermed dekket av Node ≥24). Skriv i spinen at `npm run demo` aldri krever `.env`. Legg til en CI-sjekk eller test som starter `demo` uten `.env`.

### F3 – Standardgrensen for JSON-kroppen i Express (100 kB) avviser store fullføringer · **medium**

- **Sted:** AD-2 (fullføring i ett kall), AD-12, Consistency Conventions › Opplasting
- **Problem:** `express.json()` har en standardgrense på 100 kB. En fullføring med 20 forslag og merknader nær 5 000 tegn er 100 000 tegn og opptil 400 kB i UTF-8. Den får `413`, og svaret kommer fra Express sin standard feilbehandler, ikke i `{ code, message }`. `express.raw()` har samme grense på 100 kB, så opplasting på opptil 10 MB krever at grensen settes eksplisitt.
- **Tiltak:** Legg til i AD-12: «JSON-grensen og grensen for rå bytes settes eksplisitt fra konstantene i `shared/` (for eksempel JSON 2 MB og rå bytes = maks filstørrelse). En global feilbehandler gjør alle feil, også 413 og parsefeil, om til `{ code, message }`.»

### F4 – PlanStore gjør ikke én operasjon om gangen · **medium**

- **Sted:** AD-3, Deferred › Samtidige faner
- **Problem:** Lesing, endring, skriving til temp-fil og rename er asynkront i Node. To kall som overlapper, for eksempel en sletting og en fullføring, eller to faner, kan lese den samme gamle planen. Da forsvinner den ene endringen. Det er ikke «siste skriving vinner per operasjon», som Deferred lover. Bruker begge kallene samme navn på temp-filen, kan de også ødelegge hverandres skriving. I tillegg kan `rename` over en eksisterende fil på Windows feile med `EPERM`/`EBUSY` når antivirus eller indeksering holder filen.
- **Tiltak:** Legg til i AD-3: «PlanStore utfører én operasjon om gangen, med en enkel løftekø i minnet. Temp-filen har et unikt navn. Feiler rename, prøves den noen få ganger kort, og ellers gir den lagringsfeil (NFR-1).» Det er nok med noen få linjer kode. Det trengs ikke noe bibliotek.

### F5 – Kategorilisten i KI-instruksjonene kommer ikke fra `shared/` · **medium**

- **Sted:** AD-6, AD-9
- **Problem:** AD-6 sier at kategorilisten importeres overalt, også i KI-instruksjonen. AD-9 legger instruksjonene som versjonerte tekstfiler i `prompts/`. En tekstfil kan ikke importere `shared/`, så kategorinavn og koder blir lett skrevet inn for hånd og kan komme i utakt. Det samme gjelder svarskjemaet, hvis det beskrives i prompten. Dessuten finnes `prompts/` allerede i repoet med `chatgpt-kontrollagent.md`, som er en masterprompt for gruppens ChatGPT-kontrollagent og ikke en app-instruksjon. Mappen får da to formål.
- **Tiltak:** Skriv i AD-9: «Instruksjonsfilene er maler. Kategorilisten og skjemaet settes inn fra `shared/` når appen kjører.» Bruk structured output eller tool use med skjemaet fra `shared/` (zod til JSON-skjema). Legg app-instruksjonene i en egen undermappe, for eksempel `prompts/analysis/`, eller i `server/adapters/anthropic/prompts/`, og nevn at `prompts/chatgpt-kontrollagent.md` er utenfor appen.

### F6 – SDK-ens egne nye forsøk og frist er ikke tatt med i AD-12 · **medium**

- **Sted:** AD-12, AD-8, AD-9
- **Problem:** `@anthropic-ai/sdk` har egne nye forsøk (standard `maxRetries` 2) og en egen lang frist. Slås ikke disse av, gjør appen opptil 2 × 3 forsøk, og «høyst ett nytt forsøk» og «én frist avbryter alt» gjelder ikke. Det står heller ikke hvilke feil som gir nytt forsøk: nettverk og 5xx/529, eller også ugyldig skjema.
- **Tiltak:** Legg til i AD-9/AD-12: «Klienten opprettes med `maxRetries: 0`. Pipelinen gjør høyst ett nytt forsøk, og bare ved nettverksfeil, 429 eller 5xx. Ett `AbortSignal` fra fristen på 120 s sendes inn i SDK-kallet.» Kontroller SDK-standardene i 1.12.0 når dette bygges.

### F7 – Opplasting: filnavn i header og format ut fra MIME-type · **medium**

- **Sted:** Consistency Conventions › Opplasting, AD-8 (grensesjekk/tekstuttrekk)
- **Problem:** En HTTP-header tåler bare ByteString. Et filnavn med tegn utenfor Latin-1, for eksempel en tankestrek, får `fetch` til å kaste feil i nettleseren. På Windows uten Office gir `File.type` ofte en tom streng for .docx, så formatet kan ikke avgjøres ut fra typen klienten oppgir.
- **Tiltak:** «Filnavnet sendes `encodeURIComponent`-kodet og brukes bare i meldinger. Serveren avgjør formatet ut fra filsignaturen (`%PDF-` eller ZIP med `word/document.xml`), ikke ut fra headeren. Tom tekst etter normalisering gir koden for PDF uten tekst.»

### F8 – Plassering av gjennomgangstilstanden og navigasjon i klienten · **lav–medium**

- **Sted:** AD-2, Structural Seed
- **Problem:** FR-26 krever at brukeren kan gå fra gjennomgangen til årshjulet og tilbake uten å miste noe. Ligger tilstanden i en visningskomponent, forsvinner den når komponenten fjernes. Ingen router er valgt eller utelukket. En story som legger til `react-router`, kan også gjøre at omlasting og tilbake-knappen oppfører seg annerledes enn UX forventer.
- **Tiltak:** Én setning i AD-2: «Gjennomgangen holdes i tilstand på app-nivå (React-kontekst eller `useReducer` øverst i treet), over visningsbyttet. Visningen styres av app-tilstand uten router-bibliotek.» Det kan også legges under Deferred med denne rammen.

### F9 – Driftsrammen: CI bygger ikke klienten, og statisk servering er ikke nevnt · **lav**

- **Sted:** Structural Seed › Lokal kjøring, `.github/workflows/`
- **Problem:** Sensors vei (`npm run demo`) bygger klienten med Vite, men CI kjører bare `npm ci`, typecheck og test. En feil i Vite-bygget blir derfor først oppdaget hos sensor. Det står heller ikke at Express serverer `dist/` i `demo` og `start`, eller hvordan serveren kjøres (tsx eller kompilert). Eieren har lagt vekt på Mac og Windows, men CI kjører trolig bare på Linux.
- **Tiltak:** Legg til `npm run build` i CI, gjerne med et enkelt oppstartstest av `demo` uten `.env` (jf. F2). Skriv at Express serverer den bygde klienten, og at serveren kjøres med `tsx` (avhengigheten må da ligge i `dependencies`). Valgfritt: én `windows-latest`-jobb.

### F10 – Merknader til stacken · **lav**

- **Sted:** Stack
- Node: «>=24 (gjeldende LTS)». I november 2026 er Node 26 Active LTS og Node 24 Maintenance LTS. Kravet ≥24 er riktig fordi unpdf krever det, men teksten bør si «≥24 (LTS)». Legg inn `engines` og eventuelt `.nvmrc`, og skriv kravet i README (C-5).
- TypeScript 7.0.2 er den native kompilatoren og har ikke den gamle programmatiske API-en. Det går fint så lenge ingen verktøy trenger den, og ESLint er utsatt. Skriv som reserve: «Trenger et verktøy TS-API-et, brukes 6.x.»
- `@types/node`, `@types/express`, `@types/react` og `@types/react-dom` står ikke i listen, men trengs for `tsc --noEmit`.

### F11 – Kapabilitetskartet mangler noen krav · **lav**

- **Sted:** Capability → Architecture Map
- NFR-4 (feilformat, F1), NFR-5 (fremdrift i F6, bare i klienten), NFR-6 (beregning i klienten over hele planen, ingen egne API-kall ved navigasjon), NFR-7 og NFR-8 (AD-15 og manuell sjekkliste), C-1 (merkede testdokumenter), C-5 (`npm run demo`), C-6 (127.0.0.1, én bruker), C-7 (AD-4, AD-8) og C-8 (konvensjonen for språk i kode) dekkes alle, men har ingen egen rad. FR-16 står bare indirekte under AD-8. Legg til to eller tre rader slik at sporingen blir fullstendig.

### F12 – Små motsigelser og krav som har falt ut · **lav**

- **AD-12 og nettlesere:** Eieren vedtok «Edge og Chrome primært, med stikkprøver i Firefox og Safari». Stikkprøvene er falt ut. NFR-8 krever at nettleserne står i README.
- **Kategorikoder:** Konvensjonen sier at domenefelt skal være uten æøå, mens koden `Ø` er en verdi med Ø. Skriv eksplisitt at kodene lagres nøyaktig som i UX (`Ø, U, S, M, P, L, E, F, A`) og at filen er UTF-8. Da blir ingen fristet til å «rette» koden til `O`.
- **AD-12 og merknader:** Telling i kodepunkter med `\r\n` → `\n` bør skje i én funksjon i `shared/`, slik at telleren i F4 og validering på serveren gir samme tall.
- **AD-5 og FR-9:** «Dagens dato» må regnes ut i lokal tid. `toISOString()` gir UTC og kan gi feil år rundt midnatt nyttårsaften. Legg til en `today()`-hjelper i `shared/`.
- **AD-11 og hashavvik:** En ny versjon av mammoth eller unpdf kan endre den uttrukne teksten, og demo-treffene forsvinner da uten varsel. Legg til en test som henter ut tekst fra alle filer i `testdata/` og sjekker hashene mot manifestet. Den passer inn i NFR-10, «demo-modus mot fasit».
- **C-2:** PRD-en krever at valget av modell og leverandør begrunnes *i arkitekturen*. Spinen har ingen begrunnelse for Anthropic, og memloggen mangler i klonen. Skriv én setning i AD-9, og si hvor modellvalget etter `npm run eval` dokumenteres.
- **AD-1 (valgfritt):** Lokale tjenester kan nås fra andre nettsider gjennom DNS-rebinding eller CSRF. En kontroll av `Host`-headeren (127.0.0.1 eller localhost) og krav om `Content-Type: application/json` på JSON-ruter er billig, men ikke nødvendig med fiktive data.

## Dekningskontroll (kort)

| Krav | Plass i spinen | Status |
| --- | --- | --- |
| FR-1–FR-7 | AD-3, AD-4, AD-5, AD-6, AD-7; API | OK (F4) |
| FR-8–FR-14 | `client/` SVG, AD-5, AD-15; UX | OK |
| FR-15–FR-20 | AD-8–AD-12 | OK, men utfallene mangler (F1, F7) |
| FR-21–FR-26 | AD-2, AD-7; commit-API | OK (F3, F8) |
| FR-27–FR-30 | AD-8, AD-11, AD-13; normalisering | OK |
| NFR-1–NFR-3 | AD-3, AD-8, AD-12 | OK (F4, F6) |
| NFR-4–NFR-8 | Feilformat, AD-15, AD-12, manuell sjekkliste | Delvis uten rad i kartet (F11) |
| NFR-9 | AD-1, AD-9, AD-13 | OK |
| NFR-10 | AD-14 | OK |
| C-1–C-8 | AD-1, AD-9, AD-4, konvensjoner, skript | OK (F2 truer C-5) |
| OQ-6 / OQ-7 / OQ-8 | AD-9 + Deferred / AD-10–AD-11 / AD-12 | Avgjort |

## Ting som ikke bør endres

Spinen holder seg bevisst liten. Følgende er riktig nivå og bør ikke utvides:

- ingen database
- ingen router- eller state-bibliotek
- ingen multipart-bibliotek
- ingen ESLint
- Playwright som «bør»
- manuell NFR-7-sjekkliste

Tiltakene over kan alle gjøres med noen få setninger i eksisterende AD-er og konvensjoner. Ingen av dem krever nye AD-er.
