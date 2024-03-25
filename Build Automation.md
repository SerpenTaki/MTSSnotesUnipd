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
**Apache Maven** is a software project management and comprehension tool. Based on the concept of a Project Object Model (POM). Maven can manage a **project's build**, **reporting** and **documentation** from a central piece of information.

Sfrutta il paradigma "*Convention Over Configuration*" che prevede una configurazione minima (*o addirittura assente*) per il programmatore che utilizza un framework (*come maven*) che lo rispetti, obbligandolo a configurare solo **gli aspetti che si differenziano** dalle **implementazioni standard** o che non rispettano particolari convenzioni di denominazione o simili.
### Caratteristiche:
- *Build Tool*: sono definite delle Build Lifecycle che permettono di configurare ed eseguire il processo di build (*ed altri processi*)
- *Dependency Management*: Le dipendenze di progetto vengono specificate nel file di configurazione (`pom.xml`). Maven si occupa di scaricarle in automatico da dei Repository remoti e salvarle in un repository locale.
- *Remote Repositories*: sono stati definiti dei repository remoti dove sono presenti gran parte delle librerie di progetti opensource e dei plugin utilizzati da maven per implementare e estendere le fasi dei Build Lifecycle
- *Universal Reuse of Build Logic*: Le Build Lifecycle, i plugin maven permettono di definire in modo riusabile i principali aspetti richiesti per la gestione di progetto. Tra cui: l'esecuzione del processo di build, l'esecuzione di framework di test (*p.es. Junit/TestNG*), la creazione di template di progetto (*p.es. Applicazioni Java Web o applicazioni costruite con un determinato framework*)
## Build Lifecycle
Maven is **based around the central concept of a build lifecycle**. What this means is that **the process for building and distributing a particular aritfact _(project)_ is clearly defined**.

For the **person building a project**, this means that it **is only necessary to learn a small set of commands to build** any Maven project, and the POM will ensure they get the result they desired.

These are 3 built-in build lifecycles:
1. The **default** lifecycle handles your project deployment
2. The **clean**  lifecycle handles project cleaning
3. site **lifecycle** handles the creation of your project's site documentation
### Build Lifecycle (_default_)
La **default** Build Lifecycle è composta dalle seguenti fasi (*o goals*)
- **Validate** -> validate the project is correct and all necessary information is available
- **Compile** -> compile the source code of the project
- **Test** -> test the compiled source code using a suitable unit testing framework. These test should not require the code be package or deployed
- **Package** -> Take the compiled code and package it in its distributable format, such as JAR
- **Verify** -> run any checks on result of integration test to ensure quality criteria are met
- **Install** -> install the package into the local repository, for use as a dependency in other projects locally
- **Deploy** -> done in the build environment, copies the final package to the remote repository for sharing with othere developers and project
![[Screenshot 2024-03-25 alle 11.13.57.png]]
# POM
A **Project Oriented Model** or **POM** is the fundamental unit of work in Maven. It is an **XML file** that contains **information about the project** and **configuration details** used by Maven to build the project.
When executing a **task or goal**, Maven looks for the POM in the current directory. It reads the POM, **gets the needed configuration information**, then executes the goal.
Some of the configuration that can be specified in the POM are:
- The project dependencies
- The plugin or goals that can be executed
- The build profiles and so on
- Other information such as the project version, description, developers, mailing list and such can also be specified
- Project ID (*group ID + artifact ID + version*)
![[Screenshot 2024-03-25 alle 11.29.10.png]]
### Project Archetypes
In short, Archetype is a **Maven project templating toolkit**. An archetype is defined as an **original pattern or model** from which all **other things of the same kind are made**. The name fits as we are trying to provide a system that provides a consistent means of generating Maven project templates for users, and provides users with the means **to generate parameterized versions of those project templates.**
```shell
mvn archetype:generate -DgroupId=com.mycompany.app -DartifactId=my-app -DarchetypeArtifactId=maven-archetype-quickstart -DinteractiveMode=false
```
Allows you to create a project as defined by the `maven-archetype-quickstart`archetype
### Maven Plugin e Mojo
"Maven" is really just a **core framework for a collection of Maven Plugins**. In other words, **plugin are where much of the real action is performed**, plugin are used to create jar files, create war files, compile code, unit test code, create project documentation, and on and on. **Almost any action that you can think of performing on a project is implemented as a Maven plugin**.

A Mojo is really just a goal in Maven, and plug-ins consist of any number of goals (*Mojos*). Mojos can be defined as annotaded Java classes or *Beanshell script*. A Mojo specifies metadata about a goal: a goal name, which phase of the lifecycle it fits into, and the parameters it is expecting.

It is possible to develop plugin that execute goals within the Build Lyfecycle.
Plugins are specified and configured in the `pom.xm`
They are downloaded from maven and saved to the local repository along with the other libraries.
