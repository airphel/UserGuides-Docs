

**Pi-Star Digital Voice Software**

**Mise à jour des ID/Hosts sur Pi-star - Niveau Expert**

(Version 3 du document)

***Avertissement. Cette modification a déjà été testée par plusieurs utilisateurs et nécessite un minimum de***

***connaissances du système OS Pi-Star.***

Afin d’effectuer la mise à jour, vous trouverez ci-dessous le lien pour mettre à jour les fichiers DMRIds.dat et

DMR\_Hosts.txt pour les Dashboard de MW0MWZ (version originale) ainsi que de F1RMB **(1)** et celui de W0CHP **(2)**.

Ces mises à jour fonctionnent avec les versions

\-

\-

\-

Pi-star à partir de la version 4.1.6 et le Dashboard de MW0MWZ

Pi-star à partir de la version 4.1.6 et le Dashboard de F1RMB v4.1.15

Pi-star à partir de la version 4.1.6 et le Dashboard de W0CHP

**(1) Dashboard de MW0MWZ / F1RMB**

Si vous avez installé la version Dashboard de F1rmb, vous pouvez utiliser le « Tiny File Manager ».

Dans le fichier DMRIds.dat, vous trouverez la liste des indicatifs Radio Amateurs et Amateurs Radio.

Lien de téléchargement :

<http://www.radioshack.io/downloads/DMRIds.dat>

Une autre version du fichier existe qui permet l’affichage des indicatifs et des prénoms des opérateurs sur le

Dashboard mais qui nécessite la modification de plusieurs fichiers. **(4)**

Lien de téléchargement pour cette version du fichier (indicatifs et prénoms) :

<http://www.radioshack.fr/downloads/DMRIds.dat>

Dans le fichier DMR\_Hosts.txt, vous trouverez la liste des serveurs Radio Amateurs + Amateurs Radio avec la

configuration pour la connexion. Lien de téléchargement :

<http://www.radioshack.io/downloads/DMR_Hosts.txt>

***Afin d’effectuer les mises à jour, il existe plusieurs méthodes***

***Manuellement** :*

Vous devez télécharger et copier les fichiers via le mode « SSH Access » (configuration « Expert ») dans le répertoire

du Pi-Star : /usr/local/etc

***Automatiquement** :*

Vous devez modifier le fichier **HostFilesUpdate.sh** de votre Pi-Star pour un mise à jour automatique tous les jours

des fichiers via « SSH Access » (configuration « Expert ») en utilisant la méthode suivante en SSH :

sudo su

rpi-rw

sudo nano /usr/local/sbin/HostFilesUpdate.sh





*1) Avec votre curseur vous descendez afin de trouver la ligne suivante dans le fichier :*

**curl --fail -o \{DMRIDFILE} -s http://www.pistar.uk/downloads/DMRIds.dat**

Puis remplacer **www.pistar.uk** par **www.radioshack.io**

*Vous devriez avoir la ligne suivante après la modification :*

**curl --fail -o \{DMRIDFILE} -s http:/[/www.radioshack.io/downloads/DMRIds.dat**](http://www.radioshack.io/downloads/DMRIds.dat)**

*2) Avec votre curseur vous descendez afin de trouver la ligne suivante dans le fichier :*

**curl --fail -o \{DMRHOSTS} -s http://www.pistar.uk/downloads/DMR\_Hosts.txt**

Puis remplacer **www.pistar.uk** par **www.radioshack.io**

*Vous devriez avoir la ligne suivante après la modification :*

**curl --fail -o \{DMRHOSTS} -s http:/[/www.radioshack.io/downloads/DMR_Hosts.txt**](http://www.radioshack.io/downloads/DMR_Hosts.txt)**

Vous devez appuyer sur les touches du clavier « Ctrl + o » puis « Entrée » pour enregistrer, appuyer sur les touches

« Ctrl + x » puis « Entrée » pour quitter.

Vous devez exécuter la commande :

sudo HostFilesUpdate.sh

Pour finir, ressortir du mode « SSH Access ». Dans le menu votre Dashboard Pi-star, choisir le menu

« Configuration », puis exécuter « Mise à jour ».

**(2) Dashboard de W0CHP**

***Afin d’effectuer les mises à jour automatique avec la liste des indicatifs Radio Amateurs et Amateurs Radio.***

Vous pouvez utiliser le « Tiny File Manager » intégré à la version du Dashboard.

Vous devez modifier le fichier **HostFilesUpdate.sh** de votre Pi-Star pour un mise à jour automatique tous les jours

des fichiers via « SSH Access » (configuration « Expert ») en utilisant la méthode suivante en SSH :

sudo su

rpi-rw

sudo nano /usr/local/sbin/HostFilesUpdate.sh

*Avec votre curseur vous descendez afin de trouver la ligne suivante dans le fichier :*

**hostFileURL=https://hostfiles.w0chp.net** et rajouter un « **#** » devant la ligne

*et rajouter le ligne la ligne suivante en dessous :*

**hostFileURL=https://raw.githubusercontent.com/airphel/WPSD-HostFiles/main**

*Vous devriez avoir les lignes suivantes après la modification :*

**# hostFileURL=https://hostfiles.w0chp.net**

**hostFileURL=https://raw.githubusercontent.com/airphel/WPSD-HostFiles/main**





Vous devez appuyer sur les touches du clavier « Ctrl + o » puis « Entrée » pour enregistrer, appuyer sur les touches

« Ctrl + x » puis « Entrée » pour quitter.

Vous devez exécuter la commande :

sudo HostFilesUpdate.sh

Pour finir, ressortir du mode « SSH Access ». Dans le menu votre Dashboard Pi-star, choisir le menu

« Configuration », puis exécuter « Mise à jour ».

***(3) Pour bloquer les mises à jour automatiques et journalières des fichiers DMRIds.dat et DMR\_Hosts.txt***

Cette méthode ne bloque pas la possibilité d’effectuer la mise à jour manuellement via le Dashboard du Pi-Star et ne

bloque pas la mise à jour du système OS Pi-Star.

Vous devez vous connecter via « SSH Access » (configuration « Expert »), puis saisir les commandes :

sudo su

rpi-rw

sudo nano /usr/local/sbin/pistar-daily.cron

*Avec votre curseur vous descendez afin de trouver la ligne suivante dans le fichier :*

**/usr/local/sbin/HostFilesUpdate.sh** et rajouter un « **#** » devant la ligne

*Vous devriez avoir la ligne suivante après la modification :*

**# /usr/local/sbin/HostFilesUpdate.sh**

Vous devez appuyer sur les touches du clavier « Ctrl + o » puis « Entrée » pour enregistrer, appuyer sur les touches

« Ctrl + x » puis « Entrée » pour quitter.

Pour finir, ressortir du mode « SSH Access ». Dans votre Dashboard Pi-star, choisir le menu « Configuration », «

Système » puis « Reboot » afin de faire redémarrer le Pi-star pour que les changements soient pris en compte.

**(4) *Modification du Dashboard pour l’affichage de l’indicatif et du prénom de l’opérateur***

Uniquement pour les versions de Dashboard MW0MWZ / F1RMB.

Vous devez modifier le fichier **functions.php** de votre Pi-Star via « SSH Access » en utilisant la méthode suivante en

SSH.

Vous devez vous connecter via « SSH Access » (configuration « Expert »), puis saisir les commandes :

sudo su

rpi-rw

sudo nano /var/www/dashboard/mmdvmhost/functions.php





*Avec votre curseur vous descendez afin de trouver la ligne suivante dans le fichier :*

(Ligne 969)

**if ( strlen($callsign) < 11 ) {** et modifier la valeur 11 à 25.

*Vous devriez avoir la ligne suivante après la modification :*

**if ( strlen($callsign) < 25 )**

Vous devez appuyer sur les touches du clavier « Ctrl + o » puis « Entrée » pour enregistrer, appuyer sur les touches

« Ctrl + x » puis « Entrée » pour quitter.

Vous devez modifier le fichier **lh.php** de votre Pi-Star via « SSH Access » en utilisant toujours la méthode suivante en

SSH.

sudo su

rpi-rw

sudo nano /var/www/dashboard/mmdvmhost/lh.php

*Avec votre curseur vous descendez afin de trouver la ligne suivante dans le fichier :*

(Ligne 82)

**echo "<td align=\"left\"><div style=\"float:left;\"><a href=\"https://www.qrz.com/db/$listElem[2]\"**

**target=\"\_blank\">$listElem[2]</a>/$listElem[3]</div><div style=\"text-align:right;\">&#91;<a**

**href=\"https://aprs.fi/#!call=".$listElem[2]."\*\" target=\"\_blank\">APRS</a>&#93;</div></td>";**

*Modifier la ligne complète par :*

**echo "<td align=\"left\"><div style=\"float:left;\"><a href=\"https://www.qrz.com/db/$listElem[2]\"**

**target=\"\_blank\">$listElem[2]</a>/$listElem[3]</div></td>";**

*Avec votre curseur vous descendez afin de trouver la ligne suivante dans le fichier :*

(Ligne 85)

**echo "<td align=\"left\"><div style=\"float:left;\"><a href=\"https://www.qrz.com/db/$listElem[2]\"**

**target=\"\_blank\">$listElem[2]</a></div><div style=\"text-align:right;\">&#91;<a**

**href=\"https://aprs.fi/#!call=".$listElem[2]."\*\" target=\"\_blank\">APRS</a>&#93;</div></td>";**

*Modifier la ligne complète par :*

**echo "<td align=\"left\"><div style=\"float:left;\"><a href=\"https://www.qrz.com/db/$listElem[2]\"**

**target=\"\_blank\">$listElem[2]</a></div></td>";**

Vous devez appuyer sur les touches du clavier « Ctrl + o » puis « Entrée » pour enregistrer, appuyer sur les touches

« Ctrl + x » puis « Entrée » pour quitter.

**Rappel :** vous devez choisir la bonne version du fichier DMRIds.dat afin que les prénoms s’affichent correctement.

(Voir premier paragraphe de la page 1)

By airphel, 45F1.

