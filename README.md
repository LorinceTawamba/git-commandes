# GIT - COMMANDES

Les commandes git principales pour mieux travailler. 

# Git config  

## Rappel

**Ne pas oublier : l'aide en ligne de commande.**

```shell
git help config
git help push
git help pull
git help branch
```  
## Configuration

```shell
# Identity Name
git config --global user.name "lorince"

# Identity Email
git config --global user.email "lorince@entreprise.com"

# Editor Tool
git config --global core.editor subl

# Diff Tool
git config --global merge.tool filemerge
```
## Liste des globals

```shell
git config --list
```

# Installation projet

## Initialiser un projet

```shell
cd chemin/vers/mon_dossier
echo "# MON_PROJET" >> README.md
git init
git add README.md
git commit -m "Initial commit"
git remote add origin ....git
git push -u origin master
```

## Récuperer le repo sur Github

```shell
git clone ....git chemin/vers/mon_dossier
```

Mon repo est composé d'au moins deux branch.

develop : dédié au développement et résolution de bug.
master : reflète le code en production. Personne ne doit travailler directement sur cette branch.

Pour récupérer votre branch develop

```shell
git branch -a
git checkout origin/develop
git checkout -b develop origin/develop
git branch
```

## Developpement : Branch develop

## Prod : Branch Master

```shell
# On se met sur la branche master
git checkout master
# On merge la branche develop
git merge develop
# Pour pousser les changements
git push origin master
# Penser à revenir sur develop
git checkout develop
```

# Principales commandes

## Status des fichiers

```shell
git status
```

## Lister les branchs

```shell
git branch -a
```

`*`sur la branche courante.

## Créer une branch

```shell
# Deux lignes: créer et basculer sur la nouvelle branch
git branch nom_de_ma_branch_nouvelle
git checkout nom_de_ma_branch_nouvelle

# Une seule ligne: créer et basculer
git checkout -b nom_de_ma_branch_nouvelle
```

## Supprimer une branch

```shell
# Si la branch est local et n'est pas créée sur le repo distant
git branch -d nom_de_ma_branch_local

# Si la branch est présente sur le repo distant
git push origin --delete nom_de_ma_branch_distante
```

## Changer de branch

```shell
git checkout nom_de_ma_branch

# GIT --version 2.23
git switch nom_de_ma_branch
```

## Premier commit

```shell
git add .
git commit -m "initial commit"
```

## Commit suivant

```shell
git add chemin_vers_mon_fichier
git commit -m "message du commit"
```

## Annuler le dernier commit et modifs

```shell
git reset --hard md5_commit
git push --force
```

## Antidaté un commit.

```shell
git add .
GIT_AUTHOR_DATE="2015-12-12 08:32 +100" git commit -m "Commit antidaté"
```

## Mettre à jour le dépôt local

```shell
git pull
```

## Mettre à jour le dépôt local d'une branch spécifique

```shell
git pull origin MA_BRANCH
```

## Envoyer ses commits vers le dépôt distant

```shell
git push
```

## Envoyer ses commits vers le dépôt distant sur une branch spécifique

```shell
git push origin MA_BRANCH
```

## Supprimer un fichier du répertoire de travail et de l'index

```shell
git rm nom_du_fichier
```

## Supprimer un fichier de l'index

```shell
git rmg --cached nom_du_fichier
```

# Créer une release

Créer une nouvelle branche `release/aaaammyy_xx`

```bash
$ git checkout -b release/20140707_01 dev
```

Modifier le numéro de version dans le fichier racine READ.md.

```bash
$ git commit -a -m "Bumped version 20140707_01"
```

Se mettre sur la branche `dev` et :

```bash
$ git merge release/20140707_01
```

Pour finaliser la release, merger les corrections éventuelles sur la `master` et la `dev`

```bash
$ git checkout master && git merge --no-ff release/20140707_01 && git push origin master
$ git checkout dev && git merge --no-ff release/20140707_01 && git branch -d release/20140707_01 && git push origin dev
```

Marquage de la version sur la branch master

```bash
$ git tag -a 20140707_01 -m "New prod 20140707_01" master && git push origin master --tags
```

# Annuler commit

## Annuler commits (soft)

Seul le commit est retiré de Git ; vos fichiers, eux, restent modifiés. Vous pouvez alors à nouveau changer vos fichiers si besoin est et refaire un commit.

### Annuler le dernier commit

```shell
git reset HEAD^
```

Pour indiquer à quel commit on souhaite revenir, il existe plusieurs notations :

* HEAD : dernier commit ;
* HEAD^ : avant-dernier commit ;
* HEAD^^ : avant-avant-dernier commit ;
* HEAD~2 : avant-avant-dernier commit (notation équivalente) ;
* d6d98923868578a7f38dea79833b56d0326fcba1 : indique un numéro de commit ;
* d6d9892 : indique un numéro de commit version courte.

## Annuler commits (hard)

Si vous voulez annuler votre dernier commit et les changements effectués dans les fichiers, il faut faire un reset hard. *Cela annulera sans confirmation tout votre travail !*

### Annuler les commits et perdre tous les changements

```shell
git reset --hard HEAD^
```

### Annuler les modifications d’un fichier avant un commit

Si vous avez modifié plusieurs fichiers mais que vous n’avez pas encore envoyé le commit et que vous voulez restaurer un fichier tel qu’il était au dernier commit :

```shell
git checkout nom_du_fichier

# GIT --version 2.23
git restore nom_de_ma_branch
```

### Annuler/Supprimer un fichier avant un commit

Supposer que vous venez d’ajouter un fichier à Git avec `git add` et que vous vous apprêtez à le « commiter ». Cependant, vous vous rendez compte que ce fichier est une mauvaise idée et vous voulez annuler votre `git add`.

Il est possible de retirer un fichier qui avait été ajouté pour être « commité » en procédant comme suit :

```shell
git reset HEAD -- nom_du_fichier_a_supprimer
```


# Authors

* **Lorince TAWAMBA** _alias_ [@LorinceTawamba](https://github.com/LorinceTawamba)

Read the list of [contributors](https://github.com/lorince-tawamba/gescom/contributors) to see who helped with the project ! 

# License

Ce document est placé sous licence CC BY-NC-SA :  [Creative Commons
Attribution - Pas d'Utilisation Commerciale - Partage dans les Mêmes Conditions](https://creativecommons.org/licenses/by-nc-sa/4.0/)

![Logo](https://licensebuttons.net/l/by-nc-sa/3.0/88x31.png)

En savoir plus sur [les licences Creative Commons](https://creativecommons.org/licenses/?lang=fr-FR)...
