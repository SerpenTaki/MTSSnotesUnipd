**Static program analysis/static code analysis** is the **analysis of computer software** that is performed **without actually executing programs**, in contrast with dynamic analysis, which is analysis performed on programs while they are executing. In most cases the analysis is performed on some version of the source code, and in the other cases, some form of the object code.
The term is usually applied to the **analysis performed by automated tool**, with **human analysis** being called program understanding, program comprehension, or code review. Software inspections and software walkthroughs are also used in the latter case.
Appartiene alle seguenti categorie di test:
- **Test statico:** non richiede l'esecuzione
- **White Box**: è presente il codice sorgente
- **Test Non Funzionale**
Il software di **revisione automatica del codice** **verifica la conformità del codice sorgente** con un **insieme predefinito di regole o best practice**. L'uso di metodi analitici per ispezionare e rivedere il codice sorgente al fine di individuare i bug è una **pratica di sviluppo standard**, che può essere eseguita sia manualmente che in modo automatizzato. Con l'automazione, gli strumenti software forniscono assistenza nel processo di revisione e ispezione del codice. **Il programma o lo strumento di revisione visualizza in genere un elenco di avvertenze**. Un programma di revisione può anche fornire un modo automatico o assistito dal programmatore per correggere i problemi riscontrati. Si tratta di un componente che permette di padroneggiare facilmente il software. Contribuisce alla pratica della Software Intelligence.
Alcuni strumenti di analisi statica del codice possono essere utilizzati per la revisione automatica del codice. Non sono paragonabili alle revisioni manuali, tuttavia **possono essere eseguite più velocemente** e in modo più efficiente. Questi strumenti, inoltre, **incapsulano una conoscenza approfondita delle regole e della semantica** necessarie per eseguire questo tipo di analisi, in modo da non richiedere al revisore umano del codice lo stesso livello di competenza di un revisore umano esperto.
## Teoria delle finestre rotte
è una teoria criminologica sulla **capacità del disordine** urbano e del vandalismo **di generare criminalità aggiuntiva** e comportamenti anti-sociali. La teoria afferma che mantenere e controllare ambienti urbani **reprimendo i piccoli reati**, gli atti vandalici, la deturpazione dei luoghi, il bere in pubblico, la sosta selvaggia... contribuisce a creare un clima di ordine e legalità **riducendo il rischio di crimini più gravi**.
*Ad esempio l'esistenza di una finestra rotta potrebbe generare fenomeni di emulazione, portando qualcunaltro a rompere un lampione o un idrante dand inizio così ad una spirale di degrado urbano e sociale*.
![[Screenshot 2024-05-02 alle 17.13.20.png]]
### Funzionalità
Simili ad un correttore ortografico, permettono di:
- Imporre il rispetto di convenzioni e stili
- Verificare la congruità della documentazione
- Controllare metriche e indicatori
- Ricercare codice copiato in più punti
- Ricercare errori comuni nel codice
- Misurare la percentuale di codice testato
- Ricercare indicatori di parti incomplete
### Checkstyle
Checkstyle è uno strumento di sviluppo che aiuta i programmatori a scrivere codice Java che aderisce a uno **standard di codifica**. Automatizza il processo di verifica del codice Java per risparmiare all'uomo questo noioso (ma importante) compito. Questo lo rende ideale per i progetti che desiderano **fornire uno standard di codifica**.
Checkstyle può controllare molti aspetti del codice sorgente. Può trovare **problemi di progettazione** delle classi, problemi di progettazione dei metodi. Ha anche la capacità di controllare il layout del codice e i problemi di formattazione.
### FindBugs/SpotBugs
**FindBugs** è un programma che usa l'analisi statica per **trovare i bug nel codice Java**.
**SpotBugs** è il successore spirituale di *FindBugs*, continuare dal punto in cui si è interrotto con il sostegno della sua comunità
### PMD
È un analizzatore statico di codice sorgente. **Individua i più comuni difetti di programmazione** come variabili inutilizzate, blocchi di cattura vuoti, creazione di oggetti non necessari, copia e incolla e così via. Si occupa principalmente di Java e Apex, ma supporta altri sei linguaggi.
## SonarQube
SonarQube è uno strumento di revisione automatica del codice per individuare bug, vulnerabilità e code smell nel codice. Può integrarsi con il flusso di lavoro esistente per consentire una **ispezione continua del codice** tra i rami del progetto e le richieste di pull.
![[Screenshot 2024-05-03 alle 13.30.18.png]]
### Funzionalità:
- **storicizza** l'andamento della qualità
- Permette di verificare se c'è un miglioramento o un deterioramento del progetto nel tempo
- Permette di stabilire un **quality profile** da applicare al progetto
- Permette di stabilire un **quality gate** per verificare se la qualità del progetto rispetta determinati standard
- Le **issue** segnalate vengono classificate in base alla gravità
- Le issue vengono classificate in:
	- **vulnerabilità** -> Permette di valutare il livello di sicurezza del progetto (_security_)
	- **bug** -> Permette di valutare l'affidabilità del progetto (_Reliability_)
	- **Code Smell** -> Permette di valutare la manutenibilità del progetto (_Maintainability_)
- Permette di revisionare le issue segnalate e segnare i falsi positivi
![[Screenshot 2024-05-03 alle 13.42.03.png]]
![[Screenshot 2024-05-03 alle 13.42.13.png]]
