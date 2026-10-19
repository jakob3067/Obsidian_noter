løse $A\vec x, x \ ikke \  0$ 

Egenværdi  er 
$$
det(A-\lambda I )=0
$$
for hver egenværdi findes en egenvector

$$(A-\lambda I ) \vec x = \vec 0$$
for nxn matrix findes mindst 1 egenværdi og maks n egenværdier

eks. 
$$
\begin{bmatrix} -5 & 2 \\ 2 & -2 \end{bmatrix}=A$$
karaktiske ligning

$Det(A-\lambda I ) = 0$ 

### Eksempel
Eksempel

$$
A-\lambda I=\begin{bmatrix} -5 & 2 \\ 2 & -2 \end{bmatrix}- \lambda\begin{bmatrix} 1 & 0 \\ 0 & 1 \end{bmatrix}$$
$$
=\begin{bmatrix} -5\lambda & 2 \\ 2 & -2\lambda \end{bmatrix}
$$
$$
det\begin{bmatrix} -5\lambda & 2 \\ 2 & -2\lambda \end{bmatrix}=0
$$
Omskrevet og regnet til
$$
\lambda^2+7\lambda+6=0
$$
$$
\lambda =  {-7 \pm \sqrt{7^2-4*1*6} \over 2*1}={-7\pm5\over 2}= \lambda =-1,\lambda=-6
$$
for lambda = -1

$$
(A-\lambda,I)\vec x= \vec 0
$$

$$
A-\lambda,I= \begin{bmatrix} -5 -(-1) & 2 \\ 2 & -2-(-1) \end {bmatrix}
$$
$$=\begin {bmatrix} -4& 2 \\ 2 & -1 \end{bmatrix}$$
fortsætter i billeder
![[20241004_094445 1.jpg]]
![[20241004_094457.jpg]]

Eks. 2 billede
![[20241004_095633.jpg]]

#### Hvad kan det bruges til
Bestemme "spredningen"/retningen af en 'blob' eller datapunkter

![[Pasted image 20241004100252.png]]

Finder de vektorer der går længst og kortest i data sættet hvor begge er 

$$
\vec u={1 \over n}({\sum x\over\sum y})={\hat x \over \hat y}
$$
Afvigelse fra u vector

$$
B=X-h\vec u^T \ , \ h =\begin{bmatrix} 1 \\ 1\\1\\1\\...\\1\end{bmatrix} Med \ n \ rækker
$$
Covarians matrix

$$
C= {1 \over n-1}B^T*B
$$
(B indeholder reele tal)

Bestem egenværdier og tilhørende egenvekturer til C

Egenvektor $\vec V_1$ til største egen værdi
 - Retning af største dataspredning
 Egenvektor $\vec V_2$ til mindste egenværdi
 * retning af mindste dataspredning
$W = [\vec V_1 \vec V_2]$ 
så
$T=BW$ (projicere data ind op akserne for dataspredning)