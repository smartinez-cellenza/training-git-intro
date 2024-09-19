# Travailler avec Gitlab

## Overview

Dans ce lab, vous allez utiliser Gitlab.

## Objectives

Après la complétion de ce lab, vous pourrez :

-   Pousser un repository existant vers Gitlab.
-   Cloner un repository depuis Gitlab.
-   Créer une Pull Request.
-   Consulter l'historique dans Gitlab.

## Instructions

### Avant de commencer

- Avoir dérouler le lab **Travailler avec les branches**.
- Avoir un compte Gitlab

### Exercice 1: Pousser un repository existant

Récuperez l'url de votre repository dans Gitlab

Dans le shell de votre choix, aller dans le dossier contenant votre repository git. (Code -> Clone -> Clone with https)

```shell
cd trainingrepo
```

Executer les commandes git

```shell
git remote add origin <l'url de votre projet git>
git push --set-upstream origin --all
```

> Le repository est maintenat poussé sur Gitlab

> L'ensemble des branches et de l'historique est disponible

### Exercice 2: Cloner un repository

Remontez d'un niveau dans l'arboresence par rapport à votre repository local.

```shell
cd ..
```

Lancer la commande

```shell
git clone <l'url de votre projet git>
cd <le nom de votre repository>
git status
```

> Le projet git est récupérer depuis Gitlab

### Exercice 3: Créer une branche dans Gitlab et la récupérer localement

Créez une nouvelle branche sur Gitlab (Code -> Branches -> New Branches ).

Cette branche est créée depuis *main* et s'appele *feature4*.

Lancer la commande suivante

```shell
git branch -a
```

> La branche feature4 n'apparait pas pour l'instant

Lancer les commandes suivante

```shell
git fetch
git branch -a
```

> La branche feature4 apparait maintenant


### Exercice 4: Modifier localement la branche et pousser vers Gitlab

Lancer les commandes suivante

```shell
git checkout --track origin/feature4
```

> Cette commande permet de créer la branche *feature4* , associé à la branche remote *feature4*.

Modifiez le fichier readme.md et créez un commit

```shell
git add .
git commit -m "update readme"
git status
```

> Le commande status nous indique que nous avons un commit local qui doit être poussé en remote

Lancez la commande git

```shell
git push
git status
```

> La branche local et la branche en remote sont à jour
