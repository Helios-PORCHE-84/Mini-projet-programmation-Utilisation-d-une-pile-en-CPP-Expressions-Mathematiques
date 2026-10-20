# Mini-projet programmation Utilisation d'une pile en C++ (Expressions Mathématiques).

# Contexte & Objectif : 

Projet individuel (L1, UE POO). Maîtrise de la structure de données "Pile" à travers trois applications mathématiques : l'évaluation, la conversion et la modélisation arborescente d'expressions. 


# Détails Techniques & Concepts Clés :

Notation Polonaise Inverse (Suffixée) : Évaluation d'expressions sans parenthèses.

Algorithme de Shunting Yard : Conversion d'expressions infixées (classiques) en suffixées en gérant les priorités des opérateurs et l'associativité.

Arbres Binaires : Construction d'un arbre d'expression et évaluation récursive. 


# Cheminement de réalisation (Synopsis) :

Implémentation de la Pile : Création d'une classe Pile générique (via liste chaînée ou tableau) avec les méthodes empiler, depiler, sommetPile et vide.

Évaluateur Suffixé : Parcours de la chaîne de caractères. Si opérande →empiler. Si opérateur →dépiler deux valeurs, calculer, et empiler le résultat.

Convertisseur Infixé →Suffixé : Utilisation d'une pile pour les opérateurs (en respectant les priorités *, / > +, - et les parenthèses) et d'une file pour la sortie finale.

Arbre d'Expression : Création des classes Noeud (type, valeur, fils gauche, fils droit) et Arbre. Construction de l'arbre via une pile, puis implémentation de méthodes récursives pour l'évaluation et l'affichage infixe (avec ajout dynamique des parenthèses).




Une expression suffixée abc+∗ est très facile à évaluer pour un programme informatique. On utilise pour cela une pile contenant les opérandes. L'expression est parcourue de la gauche vers la droite. Lorsqu'un opérande est rencontré, elle est placée au sommet de la pile. Lorsqu'un opérateur est rencontré, les deux derniers opérandes sont enlevés de la pile, l'opération leur est appliquée, et le résultat est placé au sommet de la pile. Lorsqu'une fonction est rencontrée, le dernier opérande est retiré de la pile, la fonction lui est appliquée, et le résultat est placé au sommet de la pile.


# Question 1: Montrer comment, d’après le paragraphe précédent, on évalue grâce à une pile l’expression abc+*.

•Écrire la classe pile avec les fonctions empiler/dépiler/vide, cette classe doit être implémentée avec une liste chaînée.
•Écrire la fonction évaluer qui prend un argument de type string correspondant à une expression suffixée et qui retourne le résultat de l’évaluation de celle-ci avec cette méthode : on utilise pour cela une pile ; l’expression est parcourue de la gauche vers la droite.
•Lorsqu’un opérande est rencontré, il est placé au sommet de la pile.
•Lorsqu'un opérateur est rencontré, les deux derniers opérandes sont enlevés de la pile, l'opération leur est appliquée, et le résultat est placé au sommet de la pile.
•N'oubliez pas de bien tester la fonction


# Question 2: Transformer une expression infixée en une expression suffixée.

Pour évaluer une expression infixée, une méthode consiste à la convertir tout d'abord en expression suffixée. L'algorithme de la gare de triage (shunting yard) permet de faire cette conversion. Les éléments de l'expression infixée (l'entrée) sont traités de la gauche vers la droite. Les opérandes sont ajoutés à une liste de sortie. Les opérateurs sont ajoutés dans une pile d'attente. Lorsqu'un opérateur de priorité inférieure à celui du sommet de la pile est traité, celui-ci est enlevé de la pile et placé dans la liste de sortie. Lorsque tous les lexèmes sont traités, la pile est vidée dans la liste de sortie. Voici l’algorithme complet:
- Si l'élément est un opérande, l'ajouter à la liste de sortie.
- Si l'élément est un opérateur, vider la pile vers la sortie tant que la priorité de l'opérateur est inférieure ou égale à celle de l'élément du haut de la pile. Si l'associativité de l'opérateur est à droite, la condition inférieure strictement doit être utilisée.
- Si l'élément est (, le placer dans la pile.
- Si l'élément est ), vider la pile vers la sortie jusqu'à rencontrer ). Enlever ) de la pile.
- Lorsque l'entrée est vide, vider la pile dans la sortie.


# Question 3: Construire un arbre binaire contenant une expression. 

Pour distinguer les noeuds contenant un opérateur des noeuds contenant une valeur utilisez la classe noeud suivante : class noeud { char type ; //‘o’ pour opérateur et ‘f’ pour valeur. char ope ; float val ; noeud * fg, * fd ; } ; 
Voici un exemple : Cet arbre représente l’expression a+((b*4)/3). On commence par transformer l’expression infixe en une représentation suffixe, en utilisant la méthode décrite précédemment mais en utilisant une pile d’adresses de Noeuds. 
Nous allons procéder de la même manière que lors de l’évaluation, mais au lieu de mettre dans la pile les opérandes eux-mêmes, on mettra des pointeurs sur des Noeuds contenant les opérandes. 
L’expression suffixée est lue de gauche à droite, si l’élément lu n’est pas une opération, alors on le met dans un Noeud (alloué dynamiquement) dont on empile l’adresse. Lorsqu’on rencontre une opération, on crée un noeud N représentant cette opération puis on dépile un élément qui constituera le fils gauche de N et un autre élément qui sera le fils droit de N. L’adresse de N est ensuite empilée. Le processus s’arrête lorsqu’on traite tous les éléments de l’expression. La pile contiendra à ce moment-là l’adresse de la racine de l’arbre. 
Écrire les classes noeud et arbre avec entre autres les différents éléments :
 -Constructeur sans argument 
-Constructeur (de Arbre) avec une expression arithmétique normale (infixe) -Destructeur
-Une fonction évaluation qui évalue un arbre 
-Écrire une fonction qui affiche une expression contenue dans un arbre de manière infixe avec les parenthèses nécessaires.


# Question 4 On va maintenant considérer des expressions arithmétiques construites à partir de nombres, variables et opérateurs. 

Plus précisément, les expressions étudiées pourront être :
- un nombre flottant r. Dans ce cas, l’expression sera représentée par un arbre réduit à un seul nœud contenant r.
- l’une des variables X, Y ou Z. Dans ce cas, l’expression sera représentée par un arbre réduit à un seul nœud contenant cette variable.
Ou bien, si u et v sont des expressions représentées par les arbres A et B, et si n est un nombre entier :
- la somme, la différence, le produit ou le rapport de u et v. Dans ces cas, les expressions obtenues seront respectivement représentées par les arbres.
- la mise à la puissance n, avec n entier, de u. Pour éviter toute ambiguïté, le moins unaire de l’opposé sera noté par le caractère « souligné » (‘_’). Dans ces cas, les expressions obtenues seront respectivement représentées par les arbres.
Adapter les classes arbre et noeuds précédentes pour créer ces arbres. Écrire les fonctions membres permettant de fabriquer l’arbre codant la dérivée d’une expression par rapport à une variable prise en paramètre. 


Si l’on note e’ la dérivée en X de l’expression e,
r’ = 0, si r est un nombre,
X’ = 1,
Y’ = Z’ = 0,
(u + v)’ = u’ + v’,
(u – v)’ = u’ – v’,
(u.v)’ = u’.v + u.v’,
(u/v)’ = (u’.v – u.v’) / v2,
(un)’ = n.u’.un-1


// X + 3
arbre A1(new Noeud('+',
new Noeud('X'),
new Noeud(3))) ;


// 4 * X ^2 - 2 * y + (-Z)
arbre A2(new Noeud('-',
new Noeud('*',
new Noeud(4),
new Noeud('^',
new Noeud('X'),
new Noeud(2))),
new Noeud('+',
new Noeud('*',
new Noeud(2),
new Noeud(Y)),
 new Noeud('_',
new Noeud('Z')))));
