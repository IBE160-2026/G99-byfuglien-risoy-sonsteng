# Ad hoc-review: brief, beslutninger og kravlogikk (Validate PRD)

**Dato:** 2026-11-01
**Gjennomgått:** `product-brief.md` (forkortet 2026-11-01), `prd.md`, `.memlog.md`, `CLAUDE.md`, `AGENTS.md`, `docs/ki-logg/2026-11-01-product-brief-validering.md`, `git diff d128796 HEAD` for briefen. Bare filer i scratchpad er skrevet. Repoet er ikke endret.

## Konklusjon

**Betinget klar for UX Design.** Ingen kritiske funn og ingen reelle konflikter mot memlog. Strukturen i PRD-en holder.

Ett funn bør avgjøres før UX starter:
- **F1:** Briefens regel om at frister registreres som aktiviteter, finnes ikke i PRD-en, og FR-17 gir feil eller udefinert resultat for frister.

F2–F4 er produktbeslutninger gruppen bør ta før eller i starten av UX, fordi de styrer utformingen av gjennomgangen. F5–F10 kan rettes i samme oppdatering. De lave funnene er opprydding.

| Alvorlighet | Antall | Funn |
|---|---|---|
| Critical | 0 | |
| High | 1 | F1 |
| Medium | 9 | F2–F10 |
| Low | 8 | F11–F18 |

Skalaen måler konsekvens for overgangen til UX Design, ikke hvor alvorlig saken er for produktet på sikt.

---

## High

### F1. Frister: briefens regel mangler i PRD-en, og FR-17 håndterer dem ikke

- **Referanse:** Brief §7 IN 2. PRD Glossary, FR-17, UJ-1 E6. KI-logg, Videreføringspunkter.
- **Brief:** «Frister registreres som aktiviteter.»
- **PRD:** Ordet «frist» står bare i §1, JTBD og UJ-1 persona. Det finnes verken som krav eller i Glossary. Glossary sier: «Aktivitet — En planlagt hendelse lagret i planen.» FR-17 sier: «KI antar ikke at en aktivitet varer én dag bare fordi dokumentet angir én dato» og «Gir dokumentet ingen holdepunkter for aktivitetens varighet, markeres sluttdatoen som *manglende*.»
- **KI-logg:** «Datoene er like for éndagsaktiviteter og frister. For frister er dette Risøys presisering. PRD-en sier det ikke uttrykkelig.»
- **Scenario:** Ordren sier «Rapport leveres innen 15. mars». Regelen om tydelig éndagsaktivitet treffer ikke, for dokumentet beskriver en leveringsfrist. Etter FR-17 kan sluttdatoen bli *manglende*, selv om gruppens presisering sier at begge datoer skal være 15. mars. PRD-en sier heller ikke om datoen er startdato eller sluttdato.
- **Konsekvens:**
  - Alle frister kan kreve manuell utfylling, som svekker briefens mål om mindre manuell registrering.
  - Fasit for SM-3 og demo-modus (FR-18, FR-30) kan ikke fastsettes entydig.
  - UX får ikke vite om frister skal se annerledes ut. Loggens punkt «Vurdere om frister skal ha egen kategori» står ikke i OQ-3.
- **Vurdering av tidligere kontroll:** Loggen konkluderte med at dette ikke krevde endring («Brukeren fyller da inn datoen»). Det holder ikke når loggen samtidig fastsetter at datoene for frister skal være like.
- **Minimal retting:**
  1. Legg til Glossary-begrepet «Frist — aktivitet med startdato lik sluttdato lik fristdatoen».
  2. Legg til en konsekvens i FR-17: «Angir dokumentet en frist, foreslås fristdatoen som startdato og sluttdato.»
  3. Speil regelen i UJ-1 E6.
  4. Legg spørsmålet om egen fristkategori inn i OQ-3.

---

## Medium

### F2. Delvise datoer og datoer uten år er udefinert, og aktiviteten kan havne utenfor visningen

- **Referanse:** FR-17, UJ-1 E6, FR-9, FR-23, UJ-1 Klimaks.
- **PRD:** Alle datoreglene i FR-17 gjelder én eksakt dato eller sluttdato. E6 sier: «Dokumentet angir bare én dato for en aktivitet.» Startdato har ingen egen regel utover «Felt uten verdi er markert som *manglende*». FR-9 sier: «Etter bytte vises bare aktiviteter som berører valgt kalenderår.» FR-23 sier at en godkjent aktivitet «vises i årshjulet (FR-8)».
- **Scenario 1:** Ordren sier «Skyteøvelse i uke 12» eller «i løpet av april». Ingen regel sier om KI skal foreslå første dag med *usikker*, eller markere feltet som *manglende*. To kjøringer kan gjøre ulikt, og SM-3 («hvor korrekt startdato og sluttdato ble identifisert») får ingen fasit.
- **Scenario 2:** Ordren sier «15. mars» uten år, og KI foreslår feil år. Berg godkjenner i visningen for 2026, men aktiviteten havner i 2027. Den synes ikke i gjeldende visning, og PRD-en krever ingen tilbakemelding om det.
- **Konsekvens:** Datohåndtering er kjernen i KI-kvaliteten, og UX mangler regel for hva brukeren skal se og rette.
- **Minimal retting:**
  1. Legg én konsekvens i FR-17: uke, måned eller periode uten eksakt dato, og dato uten år, gir enten *manglende* eller et forslag med *usikker*. Gruppen velger.
  2. Legg en konsekvens i FR-23: brukeren får beskjed når en godkjent aktivitet ligger utenfor kalenderåret som vises.

### F3. Ny opplasting etter delvis godkjenning er ikke en fortsettelse, men gir nye duplikater

- **Referanse:** FR-26, UJ-1 E5, C-3, FR-25.
- **PRD:** «Lukkes applikasjonen eller lastes den på nytt, går ubehandlede forslag tapt. Brukeren må laste opp dokumentet på nytt for å fortsette.» FR-26 Out of Scope: «Automatisk konfliktanalyse, inkludert kontroll av duplikater eller overlapp». C-3: «Eksisterende aktiviteter i planen sendes ikke.»
- **Memlog:** «Automatic conflict analysis and duplicate/overlap checks against existing activities out of scope in v1». Avgrensningen er altså bevisst og riktig, men følgen av den er ikke beskrevet.
- **Scenario:** Berg godkjenner 3 av 8 forslag og avviser 2, så krasjer nettleseren. Ny opplasting gir alle 8 igjen, gjerne med andre titler, også de godkjente og avviste. Godkjenner Berg ett av dem på nytt, ligger aktiviteten dobbelt i planen, og ingenting varsler om det.
- **Konsekvens:** «For å fortsette» lover noe produktet ikke gjør. UX vet ikke at flyten trenger støtte for dette, for eksempel at brukeren kan se planen ved siden av eller får en advarsel før forslag går tapt.
- **Minimal retting:** Bytt ut «for å fortsette» med: «Ny opplasting gir en ny analyse. Alle aktivitetsforslag kan komme tilbake, også de som er godkjent eller avvist, og brukeren må selv unngå duplikater.» Legg til OQ-5: «støtte for å unngå duplikater ved ny analyse, og eventuell advarsel før ubehandlede forslag går tapt».

### F4. Når forkastes gamle forslag hvis ny opplasting eller analyse feiler?

- **Referanse:** FR-15, FR-26, UJ-1 E8, FR-18, FR-19, FR-20.
- **PRD:** FR-26: «får brukeren beskjed om at de vil forkastes, og må bekrefte før analysen starter.» FR-20 og FR-19 sikrer bare at «planen er uendret», og sier ingenting om eksisterende forslag.
- **Scenario:** Berg har 5 ubehandlede, redigerte forslag og laster opp et nytt dokument. Berg bekrefter, og så er dokumentet skadet, språkmodellen svarer ikke (NFR-3), analysen finner ingenting (FR-19), eller demo-modus støtter ikke dokumentet (FR-18). Forkastes de ved bekreftelsen, står Berg uten noe. PRD-en sier ikke hvilket tidspunkt som gjelder.
- **Konsekvens:** Tekst og flyt i bekreftelsen kan ikke utformes uten svaret (OQ-5). Tapt arbeid er en reell risiko.
- **Minimal retting:** Legg en setning i FR-26: «Forslagene forkastes først når den nye analysen har gitt aktivitetsforslag. Feiler den, beholdes de.» Alternativet er at de forkastes ved bekreftelse, med tekst som sier det. Gruppen velger.

### F5. OQ-3–OQ-10 mangler eier, og «testplanen» har ingen hjemmeworkflow

- **Referanse:** §0, §10.3–§10.5, SM-2.
- **PRD:** §10.1 og §10.2 har «*(eier: gruppen)*». §10.3–§10.5 har ingen eier. §0 nevner «de neste BMAD-workflowene: UX, arkitektur og epics og stories», ikke testplan. SM-2: «Testplanen angir hvilke krav som inngår.»
- **Kontroll:** Det finnes ingen testplan eller henvisning til en testplan i repoet utenfor PRD-mappen, KI-loggen og `.logs`.
- **Konsekvens:**
  - OQ-9 og OQ-10 kan bli liggende. SM-2 er et MVP-kriterium som er tomt til testplanen finnes.
  - Fasit og testdokumenter trengs også til demo-modus (FR-18, FR-30), så det må skje før implementering.
  - KI-loggens videreføringspunkter for testplanen er ikke registrert noe sted i PRD-en.
- **Minimal retting:** Sett «eier: gruppen» eller navngitt medlem på §10.3–§10.5. Si i §10.5 hvor og når testplanen lages, for eksempel «egen fil i planning-artifacts, ferdig før epics og stories». Før loggens testplanpunkter inn i OQ-9 og OQ-10.

### F6. Tegngrensen for merknader er utsatt uten OQ, og godkjenning over grensen er uavklart

- **Referanse:** FR-6, OQ-5, OQ-8, FR-2, FR-23.
- **PRD:** FR-6: «Grensen fastsettes i arkitekturen.» og «Håndteringen avgjøres i UX-workflowen og arkitekturen.» OQ-8 lister: «Lagringsløsning, tidsgrense for analyse, maksimal dokumentstørrelse og hvilke nettlesere som støttes.» Verken OQ-5 eller OQ-8 nevner tegngrensen eller FR-6.
- **Scenario:** KI foreslår en merknad over grensen. FR-2 og FR-23 sier ikke om den blokkerer godkjenning, for merknader er ikke obligatoriske.
- **Konsekvens:** Dette er den eneste tallgrensen i PRD-en som ikke er sporet, og memlog-beslutningen (linje 144 og 147) blir lett glemt.
- **Minimal retting:** Legg «tegngrense for merknader (FR-6)» til OQ-8 og «håndtering av merknader over grensen (FR-6, FR-23)» til OQ-5.

### F7. Briefens to nye suksesskriterier er ikke ført inn i Success Metrics

- **Referanse:** Brief §6 User outcome og Business / mission. SM-1, SM-4, Counter-metrics.
- **Brief:** «I brukertest kan brukeren finne ut når en aktivitet skjer og hvem som har ansvaret, uten å åpne andre filer.» og «Løsningen regnes som mer effektiv dersom oppgaven tar kortere tid uten flere feil sammenlignet med en forhåndsdefinert fasit.»
- **PRD:** SM-1 omtaler bare «de sentrale arbeidsflytene». SM-4 registrerer tid og feil, men har ikke noe vurderingskriterium. Counter-metric dekker bare halve regelen: «Er applikasjonen raskere, men gir flere feil mot fasit enn Excel (SM-4), er det ingen gevinst.» §9 sier også: «Resultatene i §9.2 og §9.3 er veiledende.»
- **Konsekvens:** Kriteriene er lagt til etter at PRD-en ble ferdig, og har ingen sporing. Oppgaven er delvis dekket av UJ-3 Klimaks. KI-loggen sier at den «kan tas inn i testplanen», men OQ-9 og OQ-10 nevner det ikke. For UX betyr det at finn-når-og-hvem-oppgaven ikke er et uttalt designmål.
- **Minimal retting:** Legg til i SM-1: «inkludert å finne når en aktivitet skjer og hvem som har ansvaret, uten å åpne andre filer». Legg til i SM-4: «Regnes som mer effektiv når oppgaven tar kortere tid uten flere feil mot fasit.» Behold merknaden om «veiledende».

### F8. Kategorilisten er en produktbeslutning uten svar på «ingen kategori passer»

- **Referanse:** Glossary Kategoriliste, OQ-3, FR-2, FR-17.
- **PRD:** «Innholdet fastsettes i UX-workflowen.» og «Kategorier utenfor kategorilisten kan ikke velges eller opprettes.» Kategori er obligatorisk.
- **Memlog:** Linje 55 plasserer dette bevisst i UX-workflowen, så det er ingen konflikt.
- **Vurdering:** Innholdet er en domeneavgjørelse for gruppen (troppssjefens språk), ikke en designfrase. Plasseringen er akseptabel hvis gruppen faktisk avgjør det. Det er ikke presisert.
- **Scenario:** Berg skal registrere en aktivitet som ikke passer noen kategori. Lagring er umulig (FR-2). Hvis lista får «Annet», mister FR-17 sin *manglende*-regel mye av innholdet, for KI kan alltid velge «Annet».
- **Minimal retting:** Utvid OQ-3 med: «Beslutningen tas av gruppen. Må dekke alle aktiviteter, avgjøre om lista har en restkategori og om frister har egen kategori.»

### F9. Demo-aktivering (OQ-7) er også et UX-spørsmål, og manglende API-nøkkel er ikke beskrevet

- **Referanse:** OQ-7, OQ-5, FR-18, FR-20, C-5.
- **PRD:** OQ-7: «Hvordan demo-modus aktiveres, og hvordan støttede testdokumenter gjenkjennes.» (arkitektur). C-5: «Det krever ikke gruppens nøkler». FR-20 dekker «ikke tilgjengelig», men ikke manglende nøkkel.
- **Memlog (linje 74):** «no advanced mode control or arbitrary documents». Denne avgrensningen står ikke i PRD-en.
- **Scenario:** En sensor kloner repoet uten nøkkel og starter applikasjonen. PRD-en sier ikke om den starter i demo-modus, viser et valg, eller feiler først ved opplasting. UX kommer før arkitektur og må vite om det finnes en bryter i grensesnittet.
- **Vurdering:** Gjenkjenning av testdokumenter er teknisk og hører hjemme i arkitekturen. Aktiveringen er delvis en produktbeslutning.
- **Minimal retting:** Legg til i FR-18: «Uten API-nøkkel får brukeren en tydelig melding om at analyse med språkmodellen ikke er tilgjengelig, og hvordan demo-modus brukes. Ingen avansert modusstyring i v1.» Legg en henvisning fra OQ-5 til OQ-7.

### F10. FR-3 krever åpning fra årsvisningen, FR-13 tillater månedsvisningen i stedet

- **Referanse:** FR-3, FR-13, UJ-3.
- **PRD:** FR-3: «Brukeren kan åpne en aktivitet fra årsvisningen og månedsvisningen». FR-13: «Alle aktiviteter kan finnes og åpnes via årsvisningen eller månedsvisningen, også når mange aktiviteter ligger i samme måned.»
- **Konsekvens:** Dette avgjør grunnutformingen av hjulet (OQ-4). Må hver aktivitet være klikkbar i hjulet, eller kan en full måned vise «+7 flere» som fører til månedsvisningen? Sistnevnte bryter FR-3 etter ordlyden.
- **Minimal retting:** Presiser i FR-3: «I årsvisningen kan aktiviteter i en full måned nås via månedsvisningen (FR-13).» Gruppen kan også velge motsatt regel.

---

## Low

### F11. C-1 kontrollerer repoet, men ikke opplasting

- **Brief:** «Ingen ekte dokumenter fra Forsvaret skal legges i repoet, lastes opp i applikasjonen eller sendes til eksterne språkmodeller.»
- **PRD C-1 Etterprøving:** «Alle testdokumenter i repoet er merket som fiktive. Ingen dokumenter i repoet stammer fra Forsvaret.»
- **Konsekvens:** Krav om opplasting og sending har ingen etterprøving. En testdeltaker med tjenestebakgrunn kan laste opp en ekte ordre, og teksten går til en ekstern tjeneste uten forvarsel.
- **Minimal retting:** Gruppen avgjør om det skal være en kort tekst ved opplasting, for eksempel i OQ-5. Hvis ikke, bør etterprøvingen omfatte instruksjonene til testdeltakerne.

### F12. PRD-tekst om briefen er utdatert

- **§4.5:** «*(Gruppegodkjent tillegg utover Product Brief.)*». Briefen har nå kildeutdrag i §3 steg 3 og IN 5.
- **§8.2 punkt 4:** «Sluttdato er obligatorisk for alle aktiviteter, ikke bare for flerdagsaktiviteter». Briefen sier nå «Hver aktivitet skal ha tittel, startdato, sluttdato». Det er ikke lenger en endring fra briefen.
- **OQ-1:** «Detaljene i §8.2 er dokumentert i PRD-en og gjentas ikke i briefen.» Dette stemmer ikke helt for kildeutdrag, og sier ingenting om endringene 2026-11-01.
- **Memlog:** Siste oppdatering er 2026-10-22. Den har ingen oppføring om briefens endringer 2026-11-01.
- **Minimal retting:** Endre §4.5 til «presisert utover Product Brief». Merk §8.2 punkt 1 og 4 som «senere også tatt inn i briefen på overordnet nivå». Legg en dato og en setning til OQ-1. Legg en memlog-oppføring til ved rettingen.

### F13. To OUT-punkter er ikke speilet presist i PRD §7

- **Brief:** «Operativ bruk med ekte dokumenter. Første versjon demonstrerer konseptet med fiktive data.» og «Prediksjon, konfliktanalyse, optimalisering og beslutningsstøtte.» (uavhengig av teknologi, jf. prompt 4 i KI-loggen).
- **PRD §7:** Har ikke punktet om operativ bruk, selv om C-1 dekker forbudet. Plasserer prediksjon og de øvrige under «*Avanserte KI-funksjoner:*», som kan leses som at bare KI-varianter er utelatt. «Beslutningstaking» er bare dekket indirekte gjennom menneskelig kontroll.
- **Konsekvens:** Svak for UX. En enkel regelbasert overlappvarsling er dekket av FR-26 («Automatisk konfliktanalyse»), men andre varianter er utydelige.
- **Minimal retting:** Legg til «Operativ bruk med ekte dokumenter (C-1)» i §7. Endre overskriften til «Avanserte analysefunksjoner, uavhengig av teknologi».

### F14. KI-status på det andre datofeltet blir stående etter retting

- **PRD FR-22:** «Når brukeren har endret eller fylt inn et felt, gjelder ikke lenger statusen KI satte for feltet.» FR-17: «Et forslag som bryter datoregelen, får sluttdatoen markert som *ugyldig*.» FR-23 blokkerer ved *ugyldig*.
- **Scenario:** Start 10.05, slutt 05.05. Kilden viser at startdatoen er feil, så Berg endrer bare den til 01.05. Sluttdatoen er ikke endret, så etter ordlyden står den fortsatt som *ugyldig*, og godkjenning er blokkert.
- **Minimal retting:** Legg til i FR-22: «Status *ugyldig* vurderes på nytt når et felt regelen avhenger av, endres.»

### F15. FR-17 kan leses som at tomme merknader er «manglende»

- **PRD:** «Hvert aktivitetsforslag har alle feltene. Felt uten verdi er markert som *manglende*.» og «Merknader foreslått av KI ... er valgfrie.»
- **Konsekvens:** Forslag uten merknad kan få en unødvendig markering (FR-21).
- **Minimal retting:** Skriv «Obligatoriske felt uten verdi».

### F16. Hva skjer med forslaget når lagring feiler ved godkjenning?

- **PRD:** FR-23: «En godkjent aktivitet lagres umiddelbart». NFR-1: «Mislykkes en lagring, får brukeren beskjed». Ingen av dem sier hva som skjer med forslaget.
- **Scenario:** Lagring feiler. Forslaget kan forsvinne, og da er brukerens redigeringer tapt.
- **Minimal retting:** Legg til i NFR-1: «Ved mislykket godkjenning forblir forslaget ubehandlet med brukerens endringer.»

### F17. Aktiviteter i uker som deles med nabomåneden

- **PRD FR-10:** «Månedsvisningen viser alle uker som berører måneden» og «Aktiviteter vises i ukene de berører.» UJ-3 E1 og FR-8 omtaler måneder den berører.
- **Scenario:** En aktivitet 30.12.2025 ligger i uke 1 (2026). Skal den vises i januar 2026, som også viser uke 1? Hvis den vises, viser FR-14 da tom tilstand for en januar uten egne aktiviteter?
- **Minimal retting:** Legg dette til i OQ-5, eller legg til i FR-10: «Månedsvisningen viser bare aktiviteter som berører måneden.»

### F18. Demo-modus kan ikke vise manglende verifisering

- **PRD FR-30:** «De forhåndsdefinerte aktivitetsforslagene for et støttet testdokument har kildeutdrag som finnes i testdokumentet.» FR-18: «demonstrere og teste hele kjerneflyten». UJ-1 E4 er i samme flyt.
- **Konsekvens:** Merkingen av ikke verifisert eller manglende kildeutdrag kan ikke demonstreres uten API-nøkkel. Memlog (linje 100) er i tråd med FR-30, så dette er et hull, ikke en konflikt. NFR-10 dekker regelen i automatiske tester.
- **Minimal retting:** Legg til i FR-30: «Testdataene kan i tillegg ha forslag uten kildeutdrag eller med bevisst ikke verifisert kildeutdrag.»

---

## Spørsmål 1: Hva er kontrollert mot briefen

| Briefpunkt | PRD | Resultat |
|---|---|---|
| §3 kjerneflyt, steg 1–5 | UJ-1, §4.3–§4.5, FR-8, FR-3, FR-10 | OK |
| IN 1 årshjul | FR-3, FR-8, FR-9, FR-10 | OK. «Sirkulær» er en presisering av årshjul (memlog linje 61) |
| IN 2 felt og manuell håndtering | FR-1, FR-2, FR-4, FR-5, C-6 | OK |
| IN 2 «Frister registreres som aktiviteter» | Mangler | **F1** |
| IN 3 formater | FR-15 | OK |
| IN 4 forslag og markering | FR-17, FR-21 | OK, men se F1 og F2 |
| IN 5 kontroll, godkjenning, lagring | FR-2, FR-7, FR-21–FR-25, FR-27–FR-29 | OK |
| OUT integrasjoner | §7 | OK |
| OUT flerbruker, roller, sanntid | §2.2, §7, C-6 | OK. Korte §7-linja er en bevisst beslutning (memlog linje 124) |
| OUT ringer, uke- og dagsvisning, tilpasning | §7, UJ-3 | OK |
| OUT OCR | FR-15, §7 | OK |
| OUT KI-prioritering, automatiske endringer | §7, FR-25 | OK. Ordlyd i F13 |
| OUT prediksjon m.m. | §7, FR-26 | OK i sak. Ordlyd i F13 |
| OUT Task Manager | §7 | OK |
| OUT operativ bruk | C-1 i sak, ikke i §7 | **F13** |
| §6 overordnet og Behavior | SM-1, UJ-1–UJ-3 | OK |
| §6 User outcome, ny testsetning | SM-1 bare indirekte | **F7** |
| §6 Quality | SM-3 | OK. Ingen prosentgrense er besluttet (memlog linje 130) |
| §6 Business, ny effektivitetsregel | SM-4 og counter-metric, delvis | **F7** |
| §8 fiktive data | C-1 | OK i sak. Etterprøving i F11 |
| §8 én språkmodell | C-2, OQ-6 | OK |
| §8 hemmeligheter | C-4 | OK |
| §8 demo-modus | FR-18, FR-30, C-5 | OK. Begrensning til testdokumenter er besluttet (memlog linje 74 og 77) |
| §8 test mot fasit | SM-3, NFR-10 | OK |
| §5 målgruppe, §9 visjon | §2.2, §7 | OK, ingen motstrid |

**Henvisninger fra PRD til brief som fortsatt stemmer:**
- §2.1 («§1–§3 og §5»)
- UJ-3 og FR-15 («fra Product Brief, OUT»)
- §7 («Product Brief §9»)
- P-1 og P-2 («Scope IN 3–4»)
- Kildene i SM-1, SM-3 og SM-4
- §8.2 punkt 2, 3 og 5, som fortsatt er reelle tillegg

**Utdatert tekst:** §4.5, §8.2 punkt 4 og OQ-1 (F12).

**Tillegg uten sporing:** Ingen funnet. Stikkprøver av FR-6, FR-12, FR-18, FR-26, C-1, C-3, C-5, NFR-7, NFR-9 og SM-1 kan alle spores til memlog.

**Merknad uten funn:** `AGENTS.md` kaller prosjektet «G99 — Sambandet», mens PRD-en har en arbeidstittel og OQ-2 åpent. Det er ingen motstrid, men gruppen bør ha det med når OQ-2 avgjøres.

## Spørsmål 2: Hver utsettelse vurdert

| Utsettelse | Type | OQ | Hjem | Eier | Merknad |
|---|---|---|---|---|---|
| Kategorilistens innhold | **Produkt** | OQ-3 | UX | Mangler | F5, F8 |
| Lesbarhet, FR-13, UJ-3 E4 | Design | OQ-4 | UX | Mangler | F5, F10 |
| Visuell form FR-8, FR-10, FR-12, FR-27, NFR-7 | Design | OQ-5 | UX | Mangler | F5 |
| Bekreftelse FR-26 | Design, men tidspunktet er **produkt** | OQ-5 | UX | Mangler | F4 |
| Tekst og utforming C-8 | Design | Ikke eget OQ | UX | Mangler | Godt nok. Dette er vanlig UX-arbeid |
| Tegngrense FR-6 | Teknisk | **Mangler** | Arkitektur | Mangler | F6 |
| Håndtering over grensen FR-6 | Design og **produkt** | **Mangler** | UX og arkitektur | Mangler | F6 |
| Språkmodell | Teknisk | OQ-6 | Arkitektur | Mangler | Briefen legger også dette dit |
| Demo-aktivering | Teknisk og delvis **produkt** | OQ-7 | Arkitektur | Mangler | F9 |
| Gjenkjenning av testdokumenter | Teknisk | OQ-7 | Arkitektur | Mangler | OK |
| Lagring, tidsgrense, dokumentstørrelse, nettlesere | Teknisk | OQ-8 | Arkitektur | Mangler | OK |
| Testdokumenter og krav i SM-2 | Prosess | OQ-9 | Ingen workflow | Mangler | F5 |
| Deltakere, kjøringer, Excel-oppsett, testmengder, ytelse | Prosess | OQ-10 | Ingen workflow | Mangler | F5 |
| Produktnavn | Produkt | OQ-2 | Gruppen | Gruppen | OK, blokkerer ikke |

**Produktbeslutninger som verken er avgjort eller utsatt:** frister (F1), delvise datoer (F2), ny opplasting (F3), tidspunkt for forkasting (F4).

## Spørsmål 3: Memlog mot PRD

Hele memloggen er lest (linje 6–168). **Ingen reelle konflikter.** Senere beslutninger er fulgt:

| Tidligere | Gjeldende | I PRD |
|---|---|---|
| A9, én dato gir *usikker* | A18 | FR-17, E6. A9 finnes ikke som regel |
| A4 og rubrikkfiks om kategori *ugyldig* | Linje 157 og 160 | FR-2, FR-17, Glossary |
| A11, ingen grense | Linje 144 | FR-6 |
| «Unfinished review not persisted» | A20, A21 | FR-26, E5, E8 |
| Detaljert briefoppdatering (linje 25, 39, 47, 135, 164) | Linje 165–168 | OQ-1, §8.2 |
| Bred visjonslinje | Linje 124 | §7 |

Andre beslutninger er kontrollert og finnes i PRD-en: A1–A3, A5, A6, A8, A10, A12–A17, A19, A21–A33, NFR-9 og prinsippet om menneskelig kontroll. Status for A1–A33 i §11.2 er komplett.

**Beslutning uten full dekning i PRD:**
- Linje 74, «no advanced mode control», står ikke i PRD-en (tatt med i F9).
- Linje 90, «no requirement for sorting, filtering», står heller ikke der. Det er ufarlig og gir ikke eget funn.

**ISO-eksemplene i FR-10** er regnet på nytt og stemmer: 29.12.2025 er mandag i uke 1 (2026), 29.01.2026 er i uke 5, 31.12.2026 og 02.01.2027 er i uke 53 (2026).

## Spørsmål 4: Testede samspill uten funn

- **Usikker og godkjenning:** Feltstatus, FR-22, FR-23, UJ-1 E1 og E1a er konsistente.
- **Kategori utenfor lista:** FR-2, FR-17 og E1a gir én entydig vei.
- **Kildeutdrag og godkjenning:** E4, FR-28 og FR-29 stemmer overens.
- **Kildeutdrag og lagring:** FR-16, FR-23, FR-29 og C-7 stemmer overens. Merknader med dokumentinnhold er bevisst akseptert i C-7.
- **Flerdagsaktivitet over årsskifte:** FR-8, FR-9, FR-10 og FR-11 stemmer overens, bortsett fra F17.
- **Navigasjon til gjennomgangen og tilbake:** FR-26 og E5 stemmer overens.
- **Redigering av godkjent aktivitet:** FR-4 og FR-23 stemmer overens, og skillet mot manuelle aktiviteter er bevisst fjernet.
- **Demo-modus med ustøttet dokument:** FR-18 er definert, bortsett fra F4 ved ubehandlede forslag.
- **Ubetrodd innhold:** NFR-9 stemmer med FR-2, FR-25 og FR-28.

## Avgrensning

Dette er en dokumentgjennomgang. Ingen brukere er spurt. Vurderingene av hva som er produkt- eller designbeslutninger er anmelderens, og de minimale rettingene er forslag som gruppen må godkjenne. `review-rubric.md` og `tilbakemelding-product-brief.md` er bare kontrollert for at de finnes, ikke lest.
