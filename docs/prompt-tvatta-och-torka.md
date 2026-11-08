# Prompt: Tvätta och torka

Klistra in texten under strecket som första meddelande i en ny session.

---

Jag vill bygga en ny liten webbsida, "Tvätta och torka", som kombinerar elpris och väder. Den ska tala om när det är bäst att köra tvättmaskinen och när tvätten torkar ute. Svara på svenska, var kort och rak, och planera upplägget med mig innan du bygger.

BAKGRUND
Jag har byggt en liknande sida, "Elpris", i repot MarcusMedina/elpris (publik, GitHub Pages: marcusmedina.github.io/elpris/). Lägg till det repot i sessionen och läs index.html. Återanvänd det som passar:
- Hämtning av elpriser från elprisetjustnu.se (https://www.elprisetjustnu.se/api/v1/prices/ÅÅÅÅ/MM-DD_SE3.json, kvartspriser, elområde SE3)
- Sparar senaste lyckade hämtning i localStorage och hämtar högst var 10:e minut
- Algoritm för bästa startfönster (tidsviktat snitt över programtiden, med lucktäckning)
- Diagram, kr/kWh med två decimaler, ljust och mörkt tema, Pages-publicering

NYTT I DEN HÄR SIDAN
- Väderdata för Kungsbacka (ca 57,49 N, 12,08 E), förslagsvis SMHI:s öppna prognos-API. Verifiera först att API:et finns, vilken version som gäller, att det inte kräver nyckel och att det tillåter anrop från webbläsare (CORS). Om inte behövs ett mellansteg, så säg det innan vi bygger.
- Plats: knapp "Använd min plats" (navigator.geolocation.getCurrentPosition, med timeout och felhantering för nekad/otillgänglig plats). Standardplats Kungsbacka. Avrunda koordinater till två decimaler och spara bara i localStorage. Visa tydligt vilken plats som används och låt användaren byta tillbaka. Hantera att prognos-API:et inte täcker positionen. Elområdet väljs fortfarande manuellt.
- Föreslå vilka regler som avgör "torkar ute" (regn, nederbördssannolikhet, luftfuktighet, vind, temperatur) och visa dem öppet.
- Ge ett samlat råd: kör maskinen nu eller senare, och när det går att hänga ut. Visa gärna hur elpris och väder samspelar i en tidslinje.

SAKER JAG HAR LÄRT MIG
- Sandlådans shell och WebFetch når inte elprisetjustnu.se, och troligen inte SMHI heller. Testa logiken mot fixturer, och jag kontrollerar i webbläsaren.
- En Claude-artefakt får inte anropa externa sajter, så sidan ska vara en fristående HTML-fil som publiceras via GitHub Pages.
- Du kan inte skapa repon. Jag skapar ett tomt publikt repo och ger Claude-appen åtkomst under github.com/settings/installations (Repository access) innan du pushar.
- Pages: Source ska vara "Deploy from a branch" → main / root. Första bygget startar först vid en push efter att Pages slagits på.
- Gör ingen "Installera"-knapp. Det utlöste Play Protect-varning på en Samsung. Dela-knapp och GitHub-länk längst ner är bra.

FÖRST
1. Kontrollera väder-API:et (nyckel, CORS, format).
2. Föreslå arkitektur och reglerna för "torkar ute", så godkänner jag innan du bygger.
