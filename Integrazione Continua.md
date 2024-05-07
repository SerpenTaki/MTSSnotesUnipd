**Continuos Integration _NON E'_ Build Automation**
#### Definizione
Nell'ingegneria del software, la continuos integration è una pratica che si applica in contesti in cui lo sviluppo del software avviene attraverso un sistema di versioning. Consiste **nell'allineamento frequente dagli ambienti di lavoro degli sviluppatori verso l'ambiente condiviso**. Il concetto è stato originariamente proposto nel contesto dell'extreme programming (XP), come contromisura preventiva per il problema dell'integration hell.
Il CI è stato originarimente concepito per essere complementare rispetto ad altre pratiche, in particolare legate al Test Driven Development. In particolare si suppone generalmente che siano stati predisposti **test automatici** che gli sviluppatori **possono eseguire immediatamente** prima di rilasciare i loro contributi verso l’ambiente condiviso, in modo da garantire che le modifiche non introducano errori nel software esistente. Per questo motivo il CI viene applicato in ambienti in cui siano presenti sistemi di **build automatico** e/o esecuzione automatica di test, come Jenkins.
### Motivazioni:
Per **lunghi periodi di tempo**, durante il processo di sviluppo, **il progetto non è in uno stato funzionante** o in uno stato utilizzabile. Sopratutto in progetti dove si sviluppa in un singolo ramo di sviluppo.
Nessuno è interessato a provare ad eseguire l'intera applicazione fino a quando non è finito il processo di sviluppo
In questi progetti spesso viene pianificata la fase di integrazione alla fine del processo di sviluppo. In questa fase gli sviluppatori effettuano attività di merge ed effettuano attività di verifica e validazione
##### Problema (*integration hell*):
La fase di integrazione può richiedere molto tempo e nel caso peggiore, **nessuno ha modo di prevedere quando terminerà** questa fase e di conseguenza quando l'applicazione può essere rilasciata.
#### Definizione
*"Continuos Integration doesn't get rid of bugs, but it does make them dramatically easier to find and remove." (Martin Fowler)*
Consente a un Team di intensificare l'attività di sviluppo e test, **integrando gli sviluppi _(nel VCS)_ il più spesso possibile.**
![[Screenshot 2024-05-07 alle 20.29.11.png]]
### Processo - visione generale
- Al **completamento** di un'attività viene **costuito il prodotto:**