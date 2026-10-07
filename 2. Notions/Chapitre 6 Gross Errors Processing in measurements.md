---
category: notion-note
---

> [!tldr] Summary
> .

## 1. Objectif du chapitre

Le chapitre 6 s'intéresse aux "gross errors", c'est-à-dire aux erreurs importantes présentes dans les mesures.

On a toujours le modèle :

$$
\boxed{
z=
\mathbf{h}(\mathbf{x})  
+  
\mathbf{e}  
}
$$

où $\mathbf{e}$ représente les erreurs de mesure.

L'objectif est maintenant de détecter si une mesure contient une **erreur anormalement importante**.

## 2. Erreur normale vs erreur grossière

Toutes les mesures contiennent généralement de petites erreurs.

### Erreur normale

Elle est due par exemple à :

- bruit des capteurs ;
- précision limitée des appareils ;
- erreurs de transmission ;
- petites perturbations.

On suppose généralement :

$$  
e_i \sim \mathcal{N}(0,\sigma_i^2)  
$$

Ces erreurs sont considérées comme normales.

### Gross error

Une **gross error** est une erreur beaucoup plus importante que l'erreur normale.

Elle peut être due à :

- un capteur défaillant ;
- une mauvaise communication ;
- une erreur de configuration ;
- une donnée mal enregistrée ;
- une mesure corrompue.

On peut représenter :

$$
h_i(\mathbf{x})  
+  
e_i  
+  
b_i  
$$

où $b_i$ représente une erreur importante (_biais_).

## 3. Pourquoi les gross errors sont dangereuses ?

Une mauvaise mesure peut influencer fortement l'estimation WLS.

On cherche donc à éviter :

$$  
\text{mauvaise mesure}  
\rightarrow  
\text{mauvaise estimation de } \mathbf{x}  
$$

L'objectif est :

$$  
\boxed{  
\text{Détecter}  
\rightarrow  
\text{Identifier}  
\rightarrow  
\text{Traiter}  
}  
$$

---

## 4. Résidus

Après l'estimation, on peut comparer les mesures réelles aux mesures calculées.

On définit le résidu :

 
$$
\mathbf{z}
-
\mathbf{h}(\hat{\mathbf{x}})  

$$

où :

- $\mathbf{z}$ : mesures réelles ;
- $\hat{\mathbf{x}}$ : état estimé ;
- $\mathbf{h}(\hat{\mathbf{x}})$ : mesures prédites à partir de l'état estimé.

Pour une mesure particulière :
$$
z_i-h_i(\hat{\mathbf{x}})  
$$
### Interprétation

Si le modèle et les mesures sont cohérents :

$$  
r_i \approx 0  
$$

Si une mesure est très différente de la valeur calculée :

$$  
|r_i| \gg 0  
$$

elle peut être **suspecte** et contenir une gross error.

### Exemple

Si la mesure réelle est :

$$  
z_i=100  
$$

et que l'estimation prédit :

$$  
h_i(\hat{\mathbf{x}})=98  
$$

alors :

$$  
r_i=100-98=2  
$$

Le résidu est donc :

$$  
\boxed{r_i=2}  
$$