---
layout: post
title: "Preuves mathématiques"
categories: Science
comments: true
---

# Avant propos

Ce travail repose sur celui de Alistair Savage, à propos de raisonnement
mathématique et preuves, et plus précisément sur la traduction de Simon Fortier-Garceau.

Ainsi, cet article est soumis à la licence [Attribution-ShareAlike 4.0 International](https://creativecommons.org/licenses/by-sa/4.0/).

# Définitions

On note l’ensemble des *entiers* l’ensemble $$\mathbb Z$$.

L’opérateur « + » est binaire (c’est-à-dire qu’il possède deux opérandes) et s’appelle l’addition.
L’addition s’applique sur les nombres entiers.

L’opérateur « · » est aussi binaire et s’appelle la multiplication. Elle s’applique aussi sur les
nombres entiers.

On appelle juxtaposition le fait de poser des éléments côte à côte, sans liaison. Lorsque nous
juxtaposons deux éléments $$a$$ et $$b$$, nous écrivons $$ab$$.

$$a · b$$ (a multiplié par b) peut s’écrire $$ab$$.

Un axiome est, par définition, un concept évident de lui-même. C’est-à-dire que,
dans un contexte mathématique, sa démonstration (preuve) n’est pas nécessaire.


# Axiomes


Nous élaborerons une liste numérotée d’axiomes et les utiliserons pour démontrer
que des propositions sont vraies (ou fausses !).

À noter que les propositions précédemment démontrées peuvent être réutilisées
dans d’autres preuves plus conséquentes. Inutile de se répéter.

**Axiome 1** : $$a + b = b + a$$. L’addition est dite **commutative**.

**Axiome 2** : $$(a + b) + c = a + (b + c)$$. L’addition est dite **associative**.

**Axiome 3** : $$a · (b + c) = a · b + a · c$$. La multiplication est dite **distributive**.

**Axiome 4** : $$a · b = b · a$$. La multiplication est aussi **commutative**.

**Axiome 5** : $$(a · b) · c = a · (b · c)$$. La multiplication est aussi **associative**.

**Axiome 6** : $$\exists 0 \in \mathbb{Z} : \forall a \in \mathbb{Z}, a + 0 = a$$. Traduction : « il existe un élément $$0$$ dans l’ensemble des entiers relatifs ($$\mathbb Z$$) tel que pour chaque entier relatif a, $$a + 0 = a$$ ». Autrement dit, $$0$$ est l’**élément neutre additif** ou **élément identité de l’addition**.

**Axiome 7** : $$\exists 1 \in \mathbb{Z} : 1 \neq 0 \wedge \forall a \in \mathbb{Z},  a · 1 = a$$. Traduction : « Il existe un élément $$1$$ dans l’ensemble des entiers relatifs ($$\mathbb Z$$) tel que 1 est différent de 0 et que $$a · 1 = a$$. Autrement dit, $$1$$ est l’**élément neutre multiplicatif** ou **élément identité de la multiplication**.

**Axiome 8** : $$\forall a \in \mathbb{Z}, \exists{(-a)} \in \mathbb{Z} : a + (-a) = 0$$. Traduction : « Pour chaque entier relatif $$a$$, il existe un entier relatif $$-a$$ tel que $$a + (-a) = 0$$. L’élément $$-a$$ est l’**inverse additif** de $$a$$.

**Axiome 9** : $$\forall a, b, c \in \mathbb{Z}, a · b = a · c \wedge a \neq 0 \Longrightarrow b = c$$. Traduction : « Pour tout entiers relatifs $$a$$, $$b$$ et $$c$$, si $$a · b = a · c$$ et $$a \neq 0$$, alors b = c. Il s’agit de la **propriété d’annulation** (on peut supprimer a de part et d’autre de l’égalité).

**Axiome 10** : $$\forall a, \in \mathbb{Z}, a = a$$. Traduction : « pour tout entier relatif $$a$$, $$a$$ est égal à $$a$$. Plus simplement : l’égalité est **réflexive**.

**Axiome 11** : $$\forall a, b \in \mathbb{Z}, a = b \Longrightarrow b = a$$. Traduction : « si $$a$$ est égal à $$b$$, alors $$b$$ est égal à $$a$$ ». Autrement : l’égalité est **symétrique**.

**Axiome 12** : $$\forall a, b, c \in \mathbb{Z}, a = b \wedge b = c \Longrightarrow a = c$$. Traduction : « si a est égal à b et b est égal à c, alors a est égal à c ». L’égalité est **transitive**.

**Axiome 13** : $$\forall a, b, c \in \mathbb{Z}, a = b \Longrightarrow a + c = b + c$$. Traduction : « pour tous entiers relatifs $$a$$, $$b$$ et $$c$$,
si $$a$$ est égal à $$b$$, alors $$a + c$$ est égal à $$b + c$$ ». Dit plus simplement : si on a $$a = b$$ alors a peut être substitué par b sans changer le sens de l’expression.

**Axiome 14** : $$\forall{a} \in \mathbb{Z}, \neg(a \neq a)$$. Traduction : « Pour tout entier relatif a, l’inégalité a ≠ a est fausse. Autrement dit, l’opérateur $$≠$$ n’est pas réflexif. Cet axiome peut sembler trivial car il semble redondant avec l’axiome 10, mais il souligne le fait que **l’inégalité n’est pas réflexive**.

**Axiome 15** : $$\forall a, b \in \mathbb{Z}, a \neq b  \Longrightarrow b \neq a$$. Traduction : « Pour tous entiers relatifs a et b, si a est différent de b, alors b est différent de a ». **L’inégalité est symétrique**.

**Axiome 16** : $$\exists 2 \in \mathbb{Z}, 1 \neq 2 \wedge 2 \neq 1 \wedge \neg(1 \neq 1)$$. Traduction : « Il existe un entier relatif 2 tel que 2 est différent de 1, 1 est différent de 2 et l’inégalité 1 ≠ 1 est fausse. Il sert à souligner que **l’inégalité n’est pas transitive**.

Nous avons à notre disposition 16 axiomes. À partir de ceux-là, nous pouvons prouver des propositions.

# Propositions

**Proposition 1** : $$\forall a, b, c \in \mathbb{Z}, (a + b)c = ac + bc$$.

Commençons par traduire la proposition pour mieux la comprendre : « pour tous entiers relatifs a, b et c, on a
$$(a + b)c = ac + bc$$.

Pour prouver cela, nous allons utiliser les axiomes à notre disposition pour exprimer différemment $$(a + b)c$$. On remarque que les
expressions $$(a + b)$$ et $$c$$ sont juxtaposées. Donc l’opérateur multiplication est utilisé.

Ensuite, d’après l’axiome 4, la multiplication est commutative. Alors nous avons le droit d’écrire :

$$(a + b)c = c(a + b)$$

Nous utilisons ensuite l’axiome 3 qui atteste que la multiplication est distributive, ainsi :

$$c(a + b) = c · a + c · b = ca + cb$$

Note : on utilise la juxtaposition pour écrire $$ca + cb$$ à des fins de lisibilité, mais notez le développement de la
distributivité en accord avec l’axiome 3.

Enfin, nous nous basons de nouveau sur l’axiome 4 sur la commutativité de la multiplication. Nous pouvons donc écrire :

$$ca + cb = ac + bc$$

Preuve complete :

$$
\begin{aligned}
(a + b)c &= c(a + b) \\
         &= ca + cb \\
         &= ac + bc
\end{aligned}
$$

Grâce à cette proposition prouvée formellement, nous pouvons nous en servir dans d’autres preuves, en « raccourcissant »
le fait que $$(a + b)c = ac + bc$$ sans devoir nous justifier autre que d’indiquer « d’après la proposition 1 ».

**Proposition 2** : $$\forall a \in \mathbb{Z}, 0 + a = a \wedge 1 · a = a$$.

Pour tout entier relatif a, les égalités 0 + a = a et 1 · a = a sont vraies.

Preuve : d’après l’axiome 1, l’addition est commutative. Ainsi :

$$0 + a = a + 0$$

De plus, d’après l’axome 6, il existe un entier relatif 0 tel que $$a + 0 = a$$ ($$0$$ est l’élément neutre additif).

Nous avons prouvé que $$0 + a = a + 0 = a$$, mais la preuve ne s’arrête pas là.

D’après l’axiome 4, la multiplication est commutative. Ainsi :

$$1 · a = a · 1$$

Ensuite, d’après l’axiome 7, il existe un entier relatif 1 tel que $$a · 1 = a$$ ($$1$$ est l’élément neutre multiplicatif, ou élément identité de la multiplication).

Nous avons également prouvé que $$1 · a = a · 1 = a$$.

Par conséquent, pour tout entier relatif a, nous avons bien $$0 + a = a$$ **et** $$1 · a = a$$.


**Proposition 3** : $$\forall a \in \mathbb Z, (-a) + a = 0$$

Pour tout entier relatif a, l’égalité (-a) + a = 0 est vraie.

Preuve : on utilise l’axiome 1 (commutativité de l’addition) et l’axiome 8 sur l’inverse additif. Ainsi :

$$\begin{aligned}
(-a) + a &= a + (-a) \ \ &(axiome\ 1) \\
        &= 0\ \ &(axiome\ 8)
\end{aligned}
$$

**Proposition 4** : $$\forall a, b, c \in \mathbb{Z}, a + b = a + c \Longrightarrow b = c$$

Pour tous $$a$$, $$b$$ et $$c$$ entiers relatifs, si $$a + b = a + c$$ alors $$b = c$$.

Preuve : d’après l’axiome 13, si $$a + b = a + c$$ alors $$a + b + (-a) = a + c + (-a)$$. En effet,
dans l’hypothèse où on a $$a + b = a + c$$, on peut alors substituer $$a + b$$ à $$a + c$$ et *vice versa*.
Il est donc possible d’ajouter un entier relatif des deux côtés de l’addition.

Ensuite, étant donné que l’addition est commutative (axiome 1), on a :

$$a + b + (-a) = a + c + (-a) \Longrightarrow a + (-a) + b = a + (-a) + c$$

D’après l’axiome 8, il existe un inverse additif $$(-a)$$ de $$a$$ tel que $$a + (-a) = 0$$. Ainsi :

$$a + (-a) + b = a + (-a) + c \Longrightarrow 0 + b = 0 + c$$

Grâce à la proposition 1, nous avons montré que pour tout entier relatif $$a$$, on a $$0 + a = a$$.

Ainsi : $$0 + b = 0 + c \Longrightarrow b = c$$.

**Proposition 5** : $$\forall a, b \in \mathbb{Z}, a + b = 0 \Longrightarrow b = -a$$.

Pour tous entiers relatifs $$a$$ et $$b$$, si $$a + b = 0$$ alors $$b = -a$$.

Preuve : d’après l’axiome 13 :

$$a + b = 0 \Longrightarrow (-a) + a + b = (-a) + 0$$

D’après l’axiome 6 sur l’élément neutre additif, $$(-a) + 0 = a$$. Ainsi :

$$(-a) + a + b = (-a) + 0 \Longrightarrow (-a) + a + b = -a$$

D’après l’axiome 8 sur l’inverse additif, on a : $$(-a) + a + b = 0 + b$$. Aainsi :

$$(-a) + a + b = -a \Longrightarrow 0 + b = -a$$

On se sert de la proposition 2 où nous avons démontré que pour tout entier relatif $$a$$, on a $$0 + a = a$$. Ainsi :

$$0 + b = -a \Longrightarrow b = -a$$

**Proposition 6** : $$\forall a,b,c,d \in \mathbb{Z}, (a + b)(c + d) = (ac + bc) + (ad + bd)$$

Pour cette proposition, nous écrirons la preuve complète avec les axiomes directement afin d’être plus concis, étant donné
que nos propositions précédentes ont été suffisamment « verbeuses » à des fins didactiques. Notez cependant que la démarche reste la même.

Preuve :

$$
\begin{aligned}
(a + b)(c + d) &= (a + b)c + (a + b)d & (axiome\ 3) \\
               &= c(a + b) + d(a + b) & (axiome\ 4) \\
               &= (ca + cb) + (da + db)   & (axiome\ 3) \\
               &= (ac + bc) + (ad + bd)   & (axiome\ 4)
\end{aligned}
$$

Remarque : on constate que des opérations que l’on considérait comme acquises lors de nos études reposent en fait sur des axiomes et
des démonstrations rigoureuses. Grâce à la proposition 6, nous pouvons désormais développer un produit rapidement, sans avoir à refaire la démonstration
qui repose sur les axiomes de la commutativité et de la distributivité de la multiplication. Chose que nous
faisions déjà « par cœur » à une certaine étape de notre éducation mathématique.

**Proposition 7** : $$\forall a, b, c, d \in \mathbb{Z}, a + (b + (c + d)) = (a + b) + (c + d) = ((a + b) + c) + d$$

Nous nous servirons le l’axiome 2 sur l’associativité de l’opérateur addition.

Ainsi :

$$
\begin{aligned}
a + (b + (c + d)) &= (a + b) + (c + d) & (axiome\ 2)
                  &= ((a + b) + c) + d & (axiome\ 2)
\end{aligned}
$$

Si la démonstration vous perturbe, reprenez l’axiome 2 : $$(a + b) + c = a + (b + c)$$ Pour mieux imager et éviter
toute ambiguïté, utilisons à la place des lettres grecques pour l’axiome : $$(\alpha + \beta) + \gamma = \alpha + (\beta + \gamma)$$.

Dans notre proposition, on retrouve bien :

$$
\begin{aligned}
\alpha &= a
\beta  &= b
\gamma &= c + d
\end{aligned}

Et nous avons une forme de départ $$a + (b + c)$$. Grâce à l’axiome 4 de la commutativité, on peut écrire :

$$\alpha + (\beta + \gamma) = (\alpha + \beta) + \gamma$$

Ainsi :

$$a + (b + (c + d)) = (a + b) + (c + d)$$

C’est pourquoi la démonstration n’a pris qu’une étape, sauf qu’en réalité nous avons utilisé deux axiomes.
Notez qu’elle reste parfaitement correcte.