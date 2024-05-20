#### Origini
- è uno strumento di Configuration Management e IT Automation: permette di definire lo stato di uno o più server in modo *prevedibile, replicabile, consistente*
- Nasce nel 2012 quando la "scena" era dominata da Chef e Puppet, Micheal de Haan decide di semplificare al massimo attività ripetitive di Configuration Management
- Il nome deriva dall'omonimo dispositivo che nel romanzo di fantascienza "Il Gioco di Ender" serviva per comandare remotamente le astronavi
### Caratteristiche Principali
- Non richiede l'installazione di "agent" sulle macchine da gestire, si opera dal "controller"
- semplice ed immediato da usare, non richiede conoscenza di linguaggi di programmazione
- Multipiattaforma (*scritto in python*), portabile
- Particolarmente leggero e performante
- idempotente (*si ottiene sempre il risultato atteso*)
- Permette un approccio graduale: si può iniziare ad utilizzare con script già fatti
- Curva di apprendimento bassa: in pochi minuti dalla lettura del manuale si è già operativi
### Concetti Chiave
- **_Control Node o Controller_**
	- Una qualsiasi "macchina" ove sia installato Ansible, si possono eseguire i comandi `ansible`e `ansible-playbook`; si può usare un qualsiasi server linux come controller
- **_Managed Nodes_**
	- Tutti i server gestiti con Ansible, anche chiamati 'hosts'. Sui sistemi Linux è necessario vi sia Python > 2.6 o per quelli Windows WinRM + Powershell
- **_Inventory_**
	- È una lista di server, opzionalmente raggruppati, sui quali ansible può operare
- **_Tasks_**
	- La singola unità di "esecuzione" su Ansible; un singolo task può essere eseguito come comando "ad hoc" con il comando `ansible`
- **_Handlers_** 
	- Sono istruzioni che possono essere eseguite quando un task opera una modifica al sistema. Ad esempio dopo l'installazione di una applicazione potremmo voler avviare il servizio
- **_Playbooks_**
	- Sono insiemi di Tasks e Handlers. Un esempio di playbook potrebbe essere quello per l'installazione e la configurazione di un sistema Apache, php e mysql, che comprende vari step da eseguire in sequenza
- **_Modules_**
	- Sono i "verbi" del nostro linguaggio. Ci sono moduli per installare pacchetti, per copiare file, per eseguire comandi remoti, per interagire con i servizi cloud di Amazon, Google, Openstack, Vmware. È possibile sviluppare un modo custom per estendere Ansible sulle nostre esigenze.
### Installare Ansible
Ansible può essere installato con i packages manager dei vari sistemi operativi Linux (yum, rpm, apt..)
Se non si volesse ricorrere al package manager di sistema operativo si può installare per mezzo di pip, il Python Package Manager.
Requisito di installazione sul controller è quello di avere Python 2 (2.7) o Python 3 (>=3.5) installato.
Una volta installato Ansible con il package manager di SO, il file di configurazione di default è
`/etc/ansible/ansible.cfg*`
* Se si volesse un template del file ‘ansible.cfg’ lo si può scaricare da:
https://raw.githubusercontent.com/ansible/ansible/devel/examples/ansible.cfg
Si usa il comando `ansible-config` per poter vedere quanto configurato di default.
Le configurazioni possono anche essere fatte per mezzo di variabili d’ambiente (es: `ANSIBLE_REMOTE_USER`)
### Comandi in Ansible
I comandi che mette a disposizione Ansible sono:
- `ansible`: serve per eseguire un singolo task su un insieme di host, anche conosciuto come esecuzione di un comando “ad hoc”
- `ansible-playbook`: viene eseguito per far “girare” i playbooks Ansible sugli insiemi di hosts definiti dall’inventory
- `ansible-inventory`: serve per gestire gli Inventory Ansible via command line
- `ansible-doc`: si può accedere all'help "in linea" dei vari moduli installati
Vi sono altri eseguibili forniti con Ansible:
`ansible-galaxy, ansible-vault, ansible-pull, ansible-config`
![[Screenshot 2024-05-20 alle 14.37.44.png]]
#### Commands
L’eseguibile per lanciare un comando “ad-hoc” è: `ansible`
Un comando ad-hoc è un “qualcosa” che si vuole eseguire molto velocemente senza volerlo salvare per essere riutilizzato in futuro, più precisamente l’esecuzione di un singolo modulo, ovvero un’attività singola; ad esempio l’installazione di un pacchetto su più sistemi, la verifica della presenza di un’utenza, lo stato dell’occupazione di un file systems.
Con un comando “ad-hoc” si può eseguire un singolo task sui sistemi indicati dall’inventory.
Capita spesso venga richiesta un’informazione, lo stato, o allineare il contenuto di un file su più sistemi, il comando “ad-hoc” può evitare di collegarsi in ssh ad ogni singolo sistema per effettuare la medesima operazione.
Come parametro del comando `ansible` verrà passato il modulo che si vorrà venga eseguito sui sistemi remoti, se non si specificherà alcun modulo verrà eseguito di default il modulo `command`
![[Screenshot 2024-05-20 alle 14.39.29.png]]
### Ansible Playbooks
Mentre i moduli sono gli ‘strumenti’ messi a disposizione da Ansible, i Playbooks possono essere visti come i manuali di istruzioni di quanto fatto e gli Inventory degli hosts la lista su “dove” venga fatto quanto dettagliato nei “manuali”.
Il modo migliore per imparare a scrivere playbooks Ansible è quello di iniziare a “tradurre” alcuni scripts che già sono stati sviluppati o usati; l’approccio è graduale e si aggiungeranno funzioni e modalità d’uso all’occorrenza.
Prendere spunto da altri Playbooks permette di iniziare ad usare Ansible in pochissimo tempo (anche un paio d’ore).
Un repository di Playbooks examples è presente a questo URL: https://github.com/ansible/ansible-examples
I Playbooks sono scritti in linguaggio YAML.
![[Screenshot 2024-05-20 alle 14.40.24.png]]
![[Screenshot 2024-05-20 alle 14.40.36.png]]
