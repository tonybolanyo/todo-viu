# todo-viu

Lista de tareas simple creada en VueJS para el seminario
"Introducción a la creación de aplicaciones web con VueJS"
impartido en la VIU.

La aplicación incluye un backend simple para desarrollo creado
con el paquete [JSON-Server](https://github.com/typicode/json-server) que no está pensado para usar en producción, es decir,
solamente se proporciona como una forma simple de desarrollar
la aplicación frontend sin necesidad de un desarrollo de un
servidor con una API REST dedicada.

JSON Server guarda los datos en el un archivo `json` y permite
operaciones estándar a través de una API REST.

Para comenzar a desarrollar o simplemente inspeccionar el
funcionamiento sigue los siguientes pasos:

1. Instala las dependencias necesarias

```shell
yarn install

npm install
```

2. Arranca el backend con JSON Server

```shell
yarn backend

npm run backend
```

3. Arranca el frontal con el servidor de desarrollo.
   El servidor de desarrollo soporta hotreloading.

```shell
yarn serve

npm run serve
```

En condiciones normales, el backend estará disponible en
`http://localhost:3000` y podrás acceder a las tareas a través
del endpoit `http://localhost:3000/tasks` y la aplicación
frontal en `http://localhost:8080`. Ten en cuenta que si
tienes otros servicios funcionando en esos puertos debes
cambiar la configuración de los comandos en el archivo
`package.json` o parar los servicios que ocupan esos puertos.

## Compilar para producción

```shell
yarn build

npm run build
```

### Para usar el linter y escanear los archivos

```shell
yarn lint

npm run lint
```

### Más configuraciones de VueJS

See [Configuration Reference](https://cli.vuejs.org/config/).
