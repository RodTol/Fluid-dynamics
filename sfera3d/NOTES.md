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
