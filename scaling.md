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

### Print out

##### Docker Node LS
```
ID                            HOSTNAME                 STATUS              AVAILABILITY        MANAGER STATUS
cozf2jsbcja44zoqm6efexp13 *   LDS                      Ready               Active              Leader
h9tuejesinzox8hbe0novy7bc     HackerNewClone-Worker2   Ready               Active              
li2i8ivgpslm4l88dav7bkdof     HackerNewClone-Worker1   Ready               Active
```

##### Docker Service LS

```
ID                  NAME                MODE                REPLICAS            IMAGE                                     PORTS
1qo3ecfz14yq        elk                 replicated          1/1                 sebp/elk:latest                           *:5601->5601/tcp,*:9200->9200/tcp,*:5044->5044/tcp
3ytu2s1wds0a        backend             replicated          2/2                 databasserne/lsd-hackernews-backend:60    *:8080->8080/tcp
73ktwc7e45rf        docker-exporter     global              3/3                 basi/socat:v0.1.0                         *:0->4999/tcp
ohgrookwslch        prometheus          replicated          1/1                 basi/prometheus-swarm:v0.4.0              *:9090->9090/tcp
psojyyhcq6ep        frontend            replicated          2/2                 databasserne/lsd-hackernews-frontend:24   *:80->5000/tcp
ywgkobov6ymh        grafana             replicated          1/1                 grafana/grafana:4.5.2                     *:3000->3000/tcp

```
