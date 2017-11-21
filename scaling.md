### What is Docker Swarm and why do we need it?
Docker Swarm er en samling af services (heraf "swarm") som hver især består af x antal containere.
Docker Swarm gør det let at scalere efter behov, da man kan bestemme hvor mange containers der skal være, i hver service.

### How can it help eliminate bottlenecks?

##### Update-downtime
Docker Swarm har rolling updates.<br/>
Dette betyder at vi kan update én container ad gangen, i hver service.<br />
Ved at gøre dette kan man opdatere containers løbende, i stedet for det hele samtidigt.

##### Single point of entry
Ved hjælp af Ingress netværket som følger med Docker Swarm, er der automatisk load-balance.<br/>
Dvs. hvis en enkelt container er nede (f.eks. pga update eller for mange requests), så vil den automatisk bruge en anden container.<br/>
Derudover hjælper Ingress også hvis den ene server går ned. Hvis dette sker, kan DNS pege på flere IP'er og selvom containeren, ikke<br/>
lægger på den IP, kan containeren findes på en anden node, som også er i Docker Swarm'en.
