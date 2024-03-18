Il framework Scrum è una pratica, un modo di lavorare, fino agli anni '90 approccio **a staffetta**, che comporta svantaggi se una volta terminato il progetto ci sono delle discrepanze con l'assignment del committente.
Scrum introduce la pratica degli **Sprint**, un approccio olistico 

- Scrum è un **processo agile** che nasce per sviluppo di **progetti complessi**. Permette di concentrarsi sulla consegna del maggiore valore business nel più breve tempo
- consente di ispezionare il codice rapidamente e ripetutamente 
- il business, ossia il cliente, stabilisce le priorità. Il team si organizza di conseguenza.
- Ogni due settimane si valuta il software funzionante e si decide se rilasciare o aggiungere un'altra fase di Sprint. 

Viene utilizzato in molteplici ambiti come software commerciale, videogames, siti web, sistemi, sistemi embedded...
#### Caratteristiche principali
- leggero
- facile da capire 
- difficile da padroneggiare

Si basa su tre pilastri:
- trasparenza 
- controllo
- adattamento 

##### Nel dettaglio
- I gruppi si auto-organizzano.
- Il prodotto evolve attraverso "Sprint" mensili.
- I requisiti sono trattati come elementi di una lista delle "product backlog"
- non vengono prescritte particolari pratiche ingegneristiche
- Si basa sull'attività empirica cioè la conoscenza si basa sull'esperienza e le decisioni si basano su ciò che è conosciuto 
- Processo iterativo e incrementale per ottimizzare il controllo dello sviluppo e il controllo del rischio.

*persone e iterazioni* più che *processi e strumenti 
software funzionante* più che *documentazione ampia* (il framework non è una giustificazione per non produrre documentazione)
*collaborazione con il cliente* più che *negoziazione del contratto
Risposta al cambiamento* più che *seguire un piano*
#### Sprint

![[scrum.png]]
I progetti Scrum progrediscono attraverso una serie di "Sprint", analoghi alle iterazioni della Extreme Programming (altra pratica agile)
- durata tipica 2-4 settimane
- una durata costante favorisce un ritmo migliore
- il prodotto è progettato realizzato e testato durante lo Sprint 
- all'interno dello Sprint vengono celebrati tutti gli eventi/cerimonie
Le fasi di _requisiti_, _progetto_, _codifica_ e _test_ che si verificano nel framework **a staffetta** vengono in pratica affrontate anche nel framework Scrum, ma per ogni fase di Sprint. 
**Non si cambia durante lo Sprint** una volta che sono stati fissati i goal dello sprint, nel 99% dei casi nello sprint si sviluppa una certa funzionalità, se si interrompe si va ad allungare i tempi. 
##### Revisione e rischi Sprint 
- Lo Sprint backlog può essere chiarito e rinegoziato tra il Product Owner e il team di sviluppo non appena si conosce di più
- la durata dello Sprint assicura che il rischio di scostarsi da quanto chiesto dal product owner sia limitato alla durata dello sprint
- **uno Sprint può essere cancellato** se lo Sprint Goal diventa obsoleto 
- **MA** avendo una durata limitata (max 1 mese) **raramente ha senso** 

#### Ruoli 
##### Product owner
- definisce caratteristiche prodotto
- rappresenta desidero committente
- decide date e contenuto del rilascio 
- responsabile 
- ...

##### Scrum Master
- rappresenta conduzione progetto 
- responsabile adozione valori pratiche scrum
- rimuove ostacoli
- si assicura che gruppo di lavoro sia pienamente operativo e produttivo
- favorisce una stretta cooperazione tra tutti i ruoli e le funzioni 
- protegge il gruppo di lavoro da interferenze esterne
- servant leader: aiuta Product Owner e il Team di sviluppo condividendo la gestione e le decisioni con il team.

##### Development team 
- tipicamente 5-9 persone
- responsabili di realizzare l'incremento in conformità alla [[Definition of Done#Definijjjjjj
- competenze trasversali: programmatori, tester, progettisti di user experience, ecc 
- membri di progetto dovrebbero lavorare full-time (possono esserci eccezioni, ad esempio amministratori di basi di dati)
- il gruppo di lavoro si auto-organizza. Idealmente, niente titoli, ma in rari casi può essere una possibilità

#### Eventi
##### Sprint Planning
È un evento _Time boxed_, solitamente della durata di 8 ore per sprint di 1 mese
- Il team seleziona dal product backlog gli item che può impegnarsi a completare.
- Viene creato lo Sprint backlog collaborativamente da tutto il team 
- Vengono identificati i Tasks, e ciascuno di questi viene stimato (1-16 ore)

#### Daily scrum (stand-up meeting)
Si tratta di un incontro giornaliero di 15 minuti, è un evento veloce che si svolge solitamente in piedi, in modo da non doversi sedere e rendere la riunione prolissa.
- non ha finalità di risoluzione problemi, ma di sincronizzazione su quanto fatto e pianificare la giornata per il raggiungimento dello Sprint goal
- si aggiorna la scrumboard
- aiuta a evitare altre riunioni non necessarie 
- solitamente si chiede
	- cos'hai fatto ieri 
	- cos'hai fatto oggi
	- c'è qualcosa che ti impedisce di farlo? 
**Non è un SAL** (che cazzo è? boh) 

#### Sprint review
È sempre un evento _Time boxed_, ossia circa 4 ore per Sprint di un mese
- il gruppo di lavoro presenta ciò che ha realizzato
- viene validato e accettato quanto realizzato
- tipicamente in forma di demo delle nuove caratteristiche o dell'architettura sottostante
- informale
	- regola delle 2 ore per la preparazione
	- niente slide
- partecipa tutto il gruppo 
- tutto sono invitati (anche esterni)
#### Sprint retrospective
- si celebra dopo la Sprint review e prima del prossimo sprint planning
- si valuta ciò che sta funzionando e cosa no
	- come migliorare la qualità del prodotto
	- la [[#Definition of Done]] è appropriata? (what cazzo does it significa?)
	- Che miglioramenti possiamo apportare al prossimo Sprint?
- partecipa tutto il gruppo i lavoro, è una riunione interna, il product owner si fotte. 
	- Scrum master
	- Product owner
	- Development Team

#### Artifatti
##### Product Backlog
- I requisiti, funzionalità, miglioramenti, fix da realizzare nei prossimi rilasci
-  Una lista di tutti i “desiderata”
- Idealmente espressa in modo che ciascun elemento ha valore per gli
- utenti o I clienti del prodotto
-  Priorità assegnate dal Product Owner mentre il Development Team stima ogni item
- Priorità rivalutate all’inizio di ogni sprint con il Development Team
- Raffinamento continuo, è una lista dinamica che evolve con il prodotto

| Elementi del backlog                                                                                                      | Stima |     |
| ------------------------------------------------------------------------------------------------------------------------- | ----- | --- |
| Permettere ad un ospite di effettuare una prenotazione                                                                    | 3     |     |
| Come ospite, voglio cancellare una prenotazione                                                                           | 5     |     |
| Come ospite, voglio cambiare le date di una prenotazione                                                                  | 3     |     |
| Come impiegato dell'hotel, posso lanciare i report RepPAR (Revenue Per Available Room = Fatturato per camera disponibile) | 8     |     |
| Migliorare la gestione delle eccezioni                                                                                    | 8     |     |
###### User Stories
Sono gli Item che compongono il Product Backlog e andranno scomposte in Task

#### Definition of Done
Definisce il significato di "FATTO" per uno Sprint Item
- il minimo set i attività per definire che un'attività è completata 
- può variare per gruppo di lavoro 
- deve essere bene chiaro per tutti i membri del gruppo di lavoro 
- È utilizzato per verificare se un'attività è da ritenersi completata 
#### Acceptance criteria
Permette di conermare se la storia è ompleta e funziona come voluto
- frasi semplici condivise da Product Owner e Development Team
- Possono essere incluse con la User Story
- Rimuovono l'ambiguità dei requisiti

(sprint burnout)

#### Scalabilità di Scrum 
- Tipica dimensione del team è 7 (± 2) persone
	- Scalabilità gestita come “team di team”
- Fattori collegata alla scalabilità
	- Tipo di applicazione
	- Dimensione del team
	- Distribuzione del team
	- Durata del progetto
- Scrum è già stato utilizzato per progetti 500+ persone (Scrum of scrums)