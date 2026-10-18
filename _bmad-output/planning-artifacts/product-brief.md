# Product Brief – KI-assistert interaktivt årshjul

## 1. Executive Summary

Vi utvikler en interaktiv planleggingsløsning med KI-støtte for troppssjefer i Forsvaret. Målet er å samle aktiviteter og frister i ett oversiktlig årshjul, slik at mer tid kan brukes på ledelse, planlegging og oppdragsløsning.

I dag er informasjon spredt mellom Excel-ark, ordre og andre dokumenter, noe som krever mye manuelt arbeid og gjør planleggingen mindre effektiv. Ved å kombinere visuell planlegging med KI-assistert dokumentbehandling skal løsningen redusere dette arbeidet og gi bedre oversikt, samtidig som brukeren beholder kontrollen over hva som legges inn i planen. Utviklingen innen KI gjør det nå mulig å automatisere deler av dette manuelle arbeidet.

### The Problem

Troppssjefer i Forsvaret bruker mye arbeidstid på å holde oversikt over informasjon som allerede finnes, fremfor på ledelse og planlegging. Informasjonen er spredt i frittstående Excel-ark og dokumenter, ofte lokalt lagret eller skrivebeskyttet og uten felles struktur, slik at planlegging krever manuell navigering mellom filer og gjeninntasting av data. I møter går tid tapt til lasting og leting etter dokumenter, samtidig som et samlet og oppdatert planbilde mangler. Resultatet er at arbeidskraft og planleggingshorisont bindes opp i dokumenthåndtering fremfor ledelse og oppdragsløsning.

## 2. The Solution

Løsningen er et interaktivt årshjul. Kjerneflyten består av fem steg:

1. **Last opp dokument:** Brukeren laster opp en ordre eller et annet dokument (.docx eller tekstbasert PDF).
2. **Få aktivitetsforslag:** KI analyserer dokumentet og foreslår aktiviteter med tittel, dato, varighet, kategori og ansvarsområde. Informasjon som mangler eller er usikker, markeres i forslaget.
3. **Kontroller forslagene:** Brukeren går gjennom forslagene, kompletterer eller endrer dem ved behov, og godkjenner eller avviser hvert forslag.
4. **Legg inn i planen:** Godkjente aktiviteter lagres og legges inn i årshjulet.
5. **Få oversikt:** Brukeren ser planen i årsvisning, zoomer inn til månedsvisning med ukeinndeling og åpner enkeltaktiviteter for utfyllende informasjon.

Alle visningene bygger på de samme aktivitetene. Brukeren kan også opprette, redigere og slette aktiviteter manuelt.

**Eksempel (fiktivt):** Troppssjefen mottar en øvingsordre for «Øvelse Testfjell». Ordren beskriver en skytedag 12. mars, en feltøvelse 24.–26. mars og en frist 1. mars for innmelding av materiellbehov. Etter opplasting foreslår KI aktiviteter basert på ordren. For feltøvelsen står ansvarsområde ikke i ordren, så det markeres som manglende. Troppssjefen fyller inn ansvarsområdet, godkjenner forslagene og ser aktivitetene i mars i årshjulet.

## 3. What Makes This Different

Relevante alternativer er Excel, eksisterende årshjul og planleggingsverktøy som Microsoft Planner, Trello og Teams-kalender. Disse dekker ulike planleggingsbehov, men krever ofte at informasjon fra ordre og dokumenter overføres manuelt til planen.

Løsningens særpreg er kombinasjonen av et interaktivt årshjul, KI-assistert aktivitetsgenerering og brukergodkjenning i én sammenhengende arbeidsflyt, tilpasset troppssjefens planleggingsbehov.

## 4. Who This Serves

Primærbrukeren i første versjon er troppssjefen i Forsvaret, som skal planlegge og følge opp øvelser, utdanning og frister basert på informasjon fra flere kilder. I en typisk uke mottar troppssjefen ordre fra overordnet ledd og omsetter dem til ukeplaner for troppen. Brukeren har behov for et samlet og oppdatert planbilde som også kan benyttes i planleggingsmøter. Andre lederroller er aktuelle målgrupper på sikt.

## 5. Success Criteria

Løsningen lykkes dersom troppssjefen kan gå fra et opplastet dokument til en oppdatert plan i én samlet løsning, med mindre behov for manuelt planleggingsarbeid.

**User outcome:** Brukeren får bedre oversikt over aktiviteter og frister gjennom et samlet årshjul, samtidig som KI-assistert dokumentbehandling reduserer behovet for manuell registrering.

**Behavior:** Brukeren skal kunne opprette, redigere og slette aktiviteter, navigere mellom års- og månedsvisning og kontrollere, endre, godkjenne eller avvise KI-genererte aktivitetsforslag. I brukertest skal hele arbeidsflyten fra dokumentopplasting til oppdatert plan kunne gjennomføres uten veiledning.

**Quality:** KI-genererte aktivitetsforslag skal testes mot 3–4 fiktive dokumenter med kjent fasit for å kontrollere om relevante aktiviteter og datoer identifiseres korrekt.

**Business / mission:** Samme planleggingsoppgave skal gjennomføres både manuelt i Excel og ved bruk av applikasjonen. Tidsbruken sammenlignes for å undersøke om løsningen effektiviserer planleggingsarbeidet.

## 6. Scope

### IN – First version

1. Interaktivt årshjul: Løsningen skal visualisere aktiviteter i et interaktivt årshjul med hele kalenderåret og dets 12 måneder som hovedvisning (årsvisning). Brukeren skal kunne zoome inn på en enkelt måned for å se aktivitetene fordelt på uker (månedsvisning med ukeinndeling), og åpne enkeltaktiviteter for mer detaljert informasjon. Brukeren skal kunne velge hvilket kalenderår som vises.
2. Aktivitetshåndtering: Løsningen skal være en enkeltbrukerløsning der brukeren manuelt kan opprette, redigere og slette aktiviteter. Hver aktivitet skal minimum inneholde tittel, dato, varighet, kategori og tilknyttet ansvarsområde.
3. Dokumentopplasting: Brukeren skal kunne laste opp Word-dokumenter (.docx) og tekstbaserte PDF-dokumenter som grunnlag for KI-assistert aktivitetsgenerering.
4. KI-assistert aktivitetsgenerering: KI skal analysere innholdet i opplastede dokumenter og foreslå relevante aktiviteter med tittel, dato, varighet, kategori og ansvarsområde når informasjonen kan utledes av dokumentet. Dersom nødvendig informasjon mangler eller er usikker, skal dette tydelig fremgå av forslaget, slik at brukeren kan komplettere informasjonen før godkjenning.
5. Brukerkontroll og lagring: KI-genererte aktivitetsforslag skal presenteres for brukeren, som kan redigere, godkjenne eller avvise hvert forslag før det legges inn i årshjulet. Ingen KI-genererte aktiviteter skal legges inn i planen uten eksplisitt godkjenning fra brukeren. Godkjente og manuelt opprettede aktiviteter skal lagres og være tilgjengelige ved senere bruk.

### OUT – First version

- Direkte integrasjon med eksterne applikasjoner, inkludert automatisk innhenting og synkronisering av informasjon.
- Flerbrukerfunksjonalitet, inkludert deling av årshjul, rolle- og tilgangsstyring, og sanntidssamarbeid.
- Mulighet for flere konsentriske ringer i årshjulet.
- Muligheten til å zoome inn på en enkelt uke og se aktivitetene fordelt på ukedager (mandag–søndag).
- OCR og analyse av skannede dokumenter eller bilder.
- Omfattende tilpasning av format, layout, farger og planleggingsstrukturer.
- KI-basert prioritering, beslutningstaking og automatisk gjennomføring av endringer uten brukerens godkjenning.
- Prediksjon, konfliktanalyse, optimalisering og beslutningsstøtte.
- Separat oppgavestyring (Task Manager), inkludert oppgavestatus, fremdriftsoppfølging og fullføring av oppgaver.

## 7. Security & Testing

- Kun fiktive dokumenter og testdata skal benyttes under utvikling, testing og demonstrasjon. Ingen ekte dokumenter fra Forsvaret skal legges i repoet, lastes opp i applikasjonen eller sendes til eksterne språkmodeller.
- Løsningen skal benytte én ekstern språkmodell via API for å analysere dokumenter og foreslå aktiviteter. Valg av modell og leverandør skal dokumenteres og begrunnes i arkitekturen.
- API-nøkler og andre hemmeligheter skal lagres i miljøvariabler og holdes utenfor Git.
- Applikasjonen skal kunne kjøres og demonstreres uten betalt KI-tilgang gjennom en mock/demo-modus med forhåndsdefinerte KI-svar. Demo-modusen skal støtte den samme brukerflyten for gjennomgang, redigering, godkjenning og avvisning av aktivitetsforslag som ved bruk av en ekstern språkmodell.
- Kjernefunksjonaliteten skal testes med fiktive dokumenter der forventede aktiviteter er definert på forhånd, slik at resultatene fra KI-uttrekket kan sammenlignes med en kjent fasit.

## 8. Vision

Vår visjon er en arbeidshverdag der ledere bruker mindre tid på administrasjon og informasjonsleting og mer tid på ledelse, prioritering og oppdragsløsning. Planlegging skal være oversiktlig, effektiv og basert på et felles og oppdatert planbilde, der brukeren kan bevege seg sømløst mellom års-, måneds-, uke- og dagsvisning etter behov. På sikt skal løsningen bidra til bedre informasjonsflyt, raskere beslutninger og mer effektiv bruk av tid og personell.
