# Studio-se-master
http://www.deilink.fr

![alt text](https://www.deilink.fr/image/talaxie_logo.jpg "Talaxie")

> Contenu

Dépôt maître utilisant `gitslave` pour agréger tous les dépôts open source de Talaxie Studio

Ce dossier est un dossier racine GitSlave.
C'est un simple dépôt git mais il permet de travailler avec tous les dépôts open source de Talaxie Studio en tant qu'esclaves.

Installer GitSlave
==================
GitSlave est l'outil que vous pouvez utiliser pour effectuer des commandes multi-dépôts. Afin de l'utiliser à son plein potentiel, veuillez installer :
* perl
* cloner ce dépôt localement si ce n'est pas déjà fait.
* déplacer le dossier `tools/gitslave-2.0.2` dans vos propres dossiers utilisateur.
* Ensuite, vous pouvez créer un alias vers le script principal appelé "gits" (utilisez gits_for_mac si vous êtes sur Mac).

Comment l'utiliser
------------------
La liste des dépôts gérés par ce dépôt `gitslave` se trouve dans le fichier `.gitslave`
Toutes les commandes Gitslave sont disponibles ici : http://gitslave.sourceforge.net/gits-man-page.html

Si vous souhaitez télécharger (cloner) tous les dépôts esclaves du studio, utilisez la commande

```shell
gits populate --with-ifpresent
```

Si vous souhaitez télécharger un ensemble de dépôts esclaves, utilisez

```shell
gits populate <nom_du_depot1> <nom_du_depot2>
```
Ne pas utiliser Git slave
==========================
Vous pouvez configurer tous les dépôts git manuellement.
L'idée est de cloner tous les dépôts requis les uns à côté des autres, y compris celui-ci, en utilisant la commande `git clone`.
Vous trouverez la liste des dépôts dans le fichier [.gitslave](../master/.gitslave) racine pour chaque branche.

Construire le Studio Open Source
=================================
Pour construire le Studio, vous devrez peut-être augmenter la taille du tas mémoire Java utilisé. Par conséquent, vous devez configurer une variable d'environnement Maven spécifique avec les valeurs suivantes, en supposant que vous ayez suffisamment de RAM sur votre machine :)
Voici comment faire sur Linux ou Mac

```shell
export MAVEN_OPTS='-Xmx8000m -XX:MaxPermSize=512m -XX:-UseConcMarkSweepGC'
```
sur Windows

```shell
set MAVEN_OPTS=-Xmx8000m -XX:MaxPermSize=512m -XX:-UseConcMarkSweepGC
```

Tout ce qui suit suppose que Maven est installé sur votre machine.
D'abord, si vous n'avez jamais construit d'artefacts Studio sur votre machine, vous devez construire le pom.xml parent, alors veuillez faire

```shell
cd talend.studio.parent.pom mvn clean install
```

Ensuite, revenez à la racine de ce dépôt et lancez la même commande *Maven* pour construire tous les artefacts Studio.

```shell
mvn clean install
```

L'exécutable généré se trouvera alors sous 2 formes : un fichier zip et un dossier décompressé prêt à être exécuté.
* Le fichier zip peut être trouvé dans `studio-se-master\build\talend.studio.tos.di.product\target\products\`
* Le dossier décompressé prêt à exécuter peut être trouvé dans `studio-se-master\build\talend.studio.tos.XX.product\target\products\org.talend.studio.tos.XX.product\win32\win32\`


Si vous souhaitez construire un seul ou plusieurs produits, vous pouvez utiliser un ou plusieurs des arguments Maven suivants :
```shell
-Dtos.bd=true -Dtos.di=true -Dtos.dq=true -Dtos.esb=true
```

## Support

Vous pouvez demander de l'aide sur notre [Forum](https://talaxie.deilink.fr/).

## Contributeurs

Voir le fichier [CONTRIBUTORS.md](https://talaxie.github.io/) pour plus de détails.

## Licence

Copyright (c) 2023-2024 Talaxie

Sous licence Apache v2 et GPLv2
