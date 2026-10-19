

[[Lecture 4 - PID controllers.pdf]]


### PID regulator

G(s)= system

K(s) = regulator

u(s)= styre signal

y(s)=måling 

e(s)= fejl



PID styre strukturen af K(s) altså regulatoren 
![[Pasted image 20260616113804.png]]

## P led - proportonal regulator

Konstant K gange fejlen K_p er propotonial forstærkning 
![[Pasted image 20260616114029.png]]
Hvordan P led gør ved signalet exempel
![[Pasted image 20260616114728.png]]
![[Pasted image 20260616114740.png]]

K_p bliver større:

Vi kommer tættere på vores ønsket værdi men oversvinger signalet
Gør man minimere stationær fejl
stige tid liver mindre

![[Pasted image 20260616115015.png]]
I imagniær plan


### feed forward?
![[Pasted image 20260616115242.png]]

Exempel
![[Pasted image 20260616115430.png]]Kan eliminære stationær fejl
Men virker kun hvis modeleringen af systemet er perfekt
nu styre kp kun 


## PI - regulator Prop + integratorer
![[Pasted image 20260616115539.png]]

Intergrator led er på for at fjerne stationær fejl 
![[Pasted image 20260616122938.png]]
#### implementering - Auto reset
![[Pasted image 20260616123327.png]]



Eksempel på et signal
![[Pasted image 20260616123432.png]]


Hvad der sker med disturpace

![[Pasted image 20260616123656.png]]



## PID - Prop Int Diffrencial led

D led kigger frem i tidne og prøver et prediktere hvad der sker

FIlter på d led da måle støj i differencal kan være dum

![[Pasted image 20260616124057.png]]


![[Pasted image 20260616124215.png]]
Ved højere frekvenser reduceres d ledet

Hvordan d led påvirker
![[Pasted image 20260616124417.png]]
D led minimere ocellatsion og overshoot

For øger stige tid

Samenlignings til en friktion. altså demper signalet




## PID alle led

Diagram af fuld PID
![[Pasted image 20260616124316.png]]



## PID - tuning

Tuninge gennem input output signaler

Zeigler nichols tuning skruer op til systems ocelere og finder Ultimative gain

![[Pasted image 20260616130642.png]]

![[Pasted image 20260616130654.png]]




Alternativt kan man indsætte K_p lied til det ociuleres og 