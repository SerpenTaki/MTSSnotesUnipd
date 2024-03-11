**_Issue_**: Criticità: attività/evento da gestire
**_Tracking_**: registrare, lasciare delle tracce
## Cos'è un ITS
- è un **Pacchetto di SoftWare** che gestisce i problemi di gestione delle issue e le organizza.
- Sono generalmente usati in contesti collaborativi, e sono usati per risolvere i problemi segnalati da clienti/dipendenti.
- Un ITS è simile ad un **bugtracker** e spesso le aziende software vendono entrambi, alcuni bugtracker vengono usati anche come ITS e viceversa.
- L'uso di un ITS o bugtracker sono considerati un segno distintivo di _un buon team di sviluppo software_
### ITS per la gestione del progetto
**Strumento** che facilità la **gestione del processo di sviluppo** e di **_change management_** attraverso la *gestione di attività diverse* (**Work Item** _unità di misura atomica del lavoro_) come: analisi requisiti, sviluppo, test, bug, release, deploy, change request...

**4 fasi**
--
1) Pianifica
2) Programma
3) Controlla
4) Ricerca

Ogni singola "**attività minima**" (Work Item) del progetto è gestita mediante un **workflow** e mantenuta all'interno di un'unica piattaforma e di un unico **_repository_**
![[Pasted image 20240227141521.png]]
# A cosa serve?
- **Condividere** le informazioni con il **team di sviluppo**,  **Project Manager** e il **cliente (SAL)**:
	- Unico repo dove trovare le informazioni
	- Sistema di notifica
	- Dashboard
- Implementare un **processo** per **misurare la qualità** del progetto
- Avere un **istantanea** dello stato del progetto:
	- attività da fare
	- in corso d'opera
	- completate
- Decidere **quando** rilasciare e **cosa rilasciare**
	- I *Work item* possono essere assegnati ad una versione
- **Assegnare** e dare una **priorità** alle attività
- Consultare il **tempo** impiegato (memoria storica per stime future)
- Avere una chiara assegnazione delle attività (**responsabilità**)
	- Ogni *Work item* riporta **l'assegnatario** e il **segnalante**
- **Memoria storica** di tutti i cambiamenti del progetto
## Caratteristiche di un Work Item
- **Progetto**: progetto a cui si riferisce
- **Codice**: identificativo univoco
- **Riepilogo**: descrizione breve dell'attività
- **Descrizione**: descrizione esaustiva dell'attività
- **Tipo**: Categoria del Work item p.es: "Task", "Epic", "Bug", "Requisito", "Test execution". Ne determina **i campi, gli stati, le schermate** e il **workflow** (*ciclo di via*)
- **Stato**: lo stato all'interno del workflow in cui si trova il *work item*
- **Priorità**: Importanza del *work item* in relazione con gli altri *work item* del progetto
- **Stato di Risoluzione**: identifica lo stato di risoluzione del *work item*
- **Versione di riferimento:** Versione del progetto in cui è richiesta l'attività
- **Componente**: Componente del progetto a cui si riferisce il *Work item*
- **Etichette:** Permettono di collegare tra loro i *Work item*
- **Collegamenti:** Permettono di collegare tra di loro i *Work item*
- **Assegnatario:** Identifica chi è il responsabile per svolgere l'attività
- **Segnalante:** Identifica chi ha segnalato l'attività
- **Data di creazione**
- **Data di ultimo aggiornamento**
- **Data di risoluzione**
- **Stima originaria:** Stima per lo svolgimento dell'attività
- **Stima a finire:** Stima presunta per terminare l'attività
- **Tempo speso**
- **Allegati**
### Il Workflow
**Il _Workflow_** è un insieme di **Stati** e **transizioni** che un *Work item* attraversa durante il suo ciclo di vita. In genere premette di implementare **il processo da seguire** per completare l'attività.
- Viene associato ad un **Progetto** e può essere associato ad uno o più **Tipi**
- Permette di registrare tutte le transizioni e cambi di stato.
### Collegamenti
Permettono di definire **relazione** tra i *Work item* anche di differenti tipi. I collegamenti sono bidirezionali (dal/al *Work Item*).
Vengono registrate e possono essere utilizzate come criterio di ricerca. Questo permette di **verificare la presenza o meno di relazione tra i _Work Item_** (p.es. **Il requisito è coperto da casi di test**)
### Funzionalità di un ITS
1. **Gestione**
	- Ricerca avanzata dei *Work item*
	- Salvataggio di ricerche
	- Esportazione
	- Reporting
2. **Integrazione**
	- Integrazione con il Source code management
	- Integrazione con l'ambiente di sviluppo
3. **Condivisione**
	- Notifiche
	- Bacheche o Board
	- Dashboard
	- Definizione di Road map e Release Notes
##### Filtri:
- Permettono di **ricercare** i *Work item* in base ai campi
- Possono essere **salvati** per facilitare le ricerche più frequenti
- I risultati dei filtri possono essere **esportati**
- I filtri sono **la base per creare report, board e dashboard**
##### Board:
- Permette di visualizzare i *Work Item* di uno o più progetti, offrendo un modo flessibile e interattivo di visualizzazione, gestione e visualizzare dei dati di sintesi sulle attività in corso.
- è configurata e visualizza i work item ricercati con un filtro
- Permette di interagire velocemente con i *Work Items*
###### Scrum Sprint:
- metodo di lavoro che consiste nel trovare task fattibili in un tot di tempo, imporsi una scadenza e completarle nel tempo limite, ovviamente ci si concentra solo su una parte del codice senza andare a fare le altre
##### Board o bacheche:
- Permette di visualizzare i work item di uno o più progetti, offrendo un modo flessibile e interattivo di visualizzazione, gestione e visualizzare dei dati di sintesi sulle attività in corso.
- è configurata e visualizza i work item ricercati con un filtro.
- Permette di interagire velocemente con i work items (p.es, Avanzare di stato, modificare alcuni campi)
##### Report:
- ==Hanno lo scopo di monitorare e avere una visione d'insieme del progetto==
## Configurazione e utilizzo di un ITS
1. Identificare i **Processi** richiesti per la gestione del progetto:
	- Procedure e best practices definiti dai framework di qualità presenti in azienda o richiesti dal Cliente (*es. ISO 9001...*)
	- Vincoli imposti dal cliente (*SLA, info richieste da contratto*,...)
	- Modalità di gestione del progetto del Team (Waterfall, Agile Scrum, Agile Kanban, altro...)
2. Identificare e configurare gli strumenti che permettono di implementare i processi (ITS)
	- Identificazione e definizione dei **tipi**, dei **campi custom**, dei **work flow** e dei **collegamenti** che ci permettono di tracciare le informazioni richieste dal processo
	
![[Pasted image 20240227183528.png]]
##### Configurazione
**Admin** ITS: 
- Crea un nuovo progetto
- Definisce il processo da seguire:
	- Tipi di *work item*, campi custom, work flow, collegamenti
	- Seleziona il modello di stima
	- Differenti Board e Report per processo
- Aggiunge gli utenti e assegnazione ruoli/permessi
**Capoprogetto:**
- Definisce le versioni (*release*)
- Definisce le componenti del progetto
- Definisce il lavoro da svolgere (*backlog*)
	- Priorità
	- Assegnatario
	- Stima
- Definisce la prima iterazione
- Monitora l'avanzamento e il completamento delle attività (filtri, board, Dashboard, Report)
- Definisce le nuove versioni
- Definisce le nuove iterazioni
- Definisce e aggiorna e monitora le attività (*priorità, verifica stima/consuntivo*)
- Produce i report richiesti dal cliente (*p.es. Calcolo SLA, release log, qualità delle versioni o dei componenti...*)
**Team di sviluppo e utenti**:
- Ricevono notifiche dei *work item* assegnati
- Selezionano i *work item* in base alle priorità
- Avviano e completano la lavorazione
	- Avanzano gli stati del workflow
	- Aggiornano la stima a finire
	- Registrano il tempo impiegato
- Documentano lo stato dell'attività (*commenti*) e compilano i campi nel work item
- Completano tutte le attività presenti nell'iterazione
- Effettuano il rilascio
### ITS Benefici
- Implementare un processo e verificarne l'adozione
- Migliorare e misurare la qualità del progetto
- Misurare e aumentare la soddisfazione del cliente
- Migliorare la definizione delle responsabilità
- Migliorare la comunicazione nel team di sviluppo e con il cliente;
- Aumentare la produttività del team di sviluppo
- Gestione del tempo e della produttività personale
- Ridurre le spese e gli sprechi
- No mail company