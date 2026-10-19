```pdf-page
Agenda_lektion2.pdf#1
```



```pdf-page
UTF-8''Lektion_202_20slides.pdf#1
```

```pdf-page
UTF-8''Lektion_202_20slides.pdf#2
```

```pdf-page
UTF-8''Lektion_202_20slides.pdf#3
```


```pdf-page
UTF-8''Lektion_202_20slides.pdf#5
```



Noter:


# Diskret stokatiske variable og fordeling

### Diskrete stokastiske variable
Stokastisk eksperiment

S


$X: a_{1}eS \rightarrow X=x_{1}$

Diskret går ud på jeg kan tælle mine udfald ligge som sider på en terning

Udfald = x1 terning kan det kaldes 1,2,3,4,5 og 6 hvis man ville


### Probability mass function, pmf

fortæller hvor sandsyndligt et udfald er

kaldes $f$
men kan skrives som $fx$
$$ f_{x} =(x_{i})=^{def} P((X=x_{i}))$$
Pinde diagram
alt i pmf kan summers til 1 
og man kan ikke have negativ udfald
$$P(s)=1$$
### Culmulative mass function, cmf

kaldes $F$

$$
F_{x}(x_{i}) = P(X\leq x_{i})=\sum_{x_{j}\leq x_{i}} P(X=x_{})=\sum_{x_{j}\leq x_{i}} fx(x_{j})
$$

summer alt fra udfald før
Trappe diagram

*Både $f$ og $F$ kan i intergreres og diffrensere mellem sig men det er 


####  eksempler for F
hvis man vil finde sandsynligehed for interval af udfald i $f$

Udfald mellem $x_1$ og $x_2$ = $P(x_{1}<X\leq x_{2})=F_{x}(x_{2})-F_{x}(x_{1})$
kan ændres alt efter hvad < og > bliver i grænserne



## Middelværdi

$\mu_{x} = E[X] = \sum$ (mulige udfald)=sandsynlighed
$$=\sum_{x_{i}es}x_{i}fx(x_{i})$$ 

tyndepunktet i en graf

$$
E[aX+b]=E[aX]+E[b]
$$
## Variance

$\sigma_{x}²=V[X]=E[(X-\mu)²]$
$=\sum_{}(x_{i}-\mu_{x})²fx(x_{i})\geq 0$

### standardafvigelse
$$\sigma_{x}=+\sqrt{ \sigma^2_{x} }$$


## fordeling
Typer der forkommer tit


### case 1 Diskrete uniform fordeling
har en ligelig fordeling mellem a og b

$X$ ~UD(a,b), a,be Z

UD = navn
(a,b)= parameter
~: svare til fordelt som
```pdf-page
UTF-8''Lektion_202_20slides.pdf#4
```

### Case 2 binomial fordelling

kun 2 mulige udfald kaldes typisk succes eller fiasko /  true eller false

$n$= antal forsøg
$p$ = succes rate
eksemple flip en mønt


### geometrist fordelling

parameter
$p$=succesrate

X: Giver antal forsøg indtil første succes 

eks: kaster en terning indtil man rammer en 6'er



```pdf-page
UTF-8''Lektion_202_20slides.pdf#5
```

### poisson dist


$\lambda$ = ankomst intensitet 

hvad er sandsynligheden for ankomst i et tidsinterval
