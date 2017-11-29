# Security

## Threat modelling

### Assets
- <b>Database</b>
Databasen indeholder alt data som bruges i applicationen.<br/>
Det er ikke alt data som skal være tilgængeligt for alle, samt det er ikke alle som skal have mulighed for at rette data.

- <b>Specifikke endpoints</b>
Simulator endpoints burde være protected mod alle andre end Helge.<br/>
Der kan lægges nyt data ind i systemet, via disse endpoints, hvilket vi ikke vil have.

### Table
|          | Negligible | Marginal | Critical | Catastrophic |
| -------- | ---------- | -------- | -------- | ------------ |
| Certain  | High       | High     | Extreme  | Extreme      |
| Likely   | Moderate   | High     | High     | Extreme - <b>Database</b>     |
| Possible | Low        | Moderate - <b>Specifikke endpoints</b> | High     | Extreme      |
| Unlikely | Low        | Low      | Moderate | Extreme      |
| Rare     | Low        | Low      | Moderate | High         |
