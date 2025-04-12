[![Gitter chat](https://badges.gitter.im/gitterHQ/gitter.png)](https://gitter.im/big-data-europe/Lobby)

# Changes

Version 2.0.0 introduces uses wait_for_it script for the cluster startup

# Hadoop Docker
```
Iniciar el contenedor de Docker
En la carpeta que tenemos el Docker Abrir una terminal ```docker-compose up -d
Para poder comprobar si los contenedores se estan ejecutando se usa el siguiente comando  docker ps
Entrar al nodo maestro con el siguiente comando docker exec -it namenode bash
Visualizar el panel de control pero en este caso solo tenemos uno
Apagar el contenedor de Docker se usa el siguiente comando  stop-dfs.s

# Ejemplo Para contar Palabras
```
primero se descarga el archivo .jar
Despues se descarga el archivo con nombre hadoop-mapreduce-examples-2.7.1-sources.jar
Lo siguiente es mover al archivo hadoop-mapreduce-examples-2.7.1-sources.jar a la misma carpeta donde esta el repositorio Docker
```
# Descargar archivo txt para ejecutar los comandos
```
Se descarga el archivo y se comprime para realizar los comandos
Mover el archivo al repositorio donde esta el docker el_quijote.txt
Para mover el archivo se ejecuta lo sieguiente docker cp hadoop-mapreduce-examples-2.7.1-sources.jar namenode:/tmp
Hacemos lo mismo para el archivo del quijote docker cp el_quijote.txt namenode:/tmp
Creamos una carpeta de entrada dentro del contenedor namenode se ejecuta lo siguiente docker exec -it namenode bash luego se ejecuta el siguiente  hdfs dfs -mkdir /user/root/input_contador
con los siguientes coimando es para copiar el archivo .txt a HDFS
Primero se ejecuta hdfs dfs  cd /tmp despues se ejcuta lo siguiente hdfs dfs -put el_quijote.txt /user/root/input_contador` lo cual es para ejecutar el comando de contar palabras del quijote
Con este se ejecuta el MapReduce se usa el siguiente comando hadoop jar hadoop-mapreduce-examples-2.7.1-sources.jar org.apache.hadoop.examples.WordCount input_contador output_contador
Para ver los resultados ejecutamos los siguientes comandos  hdfs dfs -cat /user/root/output_contador/*
Por ultimo para poder ver los resultados con el bloc de notas que es para visualizar el archivo que ocupamos en txt quijote_wc.txt
```
# Para cambiar el archivo que sea algo diferente del quijote
```Se ocupa todos los mismos comandos solo se empieza a tener cambios es en buscar otro archivo para poder leer un diferente archivo y tener el mismo proceso con todos los comandos
```

# Resolver el Sudoku
Descargar un archivo de ejemplo MAPRREDUCE
Después movemos el archivo hadoop-examples-0.20.205.0.jar al docker que ya tenemos la carpeta realizada
También debemos de tener descargado el archivo puzzle1.dta
Movamos el archivo hadoop-examples-0.20.205.0.jar  ejecuta el siguiente comando docker cp hadoop-examples-0.20.205.0.jar namenode:/tmp 
se hace el mismo movimiento para el puzzle con el siguiente comando docker cp puzzle1.dta namenode:/tmp
Ahora tenemos que ejecutar el MAPREDUCE se ingresa al contenedor ejecutando los siguientes comandos  docker exec -it namenode bash
se va ejecutando los sieguientes comandos para ejecutar la visualización del sudoku cd /tmp y hadoop jar hadoop-examples-0.20.205.0.jar sudoku puzzle1.dta
Para ver los resultados se hacen los siguientes comandos primero se ejcuta hadoop jar hadoop-examples-0.20.205.0.jar sudoku puzzle1.dta > solucion_puzzle1.txt
Después ejecutamos el exit
Por último para acabar los comandos se ejecuta el sieguiente docker cp namenode:/tmp/solucion_puzzle1.txt .
Para poder visualizar los datos se ejcuta el siguiente comando ya para poder visualizarlo en un bloc de notas en donde se pueden checar los resultados solucion_puzzle1.txt
