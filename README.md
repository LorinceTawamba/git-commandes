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

# Authors

* **Lorince TAWAMBA** _alias_ [@LorinceTawamba](https://github.com/LorinceTawamba)

Read the list of [contributors](https://github.com/lorince-tawamba/gescom/contributors) to see who helped with the project ! 

# License

Ce document est placé sous licence CC BY-NC-SA :  [Creative Commons
Attribution - Pas d'Utilisation Commerciale - Partage dans les Mêmes Conditions](https://creativecommons.org/licenses/by-nc-sa/4.0/)

![Logo](https://licensebuttons.net/l/by-nc-sa/3.0/88x31.png)

En savoir plus sur [les licences Creative Commons](https://creativecommons.org/licenses/?lang=fr-FR)...
