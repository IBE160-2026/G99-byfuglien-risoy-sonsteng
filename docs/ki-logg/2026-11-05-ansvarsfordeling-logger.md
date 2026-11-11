# 2026-11-05 — Ansvarsfordeling mellom loggene

- **Deltakere:** Lars Tellef Risøy
- **KI-verktøy:** Claude Code med modellen Claude Opus 5.5 (`claude-opus-5-5`).
  ChatGPT (OpenAI) ble brukt til vurdering og utforming av promptene.
- **Kontrollert av:** <fylles inn av gruppemedlemmet som har godkjent loggen>

## Oppgave

Tydeliggjøre hva KI-loggen, sesjonsloggen, `issues.md` og BMAD `.memlog.md`
skal brukes til, slik at alle gruppemedlemmer følger samme praksis og
unngår dobbeltlogging. Endringen ble avgrenset til `docs/ki-logg/README.md`.

## Prompt (ordrett)

Promptene er gjengitt ordrett og i rekkefølge. Claude Codes svar mellom
promptene er ikke tatt med.

<details>
<summary><strong>Prompt 1 – Vurdering av eksisterende praksis</strong></summary>

> Vi ønsker å tydeliggjøre hvordan prosjektets ulike logger skal brukes, slik at alle gruppemedlemmer følger samme praksis og vi unngår dobbeltlogging.
>
> Les først `CLAUDE.md`, `docs/ki-logg/README.md` og eksisterende rutiner for sesjonslogg og `issues.md`.
>
> Vurder deretter om instruksjonene allerede dekker følgende ansvarsfordeling:
>
> - **KI-logg (`docs/ki-logg/`):** Dokumenterer KI-verktøy, prompter, hva KI leverte, menneskelig kontroll, beslutninger og relevante refleksjoner.
> - **Sesjonslogg (`.logs/<bruker>/`):** Kort oppsummering av arbeidsøkten, gjennomførte endringer, resultat og videre arbeid.
> - **`issues.md`:** Åpne oppgaver, problemer og uavklarte beslutninger. Punkter lukkes når de er løst.
> - **BMAD `.memlog.md`:** Beslutningshistorikk og dokumentasjon knyttet til det aktuelle BMAD-artefaktet.
>
> **Oppgave**
>
> 1. Foreslå en kort presisering i `docs/ki-logg/README.md` som forklarer ansvarsfordelingen og prinsippet om å unngå dobbeltlogging.
> 2. Kontroller at `CLAUDE.md` henviser til felles rutiner, slik at Claude Code følger dem.
> 3. Sørg for at instruksjonene gjelder alle gruppemedlemmer, ikke bare én bruker.
> 4. Gjenbruk eksisterende rutiner og skill-struktur. Ikke opprett nye loggsystemer eller parallelle instruksjoner.
> 5. Hold endringene minimale og unngå å gjøre README eller CLAUDE.md unødvendig lange.
>
> Presenter eksisterende praksis, eventuelle mangler og konkret foreslått ordlyd.
>
> Ikke endre filer, commit eller push før jeg har godkjent forslaget.

</details>

<details>
<summary><strong>Prompt 2 – Avgrenset endring av README</strong></summary>

> Jeg ønsker å begrense endringen til `docs/ki-logg/README.md`.
>
> Sesjonsloggen, `issues.md` og sesjonslogg-skillen er etablert av faglærer. Disse skal ikke endres. Vi skal heller ikke endre `CLAUDE.md` eller `AGENTS.md` nå.
>
> **Oppgave**
>
> Gjør en minimal oppdatering av `docs/ki-logg/README.md`:
>
> 1. Legg inn en kort forklaring på ansvarsfordelingen:
>    - KI-loggen dokumenterer KI-verktøy, prompter, resultater, menneskelig kontroll og relevante refleksjoner.
>    - Sesjonsloggen dokumenterer kort hva som ble gjort og hva som gjenstår, etter faglærers eksisterende rutiner.
>    - `issues.md` følger opp åpne punkter etter eksisterende rutiner.
>    - BMAD `.memlog.md` dokumenterer beslutningshistorikk for det aktuelle artefaktet.
>
> 2. Presiser at KI-loggen gjelder økter der KI bidrar til endringer i kode eller prosjektdokumentasjon, ikke bare kodeøkter.
>
> 3. Legg til én kort regel om å unngå unødvendig dobbeltlogging: Henvis til eksisterende logger i stedet for å gjenta detaljene.
>
> **Føringer**
>
> - Behold eksisterende krav om ordrette prompter, menneskelig kontroll og godkjenning før KI-loggen lagres.
> - Endringen skal gjelde alle gruppemedlemmer.
> - Ikke opprett nye logger, maler eller rutiner.
> - Ikke endre andre filer, inkludert `CLAUDE.md`, `AGENTS.md`, `.logs/`, `issues.md`, sesjonslogg-skillen eller BMAD-artefakter.
> - Hold README kort og praktisk.
>
> Vis konkret diff og Git-status, og stopp før commit og push for min godkjenning.

</details>

<details>
<summary><strong>Prompt 3 – Utkast til KI-logg</strong></summary>

> Jeg godkjenner endringene i `docs/ki-logg/README.md`.
>
> Lag et kort utkast til KI-logg for denne økten etter den eksisterende malen. Ta med den faktiske prompten ordrett, hva som ble endret, og hvordan endringene ble kontrollert. Hold beskrivelsene korte og unngå dobbeltlogging.
>
> ChatGPT ble brukt til vurdering og utforming av prompten.
>
> Vis KI-loggutkastet før det lagres, slik at jeg kan godkjenne det.
>
> Ikke endre faglærers sesjonslogg, `issues.md`, sesjonslogg-skillen, `CLAUDE.md` eller `AGENTS.md`.
>
> Ikke commit eller push ennå.

</details>

<details>
<summary><strong>Prompt 4 – Kontroll, lagring, commit og push</strong></summary>

> Jeg godkjenner innholdet i KI-loggutkastet, med forbehold om at teksten er korrekt gjengitt.
>
> Før lagring:
> 1. Kontroller at alle tre promptene er gjengitt ordrett og fullstendig, uten avkuttede ord eller setninger.
> 2. Rett eventuelle skrivefeil eller ufullstendige setninger i loggens egne beskrivelser. Ikke endre ordlyden i de faktiske promptene.
> 3. Behold loggen kort og i samsvar med eksisterende mal.
>
> Når kontrollen er gjennomført, lagre loggen som `docs/ki-logg/2026-11-05-ansvarsfordeling-logger.md`.
>
> Commit og push bare:
> - `docs/ki-logg/README.md`
> - `docs/ki-logg/2026-11-05-ansvarsfordeling-logger.md`
>
> Ikke endre faglærers sesjonslogg, `issues.md`, sesjonslogg-skillen, `CLAUDE.md`, `AGENTS.md` eller andre prosjektfiler.
>
> Vis commit-ID, resultatet av push og `git status -sb`.

</details>

## Hva KI leverte

- **Prompt 1:** En kartlegging av eksisterende praksis, en liste over mangler
  og forslag til ordlyd i `docs/ki-logg/README.md` og `CLAUDE.md`. Det kom
  også to spørsmål: om omfanget skal utvides fra kode til dokumentasjon, og om
  loggreglene skal flyttes til `AGENTS.md`.
- **Prompt 2:** En endring i `docs/ki-logg/README.md`: utvidet omfang i
  innledningen, en ny seksjon «Forholdet til andre logger» og en ny regel om
  dobbeltlogging. I tillegg ble «kodeøkt» endret til «økt» i første regel.
- **Prompt 3:** Utkastet til denne loggen.
- **Prompt 4:** En kontroll av promptene mot originalene og to språklige
  rettelser i loggens egne beskrivelser. Deretter ble loggen lagret, og den ble
  committet og pushet sammen med README (`8afac22`).

## Hva vi endret og hvorfor

- Endringen ble avgrenset til `docs/ki-logg/README.md`. Sesjonsloggen,
  `issues.md` og skillen er etablert av faglærer og skal ikke endres. Endringer
  i `CLAUDE.md` og `AGENTS.md` ble utsatt.
- Disse delene av forslaget ble forkastet: tabellen, skillet mellom
  beslutninger i KI-loggen og i `.memlog.md`, og setningen om at `issues.md`
  er per bruker. Grunnen var at README skulle holdes kort.
- Endringen av «kodeøkt» til «økt» i første regel ble beholdt, fordi regelen
  ellers ville motsagt den nye innledningen.

## Testing

Ikke testet. Endringen gjelder bare dokumentasjon. Diffen (`git diff`) og
Git-statusen ble vist og bekreftet at bare `docs/ki-logg/README.md` var endret.
Lars Tellef Risøy gikk gjennom diffen og godkjente endringen.
