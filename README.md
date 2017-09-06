# HackerNews-Requirements

## Introduction

#### Team role
Alexander Steen = Lead Developer<br />
Jonas Simonsen = Project Manager<br />
Kasper Worm = DevOps<br />
Martin Karlsen = Q&A<br />

#### Purpose of the system
Formålet er et system hvor en bruger har mulighed for at registrere sig og lave indlæg, som kan kommenteres af andre registrerede brugere på systemet. Den registrerede bruger kan også kommentere andres oplæg samt, up og down vote forskellige indlæg. 
Brugerne skal via indlæg kunne samle karma points som bla. kan bruges til at downvote andre indlæg.

#### Scope of the system
Folk med interesse i teknologi, typisk af hobby, arbejde, eller skole. 
Brugeren vil typisk være mænd i alderen 18 - 40 år 
Forum for discussion, samtale samt deling af information.


#### Objectives and success criteria of the project
En fungerende HackerNews klon som opfylder requirements.



#### Definitions, acronyms, and abbreviations
MSSQL - Microsoft Structured Query Language.<br />
API - Application program interface.<br />
REST - Representational state transfer.<br />
HTML - Hypertext Markup Language.<br />
CSS - Cascading Style Sheet.<br />
Post - Et indlæg oprettet af en bruger, hvorpå der kan votes og kommenteres.<br />
Cloud - En server hvorpå systemet ligger, som kan tilgås udefra.<br />
GitHub - En hjemmeside til at versionere projekter, samt gemme dem.<br />

#### References
Reddit: https://www.reddit.com<br />
Hacker News: https://news.ycombinator.com/<br />
Både Reddit og Hacker News er social nyhedssites, hvor brugere kan lave indlæg, der kan kommenteres og reageres på fra andre brugere. 

Requirements: https://github.com/datsoftlyngby/soft2017fall-lsd-teaching-material/blob/master/assignments/01-HN%20Clone%20Task%20Description.ipynb<br />

#### Overview
Vi skal lave en hjemmeside tilsvarende HackerNews hvorpå brugere kan oprette indlæg og vote på hinandens indlæg.

## Current system
Vi har på nuværende tidspunkt ikke noget eksisterende system. Det færdige system skal være en efterligning af det allerede eksisterende site “Hacker News”.


## Proposed system

#### Overview
Vi skal lave en hjemmeside tilsvarende HackerNews hvorpå brugere kan oprette indlæg og vote på hinandens indlæg.

#### Functional requirements
Oprette bruger.
Bruger login, logout.
Se posts.
Oprette/Slette egne post.
Redigere egne posts.
Up vote af posts.
Bruger skal have 500 karma points for at kunne down vote et post.
Kommentere på posts.
Kommentere på kommentarer
Rapporter posts for spam.
Filtrere posts mellem nye posts, hvor mange kommentarer der er
Skjule og vise posts.

#### Nonfunctional requirements

###### Usability
Brugeren interagere med systemet via en hjemmeside.

###### Reliability
Systemet skal have en oppetid på mere end 95 %, ydermere må systemet på intet tidspunkt miste data. 
Systemet skal kunne modtage data selvom det er nede, og gemme dataen til systemet er oppe igen 

###### Performance
Der er umiddelbart ikke nogen performance krav, men vi forventer at systemet skal reagere inden for “rimelig tid” så brugeren ikke tror at systemet er gået ned.

###### Supportability
Der er umiddelbart ingen krav om kontakt til support og systemet vil derfor ikke have nogen.

###### Implementation
Systemet deles op i en frontend, backend og data lag.
Frontend vil blive udviklet i HTML, Javascript (Angular2 eller React) og CSS.
Backend vil blive udviklet i Java
Data laget vil blive udviklet i .NET med EntityFramework og MSSQL som database.
Alt data skal gemmes i en database.
Der skal være et REST API som giver andre platforme adgang.

###### Interface
Interface er en hjemmeside hvor gæster kan se indlæg, men at man skal være logget ind for at kunne kommentere, up-/down vote indlæg.
Derudover er interfacet også et API, der giver adgang, for andre platforme, til systemet, så man f.eks. kan lave en app.

###### Packaging
Produktet bliver lagt op på en Cloud service og derudover kommer koden til at ligge på nogle GitHub repositories, som kunden får adgang til.

###### Legal
Systemet overskrider ingen love og der er derfor ikke nogle love som vi skal tage forbehold for. Kommer der, i fremtiden, nogle lovmæssige problemer, er det kundens ansvar at skaffe de retmæssige licenser mm.

#### Systemmodels

###### Scenarios
Som gæst kan jeg se de indlæg, der er lavet så jeg kan se om der sker noget interessant.
Som gæst kan jeg oprette en profil
Som gæst kan jeg logge ind og derved blive en bruger
Som bruger kan jeg logge af
Som bruger kan jeg oprette posts
Som bruger kan jeg redigere eller slette mine egne posts
Som bruger kan jeg få karma ved at kommentere, oprette posts og up vote 
Som bruger kan jeg vote up
Som bruger kan jeg down vote når brugeren har opnået 500 karme point

###### Use case model
