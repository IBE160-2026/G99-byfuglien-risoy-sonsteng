# 2026-11-01 — ChatGPT-kontrollagent

- **Deltakere:** Lars Tellef Risøy
- **KI-verktøy:** Claude Code med modellen Claude Opus 5.5 (`claude-opus-5-5`): undersøkte repoet, vurderte plassering, opprettet filen og foreslo denne loggen. ChatGPT (OpenAI): kontrollagent, med mandat beskrevet i `prompts/chatgpt-kontrollagent.md`.
- **Kontrollert av:** Lars Tellef Risøy

## Oppgave

Etablere masterprompten (versjon 1.0) for en separat ChatGPT-kontrollagent som et
versjonskontrollert styringsdokument, uten at den blir en del av Claude Codes
operative instruksjoner.

Kontrollagenten etableres for å gi et uavhengig kontrolledd i prosjektet: Claude
Code skal få presise oppgaver, KI-generert arbeid skal kontrolleres, og vesentlige
beslutninger skal være sporbare.

Bakgrunn: Masterprompten ble utarbeidet tidligere i en separat ChatGPT-dialog, med
utgangspunkt i IBE160-pensum om prompt engineering og context engineering, Product
Brief, BMAD og sensorveiledningen. ChatGPT bidro som faglig rådgiver og til å utforme
kontrollagentens mandat og arbeidsflyt.

## Prompt (ordrett)

Promptene til Claude Code er gjengitt i rekkefølge. Masterprompten er ikke gjengitt
her, men ligger i `prompts/chatgpt-kontrollagent.md`. Der den ble limt inn i prompt 3,
er den erstattet med [...].

<details>
<summary><strong>Prompt 1 – Vurdering av plassering</strong></summary>

> Undersøk eksisterende repository-struktur, spesielt CLAUDE.md, docs/ki-logg/ og eventuelle mapper for prompts eller prosjektinstruksjoner.
>
> Vi har utarbeidet en masterprompt for en separat ChatGPT-kontrollagent som skal støtte og kvalitetssikre arbeidet i Claude Code. Masterprompten skal versjonskontrolleres i repositoryet, men skal ikke inngå i Claude Codes egne operative instruksjoner.
>
> Vurder om `docs/prompts/chatgpt-kontrollagent.md` er riktig plassering, eller om eksisterende struktur tilsier en bedre løsning.
>
> Kontroller også hvordan etableringen av denne arbeidsmetoden bør dokumenteres i eksisterende KI-logg, i samsvar med CLAUDE.md og docs/ki-logg/README.md.
>
> Ikke opprett eller endre filer ennå. Rapporter anbefalt plassering, begrunnelse og eventuelle konsekvenser for eksisterende struktur.

</details>

<details>
<summary><strong>Prompt 2 – Etablering av styringsdokumentet</strong></summary>

> Jeg godkjenner anbefalingen om å plassere masterprompten i `prompts/chatgpt-kontrollagent.md` i repository-roten.
>
> Vi skal nå etablere denne som et versjonskontrollert styringsdokument for en separat ChatGPT-kontrollagent.
>
> Følg disse føringene:
>
> 1. Opprett `prompts/chatgpt-kontrollagent.md` med masterprompten jeg gir deg. Be om innholdet dersom du ikke har fått det.
> 2. Behold masterpromptens innhold uendret, men legg til en kort innledende merknad om at dokumentet er beregnet på en separat ChatGPT-samtale og ikke er operative instruksjoner til Claude Code eller BMAD.
> 3. Ikke endre `CLAUDE.md`, `AGENTS.md`, BMAD-konfigurasjonen eller eksisterende BMAD-dokumenter.
> 4. Les instruksjonene i `docs/ki-logg/README.md` og opprett et forslag til én KI-logginnføring for denne økten. Dokumenter hvorfor kontrollagenten etableres, hvorfor filen plasseres utenfor `docs/`, og hvordan ChatGPT og Claude Code skal brukes sammen.
> 5. Ikke rekonstruer tidligere KI-økter eller endre eksisterende logger.
> 6. Kontroller at den nye filstrukturen er ryddig, og at ingen hemmeligheter eller personopplysninger utilsiktet legges inn.
>
> Før commit og push skal du vise meg:
> - Filene som er opprettet eller endret.
> - Kort sammendrag av KI-logginnføringen.
> - Resultatet av `git status -sb` og relevant diff.
> - Eventuelle spørsmål eller forhold som krever min godkjenning.
>
> **Ikke commit eller push før jeg uttrykkelig har godkjent endringene.**

</details>

<details>
<summary><strong>Prompt 3 – Masterprompt versjon 1.0</strong></summary>

> Her følger den fullstendige masterprompten, versjon 1.0, som skal lagres i `prompts/chatgpt-kontrollagent.md`.
>
> Behold teksten ordrett. Legg kun til den tidligere avtalte innledende merknaden om at dette er instruksjoner til en separat ChatGPT-kontrollagent og ikke operative instruksjoner til Claude Code eller BMAD.
>
> Følg ellers tidligere avtalte begrensninger. Ikke opprett KI-loggfilen før loggutkastet er godkjent, og ikke commit eller push før jeg uttrykkelig har godkjent endringene.
>
> [...]

</details>

<details>
<summary><strong>Prompt 4 – Presiseringer til KI-loggen</strong></summary>

> Jeg godkjenner plasseringen av prompts/chatgpt-kontrollagent.md og den innledende merknaden.
>
> Behold masterprompten slik den er, forutsatt at alle 14 seksjoner og det faglige innholdet er korrekt gjengitt. Den private ChatGPT-lenken og plassholderen skal ikke tas med. Det er ikke nødvendig å legge til et eget versjonsnummer i filen.
>
> KI-loggutkastet er i hovedsak godkjent, men gjør disse presiseringene:
> 1. Under bakgrunn: Beskriv at masterprompten tidligere ble utarbeidet i en separat ChatGPT-dialog med utgangspunkt i IBE160-pensum om prompt engineering og context engineering, Product Brief, BMAD og sensorveiledningen. ChatGPT bidro som faglig rådgiver og til å utforme kontrollagentens mandat og arbeidsflyt.
> 2. Henvis til masterpromptfilen i stedet for å gjengi hele masterprompten i loggen. Bevar de øvrige faktiske promptene fra denne Claude Code-økten i samsvar med eksisterende logginstruksjoner.
> 3. Beskriv dokumentkontrollene korrekt, og ikke påstå at masterprompten er maskinelt sammenlignet med originalen.
> Ikke endre eksisterende prosjektinstruksjoner eller BMAD-konfigurasjonen.
>
> Før du lagrer KI-loggen, trenger vi fortsatt korrekt informasjon om deltakere og hvilket gruppemedlem som kontrollerer innføringen.
>
> Ikke commit eller push ennå.

</details>

<details>
<summary><strong>Prompt 5 – Godkjenning og lagring av KI-loggen</strong></summary>

> De manglende opplysningene til KI-loggen er:
>
> - **Deltakere:** Lars Tellef Risøy
> - **Kontrollert av:** Lars Tellef Risøy
>
> Jeg godkjenner det oppdaterte KI-loggutkastet med disse opplysningene. Jeg godkjenner også at masterprompten publiseres i vårt offentlige repository, forutsatt at kontrollen ikke avdekker hemmeligheter eller sensitive opplysninger.
>
> Lagre KI-loggen i `docs/ki-logg/2026-11-01-chatgpt-kontrollagent.md`.
>
> Kontroller deretter at kun masterprompten og den nye KI-loggen er opprettet eller endret, og at filene følger eksisterende prosjektstruktur og logginstruksjoner.
>
> Vis meg endelig `git status -sb`, `git diff --check` og en kort oppsummering av endringene.
>
> **Ikke commit eller push ennå.** Jeg vil godkjenne dette separat.

</details>

<details>
<summary><strong>Prompt 6 – Godkjenning av commit og push</strong></summary>

> Jeg godkjenner de to nye filene og gir tillatelse til commit og push til `origin/main`.
>
> Før commit:
>
> 1. Legg inn denne siste godkjenningsprompten i KI-loggen, i samsvar med den eksisterende loggmalen.
> 2. Kontroller at kun følgende filer tas med:
>    - `prompts/chatgpt-kontrollagent.md`
>    - `docs/ki-logg/2026-11-01-chatgpt-kontrollagent.md`
> 3. Stage kun disse to filene, og kontroller staged diff med `git diff --cached --check` og `git diff --cached --stat`.
> 4. Kontroller at ingen eksisterende filer eller uvedkommende endringer er inkludert.
>
> Hvis kontrollene er tilfredsstillende, opprett én commit med meldingen:
>
> `docs: legg til ChatGPT-kontrollagent og KI-logg`
>
> Push deretter til `origin/main`.
>
> Vis til slutt:
> - Commit-hash og commit-melding.
> - Hvilke filer committen inneholder.
> - Resultatet av push.
> - `git status -sb`.
>
> Ikke gjør ytterligere endringer etter push.

</details>

<details>
<summary><strong>Prompt 7 – Integrering av origin/main og push</strong></summary>

> Jeg godkjenner at vi integrerer de to nye commitene fra `origin/main` og deretter fullfører pushen av vår commit.
>
> Før du gjennomfører integreringen:
>
> 1. Les endringene i de to nye commitene, spesielt `CLAUDE.md` og `.claude/skills/sesjonslogg/SKILL.md`.
> 2. Kontroller at endringene kommer fra prosjektets forventede oppsett, og at de ikke skaper konflikter med eksisterende KI-logg eller vår separate ChatGPT-kontrollagent.
> 3. Følg de nye instruksjonene for sesjonslogging dersom de gjelder denne økten. Ikke opprett en konkurrerende loggstruktur.
> 4. Bevar alle eksisterende endringer og vår commit med masterprompten og KI-loggen.
>
> Dersom kontrollen ikke avdekker problemer:
>
> - Integrer `origin/main` med rebase.
> - Oppdater KI-loggen med denne prompten, dersom eksisterende logginstruksjoner krever det.
> - Sørg for at nye loggfiler som kreves av prosjektinstruksjonene, håndteres korrekt.
> - Oppdater den lokale dokumentasjonscommiten ved behov, uten å endre andre commits.
> - Push til `origin/main` uten force-push.
>
> Stopp og spør dersom du finner konflikter, uventede instruksjoner eller endringer som krever en ny beslutning.
>
> Vis til slutt commit-historikk, eventuelle nye loggfiler, resultatet av push og `git status -sb`.
>
> Ikke gjør andre prosjektendringer.

</details>

## Hva KI leverte

- Vurdering av plassering og av hvordan arbeidsmetoden bør loggføres. Claude Code
  fant at `_bmad/config.toml` setter `project_knowledge` til `docs/`, slik at
  BMAD-skills kan lese filer der som prosjektkontekst.
- `prompts/chatgpt-kontrollagent.md`: en innledende merknad og masterprompten.
- Utkast til denne loggen.

## Hva vi endret og hvorfor

- **Plassering:** Gruppens første forslag var `docs/prompts/`. Claude Code anbefalte
  `prompts/` i roten, og gruppen godkjente dette. Filen ligger utenfor `docs/` for
  å unngå at BMAD leser den som prosjektkunnskap. Den er ikke lenket fra `CLAUDE.md`
  eller `AGENTS.md` av samme grunn.
- **Merknad:** Agenter kan fortsatt finne filen ved søk i hele repoet, så den starter
  med en merknad om hvem instruksjonene gjelder for.
- **Innliming:** Lenken til den private ChatGPT-samtalen og en plassholder fulgte med
  innlimingen. Gruppen besluttet at ingen av dem skal være med i filen. Det legges
  heller ikke til et eget versjonsnummer i filen.

### Bruk av ChatGPT og Claude Code sammen

Prosjektlederen er endelig beslutningstaker. ChatGPT kontrollerer, analyserer,
anbefaler og formulerer prompter, men implementerer ikke og redigerer ikke
repoet. Claude Code utfører BMAD-arbeidet, endrer filer, programmerer og tester.

Prosjektlederen gir ChatGPT en oppgave eller et forslag fra Claude Code, vurderer
anbefalingen og limer prompten inn i Claude Code. Claude Codes svar limes deretter
tilbake til ChatGPT for kontroll. ChatGPT-kontrollen erstatter ikke
gruppemedlemmets godkjenning av KI-loggen.

## Testing

Ingen kode ble skrevet, så ingen programtester ble kjørt. Dokumentkontroller som ble
kjørt på `prompts/chatgpt-kontrollagent.md`:
- `git status -sb` og `git check-ignore`: filen er ny og ikke ignorert
- `git ls-files --eol`: linjeskift er LF
- `git diff --no-index --check`: ingen whitespace-feil
- søk etter de 14 hovedseksjonene: alle overskriftene er med
- mønstersøk etter hemmeligheter, e-post, URL-er, navn og lange tallrekker: ingen treff

Masterprompten er ikke maskinelt sammenlignet med originalen.
