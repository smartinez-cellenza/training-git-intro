# Travailler avec les branches

## Overview

Dans ce lab, vous allez utiliser des branches et explorez les opérations de merge.

## Objectives

Après la complétion de ce lab, vous pourrez :

-   Créer des branches.
-   Les réintégrer en utilisant une opération de merge.
-   Faire un rebase.
-   Squasher en ensemble de commits.

## Instructions

### Avant de commencer

- Avoir dérouler le lab **Initialiser un Repository et faire un commit**.

### Exercice 1: Créer une branche et faire un merge fast foward

Dans le shell de votre choix, aller dans le dossier contenant votre repository git.

```shell
cd trainingrepo
```

Créez une nouvelle branche à partir de la branche *main*.

```shell
git checkout -b feature1
git status
```

> La command git status nous indique que nous sommes maintenant en train de travailler sur la branche *feature1*.

Dans le dossier *src*, ajouter un nouveau dossier *modules*, qui contient un fichier *main.tf*.

Lancez la commande git

```shell
git add .
git commit -m "new feature1"
git log
```

> Un nouveau commit a été fait sur la branche *feature1*

Le développement de la feature est terminée. Il faut maintenant la merger sur la branche *master*.

Lancez la commande git

```shell
git checkout master
git status
```

> La command git status nous indique que nous sommes maintenant en train de travailler sur la branche *master*.

Executez l'opération de merge

```shell
git merge feature1
```

> Dans l'ouput, on peut voir qu'une opération de merge fast foward a été réalisée. Cela est possible car la branche main n'a pas évolué entre le moment de la création de la branche de feature et l'opération de merge.

```shell
git log
```

> Les logs indiquent qu'un seul commit à été ajouté, celui provenant de la branche *feature1*.

La branche de feature étant mergée, elle peut être supprimée

```shell
git branch -d feature1
git branch
```

### Exercice 2: Créer une branche et faire un merge recursive

Créez une nouvelle branche à partir de la branche *main*.

```shell
git checkout -b feature2
git status
```

> La command git status nous indique que nous sommes maintenant en train de travailler sur la branche *feature2*.

Dans le dossier *src*, ajouter un nouveau dossier *betterModules*, qui contient un fichier *main.tf*.

Lancez la commande git

```shell
git add .
git commit -m "new feature2"
git log
```

> Un nouveau commit a été fait sur la branche *feature2*

Créez un nouveau commit sur la branche master

```shell
git checkout master
```

Modifier le contenu du fichier *readme.md*.

Créez un commit

```shell
git add .
git commit -m "update readme.md"
```

Executez l'opération de merge

```shell
git merge feature1
```

> Un message de commit est nécessaire. La raison est que git va devoir créer un commit supplémentaire pour l'opération de merge, la branche source ayant évoluée entre le moment de la création de la branche de feature et l'opération de merge.

```shell
git log
```

> Les logs indiquent 3 commits : celui de la branche *feature2*, celui de la branche *main* et un troisième pour l'opération de merge.


### Exercice 3: Créer une branche, faire un rebase et merger

Créez une nouvelle branche à partir de la branche *main*.

```shell
git checkout -b feature3
git status
```

> La command git status nous indique que nous sommes maintenant en train de travailler sur la branche *feature3*.

Dans le dossier *src*, ajouter un nouveau dossier *evenbetterModules*, qui contient un fichier *main.tf*.

Lancez la commande git

```shell
git add .
git commit -m "new feature3"
git log
```

> Un nouveau commit a été fait sur la branche *feature3*

Créez un nouveau commit sur la branche master

```shell
git checkout master
```

Modifier le contenu du fichier *readme.md*.

Créez un commit

```shell
git add .
git commit -m "update readme.md"
```

Effectuez un rebase sur la branche *feature3*

```shell
git checkout feature3
git rebase master
git log
```

> Le commit de la branch master à été ajouté à la branche *feature3*.

Executez l'opération de merge

```shell
git merge feature3
```

```shell
git log
```

> Les logs indiquent un seul nouveau commit, celui provenant de *feature3*.

