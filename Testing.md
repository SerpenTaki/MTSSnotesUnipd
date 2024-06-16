Il **software testing** è un'indagine condotta per fornire alle parti interessate informazioni sulla **qualità** del **prodotto software** o **servizio in fase di test** (SUT, Service Under Test).

Il software testing può anche fornire una visione obiettiva e indipendente del software, permettendo all'azienda di analizzare e comprendere il rischio dell'implementazione del software.

Le tecniche di test includono il processo di esecuzione di un programma o applicazione con l'intento di **trovare bug nel software** (errori o altri difetti) e di verificare che il **prodotto software sia adatto all'uso**.
# Definizione
Il **processo** costituito da tutte le attività di lifecycle, sia **statiche** che **dinamiche**, relative alla pianificazione, preparazione e valutazione dei prodotti software e dei prodotti correlati per **determinare che soddisfano i requisiti specificati**, per dimostrare che sono **adatti allo scopo** e **rilevare difetti**.
## Perché?
- L'uomo non è perfetto
- Il codice è scritto da uomini
- Il codice può contenere errori (*bug*)
- I bug possono avere delle conseguenze
- Per questo il software deve essere testato
### Chi può inserire difetti nel codice?
**Programmatore (45%)**:
- Il programmatore fa un errore (**mistake**) durante la fase di sviluppo
	- per esempio non viene considerata la possibilità di ricevere in input una stringa troppo lunga
- Il programmatore inserisce dunque un **difetto** (*fault o bug*) all'interno del programma
- Quando il programma viene eseguito, e la condizione non considerata dal programmatore si verifica, il difetto provocherà un comportamento inatteso del programma
	- L'utente inserisce nella form di input la stringa troppo lunga
- Il programma avrà quindi una **failure**
**Analista (20% analisi dei requisiti, 25% progettazione)**
- L'analista può introdurre un difetto, interpretando in malo modo un requisito
- Il difetto viene introdotto nella fase di analisi e progettazione
- La progettazione del programma e la codifica può essere influenzata dal difetto
### Categorie di testing (*funzionale*)
**Funzionale:**
	Test condotti per valutare la conformità di un componente o di un sistema ai **requisiti funzionali**. Rappresentano **cosa** fa la nostra applicazione. Sono tipicamente più semplici da progettare perché collegati alle funzioni richieste dal cliente.
**Non funzionale:**
	Test condotti per valutare la conformità di un componente o di un sistema ai requisiti non funzionali (*p.es. performance, sicurezza, usabilità , accessibilità*).
	Rappresentano **come** la nostra applicazione risponde alle esigenze 
**Statico:**
	Testare un prodotto di lavoro senza l'esecuzione del codice. (*p.es. analisi e revisione dei documenti, analisi e revisione dei requisiti*)
**Dinamico:**
	Collaudo che prevede l’esecuzione del Software di un componente o di un sistema
**Verifica:** ==Fatto a regola d'arte==
	Il prodotto è realizzato secondo le specifiche (*tecniche*) e funziona correttamente
	Convalidare che il software sia conforme ai suoi obiettivi (*fit for purpose*)
**Validazione:**
	Il prodotto è stato realizzato rispettando le specifiche dell'utente (*requisiti*)
#### Definizione di caso di test
**IEE Standard 610:**
- **Test Case:** A set of input values, execution preconditions, expected results and execution post-conditions, developed for a particular objective or test condition, such as to exercise a particular program path or to compliance with a specific requirement
**ISTQB Glossary:**
- **Test Case** (2018): A set of preconditions, input, actions, expected results and post-conditions, developed based on test conditions.
- **Test Conditions** (2018): An item or event of a component or system that could be verified by **one or more** test cases, e.g. a function, feature, quality, attribute, or structural element.
Ricorda: Non esiste test case, se non esiste il corrispondente requisito da valutare.
I casi di test aiutano anche a ridurre l'ambiguità nei requisiti (funzionali e non funzionali), e quindi ne migliorano la descrizione, e in ultima analisi la documentazione: si parla di testable  
essere eseguiti automaticamente in catene CI/CD.
# Processo di test
1. **Test planning** -> L'attività di stabilire o aggiornare un test plan.
2. **Test control** -> Azioni correttive e di controllo se il piano non viene rispettato
3. **Test analysis** -> Cosa testare
4. **Test design** -> Come testare
5. **Test implementation** -> Attività propedeutica all'esecuzione (p.es. definizione dei casi di test)
6. **Test execution** -> Eseguire il test
7. **Checking result** -> Verificare i risultati e i dati collezionati dalla test execution per capire se il test è stato superato/fallito
8. **Evaluating exit criteria** -> Verificare se sono stati raggiunti gli exit criteria definiti nel test plan
9. **Test results reporting** -> Riportare il progresso rispetto agli exit criteria definiti nel test plan
10. **Test closure** -> Chiusura del processo e definizione azioni di miglioramento
## Seven Testing principles
1. **Testing show presence of defects**:
	- Testare un'applicazione può solo rivelare che **uno o più difetti esistono nell'applicazione**
	- Il test non può dimostrare che l'applicazione sia priva di errori
	- Pertanto, è importante progettare casi di test per trovare il maggior numero possibile di difetti.
2. **Exhaustive testing is impossible**
	- A meno che l'applicazione in prova abbia una struttura logica molto semplice e un input limitato, non è possibile testare tutte le possibili combinazioni di dati e scenari.
	- Per questo motivo, il rischio e le priorità vengono utilizzati per concentrarsi sugli aspetti più importanti da testare
	- Strategie per selezionare i test base:
		- sul rischio (**risk based testing**): funzionalità che hanno impatto sul business
		- sui requisiti (**requirement based**)
3. **Early testing**
	- Avviare la fase di test il prima possibile permette di risparmiare sui costi del progetto
	- Il processo di test non deve essere eseguito quando il progetto è al termine ma deve essere in parallelo allo sviluppo

![[Screenshot 2024-04-18 alle 14.32.08.png]]
![[Screenshot 2024-04-18 alle 14.32.27.png]]
4. **Defect clustering**
	- Durante i test si può osservare che la maggior parte dei difetti segnalati sono legati a un numero ridotto di moduli all'interno di un sistema
	- Un piccolo numero di moduli contiene la maggior parte dei difetti nel sistema
	- Questa è l'applicazione del principio di Pareto ai test del software: circa l'80% dei problemi si trova nel 20% dei moduli
5. **The pesticide paradox**
	- Se continui a eseguire lo stesso set di test più e più volte, siamo sicuri che non ci saranno più gli stessi difetti scoperti da quei casi di test.
	- Poiché il sistema si evolve, molti dei difetti precedentemente segnalati vengono corretti. Ogni volta che viene risolto un errore o è stata aggiunta una nuova funzionalità, è necessario eseguire tutti i test per assicurarsi che il nuovo software modificato non abbia interrotto vecchi errori
	- Tuttavia, anche questi casi di test di non regressione devono essere modificati per riflettere le modifiche apportate nel software per essere applicabili.
6. **Testing is context dependent**
	- Diverse metodologie, tecniche e tipi di test sono legati al tipo e alla natura dell'applicazione. Ad esempio, un'applicazione software in un dispositivo medico richiede più test di un software di giochi.
	- Un **software per dispositivi medici** richiede **test basati sul rischio**, essere conformi con i regolatori dell'industria medica e possibilmente con specifiche tecniche di progettazione dei test.
	- Un **sito web molto popolare**, deve superare rigorosi **test delle prestazioni** e test di funzionalità per assicurarsi che le prestazioni non siano influenzate dal carico sui server.
7. **Absence of errors fallacy**
	- Solo perché il test non ha riscontrato alcun difetto nel software, non significa che il software sia perfetto e pronto per essere rilasciato. I test eseguiti sono stati davvero progettati per catturare il maggior numero di difetti?
	- Il software corrispondeva ai requisiti dell'utente?
- ![[Screenshot 2024-04-18 alle 14.44.06.png]]
### V-model
Un modello di lifecycle dello sviluppo sequenziale che descrive una relazione uno a uno tra le principali fasi dello sviluppo software, dalla specifica dei requisiti aziendali alla consegna, e i corrispondenti livelli di test, dal testing di accettazione al testing dei componenti.

![[Screenshot 2024-04-18 alle 14.46.28.png]]
### Component testing (Unit testing)
- Verificano l'unità: il più piccolo sottosistema possibile (Java: classe o metodo) che può essere testato separatamente
- Veloci da eseguire
- Ogni modifica del codice sorgente dovrebbe scatenare l'esecuzione degli unit test
- Sono indipendenti tra di loro
- Non dipendono dall'ordine di esecuzione
- Il sistema sotto test (*SUT = system under test*) è considerato come white box
### Integration testing
- Verificano se sono rispettati i contratti di interfacci tra più moduli o sub-system
- Verificano l'integrazione tra più sub-systems
- I sub-systems possono essere:
	- **Interni**: già verificati dagli unit testing
	- **Esterni**: database, filesystem...
- Gli integration testing sono più lenti da configurare e eseguire
- SUT è considerato come white box
### System testing
- Verificano il comportamento dell'intero sistema
- Lo scopo principale dei system test è la verifica rispetto alle specifiche tecniche
- Il sistema può essere considerato come white box o black box
	Un tipo di system testing sono gli **smoke testing**:
- Trovare gli errori il *prima possibile* prima della produzione o prima di eseguire altri test sul SUT
- Verificano le funzionalità del SUT
- Conosciuti anche come "**Sanity checking**"
### Acceptance testing
- Anche conosciuti come "**UAT**: *User Acceptance Testing*" o "End User testing"
- Test suites su tutto il SUT, relativi agli use cases e ai requisiti concordati con l'utente finale/cliente
- Svolti con l'utente finale/cliente
- SUT è considerato come black box
![[Screenshot 2024-04-18 alle 14.55.15.png]]

$\rightarrow$ vai a [[Analisi Statica del codice]]