# vibly-registry

Provider-registret för Vibly, publicerat som en statisk fil via GitHub Pages:

```
https://elliotmarions.github.io/vibly-registry/providers.json
```

Vibly läser den var tolfte timme. Syftet är att en sajt som byter markup eller
endpoint ska kunna åtgärdas med en push här, i stället för med en ny version av
tillägget.

## Regler

**Bara data.** Match-mönster, selektorer och anteckningar — aldrig kod. En
fjärrhämtad fil som kunde köra något vore en bakdörr in i varje installation.
Tillägget validerar filen innan den används och avvisar den hellre än att låta
ett trasigt register tyst stänga av detektionen.

**Höj `version` vid varje ändring.** Tillägget har en bundlad kopia och använder
den med högst version. En fjärrfil med samma eller lägre version ignoreras — den
räknas som redan känd, inte som ett fel.

**Mönster måste ha schema.** `*://exempel.se/*`, inte `exempel.se/*`. Utan schema
matchar mönstret bredare än avsett, och valideringen avvisar det.

## Vad som händer när hämtningen misslyckas

Ingenting försämras. Det som redan finns ligger kvar, och tillägget faller
tillbaka på den bundlade filen. Registret behöver alltså aldrig vara uppe för att
Vibly ska fungera — det är en uppdateringsväg, inte ett beroende.
