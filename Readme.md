# TP1 - Installation Linux sur une VM - V0.1

## Groupe 

- vos noms 

## But 

Cette manipulation a pour but d'installer une distribution linux [Sparky Linux](https://sparkylinux.org/) dans une machine virtuelle VMware Workstation Player, à l’aide d’une image disque (ISO).

## Materiels à disposition 

- VMware Workstation Player - V17
- Image disque (ISO) : sparkylinux-6.4-x86_64-minimalcli.iso

## Utilisation de VMware et de l'image ISO linux 

1. Lancez VMware Workstation Player (logiciel)  

2. Sélectionnez **Create a New Virtual Machine** 

3. Placez le fichier `.iso` dans une repertoire connu : 

`C:\VosInitiales\VM\ISO`

4. Indiquez le chemin d’accès de l’image iso comme indiqué sous l’image ci-dessous :

![install image disk](/Images/Install_ISO.jpg) 

5. Choisir un nom d'OS : `Linux - Debian 11.x` 

![OS name choice](/Images/OS_Choice.jpg) 

6. Nommez la machine virtuelle : `SparkyLinux-VosInitiales` 

7. Creez un disque virtuel -> capcité : **20GB** 

> remarque$$^1$$ : cocher **store virtual disk a single file**

![Virtual disk](/Images/VirtualDisk.jpg) 

> remarque$$^2$$ : ci-dessous, la configuration de la VM 

![Virtual disk](/Images/VM_Config.jpg) 

8. Lancez la machine virtuelle : **Play virtual machine** 

## Lancement de l'image ISO (Linux - Live CD) 

Lancement du live CD : 

[Placer votre capture d'écran]() 

Shell Linux : 

[Placer votre capture d'écran]() 

> **ATTENTION** : par défaut, le clavier est configuré est **Clavier Americain**

9. Déplacez-vous à la **racine du système** en utilisant la commande suivante : `cd` 

> vore commande ?!

10. Affichez le contenu de la racine avec la commande : `ls –l`	

![Placer votre capture d'écran]() 

11. Créez un répertoire de travail nommé « EMSY_VosInitiales» dans quel dossier racine allez-vous le placer (justifiez votre réponse) et quelle commande allez-vous utiliser. 

> votre commande ?! 

12. Dans ce répertoire, créez un fichier texte que vous nommerez `TESTSLO_XXX_XXX` et éditez celui en écrivant un texte, exemple : "TP linux by XXX et XXX".
	Utiliser la commande `vi`

> votre commande ?! 

13. Tapez la commande `ls -l /dev/sda` 

![Placer votre capture d'écran]() 


## Questions / Réponses 

Q1. Comment se nomme le clavier américain ?

> votre réponse ?!

Q2. Comment se nomme le clavier suisse-romand ?

> votre réponse ?!

Q3. Comment se nomme le clavier français ? 

> votre réponse ?!

Q4. Que signifie l'option `-l` avec la commande `ls` 

> votre réponse ?!

Q5. Décrypter la ligne où se trouve le répertoire **home**    

[Placer votre capture d'écran]()

> votre réponse ?!

Q6. Si vous créez un répertoire de travail (pour éditer/sauvegarder des fichiers), dans quelle **répertoire racine** vous vous placez ? 

> votre réponse ?!

Q7. dans le répertoire `/home`, pouvez-vous éditez un fichier uniquement avec la commande `vi` 

> votre réponse ?!

Q8. Si vous éteignez la machine virtuelle et que vous la rallumez, est-ce que le répertoire créé ci-dessus existe toujours (justifiez votre réponse) ? 

> votre réponse ?!

Q9. Que signifie **sda** ? 

> votre réponse ?!

Q10. Décrypter la réponse après avoir taper la commande `ls -l /dev/sda` -> voir résultat point 13.

> votre réponse ?!



## Tips 

> $$Tips^1$$ : sortir de la VM -> appuyer simultanément sur `Ctrl` et `Alt` 

> $$Tips^2$$ : arrêter la VM proprement -> commande : `shutdown`

> $$Tips^3$$ : arrêter la VM pour cause de plantage -> commande : `halt` ou `poweroff`

> $$Tips^4$$ : [commande vi avec ses options](https://www.linuxtricks.fr/wiki/guide-de-sur-vi-utilisation-de-vi)

> $$Tips^5$$ : [éditer un fichier type markdown (.md)](https://ashki23.github.io/markdown-latex.html)

