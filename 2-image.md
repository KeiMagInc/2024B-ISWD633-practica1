# Imagen
Es un archivo único que contiene todos los programas, librerías, dependencias y configuraciones necesarias para instalar y/o ejecutar una aplicación o un conjunto de aplicaciones.
![Imagen](img/imagen.PNG)


## ¿Cuál es la relación entre una imagen y un contenedor? 
La imagen permite funcional al contenedor. Una imagen puede instalar y/o ejecutar en varios contenedores. Es decir, la imagen es el contenido que se visualiza o utiliza, mientras que el contenedor es el espacio, formato o estructura que la envuelve y le da contexto o funcionalidad en el entorno donde se presenta o ejecuta.

![Imagen y contenedores](img/imagenContenedores.JPG)
## Comandos para imágenes

### Descargar imagen
Descarga la última versión de la imagen disponible en el registro de Docker.

```
docker pull <nombre imagen> 
```

Descarga una versión específica de la imagen, cada imagen tiene etiquetas (tags) para diferentes versiones.
Una imagen puede tener la etiqueta latest para representar la última versión, si no se especifica una etiqueta se hará referencia a la versión latest.

```
docker pull <nombre imagen>:<tag>
```
Descargar la imagen **hello-world**
```
docker pull hello-world
```
![image](https://github.com/user-attachments/assets/58f9c43b-9ff0-415f-9161-d65a5b3da569)


**¿Qué es nginx?**
Es un servidor web de código abierto y proxy inverso especializado en web sockets.

Descargar la imagen  **nginx** en la versión **alpine**
```
docker pull nginx:alpine
```
![image](https://github.com/user-attachments/assets/b3249e16-8195-4c84-9f9c-d5170b9467b7)


### Listar imágenes

```
docker images
```

![image](https://github.com/user-attachments/assets/712d3229-614a-48aa-9563-8e5bd30e692a)


**Identificadores**

En Docker, se utilizan varios identificadores para diferenciar de manera única los elementos del sistema, como imágenes, contenedores, volúmenes y redes. Estos identificadores son generados automáticamente por Docker y son únicos dentro del contexto del sistema Docker en el que se encuentran. 

### Inspeccionar una imagen
El comando docker inspect se utiliza para obtener información detallada sobre un objeto de Docker específico, como un contenedor, una imagen, un volumen o una red.  Proporciona información en formato JSON sobre el objeto especificado.

```
docker inspect <nombre imagen>
docker inspect <nombre imagen>:<tag>
```

Inspeccionar la imagen hello-world 
```
docker inspect hello-world
```
![image](https://github.com/user-attachments/assets/0a431f67-bf61-45a8-a22e-06ba26a885c1)
![image](https://github.com/user-attachments/assets/8bc4fbfd-3317-40ae-8de7-8a05e23df6bb)
![image](https://github.com/user-attachments/assets/6dd66836-7b85-4a97-9d16-20cd96be537c)
![image](https://github.com/user-attachments/assets/cf726890-8429-4e1a-9b2c-7b67f0514fce)



**¿Con qué algoritmo se está generando el ID de la imagen?**
Se está generando cno el algoritmo SHA256. Este algoritmo es un algoritmo tipo HASH, es decir, se toman datos de la imagen y los pasa 256 bits, de modo que el ID siempre será único.

### Filtrar imágenes

```
docker images | grep <termino a buscar>

```

### Para eliminar una imagen
Eliminar permanentemente la imagen de tu sistema Docker.

```
docker rmi <nombre imagen>:<tag>
```

Eliminar la imagen hello-world 
```
docker rmi hello-world
```
![image](https://github.com/user-attachments/assets/f81f9316-c3ad-4280-91dd-e15c84dca804)


-f: Es la opción para forzar la eliminación de la imagen incluso si hay contenedores en ejecución que utilizan esa imagen.
Cuando eliminas una imagen Docker, Docker no elimina automáticamente los contenedores que se han creado a partir de esa imagen. Esto significa que, aunque hayas eliminado la imagen, el contenedor seguirá ejecutándose normalmente.  
**Considerar**
Eliminar una imagen no afecta a los contenedores que se han creado a partir de esa imagen, a menos que esos contenedores dependan de archivos o configuraciones específicas de la imagen eliminada. En ese caso, es posible que los contenedores se comporten de manera inesperada después de eliminar la imagen.
Es una buena práctica detener y eliminar todos los contenedores que dependan de una imagen antes de eliminar la imagen en sí.

```
docker rmi -f <nombre imagen>:<tag>
```

