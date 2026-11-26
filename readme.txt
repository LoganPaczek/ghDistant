PARTAGE DU HOOK PRE-COMMIT
==========================

Le dossier .git/hooks n'est pas versionné : un hook placé dedans n'est pas
transmis aux autres développeurs lors d'un clone ou d'un pull.
Le hook est donc versionné dans le dossier "hooks/" à la racine du dépôt.

Ce que fait le hook (hooks/pre-commit)
--------------------------------------
À chaque commit, il demande :
    Ajouter le fichier de suivi dans ce commit (y/[n]) ?
 - 'y' : crée suivi/commitInfo.txt contenant
         "commit vérifié le <date et heure du jour>" et l'ajoute au commit.
 - 'n' ou Entrée : le commit se fait sans fichier de suivi.

Installation (une seule fois, après le clone)
---------------------------------------------
Méthode recommandée (Git >= 2.9) : indiquer à Git d'utiliser le dossier hooks/
    git config core.hooksPath hooks

Méthode alternative : copier le hook dans .git/hooks
    cp hooks/pre-commit .git/hooks/pre-commit
    chmod +x .git/hooks/pre-commit
  (avec cette méthode, il faut recopier le fichier à chaque mise à jour du hook)

Sous Windows, utiliser Git Bash pour lancer ces commandes.

Désactivation
-------------
    git config --unset core.hooksPath
ou, ponctuellement, sans exécuter le hook :
    git commit --no-verify
