# Modifica di un solutore di OpenFoam
L'obbiettivo è quello di aggiungere una forza di massa al solutore IcoFoam (rendendolo un po' più simile a PimpleFoam).  
Ricorda di modificare assolutamente Make/file, che è quello che indica che file compilare e dove salvarlo, altrimenti modifico IcoFoam per tutti
Dentro al file C, vediamo come ho la classe fvVectorMatrix. Questa è l'equazione del moto, infatti vediamo come aggiungere la forza di massa.   
$$   \nabla $$
Abbiamo aggiunto la lettura dell'input di Force mass all'interno di createFields.h, in maniera molto simile a U e p.  


## Applicazione pratica
Una volta scritto prova a usarlo per risolvere Poiselle, ma ricorda che devi aggiungere dentro 0 il campo ForceMass che andrà letto.