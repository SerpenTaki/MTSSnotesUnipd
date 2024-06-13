![[Screenshot 2024-05-20 alle 12.03.59.png]]
![[Screenshot 2024-05-20 alle 12.06.55.png]]
### Definizione
La **gestione della configurazione** (CM) è un **processo di ingegneria dei sistemi** per **stabilire** e **mantenere la coerenza** delle prestazioni, delle funzionalità e degli attributi fisici di un **prodotto con i suoi requisiti, la progettazione e le informazioni operative per tutta la sua durata di vita.** Il processo di CM è ampiamente utilizzato dalle organizzazioni di ingegneria militare per **gestire le modifiche durante il ciclo di vita di sistemi complessi**, come sistemi d'arma, veicoli militari e sistemi informativi. Al di fuori dell'ambito militare, il processo di CM è utilizzato anche per la **gestione dei servizi informatici, come definito da ITIL**, e per altri modelli di dominio nell'ingegneria civile e in altri segmenti industriali, come strade, ponti, canali, dighe ed edifici.
#### Definizione (ITIL)
L'obiettivo dei **Configuration Management** è di fornire un **modello logico dell’infrastruttura** attraverso l’identificazione, il controllo, la gestione e la verifica di tutte le versioni di "Configuration Items" esistenti.
**Il configuration item (CI)** è un unit di configurazione che può essere gestita individualmente (tipo: computer, routers, servers, software, etc...)
Un elemento chiave del processo è il Configuration Management Database (CMDB), che viene utilizzato per tracciare tutti i CI e le relazioni tra di loro (tipo: il server A ospita il servizio B, etc...).
Alcuni benefici dell'implementare il processo di configuration management sono i seguenti:
- Disponibilità di informazioni accurate sull'infrastruttura IT
- Maggiore controllo sulle CI (*potenzialmente costose*)
- Maggiore aderenza alle leggi (*es. numero licenze software*)
- Miglior supporto al processo di Incident e Problem Management, soprattutto nella valutazione dell'impatto degli incidenti e nell'analisi della "*root cause*"
### Definizione (*continuous delivery*)
Il processo tradizionale di **gestione della configurazione del software** (SCM) è considerato dai professionisti come la migliore soluzione per **gestire le modifiche nei progetti software**. Identifica gli **attributi funzionali e fisici del software in vari momenti** e **esegue un controllo sistematico delle modifiche agli attributi identificati allo scopo di mantenere l'integrità e la tracciabilità del software** durante il ciclo di vita dello sviluppo del software.
Il processo SCM definisce inoltre la necessità di tracciare le modifiche e la capacità di verificare che il software finale consegnato abbia tutti i miglioramenti pianificati e supportati per essere inclusi nella release. Identifica **quattro procedure** che devono essere definite per ogni progetto software per garantire l'implementazione di un solido processo SCM. Esse sono:
1. Identificazione della configurazione
2. Controllo della configurazione
3. Contabilizzazione dello stato della configurazione
4. Configuration audits
## Obiettivi
**Riproducibilità**: dovremmo essere in grado di eseguire il provisioning di qualsiasi ambiente in modo **completamente automatizzato** e sapere che **qualsiasi nuovo ambiente riprodotto dalla stessa configurazione è identico** 
**Tracciabilità:** dovremmo essere in grado di selezionare qualsiasi ambiente ed essere in grado di **determinare in modo rapido e preciso le versioni di ogni dipendenza** utilizzata per creare quell'ambiente. Vogliamo anche essere in grado di **confrontare le versioni precedenti di un ambiente** e vedere cosa è cambiato tra di loro.
### CM in AWS
**AWS OpsWorks** è un servizio di gestione delle configurazioni che fornisce istanze gestite di Chef e Puppet. Chef e Puppet sono piattaforme di automazione che permettono di utilizzare del codice per automatizzare le configurazioni dei tuoi server. OpsWorks utilizza Chef e Puppet per automatizzare il modo in cui vengono configurati, distribuiti e gestiti i server in tutte le istanze Amazon EC2 o in tutti gli ambienti di calcolo locali.
**AWS CloudFormation** ti fornisce un linguaggio comune per descrivere ed effettuare il provisioning di tutte le risorse dell'infrastruttura nel tuo ambiente cloud. Con CloudFormation puoi usare un semplice file di testo per modellare ed effettuare il provisioning, in modo automatizzato e sicuro, di tutte le risorse necessarie alle tue applicazioni su tutte le regioni e tutti gli account. Questo file sarà l'unica sorgente del tuo ambiente cloud.

$\rightarrow$ vai a [[Artifact Repository]]