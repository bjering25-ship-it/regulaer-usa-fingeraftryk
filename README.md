# regulaer-usa-fingeraftryk

Offentligt fingeraftryksarkiv for USA-fondens beslutninger (Regulær Invest, USA som hjemmemarked).

Filen `beslutninger.csv` har én linje pr. beslutning i fondens beslutningslog: `nr` (postens nummer i logkæden), `registreret_utc`
(tidspunktet, beslutningen blev gemt, UTC) og `hash` (SHA-256, 64 hex-tegn). Hashen er beregnet som
`SHA-256(forrige_hash + "\n" + salt + "\n" + registreret_utc + "\n" + kanonisk)`, hvor `kanonisk` er beslutningens felter
som JSON med sorterede nøgler. Saltet og indholdet offentliggøres ikke; arkivet indeholder kun hashes. Senere kan en enkelt
beslutning bevises ved at offentliggøre dens indhold, salt og forrige hash.

Filen er kun-tilføj: linjer ændres eller slettes aldrig; nye beslutninger tilføjes til sidst.

## modanalyser.csv

Én linje pr. modanalyse (djævlens advokat og dommer efter fondens dybdeanalyse, S18): `id` (modanalysens nummer),
`registreret_utc` og `sha256` (fingeraftrykket af advokat.md, advokat.json, dom.md og dom.json: SHA-256 af linjerne
`<sha256>  <fil>` sorteret efter filnavn, som `sha256sum`). Modanalysen er en anbefaling til Henrik; den ændrer aldrig
forslaget. Filen er kun-tilføj som `beslutninger.csv`.
