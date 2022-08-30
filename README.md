# conf-steakoverlow-2022
Bypass d'authentification depuis le GRUB | SteakOverflow 2022

# GRUB

* Le **GRUB** est un programme d'amorçage s'exécutant dès lors de la mise sous tension de la machine. 
* Il permet de sélectionner sur quel système d'exploitation ou noyeau (kernel) vous allez booter, pratique dans les cas de dual boots, modifications et développement kernel. (ou simplement rescue)
* Permet de communiquer directement avec le kernel.

# GRUB (Chiffrement)

* Généralement situé en **clear** sur une partition annexe à votre système `(/boot) ` dans les cas **d'installation/partitionnement assité**, se configure de façon plus sécurisée lors d'un **partitionnement manuel**


# Elévation de privilège / Privesc 

* Permet de gérer les actions attribués aux utilisateurs, contient trois attributions (nommés flag) principale: **read, write, execute**. > voir prochaine slide.
* Une élévation de privilège est un mécanisme **malveillant** permettant à un utilisateur d'obtenir des droits supérieurs à celui attribués de base. 
* Le but de cette **manipulation** est d'accéder à la machine sans mot de passe (dans notre cas précis), voler et/ou manipuler des données  
***
* Dans cet exemple nous avons le path de `zsh` dans `/bin/zsh` , nous pouvons diviser ses droits en **trois parties**: 
![Classes flags](:/a7b08ceb650b4002aaccf083e6e26340)
1. **Owners**: Pour la personne pocédent le fichier.
2. **Group**: Pour le groupe possédant le fichier
3. **Other**: Pour tout les autres utilisateurs

# Privesc local depuis le GRUB

* Exemple de partitionnement non chiffré: le /boot se trouve sur une partition annexe au reste, malgrè cela les deux communiquerons lors du boot. Grâce à cette faiblesse de sécurité, nous allons pouvoir directement injecté des paramètres. 
***
* Ici, nous allons modifier les flags `ro`  par `rw` , ces deux la seront par la suite load dans notre configuration. 
`ro` correspond à **Read-Only**, ceci autorise **seulement** la **lecture.**
`rw` correspond à **Read-Write**, ceci autorise l'**écriture** et la **lecure.**
***
* Par la suite nous ajoutons un paramètre `init`, c'est une option de **start-up kernel**, il prend n'importe quel **binaire/executable** en paramètre.
`/bin/bash` renvoi au shell bash.
* Nous pouvons par la suite boot en appuyant sur `F10`.

Nous voilà sur un **shell root**.

# Quelques commandes avant de partir

...

## Kernel Panick
* La **panique du noyau** est un mécanisme de signalement d'erreur système du noyeau d'un **système d'exploitation**. Cette erreur de bas-niveau se produit lorsque l'**OS** ne peut rapidement ou facilement remider au problème.

# Pourquoi et comment chiffrer ? 

* Pour garantir la sécurité de tes données personnelles.
* En utilisant **LUKS** & **LUKS** lors de votre partitionnement.
* En utilisant le package **encryptfs** pour une installation déjà faite. 
* En assistant à ma prochaine rump traitant de la continuiter de celle-ci ! 

