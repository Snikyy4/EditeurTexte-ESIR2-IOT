# Editeur de texte by Enzo Potin et Thibaud Lequertier

L'objectif de ce TP est de construire un mini-éditeur de texte offrant les concepts et les fonctions suivants :
- le texte est contenu dans un buffer (zone de travail),
- il existe une notion de sélection de texte, avec des commandes utilisateur permettant de
déplacer le début et la fin de la sélection,
- copie de la sélection dans le presse-papier,
- copie de la sélection dans le presse-papier puis effacement de la sélection,
- remplacement (« collage ») de la sélection par le contenu du presse-papier,
- l’interface homme-machine est d’un type quelconque (textuelle ou graphique).

## Version 1

Pour cette première version nous devons réaliser un éditeur de texte comprenant seulement les actions ci-dessus.

Ainsi, nous avons créé une classe Buffer qui va permettre de gérer la zone de texte de notre application. Dans cette dernière, nous y ajoutons toutes les fonctions nécessaires à l'édition de texte, cela implique une fonction copier ,coller ,couper ,selectionner ,effacer ,ecrire, décaler à gauche et enfin décaler à droite. 

De plus, nous avons créé une interface ICommande contenant une fonction d'execution qui va être implémentée par toutes les classes de commandes qui implémentent ICommande.

Concernant l'interface, nous avons la zone de texte, ainsi qu'une barre noire qui permet d'afficher les différents boutons tels que Copier, Couper, Coller, Selection et également le nombre de caractères du fichier. 

#### Selection

On peut donc sélectionner du texte en appuyant sur le bouton Selection, puis par la suite choisir sa zone de sélection grâce aux flêches (gauche et droite) du clavier. En effet, lorsque l'utilisateur clique sur la flèche de gauche, le curseur se décale à gauche, de même pour la flèche de droite. Le texte sélectionné est visible grâce à un surlignage bleu ciel par dessus le texte. (comme on a l'habitude de voir sur n'importe quel éditeur de texte).

#### Copie de la sélection

Une fois le texte sélectionné, si l'utilisateur appuie sur le bouton Copier, le contenu de la selection sera gardé en mémoire dans une chaîne de caractères correspondant au presse-papiers sans supprimer la sélection.

#### Coupe de la sélection

Une fois le texte sélectionné, si l'utilisateur appuie sur le bouton Couper, le contenu de la selection sera gardé en mémoire dans une chaîne de caractères correspondant au presse-papiers tout en supprimant la sélection.

#### Collage du presse-papiers

Après avoir copier ou couper, le presse-papiers aura pour valeur la sélection précédente. Ainsi, si l'utilisateur souhaite coller ce dernier au niveau de son curseur, il suffit d'appuyer sur le bouton Coller. Le collage se fait même si l'utilisateur est en train de sélectionner une zone de texte.

## Version 2

Dans cette nouvelle version, nous avons gardé toutes les fonctionnalités de la V1, cependant, on a ajouté les fonctionnalités suivantes : revenir en arrière si l'utilistauer souhaite annuler ce qu'il vient de faire ou alors retourner à l'étape d'après. 

Pour se faire, nous commençons par ajouter dans la classe Buffer, des attributs qui vont permettre de gérer les états du fichier, c'est-à-dire permettre de savoir ce que contenait le buffer à un index précis. De ce fait, lorsque l'utilisateur veut retourner en arrière, on lui renvoie le buffer à l'état d'avant (si cela est possible) et s'il souhaite avancer, on lui renvoie le buffer à l'état d'après (si cela est possible). Danss l'interface on y ajoute deux boutons faisant référence au retour en arrière et à l'avancée. Enfin, on ajoute les deux commandes Précédent et Suivant qui implémentent ICommand.
