**L'automazione della build** è il processo di **automatizzazione** della creazione di una *costruzione di software* e dei processi associati, tra cui: la compilazione del codice sorgente del computer in codice binario e l'esecuzione di test automatizzati.
**.Build-automation** utility (come Make, Rake, Cake, MS build, Ant, Gradle ecc.)
il cui *scopo primario è generare artefatti di compilazione* attraverso attività come la compilazione e il collegamento del codice sorgente.
![[Pasted image 20240323162642.png]]
## Esigenze
Quali sono le esigenze che ci portano ad utilizzare un tool di build?
- Poter scaricare, compilare ed utilizzare un progetto open-source
- Collaborare ad un progetto e poter provare le modifiche effettuate
- Modificare un bug presente in una dipendenza
*summary*: A partire dal codice sorgente, creare un artefatto utilizzabile
# Tipi Build-Automation Utility
- **Scripting** _tools_:
	Tramite l'utilizzo di un linguaggio di scripting si definisce un automatismo (*tra cui il processo di build (ad hoc))
	- Script: `.sh, .bat`
	- Make a Makefile: creato da Stuart Feldman nel 1977 nei Laboratori Bell (*Bell Labs*)
	- Apache Ant
	- Gradle
	- Rake
	- Grunt
- **Artifact oriented** *tools*:
	Lo strumento si basa sulla definizione e creazione di un artefatto (*prodotto*)
	- **Apache Maven**
	- NPM
![[Screenshot 2024-03-25 alle 10.44.31.png]]
# Fasi della Build
Il **processo di build** è un insieme di passi che trasformano gli script di build, il codice sorgente, i file di configurazione, la documentazione e i test in un prodotto software distribuibile
![[Screenshot 2024-03-25 alle 10.45.56.png]]
## Caratteristiche (CRISP)
- **Completo**: Indipendente da fonti non specificate nello script di build
- **Ripetibile**: Accede ai file contenuti nel sistema di gestione del codice sorgente. Una esecuzione ripetuta dà lo stesso risultato
- **Informativo**: Fornisce informazioni sullo stato del prodotto
- **Schedulabile:** Può essere programmato ad una certa ora e fatto eseguire automaticamente
- **Portabile:** Indipendente il più possibile dall'ambiente di esecuzione
# Maven
**Apache Maven** è uno strumento per la comprensione e lo sviluppo di progetti software, basato sul concetto di Project Object Model (POM). Maven può gestire il **processo di build**, generare **report** e creare **documentazione** a partire dal POM.

Sfrutta il paradigma "*Convention Over Configuration*" che prevede una configurazione minima (*o addirittura assente*) per il programmatore che utilizza un framework (*come maven*) che lo rispetti, obbligandolo a configurare solo **gli aspetti che si differenziano** dalle **implementazioni standard** o che non rispettano particolari convenzioni di denominazione o simili.
### Caratteristiche:
- *Build Tool*: sono definite delle Build Lifecycle che permettono di configurare ed eseguire il processo di build (*ed altri processi*)
- *Dependency Management*: Le dipendenze di progetto vengono specificate nel file di configurazione (`pom.xml`). Maven si occupa di scaricarle in automatico da dei Repository remoti e salvarle in un repository locale.
- *Remote Repositories*: sono stati definiti dei repository remoti dove sono presenti gran parte delle librerie di progetti opensource e dei plugin utilizzati da maven per implementare e estendere le fasi dei Build Lifecycle
- *Universal Reuse of Build Logic*: Le Build Lifecycle, i plugin maven permettono di definire in modo riusabile i principali aspetti richiesti per la gestione di progetto. Tra cui: l'esecuzione del processo di build, l'esecuzione di framework di test (*p.es. Junit/TestNG*), la creazione di template di progetto (*p.es. Applicazioni Java Web o applicazioni costruite con un determinato framework*)
## Build Lifecycle
Maven è *basato sul concetto centrale di* **build lifecycle**. Questo significa che **il processo per eseguire il build e la distribuzione di un particolare artefatto _(project)_ è definita chiaramente.

Ciò significa che una persona che sta effettuando il build di un progetto dovrà **imparare solo un set ristretto di comandi per compilare** qualsiasi progetto Maven, e il POM assicurerà di ottenere il risultato desiderato.

These are 3 built-in build lifecycles:
1. The **default** lifecycle handles your project deployment
2. The **clean**  lifecycle handles project cleaning
3. Site **lifecycle** handles the creation of your project's site documentation
### Build Lifecycle (_default_)
La **default** Build Lifecycle è composta dalle seguenti fasi (*o goals*)
- **Validate** -> validate the project is correct and all necessary information is available
- **Compile** -> compile the source code of the project
- **Test** -> test the compiled source code using a suitable unit testing framework. These test should not require the code be package or deployed
- **Package** -> Take the compiled code and package it in its distributable format, such as JAR
- **Verify** -> run any checks on result of integration test to ensure quality criteria are met
- **Install** -> install the package into the local repository, for use as a dependency in other projects locally
- **Deploy** -> done in the build environment, copies the final package to the remote repository for sharing with other developers and project
![[Screenshot 2024-03-25 alle 11.13.57.png]]
# POM
Il **Project Oriented Model** (POM) è l'unità fondamentale di lavoro in Maven. Si tratta di un**file XML** che contiene **informationi relative al progetto** e **configurazioni** utilizzate da Maven per la build del project.
Quanto si esegue una **task** o **goal**, Maven cerca il file POM nella directory corrente. Legge il  POM, **ottiene le informazioni di configurazione necessarie**, e poi esegue il goal.
Alcune delle configurazioni che possono essere specificate nel POM sono: 
- Le dipendenze del progetto
- I plugin o goal che possono essere eseguiti
- I profili di build eccetera...
- Altre informazioni come la versione del progetto, la descrizione, gli sviluppatori, mailing list possono essere specificate al suo interno.
- Project ID (*group ID + artifact ID + version*)
![[Screenshot 2024-03-25 alle 11.29.10.png]]
### Project Archetypes
In breve, Archetype è un **toolkit di templating per progetti Maven**. Un archetype è definito come un **modello o schema originale** da cui sono generati **tutti gli altri oggetti dello stesso tipo**. Il nome è appropriato in quanto stiamo cercando di fornire un sistema che offra un mezzo coerente per generare template di progetti Maven per gli utenti, e che fornisca agli utenti i mezzi **per generare versioni parametrizzate di questi template di progetto**.

```shell
mvn archetype:generate -DgroupId=com.mycompany.app -DartifactId=my-app -DarchetypeArtifactId=maven-archetype-quickstart -DinteractiveMode=false
```
Consente di creare un progetto come è definito dall'archetipo `maven-archetype-quickstart`
### Maven Plugin e Mojo
Maven è essenzialmente solo un **framework centrale per una collezione di Plugin Maven**. In altre parole, i **plugin sono dove gran parte dell'azione reale viene eseguita**, i plugin vengono utilizzati per creare file jar, creare file war, compilare codice, testare unità di codice, creare documentazione del progetto, e così via. **Quasi ogni azione che si possa pensare di eseguire su un progetto è implementata come un plugin Maven**.

Un Mojo è semplicemente un obiettivo in Maven, e i plugin consistono in un qualsiasi numero di obiettivi (*Mojos*). I Mojos possono essere definiti come classi Java annotate o *script Beanshell*. Un Mojo specifica i metadati relativi a un obiettivo: un nome di obiettivo, in quale fase del ciclo di vita si inserisce e i parametri che si aspetta.

È possibile sviluppare plugin che eseguono obiettivi all'interno del build lifecycle.
I plugin sono specificati e configurati nel file `pom.xml`.
Vengono scaricati da Maven e salvati nel repository locale insieme alle altre librerie.

$\rightarrow$ vai a [[Integrazione Continua]]