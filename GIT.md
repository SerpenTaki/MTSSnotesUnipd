È un **software di controllo versione distribuito** utilizzabile da interfaccia a riga di comando, creato da **Linus Torvalds** nel **2005**.
La sua progettazione si ispirò a strumenti come BitKeeper e Monotone.
Git è nato per essere un semplice strumento per facilitare lo **sviluppo del** ==kernel Linux== ed è diventato uno degli strumenti di controllo versione più diffusi.
### Caratteristiche
- **Branching and Merging**:
	- È incentivato lo sviluppo su Branch diversi
- **Piccolo e veloce**
	- La maggior parte delle operazioni viene fatta in locale
	- È sviluppato in C. La velocità e la performance sono stati i requisiti primari
- **Distribuito (per "_clone_" del repository):
	- Backups multipli
	- Possibilità di adottare diversi Workflow
- **Integrità**
	- Ogni commit è identificato da un ID (_checksum **SHA-1** di **40 caratteri** basato sul contenuto di file o della struttura della directory_) che ne garantisce l'integrità
	- Non è possibile cambiare un commit senza modificare l'ID del commit stesso e dei commit successivi
- **Staging Area**:
	- È stata aggiunta un'area di staging dove vengono validati i file modificati che potranno essere versionati con un commit. È utile se sono state effettuate svariate modifiche riguardanti aspetti differenti del progetto, in questo modo si mantiene il repository più ordinato.
- **Free and Open Source**
	- È rilasciato con licenza *GNU General Public License version 2.0*
	- Il codice sorgente è pubblico

"... Git thinks of its data more like a **set of snapshots** of a miniature filesystem. Every time you *commit*, or **save the state of your project** in Git, it basically **takes a picture of what all your files look like at that moment** and stores a reference to that snapshot.
To be efficient, *if files have not changed*, Git doesn’t store the file again, just *a link to the previous identical file it has already stored.* Git thinks about its data more like a stream of snapshots.”
### Aree locali
In GIT i file della copia locale possono essere:
- Nella **Working directory**, *checked out*, modificati ma non ancora validati (Modified)
- Nella **Staging Area**, validati ma non ancora committati. Il commit salva uno snapshot di tutti i file presenti nella staging area (*Staged*)
- Nel **Repository locale** (*Committed*)
### Stato di un file in Git
Un file in GIT può essere in uno dei seguenti stati:
- **Untracked**: File non ancora versionato
- **Unmodified**: File non modificato rispetto alla versione precedente
- **Modifed**: Modificato nella working directory
- **Staged**: salvata una snapshot nella Staging Area
- **Commited**: presso dalla Staging Area e salvato nel repository locale
## Installazione di Git
https://git-scm.com/book/en/v2/Getting-Started-Installing-Git
## Configurazione di Git
È richiesta una configurazione iniziale dove vengono impostati username e l'email  da usare per ogni commit:
````Bash
git config --global user.name "Bugs Bunny"
git config --global user.email bugs@gmail.com
````
È possibile invocare il seguente comando per avere la lista di tutte le configurazioni
````Shell
git config --list
````
Le configurazioni possono essere fatte a vari livelli:
- **System**: per l'intero sistema per tutti gli utenti
- **Global**: per il singolo utente
- **Local** (_di default_): per singolo repository
https://git-scm.com/docs/git-config

### Creazione del repository
2 scenari:
1. **Creazione del repository locale nella cartella corrente**:
	- `git init`
	- Crea una cartella `.git` nella cartella corrente
	- Da questo momento è possibile iniziare il versionamento del file localmente
2. **Clonazione di un repository remoto nella cartella corrente**:
	- `git clone url localDirectoryName`
	- Clona il contenuto del repository remoto nella cartella corrente
	- Crea una cartella `.git` che rappresenta il repository locale
![[Pasted image 20240311113244.png]]
### Add a Commit
**Aggiungere** i file nella staging area e creazione di una Snapshot
 `git add filename`
**Commit** e salvataggio di una nuova versione nel repository locale
 `git commit -m "Fixing bug #22"`
**Rimuovere** un file dalla staging area senza perdere le modifiche
 `git restore --staged filename`
**Rimuovere** le modifiche ad un file nella working area
 `git restore filename`
### Stato e ripristino delle modifiche
- Vedere lo _stato_ dei file workspace o nella staging area:
````Bash
git status
git status -s //(Short version)
````
- Per vedere cos'è stato *modificato ma non è ancora nella staging area:*
`git diff`
- Per vedere cos'è stato *modificato ed è nella staging area:*
`git diff --cached`
- Per vedere cos'è stato *modificato rispetto al local repository (HEAD)*
`git diff HEAD`
- Per vedere la **lista dei cambiamenti** (*commit*) nel repository locale:
`git log`
### Branch e Merging
Per **creare un nuovo branch**
`git branch name`
Per avere la **lista dei branch locali**:
`git branch`
Per **passare in un branch**
`git checkout branchname`
Per **effettuare attività di merge di un branch** nel master
````shell
git checkout master/main
git merge branchname
````
### Repository remoto
lista dei repository remoti
````bash
git remote
git remote -v
````
**Fetch**: recupero i nuovi branch e le modifiche dal remoto senza aggiornare la working copy (senza fare merge):
`git fetch origin`
**Pull**: recupero le ultime modifiche dal repository remoto e aggiorno la working copy (fetch and merge):
`git pull origin master`
**Push**: Per inviare le modifiche al repository remoto:
`git push origin master`

-----------------------------
La lista dei comandi base può essere recuperata da:
- https://education.github.com/git-cheat-sheet-education.pdf
- https://git-scm.com/docs/giteveryday
- https://git-scm.com/docs/user-manual.html

Sono presenti dei tutorial per provare i comandi di GIT:
- https://git-scm.com/book/it/v2
- https://git-scm.com/docs/gittutorial

Gioco per imparare ad utilizzare git:
- https://github.com/git-learning-game/oh-my-g

$\rightarrow$ vai a [[Scrum]]