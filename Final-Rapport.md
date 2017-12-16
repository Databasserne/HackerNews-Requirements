# Final Rapport for HackerNews Project
Group: Kasper Worm, Alexander Steen, Martin Karlsen & Jonas Simonsen
<br>
[Opgave beskrivelse forefindes her](https://github.com/datsoftlyngby/soft2017fall-lsd-teaching-material/blob/master/assignments/08-Project_report.md)

## Requirements, architecture, design and process
### System requirements
I vores Large System Development, skulle vi udvikle en klon af Hackernews. Det indebærer at systemet skulle have en række funktioner for at gøre det brugbart, disse er som følgende: <br>
Som gæst af systemet skal du have mulighed for at læse posts og comments, samt oprette dig som bruger og logge ind. <br>
Som bruger skal du have mulighed for at se posts og comments, samt selv oprette posts og comments, ydermere kan du også up- og down vote på posts og comments, dog med en restriktion på downvote, som kræver du har minimum 500 karma. Karma fås ved at dine posts eller comments bliver upvoted. Du skal også som bruger have muligheden for at logge af systemet. <br>
Ud over ovenstående, skulle der laves 3 “simulator” kald, som skulle give noget bestemt data hvis de blev kaldt, der skulle være et kald til at få systemets status(alive, down, update), et til at få sidst inputtet data, samt muligheden for at en “simulator” script kunne oprette posts og comments i systemet.<br>

#### Functional requirements
Systemet skal bygget som en webapplikation med et RESTful API til mellem front-end og back-end delen, da det skulle kunne tilgår fra en simulator. Følgende funktioner er grundalag for webapplikationens funktionalitet. 

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














### Development process


### Architecture diagram
her er vores filer i systemet
![Class-Diagram](https://github.com/Databasserne/HackerNews-Requirements/blob/master/Pictures/class-diagram.png)


