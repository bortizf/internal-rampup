# Ejecución de cada microservicio

Para evitar que los entrenadores tengan que estar escribiendo los comandos completos con la redirección de cada API, se les presenta este documento con un resumen de esos comandos. Cabe aclarar que en este punto se asume que ya se tienen todas las dependencias instaladas y se ha compilado cada aplicación (Leer el README.md de cada microservicio para más detalles).  

Estas ejecuciones se pueden hacer si se quiere correr toda la aplicación en una sola terminal. Alternativamente, se pueden abrir 5 terminales y dejar cada microservicio corriendo en foreground.  

Antes de ejecutar los siguientes comandos, crear una carpeta donde almacenar los logs. En este caso se hará en el $HOME/logs.
```bash
mkdir $HOME/logs
```

## Users API

```bash
JWT_SECRET=PRFT SERVER_PORT=8083 java -jar target/users-api-0.0.1-SNAPSHOT.jar > ~/logs/users.out 2> ~/logs/users.err &
```

## Authentication API

```bash
JWT_SECRET=PRFT AUTH_API_PORT=8000 USERS_API_ADDRESS=http://127.0.0.1:8083 ./auth-api > ~/logs/auth.out 2> ~/logs/auth.err &
```

## TODOs API

La parte inicial antes del | se debe a que este microservicio queda esperando datos por la entrada estándar. Actualmente esta fue la solución que se encontró, sin embargo se está trabajando en buscar una mejor forma de hacerlo.  

```bash
( while true; do sleep 1000; done ) | JWT_SECRET=PRFT TODO_API_PORT=8082 npm start > ~/logs/todos.out 2> ~/logs/todos.err &
```

## Frontend API

```bash
PORT=8080 AUTH_API_ADDRESS=http://127.0.0.1:8000 TODOS_API_ADDRESS=http://127.0.0.1:8082 npm start > ~/logs/front.out 2> ~/logs/front.err &
```

## Log Message 

Este microservicio se puede dejar corriendo en foreground para poder observar su comportamiento: que imprima los eventos de CREATE y DELETE en la salida estándar. 
```bash
REDIS_HOST=127.0.0.1 REDIS_PORT=6379 REDIS_CHANNEL=log_channel python3 main.py
```