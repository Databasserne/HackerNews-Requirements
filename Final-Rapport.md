# Final Rapport for HackerNews Project

Group: Kasper Worm, Alexander Steen, Martin Karlsen & Jonas Simonsen
<br>
[Opgave beskrivelse forefindes her](https://github.com/datsoftlyngby/soft2017fall-lsd-teaching-material/blob/master/assignments/08-Project_report.md)

## 0 Introduction

I dette semester i Large System Development skulle vi implementere et system som skulle være en kopi af det allerede eksisterende system hackernews, med nogle af de samme features som det rigtige system. Det skulle være en introduction til at arbejde med systemer med stor brugerbase og mange requests i minuttet, som giver indblik i hvordan den virkelige verden er samt hvordan forløbet ser ud efter du har udviklet et projekt og du skal til at vedligeholde det, med hvordan du sætter monitoring op samt fixe problemer der vil opstå.

## 1 Requirements, architecture, design and process
### 1.1 System requirements

Hackernews er et socialt netværk for IT-entusiaster hvor brugere kan lave posts og comments på disse for at snakke om deres IT relaterede emner.

Vores opgave er at lave en HackerNews klon, som kan håndtere forskellige typer brugere med forskellige funktioner.
<br>
Funktionaliteten af systemet er som følgende: 
<br>
Som gæst af systemet skal du have mulighed for at læse posts og comments, samt oprette dig som bruger og logge ind. 
<br>
Som bruger skal du have mulighed for at se posts og comments, samt selv oprette posts og comments, ydermere kan du også up- og down vote på posts og comments, dog med en restriktion på downvote, som kræver du har minimum 500 karma. Karma fås ved at dine posts eller comments bliver upvoted. Du skal også som bruger have muligheden for at logge af systemet. 
<br>
Ud over ovenstående, skulle der laves 3 “simulator” kald, som skulle give noget bestemt data hvis de blev kaldt, der skulle være et kald til at få systemets status(alive, down, update), et til at få sidst inputtet data, samt muligheden for at en “simulator” script kunne oprette posts og comments i systemet.<br>

#### Functional requirements

Systemet skal bygges som en webapplikation med et REST API til mellem front-end og back-end delen, da det skulle kunne tilgås fra en simulator. Følgende funktioner er grundalag for webapplikationens funktionalitet. 

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

Til at give et bedre overblik over hvordan systemet skulle opbygges samt hvilken type bruger der skulle kunne hvad, valgte vi at lave en use case model, hvor vi har de forskellige bruger af systemet, altså som tidligere nævnt en guest, en user og en simulator. 
Derefter lavede vi pile hen til de forskellige funktioner som er beskrevet, nogle funktioner skal så have andre krav opfyldt for at kunne bruges, her bruger vi *extends*. 
På samme måde er der også funktioner som giver mulighed for at få noget, her bruger vi *include* til at illustrere dette. Vores use case model ser ud som følgende.

![use case model](https://github.com/Databasserne/HackerNews-Requirements/blob/master/Pictures/UseCaseDiagram.png)

#### Nonfunctional requirements

Der er også en række nonfunctional requirements til systemet. 

* Systemet skal have en oppetid på minimum 95%
* Systemet må på intet tidspunkt miste nogen form for data.  

### 1.2 Development process

Overordnet set har vi arbejdet med en agil tilgang, hvor vores sprints er delt ind uge for uge med de opgaver vi har fået stillet. Men den typiske tilgang hvor hver udvikler laver alt fra test til backend til frontend har vi ikke brugt, da vi har haft en som primært fokuserede på frontend delen og de 3 andre havde størst fokus på backend.

Vi har også benyttet os af TDD (Test-Driven-Development) i en del af systemet, men da vi blev tidspresset blev der skåret ned på det. TDD går ud på at man skriver tests før man begynder at implementere funktionerne. 
Dette kan hjælpe en til at holde fokus på kun at implementere det nødvendige, og målet er at gøre det på så kort en måde som muligt for at få ens test til at lyse grønt/succes.

En typisk TDD process er som følgende: 
1. Skriv en test. 
2. Kør testen, observer at den fejler da koden ikke er implementeret. 
3. Implementer koden. 
4. Kør testen igen, hvis den lykkes, fedt! gå videre. Hvis den fejler, skriv koden om til testen lykkes. 
5. Refactor koden og test ved hvert refactor step, for at være sikker på intet er gået i stykker. 
6. Gentag igen med en ny funktion. 

Ved brug af TDD har vi løbende opdaget fejl, som vi ellers ikke ville have opdaget. Dette er f.eks. SQL query fejl, som ikke compiles og dermed ikke giver fejl når projektet køres.
Udover SQL fejl, har TDD også hjulpet os med at holde os på sporet, i forhold til de requirements der er til opgaven. 
Da testen skrives før metoden, har vi skulle tænke på hvad det rent faktisk er, som metoden skal gøre. Man kan dermed ikke tilpasse testen, så den passer til koden, men vi er derimod blevet tvunget til at tilpasse koden, så den har passet til testen, og derved bliver grøn.

### 1.3. Software architecture

Vi har valgt at dele vores projekt op i 3 dele. Vores frontend, som er systemets design udadtil, backenden som er control-laget, hvor alt funktionaliteten er og så vores database som er datalaget og der alt data gemmes.
Der er en forbindelse mellem front-end og back-end, samt en forbindelse mellem back-end og datalaget. Man kan altså ikke kalde datalaget, direkte fra front-end’en. 

![3 lags diagram](https://github.com/Databasserne/HackerNews-Requirements/blob/master/Pictures/3lags.png)

Forbindelsen mellem front-end og back-end, består af REST API’er. Her er der nogle definerede protokoller som både front-end og back-end skal overholde. Disse protokoller blev defineret, før starten på projektet og kan findes [her](https://github.com/Databasserne/HackerNews-Requirements/blob/master/README.md#api-documentation).
Ved forbindelsen mellem back-end og datalaget bruges der JPA, som omdanner data’en til models i vores back-end.
Ved at bygge programmet op på denne måde, opnår vi en 3 lags arkitektur. Med en 3 lags arkitektur gør vi programmet mere overskueligt, og vi har på et hvilket som helst tidspunkt, mulighed for at bytte en af vores lag ud med et nyt, hvilket gør selve systemet væsentligt nemmere at vedligeholde og fornye hvis man ønsker at prøve f.eks. nye teknologier af.
<br> 

![Class-Diagram](https://github.com/Databasserne/HackerNews-Requirements/blob/master/Pictures/class-diagram.png)

Billedet ovenfår viser vores forskellige klasser i deres respektive packages og hvilke andre klasser de implementere. 
Vores system er bygget op på den måde at når der bliver modtaget et request følger den klasserne “ned gennem systemet”, som er illustreret på billedet ved at have det i en vertical position. 
Først bliver kaldet modtaget i .resource packagen, som sender det videre til .service packagen som igen sender det videre til .repo som så håndtere det og opretter det i databasen.

Alt efter hvilken type kald det er, vil de respektive klasser, baseret på klasse navnet, håndtere requested ned gennem systemet, da vi har holdt en bestemt navne struktur der har gjort dette nemt for os.

### 1.4. Software design

Før vi startede projektet havde vi en klar idé om hvordan arkitekturen i vores system skulle se ud. Vi vidste at vi ville køre alle containerne i docker og vi havde også en klar idé om at vi ville bruge JPA samt en MySQL database, da det var det som vi havde størst kendskab til.
Derudover vidste vi at vi ville kører back-end delen på en Tomcat server og at vi ville bruge React til front-end delen.

### 1.5. Software implementation

Selve implementeringen af systemet gik overordnet set som vi forventede, vi har dog haft nogle ting som vi blev en smule overrasket over og vi derfor valgte at bruge en anden løsning. 
Under opsætningen af systemet havde vi først tænkt os at bruge en Tomcat webserver, vi fandt dog hurtigt ud af at det tog alt for lang tid at bygge, op til 5 min, så vi valgte derfor at se på hvad vi ellers havde af muligheder, vi endte med en Jetty webserver i stedet for, ved at lave dette skift i webserver delen kom vi ned på en byggetid af systemet på ca. 30 sekunder, hvilket er en klar forbedring i forhold til vores tidligere Tomcat webserver. 
Udover vores webserver, havde vi et problem med vores servers ressourcebehov, et par gange under forløbet, da vi løb tør for memory til at køre vores projekt, samt Jenkins, og monitorerings værktøjerne. Dette resulterede i at vi opgradere vores DigitalOcean (DO) server, først til at være større, men senere hen, igen til at have flere droplets fra DO, som blev brugt til deres fulde da vi implementerede Docker swarm senere i forløbet.

Vi valgte at benytte Docker da det ville fungere godt i vores situation, det er mere lightweight end en virtual maskine, idet den har færre ting med fra start af. Senere i forløbet når vi skulle skalere systemet og blev introduceret til Docker-swarm bekræftede det blot vores valg i at fortsætte med Docker.
I kan læse mere her om hvordan vores Docler-svarm setup endte med at [se ud](https://github.com/Databasserne/HackerNews-Requirements/blob/master/scaling.md) 
<br>
Selve implementeringen af koden har vi ikke haft nogle ændringer i, fra hvad vi havde i tankerne fra start af. Vi havde en meget klar tilgang til hvad og hvordan vi ville lave det, der er kun blevet tilføjet mere til det fra start, såsom DevOps værktøjerne som blev introduceret senere i forløbet.

## 2. Maintenance and SLA status

### 2.1. Hand-over

Efter at vi fandt ud af hvem vi skulle operere og fandt ud af hvem de var, blev vi udstyret med et dokument.  
I dokumentet blev vi instrueret i den mest nødvendige viden, for at kunne operere systemet. Overordnet set bestod dokumentet af et kort systemt overblik, hvor der blev linket videre til deres Requirement Analysis Dokument, hvis vi ønskede at læse mere om systemets scope, specifikationer, implementation og meget mere. 
<br>
Dernæst fik vi en beskrivelse af systems arkitektur, altså kort hvilke komponenter det består af, hvad de er lavet med, samt hvor de kører henne. Credentials blev beskrevet og vi fik af vide hvor vi kunne komme i besiddelse af username og password til at kunne komme på serverne. Efterfølgende blev systemets dataflow beskrevet, igen både for front-end og back-end delen, Vi blev også gjort opmærksomme på hvordan vi skulle lave bug reports / issues, samt hvordan restarting af komponenter foregår. 
Til sidst i dokumentet blev vi informeret om hvordan vi kunne få adgang til inner state information samt hvordan deres CI / CO fungerer. 
<br>
Overordnet set indeholder dokumentationen, hvad der var nødvendigt, for at vi som operatorer kunne operere systemet. 
Vi kunne dog godt have tænkt os bedre kontakt oplysninger til udviklerne. 

### 2.2. Service-level agreement

Vi indgik en række Service Level Agreements med Gruppe E. Dokumentet fungerede som en kontrakt mellem dem som systemudviklere og os som opererer systemet. Dokumentet giver kun en operationel indsigt i systemet og har intet at gøre med selve udviklingen af systemet. SLA´en er gyldig pr. d. 2. november 2017 og frem til og med d. 31. januar 2018. 
<br>
Den første aftale vi indgik med gruppe E omhandler service tid for systemet, her har vi indgået aftale om, medmindre andet er aftalt, at følgende er gældende som SLA: 

* At Hackernews er tilgængeligt 24/7/365. Med mindre vedligeholdelse er annonceret. 
* Kontakt og svar tid fra Gruppe E (udviklerne) er mellem 07:00 - 17:00, fra mandag til fredag, og i weekender behandles kun system kritiske fejl. 
* For hver måned informeres på forhånd omkring vedligeholdelse.
* Ekstraordinære nedlukninger vil blive annonceret på Github eller via email hvis den er indtastet i systemet. 

#### Omkring oppetid er følgende aftale indgået: 

Hackernews vil fungere 95% af tiden. For hver procent som ligger under den aftalte oppetid vil blive krediteret med 0,5% af det samlede beløb der er betalt for systemet. 
KPI tæller ikke når den månedlige vedligeholdelse finder sted. 

#### Omkring gennemsnitlig genopretning af systemet er følgende aftale indgået: 

Den gennemsnitlige tid, det vil tage for tjenesten at genoprettes ved fejl, kan variere meget. Det er meget vanskeligt at estimere genopretnings tiden for et hypotetisk problem. Når det er sagt, vil enhver dødbringende systemfejl blive håndteret som en akut hændelse. 

#### Omkring fejlrapportering og responstid er følgende aftale indgået: 

Der vil være fire forskellige typer af problemer for systemet. Hver type hændelse har sit eget KPI som er som følgende: 

* Akutte hændelser - 6 timer.
* Vigtige hændelser - 12 timer.
* Normale hændelser - 72 timer. 
* Mindre hændelser 168 timer. 

Timerne er defineret som en TTR (Time to Response). Ved Akutte og vigtige hændelser vil der altid blive taget hånd om det med det samme. Det er også ved disse typer af hændelser, hvor operationsholdet / kunden skal kontakte udviklingsholdet direkte.
For alle andre typer af hændelser er det kun nødvendigt, at lave et issue på Github. 
br>
Generelt er alt månedligt baseret. Det betyder, at KPI'erne i slutningen af måneden vil blive evalueret. Hvis de er over de grænser, der er fastsat i SLA-aftalen, vil kunden ikke få nogen kredit. Hvis det ligger under grænsen, foretages der en beregning for kunden. 
<br>
Hele kontrakten ophæves, hvis der opstår et globalt problem. Dette kunne være certifikat brud fra Globalsign, en infrastruktur afbrydelse på Hetzner.com, naturkatastrofer eller lignende problemer. Dette er ude af vores hænder, og derfor kan Group E ikke tage ansvar for disse årsager.

### 2.3. Maintenance and reliability

Under forløbet med Hacker-News clonen har vi været operator for Gruppe E. 

Efter langt om længe, endelig at finde ud af hvem gruppe E var, kunne vi endelig opererer deres system. Vi valgte at operere deres system på den måde at vi gik på opdagelse i det, ved at prøve og være helt normal bruger, vi fandt også deres endpoint på deres GitHub, så vi valgte også at udfordre disse lidt ved hjælp af postman. 

I løbet af den tid vi har opereret deres system, har vi oplevet problemer med meget lange responstider (mellem 30 - 60 sek pr request.) Vi rapporterede fejlen til gruppen, hvilket viste sig at være et problem med, at deres database krævede for meget af CPU’ens ydeevne. Mens vi også var operatorer på deres system, opdagede vi, at vi havde mulighed for at lave request til deres simulator POST, på baggrund af det kunne vi se at der var åbent for alle ip-adresser, til at poste stories ind i deres system og at vi ikke fik det samme hanesst id tilbage. Vi fandt ud af dette, ved at lave et POST kald fra postman, det vi sende fra postman så ud som følgende:

```
{
"post_title": "Y Combinator", 
 "post_text": "test text", 
 "hanesst_id": 9999999991, 
 "post_type": "comment", 
 "post_parent": -1, 
 "username": "Vixo", 
 "pwd_hash": "b0f3dc043a9c5c05f67651a8c9108b4c2b98e7246b2eea14cb204295", 
 "post_url": "http://ycombinator.com"
 }
```
Fra det Post request fik vi følgende tilbage. 

```
{
    "post_title": "Y Combinator",
    "post_text": "test text",
    "hanesst_id": 1410065399,
    "post_type": "comment",
    "post_parent": -1,
    "username": "Vixo",
    "pwd_hash": "b0f3dc043a9c5c05f67651a8c9108b4c2b98e7246b2eea14cb204295",
    "post_url": "http://ycombinator.com"
}
```

Som det kan ses er det altså lykkedes os at poste en story til deres system via deres simulator POST. Som det også ses er der en fejl i deres hanesst id, idet vi ikke får det samme id tilbage som vi har sendt. 

På baggrund af dette kan vi derfor konkluderer at deres system er yderst sårbart over for  DDos angreb. 

Vi fandt også ud af i sammenhæng med ovennævnte problem at det var muligt at oprette stories, i deres system, uden at være logget ind. Det kunne vi gøre ved, at bruge deres simulator post API: /hackernew/post. Ved at bruge den, kunne vi skrive tilfældige usernames og passwords, og derved oprette både bruger og stories, igen brugte vi Postman til dette, det vi sende fra Postman så ud som følgende:

```
{
"post_title": "Y Combinator", 
 "post_text": "test text", 
 "hanesst_id": 9999999992, 
 "post_type": "comment", 
 "post_parent": -1, 
 "username": "JonasSimonsen", 
 "pwd_hash": "b0f3dc043a9c5c05f67651a8c9108b4c2b98e7246b2eea14cb204295", 
 "post_url": "http://ycombinator.com"
 }
 ```
 
Som det kan ses poster vi en bruger som hedder “JonasSimonsen” til systemet. Det response vi fik tilbage fra deres system, så ud som følgende: 

```
{
    "post_title": "Y Combinator",
    "post_text": "test text",
    "hanesst_id": 1410065400,
    "post_type": "comment",
    "post_parent": -1,
    "username": "JonasSimonsen",
    "pwd_hash": "b0f3dc043a9c5c05f67651a8c9108b4c2b98e7246b2eea14cb204295",
    "post_url": "http://ycombinator.com"
}
```

Da vi ikke selv er stødt på den bruger i vores CSV-filer med brugernavnet “JonasSimonsen”, tvivler vi meget på at de selv har oprettet en med præcist dette brugernavn, og vi betegner det derfor som en fejl.

Alle ovenstående problemer blev rapporteret til gruppen som github issues til projektet. Gruppen så vores issues, gav feedback på dem og fiksede dem, i de tilfælde hvor de også så det som et problem. Men vi fik desværre ikke besked når de var fikset.  

## 3. Discussion

### 3.1. Technical discussion

Selve udviklingen af Hacker New clonen har været en turbulent oplevelse. Vi har haft mange udfordringen i løbet af processen men vi har absolut også lært meget af det, hvilket har været rigtig godt. Det har gjort at vi har 3 gode og 3 mindre gode ting fra udviklingsfasen. 

Vi har listet de 3 bedste ting her under som vi vil uddybe lidt nærmere. 

* Stort datasæt
* Docker
* “The after part”

En af de bedste ting ved dette projekt har været at få lov til at arbejde med et system som skulle kunne håndtere en stor mængde data, og ikke de typiske små projekter man har arbejdet med i skoletiden. På den måde har man fået et bedre indblik i hvordan det vil være at lave et “rigtigt” system og hvad de skal kunne håndtere.

En anden rigtig god ting som vi har lært en masse af, har været brugen af Docker og Docker-swarm. Vi har fået et helt nyt kendskab til hvordan man kan opbygge store systemet med mulighed for mange brugere og request uden større voldsomme omkostninger til drift, ydermere har vi også lært hvordan vi kan vedligeholde sådanne systemer på en sådan måde at de kan være fuldt funktionsdygtige og har en ekstrem høj oppetid, selv under både opdatering og eventuelle server nedbrud.  

Delen som sker efter man er færdig med sit system, er igen noget som er helt nyt for os, da vi ikke har haft lært om det tidligere. Hele den del med monitorering/scaling og anden vedligeholdelse. Det har været nyt og spændende og enormt relevant at lære om, da det er noget man skal bruge til at holde ens systemer oppe, og mindske de fejl man nu engang vil få på en bedre og mere effektiv måde.

Vi har listet de 3 største problemer her under som vi vil uddybe lidt nærmere.

* Mange fejl i starten 
* Tidspres 
* Operator

I starten havde vi problemer med at vi fik en masse fejl 400 (bad request) som blev vist på Helge’s error chart, men da vi ikke havde sat noget monitoring system op, blev vi først klar over det sent, hvilket resulterede i vi havde fået mangel fejl. Selve udredningen af fejlene var også noget som tog os lang tid, idet vi ikke havde en decideret logfil og evt. monitoreringsværktøj til at fortælle os præcis hvor i vores system fejlen opstod. Ved at vi skulle bruge så lang tid på at finde fejlen, gjorde det også at vi hurtigt kom bagud i forhold til diverse dokumentation og andre implementeringer. 

Da vi kom til at skulle implementere Prometheus og Grafana i vores system blev vi igen presset da vi havde problemer med at få det op at køre ordentligt, vi brugte lang tid på at sætte det op, og den ene uge vi havde til at få det igang virkede ikke som tilstrækkelig tid til at kunne fuldføre det. Dette gjorde sig også gældende i andre dele af systemet da vi ofte havde flere afleveringer på tværs af vores fag. 

Ideen med operator grupper virker god, idet at man prøver det, men da kommunikationen, i vores tilfælde, har været minimal, har vi ikke fået det store udbytte af dette. Hvilket har gjort vi selv har skullet operere vores system, og finde fejl. Det gav os problemer specielt tidligt, med de mange 400 fejl, da vi havde regnet med vores operators ville have gjort os opmærksomme på dette.

### 3.2. Group work reflection & Lessons learned
Gruppearbejdet har fungeret godt, og vi har kunnet dele opgaverne ud så alle har kunnet bidrage til udviklingen af systemet. På front-end delen hvor vi kun har haft 1 enkelt mand til at arbejde med det, så der har det været mindre gruppe arbejde, men der har været kommunikation mellem ham og resten af gruppen i forbindelse med REST API’erne og håndteringen af data frem og tilbage.

Rollerne i vores tilfælde har ikke haft den store betydning, og de er ikke blevet fuldt så meget som vi i starten gerne ville have gjort det til. Vi tror at noget af grunden til dette har været vores dårlige tidshåndtering i det at vi ikke har kunnet nå at strukturere det hele på en ordentlig måde før vores deadline nærmede sig. Det ene sted rollerne er blevet brugt har været ved vores QA hvor der blevet lagt meget vægt på at vi skulle benytte TDD.

## 4 Conclusion

Overordnet har projektet været fedt at arbejde med da det har givet et godt indblik i hvordan det er at arbejde med store mængder data samt hvad der sker efter et system er færdigbygget, ved  at bruge monitoring tools, skalering etc. 

En mindre god ting har været at tiden har været så presset som den har været, og vi derfor ikke har følt vi har haft nok med tid til rigtigt at sætte os ind i de værktøjer vi har fået stillet til rådighed, og på den måde ikke fået det fulde udbytte af dem.

Set i bakspejlet burde vi have været bedre til at styre vores sprint og have delt de stillede opgaver op i mindre dele. Således at de blev mere overskuelige. Vi kunne med fordel have brugt projektstyringsværktøjer som f.eks. Trello. 

Vi skulle evt. have brugt lidt mere tid i starten af projektet på at lave nogle modeller til at illustrere hvordan vi forestillede os vores system skulle se ud, inden vi begyndte at bygge det. Det ville have givet os en rød tråd at gå tilbage til ved eventuelle tvivlsspørgsmål om opbygningen af systemet.


## 5. Reference list
[original hackernews](https://news.ycombinator.com/)
<br>[Docker](https://www.docker.com/what-docker)
<br>[Docker Swarm](https://docs.docker.com/engine/swarm/) 
<br>[Tomcat](http://tomcat.apache.org/)
<br>[Jenkins](https://jenkins-ci.org/)
<br>[Jetty](http://www.eclipse.org/jetty/)
<br>[Grafana](https://grafana.com/grafana)
<br>[Prometheus](https://prometheus.io/)
<br>[TDD](https://en.wikipedia.org/wiki/Test-driven_development)
<br>[JOA](https://en.wikipedia.org/wiki/Java_Persistence_API)
<br>[React](https://reactjs.org/)
<br>[DigitalOcean](https://www.digitalocean.com/)
<br>[Postman](https://www.getpostman.com/)
<br>[DDos](https://en.wikipedia.org/wiki/Denial-of-service_attack)
<br>[Trello](https://trello.com/)
