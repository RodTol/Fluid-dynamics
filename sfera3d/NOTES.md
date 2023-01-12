# Sfera3d
Esercizio visto il 9/1/2023. Facciamo una sfera immersa in un fluido.  
Abbiamo visto come usare snappyHexMesh per raffinare la mesh attorno a un oggetto immerso nel box. Siamo stati anche attenti a raffinare la mesh dietro all'oggetto, in modo da osservare meglio la scia.  
Abbiamo un box abbastanza piccolo, può essere sicuramente espanso.  
Per far girare snappy usa :  
```
snappyHexMesh
```
Di base lui crea varie cartelle in cui fa vedere l'evoluzione della mesh. Se aggiungo la flag ```-overwrite```, le cancella e ne fa una sola.  
Per visualizzare in Paraview lei fa una slice, usando la funzione slice di Paraview.
Ricorda che è stato aggiunto nel control dict, anche la funzione Forces per calcolare la Drag Force dell'oggetto.  

## Confronto con la soluzione analitica
Una volta calcolata la simulazione abbiamo deciso di confrontarlo con la soluzione analitica e principalmente verificare che la pressione sia uguale nei due punti della sfera. Oltre a fare lo slice, lei poi per ottenere il grafico ha usato la funzione plot over line di paraview e ha messo una linea passante per A e B.  
Così facendo però non abbiamo la P su tutta la superficie della sfera. Per ottenere ciò lei carica soltanto la mesh della sfera, nelle opzioni di case.foam. Abbiamo trovato un po' di instabilità e poi per visualizzare meglio, usiamo la funzione ```clip```, con il clip type box, in modo da prendere la semisfera superiore. Fatto ciò , tagliamo una circonferenza con un piano e ci salviamo i dati della pressione per poterli plottare. 
Per poter migliorare i risultati, lei consiglia di usare un LinearUpwind come schema di integrazione per tutte le cose, all'interno del controlDict.
Metti export ```LC_ALL = C``` se paraview ha problemi ad aprire le cartelle con i vari 0. , 1. .  

## Correzione 12/1
Abbiamo cambiato leggermente il problema, mettendo la sfera al centro e ora usiamo il risolutore con linearUpwind. Inoltre per il conto del coefficiente ricorda che il diametro è il doppio di quello che abbiamo scritto.  
I risultati sono buoni ma snappy ha fatto non un ottimo lavoro, quindi non funziona benissimo. Abbiamo provato a fare l'altro metodo (vedi MARTA/snappyspher/testSphereRefinied), ossia quello con il file stl, creato con CAD. Per generare la sfera abbiamo usato, Sources -> sphere, con raggio che vogliamo e una risoluzione di 80 per entrambi i parametri. Poi nel file abbiamo messo il nome alla sfera, all'inizio e alla fine del file, perché sarà il nome che leggerà snappy quando lo inserirà nel box. Prima di fare ciò però dobbiamo convertire il file STL in una eMesh, usando la surfaceFeatureExtract (basta mettere il nome giusto nel suo dict). Possiamo quindi andare a vedere il dizionario di Snappy e modificarlo per inserire la sfera nel box.  
