Git est un système de versionning décentralisé > on peut l’utiliser en local avant de partager le travail avec ses collaborateurs.

Configuration de GIT :
$ git config --global user.name Anais
$ git config –global user.email anais.riviere0@gmail.com
Ces commandes permettent de définir un utilisateur sur notre machine, et ainsi permettre à GIT 
d’identifier qui a fait les modifications des fichiers dans ses commits.

	$ git config --global core.editor vim
Cette commande permet de définir un éditeur pour écrire le texte du commit, cette commande est optionnelle (l’éditeur est souvent déjà défini)

Zone de travail de Git :
git init  > permet d’initialiser le projet Git. Cette commande est indispensable car elle crée le dossier .git/ qui est l’historique git du projet.
git status > En ce placant dans le dossier versionné, permet de vérifier si tout fonctionne.
git add nomdufichier> permet d’ajouter un fichier à la zone d’index.
git add . > permet d’ajouter un ensemble de fichiers
git add -A > idem
git rm --cached >permet de désindexer le fichier
git commit -m > permet de créer un commit avec une description courte.
git commit > permet de créer un commit avec une description plus longue, cette fois un éditeur de texte s’ouvre. (pour valider et sortir : echap + :wq + entrée)
Quelques règles de message de commit :
• un titre de 49 caractères max 
• un texte plus long, répondez à la question pourquoi faire dans votre texte. 
• on peut commiter avec un titre uniquement option -m


Git Log:
git log > permet de visualiser les logs. Pour sortir de l’affichage : « q »
git log --oneline  ou git shortlog > commandes équivalentes permettant de vérifier que le commit a bien été fait.
git log master..origin/master >voir les différences entre deux branches
git log -5 > pour voir les cinq derniers commits
git log -p -5 > montre les différences entre chaque commits.
git log –stat > stat sur les modifs par commit
$ git log --since=2.weeks (ou until) > depuis deux semaines

Quelques commandes pratiques :
git help [nom de la commande]
git blame -L 40,60 readme.md  >  pour rechercher qui a fait les modifications par lignes
git blame --since=3.weeks -- readme.md > rechercher les auteurs des modifications sur les trois dernières semaines
git blame -L "/^### /" readme.md > rechercher avec une expression régulière


git mv mon_ancien_fichier mon_nouveau_fichier > permet de renommer un fichier de manière à ce que git intègre cette modification à son historique.
git restore --staged ...  > pour désindexer
git rm mon_fichier > pour supprimer un fichier

git ls-files > pour voir tous les fichiers suivis

Configuration du .gitignore
Créer le fichier .gitignore à la racine du dépôt afin d’ignorer certain fichier en les renseignant dans ce fichier. >Voici quelques pattern à utiliser :
vendor > ignore TOUS les fichiers vendors. Si on veut igorer uniquement les fichiers vendor à la racine du dépôt on utilisera :  /vendor
doc/foo/ > tous les fichiers dans doc/foo mais pas dans a/doc/foo
foo/  > les fichiers dans a/foo et foo 
foo/* > matchera avec n'importe quel fichier autre qu'un "/"
*.txt > ignore tous les fichiers qui ont cette extension dans le dépôt 
foo/*.txt --> ignore tous les fichiers de ce type dans les dossiers foo de l'application.
 /*.txt  > ignore juste au niveau racine du dépôt(les fichiers de cette extension)
**/foo --> ignore foo/a, bar/foo/a mais n'ignore pas foo/a/b
 foo[0-9] --> ignore foo0, foo1, ... foo9
 foo --> ignore a/foo, foo/a/b, a/b/foo, ...
 foo/**/bar --> ignore foo/a/b/c/bar, foo/bar, …









	

