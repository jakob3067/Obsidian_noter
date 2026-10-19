![[Pasted image 20241205121725.png]]
Formlerne ser meget uoverskuelige ud. Imidlertid er metoden ikke så vanskelig i praksis. Vi illustrerer den ved hjælp af nogle eksempler.

Vi ønsker at udregne følgende integral

$$∫x⋅e^{x^{2}} \ dx$$
Vi ser, at der både er tale om et produkt af funktioner, og at den ene er sammensat. Derfor prøver vi os frem med integration ved substitution.

Det første, man gør, er at finde den indre funktion i den sammensatte funktion.  
I vores tilfælde er det x2. Vi kalder den indre funktion for t.

$$t=x^2
$$
Nu differentierer vi t:

$$\frac{dt}{dx}=2x$$

venstresiden er bare et symbol, der betyder, at vi har differentieret t med hensyn til variablen x. 

Imidlertid lades vi som om, at symbolet er en brøk og isolerer dx.

$$dx=\frac{1}{2x}dt$$

Nu sætter vi t ind i integralet samt det nye udtryk for dx.

$$∫x⋅e^{x^{{2}}} \ dx=∫x⋅e^t⋅{\frac{1}{2x}} \ dt$$

Til sidst skal vi reducere integranden, og udføre integrationen.

$$∫x⋅e^t \frac{1}{2x}dt=∫ \frac{1}{2}\times e^t dt= \frac{1}{2} e^t+c$$

Som rosinen i pølseenden substituerer vi den indre funktion tilbage ind på t's plads.

$$∫x⋅e^{x^2}dx=\frac{1}{2} e^{x^{2}}+c
$$
## Partiel integration
![[Pasted image 20241205121951.png]]
