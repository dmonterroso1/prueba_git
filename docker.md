`docker images` -> Muestra todas las imágenes descargadas.

`docker search` -> Busca una imagen por su nombre

---
`docker pull ubuntu` -> Descarga la imagen

`docker run -it ubuntu bash`

`docker run ubuntu echo 'Hello world'`

`docker pull node:18`

`docker pull mysql`

`docker pull --plataform linux/x86_64 mysql` (por si da error en apple)

---
`docker create mongo` -> Crea un contenedor a la partir de la imagen descargada

`docker create --name monguito mongo`

`docker start monguito` -> Inicia el contenedor con dicho nombre

`docker start _idContenedor_`

`docker stop _idContenedor_` (puede usarse id o name)

---
`docker run ...` -> Si la imagen no está descargada, se descarga y se ejecuta, posteriormente crea un contenedor a partir de la imagen descargada (un contenedor es una capa o instancia de una imagen)

`docker run httpd` (imagen de apache)

`docker run -d -p 3307:3306 --name mydatabase mysql` -> Descarga y ejecuta la imagen de mysql en el puerto 3307

---
Ejecutar varias instancias de la misma imagen:

`docker run -p 3000:80 nginx`

`docker run -p 4000:80 nginx`

`docker run -p 5000:80 nginx`

**-d** -> para no dejar la terminal ejecutandose

`docker run -p 3000:80 -p 4000:80 -p 5000:80 -d nginx`


---
`docker ps` -> Muetra los contenedores en ejecución

`docker ps -a` -> Muestra todos los contenedores y su estado

`docker rm _idContenedor_ ` -> Elimina el contenedor

`docker rm _name_` 

`docker rm node:16` (elimina la imagen por nombre y versión)


---
`docker run -d -p 80:80 --name website -v $(pwd):/usr/share/nginx/html:ro nginx` -> Copia un directorio (pwd) a un contenedor de nginx


---
**Crear una propia imagen en base a un dockerfile**

`docker build -t _etiqueta/nombre_ . `

(Con `docker images` debería aparecer la imagen creada)


---
**Red en docker**

Cuando se comunica un contenedor con otro contenedor que están en una red, se tiene que cambiar el "localhost" por el "name" del contenedor.

`docker network ls`

`docker network create mired`

`docker network rm mired`

---
---
---
>`docker create -p27017:27017 --name monguito --network mired -e MONGO_INITDB_ROOT_USERNAME=nico -e MONTO_INITDB_ROOT_PASSWORD=password mongo`

>`docker create -p3000:3000 --name chanchito --newtowrk mired miapp:1 `

>`docker start monguito`

>`docker start chanchito`
