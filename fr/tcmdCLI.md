# Outil d'interface en ligne de commande

## Télécharger tcmd

* [Windows 64bit (le plus courant)](https://triggercmdagents.s3.amazonaws.com/tcmd_cli/tcmd-windows-amd64.exe)
* [Windows 32bit](https://triggercmdagents.s3.amazonaws.com/tcmd_cli/tcmd-windows-386.exe)
* [Mac 64bit](https://triggercmdagents.s3.amazonaws.com/tcmd_cli/tcmd-darwin-amd64)
* [Linux 32bit](https://triggercmdagents.s3.amazonaws.com/tcmd_cli/tcmd-linux-386)
* [Linux 64bit](https://triggercmdagents.s3.amazonaws.com/tcmd_cli/tcmd-linux-amd64)
* [Linux arm (ex : Raspberry Pi ou Orange Pi)](https://triggercmdagents.s3.amazonaws.com/tcmd_cli/tcmd-linux-arm)

Après le téléchargement, renommez-le en tcmd, ou tcmd.exe sous Windows.

Déplacez-le dans **/usr/local/bin** ou **C:\Windows**, ou dans un autre dossier listé dans votre variable d'environnement PATH si vous souhaitez pouvoir l'exécuter depuis n'importe quel dossier.

## Utilisation de tcmd

Exécutez cette commande pour obtenir l'aide :
```
tcmd -h
```

```
NOM :
    tcmd - Exécutez des commandes sur les ordinateurs de votre compte TRIGGERcmd
  UTILISATION :
    tcmd [options]

  OPTIONS :
    --trigger value, -t value   Nom du trigger de la commande à exécuter
    --computer value, -c value  Nom de l'ordinateur (laisser vide pour l'ordinateur par défaut)
    --params value, -p value    Paramètres à ajouter à la commande distante
    --panel value, -P value     Nom du panneau à utiliser
    --button value, -b value    Nom du bouton du panneau à "appuyer"
    --list, -l                  Lister vos commandes
    --listpanels, -L            Lister vos panneaux
    --pair                      Se connecter avec un code de jumelage
    --help, -h                  afficher l'aide
    --version, -v               afficher la version
```

## Code source

Vous pouvez consulter le code source Go de l'outil tcmd sur Github [ici](https://github.com/rvmey/triggercmdGOclient).

## Vidéo Youtube

Pour voir l'outil **tcmd** en action, regardez [cette vidéo Youtube](https://www.youtube.com/watch?v=q0Uu4SNFKFY).
