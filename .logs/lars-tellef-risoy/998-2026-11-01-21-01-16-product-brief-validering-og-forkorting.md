# Product Brief: validering og forkorting

## 2026-11-01 kl. 21:01 — Lars Tellef Risøy

### Oppgave
Kvalitetssikre Product Brief før UX-fasen og forkorte den mot faglærers veiledende omfang, uten å endre produkt eller scope. Dokumentere arbeidet i KI-loggen og avslutte Risøys arbeid med Product Brief-fasen.

### Plan
- Uavhengig BMAD-validering med Mary, deretter de sju presiseringene Risøy godkjente og kontroll mot PRD.
- Redaksjonell forkorting i flere godkjenningsrunder, deretter kontroll mot PRD.
- Måling av A4-formatering utenfor repoet og kontroll av PDF-en side for side.
- Ferdigstilling av KI-loggen. Detaljer, prompter og testresultater står i [KI-loggen](../../docs/ki-logg/2026-11-01-product-brief-validering.md).

### Resultat
- **Validering og presisering:** Commit `0d4517e` inneholder de sju presiseringene etter valideringen. Kontrollen mot PRD fant ingen motstrid.
- **Forkorting:** Commit `fca9a6a` forkorter `_bmad-output/planning-artifacts/product-brief.md` fra 1 146 til 967 ord (15,6 %). Alle ni seksjoner, de fem MVP-kapabilitetene og de sju presiseringene er beholdt. OUT gikk fra 10 til 8 punkter uten at avgrensninger ble fjernet.
- **Kontroll mot PRD:** Ingen motstrid og ingen endring av MVP. PRD-en er ikke endret.
- **A4-formatering:** 20 profiler ble rendret med Edge. Anbefalt formatering (Calibri 11 pt, linjeavstand 1,3 og 25 mm marger) gir ca. 2,5 sider, med 3 fysiske sider der den tredje er omtrent halvfull. Formateringen er ikke lagret i repoet, siden briefen er ren Markdown. Word er ikke testet.
- **KI-logg:** `docs/ki-logg/2026-11-01-product-brief-validering.md` ble ferdigstilt og committet i `fca9a6a`. Prompt 1–2 er ikke kontrollert mot den opprinnelige samtalen, og det står i loggen.
- **Status:** Product Brief-fasen er avsluttet. UX-fasen overtas av et annet gruppemedlem og er ikke startet i denne økten.

### Åpne punkter
- UX: Vurdere om frister skal ha egen kategori.
- Testplan: Frister og datoer. Lagrede frister skal ha lik start- og sluttdato, mens KI ikke automatisk skal anta én dag når et dokument bare angir én dato (UJ-1 E6). Regelen for frister står ikke uttrykkelig i PRD-en.
- Testplan: Bruker skal kunne finne tidspunkt og ansvarsområde uten å åpne andre filer. SM-1 nevner ikke denne oppgaven eksplisitt.
- Testplan: Risikoer knyttet til fiktive dokumenter, datotolkning og feilaktig brukergodkjenning.
- PRD §4.5 og §8.2 omtaler kildeutdrag som tillegg og endring fra briefen, mens briefen nå nevner kildeutdrag. Dette krever ingen endring nå.
