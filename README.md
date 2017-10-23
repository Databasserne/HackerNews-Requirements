# HackerNews-Requirements

## Introduction

### Team role
Alexander Steen = Lead Developer <br/>
Jonas Kjær Simonsen = Project Manager <br/>
Kasper Sylvest Worm = Dev Op <br/>
Martin Karlsen = Q&A <br/>

### Participation for assignment
Alle ovenstående gruppemedlemmer har bidraget ligeligt, 25% per medlem.

### Divide into subsystems

### Logical Data Model
![LDM](https://github.com/Databasserne/HackerNews-Requirements/Pictures/LogicalDataModel.png)

### Use Case Model
Use Case: Log ind
Level goal: Få adgang til systemet
Primary Actor: Gæst
Precondition: At der er en oprettet bruger
Main succes scenario: Gæsten bliver logget int
Success guaratees: Du er logget ind som bruger
Extensions: Oprette profil
Special requirements: NOPE

Use Case: Oprette profil
Level goal: Benyt systemet som bruger
Primary Actor: Gæst
Precondition: Intet
Main succes scenario: profilen er oprettet
Success guaratees: din profil er oprettet
Extensions: Intet
Special requirements: NOPE

Use Case: Se posts
Level goal: Læse posts  
Primary Actor: Gæst
Precondition: Intet
Main succes scenario: At posts vises til gæsten 
Success guaratees: at posts vises
Extensions: Intet
Special requirements: NOPE  

Use Case: Log ud
Level goal: Log ud af din profil
Primary Actor: Bruger
Precondition: Du er logget ind
Main succes scenario: Du bliver logget af
Success guaratees: Du bliver logget af systemet
Extensions: Log ind
Special requirements: NOPE  

Use Case: Redigere post
Level goal: Redigere din egen post
Primary Actor: Bruger
Precondition: Du har oprettet en post
Main succes scenario: Posten bliver redigeret
Success guaratees: Posten bliver redigeret
Extensions: Opret post
Special requirements: NOPE

Use Case: Slette egne post
Level goal: Fjerne din post fra systemet
Primary Actor: Bruger
Precondition: Du har oprettet en post
Main succes scenario: Din post bliver slettet
Success guaratees: Din post bliver slettet
Extensions: Oprette post
Special requirements: NOPE

Use Case: Upvote post
Level goal: Få karme ved at upvote
Primary Actor: Bruger
Precondition: Der er oprettet en post
Main succes scenario: Posten bliver upvoted
Success guaratees: Posten bliver upvoted
Includes: Få karma 
Special requirements: NOPE

Use Case: Downvote post 
Level goal: Fjerne karma fra bruger der har postet denne post
Primary Actor: Bruger
Precondition: Der er oprettet en post
Main succes scenario: Posten bliver downvoted
Success guaratees: Posten bliver downvoted
Extensions:
Special requirements: Du har minimum 500 karma point.

Use Case: Upvote comment
Level goal: Få karme ved at upvote
Primary Actor: Bruger
Precondition: Der er oprettet en comment
Main succes scenario: comment bliver upvoted
Success guaratees: comment bliver upvoted
Includes: Få karma 
Special requirements: NOPE

Use Case: Downvote comment 
Level goal: Fjerne karma fra bruger der har postet denne comment
Primary Actor: Bruger
Precondition: Der er oprettet en comment
Main succes scenario: Comment bliver downvoted
Success guaratees: Comment bliver downvoted
Extensions:
Special requirements: Du har minimum 500 karma point.

Use Case: Oprette post
Level goal: Oprette en post i systemet
Primary Actor: Bruger
Precondition: Du er logget ind
Main succes scenario: Posten bliver oprettet
Success guaratees: 
Extensions: 
Special requirements: NOPE

Use Case: Skrive kommentar
Level goal: Oprette kommentar på post
Primary Actor: Bruger
Precondition: Der er oprettet en post du vil kommentere på 
Main succes scenario: Kommentaren bliver oprettet på posten
Success guaratees: 
Extensions: 
Special requirements: NOPE

Use Case: Se status
Level goal: Se API'et status
Primary Actor: Simulator/Bot
Precondition: API'et er tilgængeligt
Main succes scenario: Der kommer et response fra API'et
Success guaratees: ALIVE, UPDATE, DOWN - som de 3 svar 
Extensions: 
Special requirements: Kun tilgængeligt til Simulator/Bot
