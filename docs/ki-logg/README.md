# KI-logg

Denne mappen dokumenterer hvordan gruppen bruker KI i utviklingen. Hver kodeøkt
der KI har bidratt til endringer i koden får én loggfil.

## Regler

- Én fil per kodeøkt, navngitt `ÅÅÅÅ-MM-DD-tema.md`, for eksempel
  `2026-10-05-innlogging.md`. Bruk små bokstaver og bindestrek i temaet.
- Loggfør bare økter som faktisk har skjedd, og skriv oppføringen mens økten er
  fersk. Ikke lag oppføringer i ettertid om tidligere økter.
- Prompten gjengis ordrett. Er den for lang, kan irrelevante deler kuttes med
  `[...]`, men teksten som står igjen skal være uendret.
- Beskriv bare tester som faktisk ble kjørt. Er noe ikke testet, skriv det.
- KI kan foreslå en oppføring, men et gruppemedlem skal kontrollere og godkjenne
  den før den lagres.

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
