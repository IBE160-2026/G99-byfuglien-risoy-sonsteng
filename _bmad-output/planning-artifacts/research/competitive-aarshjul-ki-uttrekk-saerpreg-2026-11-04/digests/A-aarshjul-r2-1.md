# Digest A r2 — Årshjul: verifisering og nye leverandører

Kjøring: 2026-11-04. Budsjett brukt: ca. 18 verktøykall, 6 kilder lest direkte (resten søkeresultater/snippets). Flere sider var blokkert: Zendesk-hjelpesenteret (403), enable365.ai (403), web.archive.org (verktøyet kan ikke hente derfra).

## Verifisering av runde-1-påstander

| Påstand | Utfall (verified/disputed/unverified/overturned) | Uavhengig kilde (URL, utgiver, dato) | Kommentar |
|---|---|---|---|
| Plandisc har «AI Import» som gjør Excel/Word/PDF om til en komplett plandisc og gir et «draft» | **unverified** | Fant ingen uavhengig kilde. Leverandørens egen brukermanual: https://plandisc.com/hubfs/User%20manuals/ENG%20-%20User%20manual.pptx.pdf?hsLang=en (Plandisc, dato ikke synlig i teksten, runde 1 oppga 22.10.2026; lest 2026-11-04) | Manualen omtaler **ikke** AI-import fra Word/PDF. Den dokumenterer bare (a) en KI-funksjon som lager et *grunnoppsett* («base layout … Don't make it too detailed … a custom template, or a framework») og (b) **Excel-import via fast mal** («one Excel template per ring», start- og sluttdato, «Title»). Word/PDF nevnes bare som *vedlegg* til aktiviteter. Markedsføringssiden (https://plandisc.com/en/ai-circular-planner, lest på nytt 2026-11-04, bare «© 2026») sier at brukeren «refin[er]» et utkast og «stay[s] in control». Den nevner verken godkjenning/avvisning per element, kildeutdrag, flagging av usikre felt, beta eller hvilken plan funksjonen hører til. Det er altså fortsatt bare en **leverandørpåstand**, og påstanden mangler dekning i leverandørens egen manual. |
| Plandisc AI-assistent lager hjulmal fra tekstprompt (blogg 2026-01-05) | **unverified** (ingen uavhengig kilde), men nå **dokumentert** av leverandørens manual | Samme manual som over (Plandisc) | Manualen bekrefter at «Create a new plandisc with AI» lager oppsett og struktur (ringer, overskrifter), ikke aktiviteter. Det er samme utgiver, så kilden er ikke uavhengig. |
| KI lansert som beta i «Edition 3, 2024» | **unverified** | Ingen. Wayback Machine var utilgjengelig for verktøyet, og søk etter release notes ga ingen treff | Status (beta eller GA) og lanseringstidspunkt er fortsatt ukjent. |
| PlanIt (Enable 365) har ingen KI | **unverified** (ikke motsagt) | Søkesnippets fra Microsoft Marketplace (https://marketplace.microsoft.com/en-us/product/SaaS/enableas1652357678356.planitsaas, Enable 365 via Microsoft, udatert) | Snippetene beskriver sirkulær årsvisning, tabell, liste og måned/uke, med integrasjon mot Planner og Outlook. KI eller Copilot knyttes ikke til PlanIt; Enable 365 nevner KI bare generelt som rådgivningstjeneste. Selve enable365.ai-sidene ga 403. |

## Nye funn

| # | Påstand | Produkt | Bevistype | Levering | URL | Utgiver | Publisert/oppdatert | Lest | Konfidens | Klasse |
|---|---|---|---|---|---|---|---|---|---|---|
| 1 | Brukermanualen dokumenterer bare Excel-import via fast mal (én mal per ring, Title/start/slutt) og KI som lager *layout*. Den har ingen KI-import fra Word/PDF. | Plandisc | dokumentert (leverandørmanual) | native | https://plandisc.com/hubfs/User%20manuals/ENG%20-%20User%20manual.pptx.pdf?hsLang=en | Plandisc | ikke synlig i teksten (runde 1: 22.10.2026) | 2026-11-04 (tekst hentet ut med pdftotext) | middels–høy | Konkurrent, direkte |
| 2 | AI Import-siden nevner ingen gjennomgang per element, ingen kildeutdrag, ingen flagging av usikre felt og ingen beta- eller planbegrensning. Gjennomgangen beskrives som redigering av et helt utkast («refining it»). | Plandisc | leverandørpåstand | native | https://plandisc.com/en/ai-circular-planner | Plandisc | udatert (© 2026) | 2026-11-04 | middels | Konkurrent, direkte |
| 3 | Capterra-profilen har bare én (insentivert) anmeldelse og ingen uavhengig omtale av KI. Ingen G2-profil for Plandisc ble funnet. | Plandisc | uavhengig (tynn) | — | https://www.capterra.com/p/249127/Plandisc/ | Capterra | ifølge søkesnippet oppdatert 2025-11-08 | kun snippet | lav | Kontekst |
| 4 | Orbit er et svensk digitalt årshjul («visuellt årshjul», «cirkeldiagram») med «AI-driven flaskhalsdetektion» (analyserer kommende 90 dager for overbelastning og krockende frister, «drivet av Lovable AI», Maj 2026) og «Importera årshjul från Excel» (Juni 2026). Import fra Word/PDF eller dokumentbasert KI-uttrekk nevnes ikke. | Orbit by Uanet | leverandørpåstand | native (SaaS, sync mot Outlook/Teams/Planner via Graph, kan bygges inn i Teams/SharePoint) | https://orbitbyuanet.se/ | Uanet | endringslogg Mai–Juli 2026 | 2026-11-04 | middels | Konkurrent, delvis (KI brukes til analyse, ikke uttrekk) |
| 5 | PlanIt årshjul er Teams/SharePoint-app med sirkulær årsvisning og måned/uke-visning. Den lagrer data i kundens M365-tenant, kan opprette Planner-oppgaver og finnes på svensk, norsk, dansk, spansk og engelsk. KI/Copilot eller dokumentimport er ikke funnet. | Enable 365 PlanIt | leverandørpåstand (snippets) | native (M365-app) | https://marketplace.microsoft.com/en-us/product/web-apps/enableas1652357678356.planit_saas_no?tab=overview | Enable 365 / Microsoft Marketplace | udatert | kun snippet | middels | Konkurrent, uten KI |
| 6 | Copilot i SharePoint gir generelle KI-handlinger på filer (oppsummere, sammenligne, FAQ), men har ingen årshjulfunksjon. Et årshjul basert på Copilot ville kreve egenutvikling eller konfigurasjon (f.eks. SPFx-webdel). | Microsoft Copilot i SharePoint | dokumentert (Microsoft support) | integrasjon/konfigurasjon eller egenutvikling | https://support.microsoft.com/sv-se/sharepoint/copilot-in-sharepoint/copilot-in-sharepoint-an-overview | Microsoft | udatert | kun snippet | middels | Substitutt |
| 7 | Microsoft 365 Copilot Chat kan opprette Planner-oppgaver og -planer fra naturlig språk (utrulling fra tidlig september 2026). Funksjonen har ikke årshjul og er en tredjepartsomtale. | Microsoft Planner + Copilot | uavhengig (tredjepartsblogg) | native i M365, ikke årshjul | https://m365admin.handsontek.net/?p=22927 | HANDS ON tek (m365admin) | 2026 (ifølge snippet) | kun snippet | lav–middels | Substitutt |

## Kapabilitetsmatrise (oppdatert)

| Produkt | circular wheel | doc upload → AI suggestions | per-item review vs source excerpts | explicit per-item approval | combined workflow |
|---|---|---|---|---|---|
| Plandisc | Ja (dokumentert) | Leverandørpåstand: Excel/Word/PDF → «draft». Manualen dokumenterer bare Excel-mal-import og KI-layout | Ikke funnet | Ikke funnet (marketing beskriver redigering av helt utkast) | Nei, så langt vi kan evidensere |
| Orbit by Uanet | Ja (leverandørpåstand) | Nei: Excel-import og KI-flaskhalsanalyse, ikke uttrekk fra dokument | Ikke funnet | Ikke funnet | Nei |
| Enable 365 PlanIt | Ja (leverandørpåstand) | Ikke funnet | Ikke funnet | Ikke funnet | Nei |
| Puzzlepart årshjul | Ukjent (søk ga bare puslespill-treff) | Ikke funnet | Ikke funnet | Ikke funnet | Ukjent |
| Copilot i SharePoint/Planner | Nei | Generelle fil-KI-handlinger og oppgaver fra prompt, ikke årshjul | Ikke funnet | Ikke funnet | Nei |

## Lette etter, fant ikke

- **Plandisc AI Import i hjelpesenter eller kunnskapsbase:** Søk på «Plandisc AI import Word PDF beta release notes» og «plandisc KI import årshjul Word PDF» ga ingen artikkel. Zendesk (plandiscsupport.zendesk.com/hc/en-us) svarte med 403. Hverken /hc/no eller artikkellister ble lest.
- **Wayback-kopi av plandisc.com/knowledge-base/edition-3-2024:** web.archive.org kan ikke hentes med verktøyet. Påstanden om beta-lansering er derfor ikke sjekket.
- **Uavhengig omtale av Plandisc AI Import** (G2, Capterra, Product Hunt, kommunesider, YouTube): Søket «Plandisc AI review capterra G2 "AI"» fant ingen. Capterra har én anmeldelse uten KI-omtale. YouTube og kommunesider ble ikke søkt, fordi budsjettet var brukt opp.
- **Puzzlepart årshjul:** Søket «Puzzlepart årshjul» ga bare puslespill-treff. Det var ikke budsjett til et nytt søk (f.eks. «Puzzlepart Prosjektportalen årshjul»).
- **Årshjul med Copilot/KI som lager aktiviteter fra dokumenter (spørsmål 3):** Søk på «årshjul Copilot SharePoint KI aktiviteter fra dokument» og «enable365 PlanIt årshjul AI Copilot» ga ingen treff. Plandisc (bare leverandørpåstand) er fortsatt eneste kandidat. Dette beviser ikke at slike produkter ikke finnes, siden danske og svenske søkeord som «årshjul app AI» og «aarshjul» ikke ble dekket fullt ut.
- **PlanIt-detaljer fra enable365.ai og G2:** Begge sider ga 403 eller ble ikke lest. Funnene bygger bare på søkesnippets.
- **Kildeutdrag, verbatim-verifisering eller flagging av usikre felt** i noe årshjulprodukt: ikke funnet i noen kilde som ble lest.
