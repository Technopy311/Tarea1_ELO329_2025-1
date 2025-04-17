# Resumen y punteo de T1 ELO329

## Idea principal
Patron publicador y suscriptor: https://learn.microsoft.com/es-es/azure/architecture/patterns/publisher-subscriber


## Importante!!
El envío de la tarea considera la entrega de todas las etapas en simultáneo,
podemos entonces, crear un repositorio con varias ramas (branchs), cada una para cada etapa.

o en el repositorio, crear carpetas por separado, cada una para cada etapa.

Cada etapa debe poder ejecutarse por separado.
Se debe distinguir claramente que branch/carpeta, corresponde a cada etapa

## Modelo a implementar
Clases:
    - Publicador
    - Suscriptor:

Publicador: 
    - Streamer. 
Suscriptores: 
    - Seguidor: Escribe los mensajes de su Streamer en un archivo de salida 

Publicador: 
    - GPS. 
Suscriptores:
    - Registrador: Almacena las actualizaciones de posición en archivo CSV
    - Monitor: Reporta la posición cuando la distancia es mayor a 500, desde el (0,0) (Sistema cartesiano)

## Tareas básicas

- El programa recibe como primer y único parámetro el nombre del archivo de configuraciń (config.txt)

- Lectura de la configuración existente en "config.txt"
    formato: (publicador <nombre> <tópico>)|(suscriptor <tipo> <nombre> <tópico> <archivo>)

- Ingreso de eventos mediante el usuario, vía teclado.
    formato: <nombre del publicador> <mensaje>

- Print de la salida de un Seguidor (por terminal):
    formato: <nombre> <tópico> <notificación>

- Salida (a archivo CSV) de un Registrador:
    formato: <nombre>,<tópico>,<posicion_x>, <posicion_y>

- Creación de Makefile (para cada etapa)

## Etapa 1 - Streamer envía notificaciones a un Seguidor ( y las guarda)

Crear clases: Publisher, Subscriber, Follower, Broker

Clase Component, padre de Publisher y Subscriber

Broker: Administra los tópicos.

La configuración estará en la función *main* de *T1Stage1* (No lee archivo externo)

## Etapa 2 - GPS publica posiciones que almacena un Registrador

Crear clase Recorder (similar a Follower), graba su salida en formato CSV

GPS es instancia de Publisher, publica coordenadas *x y* (en ese formato) de la posición.

Se lee la configuración del Simulador, mediante archivo .txt

## Etapa 3 - Streamer envía notificaciones a dos suscriptores

Generalizar método setupSimulator (del programa previo)
para configurar un simulador que permite crear un streamer y dos seguidores de sus publicaciones.

Discriminar nombre del Publicador, si no existe, imprimir "Unkown Publisher"

## Etapa 4 - Número arbitrario de publicadores y suscriptores (cualesquiera)
[por escribir]

## Etapa 5 - Extra cŕedito
[por escribir]
