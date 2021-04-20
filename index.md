# Bienvenue sur le site web de Amaury Ajasse

## Présentation du projet

Ce projet a pour but d'évaluer mes compétences en Informatique Industrielle dans le cadre de l'UE Systèmes Embarqués suivi à l'ENS Paris-Saclay dans le MA EEA. Le but est d'utiliser un système d'exploitation temps réel (FreeRTOS) sur un microcontrôleur (STM32).

J'ai donc choisi de recréer un jeu très connu : le space invaders. A ce jeu, j'ai ausi décidé d'ajouter une musique afin d'utiliser la carte son du microcontrôleur STM32. L'utilisation de la carte son est la valeur ajoutée de mon projet et je vais entrer plus en détail dans son fonctionnement lors de ma présentation.

## Problématiques amenées par le projet

Ce projet venait avec une principale problématique de partage des tâches sur le microcontrôleur STM32. En effet, de nombreuses tâches avaient besoin d'utiliser l'écran et il a donc fallut répartir cette utilisation de l'écran à l'aide de Mutexes.
