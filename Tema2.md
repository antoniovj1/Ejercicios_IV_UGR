# Ejercicios tema 2

### 1. Instalar alguno de los entornos virtuales de node.js (o de cualquier otro lenguaje con el que se esté familiarizado) y, con ellos, instalar la última versión existente, la versión minor más actual de la 4.x y lo mismo para la 0.11 o alguna impar (de desarrollo).

```
//Instalamos nmp
$ sudo pacman -S npm

//Instalamos las diferentes versiones de express.js
$ npm install express
$ npm install express@4.x
$ npm install express@4.11.x

```

### 2. Como ejercicio, algo ligeramente diferente: una web para calificar las empresas en las que hacen prácticas los alumnos. Las acciones serían:

Como solución a este ejercicio se puede ver el [proyecto](https://github.com/antoniovj1/infraestructura_virtual_ugr) aunque es un poco más complejo.


### 3. Ejecutar el programa en diferentes versiones del lenguaje. ¿Funciona en todas ellas?


### 4. Crear una descripción del módulo usando package.json. En caso de que se trate de otro lenguaje, usar el método correspondiente.
Para iniciar un archivo package.json usamos `npm init` y obtenemos un archivo con la siguieten estructura:
```json
{
  "name": "antonio",
  "version": "1.0.0",
  "description": "",
  "main": "index.js",
  "scripts": {
    "test": "echo \"Error: no test specified\" && exit 1"
  },
  "author": "",
  "license": "ISC"
}

```

### 5. Automatizar con grunt, gulp u otra herramienta de gestión de tareas en Node la generación de documentación de la librería que se cree usando docco u otro sistema similar de generación de documentatión. . Previamente, por supuesto, habrá que documentar tal librería.

En lugar de usar grunt he decidido usar `WebPack`, un ejemplo de archivo de configuración sería el siguiente:
[Archivo de configuración](https://github.com/antoniovj1/infraestructura_virtual_ugr/blob/master/webpack.config.dev.js)


### 6. Para la aplicación que se está haciendo, escribir una serie de aserciones y probar que efectivamente no fallan. Añadir tests para una nueva funcionalidad, probar que falla y escribir el código para que no lo haga (vamos, lo que viene siendo TDD).
Un trabajo similar se ha realizado en [los tests del proyecto](https://github.com/antoniovj1/infraestructura_virtual_ugr/tree/master/test)

### 7. Convertir los tests unitarios anteriores con assert a programas de test y ejecutarlos desde mocha, usando descripciones del test y del grupo de test de forma correcta. Si hasta ahora no has subido el código que has venido realizando a GitHub, es el momento de hacerlo, porque lo vas a necesitar un poco más adelante.

Para realizar test he creado una serie de archivos con `Chai` que tienen la siguiente estructura [archivo chai](https://github.com/antoniovj1/infraestructura_virtual_ugr/blob/master/test/session.js), luego estos test son ejecutados por `Mocha` que nos proporciona una salida indicando lo que funciona y lo que no.

```shell
. . . . . . 

    /POST 
      ✓ should not POST an user without username field
      ✓ POST an user  (287ms)
      
    /GET/:user_id
      ✓ should GET a user by the given id (379ms)
      
    /PUT/:user_id
      ✓ it should UPDATE a user given the id (436ms)
      
    /DELETE/:user_id
      ✓ should DELETE a user given the id (358ms)
      
  30 passing (9s)
