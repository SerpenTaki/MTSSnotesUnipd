# Definizione
“Un componente della *gestione della configurazione del software*, il *controllo versione*, noto anche come controllo delle revisioni o controllo del codice sorgente, è la **gestione delle modifiche a documenti**, programmi per computer, grandi siti web e altre raccolte di informazioni.
Le modifiche sono solitamente **identificate da un numero o un codice letterale**, chiamato "numero di revisione", "livello di revisione" o semplicemente "revisione". Ad esempio, un insieme iniziale di file è "revisione 1". Quando viene apportata la prima modifica, l'insieme risultante è "revisione 2", e così via. Ogni revisione è associata a un timestamp e alla persona che ha effettuato la modifica. Le revisioni possono essere confrontate, ripristinate e, con alcuni tipi di file, unite.”

### Cosa sono gli SCM
- Sono sistemi software
- Registrano tutte le modifiche avvenute ad un insieme di file
- Permettono la condivisione di file e modifiche
- Offrono funzionalità di merging e tracciamento delle modifiche
### Perché usarlo?
Un VCS permette di:
- **Collaborare** in modo efficiente nel codice di un prodotto
- **Individuare** facilmente e risolvere i **conflitti**
- Facilitare la **Condivisione** di commenti e documentazione
- Tracciare ogni modifica (*storia del prodotto*):
	- Fornire una **storia completa** delle modifiche avvenute nel prodotto
- Facilitare il **ripristino** dei file a una **versione precedente**
### Benefici
- Mantengono la **storia completa** di ogni cambiamento avvenuto per ogni file (*autore, data, motivazione*)
- **Lavorare senza interferenze** in differenti rami di sviluppo (**_Branching_**). Le modifiche effettuate in un ramo di sviluppo possono poi confluire nel ramo principale
- **Tracciabilità**: tutte le modifiche possono far riferimento alle attività registrate nell'[[Issue Tracking System]]. In  ogni istante è possibile capire che attività sono state effettuate in una specifica versione.
## Differenti tipi di VCS
I **VCS** possono essere classificati in 3 tipologie:
- Locali
- Centralizzati
- Distribuiti
#### Local VCS
*Molte persone gestiscono le diverse versioni copiando i file in un'altra directory (magari denominata con la data). Questo approccio è comune perché molto semplice ma soggetto ad errori. è facile dimenticare in quale directory sei e modificare il file sbagliato o copiare dei file che non volevi copiare*
- **I tool più vecchi**
- Registrano **solo** la storia dei cambiamenti
	- Utilizzano un "Version Database" dove viene registrata la storia di tutti i file
	- Salva sul disco una serie di *patch* (_differenze tra file_) tra una versione e l'altra
	- è possibile ricreare lo stato di qualsiasi file in qualsiasi momento
- **Non gestiscono la condivisione**
#### Centralized VCS (CVCS)
- Meno vecchi e **molto diffusi**
- Gestiscono sia la **condivisione** che il tracciamento della storia:
	- La storia è gestita come nel **Local VCS**
	- Il "*Version Database*" è gestito in un **server centrale (_singolo punto di rottura_)**
- Ogni sviluppatore è un client che ha nel suo spazio di lavoro **solo una versione** del codice
- Facili da apprendere
#### Distributed VCS (DVCS)
- Simili ai CVCS ma il "Version Database" **è distribuito per duplicazione in ogni nodo**
	- Quando il **nodo centrale non è disponibile, è possibile continuare a lavorare** e registrare i cambiamenti
	- Hanno una **migliore risoluzione dei conflitti** che favorisca la collaborazione
	- Permette di impostare **diversi tipi di flussi di lavoro** che non sono possibili in sistemi centralizzati
- **L'apprendimento** è più **complesso** rispetto ai CVCS

| Caratteristica                | VCS                                                  | CVCS                                                                  | DVCS                                                            |
| ----------------------------- | ---------------------------------------------------- | --------------------------------------------------------------------- | --------------------------------------------------------------- |
| Definizione                   | Sistema per tracciare le modifiche ai file nel tempo | Sistema di controllo di versione con un singolo repository centrale   | Sistema di controllo di versione con più repository distribuiti |
| Esempi                        | SCCS, RCS                                            | CVS, Subversion (SVN)                                                 | [[Git]], Mercurial, Bazaar                                      |
| Struttura dei Repository      | Singolo repository                                   | Repository centrale                                                   | Repository locale e centrale                                    |
| Accesso ai Dati               | Dati accessibili localmente                          | Accesso centralizzato ai dati                                         | Ogni copia ha l'intero repository                               |
| Conflitti di Merge            | Gestione manuale dei conflitti                       | I conflitti si risolvono al momento del commit al repository centrale | I conflitti si risolvono durante i merge locali                 |
| Lavoro Offline                | Limitato o non supportato                            | Necessita di connessione al repository centrale                       | Supportato, operazioni locali complete                          |
| Prestazioni                   | Dipende dal tipo di VCS                              | Spesso più lento a causa del singolo punto centrale                   | Più veloce, operazioni locali                                   |
| Sicurezza dei Dati            | Varia a seconda del sistema                          | Punto di vulnerabilità singolo nel repository centrale                | Maggiore sicurezza, backup distribuiti                          |
| Scalabilità                   | Limitata                                             | Limitata dal server centrale                                          | Alta, grazie ai repository distribuiti                          |
| Complessità di Configurazione | Dipende dal tipo di VCS                              | Moderata                                                              | Più alta, richiede gestione di più repository                   |
| Collaborazione                | Limitata                                             | Collaborazione centralizzata                                          | Collaborazione facilitata, flussi di lavoro flessibili          |
| Storia delle Revisioni        | Gestita localmente                                   | Storia centralizzata                                                  | Ogni copia mantiene la storia completa                          |
| Esempi di Utilizzo            | Piccoli progetti, file singoli                       | Progetti di medie dimensioni, team centralizzati                      | Progetti di grandi dimensioni, team distribuiti                 |

### Cloud-based DVCS
Esistono "VCS as a Service"
Il "Version Database" è gestito in un servizio Cloud
**Vantaggi**
- **Si delega la gestione** (e l'installazione) ad un servizio esterno
- Forniscono altri servizi oltre al VCS come text editor online, strumenti visuali, IST
**Svantaggi**
- Il codice sorgente non è nel nostro PC o nell'infrastruttura aziendale
Esempi: GitHub, Bitbucket by Atlassian, Amazon CodeCommit, Visual Studio Online by Microsoft, SourceForge, GitLab, etc.
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
	- **GitFlow workflow** è leggero, branch-based per progetti
		- GITHUB model
		- GITLAB model
- **FORKING workflow** è l'ideale per i progetti open-source
#### Centralized
- Questo pattern è l'uso naturale di un CVCS come *SVN* o *CVS*
- È facile da capire e usare, ed è sufficiente in molti casi
- La collaborazione è bloccata quando il server centralizzato è inattivo o la cronologia è danneggiata

#### Feature Branch
- Obiettivi di questo pattern: l'uso di **un solo** branch **per feature (DVCS)**
	- L'incapsulamento consente di lavorare senza modificare la main codebase
	- Consente una collaborazione più semplice 
	- I conflitti di merge mappano i conflitti concettuali: *più facili da tracciare*
##### GitFlow Model
- Dedica il (*main*) **master branch** al codice che dev'essere rilasciato
- Usa un **develop branch** come "*snapshot*" corrente di cosa verrà incluso nella prossima release
- Crea *feature branches* da develop per ogni nuova funzionalità, che sono soggette a merge di nuovo in develop una volta pronte
- Quando si è pronti per il rilascio, si effettua il merge su *master* e si assegna un tag con una versione di rilascio
- Implementazione rigorosa dei branch: *ruoli* per *branch specifici*

##### GitLab Flow
Con GitLab Flow, tutte le funzionalità e le correzioni vanno al **MASTER**, prima di passare in *Pre-Production* e *Production*
###### GitHub vs GitLab
**GitHub**
- Sostiene un approccio di sviluppo veloce e focalizzato sulle caratteristiche per unire i nuovi rami con il ramo master.
- Questo flusso di lavoro è perfetto per piccoli team e progetti Agile.
- Il ramo master è sempre pronto per il deploy cosa che ci assicura di poter ripristinare rapidamente lo status quo se qualcosa va storto. Si può tornare alla versione precedente in pochi secondi
**GitLab**
- Sostiene un approccio di sviluppo più attento all'affidabilità
- Nel flusso di lavoro di GitLab, si creano più rami stabili oltre al master, di solito almeno produzione e pre-produzione. Questo significa un processo di test a più fasi in cui una singola revisione del codice sulla richiesta di merge non è sufficiente.
- Es. Se avete un team dedicato al QA, è un modo per permettere al vostro team di Ricerca e Sviluppo di lavorare liberamente su nuove funzionalità senza preoccuparsi di testare ogni singolo minuto di cambiamento del codice.
#### FORK
- Pattern ereditato da Github/Bitbucket
- Spinge sul concetto di file system distribuiti
- Ogni utente esegue il *fork* della repository principale e può proporre **pull request** *tra più repository*
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
- Esistono 2 tipi di VCS: *Centralized and Distributed VCS*
- In base alle esigenze e alla conoscenza del team, si può scegliere il workflow pattern più adatto tra: [[#Centralized]], [[#Feature Branch]], [[#GitFlow Model]], [[#FORK]]
- Per la scelta del servizio da utilizzare (on premisis o cloud) bisogna tenere in considerazione i seguenti fattori:
	- Backup
	- Crash
	- privacy
	- Esigenze del progetto
	- Dimensioni del Team


$\rightarrow$ Passa a [[GIT]]