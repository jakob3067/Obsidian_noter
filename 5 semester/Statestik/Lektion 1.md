

# Basic probability

Stokastisk eksperiment
Noget der kan fører til forskellige udfald men vi ved ikke hvad?

Sample space "S" udfaldsrum, 


er mængden af mulige udfald 
S kan være diskret eller kontinuært 

```pdf-page
UTF-8''Lektion_201_20slides-1.pdf#1
```

```pdf-page
UTF-8''Lektion_201_20slides-1.pdf#2
```
Stokastisk eksperiment
Noget der kan fører til forskellige udfald men vi ved ikke hvad?

Sample space "S" udfaldsrum, 


er mængden af mulige udfald 
S kan være diskret eller kontinuært 

**Event**
KOmbination af udfald, definiation af et event kan være et eget sat af 

**Union (forventningsmængde**)
Kan sættes op ssom venn diagram hvor event E1 og E2 og hvor de overlapper

$$
E_{1} \cup E_{2}
$$
**Intersection** (**fællesmgd**)
$$
E_{1} \\\cap E_{{2}}
$$
**Complementary**

$$
S\setminus E_{2}
$$
Disjoint event
$$
E_{1} \\or 
$$

**Defination** **af** **sandsynlighed**

$$
N_{n}(E)=
$$
Gange ud af n hvor E indtraffes
$$
P(E)=^{def}\lim_{ n \to \infty } \frac{N_{n}(E)}{n}
$$

alt undtagen A
$$
A' 
$$
**Axiomer**

Ø = { } = tomme mængde 


Når der sker noget er sandsynligheden for der sker noget altid sker

$$
P(Ø)=0 
$$
Der sker sltid noget i et eksperiment
$$
P(S)=1
$$
$$
P: E \c= S \rightarrow [0,1]
$$
$$
0 \lt P(E) \lt 1
$$
disjointet events kan kun adderes hvis de ikke overlapper
$$
E_{1} \cap E_{2} = ø = P(E_{1}UE_{2})
$$


#### addition regler

$$
P(A_{1}UB_{1})= P(A)+P(B)-P(A\cap B)
$$
$$
P(A\cup B\cup C)=P(A)+P(b)+P(C) -P(A\cup B)-P(A\cup C)-P(B\cup C)
$$


#### Disjoint set
$$
E_{1},E_{2},\dots E(n), E_{j} \cap E_{j}=Ø
$$
$$P(E_1 \cup E_2 \cup ... \cup E_n) = P(E_1) + P(E_2) + ... + P(E_n) = P(\bigcup_{i=1}^{n} E_i) = \sum_{i=1}^{n} P(E_i)
$$

#### Multiplicere sandsynlighed
Kan kun hvis og hvis events er uafhængige (ikke det samme som disjoint) skal være forskellige sample space og events

$P(E_{1}\cap E_{2}) =P(E_{1})P(E_{2})$

## betinget sandsynlighed (kalman vigitg)

Events A, B

$P(A|B)$ "A givet B" def $\frac{P(A\cap B)}{P(B)}$

**eksemple**
$A : T \lt$ 20 grader C tilfældig dag 
B_1 dag = januar
B_8 dag = august

generalle Sandsynlighed ligger mellem sandsynligheden i januar og sandsynligheden i august 
$P(A|B_{1}) \lt P(A)\lt P(A|B_{8})$



### Loven om totalt sandsynlighed

Kan kun bruges med alle mulige oversager er med alle events(betingelser)

Disjunkt og komplet set af event $E_{1},E_{2},\dots,E(n)$

$E_{i}\cap E_{j}=Ø$ $E_{1}\cup E_{2}\cup\dots\cup E_{n}=S$

Grader og måneder eksemple

$$
P(A)= P(A|E_{1})P(E_{1}) + P(A|E_{2})P(E_{2})+\dots+P(A|E_{n})P(E_{n})

$$

Samlet formel 
$$
P(A)=\sum^n_{i=1}P(A|E_{i})P(E_{i})
$$
Bayes formel
$$
P(A|B)=\frac{P(A\cap B)}{P(B)} = \frac{P(B|A)P(A)}{P(B)}
$$
$$
P(E_{i}|A)= \frac{P(A|E_{i})P(E_{i})}{P(A)}=\frac{P(A|E_{i})P(E_{i})}{P(A|E_{1})P(E_{i})}+\dots+ P(A|E_{n})P(E_{n})
$$

```pdf-page
UTF-8''Lektion_201_20slides-1.pdf#3
```





```pdf-page
UTF-8''Lektion_201_20slides-1.pdf#4
```

```pdf-page
UTF-8''Lektion_201_20slides-1.pdf#5
```

#### kombinatorik

Ordnet sequencer (permutationer)
n objekter 
Rækkefølge er vigtig
PÅ hvor mange måder kan jeg stille dem i forskellige rækkefølger

$$
n!
= n*(n-1)*(n-2)*\dots *2*1$$


**Odrede sekvenser**

n objekter men tager kun et hvis antal (r objekter)

r er antal led i formlen
$$
\frac{n!}{(n-r)!} =n*(n-1)(n-2)\dots(n-(r-1))

$$
**Uordnede sekvenser** **combination**
Orderen er ikke vigtig


n objekter udtager r blandt n

antalet af kombinationer



$$
=\frac{n!}{(n-r)!r!}
$$
