Liginingssystemer med $m$ ligning og $n$ variable
- der eksistere én eller flere løsninger hvis 
$$Rang(A) = Rang(\hat A \ ) $$
- der eksistere præcis en løsning hvis 
$$rang(A) = n$$
og
$$Rang(A) = Rang(\hat A \ ) $$
- der eksistere uendelige mange løsninger hivs
$$rang(A) = rang(\hat A)$$
#### Homogene lignings systemer
af typen
$A \vec x =\vec b$ hvor $\vec b = \vec 0$ 
dvs,
$$
A\vec x =\vec o
$$
har altid løsningen $\vec x = \vec o$ som kaldes trivielle løsning
"ikke trivielle løsninger eksistere hvis $rang(A) < n$ "

$$\begin{bmatrix} 1 & 2 & -2 &0 \\ 2 & 3&1&0\\3 &5&-1&0 \end{bmatrix}$$


#### Determinanten 
General beregning af determinanten



Hvis $A$ er en $n$ X $n$ matrix er $rang(A)=n$ hvis
$$
det(A\neq o)
$$
(dvs. hvis $A\neq 0$ så findes ALTID præcis en løsning)
(hvis $det(A)=0$ så findes uendelige mange løsninger)'

###### beregning af determinanten

Hvis matirx A og et vilkårligt k jan determinanten findes vha
$$
D=\sum^n_{j=1}(-1)^{j+k} D_{jk}a_{jk}
$$
(følge søjle k)
kan også regnes (for vikårligt j)
$$
D=\sum^n_{k=1}(-1)^{j+k} D_{jk}a_{jk}
$$

$D_{jk}$ determinanten UDEN række j og søjle k og $a_{jk}$ elementer i matrix A
##### determinanten og regneoperationer
| *Operationer*                               | *betydning for determinanten*       |
| ------------------------------------------- | ----------------------------------- |
| Ombyt to rækker                             | fortegn af determinant skifter      |
| lægge rækker til en anden række             | intet                               |
| Mulitiplikation af række med konst $c\neq0$ | determinanten bliver c gange større |
|                                             |                                     |
Regneregler

$$
det(cA)=c^n * det(A)
$$
$$
det(A^T) = det(A)
$$
lad også B være nXn matrix
$$
det(AB)=det(A)*det(B) = det(B)*det(A)=det(BA)
$$


**Regneregler for A,B,C matric nxn

Hvis @rang(A) = n og AB=AC så B=C

Hvis rang(A) = n og AB = 0, så B = 0

**Robot eksempel (Rotation vektor)

$$
R(30^¤)=R({\pi\over6})=\begin{bmatrix} cos{\pi\over6} & -sin{\pi\over6} \\ sin{\pi\over6} & cos{\pi\over6} \end{bmatrix} 
=\begin {bmatrix} \sqrt3/2 &1/2 \\ 1/2 & \sqrt3/2 \end{bmatrix} 
$$

![[20241004_090127.jpg]]

***Rotations matrice regler
$$
R(30^¤)^{-1} = R(-30^¤)=R(30^¤)^T
$$

