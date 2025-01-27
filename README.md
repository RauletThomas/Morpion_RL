# Morpion_RL
## À propos
L'objectif de ce projet est d'implémenter différent algorithme de reinforcement learning sur le jeu du morpion 

## Table des matières 

- [Introduction](#introduction)
- [Définition des états](#Définition-des-états)
- [Définition des actions et des récompense](#Défnition-des-actions-et-des-récompenses)
- [Comment utiliser les algorithmes](#Comment-utiliser-les-algorithmes)

## Introduction 
Ce projet est à pour but de manipuler des algorithme de RL sans librairie particulière, exepté numpy.
Il se compose d'une première partie de code qui définit l'ensemble des états possible, puis l'implémentation de différent algorithme, Monte-Carlo et Sarsa pour le moment, et enfin d'une partie pour créer des modèle en variant les hyperparametre et tester contre nous le niveau atteint pour jouer au morpion 

## Définition des états 
Un état est représenter par une liste python de longeur 9, représentant les 9 cases du plateau, de haut en bas et de gauche à droite. 

<img width="185" alt="image" src="https://github.com/user-attachments/assets/6aef8358-fbe7-402e-8f9b-b08f049c27b4" />

0 représente une case vide, 1 une croix et -1 un rond.
#### Exemple :
`E = [1,1,0,0,1,0,1,0,0]` donne 

<img width="165" alt="image" src="https://github.com/user-attachments/assets/7e32607a-8e1d-4361-879c-4935bb29bc06" />

### Définition de l'ensemble S
Tout les états du plateau de morpion ne nous intéresse pas, uniquement ceux jouable pour le joueur 1.
Un état suivit d'une action nous emmène donc directement dans un nouvel état jouable pour le joueur 1, en ayant choisi au hasard parmis les actions que le deuxiemme joueur pouvait choisire 

#### Exemple:

Nous nous situons dans l'état ci dessous, $S_1$

<img width="84" alt="image" src="https://github.com/user-attachments/assets/c2e08613-7983-444f-b814-9a3699cbf3b4" />

C'est au tour du joueur 1 de joueur , il joue dans la case 8 (très mauvais coup)

<img width="88" alt="image" src="https://github.com/user-attachments/assets/c6fc7531-3744-4b99-905f-04b3af8fb492" />

Le joueur 2 à donc 4 coup possible pour jouer , il choisit de jouer dans la case 5

<img width="88" alt="image" src="https://github.com/user-attachments/assets/61e27206-b2f0-4e26-bfa9-350c3ae2519a" />

Ce dernier état représente effectivement l'état $S_2$, celui qui suit $S_1$. Le choix pour le joueur 2 de prendre la case 5 est alétoire, suivant une loi uniforme sur l'ensemble des coups possible.

La probabilité de se retrouver dans un état $S_{n+1}$ sachant $S_n$ est $\frac{1}{\text{nombre de coup possible}}$

## Défnition des actions et des récompenses 

L'ensemble des actions est définit par $A =${ $0,1,2,3,4,5,6,7,8$ }

Une action est donc simplement un chiffre, représentant la case du plateau.

Attention : la liste des actions pour un état donné est un sous ensemble de A qui doit être calculé pour chaque état 

<img width="84" alt="image" src="https://github.com/user-attachments/assets/c2e08613-7983-444f-b814-9a3699cbf3b4" />

L'ensemble des actions est { $2,3,5,7,8$ }

On sait maintenant à partir d'un couple $(S_n,a_n)$ obtenir l'état $S_{n+1}$
La récompense $R_{n+1}$ ne dépend que de $S_{n+1}$ selon si il est terminal ou non 

$S_n$ est gagant pour le joueur 1 $\Rightarrow R_n = 10$

$S_n$ est gagant pour le joueur 2 $\Rightarrow R_n = -10$

$S_n$ est un match nul ou si le jeu n'est pas fini $\Rightarrow R_n = 0$

## Comment utiliser les algorithmes

Pour entrainer un modèle sur l'un des algorithme, il faut copier la tableau `Pi` et `Q` et appeller la fonction associé en donnant les hyperparamètre :
```
pi_MC = pi.copy()
Q_MC = Q.copy()
pi_MC , Q_MC = Monte_Carlo(pi_MC,Q_MC,k = 15000,n=4000)
```

Les hyperparamètre sont spécifier dans le code 

### Jouer avec notre agent 

Il possible de jouer contre un agent, avec la fonction match : `match(pi_MC)`



