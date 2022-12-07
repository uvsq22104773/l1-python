# Problèmes pour le premier TD (installation)

## Accessisibilité Conda Windows
sous windows, conda n'est pas accessible directement dans le terminal de VSCode. Ce problème est déjà abordé dans le guide [d'installation](https://github.com/uvsq-info/l1-python/blob/master/INSTALL.md). Pour ma part j'ai eu du mal à faire fonctionner les solutions préconisées. Du coup j'ai tapé les commandes (conda env create, etc..) directement dans le prompt anaconda, en me plaçant dans le répertoire du projet (commande cd). Une difficulté récurrente était que les étudiants ne savaient pas le répertoire dans lequel leur projet était sauvegardé. 

## zsh avec macs récents
le dernier macOS (nommé Catalina depuis 2019) n'utilise plus un shell bash mais zsh. Ca pose des soucis d'installation de miniconda. La solution est [ici](https://conda.io/projects/conda/en/latest/user-guide/install/macos.html), (changer le path dans .zshrc)

## cartable numérique
pour le cartable numérique, le guide d'utilisation est [là](https://github.com/uvsq-info/l1-python/blob/master/CARTABLE_NUM.md)

## réseau fac
parfois les ordis se déconnectent du réseau ce qui occasionne des erreurs au moment de télécharger des fichiers. Il faut y penser. 

## Il faut un compte github
il faut que les étudiants aient un compte github, ce qui était le cas pour la plupart. Mais il faut qu'ils aient "forké" le projet initial, ce que beaucoup n'avait pas fait (cliquer le bouton "fork" en haut du [projet](https://github.com/uvsq-info/l1-python) ). 

## Chrome book si pb (cf plus loin)
Pour les étudiant.e.s qui ont des chromebook, c'es tplus complexe, on les réoriente vers du python "online"

## vscode et cartable numérique
tant que vscode n'est pas installé sur le cartable numérique, il vaut mieux rediriger les étudiants sur google colab ou autre solution de python en ligne. On peut vérifier quand même qu'ils ont bien un compte github, et fait le fork du projet. 

## création compte github
certains étudiants n'arrivent pas à créer de compte github. Souvent c'est un problème de mail qui est redirigé sur leur boîte perso... Dans ce cas, on peut télécharger le projet sur la page principale. Parfois, le compte github n'est pas reconnu au moment de le cloner dans vscode. Une solution alternative consiste à copier coller l'adresse url du dépôt github dans l'espace de saisie en haut de l'écran. 



## Problème 1: environnement.yml not found
En tapant "conda env create", message d'erreur:

C:\Users\mbye\miniconda3\scripts\environnement.yml file not found, 

*Solution* C'est une commande à taper dans le répertoire du projet car environnement.yml contient la liste des bibliothèques du projet à installer. (La commande a probalbement été tapée dans le répertoir d'install de miniconda)

## Problème 2: Authentification Github - VScode
L'authentification Github sur VSCode ne fonctionnait pas et l'erreur suivante était affichée: L'écriture des informations de connexion dans le fichier keychain a échoué avec l'erreur 'The name org.freedesktop.secrets' was not provided by any service files. Dans ce cas pas possible de clone pull. Plusieurs solutions

*Solutions* L'erreur n'est pas bloquante. Même si le token n'est pas enregistré, il est quand même utilisé pour l'opération courante (Auth with Github ou push) et l'opération aboutit correctement. En revanche l'élève doit refaire la procédure de demande de token à chaque push à cause du manque de stockage du token. Ou bien, installer le paquet gnome-keyring (avec un apt update obligatoire avant) empêche l'affichage de l'erreur et permet de se resservir du token à chaque fois que l'élève veut push. Il faut alors saisir le mot de passe "user" à ce moment là. Voir ce [lien](https://askubuntu.com/questions/1256345/cant-connect-to-github-with-vs-code)

Pour les cartables numériques, l'utilisateur "user" peut faire sudo. Si nécessaire le mot de passe est "user" mais normalement sudo ne le demandera pas. Comme les VMs sont réinitialisées à chaque redémarrage, l'utilisateur a des droits admin.


## Problème 3: Les chrome book:
  - Activation de Linux sous ChromeOS [Lien](https://support.google.com/chromebook/answer/9145439?hl=fr)
  - Installation de Python par les paquets Linux (la base est déjà installée mais il manque sans doute jupyter). On peut aussi installer miniconda je pense.
  - Installation VSCode [Lien](https://code.visualstudio.com/blogs/2020/12/03/chromebook-get-started)
  En résumé, c'est peut-être un peu plus technique que sur Linux mais moins que sous Windows. La limite est sans doute l'espace disque disponible sur certaines configurations qui intègre juste une sorte de clé USB de 32Go mais ça devrait passer. 
  - Cependant, il y avait une étudiante avec un Chromebook et bien que tout soit bien installé (linux, miniconda, vscode et git) nous n’avons pas réussi à faire fonctionner l’accès à git depuis VScode. Git fonctionne parfaitement dans le terminal, mais dès que on essai d’y accéder depuis l’interface graphique de vscode chrome book OS bloquait l’accès, soulevant des erreurs de type « APT-SECURE(8) ». Nous n’avons pas trouvé où nous devions intervenir pour éviter que le système n’empêche l’accès. Comme je l’ai dit git fonctionnant parfaitement dans le terminal, donc l’étudiante a pu cloner le répertoire par ce biais afin d’avoir accès au TD sur sa machine. 


## Utilisation de Matplotlib:
Il faut exécuter l’exemple matplotlib dans le terminal pour ne pas avoir de problème de DLL et obtenir la sortie graphique.

## Problème de Fork:

Récemment, github a restreint les modes d'authentification en ligne de commande. L'authentification par HTTPS+mot de passe n'est plus acceptée (https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/about-authentication-to-github#authenticating-with-the-command-line). Je n'ai pas encore testé si cela impacte VSCode. Au cas où vous auriez des soucis pour l'authentification, la solution proposée par github est d'utiliser un token (https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/creating-a-personal-access-token) à la place du mot de passe. 

