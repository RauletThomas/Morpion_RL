# Morpion_RL
## À propos
L'objectif de ce projet est d'implémenter différent algorithme de reinforcement learning sur le jeu du morpion 

## Table des matières 

- [Introduction](#introduction)
- [Définition des états](#Définition)

## Introduction 
Ce projet est à pour but de manipuler des algorithme de RL sans librairie particulière, exepté python.
Il se compose d'une première partie de code qui définit l'ensemble des états possible, puis l'implémentation de différent algorithme, Monte-Carlo et Sarsa pour le moment, et enfin d'une partie pour créer des modèle en variant les hyperparametre et tester contre nous le niveau atteint pour jouer au morpion 

## Définition des états 
Un état est représenter par une liste python de longeur 9, représentant les 9 cases du plateau, de haut en bas et de gauche à droite. \\
<img width="185" alt="image" src="https://github.com/user-attachments/assets/6aef8358-fbe7-402e-8f9b-b08f049c27b4" />

0 représente une case vide, 1 une croix et -1 un rond.
#### Exemple :
`E = [1,1,0
,0,1,0,
1,0,0]` donne 
<img width="165" alt="image" src="https://github.com/user-attachments/assets/7e32607a-8e1d-4361-879c-4935bb29bc06" />

