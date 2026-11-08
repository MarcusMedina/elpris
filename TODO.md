# TODO

## Elpris-aviseringar i Android-appen

Skjutet till Android-appen. En statisk webbsida kan inte pusha när den är stängd.

**Gräns:** 1 kr/kWh. Föreslaget exkl. moms, samma bas som elprisetjustnu.se. Ska vara en inställning.

**Aviseringar**
- [ ] Nu under: priset gick precis från ≥ 1 till < 1
- [ ] Upp om en timme: < 1 nu men ≥ 1 om en timme
- [ ] Ner om en timme: ≥ 1 nu men < 1 om en timme

**Regler**
- "Om en timme" = intervallet som innehåller nu + 60 min.
- Dedupera, så samma händelse aldrig aviserar två gånger.
- Priskälla: `https://www.elprisetjustnu.se/api/v1/prices/ÅÅÅÅ/MM-DD_SE3.json` (15-minutersintervall).
- Morgondagens fil släpps cirka 13:00. Hämta idag och imorgon för att klara midnattsövergången.

**Testa**
- [ ] Hopp över gränsen, uppåt och nedåt
- [ ] Midnatt
- [ ] Sommar-/vintertid
- [ ] Saknad morgondagsdata
