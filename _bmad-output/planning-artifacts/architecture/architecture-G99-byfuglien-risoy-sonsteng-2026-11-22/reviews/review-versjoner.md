# Reviewer Gate — versjoner og teknologivalg

- **Gjennomgått:** `ARCHITECTURE-SPINE.md` (utkast 2026-11-22), seksjonene Stack, Consistency Conventions, AD-8–AD-12, AD-14 og lokal kjøring
- **Dato:** 2026-11-22
- **Rolle:** uavhengig reviewer (BMAD Architecture Reviewer Gate), fokus: er teknologivalgene kontrollert mot virkeligheten?
- **Metode:** `npm view` mot registeret for alle pakker (versjon, `engines`, `peerDependencies`), Node-utgivelsesplanen fra nodejs.org/GitHub, og en **røyktest**: et tomt prosjekt med nøyaktig de låste versjonene installert på Node 24.22.3 / npm 11.19.1, der hver påstand i spinen ble kjørt (se «Bevis» nederst).

## Konklusjon

**Godkjent med merknader.** Alle 14 versjonene i Stack-tabellen finnes, er `latest` på npm per i dag og fungerer sammen. Røyktesten bekrefter alle de konkrete påstandene (Express 5 `express.raw`, `--env-file`, ren-JS PDF-uttrekk, `.docx` til ren tekst, ISO-uker, `tsc --noEmit` med TS 7, Vite 8 + React 19.3, Vitest 5). Det er **ingen blokkerende funn**. Fire punkter bør rettes i spinen før bygging, fordi de ellers gir feil som først dukker opp i implementeringen eller hos sensor.

## Funn

| # | Alvor | Funn | Konkret retting |
|---|---|---|---|
| V-1 | **Middels** | **«Node >=24 (gjeldende LTS)» stemmer ikke.** Node 26 har vært Active LTS siden 2026-10-28. Node 24 er nå i Maintenance LTS (til 2028-04-30). `>=24` slipper dessuten inn Node 25 (EOL 2026-06-01), som Vitest 5.1.1 ikke støtter (`engines: ^22.12.0 \|\| ^24.0.0 \|\| >=26.0.0`). unpdf 2.2.1 krever `node >=24`, så 22 er riktig utelukket. | Skriv «Node.js 24 eller 26 (LTS)» og sett `"engines": { "node": "^24.0.0 \|\| >=26.0.0" }` i `package.json`. Bruk `.nvmrc` = 24 eller 26, og kjør CI på både 24 og 26. |
| V-2 | **Middels** | **SDK-ets standardoppførsel bryter AD-12.** `@anthropic-ai/sdk` 1.12.0 har `maxRetries = 2` og `timeout = 10 min` *per forsøk* som standard. Dokumentasjonen sier selv at tidsavbrudd prøves på nytt. AD-12 krever 120 s totalt og høyst ett nytt forsøk. | Legg til i AD-12 eller AD-9: adapteren lager klienten med `maxRetries: 1` (eller `0`, med egen retry) og sender `signal: AbortSignal.timeout(120_000)` (eller fristens signal fra kjernen) på hvert kall, slik at én frist avbryter alt. Lag en integrasjonstest med falsk leverandør som bekrefter at det skjer høyst 2 kall og avbrudd ved fristen. |
| V-3 | **Middels** | **TypeScript 7.0 (den native Go-porten) har nye standarder og har fjernet gamle valg.** Verifisert: (a) `types` er tom som standard, så `process` gir TS2591 uten `"types": ["node"]`. (b) `moduleResolution: node/node10`, `baseUrl` og `target: es5` gir harde feil (TS5108/TS5102). (c) `.ts`-endelser i import krever `allowImportingTsExtensions`. (d) Pakken `typescript` eksporterer ikke lenger det klassiske JS-API-et (`"."` peker til `lib/version.cjs`), så verktøy som bruker `require('typescript')` virker ikke (typescript-eslint, ts-node, vite-plugin-checker og lignende). tsx (esbuild), Vite 8 (rolldown/oxc), plugin-react 6 (oxc) og Vitest 5 bruker **ikke** typescript-API-et. Alle fungerte i røyktesten, og `tsc --noEmit` ga exit 0. | Legg til en linje i Stack eller Conventions: «tsconfig er skrevet for TS 7: `module`/`moduleResolution` `nodenext` (server/shared) og `bundler` (client), `types: ["node"]` for server og tester, ingen `baseUrl`». Legg `@types/node` (24.x, samme som runtime), `@types/express` 5.0.6, `@types/react` og `@types/react-dom` 19.3.0 inn i Stack-tabellen, fordi TS 7 ikke finner dem automatisk. Noter at ESLint (utsatt) må bruke en TS 7-kompatibel parser hvis den innføres senere. |
| V-4 | **Middels** | **Filnavn i header kan krasje opplastingen.** «Opplasting» sender filnavnet i en HTTP-header. `fetch` godtar bare tegn ≤ U+00FF i header-verdier. `Årsplan.docx` går gjennom, men `Plan – 2027.docx` (tankestrek U+2013), typografiske anførselstegn og emoji kaster `TypeError` i nettleseren før kallet sendes (verifisert med `Headers` i Node 24, samme WHATWG-regel som i Chrome og Edge). | Bestem i Conventions: filnavnet sendes `encodeURIComponent`-kodet (f.eks. `X-Filename`) og dekodes på serveren. Typen sendes i `Content-Type`. Legg til en enhetstest med et filnavn med æøå og tankestrek. |
| V-5 | Lav | **`--env-file` feiler hvis filen mangler.** `node --env-file=.env` avslutter med exit 9 når `.env` ikke finnes. Node 24 har `--env-file-if-exists`. | Bruk `--env-file-if-exists=.env` i `npm start`, slik at manglende nøkkel gir FR-20 (som AD-10 sier) og ikke krasj ved oppstart. `npm run demo` skal ikke lese `.env`. |
| V-6 | Lav | **Express 5 har ny syntaks for jokertegn i ruter.** `app.get('*')` kaster «Missing parameter name» (path-to-regexp v8). Dette gjelder hvis serveren skal levere `index.html` som reserve for klientruter i `npm run demo`. | Hvis du trenger SPA-reserve, bruk `'/{*splat}'`, eller bare `express.static` siden appen ikke har klientruting. Noter det i strukturseksjonen. |
| V-7 | Lav | **10 MB er tvetydig.** `express.raw({ limit: '10mb' })` betyr 10 × 1024 × 1024 byte og ga 413 `entity.too.large` som forventet. Klientsjekken må bruke det samme tallet. Express sin standard-feil må også oversettes til `{ code, message }` på norsk. | Definer `MAX_FILE_BYTES = 10 * 1024 * 1024` i `shared/` og send tallet (ikke strengen `'10mb'`) til `express.raw`. Feilhåndteringen mapper `entity.too.large` → `code: "file_too_large"` med norsk melding. |
| V-8 | Info | **Strukturert output er tilgjengelig, men spinen tar ikke stilling.** SDK 1.12.0 har `client.messages.parse({ output_config: { format: zodOutputFormat(schema) } })` fra `@anthropic-ai/sdk/helpers/zod`. Hjelperen importerer `zod/v4`, og den typesjekket mot zod 4.6.7. Peer-avhengigheten er `zod ^3.25 \|\| ^4`. Om valgt modell støtter strukturert output, må verifiseres i `npm run eval`. | Valgfritt: skriv i AD-9 at adapteren bruker `messages.parse` + `zodOutputFormat` med skjemaet fra `shared/`, og at AD-8 *uansett* validerer svaret med zod (modellen er ikke til å stole på). Da kan ikke et implementasjonsvalg gjøre om AD-8. |
| V-9 | Info | **Native binærfiler finnes bare i utviklingsverktøyene.** Runtime-kjeden (Express, mammoth, unpdf, zod, SDK) er ren JS. unpdf har med seg en serverless-build av pdf.js. `@napi-rs/canvas` er en *valgfri* peer-avhengighet som bare trengs til rendering, og den ble ikke installert. Vite 8 (rolldown, lightningcss), tsx (esbuild) og TS 7 (tsgo) henter ferdigbygde plattformbinærfiler via `optionalDependencies`, og det fungerer på Mac/Windows/Linux. npm 11.19 varsler at esbuilds `postinstall` ikke dekkes av `allowScripts`, men tsx virket likevel. | Commit `package-lock.json` (som planlagt) og bruk `npm ci`. Vurder en CI-matrise med `windows-latest` i tillegg til `ubuntu-latest` for å fange plattformfeil før sensor. Nevn npm-varselet i README som ufarlig. |
| V-10 | Info | **tsx er strengt tatt ikke nødvendig.** Node 24 fjerner typer innebygd (`process.features.typescript === 'strip'`), og `node server/extract.ts` kjørte. | Ingen endring kreves. tsx er et trygt valg og tåler `enum` og parameter properties. Hvis gruppen vil ha færre avhengigheter, kan den bruke `node --watch` + `erasableSyntaxOnly` i stedet. |

## Kontroll av hver Stack-rad

| Pakke | Spine | npm `latest` i dag | Engines / peer | Status |
|---|---|---|---|---|
| Node.js | >=24 | 26.13.1 (Active LTS), 24.22.3 (Maint. LTS) | — | Se V-1 |
| TypeScript | 7.0.2 | 7.0.2 (7.1.0-beta finnes) | node >=16.20 | OK, se V-3 |
| React / react-dom | 19.3.1 | 19.3.1 | react-dom peer `react ^19.3.1` | OK |
| Vite | 8.3.8 | 8.3.8 | node ^20.19 \|\| >=22.12 | OK |
| @vitejs/plugin-react | 6.3.0 | 6.3.0 | peer `vite ^8.0.0` | OK |
| Express | 5.3.0 | 5.3.0 | node >=18 | OK, se V-6/V-7 |
| tsx | 4.23.15 | 4.23.15 | node >=18, esbuild ~0.28 | OK |
| zod | 4.6.7 | 4.6.7 | — | OK, `z.iso.date()` avviser 2026-02-30 |
| @anthropic-ai/sdk | 1.12.0 | 1.12.0 | peer `zod ^3.25 \|\| ^4` (valgfri) | OK, se V-2/V-8 |
| mammoth | 1.13.0 | 1.13.0 | node >=12, typer medfølger | OK, `extractRawText` gir ren tekst med tabellceller |
| unpdf | 2.2.1 | 2.2.1 | **node >=24** | OK, ren JS |
| date-fns | 4.4.0 | 4.4.0 | — | OK, `getISOWeek`, `getISOWeekYear`, `startOfISOWeek` |
| Vitest | 5.1.1 | 5.1.1 | node ^22.12 \|\| ^24 \|\| >=26, peer `vite ^6\|\|^7\|\|^8` | OK, se V-1 |
| concurrently | 10.0.7 | 10.0.7 | node >=22 | OK |
| Playwright | utsatt | @playwright/test 1.65.1 | — | OK å utsette |
| *(mangler)* @types/node, @types/express, @types/react, @types/react-dom | — | 26.6.6 / 5.0.6 / 19.3.0 / 19.3.0 | — | Legg til, se V-3. Bruk `@types/node@24` (eller 26) så typene følger runtime |

Setningen «Versjonene er kontrollert mot npm-registeret 2026-11-22» stemmer for alle radene.

## Bevis (røyktest, Node 24.22.3 / npm 11.19.1)

- `npm i --save-exact` med alle 14 pakkene: 177 pakker, 0 sårbarheter, ingen peer-konflikter
- `tsc --noEmit` (TS 7.0.2) på server/shared/client/test: exit 0 (etter `allowImportingTsExtensions`)
- `node --env-file=.env --import tsx server/main.ts`: env-variabelen ble lest. Express 5 `express.raw` tok imot 3 byte og filnavn fra header (200), og 11 MB ga 413 `entity.too.large`
- `date-fns`: `getISOWeek(2026-12-31) = 53`, `getISOWeekYear(2027-01-01) = 2026`, `startOfISOWeek(2026-01-01) = 2025-12-29`
- `mammoth.extractRawText` på en .docx med æøå og en tabell: `"Årsplan 2027\n\nØvelse Nordlys uke 12, …\n\nStart 2027-03-22\n\nSlutt 2027-03-26"`
- `unpdf` `extractText(…, { mergePages: true })` på en 2-siders PDF: riktig tekst med æøå, ingen `canvas` installert
- Vitest 5.1.1: 3/3 tester grønne (grensen 5 000 mot 5 001 kodepunkter, også med emoji; ISO-uke 53; zod-dato)
- `vite build` (Vite 8 + plugin-react 6 + React 19.3): bygget på 100 ms
- `new Headers({ 'x-filename': 'Plan – 2027.docx' })`: TypeError (V-4)
- `node --env-file=.env.missing`: exit 9 (V-5). `app.get('*')` i Express 5 kaster (V-6)
- tsconfig med `types` utelatt: TS2591 for `process`. `baseUrl`, `moduleResolution: node` og `target: es5`: TS5102/TS5108 (V-3)
