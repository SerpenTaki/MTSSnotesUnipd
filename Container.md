# L'era delle macchine fisiche
## Scenario
Ogni applicazione viveva su un server fisico dedicato.
Limitazioni:
- Tempi di deploy molto lenti
- **Costi molto alti**
- **Molte risorse sprecate**
- Difficoltà nello scalare le applicazioni 
- Difficoltà nel migrare le applicazioni
- Difficoltà nell'ospitare più applicazioni sullo stesso sistema operativo
In questa era si sviluppano le Virtual Machine che permettono ai server fisici di **contenere più di un'applicazione**.
Anche la **scalabilità** ne ottiene dei benefici, così come la possibilità di gestire meglio le risorse fisiche **riducendo i costi**.
La nascita dell'**IaaS** permette di avere Macchine Virtuali nel cloud. 
## Virtualizzazione
- Processo di disaccoppiamento tra i servizi di infrastruttura e l'hardware sottostante (allocazione e disallocazione rapida di risorse)
- Il servizio (e.g. risorsa computazionale, rete, storage) è gestito tramite software ed espone delle API, abilitando operazioni CRUD per i clienti
- Nel cloud tutti i servizi di infrastruttura sono virtualizzati
	- Compute virtualization
	- Network virtualization
	- Storage virtualization

## Virtualizzazione delle risorse computazionali
- Astrarre l'hardware rispetto al sistema operativo
- Consente a più sistemi operativi di applicazioni di girare simultaneamente sullo stesso server fisico, cioè si crea un ambiente di esecuzione **isolato (virtual machine)**
- La virtualizzazione consente di far apparire un unico sistema fisico come se fossero molti sistemi
- Le applicazioni non possono accedere a risorse di altre VM se non tramite interfacce di rete (isolamento = maggiore sicurezza)
- Eventuali patch di OS vanno applicate a tutte le VM

## HyperVisor
- Disaccoppia l'hardware fisico dalla virtual machine, cioè emula l'hardware fisico in software (a.k.a. Virtual Machine Monitor)
- Si trova tra l'hardware e il sistema operativo della virtual machine (usa la tecnica dell'emulazione)
- Fornisce ambienti di esecuzione isolati per le VMs.
- Esempi: VMWare ESX Server, Linux KVM, Hyper-V, XenServer

### Funzionalità Hypervisor 
Responsabile primario di 
- Creare ed eseguire VM isolate
- Partizionare e condividere dinamicamente le risorse fisiche (e.g. CPU, RAM, I/O, storage) dell'hardware sottostante tra le diverse VM
### Tipologie di HyperVisor
Due tipi di HyperVisor
- Bare-metal HV, a.k.a. Type 1
	- Gira direttamente sull'hardware e ospita le VM
	- Non richiede un sistema operativo installato sull'hardware ospitante
	- Esempio: VMWare ESX
- Type 2
	- Gira direttamente sul sistema operativo
	- Esempio: VMWare Fusion, Oracle VirtualBox
- KVM (Kernel Virtual Machine) usa il kernel di Linux come hypervisor
	- Possiede aspetti sia di Type 1 che di Type 2
	
## Componenti
#### Host 
- La macchina fisica sulla quale avviene la virtualizzazione 
- Tipicamente un Intel x86 o un AMD
- Vi gira il software HV che crea le virtual machine
- Alcuni stack cloud lo definiscono come **compute node**
#### Guest
- La macchina virtuale stessa
- Ci girano
	- Un sistema operativo completo (incluse dipendenze e patches)
- È memorizzata sull'hardware fisico come insieme di files
	- Disco virtuale, file di configurazione, file di paging, file del BIOS, file di log, eccetera...
- Viene riferita come istanza nei sistemi Cloud (e.g. OpenStack, AWS, GCE)

## Virtualizzazione in Cloud
- Consente di gestire **pool** di risorse computazionali fisiche in cloud
- Uso efficiente di tutte le risorse fisiche disponibili, **riduzione di costi** (sia per il provider che per il consumer)
- Allocazione dimanica delle risorse (compute, network, storage) sulla base delle richieste dei clienti
- Elasticità rapida

## Limiti
Limitazioni delle macchine virtuali: 
- Ogni Virtual Machine necessita di molte risorse: CPU, Spazio disco, RAM ed **un intero sistema operativo completo**.
- Un sistema operativo completo implica molte risorse sprecate
- La portabilità non è garantita 

# L'era dei container 
## Scenario
L'idea di base dei container è quella di utilizzare il kernel del sistema operativo della macchina host per eseguire tanti **root ile system**.
Ogni root file system è chiamato container e su ogni container abbiamo: 
- Processi (di cui uno principale)
- Memoria
- Stack di rete 

## Cos'è un container 
- Applicazione completamente isolata che gira nativamente nel kernel della macchina host
	- Completo isolamento da altri container e dalla macchina host. Un container può accedere ai file ed alle porte di rete della macchina host solo se configurato per poterlo fare
	- Esegue applicazioni direttamente nel kernel dell'host. Un container non ha bisogno di un HyperVisor
- I container che girano sull'host condividono il kernel dell'host
	- Virtualizzazioni del sistema operativo e non dell'hardware
- Ogni container esegue un singolo componente software
	- E.g. un container che esegue Amache HTTP Server

## Come sono isolati i container 
Docker utilizza due tecnologie contenute nel kernel di Linux per isolare container
- Namespaces 
	- Forniscono un ambiente isolato per un container 
	- Quando si esegue un processo in un namespace, l'accesso è limitato a quel namespace
	- Docker isola ogni aspetto di un container utilizzando namespaces quali Process ID (PID), rete, IPC, mount per hostname e domain-name
- Control Groups (cgroups)
	- Utilizzati per limitare le risorse (e.g. memoria) disponibili per un container

## Come creare un container
- I containers sono creati a partire da immagini
- Un'immagine contiene informazioni circa:
	- Il codice eseguibile
		- E.g. codice Python o Java
	- Ambiente necessario per eseguire il codice
		- Un runtime come interprete Python o una JVM
		- Librerie utilizzate dal codice 
		- Variabili di environment
		- File di configurazione 
- Un container engine (e.g. Docker) esegue l'immagine direttamente nel kernel della macchina host e crea il container

# Docker 
## Cos'è Docker? 
Docker è una **open platform** per lo **sviluppo**, **shipping** ed **esecuzione di applicazioni**. Docker permette di separare le applicazioni dalle infrastrutture in modo da poter consegnare software velocemente. 
Con Docker, è possibile **gestire le infrastrutture nello stesso modo in cui si gestiscono le applicazioni**. 
Approfittando delle metodologie di docker per shipping, testing e rilascio veloce del codice, è possibile **ridurre significativamente l'intervallo di tempo tra la scrittura del codice e runnarlo in produzione**.

## Container VS Virtualizzazione
![[containervsvirtualiz.png]]
### Vantaggi rispetto alle VM:
- Velocità e leggerezza
- Non necessitano di un sistema operativo dedicato
- Necessitano di meno risorse: RAM, CPU, Spazio disco
- A parità di condizioni, su un host è possibile lanciare più container virtuali
- Grande portabilità 
- Sono più semplici da gestire
- Sono la soluzione più efficace per sviluppare e rilasciare microservizi

## Docker Platform 
Docker è in grado di eseguire il **package** e il **run** di un'applicazione in un ambiente vagamente isolato chiamato *container*. L'isolamento e la sicurezza consentono di **eseguire svariati containers simultaneamente in un certo host**. 
I container sono **leggeri** perché non necessitano del caricamento di un HyperVisor, ma **runnano direttamente nel kernel della macchina host**. Questo significa che una macchina con un certo hardware è in grado di gestire molti più container in parallelo di quanto non sia in grado di gestire macchine virtuali in parallelo. 
È possibile avviare container Docker all'interno di macchine che a loro volta sono macchina virtuali.

Docker dispone di strumenti e piattaforme per gestire il lifecycle dei containers:
- Sviluppo di applicazioni nonché dei loro componenti di supporto utilizzando containers
- Il container diventa l'**unità per la distribuzione** e il testing dell'applicazione
- Quando si è pronti, si rilascia l'applicazione nel proprio sistema di produzione in quanto container o servizio orchestrato. Questo funziona sia che il **production environment sia un local data center, un cloud provider o un ibrido tra i due**.

# Concetti docker
## Docker engine
È un'applicazione client/server che permette di distribuire ed eseguire i container 
È composto da: 
- **Server** (docker) che utilizza i namespaces del Kernel Linux e i control group per isolare l'esecuzione del container
- **API REST** che permettono ai client di interfacciarsi con il Server e gestire i container 
- **Client** (docker) CLI per interagire con il Server attraverso le API REST

## Docker image
La base per costruire un container. **Rappresenta l'intera applicazione**.
Un'immagine è un **file immutabile** che rappresenta un'istantanea di un container. 
Le immagini sono costituite da **strati di altre immagini** e vengono create con l'operazione di build a partire da un file descrittore chiamato **DockerFile**.
Possono essere condivise e scaricate da un registry.

```dockerfile
FROM tiangolo/meinheld-gunicorn-flask:python3.7

COPY /dist/flaskr-1.0.0-py2.py3-none-any.wh1/app

RUN pip install /app/flaskr-1.0.0-py2.py3-none-any.wh1

ENV FLASK_APP=flaskr

RUN flask init-db

ENV APP_MODULE flaskr:create_app()
```

## Docker Container 
L'unità standard in cui risiede ed esegue il servizio dell'applicazione.
L'applicazione esegue in modo isolato
Contiene tutto il necessario per eseguire l'applicazione
È possibile gestire:
- Volumi esterni
- Tipo di rete e porte utilizzate
## Docker Registry
*Cloud or server based storage and distribution service for your image*
Il registri Cloud più conosciuto è Docker Hub
- È possibile creare un account personale per pubblicare le proprie immagini
- È possibile creare un account personale per pubblicare le proprie immagini
È consigliato avere un Trusted Registry privato dove salvare ed utilizzare le immagini certificate.

## Docker Networking
I container docker sono collegati in rete attraverso network drivers.
Docker è distribuito con alcuni network drivers, abilitando per defailt il bridging e l'overlay.
I container sono spesso collegati in rete attraverso bridging e overlay
Il networking di Docker può essere esteso grazie a plugins
- Usano le API del progetto open source LibNetwork
	- e.g. Kuryr network plugin, Cisco Contiv

# Orchestrazione
## Perché l'orchestrazione? 
- Esistono molti tipi di orchestratori
- Prendono decisioni su **quando** e **dove eseguire attività**
- Sono stati utilizzati in dagli albori dell'informatica: programmazione di Mainframe, Puppet, Terraform, AWS,Mesos, Hadoop, eccetera.
- Dal 2014 è nata la necessità di creare nuovi progetti di orchestrazione
	1. Popolarità del calcolo distribuito
	2. Diffusione dei Docker per distribuzione ed esecuzione di applicazioni in modo isolato
 - Necessità di avere "molti server da gestire come uno solo per eseguire molti containers"
 - Nascita dei **Container Orchestrator** 
## Container Orchestrator
Progetti (open source) sono stati creati negli ultimi 5 anni per:
- Schedulare il running dei container sui server
- Distribuire i container sui nodi/server
- Monitorare e reagire per garantire l'integrità dei container e del nodo
- Gestire storage, network, proxy, security e logging
- Forniscono API per consentire la gestione e l'estensione delle funzionalità

# Docker swarm e Compose
## Docker Swarm
*Uno swarm ("Sciame" in italiano) consiste in un insieme di nodi Docker che si comportano da manager, per la gestione del cluster stesso, e worker, eseguono servizi.*
Swarm si proponeva quindi come lo **strumento di default** per la gestione di container in un cluster di nodi Docker.
### Nodi 
- Si tratta di **istanze di Docker** che partecipano al cluster. Solitamente, ogni istanza del Docker Engine risiede su *una* macchina fisica o virtuale che sia
- Possono essere di tipo **manager** o **worker** (o **entrambi**): più nodi possono avere il ruolo di master, ma solo uno è eletto in un certo momento a coordinare i servizi e a mantenere lo stato del cluster.
- Il **deploy** di una applicazione **passa sempre da un nodo master** che **delega un _task_ ad un nodo worker** (o un altro master, o as se stesso) in modo che *esegua il servizio richiesto*. I nodi del cluster informano sempre il nodo master sullo stato dei task assegnati, in modo da mantenere sempre lo stato dei servizi come richiesto. 
### Task e servizi
- Un nodo master assegna il compito (*task*, appunto) di eseguire un certo *servizio* su un nodo del cluster (possibilmente worker), ovvero avviare una o più istanze di un container a partire da un'immagine
- L'interazione tra il nodo master e la CLI è **asincrona**: da qua si evince che c'è qualcuno che sta facendo qualcosa (task) dopo che abbiamo eseguito un comando. 
![[architettura_docker_swarm.png]]

# Kubernetes
Kubernetes (per gli amici K8s) è un sistema open source per la gestione di **applicazioni containerizzate** in molteplici hosts. Prevede meccanismi di base per il deployment, manutenzione e scaling delle applicazioni.
Kubernetes si basa su un'esperienza di quindici anni di Google nella gestione di carichi di lavoro in produzione su larga scala utilizzando un sistema chiamato Borg, combinata con le migliori idee e pratiche della community.
Kubernetes è hostato dalla *Cloud Native Computing Foundation* (CNCF). Se la tua compagnia vuole aiutare a modellare l'evoluzione delle tecnologie container-packaged, dynamically scheduled e microservice-oriented, considera di entrare a far parte del CNCF. 
## Funzionalità di Kubernetes
- **Gestione dei Container**: automatizza il deployment, la gestione e il monitoraggio dei container
- **Scalabilità Automatica (Auto-scaling)**: K8s può scalare automaticamente le applicazioni in base alla domanda di risorse, utilizzando l'*Horizontal Pod Autoscaler (HPA)* per adattare il numero di repliche dei [[#Pod]] in esecuzione. 
- **Self-Healing**: K8s monitora continuamente lo stato dei pod e dei nodi, riavviando i container falliti, rimpiazzando i nodi morti e ridistribuendo i container su nodi sani per mantenere l'applicazione funzionante.
- **Gestione del Networking**: K8s gestisce la rete tra i container, fornendo un indirizzo IP unico per ogni pod e facilitando la comunicazione tra i pod tramite servizi di rete d DNS interno. 
- **Gestione dello Storage**: K8s può montare e gestire volumi di storage permanenti per i pod, integrandosi con vari provider di storage come AWS, GCP e Azure, nonché con soluzioni di storage permanenti on-premise.
- **Configurazione e Gestione dei Segreti**: K8s gestisce configurazioni e segreti (come password e chiavi API)
- **Gestione del Ciclo di Vita delle Applicazioni**: K8s supporta i processi di aggiornamento continuo e rollback delle applicazioni, consentendo aggiornamenti senza downtime.
- **Isolamento e Sicurezza**: K8s fornisce isolamento tra le applicazioni tramite namespace e implementa politiche di sicurezza che regolano l'accesso ai cluster, ai pod e alle risorse. 
- **Supporto per Architetture Multi-Cloud e Ibride**: K8s è agnostico rispetto al provider di infrastruttura e può essere eseguito in ambienti multi-cloud e ibridi

## Pod
I Pod sono le **unità di deployment più piccole** che possono essere create e gestite in Kubernetes.
Un Pod è un insieme di **uno o più container** (come i container Docker), con archiviazione/rete condivise, e una specifica per come eseguire i container. I contenuti di un Pod sono sempre co-localizzati e co-pianificati, e vengono eseguiti in un contesto condiviso. Un Pod modella un "host logico" specifico per l'applicazione - contiene uno o più container applicativi che sono relativamente strettamente accoppiati.

# Riferimenti
- https://www.slideshare.net/Docker/docker-101-nov-2016
- https://www.slideshare.net/MeganOKeefe1/kubernetes-a-short-introduction-2019
- https://www.docker.com/sites/default/files/Infographic_OneDocker_09.20.2016.pdf
- https://docs.docker.com/get-started/
- https://www.docker.com/blog/containers-replacing-virtual-machines/
- https://it.wikipedia.org/wiki/Docker
- https://docs.docker.com/engine/reference/commandline/docker/
- https://slides.kubernetesmastery.com/
- https://codingjam.it/da-docker-compose-a-docker-swarm-viaggio-di-sola-andata/
- https://github.com/kubernetes/kubernetes
- https://medium.com/containermind/areference-architecture-for-deploying-wso2-middleware-on-kubernetes-d4dee7601e8e
- https://docs.docker.com/compose
- https://kubernetes.io/docs/concepts/workloads/pods/pod-overview
