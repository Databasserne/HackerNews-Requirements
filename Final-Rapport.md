# Final Rapport for HackerNews Project
Group: Kasper Worm, Alexander Steen, Martin Karlsen & Jonas Simonsen
<br>
[Opg. Beskrivelse](https://github.com/datsoftlyngby/soft2017fall-lsd-teaching-material/blob/master/assignments/08-Project_report.md)

## Requirements, architecture, design and process
### System requirements
I Hackernews projektet skulle vi udvikle en klon af Hackernews. Systemet skulle have en række features for at gøre det brugbart, disse er:
Som gæst af systemet skal du have mulighed for at læse posts og comments, samt oprette dig som bruger og logge ind.
Som bruger skal du have mulighed for at se posts og comments, samt selv oprette posts og comments, yderligere kan du også up/down vote på post og comments, med en restriktion på downvote, som kræver du har 500 karma, som fås ved at blive upvoted. Du skal også som bruger have muligheden for at logge af systemet.
Ud over ovenstående, skulle der laves 3 “simulator” kald, som skulle give noget bestemt data hvis de blev kaldt, der skulle være et kald til at få systemets status(alive, down, update), et til at få sidst inputtet data, samt muligheden for at en “simulator” script kunne oprette posts og comments i systemet.
Til at give et bedre overblik over hvordan systemet skulle opbygget og hvem der skulle kunne hvad, valgte vi at lave en use case model, hvor vi har de forskellige mulige bruger af systemet, altså som tidligere nævnt en guest, en user og en simulator, derefter lavede vi pile hen til de forskellige funktioner som er beskrevet, nogle funktioner skal så have andre krav opfyldt for at kunne bruges det er så der vi bruger extends. 
På samme måde er der også funktioner som giver mulighed for at få noget, her bruger vi include til at illustrere dette. Vores use case model endte med at se ud som følgende.
<br>
![use case model](https://github.com/Databasserne/HackerNews-Requirements/blob/master/Pictures/UseCaseDiagram.png)



### Architecture diagram
her er vores filer i systemet
![Class-Diagram](https://github.com/Databasserne/HackerNews-Requirements/blob/master/Pictures/class-diagram.png)


