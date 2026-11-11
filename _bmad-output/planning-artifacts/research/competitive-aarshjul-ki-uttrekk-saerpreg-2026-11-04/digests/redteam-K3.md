# Red team K3 — er M365 godt nok?

Konklusjonen som angripes: M365 dekker behovet bare delvis. Planner Agent (GA juni 2026, Copilot-lisens) lager planutkast fra Word/Excel/PowerPoint, og brukeren godkjenner dem. Årshjul finnes bare via tredjepart. Verbatim kildeutdrag per oppgave, usikkerhetsflagg per felt og obligatorisk godkjenning per punkt krever egenutvikling.

Arbeidsdato: 2026-11-04. Alle påstander under er hentet i denne kjøringen, med mindre de er merket «ubekreftet antakelse».

## Motbevis

| # | Påstand | Produkt/kilde | Bevistype | Levering | URL | Utgiver | Dato (GA/preview) | Konfidens |
|---|---|---|---|---|---|---|---|---|
| 1 | Brukeren godkjenner hvert punkt allerede i standardproduktet. Nye oppgaver vises i et forhåndsvisningskort der brukeren kan «edit or remove items» og må «confirm the final set before tasks are added to the plan». Message Center skriver at kortene «require users to review and confirm changes before they are applied». | Planner Agent | Primær (Microsoft-blogg og Message Center) | Native, krever Copilot-lisens | https://techcommunity.microsoft.com/t5/planner-blog/planner-agent-brings-work-management-directly-into-microsoft-365/ba-p/4511720 ; https://mc.merill.net/message/MC1323264 | Microsoft (Tech Community); Merill Fernando (speil av Message Center) | Bloggen: 20.04.2026 (Frontier). MC1323264: publisert 26.05.2026, GA midt–sent i juni 2026 | Høy. Dette svekker konklusjonens påstand om at godkjenning per punkt krever egenutvikling. Godkjenningen er riktignok samlet (redigere/fjerne og så bekrefte settet), ikke en tvungen sjekk av hvert felt. |
| 2 | Agenten foreslår forfallsdatoer, og brukeren kan endre dem i naturlig språk («this Friday») eller direkte på oppgavekortet. | Planner Agent | Primær | Native | Samme Tech Community-URL | Microsoft | 20.04.2026 | Høy |
| 3 | Agenten kan «Generate plans from Word, Excel, or PowerPoint files». Redigering via agenten er begrenset til feltene Name, Progress, Due date, Start date, Priority og Plan name. | Planner Agent | Primær (support-side) | Native | https://support.microsoft.com/en-us/Planner/what-can-you-do-with-planner-agent-in-copilot | Microsoft | Udatert side, hentet 2026-11-04 | Høy. Bekrefter konklusjonen. PDF er ikke nevnt. |
| 4 | Copilot i Word viser kildehenvisninger til stedet i dokumentet: «you can also view references with citations from where Copilot pulled information in your document». | Copilot i Word (chat) | Primær | Native, krever Copilot-lisens (eller Pro) | https://support.microsoft.com/en-gb/word/copilot/chat-with-copilot-about-your-word-document | Microsoft | Udatert, hentet 2026-11-04 | Middels–høy. Dette er et delvis motbevis mot «verbatim kildeutdrag krever egenutvikling». Sporbarhet til kilden finnes, men bare i chatten. Den følger ikke med inn i Planner-oppgavene. |
| 5 | Copilot Notebooks støtter PDF som referansefil (.docx, .pptx, .xlsx, .pdf, .loop, maks 20 filer). Svarene har nummererte kildehenvisninger som åpner kildedokumentet. | Copilot Notebooks (OneNote/M365) | Sekundær (advokatforening og polsk IT-nettsted) | Native, krever Copilot-lisens. En begrenset gratisvariant finnes via Copilot Chat. | https://www.ncbar.org/2026/07/21/updates-to-microsoft-copilot-notebook/ ; https://www.centrumxp.pl/Aktualnosci/Microsoft-365-Copilot-Notebooks-dostepne-w-OneNote-na-Windows | NC Bar Association; CentrumXP | 21.07.2026 (NCBar). GA-status for PDF-henvisninger er ikke bekreftet. | Middels. Gir en native vei fra PDF-ordre til uttrekk med kildehenvisninger, men ikke direkte til Planner eller årshjul. |
| 6 | Agenten kan legge til filer som «Knowledge sources» i en plan. Generering av oppgaver fra *mål* krever premium-plan (Planner Plan 1 / Project Plan 3/5). Brukere uten Copilot-lisens kan ikke bruke agenten. | Planner Agent | Primær | Native, lisensbetinget | https://support.microsoft.com/en-au/office/access-planner-agent-86bf60a1-239d-4c37-b7b6-9a4111e1cc02 | Microsoft | Hentet 2026-11-04 | Høy. Dette styrker konklusjonen, fordi lisenskravet gjelder hver enkelt bruker. |

## Forsvaret / offentlig sektor og Copilot

- **Statlig Copilot-pålegg (hovedfunn, ikke verifisert i primærkilde):** Et skriftlig stortingsspørsmål fra Stian Storbukås (FrP) til digitaliseringsminister Karianne Oldernes Tung lyder slik: «Vil staten dekke eventuelle overtredelsesgebyr fra Datatilsynet som følge av at etater følger regjeringens KI-pålegg med hensyn til Microsoft Copilot?» Altinget viser saken med tidsstempel 25.06.2026. Jeg fant verken svaret, selve pålegget eller hvem det gjelder. https://www.altinget.no/statogstyring/statsradensvarer/22324 (Altinget, som henter fra Stortingets database). Hvis pålegget finnes, styrker det argumentet om at statlige ansatte i praksis vil få Copilot. Spørsmålet viser samtidig at personvernrisikoen er politisk omstridt.
- **Forsvaret og Microsoft-sky:** I et skriftlig stortingsspørsmål (Gjelsvik) svarte forsvarsminister Frank Bakke-Jensen at Microsoft-skytjenester rulles ut for **ugradert** informasjon. Forsvaret har «ikke konkrete planer» om å legge gradert informasjon i allmenne skytjenester. https://www.stortinget.no/no/Saker-og-publikasjoner/Sporsmal/Skriftlige-sporsmal-og-svar/Skriftlig-sporsmal/?qnid=55219 (Stortinget). Datoen er ikke hentet. Ubekreftet antakelse: svaret er fra 2017–2021, da Bakke-Jensen var minister, og er dermed gammelt. En FINN-annonse fra Cyberforsvaret (seksjon for infrastruktur og sky) nevner drift av Forsvarets skytjenester «inkludert Microsoft 365». Det tyder på at M365 er i bruk, men annonsen er ikke lest i sin helhet.
- **Forsvarets KI-modenhet:** KI-sjef Thomas Hansen sier Forsvaret ligger «fem til ti år bak». Han nevner en skystrategi under arbeid og suverenitetshensyn. Copilot og M365 nevnes ikke. https://www.altinget.no/forsvar/artikkel/forsvarets-ki-sjef-ligger-fem-til-ti-aar-bak-paa-bruk-av-ki (Altinget, 27.08.2025).
- **Personvern i offentlig sektor:** NTNU og Datatilsynet gjennomførte et sandkasseprosjekt om M365 Copilot med rapporten «Copilot med personvernbriller på», basert på tester våren 2024. Konklusjonene er ikke lest. https://www.ntnu.no/copilot. I Danmark har Datatilsynet ifølge ing.dk (23.12.2025) slått av Copilot selv. Det gjelder ikke Norge.
- **Ikke funnet:** Jeg fant ingen dokumentasjon på at Forsvaret har innført eller planlegger M365 Copilot, og heller ingen dokumentasjon på et eksplisitt forbud.

## Sterkeste motargument

Planner Agent har allerede den viktigste kontrollen innebygd, nemlig at mennesket bekrefter før noe opprettes. Det finnes også native kildesporing i nabofunksjonene: Copilot i Word har henvisninger til steder i dokumentet, og Copilot Notebooks har nummererte henvisninger og støtter PDF. Dersom staten i tillegg har et «KI-pålegg» om Copilot, vil en troppssjef i Forsvaret kunne få verktøyet uten egen anskaffelse, sikkerhetsgodkjenning eller opplæring i en ny app. Da kan arbeidsflyten «ordre → Notebook med henvisninger → Planner Agent med godkjenningskort → Plandisc-årshjul» bli godt nok i praksis.

Det som mangler, er presisjon og sammenheng. Ingen funksjon setter usikkerhetsflagg per felt, og kildeutdraget følger ikke med inn i oppgaven. Det er et nisjekrav. Det er ikke en grunnleggende mangel ved M365.

Motvekt: Forsvarets ordrer er ofte graderte. M365-skyen er (etter det som er dokumentert) bare for ugradert informasjon, så Copilot kan ikke behandle graderte ordrer. Det samme gjelder trolig enhver skybasert nisjeløsning.

## Søkt etter, ikke funnet

- At Planner Agent støtter PDF som kilde. Ikke nevnt i noen Microsoft-kilde.
- At Planner Agent viser kildehenvisninger eller utdrag per oppgave.
- Usikkerhets- eller konfidensflagg per felt i noe Copilot-produkt.
- Et native årshjul eller en sirkulær årsvisning i Planner, Outlook eller Loop. Ikke funnet. Dette er ikke søkt eksplisitt, men kom heller ikke opp i noen treff.
- Teksten i regjeringens «KI-pålegg om Copilot» og statsrådens svar.
- At Forsvaret selv har tatt i bruk M365 Copilot (Forsvaret.no, FMA, digi.no).
- Uavhengig analyse- eller undersøkelsesdata om at brukere foretrekker innebygd Copilot fremfor frittstående verktøy. Petri (01.07.2025, https://petri.com/why-are-users-choosing-chatgpt-over-microsoft-365-copilot/) argumenterer for at integrasjon med tenant-data er Copilots fortrinn, men skriver at «Users are choosing ChatGPT instead» og at adopsjonen er «sluggish». Artikkelen oppgir ingen data. Gartner-sidene som dukket opp, inneholdt ingen slike tall. Tool consolidation-argumentet er dermed ikke belagt med uavhengig evidens i denne kjøringen.
- Om Planner Agent fungerer på norsk og i offentlige skyer (GCC eller tilsvarende).

## Dom: står konklusjonen? — **må nyanseres**

Hovedpoenget står: M365 dekker behovet bare delvis. Ingen kilde viser verbatim utdrag per oppgave, usikkerhetsflagg per felt, PDF-støtte i Planner Agent eller et native årshjul.

Tre ting bør likevel rettes:
1. **«Obligatorisk godkjenning per punkt krever egenutvikling» er for sterkt.** Planner Agent krever at brukeren gjennomgår og bekrefter, og lar brukeren redigere eller fjerne enkeltpunkter før de opprettes (MC1323264, Tech Community 20.04.2026). Det som eventuelt krever egenutvikling, er tvungen avkrysning per felt med kilde ved siden av.
2. **Kildesporing finnes delvis native** i Copilot i Word (henvisninger til dokumentet) og i Copilot Notebooks (nummererte henvisninger, PDF støttes). Den finnes bare ikke i Planner-kjeden. Konklusjonen bør si «ikke ende-til-ende» i stedet for å antyde at det ikke finnes i det hele tatt.
3. **Kontekst om tilgjengelighet:** Et mulig statlig Copilot-pålegg (2026, innholdet ikke verifisert) gjør det mer sannsynlig at brukerne allerede har Copilot. På den andre siden begrenser skyløsninger for bare ugradert informasjon i Forsvaret nytten for graderte ordrer, både for M365 og for en nisjeløsning.
