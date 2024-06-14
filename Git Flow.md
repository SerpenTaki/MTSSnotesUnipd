Per inizializzare il repository:
```
git flow init
```

il programma chiede
- nome branch principale
- prefisso per features
- prefisso per bug-fix
- prefisso release
- tag 
- eccetera

Per iniziare una feature:
```
git-flow feature start nome_feature
```

analogamente con `finish` al posto di `start` per terminare la feature. 

### Perché usare `feature`

- workflow comune in ambiente di lavoro condiviso
- terminare una feature implica direttamente la cancellazione del branch **in locale** della feature 

**`release`** si comporta nella stessa maniera di `feature` 

## Fork


