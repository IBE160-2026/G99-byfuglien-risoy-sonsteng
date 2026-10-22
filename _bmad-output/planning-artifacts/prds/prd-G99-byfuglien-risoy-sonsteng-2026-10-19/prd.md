---
title: "PRD – KI-assistert interaktivt årshjul"
status: final
created: 2026-10-19
updated: 2026-10-22
---

# PRD: KI-assistert interaktivt årshjul

*Arbeidstittel – bekreftes.*

## 0. Document Purpose

Denne PRD-en beskriver hva første versjon av det KI-assisterte årshjulet skal gjøre. Den er skrevet for prosjektgruppen, faglærer og sensor i IBE160, og for de neste BMAD-workflowene: UX, arkitektur og epics og stories.

PRD-en bygger på godkjent Product Brief (`product-brief.md`) og tilbakemeldingen på den (`tilbakemelding-product-brief.md`). Endringer fra briefen står i §8.2. Begrepene i Glossary (§3) brukes uten synonymer gjennom hele dokumentet.

Kravene har faste ID-er:
- brukerreiser: UJ
- funksjonelle krav: FR, gruppert etter funksjonsområde
- rammebetingelser: C
- ikke-funksjonelle krav: NFR
- suksesskriterier: SM
- åpne spørsmål: OQ
- forutsetninger: P

Begrunnelser og beslutningshistorikk står i `.memlog.md`. Det finnes ennå ikke UX- eller arkitekturdokumenter.

## 1. Vision

Troppssjefer i Forsvaret bruker mye tid på å holde oversikt over informasjon som allerede finnes. Aktiviteter og frister ligger spredt i ordre, dokumenter og frittstående Excel-ark, og planlegging krever manuell leting og gjeninntasting. Tiden går til dokumenthåndtering i stedet for til ledelse og oppdragsløsning.

Løsningen er et interaktivt årshjul som samler planen i ett oversiktlig bilde. Brukeren laster opp en ordre. KI foreslår aktiviteter, og brukeren kontrollerer forslagene mot kildeutdrag fra dokumentet før de legges inn i planen. Årshjulet gir oversikt over hele året og detaljer per måned, og kan brukes direkte i planleggingsmøter.

Det som skiller løsningen fra Excel og vanlige planleggingsverktøy, er at årshjul, KI-assistert uttrekk og brukergodkjenning henger sammen i én arbeidsflyt. Brukeren har alltid kontrollen over hva som legges inn i planen.

## 2. Target User

### 2.1 Jobs To Be Done

*Behovene bygger på Product Brief §1–§3 og §5, og realiseres i UJ-1 til UJ-3.*

- **Når jeg mottar en ordre**, vil jeg få aktivitetene og fristene inn i planen uten å skrive dem inn på nytt, slik at jeg bruker tiden på planlegging og ikke på dokumenthåndtering.
- **Når KI foreslår aktiviteter**, vil jeg kunne kontrollere dem mot det som faktisk står i dokumentet, slik at jeg kan stole på planen.
- **Når planen endres utenom dokumenter**, vil jeg raskt kunne legge inn, flytte og fjerne aktiviteter selv, slik at planen alltid er oppdatert.
- **Når jeg leder et planleggingsmøte**, vil jeg kunne vise et samlet og oppdatert planbilde, slik at jeg raskt kan svare på når noe skjer og hvem som har ansvaret, uten å lete i filer.

### 2.2 Non-Users (v1)

Første versjon utvikles og testes med troppssjefer som primærmålgruppe. Andre lederroller, som kompanisjefer og seksjonssjefer, er ikke egne målgrupper for v1. Flerbrukerfunksjonalitet og deling av planer inngår ikke i første versjon.

*Dette er en målgruppeavgrensning, ikke en teknisk begrensning som hindrer andre lederroller i å bruke applikasjonen.*

### 2.3 Key User Journeys

- **UJ-1. Troppssjef Berg gjør en ny ordre om til aktiviteter i årshjulet**
  - **Persona og kontekst:** Troppssjef Berg leder en tropp og har mottatt en ordre fra overordnet ledd om øvelser, utdanning og frister de kommende månedene. Aktivitetene må inn i planen før neste planleggingsmøte, og Berg vil unngå å skrive dem inn manuelt.
  - **Utgangspunkt:** Berg åpner applikasjonen lokalt i nettleseren og ser årshjulet for inneværende kalenderår med eksisterende aktiviteter. Applikasjonen er en lokal enkeltbrukerløsning uten innlogging.
  - **Flyt:**
    1. **Last opp dokument:** Berg laster opp ordren (et fiktivt dokument i .docx-format). Dokumentet brukes kun til analyse og lagres ikke permanent.
    2. **Få aktivitetsforslag:** Analysen gjøres av språkmodellen eller i demo-modus. Applikasjonen viser en liste med aktivitetsforslag, hver med tittel, startdato, sluttdato, kategori, ansvarsområde og eventuelle merknader foreslått av KI, samt ett eller flere tilknyttede kildeutdrag når dette er tilgjengelig. Feltstatus (manglende, ugyldig eller usikker) er tydelig markert.
    3. **Kontroller forslagene mot kilden:** Berg går gjennom aktivitetsforslagene ett for ett. Ved hvert forslag vises kildeutdragene, for eksempel i et panel til høyre.
       - Ett forslag er komplett, og kildeutdraget bekrefter det. Berg godkjenner.
       - Ett forslag mangler ansvarsområde (manglende). Berg leser kildeutdraget, fyller inn feltet og godkjenner.
       - I ett forslag viser kildeutdraget at sluttdatoen er feil. Berg retter datoen og godkjenner.
       - Ett forslag har en kategori markert som usikker. Berg kontrollerer den mot kildeutdraget og godkjenner uendret.
       - Ett forslag har en lang merknad foreslått av KI. Berg korter den ned før godkjenning; i et annet forslag fjerner Berg merknaden helt.
       - Ett forslag er ikke relevant for troppen. Berg avviser det, og det forkastes uten historikk.
    4. **Legg inn i planen:** Godkjente aktivitetsforslag lagres som aktiviteter og vises i årshjulet. Hvert forslag godkjennes individuelt; det finnes ingen «godkjenn alle».
  - **Klimaks:** Berg går tilbake til årsvisningen og ser de nye aktivitetene plassert i riktige måneder. Ordren er omsatt til plan uten gjeninntasting, og hver aktivitet er kontrollert mot det som faktisk står i dokumentet.
  - **Avslutning:** Når Berg åpner applikasjonen neste gang, ligger de godkjente aktivitetene der fortsatt, med eventuelle merknader. De behandles som vanlige aktiviteter, uten lagret KI-opprinnelse eller kildeutdrag. Verken dokumentet eller de avviste aktivitetsforslagene er lagret. Planen er klar til planleggingsmøtet.
  - **Edge cases:**
    - **E1:** Berg forsøker å godkjenne et aktivitetsforslag der et obligatorisk felt er manglende eller ugyldig, for eksempel en manglende kategori eller en sluttdato som er tidligere enn startdatoen. Godkjenningen stoppes, og applikasjonen viser hvilket felt som må rettes og hvorfor. Et felt som bare er usikkert, med gyldig verdi, stopper ikke godkjenningen.
    - **E1a:** KI klarer ikke å identifisere en passende kategori fra dokumentet (manglende), eller foreslår en kategori fra kategorilisten, men er usikker på om den er riktig (usikker). Er kategorien manglende, må Berg velge en kategori fra kategorilisten før forslaget kan godkjennes. En usikker kategori kan godkjennes uendret etter Bergs kontroll.
    - **E2:** Berg laster opp en skannet PDF, et bilde eller et format som ikke støttes. Applikasjonen melder at dokumentet ikke kan leses, og ingen aktivitetsforslag genereres.
    - **E3:** Analysen finner ingen aktiviteter i dokumentet. Applikasjonen melder dette, og planen er uendret.
    - **E4:** Et aktivitetsforslag har et kildeutdrag som ikke er verifisert, eller ingen kildeutdrag. Applikasjonen viser tydelig at verifisering mangler, og presenterer ikke et ikke verifisert kildeutdrag som sikker kilde. Manglende verifisering blokkerer ikke godkjenning: Berg kan redigere og godkjenne forslaget etter egen kontroll, forutsatt at alle obligatoriske felt er gyldige, eller avvise det.
    - **E5:** Berg går til årshjulet midt i gjennomgangen og kommer tilbake. De ubehandlede aktivitetsforslagene er der fortsatt. Lukker Berg applikasjonen eller laster den på nytt før gjennomgangen er ferdig, går de ubehandlede forslagene tapt, og Berg må laste opp dokumentet på nytt for å fortsette. Aktiviteter som allerede er godkjent, ligger i planen.
    - **E6:** Dokumentet angir bare én dato for en aktivitet. KI antar ikke at aktiviteten varer én dag bare av den grunn.
      - Beskriver dokumentet tydelig en éndagsaktivitet, foreslår KI samme dato som startdato og sluttdato.
      - Gir dokumentet ingen holdepunkter for varigheten, markeres sluttdatoen som manglende. Berg må fylle den inn før forslaget kan godkjennes.
      - Foreslår KI en sluttdato ut fra tvetydige holdepunkter, markeres den som usikker. Berg kontrollerer den og godkjenner den uendret eller retter den.
    - **E7:** Språkmodellen er ikke tilgjengelig, analysen feiler, eller språkmodellen returnerer et ugyldig svar. Applikasjonen viser en tydelig feilmelding, ingen aktivitetsforslag presenteres som gyldige, og planen er uendret.
    - **E8:** Berg laster opp et nytt dokument mens det finnes ubehandlede aktivitetsforslag. Applikasjonen opplyser om at de vil forkastes, og Berg må bekrefte før den nye analysen starter. Avbryter Berg, beholdes de ubehandlede forslagene. Godkjente aktiviteter ligger fortsatt i planen.
  - **Capabilities (blir FR-er):**
    - Systemet må ta imot .docx og tekstbasert PDF, og avvise andre formater med en tydelig melding. → FR-15
    - Systemet må bruke dokumentet kun til analyse og ikke lagre det permanent. → FR-16
    - Systemet må generere aktivitetsforslag med tittel, startdato, sluttdato, kategori, ansvarsområde og eventuelle merknader, og markere feltstatus (manglende, ugyldig eller usikker). Kategori skal hentes fra kategorilisten og kan bare ha status manglende eller usikker. Samme dato som startdato og sluttdato foreslås bare når dokumentet tydelig beskriver en éndagsaktivitet; ellers markeres sluttdatoen som manglende (ingen holdepunkter) eller usikker (tvetydige holdepunkter). → FR-17
    - Systemet må støtte samme flyt i demo-modus med forhåndsdefinerte aktivitetsforslag. → FR-18, FR-30
    - Systemet må gi tydelig beskjed når analysen ikke finner aktiviteter, og planen er uendret. → FR-19
    - Systemet må vise en tydelig feilmelding når analysen feiler eller språkmodellen gir et ugyldig svar, uten å presentere aktivitetsforslag som gyldige, og planen er uendret. → FR-20
    - Systemet må vise ett eller flere kildeutdrag per aktivitetsforslag når dette er tilgjengelig, hentet ordrett fra dokumentteksten og verifisert individuelt av applikasjonen mot den etter normalisering av mellomrom og linjeskift. Et kildeutdrag som ikke er verifisert, eller som mangler, skal markeres tydelig og ikke presenteres som sikker kilde, men skal ikke blokkere godkjenning. Ingen full dokumentviser, automatisk navigasjon eller markering i v1. → FR-27, FR-28, FR-29
    - Systemet må la brukeren redigere, komplettere, godkjenne eller avvise hvert aktivitetsforslag individuelt, inkludert å kontrollere, redigere eller fjerne merknader foreslått av KI før godkjenning. → FR-21, FR-22, FR-23, FR-24
    - Systemet må forkaste avviste aktivitetsforslag uten historikk. → FR-24
    - Systemet må blokkere godkjenning når et obligatorisk felt (tittel, startdato, sluttdato, kategori, ansvarsområde) er manglende eller ugyldig, eller når datoregelen brytes. Et usikkert felt med gyldig verdi kan godkjennes uendret. Samme valideringsregler gjelder som ved manuell opprettelse og redigering (UJ-2). → FR-2, FR-23
    - Systemet må aldri legge inn en KI-generert aktivitet uten brukerens eksplisitte godkjenning. → FR-25
    - Systemet må lagre godkjente aktiviteter slik at de er tilgjengelige når applikasjonen åpnes på nytt, og beholde ubehandlede aktivitetsforslag midlertidig i den aktive økten, men ikke lagre dem permanent. → FR-7, FR-26
    - Systemet må behandle en godkjent aktivitet som en vanlig aktivitet, uten å lagre KI-opprinnelse eller kildeutdrag. → FR-23

- **UJ-2. Troppssjef Berg oppretter, flytter og sletter aktiviteter manuelt**
  - **Persona og kontekst:** Etter et koordineringsmøte med overordnet ledd har Troppssjef Berg fått tre endringer som ikke står i noe dokument: en ny todagers skyteøvelse, en utdanningsaktivitet som er flyttet én uke (opprinnelig lagt inn fra et aktivitetsforslag), og en aktivitet som er avlyst. Planen må oppdateres før Berg går gjennom den med troppen.
  - **Utgangspunkt:** Berg åpner applikasjonen lokalt i nettleseren og ser årshjulet for inneværende kalenderår.
  - **Flyt:**
    1. **Opprett aktivitet:** Berg velger å opprette en ny aktivitet og fyller inn tittel, startdato og sluttdato (flerdagsaktivitet over to dager). Berg velger kategori fra kategorilisten, skriver ansvarsområde som fritekst og noterer forberedelser til skyteøvelsen i merknader. Berg lagrer, og aktiviteten vises i riktig måned i årshjulet.
    2. **Rediger aktivitet:** Berg åpner utdanningsaktiviteten fra årshjulet og ser detaljene. Aktiviteten behandles som en vanlig aktivitet, uten KI-opprinnelse eller kildeutdrag. Berg endrer startdato og sluttdato, legger til en merknad om hvorfor datoen er flyttet, og lagrer. Aktiviteten flyttes til riktig sted i årshjulet.
    3. **Slett aktivitet:** Berg åpner den avlyste aktiviteten og velger å slette den. Applikasjonen ber om bekreftelse. Berg bekrefter, og aktiviteten fjernes fra årshjulet. Sletting kan ikke angres i v1.
  - **Klimaks:** Årshjulet viser planen slik den faktisk er etter møtet, uten at Berg har åpnet Excel eller andre dokumenter.
  - **Avslutning:** Endringene er lagret og er tilgjengelige når applikasjonen åpnes på nytt.
  - **Edge cases:**
    - **E1:** Berg forsøker å lagre en aktivitet der et obligatorisk felt mangler, for eksempel kategori. Lagringen stoppes, og applikasjonen viser hvilket felt som må rettes.
    - **E2:** Berg legger inn en sluttdato som er tidligere enn startdatoen. Lagringen stoppes, og applikasjonen forklarer hvorfor.
    - **E3:** Berg velger å slette, men avbryter i bekreftelsen. Aktiviteten slettes ikke.
    - **E4:** Berg oppretter en éndagsaktivitet. Startdato og sluttdato er like, og aktiviteten lagres.
  - **Capabilities (blir FR-er):**
    - Systemet må la brukeren opprette en aktivitet med tittel, startdato, sluttdato, kategori (valgt fra kategorilisten), ansvarsområde (fritekst) og valgfrie merknader. → FR-1
    - Systemet må la brukeren åpne en aktivitet fra årshjulet og se all informasjon om den, inkludert merknader. → FR-3
    - Systemet må la brukeren redigere og lagre en aktivitet, inkludert merknader, slik at årshjulet oppdateres. → FR-4, FR-6
    - Systemet må la brukeren slette en aktivitet etter bekreftelse (ingen angrefunksjon i v1). → FR-5
    - Systemet må behandle godkjente aktivitetsforslag som vanlige aktiviteter, uten lagring eller visning av KI-opprinnelse eller kildeutdrag. → FR-4, FR-23
    - Systemet må blokkere lagring når et obligatorisk felt mangler eller datoregelen brytes. Merknader er ikke obligatorisk. Samme valideringsregler gjelder som ved godkjenning av aktivitetsforslag (UJ-1). → FR-2
    - Systemet må lagre endringer slik at de er tilgjengelige når applikasjonen åpnes på nytt. → FR-7

- **UJ-3. Troppssjef Berg bruker årshjulet til å forberede og gjennomføre et planleggingsmøte**
  - **Persona og kontekst:** Troppssjef Berg skal ha planleggingsmøte med troppsledelsen og trenger samlet oversikt over planen for resten av året, et mer detaljert bilde av neste måned, og mulighet til å se detaljer i enkeltaktiviteter underveis i møtet uten å lete i dokumenter.
  - **Utgangspunkt:** Berg åpner applikasjonen lokalt i nettleseren. Årshjulet for inneværende kalenderår vises.
  - **Flyt:**
    1. **Se årsvisningen:** Det sirkulære årshjulet viser 12 måneder med aktivitetene plassert i månedene de hører til. Hver kategori har en fast og konsekvent visuell identitet, slik at Berg raskt ser hva slags aktiviteter som ligger hvor og hvilke perioder som er travle. Kategorien kan identifiseres uten å være avhengig av farge alene.
    2. **Velg kalenderår:** Berg bytter til neste kalenderår for å sjekke en øvelse i januar som allerede er lagt inn, og bytter tilbake.
    3. **Zoom inn til måned:** Berg velger neste måned og får en månedsvisning med ukeinndeling etter ISO 8601 (mandag som første ukedag, norske ukenumre). Aktivitetene vises i ukene de hører til. Berg går deretter direkte videre til måneden etter, uten å gå via årsvisningen.
    4. **Åpne en aktivitet:** Berg åpner en aktivitet i månedsvisningen og ser all informasjon om den: tittel, startdato, sluttdato, kategori, ansvarsområde og merknader. Herfra kan Berg redigere eller slette aktiviteten (UJ-2).
    5. **Zoom ut:** Berg går tilbake til årsvisningen for kalenderåret til måneden som vises.
  - **Klimaks:** I møtet viser Berg årshjulet på skjermen. Spørsmål om når noe skjer og hvem som har ansvaret, besvares med noen få klikk, uten leting i Excel-ark eller ordre.
  - **Avslutning:** Berg lukker applikasjonen. Ingenting er endret med mindre Berg har redigert.
  - **Edge cases:**
    - **E1:** En flerdagsaktivitet strekker seg over to måneder (f.eks. 29. september–2. oktober) eller over et årsskifte. Aktiviteten vises i alle måneder og uker den berører, i både årsvisning og månedsvisning og i begge kalenderår, men er lagret som én aktivitet.
    - **E2:** Ukeinndelingen ved årsskifte følger ISO 8601, slik at uker som strekker seg over to kalenderår får riktig ukenummer (f.eks. uke 1 som starter i desember, eller uke 53).
    - **E3:** Berg velger en måned eller et kalenderår uten aktiviteter. Visningen er tom og viser tydelig at ingen aktiviteter er lagt inn.
    - **E4:** Mange aktiviteter ligger i samme måned. Årsvisningen forblir lesbar og oversiktlig. Visuell løsning avgjøres i UX-workflowen.
  - **Capabilities (blir FR-er):**
    - Systemet må vise årsvisningen som et sirkulært, interaktivt årshjul med 12 måneder der aktivitetene er plassert i riktig måned. → FR-8
    - Systemet må vise inneværende kalenderår ved oppstart og la brukeren velge et annet kalenderår. → FR-9
    - Systemet må la brukeren zoome inn fra årsvisning til månedsvisning og tilbake. → FR-10
    - Systemet må la brukeren navigere direkte mellom måneder i månedsvisningen, også over årsskiftet, uten å gå tilbake til årsvisningen. → FR-10
    - Systemet må vise månedsvisningen med ukeinndeling etter ISO 8601 (mandag som første ukedag, norske ukenumre), også korrekt ved årsskifter. → FR-10
    - Systemet må la brukeren åpne en aktivitet fra årsvisning og månedsvisning og se all informasjon om den, inkludert merknader. → FR-3
    - Systemet må vise en flerdagsaktivitet i alle måneder og uker den berører, også over årsskifte, og lagre den som én aktivitet. → FR-11
    - Systemet må gi hver kategori i kategorilisten en fast, konsekvent visuell identitet i årshjulet som ikke er avhengig av farge alene. Brukertilpasning av farger er utenfor v1. → FR-12
    - Systemet må holde årsvisningen lesbar og oversiktlig når mange aktiviteter ligger i samme måned. → FR-13
    - Systemet må vise en tydelig tom tilstand når det ikke finnes aktiviteter i valgt periode. → FR-14
  - **Utenfor v1 (fra Product Brief, OUT):** flere konsentriske ringer, ukevisning med aktiviteter fordelt på mandag–søndag, og omfattende tilpasning av format, layout og farger.

## 3. Glossary

*Alle øvrige deler av PRD-en og senere BMAD-artefakter skal bruke disse begrepene uten synonymer.*

**Plan og visning**

- **Plan** — Alle lagrede aktiviteter. Én plan i v1 (én bruker).
- **Årshjul** — Den interaktive visningen av planen, med to nivåer: årsvisning og månedsvisning.
- **Årsvisning** — Sirkulært, interaktivt årshjul for ett kalenderår, med 12 måneder.
- **Månedsvisning** — Én måned med ukeinndeling. Nås ved å zoome inn fra årsvisningen. Brukeren kan navigere direkte mellom måneder, også over årsskiftet.
- **Kalenderår** — Året som vises i årshjulet. Inneværende år ved oppstart.
- **Uke** — Uke etter ISO 8601: mandag som første ukedag, norsk ukenummer.

**Aktivitet**

- **Aktivitet** — En planlagt hendelse lagret i planen. Har tittel, startdato, sluttdato, kategori og ansvarsområde, og kan ha merknader. Lagres én gang, selv om den vises i flere perioder. Det skilles ikke mellom aktiviteter som er opprettet manuelt og aktiviteter som kommer fra et godkjent aktivitetsforslag.
- **Éndagsaktivitet** — Aktivitet der sluttdato er lik startdato.
- **Flerdagsaktivitet** — Aktivitet der sluttdato er etter startdato.
- **Datoregel** — Startdato og sluttdato er obligatoriske, og sluttdato kan aldri være tidligere enn startdato. Gjelder ved manuell opprettelse, redigering og godkjenning av aktivitetsforslag.
- **Obligatoriske felt** — Tittel, startdato, sluttdato, kategori og ansvarsområde.
- **Kategori** — Én verdi valgt fra kategorilisten. Kategorier utenfor kategorilisten kan ikke velges eller opprettes. Hver kategori har en fast visuell identitet som ikke er avhengig av farge alene.
- **Kategoriliste** — Den forhåndsdefinerte, faste listen over kategorier. Innholdet fastsettes i UX-workflowen.
- **Ansvarsområde** — Fritekstfelt som angir hvem som har ansvaret for aktiviteten.
- **Merknader** — Valgfritt fritekstfelt på en aktivitet for lengre tekst med flere avsnitt: utfyllende informasjon, kladd, vurderinger, forberedelser og egne tanker. Lagres permanent sammen med aktiviteten.

**Dokument og KI**

- **Dokument** — En .docx-fil eller tekstbasert PDF som brukeren laster opp, for eksempel en ordre. Brukes kun til analyse og lagres ikke permanent.
- **Dokumenttekst** — Teksten som hentes ut av et dokument. Grunnlag for analyse og for verifisering av kildeutdrag.
- **Analyse** — Prosessen der språkmodellen eller demo-modus genererer aktivitetsforslag fra dokumentteksten.
- **Språkmodell** — Den ene eksterne KI-tjenesten som brukes via API.
- **Demo-modus** — Kjøremodus der analysen gir forhåndsdefinerte aktivitetsforslag for støttede testdokumenter i stedet for å kalle språkmodellen, med samme brukerflyt.
- **Aktivitetsforslag** — En foreslått aktivitet fra analysen. Har de samme feltene som en aktivitet, inkludert eventuelle merknader foreslått av KI, samt ett eller flere tilknyttede kildeutdrag når dette er tilgjengelig. Eksisterer bare under gjennomgangen og lagres ikke permanent. Blir en aktivitet først ved godkjenning.
- **Feltstatus** — Markering av et felt i et aktivitetsforslag: *manglende* (ingen verdi), *ugyldig* (verdien bryter reglene, f.eks. brudd på datoregelen) eller *usikker* (KI er usikker på verdien). Et felt kan være usikkert uten å være ugyldig. Kategori kan bare ha status *manglende* eller *usikker*. Manglende eller ugyldige obligatoriske felt må rettes før godkjenning; et usikkert felt med gyldig verdi kan godkjennes uendret etter brukerens kontroll.
- **Kildeutdrag** — Tekst hentet ordrett fra dokumentteksten som et aktivitetsforslag bygger på. Er enten *verifisert* (finnes i dokumentteksten etter normalisering av mellomrom og linjeskift) eller *ikke verifisert*. Et aktivitetsforslag kan ha flere kildeutdrag, og applikasjonen verifiserer hvert for seg. Mangler kildeutdrag, eller er det ikke verifisert, markeres manglende verifisering tydelig; forslaget kan likevel godkjennes.
- **Gjennomgang** — Steget der brukeren kontrollerer, redigerer, godkjenner eller avviser aktivitetsforslagene fra ett dokument. Ubehandlede aktivitetsforslag beholdes i økten, men lagres ikke permanent.
- **Økt** — Perioden fra applikasjonen åpnes til den lukkes eller lastes på nytt.
- **Godkjenning** — Brukerens eksplisitte handling som gjør et aktivitetsforslag om til en aktivitet. Krever at alle obligatoriske felt er gyldige og at datoregelen er oppfylt.
- **Avvisning** — Brukerens handling som forkaster et aktivitetsforslag uten historikk.
- **Kjerneflyt** — Opplasting av dokument, gjennomgang og godkjenning av aktivitetsforslag, etterfulgt av visning i årshjulet.

**Kvalitet**

- **Testdokument** — Fiktivt dokument som brukes til testing og demonstrasjon.
- **Fasit** — Forhåndsdefinerte forventede aktiviteter for et testdokument.

## 4. Features

### 4.1 Aktivitetshåndtering

**Description:** Brukeren kan opprette, åpne, redigere og slette aktiviteter i planen. Alle aktiviteter behandles likt, uavhengig av om de er opprettet manuelt eller kommer fra et godkjent aktivitetsforslag. Valideringsreglene i FR-2 er felles for manuell opprettelse, redigering og godkjenning (§4.4). Realiserer UJ-2, og delvis UJ-1 og UJ-3.

**Functional Requirements:**

#### FR-1: Opprette aktivitet

Brukeren kan opprette en aktivitet med tittel, startdato, sluttdato, kategori (valgt fra kategorilisten), ansvarsområde (fritekst) og valgfrie merknader. Realiserer UJ-2.

**Consequences (testable):**
- En gyldig aktivitet lagres og vises i alle måneder den berører i årshjulet.
- Aktiviteten lagres én gang, selv om den vises i flere perioder.
- Kategori kan bare velges fra kategorilisten.
- En éndagsaktivitet (startdato lik sluttdato) lagres.

#### FR-2: Validering av aktivitet

Systemet blokkerer lagring og godkjenning når et obligatorisk felt er manglende eller ugyldig, eller når datoregelen brytes. Realiserer UJ-1, UJ-2.

**Consequences (testable):**
- Mangler tittel, startdato, sluttdato, kategori eller ansvarsområde, lagres ikke aktiviteten, og applikasjonen viser hvilket felt det gjelder.
- Et obligatorisk fritekstfelt som bare inneholder mellomrom, regnes som manglende.
- Kategori kan bare velges fra kategorilisten. Kategorier utenfor kategorilisten kan ikke velges eller opprettes.
- Er sluttdato tidligere enn startdato, lagres ikke aktiviteten, og applikasjonen forklarer hvorfor.
- Tomme merknader blokkerer ikke lagring.
- De samme reglene, inkludert konsekvent bruk av kategorilisten, gjelder ved opprettelse (FR-1), redigering (FR-4) og godkjenning av aktivitetsforslag (§4.4).

#### FR-3: Åpne aktivitet

Brukeren kan åpne en aktivitet fra årsvisningen og månedsvisningen og se alle feltene. Realiserer UJ-2, UJ-3.

**Consequences (testable):**
- Alle felt vises med lagrede verdier.
- Merknader vises med bevart avsnittsinndeling.
- Fra en åpnet aktivitet kan brukeren gå videre til redigering (FR-4) eller sletting (FR-5).

#### FR-4: Redigere aktivitet

Brukeren kan endre alle felt i en aktivitet, inkludert merknader, og lagre endringene. Realiserer UJ-2.

**Consequences (testable):**
- Etter lagring vises aktiviteten med nye verdier, og i nye perioder dersom datoene er endret.
- En redigering som bryter FR-2, lagres ikke, og den tidligere lagrede aktiviteten er uendret.
- En aktivitet som kommer fra et godkjent aktivitetsforslag, kan redigeres på samme måte som en manuelt opprettet aktivitet.

#### FR-5: Slette aktivitet

Brukeren kan slette en aktivitet etter bekreftelse. Realiserer UJ-2.

**Consequences (testable):**
- Ved bekreftelse fjernes aktiviteten fra planen og årshjulet.
- Ved avbrutt bekreftelse er planen uendret.

**Out of Scope:**
- Angrefunksjon.

#### FR-6: Merknader

Brukeren kan legge inn valgfrie merknader på en aktivitet som lengre fritekst over flere avsnitt. Feltet kan ha en romslig øvre tegngrense som hindrer urimelig store tekstmengder uten å hemme normal bruk. Grensen fastsettes i arkitekturen. Merknader lagres permanent sammen med aktiviteten. Realiserer UJ-2, UJ-3.

**Consequences (testable):**
- Merknader med flere avsnitt lagres og vises igjen med bevart avsnittsinndeling.
- Merknader kan legges til, endres og tømmes via redigering (FR-4).
- En merknad som overskrider grensen, enten den er skrevet av brukeren eller foreslått av KI, forkortes ikke automatisk uten at brukeren informeres. Håndteringen avgjøres i UX-workflowen og arkitekturen.

#### FR-7: Varig lagring

Alle aktiviteter lagres lokalt og er tilgjengelige når applikasjonen åpnes på nytt. Realiserer UJ-1, UJ-2, UJ-3.

**Consequences (testable):**
- Opprettede, redigerte og slettede aktiviteter har samme tilstand etter at nettleser og applikasjon er startet på nytt.

### 4.2 Årshjul

**Description:** Årshjulet viser planen for ett kalenderår på to nivåer: årsvisning og månedsvisning. Brukeren kan bytte kalenderår, zoome mellom nivåene, navigere mellom måneder og åpne aktiviteter (FR-3). Realiserer UJ-3, og delvis UJ-1 og UJ-2.

**Functional Requirements:**

#### FR-8: Årsvisning

Systemet viser valgt kalenderår som et sirkulært, interaktivt årshjul med 12 måneder. Hver aktivitet er plassert i månedene den berører. Den konkrete visuelle utformingen avgjøres i UX-workflowen. Realiserer UJ-3, UJ-1, UJ-2.

**Consequences (testable):**
- Årsvisningen er sirkulær og viser alle 12 måneder i valgt kalenderår.
- En aktivitet vises i hver måned der minst én dag mellom startdato og sluttdato faller.
- Etter opprettelse (FR-1), redigering (FR-4), sletting (FR-5) eller godkjenning (§4.4) viser årsvisningen den oppdaterte planen uten omstart.

#### FR-9: Valg av kalenderår

Ved oppstart vises inneværende kalenderår. Brukeren kan bytte til et annet kalenderår. Det er ingen fast begrensning på hvilke kalenderår som kan velges. Realiserer UJ-3.

**Consequences (testable):**
- Ved oppstart vises kalenderåret for dagens dato.
- Etter bytte vises bare aktiviteter som berører valgt kalenderår.

#### FR-10: Månedsvisning og navigasjon

Brukeren kan zoome inn fra årsvisningen til en valgt måned og zoome ut igjen. Fra månedsvisningen kan brukeren navigere direkte til en annen måned uten å gå tilbake til årsvisningen. Utformingen av navigasjonen avgjøres i UX-workflowen. Realiserer UJ-3.

**Consequences (testable):**
- Månedsvisningen viser alle uker som berører måneden, med ukenummer etter ISO 8601 og mandag som første ukedag.
- Aktiviteter vises i ukene de berører.
- Brukeren kan gå fra én måned til en annen direkte i månedsvisningen.
- Navigasjon forbi desember eller januar fører til tilstøtende kalenderår. Zoom ut gir årsvisningen for kalenderåret til måneden som vises.
- Ukenummer er korrekte, også ved årsskifte. Testbare eksempler:
  - 29.12.2025 ligger i uke 1 (2026).
  - 29.01.2026 ligger i uke 5 (2026).
  - 31.12.2026 og 02.01.2027 ligger begge i uke 53 (2026).

#### FR-11: Flerdagsaktivitet over flere perioder

En flerdagsaktivitet vises i alle måneder og uker den berører, også over årsskiftet, men lagres som én aktivitet. Realiserer UJ-3.

**Consequences (testable):**
- En aktivitet fra 29.09 til 02.10 vises i september og oktober i årsvisningen, og i de berørte ukene i begge månedsvisningene.
- En aktivitet fra 30.12.2026 til 02.01.2027 vises i desember 2026 og januar 2027.
- Endres eller slettes aktiviteten fra én periode, gjelder endringen alle periodene.

#### FR-12: Visuell identitet for kategorier

Hver kategori i kategorilisten har en fast visuell identitet i årshjulet. Realiserer UJ-3.

**Consequences (testable):**
- Identiteten er den samme i årsvisning og månedsvisning, og endres ikke mellom økter.
- Kategorien kan identifiseres uten farge, for eksempel med tekst eller symbol. Den skal kunne gjenkjennes i gråtonevisning.

**Out of Scope:**
- Brukertilpasning av farger.

#### FR-13: Lesbarhet ved mange aktiviteter

Årsvisningen forblir lesbar og oversiktlig når mange aktiviteter ligger i samme måned. Den visuelle løsningen avgjøres i UX-workflowen, og antall aktiviteter i testscenarioer fastsettes i testplanen. Realiserer UJ-3.

**Consequences (testable):**
- Alle aktiviteter kan finnes og åpnes via årsvisningen eller månedsvisningen, også når mange aktiviteter ligger i samme måned.
- Ingen aktivitet skjules uten at det går tydelig fram at det finnes flere.

#### FR-14: Tom tilstand

Når valgt periode ikke har aktiviteter, viser årshjulet en tydelig tom tilstand. Realiserer UJ-3.

**Consequences (testable):**
- En årsvisning eller månedsvisning uten aktiviteter viser tydelig at ingen aktiviteter er lagt inn.

**Out of Scope:** Se §7 Non-Goals.

### 4.3 Dokumentopplasting og analyse

**Description:** Brukeren laster opp ett dokument om gangen, og systemet analyserer dokumentteksten med språkmodellen eller i demo-modus og genererer aktivitetsforslag til gjennomgang (§4.4). Dokumentet brukes kun til analyse og lagres ikke permanent. Realiserer UJ-1.

**Functional Requirements:**

#### FR-15: Laste opp dokument

Brukeren kan laste opp ett dokument om gangen i formatet .docx eller tekstbasert PDF. Realiserer UJ-1.

**Consequences (testable):**
- En .docx-fil eller tekstbasert PDF tas imot, og analysen starter. Finnes det ubehandlede aktivitetsforslag, må brukeren først bekrefte at de kan forkastes (FR-26).
- En PDF uten dokumenttekst som kan hentes ut (for eksempel en skannet PDF), et bilde eller et annet format avvises med en tydelig melding.
- Ved avvisning genereres ingen aktivitetsforslag, og planen er uendret.
- Flere dokumenter kan analyseres etter hverandre, men ikke lastes opp eller analyseres samtidig.

**Out of Scope (fra Product Brief, OUT):**
- OCR og analyse av skannede dokumenter eller bilder.

#### FR-16: Ingen permanent lagring av dokument

Dokumentet og dokumentteksten brukes kun til analyse, inkludert verifisering av kildeutdrag (§4.5), og lagres ikke permanent. Realiserer UJ-1.

**Consequences (testable):**
- Når applikasjonen er startet på nytt, finnes verken dokumentet eller dokumentteksten i applikasjonen.
- Bare godkjente aktiviteter, med eventuelle merknader, lagres i planen (FR-7).

#### FR-17: Generere aktivitetsforslag

Analysen genererer en liste med aktivitetsforslag fra dokumentteksten. Hvert forslag har tittel, startdato, sluttdato, kategori, ansvarsområde og eventuelle merknader foreslått av KI. Hvert felt har feltstatus der det er relevant. Realiserer UJ-1.

**Consequences (testable):**
- Hvert aktivitetsforslag har alle feltene. Felt uten verdi er markert som *manglende*.
- Kategori foreslås bare fra kategorilisten, og status *ugyldig* brukes ikke for kategori.
- Kan KI ikke identifisere en passende kategori fra dokumentet, markeres feltet som *manglende*.
- Foreslår KI en kategori fra kategorilisten, men er usikker på om den er riktig, markeres feltet som *usikker*.
- Returnerer språkmodellen en kategori som ikke finnes i kategorilisten, presenteres den ikke som en valgbar kategori. Feltet markeres som *manglende*, og brukeren må velge en kategori fra kategorilisten før godkjenning.
- En kategori fra kategorilisten som KI foreslår uten identifisert usikkerhet, får ingen avviksstatus.
- Et forslag som bryter datoregelen, får sluttdatoen markert som *ugyldig*.
- Beskriver dokumentet tydelig en éndagsaktivitet, foreslås samme dato som startdato og sluttdato.
- KI antar ikke at en aktivitet varer én dag bare fordi dokumentet angir én dato.
- Gir dokumentet ingen holdepunkter for aktivitetens varighet, markeres sluttdatoen som *manglende*.
- Foreslår KI en sluttdato ut fra tvetydige holdepunkter i dokumentet, markeres sluttdatoen som *usikker*.
- Merknader foreslått av KI kan inneholde informasjon fra dokumentet og er valgfrie.

#### FR-18: Demo-modus

Applikasjonen kan kjøres i demo-modus med forhåndsdefinerte aktivitetsforslag for et begrenset antall fiktive testdokumenter. Formålet er å kunne demonstrere og teste hele kjerneflyten uten API-nøkkel, betalt KI-tilgang eller tilgjengelig språkmodell. Demo-modus erstatter ikke analysen med språkmodellen. Realiserer UJ-1.

**Consequences (testable):**
- Det går tydelig fram for brukeren når applikasjonen kjører i demo-modus.
- I demo-modus sendes ingen data til språkmodellen, og det kreves ingen API-nøkkel.
- Gjennomgang, redigering, komplettering, godkjenning og avvisning fungerer på samme måte som med språkmodellen.
- For et støttet testdokument gir demo-modus de samme aktivitetsforslagene hver gang, slik at resultatet kan sammenlignes med fasit.
- Lastes et dokument opp som demo-modus ikke støtter, får brukeren en tydelig melding om dette. Ingen aktivitetsforslag presenteres som om de kommer fra dokumentet, og planen er uendret.

#### FR-19: Ingen aktiviteter funnet

Når analysen ikke finner aktiviteter i dokumentet, får brukeren beskjed om det. Realiserer UJ-1.

**Consequences (testable):**
- Finner analysen ingen aktiviteter, får brukeren en tydelig melding om dette, og planen er uendret.

#### FR-20: Feil ved analyse

Når analysen feiler, får brukeren en tydelig feilmelding, og planen påvirkes ikke. Realiserer UJ-1.

**Consequences (testable):**
- Er språkmodellen ikke tilgjengelig, feiler analysen, eller returnerer språkmodellen et ugyldig svar, får brukeren en tydelig feilmelding.
- Etter en feilet analyse presenteres ingen aktivitetsforslag som gyldige.
- Planen er uendret.

### 4.4 Gjennomgang og godkjenning

**Description:** Brukeren går gjennom aktivitetsforslagene fra ett dokument og kontrollerer, redigerer, kompletterer, godkjenner eller avviser hvert forslag individuelt, i valgfri rekkefølge. Ingen KI-generert aktivitet legges inn i planen uten brukerens eksplisitte godkjenning. Valideringsreglene er de samme som for manuelle aktiviteter (FR-2). Realiserer UJ-1.

**Functional Requirements:**

#### FR-21: Vise aktivitetsforslag til gjennomgang

Etter analysen vises alle aktivitetsforslagene fra dokumentet, med feltstatus tydelig markert. Realiserer UJ-1.

**Consequences (testable):**
- Alle aktivitetsforslag fra analysen vises.
- For hvert forslag vises alle feltene. Felt med status *manglende*, *ugyldig* eller *usikker* er tydelig markert.
- Forslagene kan gjennomgås, redigeres, godkjennes og avvises i valgfri rekkefølge.
- Kildeutdrag vises etter §4.5.

#### FR-22: Redigere og komplettere aktivitetsforslag

Brukeren kan endre og fylle inn alle feltene i et aktivitetsforslag før godkjenning, inkludert merknader foreslått av KI. Realiserer UJ-1.

**Consequences (testable):**
- Alle felt kan endres. Kategori velges fra kategorilisten.
- Merknader foreslått av KI kan kortes ned, endres eller fjernes helt.
- Når brukeren har endret eller fylt inn et felt, gjelder ikke lenger statusen KI satte for feltet.
- Feltet valideres etter FR-2, og en verdi som er manglende eller ugyldig, markeres fortsatt.

#### FR-23: Godkjenne aktivitetsforslag

Brukeren godkjenner hvert aktivitetsforslag individuelt. Ved godkjenning blir forslaget en aktivitet i planen. Realiserer UJ-1.

**Consequences (testable):**
- Godkjenning blokkeres når et obligatorisk felt er *manglende* eller *ugyldig*, eller når datoregelen brytes. Applikasjonen viser hvilket felt som må rettes, og hvorfor (FR-2).
- Et felt med status *usikker* og gyldig verdi blokkerer ikke godkjenning.
- En godkjent aktivitet lagres umiddelbart (FR-7), vises i årshjulet (FR-8) og behandles som en vanlig aktivitet. KI-opprinnelse og kildeutdrag lagres ikke.
- Det finnes ingen funksjon for å godkjenne alle forslag samtidig.

#### FR-24: Avvise aktivitetsforslag

Brukeren kan avvise et aktivitetsforslag. Realiserer UJ-1.

**Consequences (testable):**
- Et avvist forslag forkastes uten historikk, og planen er uendret.

#### FR-25: Ingen aktivitet uten godkjenning

Ingen KI-generert aktivitet legges inn i planen uten brukerens eksplisitte godkjenning. Realiserer UJ-1.

**Consequences (testable):**
- Etter en analyse uten godkjenninger er planen uendret.
- Planen inneholder bare de aktivitetsforslagene brukeren har godkjent.

#### FR-26: Ubehandlede aktivitetsforslag i økten

Ubehandlede aktivitetsforslag beholdes midlertidig i den aktive økten, men lagres ikke permanent. Realiserer UJ-1.

**Consequences (testable):**
- Brukeren kan gå fra gjennomgangen til årshjulet og tilbake uten at ubehandlede forslag eller endringer i dem går tapt.
- Lukkes applikasjonen eller lastes den på nytt, går ubehandlede forslag tapt. Brukeren må laste opp dokumentet på nytt for å fortsette.
- Aktiviteter som er godkjent, ligger fortsatt i planen.
- Laster brukeren opp et nytt dokument mens det finnes ubehandlede forslag, får brukeren beskjed om at de vil forkastes, og må bekrefte før analysen starter. Avbryter brukeren, beholdes de ubehandlede forslagene. Presentasjonen av bekreftelsen avgjøres i UX-workflowen.

**Out of Scope:**
- Automatisk konfliktanalyse, inkludert kontroll av duplikater eller overlapp mot eksisterende aktiviteter.

### 4.5 Kildeutdrag

**Description:** Under gjennomgangen vises kildeutdragene hvert aktivitetsforslag bygger på, slik at brukeren kan kontrollere forslaget mot det som faktisk står i dokumentet. Applikasjonen verifiserer hvert kildeutdrag mot dokumentteksten. Manglende verifisering markeres tydelig, men blokkerer ikke godkjenning. Kildeutdrag lagres ikke. Realiserer UJ-1. *(Gruppegodkjent tillegg utover Product Brief.)*

**Functional Requirements:**

#### FR-27: Vise kildeutdrag

Under gjennomgangen vises kildeutdragene til hvert aktivitetsforslag sammen med forslaget, når kildeutdrag er tilgjengelig. Plassering og utforming avgjøres i UX-workflowen. Realiserer UJ-1.

**Consequences (testable):**
- Et aktivitetsforslag kan ha ett eller flere kildeutdrag, når relevant informasjon står i ulike deler av dokumentet.
- Et aktivitetsforslag med kildeutdrag viser kildeutdragene samtidig med forslagets felt.
- Et aktivitetsforslag uten kildeutdrag viser tydelig at kildeutdrag mangler.

#### FR-28: Verifisering av kildeutdrag

Applikasjonen verifiserer hvert kildeutdrag individuelt mot dokumentteksten. Et kildeutdrag er *verifisert* hvis teksten finnes i dokumentteksten etter normalisering av mellomrom og linjeskift, og ellers *ikke verifisert*. Realiserer UJ-1.

**Consequences (testable):**
- Et kildeutdrag som finnes i dokumentteksten, vises som verifisert.
- Et kildeutdrag som bare avviker fra dokumentteksten i mellomrom eller linjeskift, vises som verifisert.
- Et kildeutdrag med andre tekstlige avvik vises tydelig som ikke verifisert og presenteres ikke som sikker kilde.
- Har et aktivitetsforslag flere kildeutdrag, vises status for hvert kildeutdrag.
- Verifiseringen bygger ikke på språkmodellens egen vurdering eller på KI-basert vurdering av semantisk likhet.

#### FR-29: Kildeutdrag og godkjenning

Manglende eller ikke verifiserte kildeutdrag blokkerer ikke godkjenning, og kildeutdrag lagres ikke. Realiserer UJ-1.

**Consequences (testable):**
- Et aktivitetsforslag uten kildeutdrag, eller med ett eller flere ikke verifiserte kildeutdrag, kan godkjennes når alle obligatoriske felt er gyldige (FR-23).
- Etter godkjenning eller avvisning finnes kildeutdragene ikke lenger i applikasjonen (FR-16, FR-23).

#### FR-30: Kildeutdrag i demo-modus

Demo-modus støtter samme visning og verifisering av kildeutdrag som analysen med språkmodellen. Realiserer UJ-1.

**Consequences (testable):**
- De forhåndsdefinerte aktivitetsforslagene for et støttet testdokument har kildeutdrag som finnes i testdokumentet.
- Kildeutdragene vises og verifiseres på samme måte som ved analyse med språkmodellen, slik at verifiseringen kan testes mot fasit.

**Out of Scope:**
- Full dokumentvisning, automatisk navigasjon til kildeutdraget i dokumentet og markering i dokumentet.

## 5. Constraints

*Rammebetingelser som gjelder hele løsningen. Repoet er offentlig, og analysen sender dokumenttekst til en ekstern språkmodell. Det er bakgrunnen for C-1 til C-4.*

**C-1: Kun fiktive dokumenter og testdata**
Bare fiktive dokumenter og testdata brukes under utvikling, testing og demonstrasjon. Ekte dokumenter fra Forsvaret skal ikke legges i repoet, lastes opp i applikasjonen eller sendes til språkmodellen. Det gjelder også ugraderte interne dokumenter.
- *Etterprøving:* Alle testdokumenter i repoet er merket som fiktive. Ingen dokumenter i repoet stammer fra Forsvaret.

**C-2: Én ekstern språkmodell**
Analysen bruker én ekstern språkmodell via API. Valg av modell og leverandør dokumenteres og begrunnes i arkitekturen.

**C-3: Data som sendes til språkmodellen**
Til språkmodellen sendes bare dokumentteksten, nødvendig kategorikontekst og instruksjonene som trengs for å hente ut aktivitetsforslag. Eksisterende aktiviteter i planen sendes ikke. Analysen gjør ingen konfliktanalyse eller duplikatkontroll (§4.4). I demo-modus sendes ingen data (FR-18).

**C-4: Hemmeligheter**
API-nøkler og andre hemmeligheter ligger i miljøvariabler og holdes utenfor Git.
- *Etterprøving:* Repoet og Git-historikken inneholder ingen API-nøkler eller andre hemmeligheter.

**C-5: Lokal kjørbarhet**
Applikasjonen kan kjøres lokalt i nettleseren ved å følge README. Det krever ikke gruppens nøkler, betalte kontoer eller egen infrastruktur. Ved analyse med språkmodellen er ingen andre eksterne tjenester nødvendige. Demo-modus fungerer uten eksterne tjenester og uten API-nøkkel (FR-18).
- *Etterprøving:* En person utenfor gruppen kloner repoet, følger README og gjennomfører kjerneflyten i demo-modus: opplasting av et støttet testdokument, gjennomgang, godkjenning og visning i årshjulet.

**C-6: Lokal enkeltbrukerløsning**
Applikasjonen er en lokal enkeltbrukerløsning uten innlogging. Planen lagres lokalt (FR-7).

**C-7: Dokumentinnhold som lagres**
Dokumentet, dokumentteksten og kildeutdragene lagres ikke permanent (FR-16, FR-29). Godkjente merknader kan inneholde informasjon fra dokumentet og lagres permanent sammen med aktiviteten. Det er akseptabelt fordi bare fiktive data brukes (C-1).

**C-8: Språk i brukergrensesnittet**
Brukergrensesnittet er på norsk bokmål. Tekst og utforming avgjøres i UX-workflowen.

## 6. Non-Functional Requirements

**Pålitelighet og stabilitet**

**NFR-1: Konsistent lagring**
En lagring fullføres helt eller ikke i det hele tatt. Planen skal aldri bli stående med en halvveis lagret aktivitet. Mislykkes en lagring, får brukeren beskjed, og applikasjonen viser ikke at lagringen var vellykket.
- *Begrunnelse:* Planen er det eneste som lagres permanent (C-7), og brukeren må kunne stole på den.
- *Etterprøving:* Ved en simulert lagringsfeil er planen uendret, og brukeren får en feilmelding.

**NFR-2: Robusthet ved feil**
Feil ved lesing av dokument, analyse eller lagring får ikke applikasjonen til å krasje, og de påvirker ikke lagrede aktiviteter. Brukeren kan fortsette å bruke applikasjonen etter feilen. Dokumenter som er for store til å behandles, avvises med en tydelig melding. Grensen fastsettes i arkitekturen.
- *Etterprøving:* Testene omfatter et skadet dokument, et svært stort dokument og et ugyldig svar fra språkmodellen. Etter hver test er planen uendret, og applikasjonen kan brukes videre.

**NFR-3: Analysen henger ikke**
En analyse som ikke gir svar, avsluttes etter en tidsgrense og behandles som en feilet analyse (FR-20). Tidsgrensen fastsettes i arkitekturen.
- *Begrunnelse:* Svartiden avhenger av en ekstern tjeneste som gruppen ikke kontrollerer.

**Brukervennlighet**

**NFR-4: Forståelige meldinger**
Feilmeldinger og valideringsmeldinger forteller hva som er galt og hva brukeren kan gjøre. Tekniske feilkoder vises ikke som eneste informasjon.
- *Etterprøving:* Gjennomgang av alle feilmeldingene i FR-2, FR-15, FR-18, FR-19 og FR-20.

**NFR-5: Synlig fremdrift under analyse**
Mens analysen pågår, ser brukeren at den er i gang.
- *Begrunnelse:* Analysen kan ta merkbar tid, og uten tilbakemelding kan applikasjonen se ut som om den har stoppet.

**Ytelse**

**NFR-6: Responsiv navigasjon**
Bytte av kalenderår, zoom mellom årsvisning og månedsvisning, navigasjon mellom måneder og åpning av en aktivitet skal oppleves som raskt og responsivt. Foreløpig ytelsesmål er under 1 sekund. Endelige ytelseskriterier og testmengder fastsettes i testplanen.
- *Begrunnelse:* Ved 1 sekund går en vanlig grense for når brukeren mister flyten i arbeidet (Nielsens responstidsgrenser). Det er viktig når årshjulet vises i et møte (UJ-3).

**Tilgjengelighet**

**NFR-7: Grunnleggende tilgjengelighet**
Kjerneflyten oppfyller disse kravene:
- Kjerneflyten kan gjennomføres med tastatur.
- Fokus er synlig.
- Tekst har tilstrekkelig kontrast, målt etter WCAG 2.1 kriterium 1.4.3 (Kontrast, minimum).
- Skjemafelt har tydelige etiketter.
- Feil beskrives i tekst.

Relevante WCAG-prinsipper brukes som veiledning, men full samsvar med WCAG 2.1 AA kreves ikke i v1. Hvordan kravene løses for det sirkulære årshjulet, avgjøres i UX-workflowen.
- *Etterprøving:* Kjerneflyten gjennomføres manuelt med bare tastatur, og hvert av kravene kontrolleres. Tekstkontrast måles mot kriterium 1.4.3.

**Kompatibilitet**

**NFR-8: Skjerm og nettleser**
Applikasjonen er tilpasset bruk på PC og kan vises på storskjerm eller projektor i planleggingsmøter. Særskilt mobiltilpasning kreves ikke i v1. Nettleserne som støttes, dokumenteres i README når teknologivalgene er gjort.

**Sikkerhet**

**NFR-9: Ubetrodd innhold**
Tekst fra opplastede dokumenter og svar fra språkmodellen behandles som ubetrodd innhold.
- **Håndtering og visning:** Kildeutdrag, merknader, feltverdier og annet slikt innhold vises som ren tekst. Det kjøres aldri som kode, og applikasjonen tolker det aldri som instruksjoner til seg selv.
- **Prompt injection mot språkmodellen:** Et dokument kan inneholde tekst som forsøker å påvirke språkmodellens svar. Denne risikoen kan ikke fjernes helt. Konsekvensene begrenses fordi svarene bare blir aktivitetsforslag:
  - forslagene valideres (FR-2)
  - applikasjonen verifiserer kildeutdragene selv (FR-28)
  - ingen aktivitet legges inn uten eksplisitt godkjenning (FR-25)
- *Etterprøving:* Et testdokument med HTML- eller skriptkode og med instruksjoner rettet til språkmodellen gir ingen kjørt kode. Innholdet vises som tekst, og ingen aktivitet legges inn uten godkjenning.

**Testbarhet**

**NFR-10: Automatiske tester for sentrale regler**
Sentrale, deterministiske regler dekkes av automatiske tester som kan kjøres uten API-nøkkel:
- validering og datoregel (FR-2)
- ISO-ukenummer og årsskifte (FR-10)
- visning av flerdagsaktiviteter i flere perioder (FR-11)
- verifisering av kildeutdrag (FR-28)
- demo-modus mot fasit (FR-18, FR-30)

## 7. Non-Goals

**Grunnleggende produktprinsipp** *(gjelder også utover v1)*
- **Menneskelig kontroll:** KI kan ikke opprette, endre eller slette aktiviteter i planen uten brukerens eksplisitte godkjenning (FR-25). Prinsippet gjelder selvstendige handlinger fra KI. Det utelukker ikke at KI senere kan gi analyse, prioritering eller beslutningsstøtte.

**Utenfor v1, men del av produktvisjonen** *(Product Brief §9)*
- Felles planbilde med flere brukere.
- Ukevisning og dagsvisning, inkludert aktiviteter fordelt på mandag–søndag.

**Utenfor v1**
- *Integrasjoner:* direkte integrasjon med eksterne applikasjoner, inkludert automatisk innhenting og synkronisering.
- *Årshjul og tilpasning:*
  - flere konsentriske ringer
  - omfattende tilpasning av format, layout, farger og planleggingsstrukturer, inkludert brukertilpasning av kategorifarger (FR-12)
  - mobiltilpasning (NFR-8)
- *Dokumenter og analyse:*
  - OCR og analyse av skannede dokumenter eller bilder (FR-15)
  - samtidig analyse av flere dokumenter (FR-15)
  - full dokumentvisning med navigasjon og markering (§4.5)
- *Avanserte KI-funksjoner:* KI-basert prioritering, prediksjon, konfliktanalyse (inkludert duplikat- og overlappkontroll, §4.4), optimalisering og beslutningsstøtte.
- *Aktivitetshåndtering:*
  - angrefunksjon (FR-5)
  - «godkjenn alle» (FR-23)
  - separat oppgavestyring med oppgavestatus, fremdriftsoppfølging og fullføring av oppgaver

*Avgrensningene under «Utenfor v1» er ikke planlagte fremtidige funksjoner.*

## 8. MVP Scope

*Første versjon er en komplett, lokalt kjørbar enkeltbrukerløsning der brukeren kan holde planen oppdatert både manuelt og ved hjelp av KI, og bruke årshjulet til oversikt i planleggingsmøter. Detaljerte krav står i §4–§6. Avgrensninger står i §7.*

### 8.1 In Scope

| Arbeidsflyt | Innhold i v1 | Krav |
|---|---|---|
| **Oversikt i årshjulet** | Sirkulær årsvisning med 12 måneder og valg av kalenderår. Månedsvisning med ISO-uker og direkte navigasjon mellom måneder. Fast visuell identitet per kategori. Åpning av aktiviteter fra begge visningene. | §4.2, FR-3 |
| **Manuell aktivitetshåndtering** | Opprette, åpne, redigere og slette aktiviteter med merknader. Felles validering og varig lokal lagring. | §4.1 |
| **KI-assistert dokumentanalyse** | Opplasting av ett dokument om gangen (.docx eller tekstbasert PDF). Aktivitetsforslag med feltstatus, demo-modus og tydelig feilhåndtering. | §4.3 |
| **Kontroll og godkjenning** | Individuell gjennomgang i valgfri rekkefølge, med kildeutdrag som applikasjonen verifiserer. Eksplisitt godkjenning eller avvisning av hvert forslag. Ubehandlede forslag beholdes i økten. | §4.4, §4.5 |
| **Rammer for kjøring og kvalitet** | Lokal kjøring etter README, fiktive testdata, én ekstern språkmodell og hemmeligheter utenfor Git. Norsk grensesnitt, bruk på PC og projektor, grunnleggende tilgjengelighet og automatiske tester av sentrale regler. | §5, §6 |

### 8.2 Presiseringer og endringer fra Product Brief

1. **Kildeutdrag:** Hvert aktivitetsforslag kan ha ett eller flere kildeutdrag som applikasjonen verifiserer. De er tilgjengelige under gjennomgangen, men lagres ikke permanent (§4.5, FR-16, FR-29).
2. **Visuell identitet per kategori:** Hver kategori har en fast visuell identitet som ikke er avhengig av farge alene (FR-12).
3. **Merknader:** Valgfritt fritekstfelt på alle aktiviteter (FR-6).
4. **Sluttdato:** Sluttdato er obligatorisk for alle aktiviteter, ikke bare for flerdagsaktiviteter (FR-2).
5. **Månedsnavigasjon:** Brukeren kan navigere direkte mellom måneder i månedsvisningen (FR-10).

### 8.3 Out of Scope

Se §7 Non-Goals.

## 9. Success Metrics

*§9.1 avgjør om MVP-en fungerer. §9.2 og §9.3 måler kvalitet og nytteverdi. Testprosedyrer, antall deltakere og antall kjøringer fastsettes i testplanen.*

### 9.1 MVP-kriterier

**SM-1: Hele arbeidsflyten uten veiledning**
I en brukertest med fiktive testdokumenter skal deltakerne gjennomføre de sentrale arbeidsflytene i UJ-1, UJ-2 og UJ-3 uten veiledning. Minst én deltaker har ikke vært med på utviklingen. Erfaring med planlegging er en fordel, men ikke et krav.
- *Oppfylt når:* deltakerne fullfører arbeidsflytene uten veiledning. Steder der en deltaker stoppet opp, dokumenteres.
- *Kilde:* Product Brief, Behavior.

**SM-2: Sentrale krav er testet**
De sentrale funksjonelle og ikke-funksjonelle kravene er testet ut fra de testbare konsekvensene i §4 og etterprøvingspunktene i §5 og §6. Testplanen angir hvilke krav som inngår.
- *Oppfylt når:* ingen av disse testene feiler, og resultatene er dokumentert.

### 9.2 KI-kvalitet

**SM-3: KI-uttrekk vurdert mot fasit**
Analysen med språkmodellen kjøres på 3–4 fiktive testdokumenter med forhåndsdefinert fasit. Hvert dokument analyseres flere ganger for å vise variasjon mellom kjøringene. For hvert dokument dokumenteres:
- hvor mange relevante aktiviteter som ble identifisert
- hvor mange feilaktige forslag som ble generert
- hvor korrekt startdato og sluttdato ble identifisert
- hvordan manglende eller usikker informasjon ble markert

Resultatene vurderes mot fasiten. Vurderingen beskriver feil, begrensninger og konsekvenser for brukerens kontrollarbeid. Det settes ingen prosentgrense. Demo-modus testes separat (NFR-10).
- *Kilde:* Product Brief, Quality.

### 9.3 Nytteverdi

**SM-4: Sammenligning med Excel**
Samme planleggingsoppgave gjennomføres manuelt i Excel og i applikasjonen. For hver metode registreres tiden fra start til ferdig plan og antall feil sammenlignet med fasit. Testplanen beskriver hvordan sammenligningen gjennomføres, og hvilke feilkilder som kan påvirke resultatet, for eksempel læringseffekt.
- *Kilde:* Product Brief, Business / mission.

**Counter-metrics**
- **Riktighet:** Er applikasjonen raskere, men gir flere feil mot fasit enn Excel (SM-4), er det ingen gevinst.
- **Kontrollarbeid:** Må brukeren rette mange felt per aktivitetsforslag (SM-3), kan det spise opp tiden KI sparer.

*Resultatene i §9.2 og §9.3 er veiledende. Med få deltakere og testdokumenter gir de ikke statistisk sikre konklusjoner.*

## 10. Open Questions

### 10.1 Avklares ved ferdigstillelse av PRD-en *(eier: gruppen)*

| ID | Spørsmål |
|---|---|
| OQ-1 | **Avklart 2026-10-22:** Product Brief er oppdatert slik at den samsvarer med PRD-en på capability-nivå og ikke motsier den. Detaljene i §8.2 er dokumentert i PRD-en og gjentas ikke i briefen. |

### 10.2 Åpent, blokkerer ikke implementering *(eier: gruppen)*

| ID | Spørsmål |
|---|---|
| OQ-2 | Endelig produktnavn. Arbeidstittelen brukes inntil videre. |

### 10.3 Avklares i UX-workflowen

| ID | Spørsmål | Krav |
|---|---|---|
| OQ-3 | **Prioritert:** innholdet i kategorilisten. Må avklares før implementering av aktivitetshåndtering, analyse og demo-modus. | FR-1, FR-12, FR-17, FR-18 |
| OQ-4 | Hvordan årsvisningen forblir lesbar når mange aktiviteter ligger i samme måned. | FR-13 |
| OQ-5 | Visuell utforming av årshjulet og gjennomgangen. Det omfatter kategoriidentitet, tastaturbruk i hjulet, månedsnavigasjon, plassering av kildeutdrag, markering av demo-modus og bekreftelser. | FR-8, FR-10, FR-12, FR-18, FR-26, FR-27, NFR-7 |

### 10.4 Avklares i arkitekturen

| ID | Spørsmål | Krav |
|---|---|---|
| OQ-6 | Valg av språkmodell og leverandør, med begrunnelse. | C-2 |
| OQ-7 | Hvordan demo-modus aktiveres, og hvordan støttede testdokumenter gjenkjennes. | FR-18 |
| OQ-8 | Lagringsløsning, tidsgrense for analyse, maksimal dokumentstørrelse og hvilke nettlesere som støttes. | FR-7, NFR-2, NFR-3, NFR-8 |

### 10.5 Avklares i testplanen

| ID | Spørsmål | Krav |
|---|---|---|
| OQ-9 | Testdokumenter med fasit, og hvilke sentrale krav som testes. | SM-2, SM-3, FR-30 |
| OQ-10 | Antall deltakere, antall KI-kjøringer per dokument, oppsett av Excel-sammenligningen, testmengder og ytelseskriterier. | SM-1, SM-3, SM-4, FR-13, NFR-6 |

## 11. Assumptions Index

### 11.1 Forutsetninger PRD-en bygger på

| ID | Forutsetning | Grunnlag | Konsekvens hvis den ikke holder |
|---|---|---|---|
| P-1 | Troppssjefer bruker vesentlig tid på å hente aktiviteter fra spredte dokumenter og Excel-ark. | Product Brief, problembeskrivelse, basert på gruppens egen erfaring. Ikke undersøkt med brukere. | Nytteverdien blir mindre. SM-4 gir et første signal. |
| P-2 | Aktiviteter og datoer i ordre står i dokumenttekst som kan hentes ut fra .docx eller tekstbasert PDF. | Product Brief, Scope IN 3–4. | Analysen gir færre forslag, og brukeren må registrere mer manuelt (FR-1). |
| P-3 | Fiktive testdokumenter gir grunnlag for å vurdere løsningen i et kontrollert testmiljø. | C-1, SM-3. | Resultatene kan ikke uten videre generaliseres til faktiske militære ordre. Dette beskrives som en begrensning. |
| P-4 | En ekstern språkmodell er tilgjengelig via API under utvikling og testing. | C-2. | Demo-modus sikrer at kjerneflyten kan demonstreres (FR-18), men SM-3 kan ikke gjennomføres. |
| P-5 | Brukeren kontrollerer forslagene før godkjenning. | FR-25, §7 Menneskelig kontroll. | Feil fra KI kan komme inn i planen. Kildeutdrag (§4.5) og feltstatus (FR-17) skal gjøre kontrollen enklere. |

### 11.2 Status for nummererte antakelser

*Ingen `[ASSUMPTION]`-markeringer står åpne i PRD-en. Den fullstendige historikken står i `.memlog.md`.*

- **Godkjent og innarbeidet:**
  - §4–§5: A1–A3, A5, A6, A8, A10, A12, A14–A17, A19–A27
  - §6: A28–A31
  - §9: A32
- **Revidert:**
  - A4: Kategori har bare status *manglende* eller *usikker*. Status *ugyldig* brukes ikke for kategori (FR-17).
  - A11: Den opprinnelige antakelsen om en minstelengde er revidert. Gjeldende: romslig øvre tegngrense som fastsettes i arkitekturen (FR-6).
  - A13: FR-13.
  - A33: SM-4.
- **Erstattet:** A9 er erstattet av A18 (FR-17).
- **Forkastet:** A7. Den opprinnelige antakelsen om at éndagsaktiviteter ikke har sluttdato, er forkastet. Gjeldende: sluttdato er obligatorisk for alle aktiviteter, også éndagsaktiviteter (FR-2).
- **Ikke dokumentert:** ingen. A2 og A3 er avklart gjennom transkripsjonen fra forrige økt.
