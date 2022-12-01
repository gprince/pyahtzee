# pyahtzee
Kata sur les base du jeu Yahtzee en python

## Le Yahtzee en quelques mots

Le Yahtzee est un simple jeu de dés se déroulant en plusieurs rounds. Il se joue à l’aide de 5 dès comme suit :

A chaque round, chaque joueur lance les dés à leur tour. Le but est de réaliser une figure (5 dés identiques, une paire, un brelan, Yahtzee, ...). Pour réaliser cette figure, il a le droit à trois jets de dés par tour et il est, à chaque jet, libre de les relancer tous ou juste ceux de son choix. Chaque figure réalisée lui rapporte alors des points suivant les règles établies. Il ne peut cependant pas réaliser deux fois la même figure. A la fin de la partie, le gagnant est celui qui totalisée le plus de points.

## Description du problème

Le kata consiste, dans un premier temps,  à créer l’ensemble des règles de calcul qui, pour un joueur donné et à partir d’une combinaison de dés et d’une figure, restituera le score associé.

Dans un second temps, on pourra aller plus loin en relisant le jeu complet :

Au début de la partie, le programme demandera le nombre de joueur.

A chaque tour, il demandera, joueur par joueur, la combinaison de dés. En fonction de celle-ci et des combinaisons déjà associées à un score, il proposera un ensemble de figures possibles et demandera au joueur d’en sélectionner une.

A la fin de la partie il donnera un classement de chaque joueur avec le score et désignera le vainqueur.

## Règles du jeu :

La feuille de score est divisée en deux parties : partie mineure et partie majeure.

_La partie mineure regroupe les figures suivantes_ :

- **Maximum de 1** : les joueurs doivent obtenir le plus grand nombre de dés avec la face 1. Ils marquent 1 fois le nombre de dés de valeur 1 ;
- **Maximum de 2** : les joueurs doivent obtenir le plus grand nombre de dés avec la face 2. Ils marquent 2 fois le nombre de dés de valeur 2 ;
- **Maximum de 3** : les joueurs doivent obtenir le plus grand nombre de dés avec la face 3. Ils marquent 3 fois le nombre de dés de valeur 3 ;
- **Maximum de 4** : les joueurs doivent obtenir le plus grand nombre de dés avec la face 4. Ils marquent 4 fois le nombre de dés de valeur 4 ;
- **Maximum de 5** : les joueurs doivent obtenir le plus grand nombre de dés avec la face 5. Ils marquent 5 fois le nombre de dés de valeur 5 ;
- **Maximum de 6** : les joueurs doivent obtenir le plus grand nombre de dés avec la face 6. Ils marquent 6 fois le nombre de dés de valeur 6 ;

Quand les figures de la partie mineure sont entièrement réalisées, le joueur obtient un bonus de 35 points si le total des points de celles-ci est supérieur à 63 points.

_La partie majeure regroupe les figures suivantes_ :

- **Brelan** : les joueurs doivent obtenir 3 dés de même valeur. Ils marquent 3 fois la valeur des dés identiques ;
- **Carré** : les joueurs doivent obtenir 4 dés de même valeur. Ils marquent 4 fois la valeur des dés identiques ;
- **Full** : les joueurs doivent obtenir 3 dés de même valeur et 2 dés d’une autre valeur - (brelan + paire). Ils marquent 25 points ;
- **Petite Suite** : les joueurs doivent obtenir 4 dés qui se suivent (1-2-3-4, 2-3-4-5, 3-4-5-6). Ils marquent 30 points ;
- **Grande Suite** : les joueurs doivent obtenir 5 dés qui se suivent (1-2-3-4-5 / 2-3-4-5-6). Ils marquent 40 points ;
- **Yahtzee** : les joueurs doivent obtenir 5 dés de même valeur. Ils marquent 50 points. 2 Yahtzee sont autorisés au cours d’une partie ;
- **Prime Yahtzee** : Les joueurs peuvent obtenir 2 Yahtzee au cours d’une partie à condition d’avoir déjà obtenu un premier Yahtzee. Ils marquent 50 points supplémentaires ;
- **Chance** : les joueurs doivent obtenir le plus grand nombre de points. Ils marquent la somme de la valeur des dés ;

A la fin de la partie, ont totalise les points de la partie mineure, du bonus associé et de la partie majeure.

Mis à part pour le Yahtzee / Prime Yahtzee, chaque figure ne peut être obtenue qu’une seule fois de sorte qu’une partie comptabilise un total de 14 jets maximum par joueur. Le joueur est cependant libre de choisir la figure (sauf "Prime Yahtzee") qu’il désire associer à son jet tant qu’il respecte cette règle. Dans le cas où toutes les figures correspondant à une combinaison de dés ont déjà été choisies, le joueur marquera 0 dans la figure de son choix.

## Exemple pour une partie solo :

_Première combinaison (après trois lancés)_ :

            4, 4, 6, 5, 3.

A partir de cette combinaison, le joueur peut choisir de totaliser :

- 3 pour la figure mineure "Maximum de 3",
- 8 pour la figure mineure "Maximum de 4",
- 5 pour la figure mineure "Maximum de 5",
- 6 pour la figure mineure "Maximum de 6",
- 30 pour la figure majeure "Petite suite",
- 22 pour la figure majeure "Chance".

Il choisit "Petite suite" et totalise donc 30 pour cette figure.

_Deuxième combinaison_ :

            4, 3, 2, 4, 5

Les choix possibles sont :

- 2 pour la figure mineure "Maximum de 2",
- 3 pour la figure mineure "Maximum de 3",
- 8 pour la figure mineure "Maximum de 4",
- 5 pour la figure mineure "Maximum de 5",
- 18 pour la figure majeure "Chance".

Il choisit "Chance" et totalise donc 18 pour cette figure.

_Troisième combinaison_ :

            1, 5, 4, 5, 5

Les choix possibles sont :

- 1 pour la figure mineure "Maximum de 1",
- 4 pour la figure mineure "Maximum de 4",
- 15 pour la figure mineure "Maximum de 5",
- 15 pour la figure majeure "Brelan".

Il choisit "Maximum de 5" et totalise donc 15 pour cette figure.

_Quatrième combinaison_ :

            4, 4, 4, 2, 4

Les choix possibles sont :

- 2 pour la figure mineure "Maximum de 2",
- 16 pour la figure mineure "Maximum de 4",
- 12 pour la figure majeure "Brelan",
- 16 pour la figure majeure "Carré".

Il choisit "Carré " et totalise donc 16 pour cette figure.

La partie se déroule ainsi de suite jusqu’à obtenir la grille de score suivante :

- Maximum de 1: 3
- Maximum de 2: 8
- Maximum de 3: 6
- Maximum de 4: 12
- Maximum de 5: 15
- Maximum de 6: 18
- Prime partie mineure : 0 (total 62 < 63)
- Brelan: 9
- Carré: 16
- Full: 25
- Petite Suite: 30
- Grande Suite: 40
- Yahtzee: 0
- Prime Yahtzee: -
- Chance: 18

Score final : 200

Lors de cette partie, le joueur a décidé de marqué 0 dans Yahtzee, en fin de partie, car aucune autre combinaison n’était possible. Ne pouvant tenter d’obtenir un second Yahtzee, il n’aura, au final, lancé que 13 combinaisons au cours de cette partie.
