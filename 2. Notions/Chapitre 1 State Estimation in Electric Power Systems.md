---
category: notion-note
---
> [!tldr] Summary
> .


> ## 1. Objectif de l'estimation d'état

L'objectif de l'**estimation d'état** est de déterminer l'état électrique d'un réseau à partir d'un ensemble de mesures disponibles.

Dans un réseau électrique, l'état du système est principalement décrit par :

- le **module de tension** $V_i$ de chaque bus ;
- l'**angle de tension** $\theta_i$ de chaque bus.

L'estimateur cherche donc à déterminer les valeurs de $V_i$ et $\theta_i$ qui représentent au mieux l'état réel du réseau.

---

## 2. Vecteur d'état

Le vecteur d'état regroupe les variables nécessaires pour décrire l'état du réseau.

On peut l'écrire :

$$  
x =  
\begin{bmatrix}  
\theta_1 \  
\theta_2 \  
\vdots \  
\theta_n \  
V_1 \  
V_2 \  
\vdots \  
V_n  
\end{bmatrix}  
$$

où :

- $V_i$ : module de la tension au bus $i$ ;
- $\theta_i$ : angle de la tension au bus $i$ ;
- $n$ : nombre de bus du réseau.

> **À retenir :** l'état du réseau est principalement défini par les tensions $V_i$ et leurs angles $\theta_i$.

---

## 3. Les mesures

L'état réel du réseau n'est généralement pas directement accessible.

On dispose plutôt de différentes mesures électriques, par exemple :

- puissance active $P$ ;
- puissance réactive $Q$ ;
- tension $V$ ;
- puissance active transitant sur une ligne $P_{ij}$ ;
- puissance réactive transitant sur une ligne $Q_{ij}$.

On regroupe toutes ces mesures dans un vecteur :

$$  
z =  
\begin{bmatrix}  
P_1 \  
P_2 \  
Q_1 \  
Q_2 \  
P_{12} \  
Q_{12} \  
V_1 \  
\vdots  
\end{bmatrix}  
$$

où $z$ représente le **vecteur des mesures**.

---

## 4. Relation entre l'état et les mesures

Les mesures sont liées à l'état du réseau par les lois physiques du système électrique.

On utilise généralement le modèle :

$$  
z = h(x) + e  
$$

avec :

- $z$ : vecteur des mesures ;
- $x$ : vecteur d'état ;
- $h(x)$ : fonction qui relie l'état aux mesures ;
- $e$ : vecteur des erreurs de mesure.

Cette équation est fondamentale pour toute la suite du cours.

---

## 5. Pourquoi y a-t-il une erreur ?

Les mesures réelles ne sont jamais parfaitement exactes.

Les erreurs peuvent provenir :

- des capteurs ;
- des transformateurs de mesure ;
- du bruit ;
- des erreurs de communication ;
- d'erreurs de données ;
- de défauts ou de mauvaises mesures.

On représente généralement ces erreurs par $e$ :

$$  
z = h(x) + e  
$$

L'estimateur cherche donc à trouver une valeur de $x$ qui explique au mieux les mesures disponibles.

---

## 6. Les trois éléments fondamentaux

Il faut bien distinguer :

$$  
\boxed{\text{État} \neq \text{Mesures} \neq \text{Modèle}}  
$$

### État $x$

Ce que l'on cherche à connaître :

$$  
x = [\theta_1,\ldots,\theta_n,V_1,\ldots,V_n]^T  
$$

### Mesures $z$

Ce que l'on mesure réellement :

$$  
z = [P,Q,V,P_{ij},Q_{ij},\ldots]^T  
$$

### Modèle $h(x)$

Les équations physiques qui relient l'état aux mesures.

---

## 7. Exemple simple

Pour une ligne reliant deux bus $i$ et $j$, la puissance active peut dépendre des tensions et des angles :

$$  
P_{ij} = f(V_i,V_j,\theta_i,\theta_j)  
$$

Ainsi, si l'on connaît certaines mesures de puissance et de tension, on peut utiliser les équations physiques du réseau pour estimer les variables d'état inconnues.

---

## 8. Pourquoi utiliser une estimation d'état ?

L'estimation d'état permet de :

- reconstruire l'état du réseau à partir de mesures imparfaites ;
- gérer les erreurs de mesure ;
- obtenir une représentation cohérente du réseau ;
- fournir des informations nécessaires à l'exploitation en temps réel ;
- servir de base à d'autres fonctions du système de gestion du réseau.

> [!quote] Quote
> .

