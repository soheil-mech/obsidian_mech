---
category: notion-note
---

> [!tldr] Summary
> .


## 1. Objectif du chapitre

Le chapitre 5 cherche à répondre à une question fondamentale :

> **Est-ce que les mesures disponibles permettent de déterminer l'état du réseau ?**

On part toujours du modèle :

$$  
\mathbf{z}=\mathbf{h}(\mathbf{x})+\mathbf{e}  
$$

avec :

- $\mathbf{x}$ : vecteur d'état du réseau
- $\mathbf{z}$ : vecteur des mesures
- $\mathbf{h}(\mathbf{x})$ : modèle de mesure
- $\mathbf{e}$ : erreurs de mesure

---

## 2. Observabilité

Un réseau est **observable** si les mesures disponibles contiennent suffisamment d'informations indépendantes pour déterminer l'état du réseau.

On peut résumer :
$$
\text{possibilite de déterminer } \mathbf{x}  
\text{ à partir de } \mathbf{z}  
}  
$$

L'objectif est donc de pouvoir passer de :

$$  
\mathbf{z}  
\longrightarrow  
\hat{\mathbf{x}}  
$$

---

## 3. Exemple simple

Supposons que l'état soit :

\begin{bmatrix}  
\theta_1\  
\theta_2\  
V_1\  
V_2  
\end{bmatrix}  
$$

On dispose de plusieurs mesures :

\begin{bmatrix}  
P_1\  
Q_1\  
P_2\  
V_2  
\end{bmatrix}  
$$

Ces mesures peuvent fournir suffisamment d'informations pour déterminer les variables de $\mathbf{x}$.

À l'inverse, avec seulement :

\begin{bmatrix}  
P_1  
\end{bmatrix}  
$$

on ne possède pas suffisamment d'informations pour déterminer tout l'état du réseau.

---

## 4. Le nombre de mesures ne suffit pas

Avoir beaucoup de mesures ne garantit pas l'observabilité.

Les mesures doivent fournir des **informations indépendantes**.

Par exemple :

$$  
z_1=V_1  
$$

et

$$  
z_2=V_1  
$$

constituent deux mesures, mais elles apportent essentiellement la même information.

Il faut donc que les mesures soient suffisamment indépendantes pour permettre de déterminer les différentes variables d'état.

---

## 5. Matrice Jacobienne $H$

Dans le chapitre précédent, nous avons introduit la matrice :

$$  
\boxed{  
H=  
\frac{\partial \mathbf{h}}{\partial \mathbf{x}}  
}  
$$

$H$ est la **matrice Jacobienne du modèle de mesure**.

Elle indique comment les mesures varient lorsque les variables d'état varient.

Pour l'observabilité, on étudie notamment le **rang de $H$**.

Si $n$ est le nombre de variables d'état indépendantes :

$$  
\boxed{  
\operatorname{rank}(H)=n  
}  
$$

alors le système est observable.

---

## 6. Redondance des mesures

La **redondance** correspond au fait d'avoir plus de mesures que le minimum nécessaire pour déterminer l'état.

Par exemple, si le système possède :

$$  
n=5  
$$

variables d'état indépendantes et que l'on dispose de :

$$  
m=8  
$$

mesures indépendantes, on possède des informations supplémentaires.

On peut résumer :

$$  
\boxed{  
\text{Observabilité}  
\rightarrow  
\text{Peut-on déterminer l'état ?}  
}  
$$

$$  
\boxed{  
\text{Redondance}  
\rightarrow  
\text{Avons-nous des informations supplémentaires ?}  
}  
$$

---

## 7. Trois situations

### Cas 1 — Juste suffisamment de mesures

$$  
m=n  
$$

Si les mesures sont indépendantes :

$$  
\text{Système observable}  
$$

---

### Cas 2 — Mesures redondantes

$$  
m>n  
$$

On possède plus de mesures que nécessaire.

Cela permet notamment :

- d'améliorer l'estimation ;
- de réduire l'influence du bruit ;
- de détecter certaines mauvaises mesures ;
- d'améliorer la robustesse de l'estimation.

---

### Cas 3 — Pas suffisamment d'informations

Si les mesures disponibles ne permettent pas d'obtenir suffisamment d'informations indépendantes :

$$  
\operatorname{rank}(H)<n  
$$

alors :

$$  
\boxed{  
\text{Système non observable}  
}  
$$
