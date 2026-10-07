---
category: notion-note
---

> [!tldr] Summary
> .

# 1. Error masking

C'est probablement **le concept le plus important du chapitre**.

Imaginons une mesure :

$$
z_i
=
h_i(\mathbf{x})
+
e_i
$$

avec une grosse erreur $e_i$.

On pourrait s'attendre à obtenir un gros résidu :

$$
r_i
=
z_i-h_i(\hat{\mathbf{x}})
$$

Mais ce n'est pas nécessairement le cas.

L'estimation WLS utilise **toutes les mesures simultanément**. Une erreur importante dans une mesure peut donc être partiellement « absorbée » par l'estimation de l'état.

On peut avoir :

$$
\boxed{
\text{Gross Error important}
\not\Rightarrow
\text{résidu important}
}
$$

C'est ce phénomène que le livre appelle **error masking**.


# 2. Pourquoi c'est un problème pour WLS ?

Les méthodes classiques de détection des gross errors utilisent les résidus du WLS.

Schématiquement :

$$
\mathbf{z}
\rightarrow
\text{WLS}
\rightarrow
\hat{\mathbf{x}}
\rightarrow
\mathbf{r}
\rightarrow
\text{détection GE}
$$

Mais si l'erreur est masquée :

$$
\boxed{
\text{GE}
\rightarrow
\text{résidu faible}
\rightarrow
\text{GE non détectée}
}
$$

C'est donc une limitation importante des méthodes classiques.


# 3. Composed Measurement Error — CME

Le chapitre introduit ensuite le concept de **Composed Measurement Error (CME)**.

L'idée est qu'une mesure peut être affectée par plusieurs contributions d'erreur qui, ensemble, déterminent l'erreur effectivement présente dans la mesure.

On peut représenter conceptuellement :

$$
\boxed{
\text{CME}
=
\text{erreurs composant l'erreur de mesure}
}
$$

Le CME est utilisé pour analyser plus précisément **comment les différentes erreurs se combinent**.


# 4. Normalized Composed Error — CNE

Le chapitre introduit également le **Normalized Composed Error (CNE)**.

L'objectif est de normaliser l'erreur composée afin de pouvoir comparer les erreurs de différentes mesures sur une base commune.

Conceptuellement :

$$
\boxed{
\text{CME}
\rightarrow
\text{normalisation}
\rightarrow
\text{CNE}
}
$$

Le CNE devient donc un outil pour analyser la gravité et les caractéristiques des erreurs de mesure.


# 5. Innovation Index — II

Et là arrive le concept central du chapitre :

$$
\boxed{
\text{Innovation Index (II)}
}
$$

L'Innovation Index sert notamment à **caractériser les mesures selon leur capacité à masquer leurs propres erreurs**.




# 6. L'idée intuitive de l'Innovation Index

Imagine deux mesures qui ont exactement la même grosse erreur.

### Mesure A

Son erreur provoque un très gros changement dans le résidu :

$$
\text{GE}
\rightarrow
\text{grand résidu}
$$

Elle est donc facile à détecter.

### Mesure B

Son erreur est en grande partie absorbée par l'estimation :

$$
\text{GE}
\rightarrow
\text{petit résidu}
$$

Elle est donc difficile à détecter.

L'Innovation Index permet justement de **caractériser cette différence de comportement**.