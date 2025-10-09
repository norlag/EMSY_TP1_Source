# TP1 - Installation Linux sur une VM - V2

## Groupe 

SSR

## But 

Cette manipulation a pour but d'installer une distribution linux [Sparky Linux](https://sparkylinux.org/) dans une machine virtuelle VMware Workstation Player, à l’aide d’une image disque (ISO).

## Materiels à disposition 

- VMware Workstation Player - V17
- Image disque (ISO) : sparkylinux-6.4-x86_64-minimalcli.iso

## Utilisation de VMware et de l'image ISO linux 

A. Lancez VMware Workstation Player (logiciel)  

B. Sélectionnez **Create a New Virtual Machine** 

C. Placez le fichier `.iso` dans une repertoire connu : 

`C:\SSR\VM\ISO`

D. Indiquez le chemin d’accès de l’image iso comme indiqué sous l’image ci-dessous :

![install image disk](/Images/Install_ISO.jpg) 

E. Choisir un nom d'OS : `Linux - Debian 11.x` 

F. Nommez la machine virtuelle : `SparkyLinux-SSR` 

G. Creez un disque virtuel -> capcité : **20GB** 

> remarque : cocher **store virtual disk a single file**

![Virtual disk](/Images/VirtualDisk.jpg) 

> remarque : ci-dessous, la configuration de la VM 

![Virtual disk](/Images/VM_Config.jpg) 

H. Lancez la machine virtuelle : **Play virtual machine** 

## Lancement de l'image ISO (Linux - Live CD) 

G. Lancement du live CD : 

<img width="1920" height="1080" alt="lancement_live_1" src="https://github.com/user-attachments/assets/59d623f6-76d2-4fa4-85d1-51d16fcb050a" />

Shell Linux : 

<img width="1920" height="1080" alt="shell" src="https://github.com/user-attachments/assets/c98104c8-96ea-449e-9d40-62bc776376ce" />

A ce moment là, le clavier est en mode américain. J'utilise la commande loadkeys fr_CH pour le mettre en suisse romand

### Q1. disposition du clavier américain ?

us -> qwerty

### Q2. disposition du clavier suisse-romand ?

fr_CH -> qwertz

### Q3. disposition du le clavier français ? 

fr -> azerty

H. Déplacez-vous à la **racine du système** en utilisant la commande suivante : `cd` 

cd /

I. Affichez le contenu de la racine avec la commande : `ls –l`	

<img width="872" height="543" alt="ls-racine" src="https://github.com/user-attachments/assets/e02e18d7-e238-46c0-bf2d-8ae948188d8f" />

### Q5. Que signifie l'option `-l` avec la commande `ls` 

Affiche les dossiers du répertoire sous forme de liste, avec les détails pour chaque dossier et fichier.
Dans le sens de lecture :
La première colonne s'agit du type de fichier : par exemple d pour dossier, l pour lien symbolique ou un - pour un fichier normal
Ensuite à côté on retrouve les permissions de lecture (r), écriture (w) et exécution (x) pour l'utilisateur, le groupe ou les autres utilisateurs. Là ou se trouve un - c'est que l'on a pas un droit.
root  root s'agissent des propriétaires du fichier. le premier root c'est l'utilisateur et le deuxième le groupe d'utilisateurs. il peut il y avoir plusieurs utilisateurs dans un groupe.
Colonne suivante, on retrouve la taille en octet du fichier, la dernière date de modification et finalement le nom.
Les noms ou l'on trouve un flèche -> s'agissent de liens symboliques
Dans le screenshot on peut voir l'arborescence de base de linux essentielle à son bon fonctionnement.

### Q6. Décrypter la ligne où se trouve le répertoire **home**    

<img width="490" height="39" alt="home" src="https://github.com/user-attachments/assets/a5b708f7-811b-4e9a-ba00-64554b6111c5" />

on voit un dossier live qui s'agit du dossier utilisateur. Comme dans windows chaque utilisateur a son propre dossier utilisateur dans C:/Utilisateurs/seb par exemple

J. Créez un répertoire de travail nommé « EMSY_VosInitiales» dans quel dossier racine allez-vous le placer (justifiez votre réponse) et quelle commande allez-vous utiliser. 

mkdir /home/live/EMSY_SSR

### Q7. Si vous créez un répertoire de travail (pour éditer/sauvegarder des fichiers), dans quelle **répertoire racine** vous vous placez ? 

dans /home/live

par exemple je peux créer un dossier rapports comme ceci : /home/live/rapports

K. Dans ce répertoire, créez un fichier texte que vous nommerez `TESTSLO_XXX_XXX` et éditez celui en écrivant un texte, exemple : "TP linux by XXX et XXX".
	Utiliser la commande `vi`

vi TESTSLO_SSR.txt

### Q9. dans le répertoire `/home`, pouvez-vous éditez un fichier uniquement avec la commande `vi` 

non il existe plein d'autres commandes ou programmes tels que nano ou vim par exemple.

### Q10. Si vous éteignez la machine virtuelle et que vous la rallumez, est-ce que le répertoire créé ci-dessus existe toujours (justifiez votre réponse) ? 

Absolument pas, la machine virtuelle n'a que démarré un live iso. Nous n'avons pas créé de partitions, ni mount un disque (aucune système de fichier n'as été attaché et l'OS n'est pas installé. il est juste chargé en mémoire)

L. Tapez la commande `ls -l /dev/sda` 

<img width="859" height="649" alt="ls_sda" src="https://github.com/user-attachments/assets/2307557f-7886-4c0d-a2ba-00aaefaeb7b5" />

### Q11. Que signifie **sda** ? 

sda est un fichier spécial qui représente un disque de stockage sur linux. a pour dire que c'est le premier disque. pour un deuxième disque il aurait le nom sdb et après sdc pour un troisième, etc...

### Q12. Décrypter la réponse après avoir taper la commande `ls -l /dev/sda`

<img width="403" height="35" alt="ls-sda" src="https://github.com/user-attachments/assets/9a504095-9b68-458c-b4c2-d425c93af820" />

brw-rw---- c'est la partie qui décrit les permissions sur le fichier. La première partie donne read (r) et write (w) pour l'utilisateur root et le groupe disk. Les autres utilisateurs ou groupes n'ont pas les droits d'écriture ou de lecture. Il existe également un droit d'execution mais il n'apparaît pas ici (x). le b indique qu'il s'agit d'un fichier spécial de type bloc -> voir https://www.gnu.org/software/coreutils/manual/html_node/What-information-is-listed.html#index-verbose-ls-format

ensuite, on voit l'utilisateur propriétaire. ici root, et le groupe est disk

Le numéro 8 identifie le type de périphérique (ici, disque SCSI). et le 0 indique que c'est le premier disque voir https://www.kernel.org/doc/Documentation/admin-guide/devices.txt

Ensuite on voit la dernière date de modification du fichier, ici le 18 septembre à 13:41

Et finalement le nom du fichier

# Installation de sparky

En me basant sur le wiki de sparky accessible à l'adresse suivante : https://wiki.sparkylinux.org/doku.php/advanced_installer

## Question M

<img width="798" height="586" alt="image" src="https://github.com/user-attachments/assets/38fd1f37-f313-45a0-9151-dacb4e653880" />

Je me met comme demandé en administrateur en supposant que l'utilisateur live n'est pas admin, j'exécute la commande "sudo su" pour me "login" en tant qu'utilisateur sudo pour pouvoir lancer mon installation
Je lance l'installateur avancé avec la commande "sparky-installer"

<img width="802" height="599" alt="image" src="https://github.com/user-attachments/assets/d149e771-7051-4a42-a037-e819a47892c5" />

Il est écrit qu'il est fortement recommendé de quitter l'installateur et vérifier qu'il existe une nouvelle version de celui-ci. Je quitte donc l'installateur.
Avec les commandes qu'ils m'ont indiqué "apt update" et "apt install sparky-backup-core" je met à jour l'installateur.

<img width="852" height="573" alt="image" src="https://github.com/user-attachments/assets/0fc2f99e-635d-4e6e-89c7-8ba5831e1839" />

On peut voir que le package sparky-backup-core a été mis à jour

Lorsque je lance la partie d'installation pour les différentes partitions, je laisse GPT

<img width="714" height="586" alt="image" src="https://github.com/user-attachments/assets/59e2ed02-c4f0-4249-8e6a-f5cc443e9586" />

Je n'ai aucune partition de créée :

<img width="938" height="695" alt="image" src="https://github.com/user-attachments/assets/d7405e4d-fb41-46f2-8d2c-8dbad3b79d53" />

### Q13
Selon le wiki : La taille de disque minimum recommandée par le wiki est de 10 à 20GB pour la partition root principale. La partition swap doit être entre 500MB et 1GB. La partition efi doit faire entre 100 et 300MB.

<img width="868" height="592" alt="image" src="https://github.com/user-attachments/assets/77bdda00-0eff-4653-b7bb-5a1bcad32678" />

Ma table de partitions

### Q14
Elle sert à, lorsque il n'y a plus de place dans la ram, stocker les données temporaires des processus (programmes) de l'OS

### Q15
exFAT

### Q16
On nous demande un nom d'utilisteur normal avec son mot de passe et on nous demande directement le mot de passe pour le compte root qui s'agit du compte administrateur qui a tout les privilèges sur le système.

## Question M.

<img width="666" height="447" alt="image" src="https://github.com/user-attachments/assets/de9adeaa-2da7-45ff-890a-084ee4a72ea6" />

Mon écran GRUB

## Question O.
J'utilise la commande sudo dpkg-reconfigure keyboard-configuration qui m'ouvre une configuration du clavier. La je peux choisir sous German (Switzerland) mon clavier French (Switzerland)

## Question P.

<img width="793" height="371" alt="image" src="https://github.com/user-attachments/assets/9249731f-ad06-461e-b84c-c6be09b44edd" />

la commande nano -version ne fonctionne manifestement pas. Je procède à l'installation du programme avec la commande "apt install nano"
Moi même m'étant connecté en tant qu'utilisateur root avec la commande "sudo su", je peux omettre la commande "sudo" car j'ai déjà tout les droits administrateur. Sinon j'aurait du faire "sudo apt install nano"
La commande sudo est utilisée lorsque l'on veut executer une commande spécifique qui nécessiterait les droits en tant qu'utilisateur "normal" sans devoir se connecter en tant qu'administreur juste pour faire la commande.

### Q17.
Nano est un éditeur de texte à partir de la console tel que vi ou bien vim. Il est simple d'utilisation, c'est pourquoi il est mon editeur de choix en tant normal dans la console.
Lorsque l'on a ouvert un fichier avec nano, les commandes de base sont : ctrl+O pour écrire dans le fichier, ctrl+X pour sortir, ctrl+G pour voir une page d'aide. Il existe d'autres commandes bien sûr, on les retrouve dans la page d'aide ainsi que en bas de la console pour référence :

<img width="841" height="648" alt="image" src="https://github.com/user-attachments/assets/631541e8-a682-4bab-b56e-1df04956964a" />

## Question Q.
### Q18.
Je lance la commande "git" pour voir si quelque chose se passe, alternativement on peut faire "git --version" ou "man git"

### Q19.
En tant que root, j'utilise la commande "apt install git". Cette commande s'occupe de télécharger et d'installer le package git

### Q20.
apt vient de "Advanced package tool". Ce programme nous permet de gérer, installer ou supprimer les programmes ainsi que de mettre à jour le système.

### Q21.
apt n'est pas forcément disponible sur toutes les distributions. Cela est un choix pour chaque éditeur d'OS de l'intégrer par défaut ou non sur l'OS. D'expérience par exemple sur Arch linux, le gestionnaire de packets se nomme pacman et il fonctionne différemment de apt. 

## Question R.
### Q22.
Le répertoire de l'utilisateur seb se trouve dans /home/seb/

### Q23.
étant déjà dans mon répertoire, je vais juste lancer la commande "mkdir EMSY_TP1_SSR" en tant qu'utilisateur seb. Je le précise car j'était en root avant, j'ai fait la commande "exit" pour me déconnecter et je me suis login en tant que utilisateur seb pour la manipulation. Autrement en tant que root j'aurais du modifier les permissions sur le dossier.

## Question S.
Je vois un dossier contenant mon repo git qui se nomme EMSY_TP1_Source

## Question T.
Mon hello world :

<img width="825" height="631" alt="image" src="https://github.com/user-attachments/assets/530bc363-57a8-4855-bd87-4256566636b3" />

## Question U.
Ma version de gcc :

<img width="634" height="121" alt="image" src="https://github.com/user-attachments/assets/fd8d29ba-76ad-4ff1-a586-f951c6f60743" />

### Q25.
Les fichiers qui sont générés sont :
EMSY_TP1.o qui contient du code machine
ainsi que EMSY_TP1 l'exécutable

Malheureusment les commandes qui nous sont proposées dans la donnée ne fonctionnent pas. J'ai un message d'erreur :

<img width="814" height="86" alt="image" src="https://github.com/user-attachments/assets/5bd90bbe-53fa-487c-98b8-23c3977545ed" />

Alternativement à la place j'ai donc continué en utilisant la commande "gcc EMSY_TP1.c -o EMSY_TP1" 

Après quelques recherches, je trouve qu'il faut pour la première commande ne pas spécifier le fichier .o avec la commande "gcc -Wall -o fichier.o -c fichier.c". A la place il faut juste faire "gcc -Wall -c fichier.c"
Ensuite nous pouvons générer l'exécutable normalement avec la commande "gcc -o EMSY_TP1 EMSY_TP1.o"

## Question V.
### Q26.
Lorsque j'exécute mon programme avec la commande ./EMSY_TP1, mon hello world s'affiche sur la console :

<img width="420" height="34" alt="image" src="https://github.com/user-attachments/assets/1bc87b8f-3ce7-4910-990a-646ec052a7fa" />






















