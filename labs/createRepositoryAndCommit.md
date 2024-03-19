# Initialiser un Repository et faire un commit

## Overview

Dans ce lab, vous allez initialiser un repository Git, et réaliser un commit.

## Objectives

Après la complétion de ce lab, vous pourrez :

-   Initialiser un repository localement.
-   Configurer le nom et l'email au niveau de git
-   Commiter une modification.
-   Utiliser la command git status pour afficher les informations sur l'état du repository.

## Instructions

### Avant de commencer

- Avoir installé git.
- Git est disponible dans le shell que vous utilisez.

### Exercice 1: Initialiser un repository Git

Dans le shell de votre choix, créez un nouveau dossier.

```shell
mkdir trainingrepo
cd trainingrepo
```

Ce dossier va devenir le repository git.

Lancez la commande git

```shell
git status
```

> Cette commande renvoie une erreur. Il s'agit du comportement attendu, notre dossier n'ayant pas encore été initialisé.

Lancez la commande git

```shell
git init
```

> Cette commande permet d'initialiser un nouveau repository git. Nous verrons plus tard qu'il est possible de récupérer localement un repository git existant en utilisant la command git clone.

> Le repository git est maintenant initialisé. Le dossier contient maintenant un dossier caché *.git*. Ce dossier est exploité par git pour le contrôle de version.

Lancez la commande git

```shell
git status
```

> Les informations sur le repository sont affichées, notament la branche en cours d'utilisation (main ou master).

> Les branches seront abordées plus tard lors de ce traingin.

### Exercice 2: Configuration de git

Vous allez configuer git afin de pouvoir créer un premier comit.

> Si vous avez déjà utilisé git, il est possible que cette configuration soit déjà faite de façon globale.

Executez les commandes suivantes, dans votre repository :

```shell
git config --local user.name "nom"
git config --local user.email "email"
```

> Ces informations sont nécessaire pour pouvoir réaliser un commit. Elles apparaitront dans l'historique de git.

### Exercice 3: Création d'un commit

Vous allez créer un nouveau fichier *readme.md* et réaliser un commit.

Ouvrir Visual Studio code en lancant la commande

```shell
code .
```

Ajouter un nouveau fichier readme.md, avec le contenu de votre choix.

Lancez la commande git

```shell
git status
```

> le fichier readme apparait maintenant dans les fichiers untracked de git. Il doit être ajouté pour le prochain commit. Cette logique de staging sera abordée plus tard dans ce training.

Lancez la commande git

```shell
git add readme.md
```

> Cette commande permet d'ajouter le fichier readme.md au prochain commit

Lancez la commande git

```shell
git status
```

> Le fichier readme.md sera ajouté lors du prochain commit

Lancez la commande git

```shell
git commit -m "first"
```

> Le commit est crée, incluant 1 fichier.

Lancez la commande git

```shell
git status
```

> Il n'y a plus de modification en cours dans le repository.