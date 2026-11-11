# 2026-11-05 — Presisering av særpreget i Product Brief og PRD

- **Deltakere:** Lars Tellef Risøy
- **KI-verktøy:** Claude Code med modellen Claude Opus 5.5 (`claude-opus-5-5`). Ingen BMAD-workflow eller underagenter ble brukt. ChatGPT (OpenAI) ble brukt til vurdering av forslagene og utforming av promptene.
- **Kontrollert av:** <fylles inn av gruppemedlemmet som har godkjent loggen>

## Oppgave

Vurdere og deretter gjennomføre en minimal presisering av særpreget i Product
Brief §4 og PRD §1, basert på Competitive Research fra 2026-11-04
(commit `e25b07e`). Ingen krav, funksjoner eller scope skulle endres.

## Prompt (ordrett)

Promptene er gjengitt ordrett og i rekkefølge. Claude Codes svar mellom
promptene er ikke tatt med.

<details>
<summary><strong>Prompt 1 – Vurdering av justeringer</strong> (2026-11-05)</summary>

> Competitive Research er nå ferdigstilt, dokumentert og pushet til origin/main (commit e25b07e).
>
> Vi skal gå videre med en avgrenset vurdering av nødvendige justeringer i Product Brief og PRD, basert på funnene.
>
> **Oppgave**
>
> 1. Kontroller Git-status og hent siste endringer fra origin på en trygg måte. Ikke overskriv arbeid fra andre gruppemedlemmer.
> 2. Les gjeldende Product Brief §4, PRD §1 og den ferdige Competitive Research-rapporten.
> 3. Vurder om særpreget bør presiseres i lys av researchen.
> 4. Presenter konkrete forslag til ny ordlyd for Product Brief §4 og eventuelt PRD §1.
> 5. Vis eksisterende og foreslått tekst side om side, med en kort begrunnelse for hver endring.
>
> **Føringer**
>
> - Fremhev den samlede arbeidsflyten fra ordre til kontrollert årshjul.
> - Legg vekt på kildeutdrag, sporbarhet, menneskelig kontroll og troppssjefens planleggingsbehov.
> - Nevn relevante konkurrenter som Plandisc og Microsoft Planner Agent.
> - Skill mellom spesifisert funksjonalitet og egenskaper som ennå ikke er testet.
> - Vurder om kostnadsfri demo-modus og militær tilpasning bør nevnes, men ikke overdriv betydningen av dem.
> - Ikke påstå at løsningen er teknologisk unik eller dokumentert bedre enn konkurrentene.
> - Behold Product Brief og PRD konsistente.
> - Ikke utvid MVP-scope, endre funksjonskrav eller legge til nye egenskaper.
>
> **Viktig**
>
> Dette er kun en vurderingsfase. Ikke endre noen filer ennå.
>
> Ikke start nye BMAD-workflows eller omfattende valideringsrunder. Ikke gjør ny Competitive Research.
>
> Presenter forslagene og din anbefaling, og stopp for min godkjenning.
>
> Ingen commit eller push.

</details>

<details>
<summary><strong>Prompt 2 – Minimal revisjon</strong> (2026-11-05)</summary>

> Jeg ønsker en minimal revisjon av Product Brief §4 og PRD §1 basert på Competitive Research. Dokumentene skal fortsatt være korte og presise, uten unødvendige gjentakelser.
>
> **Product Brief §4 – erstatt eksisterende avsnitt med:**
>
> Relevante alternativer er Excel, digitale årshjul som Plandisc og planleggingsverktøy som Microsoft Planner, Trello og Teams-kalender. Plandisc markedsfører KI-import fra dokumenter, mens Microsoft Planner Agent ifølge Microsoft kan generere planutkast fra Word-filer som brukeren bekrefter.
>
> Løsningens særpreg ligger i en samlet arbeidsflyt fra ordre til årshjul, der KI-genererte aktivitetsforslag kontrolleres mot kildeutdrag som applikasjonen verifiserer, og godkjennes enkeltvis før de legges inn i planen. Løsningen er tilpasset troppssjefens planleggingsbehov.
>
> **PRD §1 – erstatt bare tredje avsnitt med:**
>
> Eksisterende løsninger dekker allerede deler av arbeidsflyten. Vårt særpreg ligger i en samlet flyt fra ordre til årshjul, der KI-genererte aktivitetsforslag kontrolleres mot verifiserte kildeutdrag og godkjennes enkeltvis før de legges inn i planen. Brukeren har kontroll over hva som lagres.
>
> **Gjennomføring**
>
> 1. Kontroller Git-status og sikre at andre gruppemedlemmers arbeid ikke berøres.
> 2. Gjennomfør bare de to tekstendringene.
> 3. Behold PRD-status `final`, og oppdater kun nødvendig metadata og beslutningshistorikk.
> 4. Følg KI-loggrutinene, men hold loggføringen kort.
> 5. Vis en kort diff og bekreft at ingen nye krav eller scope-endringer er introdusert.
>
> Ikke endre UX, arkitektur eller funksjonskrav.
>
> Stopp før commit og push for godkjenning.

</details>

<details>
<summary><strong>Prompt 3 – Presisering av PRD §1</strong> (2026-11-05)</summary>

> Jeg har gjennomgått endringene og godkjenner Product Brief §4 slik den nå står.
>
> Før commit ønsker jeg én presisering i PRD §1:
>
> Endre «kontrolleres mot verifiserte kildeutdrag» til «kontrolleres mot kildeutdrag som applikasjonen verifiserer».
>
> Begrunnelsen er at PRD FR-27–FR-29 også tillater forslag med manglende eller ikke-verifiserte kildeutdrag, så lenge dette markeres tydelig.
>
> Behold alle øvrige tekstendringer uendret.
>
> **Loggføring**
>
> - Oppdater det korte KI-loggutkastet med denne siste presiseringen.
> - ChatGPT ble brukt til vurdering av forslagene og utforming av promptene, og skal føres opp som KI-verktøy.
> - Vis meg hele KI-loggutkastet før det lagres i repoet, slik at jeg kan godkjenne det.
> - Behold eksisterende rutiner for sesjonslogging, uten ekstra automatisk commit.
>
> Ikke endre andre prosjektfiler eller starte ny validering.
>
> Stopp før commit og push.

</details>

## Hva KI leverte

- Et forslag til ny ordlyd for Product Brief §4 og PRD §1, vist ved siden av eksisterende tekst og med begrunnelse.
- Etter gruppens beslutning ble gruppens egen, kortere ordlyd satt inn ordrett.
- PRD-ens `updated` ble satt til 2026-11-05, og status `final` ble beholdt. Beslutningen og den senere presiseringen er ført i PRD-ens `.memlog.md`.
- Claude Code påpekte to forhold før commit:
  - «verifiserte kildeutdrag» i PRD §1 kunne leses som at alle forslag har verifiserte kildeutdrag, i strid med FR-27–FR-29.
  - Setningen om manuell overføring ble fjernet fra briefen. Problemet er fortsatt beskrevet i §2.

## Hva vi endret og hvorfor

Vi valgte en kortere og mer minimal ordlyd enn KI-forslaget, slik at dokumentene
fortsatt er korte. Før commit endret vi «kontrolleres mot verifiserte
kildeutdrag» i PRD §1 til «kontrolleres mot kildeutdrag som applikasjonen
verifiserer». Grunnen er at FR-27–FR-29 også tillater forslag med manglende
eller ikke-verifiserte kildeutdrag, så lenge dette markeres tydelig. PRD §1 og
Product Brief §4 har nå samme ordlyd om dette.

Sammenligningen med Excel og forbeholdet om at effekten ennå ikke er testet,
står allerede i §6 (brief) og §9 (PRD), og ble derfor ikke gjentatt.
Konkurrentene nevnes med forbehold («markedsfører», «ifølge Microsoft»), så
briefen ikke fremsetter udokumenterte påstander om konkurrentenes
funksjonalitet.

## Testing

Ikke testet. Det er ingen kode. Kontrollen var `git diff --check`, en ordvis
diff og en manuell sammenligning mot FR-23 og FR-27–FR-29 for å bekrefte at
ingen krav eller scope er endret.
