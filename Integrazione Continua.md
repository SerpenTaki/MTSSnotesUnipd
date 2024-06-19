**Continuos Integration _NON E'_ Build Automation**
#### Definizione
Nell'ingegneria del software, la continuous integration è una pratica che si applica in contesti in cui lo sviluppo del software avviene attraverso un sistema di versioning. Consiste **nell'allineamento frequente dagli ambienti di lavoro degli sviluppatori verso l'ambiente condiviso**. Il concetto è stato originariamente proposto nel contesto dell'extreme programming (XP), come contromisura preventiva per il problema dell'integration hell.
Il CI è stato originariamente concepito per essere complementare rispetto ad altre pratiche, in particolare legate al Test Driven Development. In particolare si suppone generalmente che siano stati predisposti **test automatici** che gli sviluppatori **possono eseguire immediatamente** prima di rilasciare i loro contributi verso l’ambiente condiviso, in modo da garantire che le modifiche non introducano errori nel software esistente. Per questo motivo il CI viene applicato in ambienti in cui siano presenti sistemi di **build automatico** e/o esecuzione automatica di test, come Jenkins.
### Motivazioni:
Per **lunghi periodi di tempo**, durante il processo di sviluppo, **il progetto non è in uno stato funzionante** o in uno stato utilizzabile. Sopratutto in progetti dove si sviluppa in un singolo ramo di sviluppo.
Nessuno è interessato a provare ad eseguire l'intera applicazione fino a quando non è finito il processo di sviluppo
In questi progetti spesso viene pianificata la fase di integrazione alla fine del processo di sviluppo. In questa fase gli sviluppatori effettuano attività di merge ed effettuano attività di verifica e validazione
##### Problema (*integration hell*):
La fase di integrazione può richiedere molto tempo e nel caso peggiore, **nessuno ha modo di prevedere quando terminerà** questa fase e di conseguenza quando l'applicazione può essere rilasciata.
#### Definizione
*"Continuous Integration doesn't get rid of bugs, but it does make them dramatically easier to find and remove." (Martin Fowler)*
Consente a un Team di intensificare l'attività di sviluppo e test, **integrando gli sviluppi _(nel VCS)_ il più spesso possibile.**
![[Screenshot 2024-05-07 alle 20.29.11.png]]
### Processo - visione generale
- Al **completamento** di un'attività viene **costruito il prodotto:**
	- Ogni volta che uno sviluppatore invia un commit al VCS viene eseguito il processo di build
- Se il processo di costruzione **fallisce l'attività non continua** fino a che il prodotto non viene riparato
- Se **non è possibile riparare** il prodotto immediatamente (*in pochi minuti*) si **ritorna all'ultima versione funzionante**
- In questo modo si **assicura la presenza di un prodotto consistente** potenzialmente pronto per essere validato e rilasciato
#### Prerequisiti
Per implementare la pratica di CI è necessario che:
1. il codice del progetto venga gestito in un **VCS**
2. Il **processo di build** del progetto sia **automatico**
3. Il processo di build esegua delle **verifiche automatiche** (*test di unità, test di integrazione, analisi statica del codice*)
4. il team di sviluppo adotti correttamente questa pratica
 ![[Screenshot 2024-05-10 alle 13.17.34.png]]
### Processo in dettaglio
1. Controllo se il processo di build è in esecuzione nel sistema di CI. Se è in esecuzione aspetto che finisca, se fallisce lavoro con il team in modo da sistemare il problema.
2. Quando il processo di build ha terminato con successo, aggiorno il codice nel mio workspace con il codice del VCS ed effetuo l'integrazione in locale
3. Eseguo il processo di build in locale in modo da verificare che tutto funzioni correttamente
4. Se il processo di build termina con successo invio le modifiche al VCS
5. Attendo che il sistema di CI esegua il processo di build con i miei cambiamenti
6. Se il processo di build fallisce mi fermo con le attività di sviluppo e lavoro per sistemare il problema in locale e riprendo dal passo 3.
7. Se il processo di build termina con successo passo allo sviluppo dell'attività successiva
![[Screenshot 2024-05-10 alle 13.22.10.png]]
### Integrare frequentemente gli sviluppi
*più di una volta al giorno*
in questo modo:
- Le modifiche da integrare saranno poche e più facili da gestire
- Se viene segnalato un errore dall'esecuzione del processo di build sarà più semplice identificare il codice che ha introdotto l'errore (*che sarà presente nei commit che hanno fatto scatenare il processo di build*)
Per poter integrare frequentemente gli sviluppi è richiesto che il progetto venga scomposto in tante attività brevi ("DIVIDE ET IMPERA")
#### Creare una "*Automated Test Suite*"
Se non vengono eseguiti dei test automatici per verificare e validare il progetto, il processo di build può solo verificare se il codice integrato compila correttamente.
I test che possono essere eseguiti nel processo di CI sono:
- i test di unità
- I test di integrazione di subsystem interni (no esterni)
- Analisi statica del codice
**Devono avere le caratteristiche del modello CRISP**
#### Avere un processo di Build and Test breve
Nella CI il processo di Build è lento:
- Gli sviluppatori smetteranno di eseguire il processo di build e i test prima di inviare le modifiche al VCS -> inizieranno a generare più build in errore
- Il processo di integrazione continua richiederà così tanto tempo che si verificheranno più commit nel momento in cui è possibile eseguire nuovamente la build -> sarà più difficile identificare cosa ha fatto fallire la build
- Si disincentiva l'invio frequente delle modifiche al VCS
#### Gestire il nostro ambiente di sviluppo (*Workspace*)
Ogni sviluppatore deve essere in grado di:
- Eseguire localmente il processo di build e test e deploy -> per questo nel VCS devono essere gestiti:
	- codice di produzione
	- codice di test
	- Script richiesti per configurare l'ambiente dove eseguire il progetto
- **Always be prepared to revert to the previous revision:** Scaricare le modifiche dal VCS e essere in grado di ripristinare il progetto ad uno stato consistente
- **Never Go Home on a Broken Build:** Verificare l'esito della compilazione nel CI server -> Se il processo di CI fallisce o lo sviluppatore deve essere in grado o di risolvere il problema o di ripristinare la versione del VCS all'ultimo stato consistente
### Fix una build in errore subito
**"_nobody has a higher priority task than fixing the build_"** "*Kent Beck*"
Il tempo per ripristinare lo stato del progetto deve essere limitato. Se non è possibile correggere l'errore che ha fatto fallire la build velocemente, ripristinare lo stato del VCS all'ultima versione funzionante.
Non è ammesso correggere il problema commentano le verifiche cha hanno fatto fallire la build
#### Tutti possono vedere cosa succede
Lo stato della build deve essere pubblicato in un servizio visibile a tutto il team del progetto. Ogni componente del team deve essere in grado di capire lo stato del progetto e capire qual è l'ultima versione in cui è stato eseguito il processo di build con successo.
- Identificare chi ha introdotto l'errore
- Avere a disposizione un log per identificare quale parte del processo di build è fallita
- Avere a disposizione la lista dei commit che hanno introdotto l'errore
Il sistema di continuous integration deve poter avvisare i componenti del team ad ogni cambio di stato del processo. (*da successo a fallimento, da fallimento a successo*)
![[Screenshot 2024-05-10 alle 14.54.35.png]]
#### Principali caratteristiche di Jenkins
- **Build Automation:** può automatizzare la costruzione del software attraverso script, facilitando la creazione di build consistenti e ripetibili
- **Trigger Automatici:** può essere configurato per avviare automaticamente una build in base a eventi come il commit di codice su un repository, modifiche a determinati file, o in un momento prestabilito
- **Test Automation:** Jenkins può eseguire automaticamente test unitari, test di integrazione e altri test ogni volta che viene eseguita una build, aiutando a identificare i problemi rapidamente
- **Integrazione con VCS:** si integra con vari sistemi di controllo del codice sorgente, permettendo di monitorare e utilizzare le modifiche al codice per innescare build
- **Notifiche e Reportistica:** può inviare notifiche per informare il team dei risultati delle build e generare report dettagliati sulle esecuzioni e sui test
- **Configurazione semplice delle Pipeline:** Utilizzando Jenkinsfile, le pipeline CI possono essere configurate e versionate insieme al codice sorgente, consentendo un approcio "*Infrastructure as Code*"
- **Integrazione con Altri Strumenti di Automazione:** Jenkins si integra con strumenti come Docker, Kubernetes, Ansible, Terraform, consentendo build Automatizzati in ambienti containerizzati o distribuiti.
- **Cronologia delle Build:** tiene traccia della cronologia delle build, fornendo un registro dettagliato di ogni esecuzioni, compresi i log di output e i risultati dei test.
- **Scalabilità e Flessibilità :** può essere scalato orizzontalmente con più nodi di build, e le pipeline possono essere personalizzate in base a esigenze specifiche, fornendo grande flessibilità 
- **Sicurezza e Permessi:** Jenkins permette di configurare ruoli e permessi specifici per utenti e gruppi assicurando che solo gli utenti autorizzati possano avviare, modificare o visualizzare le buid.
### Pipeline
**Una pipeline in Jenkins è una serie di fasi o passaggi** che rappresentano il processo di continuous integration (CI) e continuous delivery (CD) per un progetto software. È uno strumento potente e flessibile che consente di automatizzare il flusso di lavoro di sviluppo, test e distribuzione del software.
- **Concetto di Pipeline:**
	- Una pipeline è un insieme di fasi (*stages*) che descrivono le attività necessarie per costruire, testare, e distribuire il software. Le pipeline in Jenkins sono definite utilizzando un linguaggio di script, spesso scritto in formato "as code" con un file chiamato "Jenkinsfile"
- **Fasi (_Stages_) e Passaggi (_Steps_)
	- Le pipeline consistono in diverse fasi, ognuna delle quali può contenere uno o più passaggi. Ad esempio, una fase potrebbe essere "Build" e potrebbe contenere passaggi per compilare il codice e generare un eseguibile. Un'altra fase potrebbe essere "Test", con passaggi per eseguire test unitari e di integrazione.
- **Pipeline Scriptate e Dichiarative:**
	- Pipeline **scriptate** (*Scripted Pipelines*): Scritte in Groovy, offrono una grande flessibilità e possono essere utilizzate per pipeline complesse e dinamiche.
	- Pipeline **dichiarative** (_Declarative Pipelines_): Forniscono una sintassi più strutturata, ideale per pipeline più semplici e per chi preferisce un approccio più dichiarativo.
## GitHub Action caratteristiche principali
*GitHub Action è una funzionalità di GitHub che consente di automatizzare i flussi di lavoro per la C.I. e C.D.*:
- **Integrazione nativa con GitHub:** è progettato per funzionare all'interno di GitHub, consentendo automazioni basate su eventi GitHub come commit, pull request e rilasci.
- **Definizione tramite file YAML:** Le azioni sono configurate utilizzando file YAML all'interno del repository GitHub. Questi file definiscono le pipeline e i passaggi da eseguire.
- **Azioni personalizzate e da terzi:** È possibile creare azioni personalizzate o utilizzare una vasta gamma di azioni predefinite da GitHub o da terzi rendendo semplice l'integrazione con altri strumenti
- **Integrazioni con piattaforme cloud e strumenti DevOps:** può integrarsi con servizi cloud e strumenti DevOps
- **Supporto per Esecuzione Parallela e Matrici:** consente di eseguire attività in parallelo e di definire "matrici" per eseguire build e test in diverse configurazioni.
- **Integrazione con Notifiche e Servizi Esterni:** Offre integrazioni con servizi di notifica e può eseguire chiamate API a servizi esterni
![[Screenshot 2024-05-10 alle 17.08.59.png]]

$\rightarrow$ vai a [[Feedback Loop]]