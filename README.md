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
Vi har delt vores system op i en frontend del og en backend del, vi har delt systemet i to sub systemer for nemmere vedligeholdelse, samt senere kunne proppen en frontend del mere på I form af for eksempel en app.

### Logical Data Model
![LDM](https://github.com/Databasserne/HackerNews-Requirements/blob/master/Pictures/LogicalDataModel.png)

### Use Case Model
![ucdiagram](https://github.com/Databasserne/HackerNews-Requirements/blob/master/Pictures/UseCaseDiagram.png)

#### Actor discription
##### Guest
Gæsten er en besøgende, som ikke er logget ind i systemet og som derfor ikke er genkendelig.<br />
Gæsten har ingen responsibility.

##### User
Brugeren er en besøgende, som er logget ind i systemet og som derfor er genkendelig.<br/>
Brugere har større adgang til systemet og kan derfor gøre flere ting,<br/>
som f.eks. at oprette posts og kommentere på andre posts.<br/>
Med disse muligheder har brugeren også et ansvar for at opfører sig ordentligt overfor andre brugere.

##### Simulator
Simulatoren er en bot, hosted af Helge.<br/>
Den har ansvar for at lave daglige requests til systemet, for at tjekke hvorvidt det fungerer.

#### Use Case Description
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

### API Documentation
##### Simulator
```POST(SimulatorPost): /post -> (Null, Error)``` <br/>
```GET: /latest -> (SimulatorResponseInteger)``` <br/>
```GET: /status -> (SimulatorResponseStatus)```
##### Authentication
```POST(UserCredentials): /api/v1/auth/login -> (UserToken, Error)``` <br/>
```POST(SignUpCredentials): /api/v1/auth/signup -> (Null, Error)```
##### User
```GET: /api/v1/user/me -> (User, Error) ```<br/>
```GET: /api/v1/user/post -> (PostList) ```<br/>
```PUT(UserInfo): /api/v1/user/edit -> (Null, Error)```
##### Posts
```GET: /api/v1/post/ -> (PostList, Error)```<br/>
```GET: /api/v1/post/{id:Number} -> (PostResponse, Error)```<br/>
```POST(Post): /api/v1/post -> (Null, Error)```<br/>
```PUT(Post): /api/v1/post/{id:Number} -> (Null, Error)```<br/>
```DELETE: /api/v1/post/{id:Number} -> (Null, Error)```
##### Comments
```GET: /api/v1/post/{id:Number}/comment -> (CommentList, Error)```<br/>
```GET: /api/v1/post/{id:Number}/comment/{id:Number} -> (CommentList, Error)```<br/>
```POST(Comment): /api/v1/post/{id:Number}/comment -> (Null, Error)```
##### Vote
```POST(): /api/v1/post/{id:Number}/upvote -> (Null, Error)```<br/>
```POST(): /api/v1/post/{id:Number}/downvote -> (Null, Error)```<br/>
```POST(): /api/v1/post/{id:Number}/comment/{id:Number}/upvote -> (Null, Error)```<br/>
```POST(): /api/v1/post/{id:Number}/comment/{id:Number}/downvote -> (Null, Error)```
 
#### Models
##### SimulatorPost
```
{"username": "<string>", 
 "post_type": "<string>", 
 "pwd_hash": "<string>", 
 "post_title": "<string>",
 "post_url": "<string>", 
 "post_parent": <int>, 
 "hanesst_id": <int>, 
 "post_text": "<string>"}
 ```

##### SimulatorResponseInteger
```<integer>```
##### SimulatorResponseStatus
```<string>```
##### UserCredentials
```
{"username": "<string>",
"password": "<string>"}
```
##### SignUpCredentials
```
{"username": "<string>",
"password":"<string>",
"rep_password":"<string>",
"fullname":"<string>"}
```
##### UserToken
```
{"token": "<string">,
"username": "<string>",
"fullname": "<string>"}
```

##### User
```
{"username":"<string>",
"fullname":"<string>"}
```
##### UserInfo
```
{"fullname": "<string>"}
```
##### Post
```
{"title":"<string>",
"body":"<string>"}
```
##### Comment
```
{"comment_text":"<string>"}
```
##### Null
Tom body med successfull status code (PUT/DELETE = 200, POST = 201)
##### Error
Status code 400
```
{"error_code":<int>,
"error_message":"<string>"}
```
##### PostList
```
[{"id":<int>,
"title":"<string>",
"body":"<string>",
"author_name":"<string>",
"created_at":"<date>"}]
```
##### PostResponse
```
{"title":"<string>",
"body":"<string>",
"author_name":"<string>",
"created_at":"<date>"}
```
##### CommentList
```
[{"id":<int>,
"comment_text":"<string>",
"author_name":"<string>",
"created_at":"<date>",
"comments": <CommentList>}]
```
