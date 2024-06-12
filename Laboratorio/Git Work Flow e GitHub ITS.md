### Creazione del Repo locale
- Accedi a GitHub
- crea nuovo repo
- Apri una shell git e seguire le istruzioni riportate:
```Shell
echo "# Lab2" >> README.md
git init
git add README.md
git commit -m "first commit"
git remote add origin "https://github.com/SerpenTaki/MTSS-1Lab.git"
git push -u origin main
```
- Verificare che nel file system locale e nel repository remoto è presente il file README.md
## Comandi basi
- Verificare lo stato del repository locale
```Shell
git status
//Sul branch main
Your branch is up to date with 'origin/main'

nothing to commit, working tree clean
```
- Verificare i branch locali presenti nel repository
```Shell
git branch
* main
```
- Verificare i branch locali e remoti presenti nel repository
```Shell
git branch -a
* main
	remotes/origin/main
```
- Modificare il file _README.md_ aggiungendo una nuova riga
```Shell
echo "nuova riga" >> README.md
```
- Verificare lo stato del repository locale
```Shell
git status
Sul branch main
Your branch is up to date with 'origin/main'.

Changes not staged for commit:
 (use "git add <file>.." to update what will be committed)
 (use "git checkout -- <file>..." to discard changes in working directory)
	modified: README.md
no changes added to commit (use "git add" and/or "git commit -a")
```
- Visualizzare le differenze apportate al file
```Shell
git diff
diff --git a/README.md b/README.md
index 7936d01..ba0dc76 100644
--- a/README.md
+++ a/README.md
@@ -1 +1,2 @@
+nuova riga
```
- Aggiungere il file nell'area di staging e visualizzare lo stato
```Shell
git add README.md
git status
Sul branch main
Your branch is up to date with 'origin/main'.

Changes to be committed:
 (use "git reset HEAD <file>..." to unstage)

	modified: README.md
```
- Rimuovere il file dall'area di staging senza perdere le modifiche effettuate
```Shell
git restore --staged README.md
```
- Verificare che il file contenga ancora le modifiche
```Shell
cat README.md
```
- Verificare che il file non è più nell'area di staging
```Shell
git status
Sul branch main
Your branch is up to date with 'origin/main'.

Changes not staged for commit:
 (use "git add <file>..." to update what will be committed)
 (use "git checkout -- <file>.." to discard changes in working directory)
	modified: README.md
no changes added to commit (use "git add" and/or "git commit -a")
```
- Rimuovere le modifiche al file (e riportarlo alla versione precedente)
```Shell
git restore README.md
```
- Verificare lo stato del repository
```Shell
git status
```
- Modificare che il commit è stato salvato nel repository locale e siamo avanti rispetto a origin
```shell
fguzzo@UKG06616 LAB2 % git status
On branch main
Your branch is ahead of 'origin/main' by 1 commit.

  (use "git push" to publish your local commits)
nothing to commit, working tree clean

fguzzo@UKG06616 LAB2 % git log
commit 14db40d1296f569efcd7bbe63404e8b3d3e0d5c0 (HEAD -> main)
Author: fguzzo <francesco.guzzo@unipd.it>
Date:   Sun Mar 10 10:17:38 2024 +0100

    aggiunta riga

commit d29eac8cfb17bf85925c079854b71dde78171670 (origin/main)
Author: fguzzo <francesco.guzzo@unipd.it>
Date:   Sun Mar 10 10:04:49 2024 +0100

prima commit
```
- inviamo le modifiche al repository remoto
```shell
git push origin main
```
- verifichiamo lo stato del repository locale
```shell
git status
Sul branch main
Your branch is up to date with 'origin/main'

nothing to commit, working tree clean
```
## Relazioni tra commit e *Issue* in GitHub
##### Aggiungere una nuova attività in GitHub
- Accedere al progetto e cliccare nella tab *issues*
- Creare una nuova *Issue* con i seguenti campi:
	- **Title**: Aggiungere una nuova riga a README.md
	- **Leave a Comment:** Aggiungere la nuova riga "seconda riga" al file README.md
- Cliccare il bottone "*Submit new issue"
- Recuperare l'ID della nuova issue
#### Svolgimento
###### Collegare le attività di sviluppo con le issue
- modificare nuovamente il file
```Shell
echo "terza riga" >> README.md
```
- aggiungere il file all'area di staging
```Shell
git add README.md
```
- effetuare il commit con il messaggio *"#1 aggiunta una nuova riga"*
```shell
git commit -m "#1 aggiunta una nuova riga"
```
- effettuare il push
```shell
git push origin main
```
**TIP**: GitHub permette di associare le modifiche effettuate nel VCS alle *Issue* censiti nel ITS riportando l'ID del workitem nei commit
## Work Flow
### Centralized Workflow
Come descritto in https://www.atlassian.com/git/tutorials/comparing-workflows:

Il Centralized Workflow è un ottimo flusso di lavoro Git per i team che stanno passando da SVN. Come Subversion, il Centralized Workflow utilizza un repository centrale come unico punto di ingresso per tutte le modifiche al progetto. Invece di trunk, il branch di sviluppo predefinito è chiamato main e tutte le modifiche vengono effettuate in questo branch. Questo flusso di lavoro non richiede altri branch oltre a main.