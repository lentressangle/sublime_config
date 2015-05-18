Partage de config Sublime Text !
==================================

Une petite astuce pour partager sa config. On peut mettre sur Git son dossier `$HOME/.config/sublime-text-3`

----------

## Que faut-il sauvegarder ?
- Les raccourcis clavier (.sublime-keymap)
- Les préférences utilisateur (.sublime-settings)
- Les builds (.sublime-build)

En plus de cela, il va falloir sauvegarder les plugins installés. Pour cela il faut avoir installé le plugin [Package Control](https://packagecontrol.io/installation), lequel permet d’installer simplement d’autres plugins via Sublime Text, mais surtout d’installer une liste complète de plugins prédéfinis ! Cette liste se trouve tout simplement dans le fichier `Package Control.sublime-settings`.


## Créer votre sauvegarde

Selon votre système d’exploitation, tous ces fichiers vont se trouver dans un dossier précis :

- `~/.config/sublime-text-3` pour Linux
- `~/Library/Application Support/Sublime Text 3` pour OS X
Rendez-vous donc dans ce dossier et créez un repository (exemple pour Windows) :

```
cd $HOME/.config/sublime-text-3
git init
```

Créez ensuite un fichier `.gitignore` pour filtrer les fichiers à sauvegarder :

```
# Tout ignorer sauf le fichier .gitignore
*
!.gitignore

# Garder le plugin Package Control uniquement
!Installed Packages
Installed Packages/*
!Installed Packages/Package Control.sublime-package

# Garder les raccourcis clavier, les préférences et les builds
!Packages
Packages/*
!Packages/User
Packages/User/*
!Packages/User/*.sublime-keymap
!Packages/User/*.sublime-settings
!Packages/User/*.sublime-build
```

Voilà votre sauvegarde prête, vous n’avez plus qu’à la mettre à jour et l’envoyer sur GitHub (n'hésitez pas à créer vos branches):
```
git remote add origin https://github.com/lentressangle/sublime_config.git
git add --all
git commit -m "Ma sauvegarde Sublime Text 3"
git push origin master
```

## Restaurer votre sauvegarde

```
cd $HOME/.config/sublime-text-3
git init
git remote add origin https://github.com/lentressangle/sublime_config.git
git fetch
git checkout -t origin/master
```
