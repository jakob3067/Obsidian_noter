

### 1 ordens system
![[Pasted image 20260615153442.png]]

Impuls responds
![[Pasted image 20260615153511.png]]
Opmærksom på y/k

*step responds*
![[Pasted image 20260615153547.png]]
63% efter tau tids enheder

måde at finde tau på udfra graf 

### 2 ordens system

Standard form
![[Pasted image 20260615153646.png]]
3 type klasser af 2 ordens systemer
![[Pasted image 20260615153746.png]]


**Løsninger for underdæmpet system**

Komplexe poler 
![[Pasted image 20260615153139.png]]
Impuls responds for under dempet
![[Pasted image 20260615154038.png]]
Eksempel hvis man havde en større imaginær del ville man have en større svingnings frekvens

Step responds for under dempet 
![[Pasted image 20260615154247.png]]
*Bode plot af 2 ordent under dempet system*
![[Pasted image 20260615154326.png]]


**Kristisk dempet  2 ordent system**

Impuls responds
![[Pasted image 20260615154425.png]]
Step respods på et kristisk dæmpet system 
![[Pasted image 20260615154439.png]]

**Over dæmpet 2 ordents system**

impuls pesponds
![[Pasted image 20260615154608.png]]
sammenligning af kristisk dæmpet system er respondsen langsomere 

Step responds
![[Pasted image 20260615154632.png]]


### Performance specifikation

Udfra 2 ordens specifikationser
![[Pasted image 20260615154822.png]]

**Rise time**: tid fra 0.1 af referancen til 0.9 siger noget om hvor hurtigt vi rammer referancen

**indsvingings tid**: Tid for at vi holder os inde for +- a%

**Overshoot**: Maximal værdi 

*Peak tid*: den tid hvor signalet får den største tid (bruges til at regne Overshoot)



##### Rise time
![[Pasted image 20260615155202.png]]
Ud fra en approximations:

Kan gøres større ved at forstørre Omega_n 


##### Indsvingnings tid 
![[Pasted image 20260615155325.png]]
Ændre vi reel delen ændre jeg indsvingnings tid

##### Oversving/overshoot

*Peak time*
![[Pasted image 20260615155603.png]]
Bruges til at regne oversving
*Oversving*

![[Pasted image 20260615155627.png]]


#### Samlet krav
![[Pasted image 20260615155909.png]]


### Poler og nulpunkter på en state space model

Beskrevet godt i performances beskrivelse

Beskrives her i State space model
#### Poler
Defination af at finde polerne:
![[Pasted image 20260615160449.png]]
egen værdierne i A svare til polerne


exempel af beregningen for at finde polerne
![[Pasted image 20260615160538.png]]

#### Nulpunkt 
![[Pasted image 20260615161214.png]]
Hvis en matrice ikke går i rank = det = 0 kan man finde 0 punkt


### Stabilitet
#### Linere discrete tidssytem
Defination:
![[Pasted image 20260615161416.png]]
ingangs signal u er = 0

Defination: vores stilstand går mod 0


Vores system er stabilt hvis størreslsen af egeinværdierne i Phi er mindre en 1

![[Pasted image 20260615162057.png]]

#### Linær tids kontinuerete systemer

![[Pasted image 20260615162256.png]]

![[Pasted image 20260615162332.png]]


Opsætning af stabilitets condition

![[Pasted image 20260615162621.png]]