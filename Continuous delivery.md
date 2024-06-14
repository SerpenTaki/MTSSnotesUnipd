#### Cos'è la Continuos Delivery
"*Your team prioritizes keeping the software deployable over working on new features*" (Martin Fowler)

La Continuous Delivery è il passo successivo alla Continuos Integration:
- **Ogni cambiamento** al sistema **può potenzialmente essere rilasciato in produzione**
- Il rilascio può essere fatto in ogni momento in ogni ambiente (**premendo un bottone**)
![[Screenshot 2024-06-14 alle 19.41.27.png]]
![[Screenshot 2024-06-14 alle 19.42.01.png]]
### Continuos Delivery
La Continuos Integration permette di avere **feedback su problemi introdotti dagli sviluppatori**. Si focalizza sulla parte DEV e assicura che:
- il codice compili
- Vengono eseguiti i test di unità, integrazione, accettazione e l'analisi statica.
Questo non è sufficiente per garantire la possibilità di rilasciare il prodotto ad ogni modifica perchè **le attività che di solito fanno perdere più tempo** avvengono nella **fase di rilascio e test** (e nella comunicazione e la collaborazione tra DEV TEST E OPS)
### Problemi ricorrenti
- i sistemisti (OPS) aspettano molto tempo per ricevere la documentazione (*procedure di rilascio*) per effettuare il rilascio
- I tester (TEST) attendono molto tempo per effettuare le verifiche e le validazioni nella versione giusta (e di avere un ambiente funzionante)
- Il team di sviluppo (DEV) riceve segnalazioni di bug su funzionalità che sono state rilasciate da settimane
- Ci si rende conto solo alla fine dello sviluppo (troppo tardi) che l'architettura scelta non permette di soddisfare i requisiti non funzionali (DEV e OPS)
### Conseguenze
Questo porta a software che:
- Non è rilasciabile perchè è stato impiegato troppo tempo per farlo entrare in un ambiente simile alla produzione
- Contiene molti difetti perchè il ciclo di feedback tra il team di sviluppo e il team di testing e Operations è troppo lungo
![[Screenshot 2024-06-14 alle 20.02.03.png]]
### Misurare per migliorare
L'obiettivo è quello di **migliorare il processo** che permette di **rilasciare una modifica** al codice sorgente del processo in produzione.
Un vantaggio competitivo è dato dalla creazione di valore su tutte le attività richieste dal processo.
Una "Value Chain" è una modellazione del processo per misurare:
- **Il valore Globale**
- Il valore residuo da inserire nella "Value Chain" **(il miglioramento)**
Usare una **"Deployment Pipeline"** dà gli **stessi risultati di utilizzare una "Value Chain"** negli altri settori non software:
- Controllare le prestazioni e migliorarne l'efficienza
- "Fast is cheap": le pipeline permettono di trovare i problemi il prima possibile
![[Screenshot 2024-06-14 alle 20.14.25.png]]
### Deployment Pipeline
È la modellazione del processo di Deployment tramite una successione di fasi (*stages*) e verifiche (*gates*)
- il passaggio da una fase all'altra viene verificato tramite il superamento di una verifica
- Il passaggio di una fase può scatenare una notifica
- È guidato dal concetto di Fail-Test
![[Screenshot 2024-06-14 alle 20.29.18.png]]
### Anatomia di una Deployment Pipeline
È composta da **stages** mappate su attività **misurabili**.
La **transazione** tra 2 stages viene definita **gate**
- Può essere **automatica** o **manuale**
- I gates scatenano il passaggio allo stage successivo
Gli stages possono essere **eseguiti in parallelo e/o in sequenza**
I **gates** possono essere multi direzionali
### Come realizzare la Continuous Delivery?
- Avere un **rapporto di lavorativo cooperativo con tutti i partecipanti**
- Utilizzare le **Deployment Pipelines** per definire il processo di build, test e deploy dell'applicazione
- Distribuire il processo di build e deploy su più ambienti

![[Screenshot 2024-06-14 alle 20.41.46.png]]
![[Screenshot 2024-06-14 alle 20.42.03.png]]
## Requisiti
- [[Integrazione Continua]]
- [[Version Contol System (VCS)]]
- [[Build Automation]]
- [[Unit Testing]]
- [[Artifact Repository]] Sistemi che permettono di gestire le dipendenze e gli artefatti prodotti dal nostro sistema
- [[Configuration Management]]: Strumenti che ci permettono di gestire la configurazione degli ambienti dove dovrà essere rilasciato il nostro software
- **Continuous Testing:** Test automatici a livello di sistema funzionali e non funzionali
- **Orchestratore**: Sistema software che ci permette di modellare le esecuzioni della pipeline

# Only Build Your Binaries Once
Eseguire il processo di build solo una volta garantisce di utilizzare lo stesso artefatto per effettuare tutte le verifiche in ogni ambiente. Questo ci garantisce che:
- L'artefatto che verrà rilasciato in produzione è esattamente lo stesso artefatto che è stato verificato e validato nelle Stages della pipeline
- È una forma di ottimizzazione. Eseguire il processo di build più volte rende la pipeline meno efficiente
Per realizzare questa pratica è consigliato avere un repository dove rilasciare gli artefatti e da cui recuperare le informazioni del commit nel VCS da cui è stato creato l'artefatto ([[Artifact Repository]])
L'artefatto generato deve essere indipendente dall'ambiente di esecuzione: è necessario tenere il codice separato dalle configurazioni che differisce tra gli ambienti

# Deploy the Same Way to Every Environment
