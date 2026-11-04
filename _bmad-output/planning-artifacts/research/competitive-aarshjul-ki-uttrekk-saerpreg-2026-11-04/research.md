---
title: 'Competitive research: Særpreg for KI-assistert interaktivt årshjul'
type: 'competitive'
topic: 'Særpreg: KI-assistert interaktivt årshjul mot eksisterende løsninger'
decision: 'Er særpreget i Product Brief §4 / PRD §1 tilstrekkelig underbygget mot faktisk MVP, eller må det snevres inn?'
source: 'native run (web search)'
status: complete
preset: 'standard'
validation: 'high'
red_team: 'on'
claims_verified: 10
claims_unverified: 17
created: '2026-11-04'
updated: '2026-11-04'
---

# Competitive research: Særpreg for KI-assistert interaktivt årshjul

**Beslutningen undersøkelsen skal støtte:** Er særpreget i Product Brief §4 / PRD §1 tilstrekkelig underbygget mot faktisk MVP, eller må det snevres inn?

## 1. Sammendrag

**Svar:** Påstanden om særpreg **holder bare delvis og bør snevres inn**. Vi fant ingen enkeltløsning som dokumenterer hele v1-flyten. De tre elementene briefen nevner, finnes likevel allerede hver for seg: interaktivt årshjul, KI-assistert aktivitetsgenerering og brukergodkjenning. Leverandørene har dessuten begynt å kombinere dem:

- **Plandisc** har sirkulært årshjul og markedsfører KI-import fra Word og PDF. Importen er bare beskrevet på markedssiden [1][2][3].
- **Microsoft Planner Agent** lager ifølge Microsoft planutkast fra Word-filer. Utkastet godkjennes før lagring [11][12][13][53].
- **Clio** lager utkast til kalenderhendelser fra dokumenter, viser kildeteksten og lagrer ingenting før brukeren bekrefter. Dette bygger bare på søkeutdrag [41].

Det vi **ikke fant** i noe planleggingsprodukt, er denne kombinasjonen: kildeutdrag som applikasjonen selv verifiserer ordrett mot dokumentet, feltstatus (manglende/usikker/ugyldig, der kategori bare kan være manglende eller usikker), tvungen avgjørelse per forslag uten «godkjenn alle», og at dette leder direkte inn i et årshjul. At vi ikke fant noe, betyr ikke at løsningen er unik. Byggeklossene finnes ferdige [45][46][47], så forskjellen er et designvalg og ikke en teknologi som er vanskelig å kopiere.

**Anbefaling:** Formuler særpreget som *sporbar kontroll av hvert KI-forslag mot verifiserte kildeutdrag før det legges inn i årshjulet*. Nevn Plandisc og Planner Agent som de nærmeste alternativene. Kostnad og tilgjengelighet og militær tilpasning gir støtte til denne formuleringen, men er ikke særpreg i seg selv (avsnitt 6). Om formuleringen skal endres, er en gruppebeslutning. Ingen dokumenter er endret.

## 2. Formål, metode og kildekritikk

- **Målestokk:** v1 slik den er spesifisert i Product Brief og PRD, ikke visjonen. Prosjektdokumentene er brukt til å formulere spørsmålene og som målestokk, ikke som bevis om konkurrentene. Vår løsning er *spesifisert*, men ikke bygget eller testet. Sammenligningen gjelder derfor krav mot dokumenterte produkter, ikke kvaliteten på to ferdige produkter.
- **Gjennomføring (2026-11-04):**
  - To runder med nettsøk i tre spor: årshjul, Microsoft 365, og KI-uttrekk med menneskelig kontroll.
  - Hver av de tre hovedkonklusjonene (K1–K3) ble prøvd av en separat KI-agent som skeptiker. Agenten fikk konklusjonen, men ikke bevisene som støttet den.
  - Til slutt kontrollerte en egen agent at kildene sier det rapporten hevder. Den fant 11 avvik, og ordlyden er rettet der.
  - Ingen produkter er prøvd i praksis.
- **Kildekritikk:** Hver påstand er merket med bevistype.

  | Merke | Betydning |
  |---|---|
  | *dokumentert* | Offisiell dokumentasjon eller utgivelsesnotater |
  | *påstand* | Bare leverandørens markedsføring |
  | *uavhengig* | En annen utgiver enn leverandøren. Samme leverandør to steder gjelder som én kilde. |
  | *søkeutdrag* | Bare utdraget i søkeresultatet er lest, fordi siden avviste verktøyet |
  | *antakelse* | Vår egen slutning |
  | *ikke funnet* | Vi lette uten å finne noe. Det er ikke bevis for at funksjonen ikke finnes. |

- **Påstandsregisteret** står i `.memlog.md`: 10 påstander er verifisert og 17 er uverifisert. Notatene fra hver søkerunde og hver skeptiker ligger i `digests/`. Kildenumrene er beholdt fra arbeidsversjonen, slik at de kan spores dit. Derfor er nummereringen ikke fortløpende.

## 3. De viktigste alternativene

### Plandisc: årshjul med markedsført KI-import

- **Årshjul:** sirkulært årshjul med ringer, aktivitetsgrupper, frist, ansvarlig og måneds- og ukevisning. Dette er en påstand som manualen delvis bekrefter [1][3]. Integrerer med Outlook, Teams og Planner, og oppgir at Planner-oppgaver kan vises i hjulet (påstand) [10].
- **«AI Import»:** Markedssiden sier at en opplastet Excel-, Word- eller PDF-fil blir til «a complete plandisc» som et utkast brukeren bearbeider. Den nevner ikke kildeutdrag, godkjenning per forslag eller markering av usikre felt (påstand) [2]. Brukermanualen fra oktober 2026 beskriver bare Excel-import via mal og en KI som lager *struktur*, ikke aktiviteter (dokumentert) [3]. Vi fant ingen uavhengig omtale. **Faktisk virkemåte: ukjent, konfidens lav.**
- **Andre årshjul:** PlanIt (Teams) og Orbit (Sverige) har også sirkulært årshjul. Orbit bruker KI til å finne flaskehalser, ikke til uttrekk fra dokumenter (påstand og søkeutdrag) [7][8].

### Microsoft 365 Planner Agent: KI-utkast fra fil med bekreftelse

- **Fra fil til utkast:** «Generate plans from Word, Excel, or PowerPoint files». Foreslått arbeid vises i kort som brukeren går gjennom og godkjenner før noe opprettes (dokumentert av Microsoft) [11]. GA ble kunngjort 15.06.2026, og utrullingen skjedde i juni 2026. Alt KI-generert opprettes som utkast, og funksjonen krever Copilot-lisens for hver bruker [12][53][58].
- **Godkjenningsmodell:** For oppgaveforslag kan brukeren redigere eller fjerne enkeltelementer før settet bekreftes. Planer godkjennes samlet [13][53]. Kontroll per element er altså innebygd, men det er ingen tvungen avgjørelse per forslag.
- **Uavhengig kontroll:** én praktisk test hos en tredjepart. Testen gjaldt en oppgave laget fra en prompt, ikke fra en fil [15]. **Den filbaserte flyten er bare dokumentert av Microsoft.**
- **Ikke funnet:** PDF som kilde, uttrekk av start- og sluttdato eller ansvarlig fra dokumentet, kildehenvisning per oppgave, feltstatus og en sirkulær visning eller årsvisning [11][17]. Copilot i Word og Copilot Notebooks gir kildehenvisninger, men de følger ikke med inn i Planner [54][55].
- **Tilgang for målgruppen:** Det er udokumentert om troppssjefer har Copilot. Et stortingsspørsmål fra juni 2026 viser til et statlig «KI-pålegg» om Copilot, men innholdet er ikke verifisert [56]. Forsvarets Microsoft-sky gjaldt etter siste kilde bare ugradert informasjon. Den kilden er fra 2019 [22].

### Clio Manage AI: det sterkeste motbeviset

- **Flyten:** Kalender → «Extract from a document» lager utkast til hendelser fra ett dokument. Hvert utkast viser «the text it was pulled from», og ingenting lagres før brukeren bekrefter. Bekreftede hendelser lastes opp samlet [41].
- **Kildekritikk:** Clios hjelpeside avviste verktøyet, så bare søkeutdrag er lest (konfidens middels). Det er uklart om bekreftelsen skjer per hendelse. Det er heller ikke dokumentert at kildeteksten verifiseres maskinelt, eller at felt markeres med status. Clio bruker en juridisk kalender, ikke et årshjul.
- **Lignende verktøy:** Juridiske fristverktøy som Mitratech ARIES har en tilsvarende «review and confirm before anything is created» (påstand) [43].

### Øvrige mønstre

Bekreftelse før lagring finnes også i Atlassian Rovo, der forslag kan fjernes og resten opprettes samlet [28], og i Ironclad, der «Verify» godtar alt som ikke er avvist [30]. Kildekobling per verdi finnes i dokumentbehandling (IDP), for eksempel Rossum [29], og som byggeklosser i LangExtract [45][59], Claude Citations [46] og Azure Content Understanding [47].

## 4. Sammenligning mot vår MVP

Kolonnen «Vår MVP» viser hva som er spesifisert i PRD-en, ikke hva som er bygget eller testet.

| Ledd i v1-flyten | Vår MVP (spesifisert) | Plandisc | Planner Agent (+ Plandisc) | Clio |
|---|---|---|---|---|
| 1. Opplasting av .docx / tekstbasert PDF | ja (FR-15) | Word/PDF (påstand) [2] | Word/Excel/PPT (dokumentert); PDF ikke funnet [11] | dokument (søkeutdrag) [41] |
| 2. KI-forslag med dato og ansvarlig | ja (FR-17) | «draft» (påstand) [2] | utkast (dokumentert); datouttrekk ikke funnet [11] | datoer og hendelser (søkeutdrag) [41] |
| 2b. Feltstatus manglende/usikker/ugyldig (kategori bare manglende/usikker) | ja (FR-17, FR-21) | ikke funnet | ikke funnet | ikke funnet |
| 3. Ordrett kildeutdrag, verifisert av applikasjonen | ja (FR-27–FR-28) | ikke funnet | ikke funnet; henvisninger bare i Word/Notebooks [54][55] | kildetekst vises; verifisering ikke funnet [41] |
| 4. Avgjørelse per forslag, uten «godkjenn alle» | ja (FR-23, FR-26) | ikke funnet; helt utkast redigeres [2] | redigere/fjerne og samlet bekreftelse [13][53] | bekreftelse før lagring; per hendelse uklart [41] |
| 5. Sirkulært årshjul med månedsvisning | ja (FR-8, FR-10) | ja (delvis dokumentert) [1][3] | nei i Planner [17]; via Plandisc (påstand) [10] | nei |
| Kjøring uten betalt KI | demo-modus for testdokumenter (FR-18) | betalt abonnement (påstand) [1] | Copilot-lisens per bruker [58] | utvalgte planer (søkeutdrag) [41] |
| **Samlet flyt 1–5** | spesifisert | delvis (1, 2, 5 på påstandsnivå) | delvis (1, 2, 4, 5 via integrasjon) | delvis (1, 2, 3–4 delvis) |

## 5. Hva som reelt skiller løsningen

- **Ikke særegent:** årshjulet, KI-uttrekk fra dokumenter og det at brukeren bekrefter før lagring. Alle tre finnes hos minst én etablert aktør (avsnitt 3).
- **Ikke funnet hos andre (forsvarbart, men ikke bevist unikt):**
  1. at applikasjonen selv kontrollerer at hvert kildeutdrag står ordrett i dokumentet, og viser tydelig når det ikke gjør det
  2. feltstatus per forslag
  3. at hvert forslag må avgjøres enkeltvis uten «godkjenn alle»
  4. at alt dette leder rett inn i årshjulet, uten integrasjon mellom flere produkter
- **Forbehold:**
  - Punkt 1–3 kan bygges med hyllevare [45][46][47] og kan kopieres.
  - Nytten av punkt 2 og 3 er omstridt (avsnitt 7).
  - Vår løsning er ikke testet. Det er derfor ikke dokumentert at den gir bedre kontroll enn alternativene. Det må vises i SM-3 og SM-4.

## 6. Supplerende faktorer

### Kostnad og tilgjengelighet

- **Spesifisert:**
  - Applikasjonen kjøres lokalt etter README, uten gruppens nøkler, betalte kontoer eller egen infrastruktur (C-5).
  - Demo-modus fungerer uten API-nøkkel og uten betalt KI. Den sender ingen data og gir de samme forslagene hver gang for støttede testdokumenter (FR-18).
- **Ordinær analyse er ikke gratis:**
  - Den bruker én ekstern språkmodell via API (C-2), krever API-nøkkel (C-4) og kan gi bruksbaserte kostnader. Modell og leverandør bestemmes i arkitekturen (OQ-6).
  - Dokumentteksten sendes til en ekstern tjeneste (C-3). Analysen er derfor lokal i drift, men ikke frakoblet.
  - Demo-modus kan ikke analysere nye dokumenter.
- **Alternativene:**
  - Planner Agent krever Copilot-lisens per bruker [58].
  - Plandisc oppgir abonnementspris per bruker, men ikke hvilket nivå KI inngår i (påstand) [1].
  - Clios KI finnes på utvalgte planer (søkeutdrag) [41].
  - Vi har ikke sammenlignet totalkostnader.
- **Vurdering:** Faktoren har **reell verdi for demonstrasjon og evaluering**. Sensor, testdeltakere og andre kan kjøre hele kjerneflyten uten kostnad, og demo-modus gjør resultatene etterprøvbare mot fasit. Den er **ikke et markedsfortrinn**. Ordinær bruk har API-kostnad, og sending av ekte dokumenter til en ekstern modell er utelukket i v1 (C-1). Den samme begrensningen for graderte dokumenter rammer M365 (antakelse).

### Militær tilpasning

- **Spesifisert:**
  - troppssjefen som primærbruker (PRD §2)
  - ordre som utgangspunkt (UJ-1)
  - frister registrert som aktiviteter
  - feltet ansvarsområde
  - ISO-uker med norske ukenummer (FR-10)
  - regler for ufullstendige datoer og ukeangivelser: «uke 12» uten dag gjøres ikke om til en dato, men markeres som manglende (FR-17, UJ-1 E6a)
  - norsk grensesnitt (C-8)
- **Bare mulig, ikke bestemt:**
  - en kategoriliste med militære aktivitetstyper (OQ-3, avgjøres i UX)
  - militær terminologi i grensesnittet utover norsk språk
  - andre lederroller
- **Må dokumenteres gjennom testing:**
  - om KI tolker ordreformater og datoangivelser riktig (SM-3). Med fiktive dokumenter kan resultatet ikke uten videre overføres til ekte ordre (P-3).
  - om troppssjefer sparer tid sammenlignet med Excel (SM-4)
- **Alternativene:** Vi fant ingen konkurrent som retter seg mot Forsvaret. Det er ikke bevis for at det ikke finnes noen. Kategorier og ringer finnes allerede i generelle årshjul [1].
- **Vurdering:** Den militære tilpasningen er **relevant for posisjoneringen, men et tynt særpreg alene**. Det mest konkrete er de spesifiserte reglene for tolkning av ordredatoer og ukeangivelser. Kategorier kan konkurrentene konfigurere selv. Verdien må vises i SM-3 og SM-4 før den kan brukes som argument.

## 7. Usikkerheter, motargumenter og konsekvenser

**Motargumenter fra skeptikerne.** Alle tre konkluderte med «må nyanseres», ingen med «faller».
- **K1: Hele flyten finnes allerede, spredt på flere aktører.**
  - Clio dekker uttrekk, kildetekst og bekreftelse [41].
  - Plandisc dekker dokument → årshjul (påstand) [2].
  - LangExtract kobler uttrekk til eksakte tegnposisjoner [45].

  *Konsekvens:* Påstander som «ingen viser kildeutdrag» eller «ingen tar dokumenter inn i et årshjul med KI» ville vært feil.
- **K2: Det snevre særpreget er standardoppsett, ikke fortrinn.**
  - Ordrette kildehenvisninger med gyldige pekere er en ferdig API-funksjon [46].
  - Kildekobling, konfidens per felt og menneskelig kontroll leveres samlet i Azure Content Understanding [47].
  - Microsofts retningslinjer for samspill mellom menneske og KI anbefaler effektiv avvisning og korrigering, med masseredigering som eksempelmønster [52].
  - Forskningen gir grunn til forsiktighet:
    - Sitater øker tilliten selv når de er tilfeldige [48].
    - Språkmodeller er overkonfidente når de oppgir egen usikkerhet [49].
    - I et randomisert eksperiment økte et ekstra obligatorisk korrigeringssteg andelen godtatte feil [50]. At det samme gjelder avgjørelse per forslag, er vår slutning.
  - *Motvekt:* Kildepassasjer ga et godt kompromiss mellom tid og nøyaktighet (preprint) [39]. Forklaringer reduserer overavhengighet når de gjør verifiseringen billigere [51].
- **K3: M365 er godt nok.** Planner Agent har innebygd gjennomgang [13][53], og nabofunksjoner har kildehenvisninger [54][55]. *Konsekvens:* Det som mangler i M365, er sammenhengen. Kildene følger ikke med inn i oppgavene, og det finnes verken feltstatus eller et innebygd årshjul. Det avgjørende er om målgruppen har tilgang [56].

**Største usikkerheter:**
- Plandisc AI Import, Clio og den filbaserte flyten i Planner Agent bygger på leverandørenes egne opplysninger eller på søkeutdrag.
- Ingen produkter er prøvd.
- Copilot-tilgang i Forsvaret er udokumentert.
- Feltene endrer seg raskt (avsnitt 10).

**Konsekvenser for prosjektet.** Dette er innspill til senere gruppebeslutninger, ikke endringer.
1. **Product Brief §4 / PRD §1:** Snevre inn påstanden om særpreg som i avsnitt 1. Nevn Plandisc og Planner Agent som de nærmeste alternativene. Det svarer også på tilbakemeldingen på Product Brief om at vanlige planleggingsverktøy ikke var nevnt. *Konfidens middels.*
2. **Testplan (OQ-9, OQ-10):** Mål om kontrollen virker, ikke bare om den finnes:
   - om brukerne oppdager bevisst innlagte feil
   - andelen verifiserte kildeutdrag
   - om «usikker» treffer de faktiske feilene

   Dette samsvarer med valideringsfunn M14 [49][50].
3. **Tolkning av FR-17:** «Usikker» bygger på språkmodellens egen angivelse og bør behandles som et signal, ikke som kalibrert sikkerhet [49].
4. **Demo-modus:** Beskriv den som etterprøvbarhet og kostnadsfri demonstrasjon, ikke som at løsningen er gratis i bruk.

## 8. Åpne spørsmål

| Spørsmål | Hva som skal til |
|---|---|
| Hvordan fungerer Plandisc AI Import i praksis: forslag enkeltvis, kilder, feltstatus? | Prøvekonto og fiktivt dokument |
| Kan Planner Agent bruke PDF, og kan forslag i et planutkast avvises enkeltvis? | Test i et Microsoft 365-miljø med Copilot-lisens |
| Bekrefter Clio hendelser enkeltvis, og verifiseres kildeteksten? | Les hjelpesiden i nettleser |
| Har troppssjefer Copilot, og hva sier det statlige KI-pålegget? | Kilder fra Forsvaret, FMA eller Digdir |

## 9. Kilder

*Utvalgte kilder. Numrene er beholdt fra arbeidsversjonen, slik at de kan spores i `.memlog.md` og `digests/`. Alle er hentet eller søkt opp 2026-11-04. Kolonnen «Grunnlag» viser om hele siden er lest.*

| [n] | Støtter | Utgiver | Publisert | Grunnlag | Konfidens |
|---|---|---|---|---|---|
| [1] | Plandisc: sirkulært årshjul, funksjoner, pris per bruker | [Plandisc ApS](https://plandisc.com/en/) | udatert (© 2026) | lest | middels |
| [2] | Plandisc «AI Import»: Word/PDF → utkast; ingen kilder eller godkjenning nevnt | [Plandisc ApS](https://plandisc.com/en/ai-circular-planner) | udatert (© 2026) | lest | lav (virkemåte) |
| [3] | Plandisc-manual: Excel-mal og KI-struktur; ingen KI-import fra dokument | [Plandisc ApS](https://plandisc.com/hubfs/User%20manuals/ENG%20-%20User%20manual.pptx.pdf?hsLang=en) | 2026-10-22 (ifølge kunnskapsbasen) | lest | middels–høy |
| [7] | PlanIt: årshjul i Teams/SharePoint; ingen KI funnet | [Enable 365 / Microsoft Marketplace](https://marketplace.microsoft.com/en-us/product/web-apps/enableas1652357678356.planit_saas_no?tab=overview) | udatert | søkeutdrag | lav–middels |
| [8] | Orbit: årshjul, KI-flaskhalsanalyse, Excel-import | [Uanet](https://orbitbyuanet.se/) | mai–juli 2026 | lest | middels |
| [10] | Plandisc: integrasjon med Planner og Outlook; viser Planner-oppgaver | [Plandisc ApS](https://plandisc.com/en/microsoft-integrations/) | udatert | lest i sitatkontrollen | middels |
| [11] | Planner Agent: planer fra Word/Excel/PowerPoint; kort med gjennomgang | [Microsoft Support](https://support.microsoft.com/planner/what-can-you-do-with-planner-agent-in-copilot) | udatert (© 2026) | lest | høy |
| [12] | Planner Agent GA; utkast som standard; Copilot-lisens | [Microsoft Tech Community](https://techcommunity.microsoft.com/t5/planner-blog/planner-agent-in-microsoft-365-copilot-is-now-generally/ba-p/4527629) | 2026-06-15 | lest | høy |
| [13] | Redigere/fjerne per oppgave, så samlet bekreftelse; planer samlet | [Microsoft Tech Community](https://techcommunity.microsoft.com/t5/planner-blog/planner-agent-brings-work-management-directly-into-microsoft-365/ba-p/4511720) | 2026-04-20 | lest | høy |
| [15] | Praktisk test hos tredjepart: utkast fra prompt, datoer satt manuelt | [oneminuteofficemagic](https://oneminuteofficemagic.com/2026/07/01/using-the-planner-agent-in-copilot/) | 2026-07-01 | lest | middels |
| [17] | Planner-visninger; ingen sirkulær visning eller årsvisning | [Microsoft Support](https://support.microsoft.com/en-us/planner/compare-microsoft-planner-basic-vs-premium-plans) | udatert (© 2026) | lest | høy |
| [22] | Forsvaret: Microsoft-sky for ugradert informasjon | [Stortinget](https://www.stortinget.no/no/Saker-og-publikasjoner/Sporsmal/Skriftlige-sporsmal-og-svar/Skriftlig-sporsmal/?qnid=55219) | 2019-12-02 | lest | høy (2019), lav (i dag) |
| [28] | Rovo: forslag fjernes, resten opprettes samlet | [Atlassian Support](https://support.atlassian.com/confluence-cloud/docs/use-jira-and-confluence-together/) | udatert (© 2026) | lest | høy |
| [29] | Rossum: kildemarkering per verdi, statusfarger | [Rossum Knowledge Base](https://knowledge-base.rossum.ai/docs/interactive-bounding-boxes-in-rossum) | 2025-03-06 | lest | høy |
| [30] | Ironclad: «Verify» godtar alt som ikke er avvist | [Ironclad Support](https://support.ironcladapp.com/hc/en-us/articles/12277694694167) | udatert | søkeutdrag | middels |
| [39] | Kildepassasjer: godt kompromiss mellom tid og nøyaktighet (preprint) | [arXiv (Irons m.fl.)](https://arxiv.org/abs/2603.11393) | 2026-03-12 | sammendrag lest | middels |
| [41] | Clio: utkast fra dokument med kildetekst; bekreftelse før lagring | [Clio Help Center](https://help.clio.com/hc/articles/42019952139035) | udatert | søkeutdrag | middels |
| [43] | Mitratech ARIES: «review and confirm all tasks before anything is created» | [Mitratech](https://clc.mitratech.com/turn-scheduling-orders-into-action-with-aries-ai) | udatert (© 2026) | lest | middels |
| [45] | LangExtract: uttrekk koblet til eksakte tegnposisjoner | [Google Developers Blog](https://developers.googleblog.com/en/introducing-langextract-a-gemini-powered-information-extraction-library/) | 2025-07-30 | lest | høy |
| [46] | Claude Citations: sitater med garantert gyldige pekere | [Anthropic](https://platform.claude.com/docs/en/build-with-claude/citations) | udatert (2025) | lest i sitatkontrollen | høy |
| [47] | Azure Content Understanding: kildekobling, konfidens per felt, menneskelig kontroll | [Microsoft Foundry Blog](https://devblogs.microsoft.com/foundry/content-understanding-confidence-grounding-hitl/) | 2026-10-14 | lest | høy |
| [48] | Sitater øker tillit også når de er tilfeldige | [AAAI (Ding m.fl.)](https://ojs.aaai.org/index.php/AAAI/article/view/34550) | 2025 | søkeutdrag | høy (funn) |
| [49] | Språkmodeller er overkonfidente når de oppgir egen usikkerhet | [arXiv / ICLR 2024 (Xiong m.fl.)](https://arxiv.org/abs/2306.13063v2) | 2024-03 | søkeutdrag | høy |
| [50] | Automasjonsskjevhet; ekstra korrigeringssteg ga flere godtatte feil | [arXiv / HDSR (Beck m.fl.)](https://arxiv.org/abs/2509.08514) | 2025-09 (preprint) | sammendrag lest | høy (hovedfunn) |
| [51] | Forklaringer reduserer overavhengighet når verifisering blir billigere | [arXiv / CSCW 2023 (Vasconcelos m.fl.)](https://arxiv.org/abs/2212.06823) | 2023 | søkeutdrag | høy |
| [52] | HAX: effektiv avvisning og korrigering; masseredigering som eksempel | [Microsoft Research HAX Toolkit](https://www.microsoft.com/en-us/haxtoolkit/library/example,pattern/all/63/) | 2019 | søkeutdrag | middels |
| [53] | MC1323264: GA; kortene krever gjennomgang og bekreftelse | [Microsoft Message Center (speilet av merill.net)](https://mc.merill.net/message/MC1323264) | 2026-05-26 | lest | høy |
| [54] | Copilot i Word: henvisninger til steder i dokumentet | [Microsoft Support](https://support.microsoft.com/en-gb/word/copilot/chat-with-copilot-about-your-word-document) | udatert | lest | middels–høy |
| [55] | Copilot Notebooks: PDF og nummererte kildehenvisninger | [NC Bar Association](https://www.ncbar.org/2026/07/21/updates-to-microsoft-copilot-notebook/) | 2026-07-21 | sekundærkilde | middels |
| [56] | Stortingsspørsmål om statlig «KI-pålegg» om Copilot | [Altinget](https://www.altinget.no/statogstyring/statsradensvarer/22324) | 2026-06-25 | lest | lav (innhold) |
| [58] | Planner Agent: Copilot-lisens per bruker | [Microsoft Support](https://support.microsoft.com/en-au/office/access-planner-agent-86bf60a1-239d-4c37-b7b6-9a4111e1cc02) | udatert | lest | høy |
| [59] | LangExtract-port: status eksakt/uskarp/ikke funnet per utdrag | [hex.pm (lang_extract)](https://readme.hex.pm/lang_extract/0.9.0) | udatert (v0.9.0) | søkeutdrag | middels |

## 10. Ferskhet

Fristene for ny kontroll er beregnet med `recon_kit.py staleness`. Vinduene er 3 måneder for funksjoner, 6 for utviklingssignaler, 12 for posisjonering og 24 for forskning.

- **Allerede utdatert:**
  - Forsvarets skystatus [22], med frist 2020-12. Det er det svakeste punktet, og ingen nyere kilde er funnet.
  - Planner Agent-meldingene [12][53], med frist august–september 2026. De støttes av supportsiden lest 2026-11-04 [11].
- **Kontrolleres i desember 2026:** det statlige KI-pålegget [56] og Microsofts retning [12].
- **Kontrolleres senest i februar 2027:** funksjonspåstandene om Plandisc, Microsoft og Clio. Gjør det uansett før særpreget brukes i en endelig rapport.
