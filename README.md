# Git - Les commandes usuelles 

## Table de matières 

- [Introduction](#Introduction) 
- [Avoir de l'aide sur une commande](#Avoir-de-laide-sur-une-commande)
- [Faire les configurations de base](#Faire-les-configurations-de-base)
- [Installation d'un projet en local](#Installation-dun-projet-en-local)
- [Récuperer en local le repository sur Github](#Récuperer-en-local-le-repository-sur-Github) 
- [Log](#Log) 
- [Créer une noouvelle branche](#Créer-une-noouvelle-
branche)
- [Concepts de base de Markdown](#Concepts-de-base-de-Markdown)

## Introduction 

Pour assurer un bon suivi des versions de votre codes source; l'optimisation du travail collaboratif de vos équipes; l'améliorer des performances et booster votre code sources, voici les commandes **git** usuelles. 

## Avoir de l'aide sur une commande  

- **Syntaxe :**

```shell
git help nom-de-votre-commande
```

- **Exemple :** 

```shell
git help config
git help push
git help pull
git help branch
```
  
## Faire les configurations de base  

- **Exemple :** 

```shell
# Nom d'identification 
git config --global user.name "LorinceTawamba"

# Email d'identification
git config --global user.email "lorince.tawamba@gmail.com"

# Outil d'édition
git config --global core.editor subl

# Outil de difference 
git config --global merge.tool filemerge 

# Branche par defaut  
git config --global init.defaultBranch main

# Lister les configurations globales existantes 
git config --list
```

## Installation d'un projet en local 

```shell
# Se déplacer vers le dossier du projet 
cd chemin/vers/mon_dossier/du_projet 

# Initialiser le dossier du projet au suivi de version par git  
git init 

# Créer un fichier de suivi git   
echo "# NOM DE MON PROJET" >> readme.md

# Ajouter le fichier dans le suivi git    
git add readme.md 

# Sauvegarder le suivi git du fichier     
git commit -m "first commit" 

# Ajouter le fichier dans le suivi git + Sauvegarder le suivi git du fichier     
git commit -am "first commit" 

# Configurer le repository local avec un ripository distant      
git remote add origin https://github.com/LorinceTawamba/git-commandes.git 

# Transférer les sauvegardes du repository local vers le repository distant     
git push -u origin main
```

## Récuperer en local le repository sur Github

```shell
git clone https://github.com/LorinceTawamba/git-commandes.git chemin/vers/mon_dossier/du_projet/en_local
```

>[!NOTE]
>
>Mon repository est composé d'au moins deux branch.
>- **feature** : dédié au développement de nouvelle fonctionalités
>- **bug** : dédié aux correction de bug.
>- **master** : reflète le code en production. Personne ne doit travailler directement sur cette branch.

## Log

```shell
# Classique
git log

# Affiche X derniers commits
git log -n X

# Affiche les commits concernant un dossier
git log --oneline -- chemin/vers/mon_dossier

# Affiche un ensemble de commits par date
git log --since=date --until=date

# Représentation de l’historique à partir de HEAD (commit / branch)
git log --oneline --graph --decorate

# Représentation de l’historique à partir d'un fichier (commit / branch)
git log --oneline --graph --decorate nom_du_fichier
```

## Créer une noouvelle branche

```shell
# Deux lignes: créer et basculer sur la nouvelle branch
git branch feature/nom_de_ma_branch_nouvelle
git checkout feature/nom_de_ma_branch_nouvelle

ou 

git branch bug/nom_de_ma_branch_nouvelle
git checkout bug/nom_de_ma_branch_nouvelle

# Une seule ligne: créer et basculer
git checkout -b feature/nom_de_ma_branch_nouvelle 

ou 

git checkout -b bug/nom_de_ma_branch_nouvelle
```


# A REORGANISER ICI 

Pour récupérer votre branch dev

```shell
git branch -a
git checkout origin/dev
git checkout -b dev origin/dev
git branch
```

## Developpement : Branch dev

## Prod : Branch Master

```shell
# On se met sur la branche master
git checkout master
# On merge la branche dev
git merge dev
# Pour pousser les changements
git push origin master
# Penser à revenir sur dev
git checkout dev
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

Ou 

```shell
git commit -am "initial commit"
```

## Ignorer les changements sur la branche

```shell
git stash
```

## Restaurer les changements sur la branche

```shell
git stash apply
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

# Diff

```shell
# Affiche la différence entre le contenu du dernier commit et celui du 
# répertoire de travail. Cela correspond à ce qui serait commité par git commit -a.
git diff HEAD

# Affiche la différence entre le contenu pointé par A et celui pointé par B.
git diff A B

# Diff entre un dossier présent sur deux branches
git diff master..MA_BRANCH chemin/vers/mon_dossier
```

# Modifier l'historique

## Modifier le message du dernier commit

```shell
git commit --amend
```

La commande ci-dessus charge le dernier message dans l'éditeur,

* Modifier message ;
* Enregistrer et quitter l'éditeur afin de prendre les modifs en compte.

## Ajouter des fichiers au dernier commit

```shell
git add mon_fichier
git commit --amend
```

## Éditer l'historique avec rebase

```shell
# Historique des trois derniers commits
git rebase -i HEAD~3
```

Ce qui va affichier ceci dans votre éditeur de texte.

```shell
pick 6cbdbe2 Message du commit 3
pick 0a75a2d Message du commit 2
pick da74a4e Message du commit 1

# Rebase b8d6fe1..da74a4e onto b8d6fe1 (3 commands)
#
# Commands:
# p, pick = use commit
# r, reword = use commit, but edit the commit message
# e, edit = use commit, but stop for amending
# s, squash = use commit, but meld into previous commit
# f, fixup = like "squash", but discard this commit's log message
# x, exec = run command (the rest of the line) using shell
# d, drop = remove commit
#
# These lines can be re-ordered; they are executed from top to bottom.
#
# If you remove a line here THAT COMMIT WILL BE LOST.
#
# However, if you remove everything, the rebase will be aborted.
#
# Note that empty commits are commented out
```

Chaque commit est précédé du mot `pick`, utiliser tous les mots-clés possibles.

* Pour éditer, un commit changer `pick` par `edit` ;
* Enregistrer et quitter l'éditeur afin de prendre les modifs en compte ;
* Et suivre les instructions.

Pour valider, les changements utiliser la commande :

```shell
git rebase NOM_DE_MA_BRANCH
```

Dans le cas, ou les commits modifier sont déjà présent sur la branch distante, il faura "forcer"

```shell
git push --force origin NOM_DE_MA_BRANCH
```


# Tag

## Retourne la liste des tags disponible

```shell
git tag
# ou
git tag -l
git tag --list
```

## Créer un tag 

```shell
# `-m` permet d'ajouter un message associé au tag
git tag -a v1.0 -m "Mon commentaire pour la version 1.0"

# Ajouter un tag à partir d'un commit anterieur
git tag -a v1.0 -m "Mon commentaire pour la version 1.0" md5_commit
```

## Vérifier un tag en affichant les informations

```shell
git tag -v nom_de_l_étiquette
```

## Un message test
Cette partie est une message de test.

## This'll  be a _Helpful_ Section About the Greek Letter Θ!
A heading containing characters not allowed in fragments, UTF-8 characters, two consecutive spaces between the first and second words, and formatting.

# Concepts de base de Markdown 

## Titres

# This is level 1 (article title)
## This is level 2
### This is level 3
#### This is level 4
##### This is level 5

## Texte de base

   This text is **bold**.
   This text is *italic*.
   This text is both ***bold and italic***.

## Listes numérotées et listes à puces

1. This is step 1.
1. This is the next step.
1. This is yet another step, the third.

* First item in an unordered list.
* Another item.
* Here we go again.

## This is the fourth step.

   >[!NOTE]
   >
   >This is note text.

## Tableaux 

| Header | Another header | Yet another header |
|--- |--- |--- |
| row 1 | column 2 | column 3 |
| row 2 | row 2 column 2 | row 2 column 3 |

## Blocs de notes

Vous pouvez choisir parmi ces types de blocs-notes afin d’attirer l’attention sur un contenu spécifique :

[!NOTE]
[!TIP]
[!IMPORTANT]
[!CAUTION]
[!WARNING]
[!ADMINISTRATION]
[!AVAILABILITY]
[!PREREQUISITES]
[!ERROR]
[!ADMINISTRATION]
[!INFO]
[!SUCCESS]

**Exemple:**

>[!NOTE]
>
>This is a standard NOTE block.

>[!TIP]
>
>This is a standard TIP.

>[!IMPORTANT]
>
>This is an IMPORTANT note.

>[!CAUTION]
>
>This is an CAUTION note.

>[!WARNING] 
>
>This is an WARNING note.

>[!ADMINISTRATION]
>
>This is an ADMINISTRATION note.

>[!AVAILABILITY]
>
>This is an AVAILABILITY note.

>[!PREREQUISITES]
>
>This is an PREREQUISITES note.

>[!ERROR]
>
>This is an ERROR note.

>[!ADMINISTRATION]
>
>This is an ADMINISTRATION note.

>[!INFO]
>
>This is an INFO note.

>[!SUCCESS]
>
>This is an SUCCESS note.

## Pousser les tags sur la branch distante

```shell
git push origin nom_de_l_étiquette

# Pousser plusieurs tags sur la branch
git push origin --tags
```



# Authors

* **Lorince TAWAMBA** _alias_ [@LorinceTawamba](https://github.com/LorinceTawamba)

Read the list of [contributors](https://github.com/lorince-tawamba/gescom/contributors) to see who helped with the project ! 

# License

Ce document est placé sous licence CC BY-NC-SA :  [Creative Commons
Attribution - Pas d'Utilisation Commerciale - Partage dans les Mêmes Conditions](https://creativecommons.org/licenses/by-nc-sa/4.0/)

![Logo](https://licensebuttons.net/l/by-nc-sa/3.0/88x31.png)

En savoir plus sur [les licences Creative Commons](https://creativecommons.org/licenses/?lang=fr-FR)...
