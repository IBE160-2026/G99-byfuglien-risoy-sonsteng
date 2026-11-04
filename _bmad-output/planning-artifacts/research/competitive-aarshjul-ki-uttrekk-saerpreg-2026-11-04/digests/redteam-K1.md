# Red team K1 — finnes hele arbeidsflyten allerede?

Kjørt 2026-11-04. Rundt 17 verktøykall og 6 kilder forsøkt lest direkte (2 Clio-sider ga 403/429, så Clio-funnene bygger på søkemotorens utdrag av Clios egne hjelpesider). Ingen konklusjoner bygger på treningsdata alene. Påstander uten evidens fra denne kjøringen er merket som **antakelse**.

Elementene som vurderes:
1. Word/PDF lastes opp, og KI foreslår daterte aktiviteter eller frister
2. Manglende eller usikre felt flagges
3. Hvert forslag vises med ordrette kildeutdrag, og programvaren verifiserer at utdraget faktisk finnes i dokumentteksten
4. Hvert forslag godkjennes eller avvises enkeltvis, uten «godkjenn alle»
5. Godkjente elementer vises i en interaktiv årsvisning, helst et sirkulært årshjul

## Motbevis (sterkest først)

| # | Produkt/prosjekt | Hva det gjør (med evidens) | Elementer dekket (1–5) | Bevistype | Levering | URL | Utgiver | Dato | Konfidens |
|---|---|---|---|---|---|---|---|---|---|
| 1 | **Clio Manage – Manage AI «Extract from a document»** | Kalender → New events → «Extract from a document». Henter datoer og hendelser fra ett dokument om gangen (opptil 20 sider eller 10 MB) og lager utkast. Ifølge søkeutdrag fra Clios hjelpeside viser hvert utkast «the text it was pulled from», og når man holder musepekeren over et utkast, ser man hvor datoen kom fra. Påminnelser kan justeres før bekreftelse, og ingenting lagres automatisk. «Manage AI will upload all confirmed events to your Clio Calendar simultaneously.» | 1 (ja, men filtyper er ikke bekreftet utover dokument/PDF). 3 delvis: kildetekst vises per hendelse, men det er ikke dokumentert at programvaren verifiserer at sitatet finnes. 4 delvis: det er uklart om man bekrefter per hendelse eller samlet, og opplastingen skjer i én batch. 2 ikke dokumentert. 5 nei: vanlig juridisk kalender, ikke årshjul. | leverandørpåstand (hjelpesiden ble ikke lest direkte på grunn av 403, bare via søkeutdrag) | native (på utvalgte planer) | https://help.clio.com/hc/articles/42019952139035 ; https://help.clio.com/hc/en-us/articles/29658207678107 | Clio | Udatert (hentet 2026-11) | Middels |
| 2 | **Plandisc AI Import** | «Your plans are probably already in an Excel file, a Word document, or a PDF. Upload the file, and the AI import feature will turn your plans into a complete plandisc.» Resultatet er et sirkulært årshjul. Siden sier ingenting om gjennomgang per forslag, kildeutdrag eller flagging. | 1 ja. 5 ja: sirkulært årshjul, native. 2, 3 og 4 ikke dokumentert. Sidens tekst («turn your plans into a complete plandisc») tyder på direkte import uten portvokter, men det er en **antakelse**. | leverandørpåstand (produktsiden er lest direkte) | native | https://plandisc.com/en/ai-circular-planner | Plandisc | © 2026, ingen dato for funksjonen | Høy for 1 og 5, lav for resten |
| 3 | **LawToolBox AI (Outlook / M365)** | Henter frister fra e-poster og vedlegg (PDF og bilde, også håndskrevne rettsordrer) og «presents those deadlines within Outlook to the user to review and, if the user chooses, edit them as needed and add them to the user's Outlook calendar». Krever Azure OpenAI i tenanten og basisproduktet. | 1 ja (vedlegg). 4 delvis: brukeren gjennomgår før frister legges til, men det er uklart om det skjer per frist. 2 og 3 ikke dokumentert. 5 nei. | leverandørpåstand (via søkeutdrag fra Microsoft Marketplace og LawNext) | native tillegg + integrasjon (M365, Azure OpenAI) | https://marketplace.microsoft.com/en-us/product/SaaS/lawtoolboxinc.lawtoolbox_ai ; https://www.lawnext.com/2023/12/with-launch-of-new-ai-features-lawtoolbox-is-first-legal-app-approved-for-use-with-copilot-for-microsoft-365.html | LawToolBox / LawNext | 2023-12 (lansering) | Middels |
| 4 | **Mitratech ARIES AI (TeamConnect)** | «AI is used only to extract, categorize, and calculate court deadlines. Legal teams review and confirm all tasks before anything is created.» Siden sier ikke om det finnes kildeutdrag, avvisning per element eller kalendervisning. | 1 ja (rettsordrer, filformat ikke oppgitt). 4 delvis: menneskelig bekreftelse er obligatorisk, men det er uklart om den skjer per element. 2, 3 og 5 ikke dokumentert. | leverandørpåstand (siden er lest direkte) | native modul | https://clc.mitratech.com/turn-scheduling-orders-into-action-with-aries-ai | Mitratech | Udatert (© 2026) | Middels |
| 5 | **syllabus2cal** | Ifølge søkeutdrag: last opp pensumplan, «review every extracted event», velg seksjon, løs konflikter og eksporter til ICS eller PDF. Direkte skriving til Google Calendar er satt på pause. | 1 ja. 4 delvis: hver hendelse gjennomgås, men eksplisitt avvisning per element er ikke bekreftet. 2 delvis («resolve conflicts»). 3 og 5 nei. | leverandørpåstand (via søkeutdrag) | native (nisje-webapp) | https://syllabus2cal.onrender.com/help | Uavhengig utvikler | Udatert | Lav–middels |
| 6 | **Deadliner (GitHub, ramneek1-exe)** | Åpen kildekode. PDF/DOCX/XLSX/bilde → LLM-uttrekk med Zod-validering, der en ugyldig respons «fails the request cleanly so no deadline is silently dropped». «Review & edit — inspect, rename, delete, or edit individual events before exporting.» Eksporterer ICS og viser hendelsene som tabell eller kort. | 1 ja (Word og PDF). 4 delvis: redigering og sletting per element, men ingen eksplisitt godkjenning. 2 delvis (schema-validering, ikke flagging). 3 nei. 5 nei. | dokumentert (README er lest direkte) | open source / egen utvikling | https://github.com/ramneek1-exe/deadliner | Privat utvikler | v0.4.0, 2026 | Høy |
| 7 | **Google LangExtract (og Elixir-porten lang_extract)** | Bibliotek som knytter hvert uttrekk til tegnposisjoner i kildeteksten. Elixir-porten setter status `:exact`, `:fuzzy` eller `:not_found` per span (byte_start er nil når teksten ikke finnes). | 3 ja, som byggekloss: maskinell verifisering av at kildeutdraget finnes er dokumentert. 1 delvis (tekst, ikke direkte Word/PDF). 2, 4 og 5 nei. | dokumentert (pakkedokumentasjon via søkeutdrag) / uavhengig (W&B-gjennomgang) | egen utvikling (bibliotek) | https://readme.hex.pm/lang_extract/0.9.0 ; https://wandb.ai/wandb_fc/genai-research/reports/LangExtract-Transform-text-into-structured-data-with-AI--VmlldzoxNDI1OTMyNw | Google (oppstrøms) / tredjepart (port) | Udatert | Middels–høy |
| 8 | **Gemini (Gmail «Add to calendar», Gemini-app med PDF)** | Det offisielle «Add to calendar» i Gmail tilbyr ved flere hendelser å «add all of them to your Google Calendar». At PDF lastes opp i Gemini-appen, at det vises et utkastkort og at brukeren bekrefter, er beskrevet av tredjepartsblogger, ikke av Google. | 1 delvis (PDF-flyten er ikke dokumentert av Google). 4 nei: Gmail-funksjonen tilbyr å legge til alle samlet. 3 nei: ingen kildeutdrag per hendelse funnet. 2 og 5 nei. | leverandørpåstand (Google Workspace Updates) + uavhengig blogg | native | https://workspaceupdates.googleblog.com/2025/03/add-events-to-google-calendar-using-gemini-in-gmail.html ; https://ideakitchen.substack.com/p/ai-recipe-quick-add-events-from-any | Google / Substack | 2025-03 og 2025-08 | Middels |

## Sterkeste motargument

Det sterkeste motargumentet er at **arbeidsflyten allerede finnes delt på to markedsledere, og at produktene ligger nær nok til at særpreget er smalere enn konklusjonen antyder**:

- **Clio Manage AI** dekker kjernen i «KI-forslag med kilde og menneskelig port». Brukeren laster opp et dokument, KI lager *utkast* til hendelser, kildeteksten vises per hendelse («showing the text it was pulled from», med hover for opprinnelse), og ingenting lagres før brukeren bekrefter. Det er nesten element 1, 3 og 4 i ett native produkt.
- **Plandisc AI Import** dekker element 1 og 5: Word/PDF blir et sirkulært årshjul, levert native av den mest kjente årshjulleverandøren i Norden.
- **LangExtract** viser at maskinell verifisering av at sitatet finnes i kilden (element 3) er en hyllevare-byggekloss med eksakt, uskarp og ikke-funnet-status, ikke en ny idé.

En kritiker vil si: «Clio pluss Plandisc pluss LangExtract er hele flyten. Det nye er bare limet.» Selv om ingen enkeltaktør er dokumentert med alle fem elementene, gjør dette det vanskelig å påstå at enkeltelementene er nye.

Det er også verdt å merke seg at Plandisc kunngjorde i september 2026 at en chat- og hjelpefunksjon i selve årshjulet er neste steg. Det er en mulig retning mot gjennomgangsflyt, men det er en **antakelse** at den vil inneholde gjennomgang per forslag.

## Søkt etter, ikke funnet

- **Maskinell verifisering av sitater i et sluttbrukerprodukt.** Ingen kalender- eller fristprodukt er dokumentert med en sjekk av at det viste kildeutdraget faktisk finnes ordrett i dokumentteksten. Clio *viser* kildetekst, men verifisering er ikke dokumentert. Det er bare biblioteket LangExtract som gjør dette.
- **Eksplisitt avvisning per element og fravær av «godkjenn alle».** Ingen kilde dokumenterer at bulk-godkjenning er bevisst utelatt. Clio laster opp bekreftede hendelser i én batch. Gemini i Gmail tilbyr å legge til alle. Ved ARIES og LawToolBox er det uklart om gjennomgangen skjer per element.
- **Flagging av manglende eller usikre felt per forslag.** Dette er ikke dokumentert for noen av produktene. Nærmest er Deadliner (schema-validering) og syllabus2cal («resolve conflicts»).
- **Gjennomgangsflyt i Plandisc AI Import.** Det er ikke dokumentert om det finnes forhåndsvisning, kilder eller enkeltgodkjenning.
- **Andre årshjulsprodukter med KI-uttrekk fra dokument.** Norske og skandinaviske søk («årshjul KI dokument», «årshjul KI importer frister godkjenn») ga bare maler og kommunale dokumenter.
- **Forskningsprototyper innen HCI.** Ingen er funnet innenfor budsjettet. Dette er ikke uttømmende søkt.
- **ChatGPT, Claude, Copilot og NotebookLM med kalender og sitater per hendelse.** Ikke funnet innenfor budsjettet. NotebookLM har ingen kalenderintegrasjon, men det er en **antakelse** som ikke er verifisert i denne kjøringen.
- **Byggebransjen, offentlig/militær planlegging og tilskuddsfrister.** Ikke dekket innenfor budsjettet.

## Dom: står konklusjonen? (står / må nyanseres / faller) — begrunnelse

**Må nyanseres.**

- **Bokstavelig står konklusjonen.** Ingen enkeltkilde funnet i denne kjøringen dokumenterer alle fem elementene samlet. Særlig mangler maskinell verifisering av sitater i et sluttbrukerprodukt, eksplisitt fravær av «godkjenn alle», flagging av usikre felt og årshjulvisning i samme produkt.
- **Formuleringen bør likevel strammes.** Clio Manage AI er dokumentert med KI-utkast fra dokument, kildetekst per hendelse og obligatorisk bekreftelse før lagring, og ligger dermed nær element 1, 3 og 4. Plandisc AI Import er dokumentert med Word/PDF til sirkulært årshjul (element 1 og 5). Påstander som «ingen viser kildeutdrag per forslag» eller «ingen tar Word/PDF inn i et årshjul med KI» faller derfor.
- **Det forsvarlige særpreget er snevrere**, nemlig kombinasjonen av:
  - (a) programvareverifisering av at hvert sitat finnes i dokumentteksten
  - (b) obligatorisk avgjørelse per element, uten bulk
  - (c) flagging av manglende eller usikre felt
  - (d) at alt dette leder inn i et årshjul

  Selv dette er bare «ikke funnet». Det er ikke bevist at det ikke finnes, fordi budsjettet var begrenset, de viktigste Clio-sidene ikke kunne leses direkte, og Plandiscs importflyt ikke er dokumentert offentlig.
- **Anbefalt oppfølging:** test Plandisc AI Import selv (prøveversjon) og les Clios hjelpeside i nettleser for å avklare om bekreftelsen skjer per hendelse og om det finnes «confirm all».
