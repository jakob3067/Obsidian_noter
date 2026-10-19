## Symboler

y(s): måling
r(s): indgangs signal
u(s): styre signal

## Open loop Control
Åbent sløjfe regulering er uden tilbage kobling 
Er det muligt?

3 mulige open løkke regulering

![[Pasted image 20260615185650.png]]
Vi kan kun rigtigt bruge en konstat value til sidst når vi går mod uendelig

Her bruger vi slut værdig sætningen til at finde pulse resoponden vi konvagere mod i et stabilt system
![[Pasted image 20260615190346.png]]
![[Pasted image 20260615190325.png]]
kan også bruges til at finde DC forstærkning (Hvad vi konvagere mod hvis vi kører uendeligt)

Puls til et step ( brug intergral) intigrer en puls til at få et step


*Problemet med åbent sløjfe*
Ikke robust mod forstyrelser

All in all brug tilbage kobling


# Feedback control

## Closed loop transfer function
Finde frem til en transfer function fra systemet
![[Pasted image 20260220083115.png]]

referance - tilbage kobling = fejl
e(s): fejl 


G(s) kan ikke ændres = plant 
K(s) kan ændres = regulatoren 
L(s) Loop gain =G(s) + K(s)

## Stabilitet
![[Pasted image 20260615194205.png]]
## Disturbance

Forstyrelse undertrykkelse
![[Pasted image 20260615194515.png]]


![[Pasted image 20260615195030.png]]


## Measure noise

Hvis vi inkludere måle støj 
![[Pasted image 20260615195221.png]]

![[Pasted image 20260615195247.png]]


# Steady state tracking/Referance tracking

system type = hvad for en grad polinumiel for hvad vores fejl er en ikke 0 konstant
Type er hvilken grad fejlen er

type 0 = konstant fejl
type 1 = rampe 
type 2 = parabol
![[Pasted image 20260615200813.png]]
man kan bruge final value therom til at finde typen


### Stationær fejl

steady state error

![[Pasted image 20260615201529.png]]

Antalet af poler i origo er også hvilken type det er

![[Pasted image 20260615201715.png]]

Exempel
![[Pasted image 20260615202041.png]]


## Cascade regulering/cascade control

Man bygger to regulerings sløjfer uden på hinanden som sørger for en bedre regulering 

Gør det muligt at implementere forskellige sample rates

![[Pasted image 20260615202645.png]]
![[Pasted image 20260615203153.png]]
![[Pasted image 20260615203349.png]]
