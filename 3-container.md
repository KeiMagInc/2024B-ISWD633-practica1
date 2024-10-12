# Contenedores
 
### Crear un contenedor
Para crear un nuevo contenedor Docker a partir de una imagen específica, pero sin iniciarlo automáticamente. 

```
docker create --name <nombre contenedor> <nombre imagen>:<tag>
```
Crear el contenedor  **srv-web** usando la imagen nginx version alpine
```
docker create --name srv-web nginx:alpine
```
![image](https://github.com/user-attachments/assets/d210cc6a-8ddc-4ad5-aea2-e2186fdf231d)

Si creas un contenedor en Docker sin asignarle un nombre específico utilizando la opción --name, Docker asignará automáticamente un nombre aleatorio al contenedor. Este nombre suele consistir en una combinación de palabras y números.  

Crear el contenedor usando la imagen hello-world
```
docker create hello-world
```
![image](https://github.com/user-attachments/assets/9c255fed-032f-4d77-a2ee-5761a2251c0c)


### Listar los contenedores ejecutándose o no

```
docker ps -a
```

### Para iniciar un contenedor

```
docker start <nombre contenedor o identificador>
```
Iniciar el contenedor srv-web
```
docker start srv-web
```
![image](https://github.com/user-attachments/assets/50007dc6-45e8-4b59-8797-d7731a5cf299)


### Listar los contenedores ejecutándose
```
docker ps 
docker ps | grep <nombre contenedor>
```

### Para detener un contenedor

```
docker stop <nombre contenedor>
```

### Para crear un contenedor y ejecutarlo inmediatamente

```
docker run --name <nombre contenedor> <nombre imagen>:<tag>
```
![Ecosistema de Docker](img/dockerRun.PNG)

Crear y ejecutar inmediatamente el contenedor **srv-web2** usando la imagen nginx:alpine
```
docker run --name srv-web2 nginx:alpine
```
![image](https://github.com/user-attachments/assets/ef2afb47-2fb3-42da-b14b-3381dac26ef7)


**¿Qué sucede luego de la ejecución del comando?**
En primer lugar, se genera la ocnfiguración del contenedor. Después se ejecutan los script del archivo docker-entrypoint.d. Luego se lanza el servicio docker-entrypoint.sh que será usado. Finalmente, se descarga la imagen por el método epoll con la imagen nginx:alpine. El servicio queda como cron en la consola hasta que se cancela. 

Cuando ejecutas un contenedor en primer plano sin la opción -d (modo detach), el contenedor captura la entrada estándar (stdin) del terminal, lo que significa que el terminal queda "atrapado" y no puedes introducir más comandos hasta que detengas el contenedor.

### Para crear un contenedor y ejecutarlo inmediatamente sin estar vinculados al mismo
-d: Es la opción que indica a Docker que ejecute el contenedor en segundo plano (en modo "detach").
Cuando un contenedor se ejecuta en segundo plano, Docker devuelve el control al terminal inmediatamente después de iniciar el contenedor, lo que permite al usuario seguir ejecutando otros comandos en el mismo terminal sin que el contenedor detenga la interacción.

```
docker run -d --name <nombre contenedor> <nombre imagen>:tag
```
Crear y ejecutar inmediatamente el contenedor **srv-web3** en modo detach usando la imagen nginx:alpine
```
docker run -d --name srv-web3 nginx:alpine
```
![image](https://github.com/user-attachments/assets/9cd5386b-2c3c-4aa3-85b6-1fdc9a10f052)


### Para eliminar un contenedor

```
docker rm <nombre contenedor>
```
Eliminar el contenedor que se creó a partir de la imagen hello-world 
```
docker rm bd92fcc34b1f46ee8b61b4135efa35d42da0b535b89b7a1fd0258d0f5a59ba43
```
![image](https://github.com/user-attachments/assets/8072c15c-8838-453c-8363-4c4aa9f65adc)

Verificar que el contenedor que se eliminó
```
docker ps -a
```
![image](https://github.com/user-attachments/assets/989bafd4-8846-4455-a87d-3643a81f6a22)

### Para eliminar un contenedor que esté ejecutándose

```
docker rm -f <nombre contenedor>
```
Eliminar el contenedor **srv-web3** 
```
docker rm -f srv-web3
```
![image](https://github.com/user-attachments/assets/a3b513de-624d-4658-9951-44b0a0aa880b)


Verificar que el contenedor que se eliminó
```
docker ps -a
```
![image](https://github.com/user-attachments/assets/cd32d233-07bd-48ef-8279-9af69be479f5)

### Para inspecionar un contenedor 

Inspeccionar el contenedor **srv-web** 
```
docker inspect srv-web
```
![image](https://github.com/user-attachments/assets/c5a5da77-a0e0-421e-a2b6-c3394c604849)
![image](https://github.com/user-attachments/assets/7fd4d6cc-68a3-4de0-b18a-a787f08a394d)
![image](https://github.com/user-attachments/assets/f3849465-12fb-429f-956b-1440daa1ca39)
![image](https://github.com/user-attachments/assets/beaf4cad-48f3-496d-891b-b5210a87d3b8)
![image](https://github.com/user-attachments/assets/7ef876d2-8ba4-403c-b1d5-8228c5a4a9f2)
![image](https://github.com/user-attachments/assets/50d7402a-0caa-4477-b32e-0d99b28fc91a)
![image](https://github.com/user-attachments/assets/fa6090df-5a50-42a0-a296-ac013a38b4ea)
