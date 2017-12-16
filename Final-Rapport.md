# Final Rapport for HackerNews Project
Group: Kasper Worm, Alexander Steen, Martin Karlsen & Jonas Simonsen
<br>
[Opgave beskrivelse forefindes her](https://github.com/datsoftlyngby/soft2017fall-lsd-teaching-material/blob/master/assignments/08-Project_report.md)

## 1 Requirements, architecture, design and process
### 1.1 System requirements
I vores Large System Development, skulle vi udvikle en klon af Hackernews. Det indebærer at systemet skulle have en række forskellige typer brugere med forskellige funktioner for at gøre det brugbart, disse er som følgende: <br>
Som gæst af systemet skal du have mulighed for at læse posts og comments, samt oprette dig som bruger og logge ind. <br>
Som bruger skal du have mulighed for at se posts og comments, samt selv oprette posts og comments, ydermere kan du også up- og down vote på posts og comments, dog med en restriktion på downvote, som kræver du har minimum 500 karma. Karma fås ved at dine posts eller comments bliver upvoted. Du skal også som bruger have muligheden for at logge af systemet. <br>
Ud over ovenstående, skulle der laves 3 “simulator” kald, som skulle give noget bestemt data hvis de blev kaldt, der skulle være et kald til at få systemets status(alive, down, update), et til at få sidst inputtet data, samt muligheden for at en “simulator” script kunne oprette posts og comments i systemet.<br>

#### Functional requirements
Systemet skal bygget som en webapplikation med et RESTful API til mellem front-end og back-end delen, da det skulle kunne tilgås fra en simulator. Følgende funktioner er grundalag for webapplikationens funktionalitet. 

* Login
* Opret profil
* Oprette post
* Se post
* Slette egne post
* Redigere egne post
* Upvote post
* Downvote post (hvis man har min. 500 karma)
* Skrive kommentar
* Upvote kommentar
* Downvote kommentar (hvis man har min. 500 karma)
* Få karma
* Logud
* Se status

Til at give et bedre overblik over hvordan systemet skulle opbygget og hvilken type bruger der skulle kunne hvad, valgte vi at lave en use case model, hvor vi har de forskellige bruger af systemet, altså som tidligere nævnt en guest, en user og en simulator, derefter lavede vi pile hen til de forskellige funktioner som er beskrevet, nogle funktioner skal så have andre krav opfyldt for at kunne bruges det er så der vi bruger *extends*. 
På samme måde er der også funktioner som giver mulighed for at få noget, her bruger vi *include* til at illustrere dette. Vores use case model endte med at se ud som følgende.

![use case model](https://github.com/Databasserne/HackerNews-Requirements/blob/master/Pictures/UseCaseDiagram.png)

#### Nonfunctional requirements
Systemet skal have en oppetid på minimum 95% og må på intet tidspunkt miste nogen form for data. I løbet af udviklingsperioden vil en simulator konstant sende request til systemet. 

### 1.2 Development process

Overordnet set har vi arbejdet med en agil tilgang, hvor vores sprints er delt ind uge for uge med de opgaver vi har stillet. Men den typiske tilgang hvor hver udvikler laver alt fra test til backend til frontend har vi ikke brugt, da vi har haft en som primært fokuserede på frontend delen og de 3 andre havde størst fokus på backend
Vi har også benyttet os af TDD (Test-Driven-Development) i en del af systemet, men da vi blev tidspresset blev der skåret ned på det. TDD går ud på at man skriver tests før man begynder at implementere sine features, dette kan hjælpe en til at holde fokus på kun at implementere den ene feature, og målet er at gøre det på så kort en måde som muligt for at få ens test til at lyse grønt/succes.
En typisk TDD process er som følgende: (1) Skriv en test. (2) Kør testen, observer at den fejler da koden ikke er implementeret. (3) Implementer koden. (4) Kør testen igen, hvis den lykkes, fedt! gå videre. Hvis den fejler, skriv koden om til testen lykkes. (5) Refactor koden og test ved hvert refactor step, for at være sikker på intet er gået i stykker. (6) Gentag igen med en ny feature. 
Ved brug af TDD har vi løbende opdaget fejl, som vi ellers ikke ville have opdaget. Dette er f.eks. SQL query fejl, som ikke compiles og dermed ikke giver fejl når projektet køres.
Udover SQL fejl, har TDD også hjulpet os med at holde os på sporet, i forhold til de requirements der er til opgaven. Da testen skrives før metoden, har vi skulle tænke på hvad det rent faktisk er, som metoden skal gøre. Man kan dermed ikke tilpasse testen, så den passer til koden, men vi er derimod blevet tvunget til at tilpasse koden, så den har passet til testen, og derved bliver grøn.

### 1.3. Software architecture

Vi har valgt at dele vores projekt op i 3 dele. Vores frontend, som er systemets design udadtil, backenden som er control-laget, hvor alt funktionaliteten er og så vores database som er datalaget og der alt data gemmes.
Der er en forbindelse mellem front-end og back-end, samt en forbindelse mellem back-end og datalaget. Man kan altså ikke kalde datalaget, direkte fra front-end’en.
Forbindelsen mellem frontend og backend, består af REST api’er. Her er der nogle definerede protokoller som både frontend og backend skal overholde. Disse protokoller blev defineret, før starten på projektet.
Ved forbindelsen mellem backend og datalaget bruges der JPA, som omdanner data’en til models i vores backend.
Ved at bygge programmet op på denne måde, opnår vi en 3 lags arkitektur. Med en 3 lags arkitektur gør vi programmet mere overskueligt, og vi har på et hvilket som helst tidspunkt, mulighed for at bytte en af vores lag ud med et nyt, hvilket gør selve systemet væsentligt nemmere at vedligeholde og fornye hvis man ønsker at prøve f.eks. nye teknologier af.<br> 

HUSK 3 LAGS MODEL <br>
DESIGNCLASS-DIAGRAM <br>

Billedet viser vores forskellige klasser i deres respektive packages og hvilke andre klasser de implementere. Vores system er bygget op på den måde at når der bliver modtaget et request følger den klasserne “ned gennem systemet”, som er prøvet at illustreres på billedet ved at have det i en vertical position. Først bliver kaldet modtaget i .resource packagen, som sender det videre til .service packagen som igen sender det videre til .repo som så håndtere det og opretter det i databasen.
Alt efter hvilken type kald det er, vil de respektive klasser, baseret på klasse navnet, håndtere requested ned gennem systemet, da vi har holdt en bestemt navne struktur der har gjort dette nemt for os.


### Architecture diagram
her er vores filer i systemet
![Class-Diagram](https://github.com/Databasserne/HackerNews-Requirements/blob/master/Pictures/class-diagram.png)


