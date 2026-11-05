# Product Brief – AI-Assisted Interactive Annual Planning Wheel

## 1. Executive Summary

Vi utvikler en interaktiv planleggingsløsning med KI-støtte for troppssjefer i Forsvaret. Den samler aktiviteter og frister i ett oversiktlig årshjul, slik at mer tid kan brukes på ledelse, planlegging og oppdragsløsning.

Utviklingen innen KI gjør det nå mulig å automatisere deler av det manuelle arbeidet med informasjon spredt mellom Excel-ark, ordre og andre dokumenter. Brukeren beholder kontrollen over hva som legges inn i planen.

## 2. The Problem

Troppssjefer bruker mye arbeidstid på å holde oversikt over informasjon som allerede finnes. De mangler en effektiv måte å omsette informasjon fra ordre og dokumenter til en samlet og oppdatert aktivitetsplan. Informasjonen ligger i frittstående Excel-ark og dokumenter, ofte lokalt lagret og uten felles struktur. Planlegging krever derfor manuell navigering mellom filer og gjeninntasting av data. I møter går tid tapt til lasting og leting etter dokumenter. Arbeidstid og planleggingskapasitet bindes dermed opp i dokumenthåndtering fremfor ledelse og oppdragsløsning. Problemforståelsen bygger på gruppemedlemmenes samlede erfaringer og observasjoner fra over ett års tjeneste som troppssjefer i Forsvaret.

## 3. The Solution

Løsningen er et interaktivt årshjul med en kjerneflyt i fem steg:

1. **Last opp dokument:** Brukeren laster opp en ordre eller et annet dokument (.docx eller tekstbasert PDF).
2. **Få aktivitetsforslag:** KI analyserer dokumentet, genererer aktivitetsforslag og markerer manglende eller usikker informasjon.
3. **Kontroller forslagene:** Brukeren kontrollerer hvert forslag mot tilgjengelige kildeutdrag, kompletterer eller endrer det ved behov, og godkjenner eller avviser det.
4. **Legg inn i planen:** Bare godkjente forslag lagres som aktiviteter og legges inn i årshjulet.
5. **Få oversikt:** Brukeren ser planen i årsvisning, zoomer inn til månedsvisning med ukeinndeling og åpner enkeltaktiviteter.

Alle visningene bygger på de samme aktivitetene, som også kan opprettes, redigeres og slettes manuelt.

## 4. What Makes This Different

Relevante alternativer er Excel, digitale årshjul som Plandisc og planleggingsverktøy som Microsoft Planner, Trello og Teams-kalender. Plandisc markedsfører KI-import fra dokumenter, mens Microsoft Planner Agent ifølge Microsoft kan generere planutkast fra Word-filer som brukeren bekrefter.

Løsningens særpreg ligger i en samlet arbeidsflyt fra ordre til årshjul, der KI-genererte aktivitetsforslag kontrolleres mot kildeutdrag som applikasjonen verifiserer, og godkjennes enkeltvis før de legges inn i planen. Løsningen er tilpasset troppssjefens planleggingsbehov.

## 5. Who This Serves

Primærbrukeren i første versjon er troppssjefen, som planlegger og følger opp øvelser, utdanning og frister. I en typisk uke mottar troppssjefen ordre fra overordnet ledd og bruker informasjonen til å planlegge og koordinere troppens aktiviteter. Brukeren trenger et samlet og oppdatert planbilde som også kan benyttes i planleggingsmøter. Andre lederroller er aktuelle målgrupper på sikt.

## 6. Success Criteria

Løsningen lykkes dersom troppssjefen kan gå fra et opplastet dokument til en oppdatert plan i én samlet løsning, med mindre manuelt planleggingsarbeid.

**User outcome:** Bedre oversikt over aktiviteter og frister, og mindre manuell registrering. I brukertest kan brukeren finne ut når en aktivitet skjer og hvem som har ansvaret, uten å åpne andre filer.

**Behavior:** Brukeren skal kunne opprette, redigere og slette aktiviteter, navigere mellom års- og månedsvisning og kontrollere, endre, godkjenne eller avvise KI-genererte aktivitetsforslag. I brukertest skal hele arbeidsflyten fra dokumentopplasting til oppdatert plan kunne gjennomføres uten veiledning.

**Quality:** KI-genererte aktivitetsforslag skal testes mot 3–4 fiktive dokumenter med forhåndsdefinert fasit: om relevante aktiviteter og datoer identifiseres korrekt, og om manglende eller usikker informasjon markeres tydelig.

**Business / mission:** Samme planleggingsoppgave skal gjennomføres manuelt i Excel og i applikasjonen. Tidsbruken måles og sammenlignes. Løsningen regnes som mer effektiv dersom oppgaven tar kortere tid uten flere feil sammenlignet med en forhåndsdefinert fasit.

## 7. Scope

### IN – First version

1. **Interaktivt årshjul:** Årsvisning med 12 måneder og valg av kalenderår, zoom til månedsvisning med ukeinndeling og åpning av enkeltaktiviteter for detaljer.
2. **Aktivitetshåndtering:** Enkeltbrukerløsning for å opprette, redigere og slette aktiviteter. Hver aktivitet skal ha tittel, startdato, sluttdato, kategori og ansvarsområde. Frister registreres som aktiviteter.
3. **Dokumentopplasting:** Støtte for Word-dokumenter (.docx) og tekstbasert PDF.
4. **KI-assistert aktivitetsgenerering:** KI skal foreslå relevante aktiviteter med tittel, startdato, sluttdato, kategori og ansvarsområde, basert på tilgjengelig informasjon i dokumentet. Manglende eller usikker informasjon skal markeres tydelig.
5. **Brukerkontroll og lagring:** Brukeren skal kunne kontrollere forslagene mot tilgjengelige kildeutdrag fra dokumentet. Hvert forslag skal kunne redigeres, kompletteres, godkjennes eller avvises. Obligatoriske opplysninger må være utfylt før godkjenning, og ingen KI-genererte aktiviteter skal legges inn uten brukerens eksplisitte godkjenning. Alle aktiviteter skal lagres og være tilgjengelige når applikasjonen åpnes på nytt.

### OUT – First version

- Direkte integrasjon med eksterne applikasjoner, inkludert automatisk innhenting og synkronisering.
- Flerbrukerfunksjonalitet, inkludert deling av årshjul, rolle- og tilgangsstyring og sanntidssamarbeid.
- Flere konsentriske ringer, egne uke- og dagsvisninger (inkludert aktiviteter fordelt på mandag–søndag) og omfattende tilpasning av format, layout, farger og planleggingsstrukturer.
- OCR og analyse av skannede dokumenter eller bilder.
- KI-basert prioritering og beslutningstaking, samt automatiske endringer uten brukerens godkjenning.
- Prediksjon, konfliktanalyse, optimalisering og beslutningsstøtte.
- Separat oppgavestyring (Task Manager), inkludert oppgavestatus, fremdriftsoppfølging og fullføring.
- Operativ bruk med ekte dokumenter. Første versjon demonstrerer konseptet med fiktive data.

## 8. Security & Testing

- Kun fiktive dokumenter og testdata skal brukes under utvikling, testing og demonstrasjon. Ingen ekte dokumenter fra Forsvaret skal legges i repoet, lastes opp i applikasjonen eller sendes til eksterne språkmodeller.
- Løsningen skal bruke én ekstern språkmodell via API. Valg av modell og leverandør skal dokumenteres og begrunnes i arkitekturen.
- API-nøkler og andre hemmeligheter skal lagres i miljøvariabler og holdes utenfor Git.
- Applikasjonen skal kunne kjøres og demonstreres uten betalt KI-tilgang gjennom en mock/demo-modus med forhåndsdefinerte aktivitetsforslag. Demo-modusen skal støtte samme brukerflyt for gjennomgang, redigering, godkjenning og avvisning som ved bruk av ekstern språkmodell.
- Kjernefunksjonaliteten skal testes med fiktive dokumenter med kjent fasit.

## 9. Vision

Planlegging skal være oversiktlig, effektiv og basert på et samlet og oppdatert planbilde. På sikt skal løsningen legge til rette for et felles planbilde og sømløs bevegelse mellom års-, måneds-, uke- og dagsvisning, og bidra til bedre informasjonsflyt, raskere beslutninger og mer effektiv bruk av tid og personell.
