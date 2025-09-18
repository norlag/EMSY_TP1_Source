# TP1 - Installation Linux sur une VM - V0.2

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

`C:\VosInitiales\VM\ISO`

D. Indiquez le chemin d’accès de l’image iso comme indiqué sous l’image ci-dessous :

![install image disk](/Images/Install_ISO.jpg) 

E. Choisir un nom d'OS : `Linux - Debian 11.x` 

![OS name choice](/Images/OS_Choice.jpg) 

F. Nommez la machine virtuelle : `SparkyLinux-VosInitiales` 

G. Creez un disque virtuel -> capcité : **20GB** 

> remarque$$^1$$ : cocher **store virtual disk a single file**

![Virtual disk](/Images/VirtualDisk.jpg) 

> remarque$$^2$$ : ci-dessous, la configuration de la VM 

![Virtual disk](/Images/VM_Config.jpg) 

H. Lancez la machine virtuelle : **Play virtual machine** 

## Lancement de l'image ISO (Linux - Live CD) 

G. Lancement du live CD : 

<img width="1920" height="1080" alt="lancement_live_1" src="https://github.com/user-attachments/assets/59d623f6-76d2-4fa4-85d1-51d16fcb050a" />

Shell Linux : 

<img width="1920" height="1080" alt="shell" src="https://github.com/user-attachments/assets/c98104c8-96ea-449e-9d40-62bc776376ce" />

Q1. disposition du clavier américain ?

us

Q2. disposition du clavier suisse-romand ?

fr_CH

Q3. disposition du le clavier français ? 

fr

H. Déplacez-vous à la **racine du système** en utilisant la commande suivante : `cd` 

cd /

I. Affichez le contenu de la racine avec la commande : `ls –l`	

<img width="872" height="543" alt="ls-racine" src="https://github.com/user-attachments/assets/e02e18d7-e238-46c0-bf2d-8ae948188d8f" />

Q5. Que signifie l'option `-l` avec la commande `ls` 

Affiche les dossiers du répertoire sous forme de liste

Q6. Décrypter la ligne où se trouve le répertoire **home**    

<img width="490" height="39" alt="home" src="https://github.com/user-attachments/assets/a5b708f7-811b-4e9a-ba00-64554b6111c5" />

on voit un dossier live qui s'agit du dossier utilisateur. Comme dans windows chaque utilisateur a son propre dossier utilisateur dans C:/Utilisateurs/seb par exemple

J. Créez un répertoire de travail nommé « EMSY_VosInitiales» dans quel dossier racine allez-vous le placer (justifiez votre réponse) et quelle commande allez-vous utiliser. 

mkdir /home/live/EMSY_SSR

Q7. Si vous créez un répertoire de travail (pour éditer/sauvegarder des fichiers), dans quelle **répertoire racine** vous vous placez ? 

dans /home/live

par exemple je peux créer un dossier rapports comme ceci : /home/live/rapports

K. Dans ce répertoire, créez un fichier texte que vous nommerez `TESTSLO_XXX_XXX` et éditez celui en écrivant un texte, exemple : "TP linux by XXX et XXX".
	Utiliser la commande `vi`

vi TESTSLO_SSR.txt

Q9. dans le répertoire `/home`, pouvez-vous éditez un fichier uniquement avec la commande `vi` 

non il existe plein d'autres commandes ou programmes tels que nano ou vim par exemple.

Q10. Si vous éteignez la machine virtuelle et que vous la rallumez, est-ce que le répertoire créé ci-dessus existe toujours (justifiez votre réponse) ? 

Absolument pas, la machine virtuelle n'a que démarré un live iso. Nous n'avons pas créé de partitions, ni mount un disque (aucune système de fichier n'as été attaché et l'OS n'est pas installé. il est juste chargé en mémoire)

L. Tapez la commande `ls -l /dev/sda` 

<img width="859" height="649" alt="ls_sda" src="https://github.com/user-attachments/assets/2307557f-7886-4c0d-a2ba-00aaefaeb7b5" />

Q11. Que signifie **sda** ? 

sda est un fichier spécial qui représente un disque de stockage sur linux. a pour dire que c'est le premier disque. pour un deuxième disque il aurait le nom sdb et après sdc pour un troisième, etc...

Q12. Décrypter la réponse après avoir taper la commande `ls -l /dev/sda`

<img width="403" height="35" alt="ls-sda" src="https://github.com/user-attachments/assets/9a504095-9b68-458c-b4c2-d425c93af820" />

brw-rw---- c'est la partie qui décrit les permissions sur le fichier. La première partie donne read (r) et write (w) pour l'utilisateur root et le groupe disk. Les autres utilisateurs ou groupes n'ont pas les droits d'écriture ou de lecture. Il existe également un droit d'execution mais il n'apparaît pas ici (x). le b indique qu'il s'agit d'un fichier spécial de type bloc -> voir https://www.gnu.org/software/coreutils/manual/html_node/What-information-is-listed.html#index-verbose-ls-format

ensuite, on voit l'utilisateur propriétaire. ici root, et le groupe est disk

Le numéro 8 identifie le type de périphérique (ici, disque SCSI). et le 0 indique que c'est le premier disque voir https://www.kernel.org/doc/Documentation/admin-guide/devices.txt

Ensuite on voit la dernière date de modification du fichier, ici le 18 septembre à 13:41

