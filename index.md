# Bienvenue sur le site web de Amaury Ajasse

## Présentation du projet

Ce projet a pour but d'évaluer mes compétences en Informatique Industrielle dans le cadre de l'UE Systèmes Embarqués suivi à l'ENS Paris-Saclay dans le MA EEA. Le but est d'utiliser un système d'exploitation temps réel (FreeRTOS) sur un microcontrôleur (STM32).

J'ai donc choisi de recréer un jeu très connu : le space invaders. A ce jeu, j'ai ausi décidé d'ajouter une musique afin d'utiliser la carte son du microcontrôleur STM32. L'utilisation de la carte son est la valeur ajoutée de mon projet et je vais entrer plus en détail dans son fonctionnement lors de ma présentation.

## Problématiques amenées par le projet

Ce projet venait avec une principale problématique de partage des tâches sur le microcontrôleur STM32. En effet, de nombreuses tâches avaient besoin d'utiliser l'écran et il a donc fallut répartir cette utilisation de l'écran à l'aide de Mutexes. C'est ce que l'on peut voir sur l'image suivante.

![image](https://user-images.githubusercontent.com/81380528/115381454-df369600-a1d3-11eb-9956-6448ba91b275.png)

La deuxième problématique a été de faire dialoguer les tâches entre elles en utilisant les *Queues* présente sur la carte STM32. On les utilise notamment pour que la position de l'homme soit connu par les tirs de l'homme mais aussi pour que la position des aliens soit connue des tirs aliens. Le but est que tous les tirs partent du même endroit que l'homme ou que les aliens. On peut voir l'utilisation des *Queues* dans l'image suivante :

![image](https://user-images.githubusercontent.com/81380528/115382067-89aeb900-a1d4-11eb-8816-1ae4010e6bca.png)

Cette ligne est utilisée pour envoyer les données d'une tâche vers une autre.

![image](https://user-images.githubusercontent.com/81380528/115382191-b367e000-a1d4-11eb-9aa1-abccc7fa280f.png)

Cette ligne est utilisée pour recevoir les données venant d'une autre tâche.

## Schéma des interactions entre les tâches

Voici le schéma d'interaction de mon space invaders, montrant comment les tâches dialoguent entre elles :

![image](https://user-images.githubusercontent.com/81380528/115384801-bca67c00-a1d7-11eb-98ff-5dfa75f37500.png)

On voit bien que toutes les tâches sont en interaction entre elles sauf la tâche qui joue la musique qui est indépendante.

## Conclusion technique

J'ai bien réussi à implémenter mes tâches d'homme et d'aliens ainsi que leurs tirs respectifs et j'ai également réussi à installer une communication entre les tâches. Cependant, je n'ai pas réussi à mettre ne place la musique à l'aide du DAC. En effet, je disposais bien des commandes d'initialisation du DAC et du port utiliser pour recevoir les informations mais je n'ai pas réussi à envoyer la musique au bon format sur le DAC pour que celle ci soit jouée. J'ai d'ailleurs créé une bibliothèque contenant la musique que je souhaitais jouer en convertissant la fréquence des notes en hexadécimal et en y mettant également une liste de la durée de chaque note.
