---
layout: post
title: "Dummy, mon meilleur échec"
---

# Dummy, mon meilleur échec

J’ai, pendant plusieurs semaines, nourri cette idée de billet dans mon esprit.
C’est la première fois depuis toute mon épopée de programmeur amateur que je
trouve enfin le recul et le courage d’écrire un billet sur un retour
d’expérience à partager.

Il y a deux ans, avec un pote, on a fait le pari fou d’écrire un moteur de
MMORPG pour copier (en "mieux") un MMOPRG 2D qu’on aime bien et qui résiste
incroyablement bien à travers le temps : [Slayers Online](http://slayersonline.net/).

Tout est parti d’un début d’interface d’éditeur de cartes fait par Grindewald
avec le langage C++ au moyen du framework Qt pendant l’été 2018. À partir de
cet éditeur, on voulait être capable d’ouvrir, éditer des cartes et les
sauvegarder.

Qt est un de mes tout premiers amours en terme de développement. D’abord parce
que j’affectionne C++ à titre personnel (à noter que le choix de ce langage
dans le projet Dummy n’avait absolument rien de rationnel) ensuite parce que
j’aime aussi faire de la GUI (entre autre choses, ce que les recruteurs qui
croisaient des gens hyper-spécialisés en entretien ont toujours eu beaucoup
de mal à comprendre).

C’était donc pour moi l’occasion rêvée de m’y remettre, d’abord parce que je
voulais aider Grindewald, ensuite parce que j’aimais les outils qu’il
utilisait.

Et après, ça a été une vague de motivations et de démotivations jusqu’à ce
jour, où je lève enfin le drapeau blanc.

## Première erreur : voir les choses en trop grand

Je me suis rendu compte de cette erreur plus tard, lorsque Poulpette – une
brillante camarade que je salue au passage — m’a montré en toute innocente une
vidéo super intéressante sur le développement du jeu-vidéo:

<iframe width="560" height="315" src="https://www.youtube.com/embed/UvCri1tqIxQ" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

Dans les grandes lignes, cette vidéo explique **tout le contraire de ce que j’ai fait sur Dummy**.
À savoir, l’importance d’aboutir à quelque chose de minimaliste en peu de temps. On appelle ça
un *Minimum Viable Product*.

L’intérêt est de démontrer la faisabilité d’un projet en un temps réduit. Pour
la faisabilité, on n’avait aucun souci par rapport à ça : j’avais confiance en
mes compétences. Pour le temps réduit, eh bien, le gros problème, c’est
**qu’on ne s’est jamais fixé de deadline**. On se disait qu’on avait le temps.
Et qu’on faisait ça sur notre temps libre sachant qu’on avait notre travail /
nos études à côté.

**Se dire qu’on a le temps, quand on voit les choses en trop grand et non à des fins commerciales, c’est le meilleur moyen de n’aboutir à nulle part.**

Certains dirons : « t’as quand même appris de trucs et progressé en C++. »
D’autres dirons que j’ai perdu mon temps. Je suis plus de l’avis de ces premiers.
Même si on n’a abouti à rien de concret, cette expérience était tellement
enrichissante que je peux me targuer de faire un billet à ce sujet, et éventuellement
transmettre des conseils à mes successeurs (**ou, du moins, à qui voudra bien m’écouter**).

## Deuxième erreur : trop s’inspirer d’un projet existant

J’aime la plupart des MMORPG. Même si je n’y joue plus aujourd’hui, bosser sur
Dummy était pour moi une suite tout à fait logique. J’ai fini par avoir ce
sentiment de perdre du temps à jouer. Alors je voulais moi-même créer un jeu-vidéo
avec le contenu que je choisirai, qui serait tout aussi agréable. Enfin, je
m’égare.

À vouloir s’inspirer de Slayers Online, je me suis mis très tôt des bâtons dans
les roues sur la partie conception. Avec Grindewald, on est parti sur des cartes
dont les tuiles mesuraient 16 par 16 pixels. « Parce que Slayers Online fait pareil. »
Et puis on a fait pareil pour les cases bloquantes (pour les collisions).
« Parce que Slayers Online fait pareil. » Et puis on s’est dit « Non mais en fait c’est
mieux d’augmenter la granuralité des cases bloquantes pour avoir des collisions plus
fines. » Donc on est parti sur du 8 par 8 pixel.

Dès le début on a été influencé sur des détails qui m’ont fait
**me casser la tête sur des trucs qui n’étaient pas prioritaires**. On est
rentré trop vite dans des détails qui devaient être discutés bien plus tard
(mais pas trop non plus si on voulait sortir quelque chose rapidement).

À la place, on aurait dû apprendre à coder un jeu-vidéo tout ce qu’il y a de
plus simple, type ARPG, sans se soucier de la partie réseau / format des maps
/ etc.

Et puis j’ai joué aussi à Guild Wars 2. Tout comme World of Warcraft et sans
doute d’autres MMORPG, on peut sélectionner un de nos personnages après
connexion sur le jeu.

Pour vous convaincre, voici une capture d’écran de l’interface de sélection
des personnages sur Guild Wars 2 :

![Guild Wars 2](/assets/2020-22-02-dummy/gw2.png)

Et maintenant, voici l’écran que j’avais commencé à faire sur le client de
Dummy :

![Dummy](/assets/2020-22-02-dummy/dummy_launcher.png)

On voit bien l’influence.

Ça aussi, **ce n’était pas une chose sur laquelle j’aurais dû passer trop de temps.**
Car non seulement je n’ai pas fait de choix technique raisonnable à partir sur
SFML « parce que c’est populaire », mais en plus parce que je me suis dit :
« tiens, je vais faire mon propre moteur d’interface graphique pour ma HUD ».
Pour comprendre comment ça fonctionne sous le capot, c’est bien (et c’était
franchement un de mes objectifs au travers de ce projet), mais si on veut
livrer dès que possible, c’est moins bien. Et puis, encore une fois, **c’est pas prioritaire**.

Mais on y reviendra, sur ce qui est prioritaire. Je vais détailler ma démarche en parlant
de ma troisième erreur.

## Troisième erreur : mettre la charrue avant les bœufs

Eh oui ! On est parti d’un éditeur et c’était pas une si mauvaise idée tout compte fait
(enfin, si, mais j’y reviendrai plus tard).

Là où j’ai merdé, et où ça rejoint ma première erreur qui a été de voir les
choses en grand, c’est que j’étais parti pour m’intéresser à la partie serveur
car j’étais très peu serein à ce niveau-là. Je me posais des questions comme :

- « Comment je gère l’état où je me connecte et sélectionne un personnage ? »
- « Comment je gère l’état où j’aurai 10 000 joueurs simultanés que je veux distribuer sur plusieurs serveurs ? »
- « Comment je gère la communication entre tous mes serveurs pour qu’elle se fasse de manière sécurisée ? »
- « Avec quel outil je fais ça ? Oh, y a Boost qui a l’air pas mal ! »

Pour rebondir sur la dernière question, parlons-en ! J’ai donc utilisé Qt et SFML. Ces
choix, comme C++, n’avaient absolument rien de rationnel ! Alors d’aucuns me diront que
C++ est très adapté au monde du jeu-vidéo, mais on n’était pas là pour faire du jeu triple A, merde !
On était là pour produire quelque chose (du moins, c’est ce qu’on aurait voulu).

Et entre temps je me suis rappelé d’un framework qui m’avait toujours intimidé
à mes débuts, qui me rappelait des discussions techniques poussées (qui étaient
sans doute au final un amas de grosse branlette intellectuelle, aussi intéressantes
et poussées fussent-elles). Je veux évidemment parler du framework Boost.

Qt, SFML, Boost. Le plan à trois s’annonçait excitant. Mais quand je me regarde
en arrière, je vois ça :

![Boost](/assets/2020-22-02-dummy/boost.jpg)

(Première fois que je fais mes propres memes dans un billet, au passage)

J’ai donc découvert boost, notamment la bibliothèque "asio" pour gérer les
communications asynchrones, et franchement c’étais super plaisant à utiliser.
Mais aujourd’hui j’ai toujours pas compris si mon serveur était capable de
passer à l’échelle (et encore, c’était pas le moment de se soucier de ça) et
en plus j’ai rien produit de concret (bon, le serveur tournait, mais on pouvait
juste se déplacer et parler).

J’aurais pu mettre Habbo Hotel à genoux, mais c’était pas vraiment le but,
m’voyez.

Donc, je disais, j’étais parti dans cet ordre-là au fur et à mesure du développement :

- Éditeur de cartes ;
- Serveur de mise à jour de contenu ;
- Launcher ;
- Serveur maître (qui accepte les connexions utilisateur depuis le launcher) ;
- Site web (pour créer les comptes) ;
- Serveur de jeu (qui simule les cartes et le jeu) ;
- Client.

Alors que j’aurais dû commencer **dès le début par le client**.

Comment je m’en suis rendu compte ? Simplement en déboguant de client.
**Car mon client était super casse-couilles à déboguer** puisqu’il fallait
faire tourner le serveur de jeu à côté pour le faire marcher.

J’ai donc découplé la logique du jeu de la logique serveur du jeu, et j’ai
abouti à un client qui n’avait pas besoin d’un serveur réseau pour fonctionner.

J’avais un client *standalone* donc, qui aurait très bien pu faire l’affaire
pour un *ARPG* local. J’ai donc tiré deux leçons de mes conneries :

- J’ai mis la charrue avant les bœufs ;
- J’aurais pu commencer avec un client non connecté au réseau, pour commencer.

Sachant que ça m’a pris une journée entière pour découpler tout ça. C’était
certes une partie de plaisir car je faisais ça sur mon temps libre, mais avec
le recul, si je dois bosser sur un jeu que je dois sortir pour hier et qui
doit se vendre… C’est signe de mauvais augure.

On va conclure avec la quatrième erreur que je ne suis pas le seul à faire et
que je n’aurais pas dû faire de par mon expérience – et ce projet m’en a
définitivement convaincu.

## 4ème erreur : réinventer la roue carrée

*Don’t reinvent the fucking wheel!*, disaient-ils. Et ils ont raison. Seulement
voilà : les motivations de base, c’était progresser en Qt et en C++. On avait
besoin de coder, Grindewald et moi. Et on se voyait mal reprendre le code
source de [https://www.mapeditor.org/](https://www.mapeditor.org/) pour
plusieurs raisons injustifiées.

D’abord, on ne voulait pas perdre le temps de s’approprier le projet. Déjà
parce qu’on voulait faire du C++ en s’amusant, ensuite parce qu’on allait vite
nous démotiver à tripoter ce projet (alors qu’avec le recul ça aurait pu être
intéressant) mais aussi parce qu’il allait sans doute évoluer de son côté et
que je me voyais mal intégrer les fonctionnalités *upstream* avec les miennes…
Bref, je voyais déjà le casse-tête et je me suis dit que repartir d’une
feuille blanche était plus simple.

Au final on a réinventé un éditeur qui fonctionne pas mal… Mais on a perdu
du temps, quoi, merde. C’étais fun dans la réalisation, mais c’était une perte
de temps si l’objectif était de sortir quelque chose.

C’est pour cela que je conseillerais à tout débutant de savoir quels sont les
*objectifs* véritables : vous voulez sortir quelque chose ? réutilisez au
maximum. Vous voulez juste apprendre ? Pas de problème mais n’espérez rien
publier (à moins d’être un sacré psychopathe).

J’ai déjà entendu plus d’une fois cet argument fallacieux qu’il fallait
réinventer la roue carrée si on avait besoin d’une roue carré (par un ancien
collègue « expert » qui avait plus de 10 ans d’expérience dans la même boîte du
haut de sa petite tour d’ivoire, à qui des publications comme
[celle-ci](https://www.freecodecamp.org/news/we-fired-our-top-talent-best-decision-we-ever-made-4c0a99728fde/)
rendrait bien mal à l’aise).

Oui, mais non. Dans ce cas, on reprend la roue et on lui met des bords.
Autrement dit, on prend un projet existant, et on l’adapte. Sur le coup c’est
parfois difficile et sans doute traumatisant pour l’ego de se dire qu’on n’est
pas l’auteur original de son produit, mais un programmeur, c’est fainéant et
ça devrait le rester.

Si [Zeste de Savoir](https://www.zestedesavoir.com) n’avait pas forké
progdupeu.pl, est-ce qu’il en serait là aujourd’hui ? On avait failli partir
sur J2EE à l’époque. Vous vous rendez compte ?

Je peux dire avec toute l’humilité du monde que :

- j’étais con (d’avoir voulu réinventer la roue) ;
- j’étais plus inexpérimenté qu’aujourd’hui (cet échec m’aura donné une bonne leçon).

Et encore aujourd’hui j’ai parfois espoir de me dire qu’il faut (ré)inventer
des roues là où les trucs qui existent déjà ne roulent pas. Mon ego me perdra…

## Tant d’erreurs, mais tant d’expérience !

On aura passé presque 2 ans à bosser sur Dummy. On avait même trouvé une acolyte
pour bosser sur la partie *lore* du jeu, car c’est moi-même un aspect des MMOPRG
qui m’intéresse, à titre purement personnel. J’avais envie d’y passer du temps
dessus, de commencer à nourir mon bébé.

Au final, c’est un avortement duquel j’en ressors incroyablement grandi. Il y
a eu près de 20 000 lignes de code pondues, j’étais sur le point d’intégrer
un gameplay basique et foireux, j’aurais peut-être pu publier quelque chose
aussi bancal fût-ce, mais la vie en a voulu autrement.

Résultat des courses, j’aime toujours autant le C++ et serai ravi de continuer
à le pratiquer, surtout avec [des gens passionnants comme Lynix](https://sirlynixvanfrietjes.be/)
et si je dois refaire un jeu, c’est certainement en revoyant mes ambitions à
la baisse.

D’ailleurs, si vous aimez le C++ et les jeu-vidéos, je vous recommande vraiment
d’aller voir ce que Lynix fait. Il a [une chaîne Twitch](https://www.twitch.tv/sirlynixvanfrietjes), 
[un serveur Discord](https://discord.gg/8HJ5cma), bref sa communauté est assez accessible
et son contenu est non seulement intéressant, mais débutant friendly.

## Remerciements

J’ai reçu beaucoup de soutiens pendant le développement de ce projet et il
faut rendre à César ce qui appartient à César. En ce sens je remercie
Grindewald pour avoir jeté la première pierre, Iluka pour avoir pris part au
projet sur le côté *lore* (dont le travail, j’en suis sûr, saura ête réutilisé
pour des projets ultérieurs), nohar pour ses critiques et encouragements,
Lynix pour les raisons suscitées, Mira pour l’aide communautaire qu’elle a
apportée aux débuts du projet, Ptiluky et Abydox pour avoir réussi à reprendre
l’éditeur (et qui, peut-être, arriveront à faire quelque chose de Dummy),
Retro pour avoir participé aux sessions de test (bon, il comprendra peut-être
pas, il est anglophone) ainsi qu’à tous ceux qui m’ont suivi de près ou de loin.

## Conclusion

Si je devais résumer les enseignements que j’ai tirés de cette expérience :

- **Essayez de faire même si vous ne savez pas faire.** (et ça, si vous suivez un gars comme Lynix, il vous le redira)
- **Si vous en faîtes un projet amateur, voyez vos objectifs à la baisse et réutilisez au possible.**
(sauf si, comme moi, vous voulez juste vous amuser avec un langage ou une bibliothèque et que son choix n’est pas rationnel)
- **Mettez-vous des deadlines**. C’est très important et ça a été d’autant plus difficile en ce qui me concerne au vu de mon perfectionnisme. Mais vous préférez quelque chose d’incomplet qui voit le jour ou quelque chose de trop complet qui ne verra certainement pas le jour ?
- **Gardez une taille d’équipe petite**. J’ai sans doute fait l’erreur d’avoir ouvert et proposé à d’autres développeurs de me seconder, même si je ne regrette en rien la venue de Ptiluky et Abydox sur le projet. Seulement, avec des opinions divergentes et une équipe trop grande, cela peut s’avérer difficile d’avancer, surtout au début lorsque des décisions doivent être prises. Avoir commencé avec Grindewald et Iluka m’a paru optimal et c’est deux personnes avec qui j’ai encore envie de travailler.
- **PRENEZ-Y DU PLAISIR !** Et ce surtout si c’est un projet amateur. On ne parle
pas d’un développeur de jeu-vidéo qui fait ça pour en vivre (même si les gens
du milieu sont des passionnés en général), mais bordel, la vie est courte,
éclatez-vous si vous décidez de faire des projets comme ça, que ça soit un pong
amateur à un bomberman en réseau. Sinon, je peux vous dire que vous allez vite
vous péter la gueule, et ça, je ne suis certainement pas le seul à le dire.