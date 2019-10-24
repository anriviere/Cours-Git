Les Branches :
Une branche est un pointeur mobile dirigé vers un des commits.
La première branche , (la branche master) est créée lors de la création du dépôt par l’utilisation de :
git init
Le pointeur « master » se déplace au fur et à mesure sur le dernier commit créé.
Système optimisé : une branche est un fichier d’environ 40 charactères.(on peut en faire autant qu’on veut)
git branch dev > permet de créer une branche
git branch > affiche l’ensemble des branches du dépôt.

git checkout dev >permet de se déplacer sur une branche (on déplace le HEAD)
	une fois que la branche est créée les deux pointeurs (head et dev se déplacent sur le dernier commit)
git checkout master > retour sur la branche master
git checkout -b feature_header > permet, en une seule commande, de créer une branche et de se déplacer dessus.

Suppression d’une branche :
git branch -d [nom de la branche] >sert à supprimer une branche
git branch -D [nom de la branche] > force la suppression d’une branche (git empèche la suppression d’une branche dont l’espace de travail n’est « pas propre »
Merge sans divergence : fast-forward
Si il n’y a pas eu de divergence entre master et dev, une fois votre travail sur la branche dev terminé , on peut la merger dans master.
Pour cela : 1. On se place sur la branche master en utilisant : git checkout master
	      2.On utilise : git merge dev (merge sans commit de merge)
                    Ou       git merge dev –no-ff > crée un commit de merge même dans le cas d’un merge sans divergence.

git branch –no-merged > liste toutes les branches non mergées.
git log --oneline --graph  > visualiser le graph des commits (à partir de la branche master)

Les branches peuvent diverger :
Si l’historique sur la branche master avance par rapport à une autre branche, l’historique Git diverge. Dans ce cas lorsque l’on merge il peut avoir des conflits entre deux versions d’un fichier. Git propose un système de gestion de conflit : Lorsque l’on merge on va devoir choisir entre les deux version (sur vs code). Pour finaliser le merge il faut ajouter les modifications à l’index et finir par un commit (création du commit de merge)
En cas de divergence il y a TOUJOURS un commit de merge !

Le remisage :
Lorsque l’on veut changer de branche, celle sur laquelle on se trouve doit être en état « nothing to commit ». !!Git nous empêche de quitter la branche si ce n’est pas le cas !!
Un commit ne doit pas être fait par dépit. Donc en cas d’urgence, pour quitter la branche sans faire de commit, alors que la feature n’est pas terminée (par ex pour fixer un bug sur la branche master), on REMISE le code. Git possède une commande pour remiser le code, c’est-à-dire quitter la branche sans faire de commit et d’y revenir plus tard en récupérant le code remisé pour terminer la feature.
Remiser revient à mettre le dépôt dans l’état : « rien à valider, la copie de travail est propre ».
git stash > remiser le code non terminé
git stash list >lister les stash sur la branche.
git stash apply >permet de récuperer ce qui était dans la stash, c-a-d de récupérer son code modifié.
Il appliquera la dernière remise dans la pile laissée.
git stash apply --index > si on avait du code dans l’index. (sinon git remet tout dans le WD)
git stash drop >permet de supprimer ce qui se trouve dans la remise (1er stash de la pile).

git stash list > appliquer un stash de la remise en particulier
git stash apply stash@{1} > appliquer un stash en particulier
git stash drop stash@{1} > supprime le stash appliqué

Les Tags :
2 types de tags : annotés et légers > utilisé pour marquer un état important du logiciel
Tag léger > contrairement aux branches, il n’est pas mobile. Il est associé à un commit.
Tag annoté > objet dans Git  , il pointe sur un commit, il n’est pas mobile. Il possède : somme de contrôle + mail de l’auteur, date, message et potentiellement signé et vérifié.
git tag -a v1.0 -m  >tag annoté (version 1 de l’application)
git tag v1 >tag léger (peu utilisé)
git tag -a v1.0.1 -m "version 1.0.1" 9fceb2 > étiqueter après coup sur un commit donné.

git tag > liste des tags
git tag -1 ‘v8.*’  > rechercher des tags particuliers
git show v8.2 > Voir un tag annoté

Introduction aux branches distantes :
Git Server :
On peut créer un serveur git sur un serveur distant, une machine, clé USB …
git --bare init > création du serveur Git

cd my_lessons 
git init  
echo "# Lessons" > README.md 
git add . 
git commit -m 'first 
git remote add origin C:\Labs\my_lessons_server.git  > chemin absolu sur votre machine pour indiquer où se trouve serveur
git push origin master > push la branche master dans votre dépôt dans le serveur origin
git pull origin master > récupérer info sur le serveur
git remote > lister les dépôt distants
git remote -v > idem mode verbeux
git remote add [alias] [chemin_du_serveur_distant] > ajoute un dépôt distant
git remote rm [alias] > supprimer un dépôt distant
git remote rename [alias] [new alias]   > renomer un dépôt distant
git fetch origin > recupere la branche distante sans fusion avec master
git log master..origin/master > compare diff entre master local et distant (après fetch)
git push [nom-distant] [nom-de-branche] >publier une branche distante
git remote show origin >inspecter un dépôt distant




