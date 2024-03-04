- Sono sistemi software
- Registrano tutte le modifiche avvenute ad un insieme di file
- Permettono la condivisione di file e modifiche
- Offrono funzionalità di merging e tracciamento delle modifiche
### Perchè usarlo?
Un VCS permette di:
- **Collaborare** in modo efficiente nel codice di un prodotto
- **Individuare** facilmente e risolvere i **conflitti**
- Facilita la **Condivisione** di commenti e documentazione
- Tracciare ogni modifica (*storia del prodotto*):
	- Fornire una **storia completa** delle modifiche avvenute nel prodotto
- Facilita il **ripristino** dei file a una **versione precedente**
### Benefici
- Mantengono la **storia completa** di ogni cambiamento avvenuto per ogni file (*autore, data, motivazione*)
- **Lavorare senza interferenze** in differenti rami di sviluppo (**_Branching_**). Le modifiche effettuate in un ramo di sviluppo possono poi confluire nel ramo principale
- **Tracciabilità**: tutte le modifiche possono far riferimento alle attività registrate nell' [[Issue Tracking System]]. In  ogni istante è possibile capire che attività sono state effettuate in una specifica versione.
## Differenti tipi di VCS
I **VCS** possono essere classificati in 3 tipologie:
- locali
- Centralizzati
- Distribuiti
#### Local VCS
*Molte persone gestiscono le diverse versioni copiando i file in un'altra directory (magari denominata con la data). Questo approccio è comune perchè molto semplice ma soggetto ad errori. è facile dimenticare in quale directory sei e modificare il file sbagliato o copiare dei file che non volevi copiare*
- **I tool più vecchi**
- Registrano **solo** la storia dei cambiamenti
	- Utilizzano un "Version DataBase" dove viene registrata la storia di tutti i file
	- Salva sul disco una serie di *patch* (_differenze tra file_) tra una versione e l'altra
	- è possibile ricreare lo stato di qualsiasi file in qualsiasi momento
- **Non gestiscono la condivisione**
#### Centralized VCS (CVCS)
- Meno vecchi e **molto diffusi**
- Gestiscono sia la **condivisione** che il tracciamento della storia:
	- La storia è gestita come nel **Local VCS**
	- Il "*version database*" è gestito in un **server centrale (_singolo punto di rottura_)**
- Ogni sviluppatore è un client che ha nel suo spazio di lavoro **solo una versione** del codice
- Facili da apprendere
#### Distributed VCS (DVCS)
- Simili ai CVCS ma il "version Database" **è distribuito per duplicazione in ogni nodo**
	- Quando il **nodo centrale non è disponibile, è possibile continuare a lavorare** e registrare i cambiamenti
	- Hanno una **migliore risoluzione dei conflitti** che favorisca la collaborazione
	- Permette di impostare **diversi tipi di flussi di lavoro** che non sono possibili in sistemi centralizzati
- **L'apprendimenti** è più **complesso** rispetto ai CVCS
### Cloud-based DVCS
Esistono "VCS as a Service"
Il "Version Database" è gestito in un servizio Cloud
**Vantaggi**
- **Si delega la gestione** (e l'installazione) ad un servizio esterno
- Forniscono altri servizi oltre al VCS come text editor online, strumenti visuali, IST
**Svantaggi**
- Il codice sorgente non è nel nostro PC o nell'infrastruttura aziendale
# Terminologia
- Ogni cambiamento di linea su un **singolo** file è chiamato **DIFF**
- Un insieme di **diffs** validi sono considerati un **COMMIT**
	- Un **Commit** è una nuova versione del codice sorgente
	- Un **Commit** esiste sia localmente che da remoto
	- Il **Commit** più recente ovvero l'ultimo è la **head** della storia
- Un **Branch** è un puntatore ad un singolo commit
	- Per integrare un branch devi fare una procedura di **merge**
- Un **pull-request** è un modo di guidare un branch verso il merge
- Un branch può essere pushato al server centrale senza fare il merge
	- In sostanza *chiede* se può essere pushato alla repo centrale
- Un branch termina venendo chiuso oppure venendo mergiato alla repo originaria
# Workflow Patterns
I Workflow che usiamo per gestire i cambiamenti nello sviluppo del codice dipendono dal VCS in uso:
- **Centralized workflow** semplice e facile da adottare
- **Feature Branch workflow** utile per isolare codice e concentrarsi sulle features
	- **GitFLOW workflow** è branchbased for projects
		- GITHUB model
		- GITLAB model
- **FORKING workflow** is ideal for opensource projects
#### Centralized
- Questo pattern is the natural usage of a CVCS like *SVN* or CVS
- It easy to understand and use, and sufficient enough for a lot of cases
- Collaboration is blocked when centralized server is down or history is broken
#### Feature Brach
- Goal of this pattern: using **one** branch **per feature (DVCS)**
	- Encapsulation allows working without disturbing the main codebase
	- Allows easier collaboration
	- Merge conflicts maps the conceptual conflicts: *easier to track*
##### GITFLOW MODEL
- Keep your (*main*) **master branch** as the code that has been released
- Use a **develop branch** as the current "*snapshot*" of what will go into the next release
- Spawn off *feature branches* off develop for every new feature, which are merged back into it when they're ready
- When you are ready to release, you merge to *master* and tag with a release version
- Strict branching implementation: *roles* for *specific branches*
##### GITLAB FLOW
Con GitLab Flow, tutte le funzionalità e le correzioni vanno al **MASTER**, prima di passare in *Pre-Production* e *Production*
###### GitHub vs GitLab
**GITHUB**
- Sostiene un approccio di sviluppo veloce e focalizzato sulle caratteristiche per unire i nuovi rami con il ramo master.
- Questo flusso di lavoro è perfetto per piccoli team e progetti Agile.
- Il ramo master è sempre pronto per il deploy cosa che ci assicura di poter ripristinare rapidamente lo status quo se qualcosa va storto. Si può tornare alla versione precedente in pochi secondi
**GITLAB**
- Sostiene un approccio di sviluppo più attento all'affidabilità
- Nel flusso di lavoro di GitLab, si creano più rami stabili oltre al master, di solito almeno produzione a pre-produzione. Questo significa un processo di test a più fasi in cui una singola revisione del codice sulla richiesta di merge non è sufficiente.
- Es. Se avete un team dedicato al QA, è un modo per permettere al vostro team di Ricerca e Sviluppo di lavorare liberamente su nuove funzionalità senza preoccuparsi di testare ogni singolo minuto di cambiamento del codice.
#### FORK
- Pattern ereditato fa Github/Bitbucket
- Spinge sul concetto di file system distribuiti
- Ogni utente *forks* la repo principale e può proporre *pullare richeste tra più repo*
- Authorization management improved
- Autonomia per un migliore processo di collaborazione
- Decentralizzato per il nuovi pattern ("*promiscuous integration*")
## CVCS vs DVCS

| CVCS                                                                                      | DVCS                                                                                                       |
| ----------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------- |
| (+) apprendimento più semplice                                                            | (+) Più recenti *de facto*                                                                                 |
| (+) Permettono il lock dei file                                                           | (+) Architettura distribuita per replica. Meno chance di perdere tutta la storia                           |
| (-) Meno recenti                                                                          | (+) è possibile adottare più tipi di *Workflow*                                                            |
| (-) Si può utilizzare solo il Centralized *Workflow*                                      | (+) Le operazioni di commit sono più veloci perchè avvengono in locale e possono avvenire anche *off-line* |
| (-) Le operazioni di commit sono più lente. Non possono essere fatte offline              | (-) Non permettono il lock dei file                                                                        |
| (-) *Single point of failure*. Se si corrompe il server centrale si perde tutta la storia | (-) L'apprendimento è più difficile                                                                        |

###### Riassuntino:
- Il codice sorgente di un progetto deve essere versionato in un VCS, che è un sistema software che tiene traccia di tutti i cambiamenti e facilità la condivisione
- Esistono 2 tipi di VCS: *Centralized and DIstributed VCS*
- In base alle esigenze e alla conoscenza del team, si può scegliere il workflow pattern più adatto tra: *centralized, Feature Branch, Gitflow, Fork*
- Per la scelta del servizio da utilizzare (on premisis o cloud) bisogna tenere in considerazione i seguenti fattori:
	- Backup
	- Crash
	- privacy
	- Esigenze del progetto
	- Dimensioni del Team
