# Security

## Threat modelling

### Assets
- <b>Database</b>
Databasen indeholder alt data som bruges i applicationen.<br/>
Det er ikke alt data som skal være tilgængeligt for alle, samt det er ikke alle som skal have mulighed for at rette data.

- <b>Specifikke endpoints</b>
Simulator endpoints burde være protected mod alle andre end Helge.<br/>
Der kan lægges nyt data ind i systemet, via disse endpoints, hvilket vi ikke vil have.

- <b>Server</b>
Serveren skal beskyttes så eventuelle hackere ikke kan lukke den eller ændre i systemet.

### Model
![TM](https://github.com/Databasserne/HackerNews-Requirements/blob/master/threat-model.PNG)

## Risk metrix
|          | Negligible | Marginal | Critical | Catastrophic |
| -------- | ---------- | -------- | -------- | ------------ |
| Certain  | High       | High     | Extreme  | Extreme      |
| Likely   | Moderate   | High     | High     | Extreme - <b>Database</b>     |
| Possible | Low        | Moderate - <b>Specifikke endpoints</b> | High     | Extreme      |
| Unlikely | Low        | Low      | Moderate | Extreme      |
| Rare     | Low        | Low      | Moderate | High -<b>Server</b>        |
## Operating group
Vi operere for gruppe e.<br/>
<br/>
Der har været problemer med gruppens system, som har haft lang responsetime (mellem 30-60 sekunder på et request).<br/>
Efter snak med gruppen har det vist sig at være problemer med deres database som har krævet for meget af CPU'ens ydeevne.<br/>
<br/>
#### DDOS
Vi har ikke kunne få OWTF til at fungerer på vores computere og vi har derfor måtte prøve at finde huller i systemet, uden OWTF.<br/>
Ved at lave request på deres simulator POST kald, kan vi se at der er åbent for alle IP'er til at poste stories ind i deres system.<br/>
Vi kan derfor konkluderer at systemet er sårbart over for DDOS angreb.<br/>

#### Authentication
Vi har fundet ud af at det er muligt at oprette stories, i systemet, uden at være logget ind, ved at bruge simulator post API'et:
``` /hackernews/post ```
Ved at skrive tilfældige usernames og passwords, kan vi stadig oprette stories.
