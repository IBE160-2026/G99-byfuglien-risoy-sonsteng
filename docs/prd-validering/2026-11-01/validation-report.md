# Validation Report — KI-assistert interaktivt årshjul

- **PRD:** `_bmad-output/planning-artifacts/prds/prd-G99-byfuglien-risoy-sonsteng-2026-10-19/prd.md`
- **Rubric:** `.claude/skills/bmad-prd/assets/prd-validation-checklist.md`
- **Run at:** 2026-11-01
- **Grade:** Fair

## Klar for UX Design?
Ikke klar for UX Design akkurat nå, men klar etter én kort oppdatering. Sju punkter merket «Før UX» må avgjøres av gruppen først. De krever små tekstendringer og ingen omskriving. Resten kan tas i UX, eller før stories.

## Overall verdict
PRD-en holder faglig: den har en tydelig tese (KI-uttrekk, kildekontroll og eksplisitt godkjenning), gjennomført begrepsbruk, sporbare ID-er og presise regler for feltstatus, datoer og ISO-uker. Risikoen ligger i done-ness: FR-17, FR-13 og MVP-porten i SM-1/SM-2 har ingen entydig bestått-grense, og flere feiltilstander i kjerneflyten er ikke avgjort.

Sammenligningen med nyeste Product Brief fant ingen motstrid i IN/OUT-scope og ingen konflikt mot memlog, men ett IN-punkt mangler som krav: «Frister registreres som aktiviteter». Fire produktbeslutninger er verken tatt eller utsatt til en navngitt workflow: frister, delvise datoer, ny opplasting og tidspunkt for forkasting.

Karakteren Fair følger av BMADs regel om at ethvert high-funn gir Fair. Karakteren Good fra 2026-10-22 er ikke lenger dekkende, fordi briefen er endret og denne runden også testet samspillet mellom kravene.

## Dimension verdicts
- Decision-readiness — adequate
- Substance over theater — strong
- Strategic coherence — adequate
- Done-ness clarity — thin
- Scope honesty — adequate
- Downstream usability — adequate
- Shape fit — strong

## Findings by severity

### Critical (0)

### High (4)

**[Samsvar med brief]** H1. Briefens regel om frister mangler i PRD-en (Brief §7 IN 2; PRD §3, FR-17, UJ-1 E6, OQ-3)
Briefen sier «Frister registreres som aktiviteter», men i PRD-en står «frist» bare i §1, §2.1 og UJ-1. «Innen 15. mars» kan etter FR-17 gi sluttdato manglende, og det står ikke om datoen er start eller slutt. Fasit for SM-3 og demo-modus blir dermed ikke entydig. Forrige kontroll aksepterte manuell utfylling, og KI-loggen skiller lagrede frister (like datoer) fra KI-tolkning. Det er derfor ingen motstrid, men en beslutning som ikke står i PRD-en.
Fix: Legg inn «Frist» i Glossary: aktivitet med startdato lik sluttdato. Velg regel i FR-17 og UJ-1 E6: enten foreslås fristdatoen som begge datoer, eller sluttdato markeres manglende som i dag. Legg spørsmålet om egen fristkategori i OQ-3.
Når: Før UX

**[Done-ness clarity]** H2. FR-17 merker sannsynlig KI-oppførsel som testbar uten toleranse (FR-17, UJ-1 E6, SM-2, SM-3, §3 Feltstatus)
SM-2 krever at «ingen av disse testene feiler», mens SM-3 sier «det settes ingen prosentgrense». Én avvikende modellkjøring gjør FR-17 uoppfylt, eller testen må ignoreres. «Usikker» er heller ikke operasjonelt definert.
Fix: Del FR-17 i (a) applikasjonskontrakt: gitt modellsvar X settes status Y, testet med kontrollerte svar, og (b) modellkvalitet, målt i SM-3. Definer usikker som at språkmodellen har oppgitt verdien som usikker i svaret.
Når: Før stories

**[Done-ness clarity]** H3. MVP-porten kan defineres etter behov (SM-1, SM-2, OQ-9, OQ-10)
SM-2 gjelder «sentrale» krav som «testplanen angir», og SM-1 «de sentrale arbeidsflytene». Gruppen kan dermed oppfylle kriteriet ved å snevre inn omfanget. Det står heller ikke hva som skjer hvis en deltaker ikke fullfører.
Fix: SM-2 omfatter alle FR-er unntatt modellkvalitet (H2) og alle etterprøvinger i §5–§6. SM-1 omfatter UJ-1 til UJ-3 og et fastsatt minste antall deltakere.
Når: Før stories

**[Done-ness clarity]** H4. FR-13 har ingen grense og er i konflikt med FR-3 (FR-13, FR-3, UJ-3 E4, OQ-4, OQ-10)
«Lesbar» og «mange» er ubestemt. Konsekvensen «via årsvisningen eller månedsvisningen» er oppfylt selv om hjulet er uleselig. FR-3 krever åpning «fra årsvisningen og månedsvisningen». Dette avgjør grunnutformingen: må alle aktiviteter være klikkbare i hjulet, eller kan en full måned vise «+7 flere»?
Fix: Avgjør regelen før UX, for eksempel: «I årsvisningen kan aktiviteter i en full måned nås via månedsvisningen». Sett et akseptansescenario med konkret antall aktiviteter og skjermstørrelse. UX velger løsningen.
Når: Før UX

### Medium (23)

**[Decision-readiness]** M1. Delvise datoer og datoer uten år er udefinert (FR-17, UJ-1 E6, FR-9, FR-23)
«Uke 12», «i løpet av april» og «15. mars» uten år har ingen regel. Feil år kan legge en godkjent aktivitet utenfor kalenderåret som vises, uten tilbakemelding. Umulige datoer er heller ikke nevnt.
Fix: Legg én konsekvens i FR-17: upresise datoer gir manglende, eller forslag med usikker (gruppen velger), og en ikke-gyldig kalenderdato er ugyldig. Legg i FR-23: brukeren får beskjed når aktiviteten ligger utenfor valgt kalenderår.
Når: Før UX

**[Decision-readiness]** M2. Ny opplasting er ikke en fortsettelse og kan gi duplikater (FR-26, UJ-1 E5, C-3)
«Laste opp dokumentet på nytt for å fortsette» lover noe produktet ikke gjør. Ny analyse kan gi andre forslag og returnerer også godkjente og avviste. Duplikatkontroll er bevisst utenfor v1, men følgen er ikke beskrevet.
Fix: Erstatt «for å fortsette» med at ny opplasting gir ny analyse, at alle forslag kan komme tilbake, og at brukeren selv må unngå duplikater. Legg støtte for dette i OQ-5.
Når: Før UX

**[Decision-readiness]** M3. Tidspunktet for å forkaste gamle forslag er uavklart (FR-15, FR-26, UJ-1 E8, FR-18–FR-20)
Brukeren bekrefter «før analysen starter», men det står ikke hva som skjer med redigerte forslag hvis dokumentet avvises eller analysen feiler.
Fix: Anbefalt i FR-26: «Forslagene forkastes først når den nye analysen har gitt aktivitetsforslag. Feiler den, beholdes de.»
Når: Før UX

**[Decision-readiness]** M4. Kategorilisten er en domenebeslutning uten eier (§3 Kategoriliste, OQ-3, FR-2, FR-17, SM-3)
Innholdet «fastsettes i UX-workflowen», men styrer validering, KI-kontekst og fasit, og domenekunnskapen ligger hos gruppen. Kategori er obligatorisk, og «ingen kategori passer» er ikke besvart. En restkategori «Annet» vil dessuten tømme manglende-regelen for innhold.
Fix: Utvid OQ-3: gruppen avgjør listen, og den må dekke alle aktiviteter, avgjøre om det finnes restkategori og om frister har egen kategori. UX fastsetter visuell identitet. Legg til FR-2, FR-22 og SM-3 i kravkolonnen.
Når: Før UX

**[Decision-readiness]** M5. Demo-aktivering og manglende API-nøkkel er uavklart (OQ-7, OQ-5, FR-18, FR-20, C-5)
OQ-7 sender aktiveringen til arkitektur, men UX kommer først og må vite om det finnes en bryter. Hva en sensor uten nøkkel ser ved oppstart, er ikke beskrevet.
Fix: Legg til i FR-18: uten API-nøkkel får brukeren tydelig melding og veiledning til demo-modus. Ingen avansert modusstyring i v1 (memlog). Pek fra OQ-5 til OQ-7.
Når: Før UX

**[Done-ness clarity]** M6. Aktiviteter i uker som deles med nabomåneden (FR-8, FR-10, FR-11, FR-14)
En aktivitet 29.–30. september ligger i uke 40, som også berører oktober. Det er uklart om den skal vises i oktober, og det avgjør også om FR-14 viser tom tilstand.
Fix: Legg til i FR-10: «Månedsvisningen viser bare aktiviteter som berører måneden», eller motsatt regel, med testeksempel.
Når: I UX

**[Done-ness clarity]** M7. «Tydelig» er akseptkriterium uten definisjon (30 forekomster, bl.a. FR-14, FR-15, FR-18, FR-21, FR-27, FR-28)
«Tydelig markert» kan ikke testes, og NFR-4 dekker bare innholdet i meldinger.
Fix: Definer «tydelig markert» i Glossary: synlig uten ekstra handling, med tekstetikett, ikke basert på farge alene.
Når: I UX

**[Done-ness clarity]** M8. «Verifisert» kan leses som mer enn det betyr (FR-28, §3 Kildeutdrag, NFR-9, UJ-1)
Et tomt eller svært kort utdrag («mars») blir verifisert. Injisert tekst finnes også i dokumentet og blir verifisert, så NFR-9 overdriver effekten. Status betyr at teksten finnes, ikke at forslaget er riktig.
Fix: Legg til i FR-28: tomt utdrag regnes som manglende, og merkingen skal vise at status gjelder tekstens forekomst. Juster NFR-9.
Når: I UX

**[Done-ness clarity]** M9. Demo-modus kan ikke vise negative tilfeller (FR-18, FR-30, UJ-1 E4, §3 Fasit)
FR-30 krever kildeutdrag som «finnes i testdokumentet», så alle blir verifisert. Merkingen fra E4 kan ikke demonstreres uten nøkkel, og FR-18 krever ikke dekning av alle feltstatuser.
Fix: Krev i FR-30 at settet samlet dekker hver feltstatus, ett ikke verifisert og ett manglende kildeutdrag. Utvid Fasit med forventet verifiseringsstatus.
Når: Før stories

**[Downstream usability]** M10. OQ-3 til OQ-10 mangler eier, og testplanen har ingen plass i kjeden (§0, §10.3–§10.5, SM-2)
Testplanen bærer SM-2-omfang, deltakere, ytelseskriterier og fasit, men har ingen eier, workflow eller tidspunkt, og §0 nevner den ikke. Fasit trengs før demo-modus kan bygges.
Fix: Sett eier på §10.3–§10.5. Si i §0 og §10.5 hvor og når testplanen lages, senest før epics og stories.
Når: Før stories

**[Done-ness clarity]** M11. Merknadsgrensen har ingen OQ, og godkjenning over grensen er uavklart (FR-6, OQ-5, OQ-8, FR-2, FR-23)
Grensen «fastsettes i arkitekturen», men står ikke i OQ-8. Håndteringen har to eiere og står ikke i OQ-5. Det er uklart om en KI-merknad over grensen blokkerer godkjenning.
Fix: Legg grensen i OQ-8 og håndteringen i OQ-5. Avgjør i FR-6 om merknad over grensen blokkerer godkjenning.
Når: Før stories

**[Samsvar med brief]** M12. Briefens to nye suksesskriterier mangler i Success Metrics (Brief §6; SM-1, SM-4, §9.3)
Oppgaven «finne ut når en aktivitet skjer og hvem som har ansvaret» og regelen «kortere tid uten flere feil» er ikke ført inn. Counter-metric dekker bare halve regelen.
Fix: Legg oppgaven til i SM-1 og effektivitetsregelen til i SM-4. Behold merknaden om at resultatene er veiledende.
Når: Før stories

**[Strategic coherence]** M13. §2.2 kan leses som testing med troppssjefer, men SM-1 krever det ikke (§2.2, SM-1, P-1)
§2.2 sier «utvikles og testes med troppssjefer som primærmålgruppe». Memlog viser at SM-1 bevisst bare krever én utenforstående deltaker, så SM-1 er en tatt beslutning. Rubric-gjennomgangen satte funnet til high. Jeg har nedgradert det, fordi problemet er ordlyd og en uvalidert forutsetning (P-1), og fordi SM-4 ikke tester P-1.
Fix: Presiser §2.2 («utvikles for»), og skriv i P-1 at forutsetningen forblir uvalidert i v1. Alternativt: ta inn en deltaker med planleggingserfaring i SM-1.
Når: Før stories

**[Strategic coherence]** M14. Counter-metric og differensiator måles ikke (§9 Counter-metrics, SM-3, SM-4)
«Må brukeren rette mange felt (SM-3)», men SM-3 teller ikke rettede felt og dekker bare datoer. Andel verifiserte kildeutdrag måles ikke. SM-4 mangler tolkningsregel for andre utfall.
Fix: Legg til i SM-3: rettede felt per forslag, treff på kategori og ansvarsområde, og andel verifiserte kildeutdrag.
Når: Før stories

**[Samsvar med brief]** M15. Briefens OUT om operativ bruk står ikke i §7 (Brief §7 OUT; PRD §1, §7, UJ-1, C-1)
Briefen sier at v1 demonstrerer konseptet med fiktive data. §1 og UJ-1 beskriver reell bruk, og C-1 forbyr bare ekte dokumenter. §7-overskriften «Avanserte KI-funksjoner» kan også leses som at ikke-KI-varianter er tillatt, mens briefen utelater dem uansett teknologi.
Fix: Legg «Operativ bruk med ekte dokumenter (C-1)» til i §7. Skriv overskriften om til «Avanserte analysefunksjoner, uavhengig av teknologi».
Når: Før stories

**[Decision-readiness]** M16. Prisen for å ikke lagre KI-opprinnelse og kildeutdrag er ikke navngitt (§2.1, UJ-1 Avslutning, FR-23)
§2.1 lover «kan stole på planen», men etter godkjenning kan ingen se grunnlaget. Valget kan være riktig, men det som gis opp, er ikke sagt.
Fix: Legg til to setninger i §4.4 eller §7: hva som gis opp, hvorfor det aksepteres, og at merknader er eneste kanal for kildeinformasjon.
Når: Før stories

**[Done-ness clarity]** M17. «Ugyldig svar» er ikke avgrenset mot delvis feil (FR-20, FR-17)
FR-17 håndterer feil per felt, mens FR-20 forkaster alt ved «ugyldig svar». Det står ikke hva som skjer når bare noen forslag er brukbare.
Fix: Definer i FR-20 ugyldig svar som et svar som ikke kan tolkes etter avtalt format, og avgjør om tolkbare forslag beholdes.
Når: Før stories

**[Done-ness clarity]** M18. Lagringsfeil ved godkjenning er ikke beskrevet (FR-23, NFR-1)
Brukeren får beskjed, men det står ikke hva som skjer med forslaget. Redigeringer kan gå tapt.
Fix: Legg til i FR-23: «Mislykkes lagringen, forblir forslaget ubehandlet med brukerens endringer.»
Når: Før stories

**[Done-ness clarity]** M19. NFR-6 er subjektiv og uten datamengde (NFR-6, OQ-10)
«Skal oppleves som raskt» og «foreløpig under 1 sekund» har verken målepunkt, planstørrelse eller etterprøving.
Fix: Formuler: under 1 sekund fra handling til oppdatert visning ved et fastsatt antall aktiviteter, med dokumentert måling.
Når: Før stories

**[Done-ness clarity]** M20. Krav uten etterprøving faller utenfor SM-2 (§5, §6, SM-2)
C-2, C-3, C-6, C-7, C-8, NFR-3, NFR-5, NFR-6, NFR-8 og NFR-10 har ingen etterprøving. Viktigst er C-3, C-7 og NFR-3, som er enkle å teste.
Fix: Legg til etterprøving for minst C-3, C-7, NFR-3 og NFR-5.
Når: Før stories

**[Done-ness clarity]** M21. NFR-7 dekker ikke det meste av bruken (NFR-7, §3 Kjerneflyt, OQ-5)
Kjerneflyt omfatter ikke manuell håndtering, månedsnavigasjon og åpning av aktivitet, så tastaturkravet gjelder ikke klart for disse.
Fix: La NFR-7 gjelde UJ-1 til UJ-3, og skriv at aktiviteter kan nås og åpnes med tastatur, minst via månedsvisningen.
Når: I UX

**[Scope honesty]** M22. Forventede funksjoner er verken krav eller Non-Goals (§2.1, UJ-3 Klimaks, §7)
Søk og filtrering, klokkeslett, gjentakende aktiviteter, eksport, sikkerhetskopi og Excel-import er ikke nevnt. Memlog utelukker bare krav om sortering og filtrering i gjennomgangen, og Excel er utgangspunktet i §1.
Fix: Legg dem under «Utenfor v1» i §7, eller ta inn søk som FR hvis UJ-3 trenger det.
Når: Før stories

**[Strategic coherence]** M23. Ingen kuttrekkefølge for 30 FR-er (§8.1)
§8.1 sier hva som er med, men ikke hva som kuttes først. Fast prosjektfrist gjør at kutt ellers skjer ad hoc i stories.
Fix: Marker i §8.1 hva som må stå igjen for å vise tesen, og hvilke krav som kuttes først.
Når: Før stories

### Low (7)

**[Samsvar med brief]** L1. PRD-tekst om briefen er utdatert (§4.5, §8.2 pkt. 1 og 4, OQ-1, .memlog.md)
§4.5 kaller kildeutdrag et «tillegg utover Product Brief», og §8.2 pkt. 4 omtaler sluttdato som en endring, men briefen har nå begge. Memlog har ingen oppføring om briefens endringer 2026-11-01.
Fix: Endre §4.5 til «presisert utover Product Brief», merk §8.2 pkt. 1 og 4 som senere tatt inn i briefen, og dater OQ-1. Legg til memlog-oppføring.
Når: Samme oppdatering

**[Samsvar med brief]** L2. C-1 etterprøver repoet, men ikke opplasting (Brief §8, C-1)
Forbudet mot å laste opp ekte dokumenter har ingen etterprøving. En testdeltaker kan laste opp en ekte ordre.
Fix: Legg kort tekst ved opplasting i OQ-5, eller ta det inn i instruksjonene til testdeltakere.
Når: Kan vente

**[Done-ness clarity]** L3. Status ugyldig kan bli stående etter retting av det andre datofeltet (FR-22, FR-17, FR-23)
Start 10.05, slutt 05.05: Berg retter startdatoen, men sluttdatoen er ikke endret og står etter ordlyden fortsatt som ugyldig. Godkjenning blokkeres.
Fix: Legg til i FR-22: status ugyldig vurderes på nytt når et felt regelen avhenger av, endres.
Når: Før stories

**[Done-ness clarity]** L4. Tomme merknader kan leses som manglende (FR-17)
«Felt uten verdi er markert som manglende» omfatter etter ordlyden også de valgfrie merknadene.
Fix: Skriv «Obligatoriske felt uten verdi».
Når: Før stories

**[Scope honesty]** L5. Avvisning er ubeskyttet, sletting er det ikke (FR-24, FR-5)
Et feilklikk på avvis kan bare rettes med ny analyse, og asymmetrien er ikke omtalt.
Fix: Skriv at avvisning skjer uten bekreftelse som et bevisst valg, eller legg til bekreftelse.
Når: Kan vente

**[Downstream usability]** L6. Status og navn er ikke ryddet (Frontmatter, tittel, §10.1, OQ-2)
`status: final` står sammen med «Arbeidstittel – bekreftes», og OQ-1 er avklart, men står fortsatt i Open Questions. README og AGENTS.md bruker navnet «Sambandet», som PRD-en ikke nevner.
Fix: Flytt OQ-1 ut av Open Questions, og ta med «Sambandet» når OQ-2 avgjøres.
Når: Kan vente

**[Shape fit]** L7. Capabilities-listene dupliserer FR-ene (§2.3)
Teksten stemmer i dag, men gir to kilder å holde i takt ved endring.
Fix: Bytt til FR-ID-er per UJ, eller skriv at §4 har forrang ved avvik.
Når: Kan vente

## Mechanical notes
- ID-er: FR-1–30, C-1–8, NFR-1–10, SM-1–4, OQ-1–10 og P-1–5 er sammenhengende og unike. Ingen `[ASSUMPTION]` står åpne.
- ISO-eksemplene i FR-10 er regnet på nytt og stemmer.
- Glossary-drift: «forslag» brukes for aktivitetsforslag, «applikasjonen» og «systemet» veksler, og «KI», «periode» og «ubehandlet» er ikke definert. Årshjul brukes i både vid og snever betydning.
- Out of Scope på feil sted: konfliktanalyse under FR-26 og full dokumentvisning under FR-30.
- NFR-4-etterprøvingen utelater meldingene fra NFR-1, NFR-2 og NFR-3.
- §11.2 viser til A-numre som bare kan slås opp i .memlog.md. §0 oppgir filer uten sti.

## Reviewer files
- `review-rubric.md`
- `review-brief-og-beslutninger.md`
