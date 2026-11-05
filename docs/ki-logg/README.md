# KI-logg

Denne mappen dokumenterer hvordan gruppen bruker KI i utviklingen. Hver økt der
KI har bidratt til endringer i kode eller prosjektdokumentasjon får én loggfil.
Reglene gjelder alle gruppemedlemmer.

## Forholdet til andre logger

- **KI-logg (`docs/ki-logg/`):** KI-verktøy, prompter, hva KI leverte,
  menneskelig kontroll og relevante refleksjoner.
- **Sesjonslogg (`.logs/<bruker>/`):** kort om hva som ble gjort og hva som
  gjenstår, etter faglærers eksisterende rutine.
- **`issues.md`:** oppfølging av åpne punkter, etter samme rutine.
- **BMAD `.memlog.md`:** beslutningshistorikk for det aktuelle artefaktet.

## Regler

- Én fil per økt, navngitt `ÅÅÅÅ-MM-DD-tema.md`, for eksempel
  `2026-10-05-innlogging.md`. Bruk små bokstaver og bindestrek i temaet.
- Loggfør bare økter som faktisk har skjedd, og skriv oppføringen mens økten er
  fersk. Ikke lag oppføringer i ettertid om tidligere økter.
- Prompten gjengis ordrett. Er den for lang, kan irrelevante deler kuttes med
  `[...]`, men teksten som står igjen skal være uendret.
- Beskriv bare tester som faktisk ble kjørt. Er noe ikke testet, skriv det.
- KI kan foreslå en oppføring, men et gruppemedlem skal kontrollere og godkjenne
  den før den lagres.
- Unngå unødvendig dobbeltlogging: henvis til eksisterende logger i stedet for å
  gjenta detaljene som står der.

## Mal

Kopier malen under til en ny fil og fyll ut alle seksjonene.

```markdown
# ÅÅÅÅ-MM-DD — Tema

- **Deltakere:** <hvem i gruppen var med>
- **KI-verktøy:** <f.eks. Claude Code, Codex, modell>
- **Kontrollert av:** <gruppemedlem som har gått gjennom oppføringen>

## Oppgave

<Hva skulle vi få til i økten, og hvorfor?>

## Prompt (ordrett)

> <Lim inn prompten nøyaktig slik den ble skrevet. Ved flere prompter, list dem
> i rekkefølge.>

## Hva KI leverte

<Kort beskrivelse av forslaget eller koden KI produserte. Nevn berørte filer.>

## Hva vi endret og hvorfor

<Hvilke deler av KI-leveransen ble endret, forkastet eller beholdt, og
begrunnelsen for det.>

## Testing

<Hvordan resultatet ble testet: kommandoer, manuelle steg og utfall. Skriv
«Ikke testet» hvis ingen test ble gjort.>
```
