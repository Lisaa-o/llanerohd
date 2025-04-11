[![Gitter chat](https://badges.gitter.im/gitterHQ/gitter.png)](https://gitter.im/big-data-europe/Lobby)

# Changes

Version 2.0.0 introduces uses wait_for_it script for the cluster startup

# Hadoop Docker


# MapReduce para contar Palabras

## Copiar los archivos .jar y .txt al contenedor
```
docker cp hadoop-examples-0.20.205.0.jar namenode:/tmp
docker cp puzzle1.dta namenode:/tmp
```
## Ejecutar MapReduce

```
docker exec -it namenode bash
cd /tmp 
hadoop jar hadoop-examples-0.20.205.0.jar sudoku puzzle1.dta
