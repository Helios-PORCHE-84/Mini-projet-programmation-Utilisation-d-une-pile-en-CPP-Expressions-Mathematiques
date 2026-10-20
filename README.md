# Mini-projet programmation Utilisation d'une pile en C++ (Expressions Mathématiques)

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
