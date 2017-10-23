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
![LDM](https://github.com/Databasserne/HackerNews-Requirements/blob/master/Pictures/LogicalDataModel.png)

### Use Case Model
Use Case: Log ind <br>
Level goal: Få adgang til systemet <br>
Primary Actor: Gæst <br>
Precondition: At der er en oprettet bruger <br>
Main succes scenario: Gæsten bliver logget int <br>
Success guaratees: Du er logget ind som bruger <br>
Extensions: Oprette profil <br>
Special requirements: NOPE <br>

Use Case: Oprette profil <br>
Level goal: Benyt systemet som bruger <br>
Primary Actor: Gæst <br>
Precondition: Intet <br>
Main succes scenario: profilen er oprettet <br>
Success guaratees: din profil er oprettet <br>
Extensions: Intet <br>
Special requirements: NOPE <br>

Use Case: Se posts <br>
Level goal: Læse posts <br>
Primary Actor: Gæst <br>
Precondition: Intet <br>
Main succes scenario: At posts vises til gæsten <br>
Success guaratees: at posts vises <br>
Extensions: Intet <br>
Special requirements: NOPE <br>

Use Case: Log ud <br>
Level goal: Log ud af din profil <br>
Primary Actor: Bruger <br>
Precondition: Du er logget ind <br>
Main succes scenario: Du bliver logget af <br>
Success guaratees: Du bliver logget af systemet <br>
Extensions: Log ind <br>
Special requirements: NOPE <br>

Use Case: Redigere post <br>
Level goal: Redigere din egen post <br>
Primary Actor: Bruger <br>
Precondition: Du har oprettet en post <br>
Main succes scenario: Posten bliver redigeret <br>
Success guaratees: Posten bliver redigeret <br>
Extensions: Opret post <br>
Special requirements: NOPE <br>

Use Case: Slette egne post <br>
Level goal: Fjerne din post fra systemet <br>
Primary Actor: Bruger <br>
Precondition: Du har oprettet en post <br>
Main succes scenario: Din post bliver slettet <br>
Success guaratees: Din post bliver slettet <br>
Extensions: Oprette post <br>
Special requirements: NOPE <br>

Use Case: Upvote post <br>
Level goal: Få karme ved at upvote <br>
Primary Actor: Bruger <br>
Precondition: Der er oprettet en post <br>
Main succes scenario: Posten bliver upvoted <br>
Success guaratees: Posten bliver upvoted <br>
Includes: Få karma <br>
Special requirements: NOPE <br>

Use Case: Downvote post <br>
Level goal: Fjerne karma fra bruger der har postet denne post <br>
Primary Actor: Bruger <br>
Precondition: Der er oprettet en post <br>
Main succes scenario: Posten bliver downvoted <br>
Success guaratees: Posten bliver downvoted <br>
Extensions: <br>
Special requirements: Du har minimum 500 karma point. <br>

Use Case: Upvote comment <br>
Level goal: Få karme ved at upvote <br>
Primary Actor: Bruger <br>
Precondition: Der er oprettet en comment <br>
Main succes scenario: comment bliver upvoted <br>
Success guaratees: comment bliver upvoted <br>
Includes: Få karma <br>
Special requirements: NOPE <br>

Use Case: Downvote comment <br>
Level goal: Fjerne karma fra bruger der har postet denne comment <br>
Primary Actor: Bruger <br>
Precondition: Der er oprettet en comment <br>
Main succes scenario: Comment bliver downvoted <br>
Success guaratees: Comment bliver downvoted <br>
Extensions: <br>
Special requirements: Du har minimum 500 karma point. <br>

Use Case: Oprette post <br>
Level goal: Oprette en post i systemet <br>
Primary Actor: Bruger <br>
Precondition: Du er logget ind <br>
Main succes scenario: Posten bliver oprettet <br>
Success guaratees: <br>
Extensions: <br>
Special requirements: NOPE <br>

Use Case: Skrive kommentar <br>
Level goal: Oprette kommentar på post <br>
Primary Actor: Bruger <br>
Precondition: Der er oprettet en post du vil kommentere på <br>
Main succes scenario: Kommentaren bliver oprettet på posten <br>
Success guaratees: <br>
Extensions: <br>
Special requirements: NOPE <br>

Use Case: Se status <br>
Level goal: Se API'et status <br>
Primary Actor: Simulator/Bot <br>
Precondition: API'et er tilgængeligt <br>
Main succes scenario: Der kommer et response fra API'et <br>
Success guaratees: ALIVE, UPDATE, DOWN - som de 3 svar <br>
Extensions: <br>
Special requirements: Kun tilgængeligt til Simulator/Bot <br>
