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