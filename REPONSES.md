
# Partie 1 — Dépôt local : comprendre le suivi de version

## 1.1 QUe fait git init et que se pass t-il dans le dossier cree apres cette commande
git init sert a ***initialiser/creer un depot local***

Il se passe qu'**un repertoire `.git` est cree dans le repertoire courant qui va contenir toutes les donnees et versions de nos fichiers et les branches**

## 1.2 Pourquoi Git considère-t-il README.md comme un fichier « non suivi» (untracked) à ce stade ?

il consisdere le fichier comme non suivit car **il n'a pas encore ete ajoute dans git(commite)**

## 1.3 Quelle est la différence entre git add et git commit ? Pourquoi Git sépare-t-il ces deux étapes au lieu de tout enregistrer directement ?
`git add` permet d'indexer (sauvegarder temporairement) les fichiers qui seront inclus dans la prochaine sauvegarde definitive tandisque `git commit` permet de sauvegarder localement les modifications via un message clair

Git separe ces deux commande pour faciliter la prise en main des fichiers du projet afin de choisir ce qu'il faut enregistrer definitivement comme modification et ce qu'il ne faut pas encore toucher

## 1.4 À quoi sert git log ? Que montre git diff avant un commit ?
git log sert a consulter l'historique de commits ( identifiant(HEAD), auteur, date, fichiers concernees(Add pour nouveau fichier et Modified pour fichier modifie))
git diff montre exactement ou sont situees les modifications par fichiers par rapport au dernier commit en precisant les lignes modifiees, ce qui a ete ajoute ousupprime

# Partie 2 — Dépôt distant : comprendre local vs distant

## 2.1 Quelle est la différence entre un dépôt local et un dépôt distant (remote) ? Que fait concrètement git push ? Que se passerait-il si vous perdiez votre ordinateur avant d'avoir fait ce push ?
Un depot local est un depot git utilisable sur son pc sans avoir besoin d'une connection a internet pour utiliser ou enregistrer ses modifications via git tabdis qu'un depot distant n'est utilisable qu'en ligne via des plateformes telles que github ou gitlab ne permettant pas seulement le versionning mais tout aussi la collaboration entre plusieurs utilisateurs

git push met a jour le depot distant en poussant en ligne les modifications locales

Si je  perdait mon ordinateur avant d'avoir fait un push les modifications ne seront disponibles que dans  mon pc perdu et pas en ligne donv je ne pourrait plus acceder a ces modifications et donc le ttravail serait perdu avec le pc

## 2.2 Pourquoi ne faut-il jamais versionner un fichier .env ou un dossier node_modules ? Que se passe-t-il si on les commit quand même ?
Il ne faut jamais versionner une fichier .env car il contient les variables environnement cle d'api et autres informations ou constantes sensibles d'une app qui ne doivent pas etre partagee ou etre rendus publiques
Il ne faut non plus versionner node_modules car c'est un repertoire lourds contenant toutes les dependances nodes  d'une application web et donc le versionner pourrait endommager le projet

# Partie 3 — Branches : comprendre le travail isolé

## 3.1 Pourquoi ne travaille-t-on pas directement sur main ? Que représente une branche par rapport au dépôt principal ?
On ne travaille pas directement sur le main car plusieurs fonctionnalitees seront developpees et permettre de prendre des risques
Une branche represente un pointeur vers un ensemble de modifications ou commit et donc tres souvent il represente une fonctionnalite du depot principal

## 3.2 Que remarquez-vous sur GitHub après ce push (dans la liste des branches) ? La branche main a-t-elle changé ?
Sur github je remarque l'apparition d'une nouvelle branche dans la liste des branches "feature/about-page"

la branche main n'a pas change
# Partie 4 — Pull Request : comprendre la revue de code

## 4.1 À quoi sert une Pull Request si on peut techniquement pousser directement sur main ? Dans une équipe, qui devrait valider une PR avant de la fusionner ?
Un pull request est une demande de fusion permettant d'eviter ou de limiter les conflits au lieu de pousser directement sur le main ce qui va casser le code existant. L'interet du pull request est de fusionner plutot que de casser ou remplacer totalement

Celui qui valide une pull request devrait-etre tout membre ayant les droit de lecture ou bien meme un architecte 

## 4.2 Pourquoi faut-il faire git pull sur main après avoir mergé la PR sur GitHub, alors que le merge a déjà eu lieu sur GitHub ?
Il faut faire un git pull sur le main en local pour mettre a jour le depot local car le merge fusionne en ligne mais pas en local

# Partie 5 — Conflit de fusion (merge conflict)
# 5.1 
## 5.2 Pourquoi ce conflit s'est-il produit ? Que représentent exactement les marqueurs <<<<<<<, ======= et >>>>>>> ? Comment auriez-vous pu éviter ce conflit en amont ?
Les modifications a fusionner dans le README coincident avec les modifications du main
Les marqueurs <<<<<<< marquent le debut du conflit
======= C'est la ligne de separation des versions en conflit
    >>>>>>> marque la fin du conflit
Pour eviter ce conflit on aurait du repartir de facon a ne pas toucher le meme fichier

# Partie 6 — Collaboration : Fork et contribution externe

## 6.1 Quelle est la différence entre un Fork et un Clone ? Pourquoi ce mécanisme est-il nécessaire quand on n'a pas les droits d'écriture sur le dépôt d'origine ?
La difference entre Fork et CLone est que le Fork cree une copie distante d'un depot d'origine dont on n'a pas les droit d'ecriture vers notre compte github tandis que clone ne cree qu'une copie locale du depot distant
Le Fork est necessaire quand on n'a pas les droits d'ecriture sur le depot d'origine car il permet apres modification de faire un pull request vers ce depot d'origine pour demander au createur d'accepeter nos mises ajours ou modifications


## 6.2 Dans ce modèle de contribution par Fork + Pull Request, qui garde le contrôle final sur le code du dépôt d'origine ? En quoi est-ce différent du travail en équipe avec des branches directement sur le même dépôt (Partie 3-4) ?

Celui qui garde le controle final sur le code du depot d'origine est le createur du depot

C'est different du travail en equipe classique dans le sens ou les depots sont differents et qu'il faut automatiquement une autorisation pour ecrire sur le projet

# Partie 7 — Issues : suivre les tâches et les problème
## 7.2 À quoi sert une Issue par rapport à une Pull Request ? Que se passe-t-il automatiquement sur l'Issue quand on fusionne une PR qui contient « closes #numéro » ?
Une issue sert a justifier ou mieux reconnaitre une pull request pour faciliter la collaboration et commenter dessus

Automatiquement apres validation et fusion de la PR l'issue est automatiquement fermee
