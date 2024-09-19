# Staging, gitgnore et historique

## Overview

Dans ce lab, vous allez utiliser la zone de staging, le fichier .gitgnore et consulter l'historique.

## Objectives

Après la complétion de ce lab, vous pourrez :

-   Créer des commits incluant plusieurs fichiers / dossiers.
-   Consulter et modifier le contenu d'un commit
-   Exclure certains dossiers / fichiers en utilisant un fichier .gitignore.
-   Consulter l'historique des modifications.

## Instructions

### Avant de commencer

- Avoir dérouler le lab **Initialiser un Repository et faire un commit**.

### Exercice 1: Créer un commit sur dossier

Dans le shell de votre choix, aller dans le dossier contenant votre repository git.

```shell
cd trainingrepo
```

Ouvrir Visual Studio code en lancant la commande

```shell
code .
```

Ajouter un nouveau fichier dossier *src* à la racine.

Ajouter 2 nouveau fichiers *main.tf* et *provider.tf*

Lancez la commande git

```shell
git status -u
```

> les 2 nouveaux fichiers apparaissent.

Lancez la commande git

```shell
git add src/
```

> Cette commande permet d'ajouter l'ensemble du dossier src dans la zone de staging

Lancez la commande git

```shell
git status
```

> Les 2 fichiers feront parti du prochaine commit

Lancez la commande git

```shell
git commit -m "hello terraform"
```

> Le commit est crée, incluant les 2 fichiers.

### Exercice 2: Retirer un fichier de la zone de staging

Ajouter 2 nouveau fichiers *version.tf* et *variables.tf*

Lancez la commande git

```shell
git add .
```

> Cette commande permet d'ajouter l'ensemble des modifications dans la zone de staging

Lancez la commande git

```shell
git status
```

> Les 2 fichiers feront parti du prochaine commit

Pour retirer le fichier *variables.tf* de la zone de staging, exécutez la commande

```shell
git reset src/variables.tf
```

Lancez la commande git

```shell
git status
```

> Le fichier *variables.tf* ne fait plus partie de la zone de staging. Le prochaine commit ne comprendra que le fichier *version.tf*.

Lancez la commande git

```shell
git commit -m "add version.tf"
git status
```

> le fichier *variables.tf* est toujours dans la zone de staging.

Lancez la commande git

```shell
git add .
git commit -m "add variables.tf"
```

### Exercice 3: Consulter l'historique

Lancez la commande git

```shell
git log
```

> Les différents commit du repository sont affichés, avec la date, l'auteur et le message de commit

Lancez la commande git

```shell
git log --patch
```

> Il est possible d'obtenir plus d'information en jouant sur les parametres de git log

> Dans VsCode, allez dans l'onglet Source Control pour consulter l'historique

### Exercice 4: Supprimer un fichier

Supprimez le fichier *version.tf* dans le dossier *src*

Lancez la commande git

```shell
git status
```

> Le fichier *version.tf* apparait comme supprimé. Cette modification doit être ajouté à la zone de staging afin de faire parti du prochain commit.

Pour restaurer le fichier, lancez la command git

```shell
git checkout src/version.tf
git status
```

> Le fichier *version.tf* a été restauré, en utilisant le repository git local.

Supprimez de nouveau le fichier *version.tf* dans le dossier *src*

Lancez la commande git

```shell
git add .
git commit -m "remove version.tf"
git log
```

> Le dernier commit dans les logs indique la supprésion du fichier *version.tf*.

### Exercice 4: Utilisation du gitignore

Créez à la racine du dossier un fichier *.gitignore* avec le contenu suivant

```
cestamoi/
```

Créez un dossier *cestamoi*, contenant un fichier *amoi.txt*.

Lancez la commande git

```shell
git status
```

> Le fichier .gitgnore peut être mis en zone de staging. Le dossier *cestamoi* n'apparait pas, étant exclu via la configuration du .gitignore.

Lancez la commande git

```shell
git add .
git commit -m "add gitignore"
```
