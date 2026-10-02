---
category: notion-note
---


> [!tldr] Summary
> 
## 1. Objectif du chapitre

Le **power flow** (écoulement de puissance ou calcul de répartition de puissance) consiste à déterminer les grandeurs électriques d'un réseau à partir des caractéristiques du réseau et des conditions de fonctionnement.

Les principales grandeurs étudiées sont :

- les tensions $V_i$ ;
    
- les angles de tension $\theta_i$ ;
    
- les puissances actives $P_i$ ;
    
- les puissances réactives $Q_i$ ;
    
- les flux de puissance sur les lignes $P_{ij}$ et $Q_{ij}$.
    

> **Lien avec l'estimation d'état :** les équations du power flow permettent de construire les fonctions qui relient les variables d'état aux mesures.

---

# 2. Représentation de la tension

Dans un réseau électrique, la tension complexe au bus $i$ peut être écrite :

$$  
\boxed{  
\underline{V_i}=V_i e^{j\theta_i}  
}  
$$

ou sous forme rectangulaire :
$$
\underline{V_i} = V_i(\cos\theta_i+j\sin\theta_i)
$$
où :

- $V_i$ : module de la tension (par exemple 230 volts) ;
    
- $\theta_i$ : angle de la tension ( par exemple 30 degrés) ;
    
- $j=\sqrt{-1}$.
    

Les variables $V_i$ et $\theta_i$ sont particulièrement importantes car elles constituent les principales variables d'état du réseau.

---

# 3. Matrice d'admittance du réseau

Le réseau électrique peut être représenté à l'aide de la **matrice d'admittance nodale**, appelée matrice $Y_{\text{bus}}$ :

I=YbusV\boxed{ I=Y_{\text{bus}}V }

où :

- $I$ : vecteur des courants injectés aux bus ;
    
- $V$ : vecteur des tensions aux bus ;
    
- $Y_{\text{bus}}$ : matrice d'admittance du réseau.
    

Pour un réseau comportant $n$ bus :

[I1I2⋮In]=[Y11Y12⋯Y1nY21Y22⋯Y2n⋮⋮⋱⋮Yn1Yn2⋯Ynn][V1V2⋮Vn]\begin{bmatrix} I_1\\ I_2\\ \vdots\\ I_n \end{bmatrix} = \begin{bmatrix} Y_{11}&Y_{12}&\cdots&Y_{1n}\\ Y_{21}&Y_{22}&\cdots&Y_{2n}\\ \vdots&\vdots&\ddots&\vdots\\ Y_{n1}&Y_{n2}&\cdots&Y_{nn} \end{bmatrix} \begin{bmatrix} V_1\\ V_2\\ \vdots\\ V_n \end{bmatrix}

Chaque élément $Y_{ij}$ représente une admittance associée au réseau.

---

# 4. Puissance complexe

La puissance complexe injectée au bus $i$ est :

Si=Pi+jQi\boxed{ S_i=P_i+jQ_i }

où :

- $P_i$ : puissance active ;
    
- $Q_i$ : puissance réactive.
    

La relation entre puissance, tension et courant est :

Si=ViIi∗\boxed{ S_i=V_i I_i^* }

où $I_i^*$ est le conjugué complexe du courant.

---

# 5. Équations de puissance

En utilisant :

I=YbusVI=Y_{\text{bus}}V

on peut obtenir les équations de puissance active et réactive.

Pour le bus $i$ :

Pi=∑j=1nViVj(Gijcos⁡(θi−θj)+Bijsin⁡(θi−θj))\boxed{ P_i = \sum_{j=1}^{n} V_iV_j \left( G_{ij}\cos(\theta_i-\theta_j) + B_{ij}\sin(\theta_i-\theta_j) \right) }

et :

Qi=∑j=1nViVj(Gijsin⁡(θi−θj)−Bijcos⁡(θi−θj))\boxed{ Q_i = \sum_{j=1}^{n} V_iV_j \left( G_{ij}\sin(\theta_i-\theta_j) - B_{ij}\cos(\theta_i-\theta_j) \right) }

où :

- $G_{ij}$ : partie réelle de $Y_{ij}$ ;
    
- $B_{ij}$ : partie imaginaire de $Y_{ij}$ ;
    
- $V_i,V_j$ : modules des tensions ;
    
- $\theta_i,\theta_j$ : angles des tensions.
    

> **À retenir :** les puissances $P_i$ et $Q_i$ dépendent des tensions $V$ et des angles $\theta$.

On peut donc écrire de manière simplifiée :

Pi=fi(V,θ)\boxed{ P_i=f_i(V,\theta) } Qi=gi(V,θ)\boxed{ Q_i=g_i(V,\theta) }

---

# 6. Flux de puissance sur une ligne

Pour une ligne reliant deux bus $i$ et $j$, on peut également calculer les puissances qui circulent sur la ligne.

On note généralement :

Pij,QijP_{ij},\quad Q_{ij}

pour le flux allant du bus $i$ vers le bus $j$.

Ces grandeurs dépendent notamment des tensions aux deux extrémités de la ligne :

Pij=f(Vi,Vj,θi,θj)P_{ij}=f(V_i,V_j,\theta_i,\theta_j) Qij=g(Vi,Vj,θi,θj)Q_{ij}=g(V_i,V_j,\theta_i,\theta_j)

Ces mesures de flux peuvent ensuite être utilisées par l'estimateur d'état.

---

# 7. Types de bus

Dans l'étude des réseaux électriques, les bus sont généralement classés en trois catégories.

## Bus PQ

Les puissances active et réactive sont connues :

Pi=connueP_i=\text{connue} Qi=connueQ_i=\text{connue}

Les inconnues sont généralement :

Vi,θiV_i,\quad\theta_i

---

## Bus PV

La puissance active et le module de tension sont connus :

Pi=connueP_i=\text{connue} Vi=connueV_i=\text{connue}

Les inconnues sont généralement :

Qi,θiQ_i,\quad\theta_i

---

## Bus Slack

Le bus slack (ou bus de référence) fixe la référence du système.

On connaît :

Vi=connueV_i=\text{connue} θi=connue\theta_i=\text{connue}

Le bus slack permet notamment de fixer la référence de l'angle de phase.

Généralement :

θslack=0\boxed{\theta_{\text{slack}}=0}

---

# 8. Pourquoi un bus de référence ?

Les angles de tension sont relatifs.

Si on ajoute la même constante à tous les angles, les différences :

θi−θj\theta_i-\theta_j

restent identiques.

Or les équations de puissance dépendent principalement de ces différences d'angles.

Il faut donc choisir une référence :

θref=0\boxed{\theta_{\text{ref}}=0}

Les autres angles sont alors exprimés par rapport à cette référence.

---

# 9. Lien avec l'estimation d'état

C'est probablement la partie la plus importante pour ton étude.

Dans le chapitre 1, nous avons vu :

z=h(x)+e\boxed{ z=h(x)+e }

Le chapitre 3 nous permet maintenant de comprendre ce qu'est réellement la fonction $h(x)$.

Par exemple, si l'état est :

x=[θ1θ2V1V2]x= \begin{bmatrix} \theta_1\\ \theta_2\\ V_1\\ V_2 \end{bmatrix}

une mesure de puissance active peut être écrite :

zk=Pi=hi(x)+ekz_k=P_i=h_i(x)+e_k

Une mesure de tension peut simplement être :

zk=Vi+ekz_k=V_i+e_k

Une mesure de puissance réactive peut être :

zk=Qi+ekz_k=Q_i+e_k

Ainsi, différentes mesures correspondent à différentes fonctions $h_i(x)$.

---

# 10. Exemple conceptuel

Supposons un réseau avec trois bus.

Le vecteur d'état peut être :

x=[θ1θ2θ3V1V2V3]x= \begin{bmatrix} \theta_1\\ \theta_2\\ \theta_3\\ V_1\\ V_2\\ V_3 \end{bmatrix}

On dispose par exemple des mesures :

z=[P1P2Q1V2]z= \begin{bmatrix} P_1\\ P_2\\ Q_1\\ V_2 \end{bmatrix}

On peut alors écrire :

z=h(x)+ez=h(x)+e

avec :

h(x)=[P1(x)P2(x)Q1(x)V2]h(x)= \begin{bmatrix} P_1(x)\\ P_2(x)\\ Q_1(x)\\ V_2 \end{bmatrix}

Chaque puissance $P_i$ ou $Q_i$ est calculée à partir des équations du réseau.

---

# 11. Ce qu'il faut comprendre avant le WLS

Le chapitre 3 prépare directement le chapitre 4.

Nous avons maintenant :

x→h(x)→z\boxed{x\rightarrow h(x)\rightarrow z}

c'est-à-dire :

**État du réseau**

↓

**Équations physiques du réseau**

↓

**Mesures**

Le problème de l'estimation d'état consiste ensuite à faire le chemin inverse :

z→x^\boxed{z\rightarrow\hat{x}}

À partir des mesures $z$, on cherche à retrouver l'état estimé $\hat{x}$.

Comme les mesures contiennent des erreurs, on ne peut généralement pas résoudre simplement les équations. C'est pour cela que l'on introduit ensuite la méthode **WLS (Weighted Least Squares)**.

---

# ⭐ À retenir absolument

### Tension complexe

Vi‾=Viejθi\boxed{ \underline{V_i}=V_i e^{j\theta_i} }

### Matrice d'admittance

I=YbusV\boxed{ I=Y_{\text{bus}}V }

### Puissance complexe

Si=Pi+jQi\boxed{ S_i=P_i+jQ_i }

### Puissance complexe et courant

Si=ViIi∗\boxed{ S_i=V_iI_i^* }

### Puissance active

Pi=∑j=1nViVj[Gijcos⁡(θi−θj)+Bijsin⁡(θi−θj)]\boxed{ P_i = \sum_{j=1}^{n} V_iV_j \left[ G_{ij}\cos(\theta_i-\theta_j) + B_{ij}\sin(\theta_i-\theta_j) \right] }

### Puissance réactive

Qi=∑j=1nViVj[Gijsin⁡(θi−θj)−Bijcos⁡(θi−θj)]\boxed{ Q_i = \sum_{j=1}^{n} V_iV_j \left[ G_{ij}\sin(\theta_i-\theta_j) - B_{ij}\cos(\theta_i-\theta_j) \right] }

### Équation fondamentale de l'estimation

z=h(x)+e\boxed{ z=h(x)+e }

### Idée fondamentale

> **Les équations du power flow permettent de relier les variables d'état $V$ et $\theta$ aux grandeurs mesurées $P$, $Q$ et $V$. Ces relations constituent la fonction $h(x)$ utilisée par l'estimateur d'état.**

---

# 🧠 Résumé en une phrase

> **Le power flow décrit comment les tensions et les angles du réseau déterminent les puissances et les flux électriques ; ces relations physiques sont ensuite utilisées par l'estimation d'état pour retrouver les tensions et angles à partir des mesures.**

> [!quote] Quote
> .

