---
category: notion-note
---
````
## Réseau électrique à 3 bus

```mermaid
flowchart LR

    B1["BUS 1<br/>V₁ ∠ θ₁<br/>P₁, Q₁"]
    B2["BUS 2<br/>V₂ ∠ θ₂<br/>P₂, Q₂"]
    B3["BUS 3<br/>V₃ ∠ θ₃<br/>P₃, Q₃"]

    B1 -->|"I₁₂<br/>Y₁₂ = G₁₂ + jB₁₂"| B2
    B1 -->|"I₁₃<br/>Y₁₃ = G₁₃ + jB₁₃"| B3
    B2 -->|"I₂₃<br/>Y₂₃ = G₂₃ + jB₂₃"| B3
````

### Vecteur d'état
$$
\begin{bmatrix}  
\theta_1\  
\theta_2\  
\theta_3\  
V_1\  
V_2\  
V_3  
\end{bmatrix}  
$$

### Matrice d'admittance
$$
\begin{bmatrix}  
Y_{11} & Y_{12} & Y_{13}\  
Y_{21} & Y_{22} & Y_{23}\  
Y_{31} & Y_{32} & Y_{33}  
\end{bmatrix}  
$$

### Relation courant-tension

$$\mathbf{Y}_{\mathrm{bus}}\mathbf{V}  
$$

### Courant au bus $i$

$$\sum_{j=1}^{3}  
Y_{ij}\underline{V_j}  
$$

### Puissance complexe

$$\underline{V_i}\underline{I_i}^{,*}  
$$

$$P_i+jQ_i  
$$

### Pour les trois bus

$$P_1+jQ_1  
$$

$$P_2+jQ_2  
$$

$$P_3+jQ_3  
$$

### Chaîne physique

$$  
\boxed{  
V_i,\theta_i  
\longrightarrow  
\underline{V_i}  
\longrightarrow  
\underline{I_i}  
\longrightarrow  
P_i,Q_i  
}  
$$

### Lien avec l'estimation d'état

$$  
\boxed{  
\mathbf{x}  
\longrightarrow  
\mathbf{h}(\mathbf{x})  
\longrightarrow  
\mathbf{z}  
}  
$$

avec :

$$\begin{bmatrix}  
\theta_1 & \theta_2 & \theta_3 &  
V_1 & V_2 & V_3  
\end{bmatrix}^{T}  
$$

et les mesures possibles :

$$\begin{bmatrix}  
P_1 & P_2 & P_3 &  
Q_1 & Q_2 & Q_3 &  
V_1 & V_2 & V_3  
\end{bmatrix}^{T}  
$$
