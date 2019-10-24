Historique :
Git Log : Par défaut, énumère les commits en ordre chronologique inversé. Mais il peut prendre de nombreux arguments :
git log --oneline > Une version compressée du journal (un commit par lignegit --no-pager log –oneline
git --no-pager log -3 –oneline > Une version compressée du journal et sort de la commande
git log --oneline -2 >consulte les deux derniers commits
git log --author "Antoine07" > consulte les commits d’un auteur en particulier
git log --since=1.day >les commits du dernier jour
git log --before="2019-09-01" > recherché en fonction d’une date
git log calzone.txt >consulter les commit d’un fichier spécifique
git log -p calzone.txt > montre les différences entre chaque commit du fichier
git log -p > montre les modifications
git log -2 -p >montre les modifications des deux derniers commits.
git log f5541d6 b058c4f > montre les logs entre deux commits

Git blame : permet de savoir qui a effectué une modification (utile pour contacter la personne si besoin de plus d’information)
git blame fichier.txt > dans un fichier spécifique

Git diff > affiche les modifications entre le WD et l’index. (utile pour savoir s’il faut indexer ou non le fichier)
git diff --cached > affiche les différence entre le dernier commit et l’index.
git diff HEAD~1 >pour voir les modifications un commit en arrière
git diff HEAD~3 HEAD >pour comparer le HEAD et un état antérieur du dépôt (ici 3 commits en arrière)

Diff stat
git diff --stat >faire des stats sur les différences opérées dans les fichiers.

GIT RESTORE
git restore NomDuFichier > permet d’annuler les modifications dans l’espace de travail.
git restore --staged > à utiliser si le fichier est déjà indexé.

Modifier un message de commit 
Pour modifier un message de commit dans l’historique IL FAUT QUE :
1 . Il n’y ai pas eu d’autres commit entre temps
2. Que le commit n’est pas été publié sur une branche distante (serveur distant)
3 . Utiliser 	git commit -m "nomDuCommit" --amend (si modif du commit)
 Ou 		git commit "un message" --amend --no-edit (permet de changer UNIQUEMENT le nom du commit)

!! Annuler des commits !!
Pour reculer d’un commit dans l’historique, sans perdre son travail :
git reset HEAD~1 > Annule le dernier commit et remet tout dans le WD sans perte
git reset --soft HEAD~1 > Annule le dernier commit et remet tout dans la staging area sans perte

Pour revenir de plusieurs commits en arrière dans l’historique (prudence, faire attention à la cohérence de l’historique):
git reset [commit] >  Le Head->master se déplace jusqu’au [commit], annule les commits entre, sans perte.  Les fichiers et leurs modifications ne sont pas perdus mais replacés dans le WD.

Pour supprimer un commit avec le fichier il faut utiliser git reset --hard , cette commande supprimant les modification il faut l’utiliser avec beaucoup de prudence !!
git reset --hard HEAD~1 > Annule le dernier commit ET supprime les modifications


git checkout : sert (entre autre) à remettre un fichier dans son état original en l’utilisant comme suit :
git checkout [n° commit] nomDuFichier

git revert [n° commit]  > autre manière d’annuler un commit en créant un commit d’annulation. (nécessite donc un message de commit !!)





