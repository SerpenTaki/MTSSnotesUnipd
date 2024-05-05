![[Screenshot 2024-05-03 alle 13.44.12.png]]![[Screenshot 2024-05-03 alle 13.44.31.png]]
### Binary repository manager
Un **gestore di repository binari** è uno strumento software progettato per **ottimizzare** il **scarico** e la **conservazione dei file binari utilizzati** e **prodotti** nello **sviluppo di software.** Centralizza la gestione di tutti gli **artefatti binari generati** e **utilizzati** dall'organizzazione per superare la complessità derivante dalla diversità dei tipi di artefatti binari, dalla loro posizione nel flusso di lavoro complessivo e dalle dipendenze tra di essi.
Un repository binario è un repository software per **pacchetti, artefatti** e **metadati corrispondenti**. Può essere utilizzato per archiviare **file binarie prodotte** da un'organizzazione stessa, come i rilasci dei prodotti e le build notturne dei prodotti, **o per file binari di terze parti** che devono essere **trattati in modo diverso per ragioni sia tecniche che legali**.
# Artifact Repository
The outputs of the commit stage, your reports and **binaries, need to be stored somewhere for reuse in the later stages of your pipeline**, and for your team to be able to get hold of them. The obvious place might appear to be your version control system. There are several reasons why this is not the right thing to do, apart from the incidental facts that in this way you're likely to work through disk space fast, and that some version control systems won't support such behavior.
Il repository degli artefatti è un tipo insolito di sistema di controllo delle versioni, in quanto **deve mantenere solo alcune versioni.** Una volta che una **release candidate ha superato una certa fase della pipeline di distribuzione, non ci interessa più.** Quindi possiamo, se lo desideriamo, eliminare i binari e i report dal repository degli artefatti.
È essenziale essere in grado di risalire **dal software rilasciato alle revisioni del controllo di versione che sono state utilizzate per crearlo.** Per fare questo, un'istanza di una pipeline deve essere correlata alle revisioni del sistema di controllo di versione che l'hanno innescata. **Il controllo di qualsiasi cosa nel controllo sorgente come parte della pipeline rende questo processo significativamente più complesso grazie alle ulteriori revisioni associate alla pipeline.**
Uno dei criteri di accettazione di una buona strategia di gestione della configurazione è che il processo di creazione dei binari deve essere ripetibile. Cioè, **se cancello i binari e poi rieseguo la fase di commit dalla stessa revisione** che l'ha originariamente attivata, **dovrei ottenere di nuovo esattamente gli stessi binari.** I binari sono cittadini di seconda classe nel mondo della gestione della configurazione, anche se vale la pena di conservare gli hash dei binari in un archivio permanente per verificare che si possa ricreare esattamente la stessa cosa e per controllare il passaggio dalla produzione alla fase di commit.![[Screenshot 2024-05-03 alle 16.32.14.png]]
##### Caratteristiche
- Ambiente dove depositare e pubblicare i prodotti
- Agisce da intermediario per scaricare prodotti da depositi esterni
- Permette di effettuare ricerche e reperire informazioni riguardanti i prodotti
- Permette di gestire e associare permessi d'accesso sui prodotti
- Permette di segnalare problemi di vulnerabilità su prodotti
- Permette di verificare problemi legati a licenze (dipendenze con prodotti terzi)
- Permette di documentare gli artefatti con dei metadati (p.es *pom.xml*)
### Caratteristiche degli artefatti
Possibilità di distinguere univocamente un artefatto (G.A.V)
Metadati che permettono di capire se (p. es. *pom.xml*)
- Artefatto di produzione/sviluppo (politiche di gestioni differenti)
- Riferimento del commit nel VCS da cui è stato creato l'artefatto
- Informazioni delle licenze
- Informazioni delle dipendenze
- MD5, SHA1 per garantire l'autenticità dell'artefatto
- Identificativo univoco
## Maven Repository Management
- **Proxy Remote Repositories:** Possibilità di configurare il repository interno in modo da recuperare gli artefatti da repository esterni. Se l'artefatto non è presente nel repository interno viene consultato il repository esterno
- **Hosted Internal Repositories:** Possibilità di condividere all'interno di un'organizzazione artefatti di terze parti che hanno vincoli di licenza
- **Release Artifacts** Gli artefatti di tipo Release solitamente possono essere rilasciati una sola volta e vengono mantenuti nel repository
- **Snapshot Artifacts**: Gli artefatti in fase di sviluppo possono essere rilasciati più volte. Possono essere eliminati. Di solito contengono il la Keyword SNAPSHOT e il timestamp
### Perchè usare un maven Repository Interno
- **Velocità del processo di Build**: Le dipendenze e gli artefatti di tipo plugin utilizzati nel processo di build vengono scaricati dalla rete interna
- **Maggiore stabilità e controllo:** I repository gestiti possono essere analizzati e si può decidere di vietare l'utilizzo di determinati artefatti per evitare problemi di sicurezza. È possibile distribuire le versioni ufficiali e certificate degli artefatti di terze parti. È più semplice fare analisi
- **Facilitano la collaborazione:** Si evita di far creare gli artefatti dal VCS ed è più semplice identificare le versioni di rilascio certificate
![[Screenshot 2024-05-05 alle 12.38.21.png]]
![[Screenshot 2024-05-05 alle 12.38.40.png]]
![[Screenshot 2024-05-05 alle 12.40.44.png]]
![[Screenshot 2024-05-05 alle 12.41.01.png]]
![[Screenshot 2024-05-05 alle 12.41.20.png]]

