In ingegneria del Software, per *unit testing* si intende l'attività di testing **di singole unità software**. Per unità si intende normalmente il **minimo componente** di un programma dotato di **funzionamento autonomo**; a seconda del paradigma di programmazione o linguaggio di programmazione, questo può corrispondere per esempio a una **singola funzione** nella programmazione procedurale, o una **singola classe** o un **singolo metodo** nella programmazione a oggetti.
Come altre forme di testing, lo unit testing può variare completamente da "*manuale*" a automatico. Specialmente nel caso dello unit testing automati, lo sviluppo dei **test case** _(singole procedure di test)_ può essere considerato **parte integrante dell'attività di sviluppo**.

DEF:
I **Test di unità** sono del codice, **prodotto dallo sviluppatore** che esercitano un'unità del programma. Per unità si intende una **funzionalità atomica** che può essere verificata in modo isolato, in modo da assicurare che il risultato del test non sia influenzato da altre unità. Nella programmazione ad oggetti un'unità può essere uno o più metodi di una classe, o un'istanza di una classe. Nella programmazione procedurale un'unità corrisponde ad una funzione.
Vengono **sviluppati dal programmatore che sviluppa le unità, per verificare l'assenza di alcuni errori, e documentare il comportamento dell'unità prodotta.**
# Proprietà desiderabili (A TRIP)
Automatic Thorough Repeatable Independent Professional.
##### Automatic
I test di unità devono essere eseguiti automaticamente. In ogni progetto deve essere disponibile un "automazione a comando" che permetta a tutti di invocare e far eseguire tutti o una parte dei test di unità in modo semplice.
Durante la fase di sviluppo del progetto è importante che i test possano essere eseguiti:
- **in modo rapido:** I test unità devono essere semplici e la loro esecuzione non deve impiegare più di pochi secondi.
- **Senza richiedere l'interazione umana:** Se un test di unità richiede che alcuni parametri siano inseriti, ogni volta, manualmente da uno sviluppatore, questo non permetterebbe di eseguire tutti i test del progetto in modo automatico a determinate ore del giorno
- **In modo autonomo:** L'automazione che effettua l'esecuzione dei test di unità deve essere in grado di capire quando e dove i test falliscono ed avvisare gli sviluppatori. In questo modo gli sviluppatori saranno interrotti, dall'attività lavorativa, solo quando uno o più test falliranno
##### Thorough (esaustivi)
Dei buoni test di unità devono essere **esaustivi e accurati**, devono verificare il comportamento di qualsiasi parte del progetto che potrebbe creare degli errori.
Esistono degli strumenti che permettono di misurare se ogni parte del progetto è stata eseguita durante la fase di test, e possono calcolare:
- La **percentuale di righe di codice** che vengono esercitate attraverso i test di unità nel progetto
- La **percentuale di possibili diramazioni** che vengono eseguiti dai test di unità 
- Il **numero di eccezioni** che vengono controllate attraverso i test
- Altri dati che permettono di capire dove il progetto è carente di test di unità
Come si può intuire, non è detto che se in un progetto viene eseguito il 100% del codice dai test di unità questo è privo di errori.
![[Screenshot 2024-04-18 alle 17.15.46.png]]
##### Repeatable
I test di unità devono produrre sempre lo stesso risultato
Per essere ripetibili, i test di unità devono avere le seguenti caratteristiche:
- **Essere indipendenti ==dall'ordine== di esecuzione**: L'ordine di esecuzione dei test di unità non deve influenzare il risultato. Per questo è necessario che i test siano indipendenti.
- **Essere indipendenti ==dall’ambiente== di esecuzione:** L'esecuzione dei test non deve dipendere da risorse esterne al progetto o da risorse non gestite nel VCS. Se alcune unità devono utilizzare risorse esterne (*p.es database*) è consigliato utilizzare la tecnica *Mock Object* per simulare il comportamento di queste componenti.
##### Independent
I test di unità devono essere il più possibile **indipendenti dall'ambiente di esecuzione, degli elementi esterni al progetto e dall'ordine di esecuzione**. Quando si scrive un test è consigliato verificare il comportamento di un **singolo aspetto del progetto**. Questo non significa che un test di un'unità deve avere solo una asserzione, ma deve controllare solo un metodo o più metodi che realizzano un aspetto di una funzionalità del progetto.
Se il test è indipendente il suo comportamento sarà ripetibile nel tempo, perchè il suo comportamento non dipenderà dalle altre unità del progetto. La ripetibilità del test è un aspetto che permette se il test è indipendente.
![[Screenshot 2024-04-18 alle 17.39.28.png]]
##### Professional
