# Ejercicios tema 3


### 1. Darse de alta en algún servicio PaaS tal como Heroku, Nodejitsu, BlueMix u OpenShift.
Para darse de alta simplemente se rellenan los formularios de registro y se espera a una confirmación, no he probado el caso de Nodejitsu, y en el caso de BlueMix es necesario solicitar una cuenta de estudiante en caso de que no se quiera pagar.


### 2. Crear una aplicación en OpenShift o en algún otro PaaS en el que se haya dado uno de alta. Realizar un despliegue de prueba usando alguno de los ejemplos.
He realizado una prueba en Heroku dado que es la plataforma de la que he encontrado más información relevante para la configuración de mi proyecto.


### 3. Realizar una app en express (o el lenguaje y marco elegido) que incluya variables como en el caso anterior.
Parte de mi proyecto consiste en una API RESTful haciendo uso de Express, [aquí](https://github.com/antoniovj1/infraestructura_virtual_ugr/blob/master/app/routes/api_user.js)


### 4. Crear pruebas para las diferentes rutas de la aplicación.
En mi proyecto hay test para las diferentes rutas, se pueden consultar [aquí](https://github.com/antoniovj1/infraestructura_virtual_ugr/tree/master/test)


### 5. Instalar y echar a andar tu primera aplicación en Heroku.
Para este ejercicio he desplegado mi proyecto https://infraestructuravirtual.herokuapp.com/


### 6. Usar como base la aplicación de ejemplo de heroku y combinarla con la aplicación en node que se ha creado anteriormente. Probarla de forma local con foreman. Al final de cada modificación, los tests tendrán que funcionar correctamente; cuando se pasen los tests, se puede volver a desplegar en heroku.
Para este ejercicio he configurado un pipeline en el que se selecciona el repositorio que se desea desplegar y se le indica que se realice un despliegue automático después de los test. https://infraestructuravirtual.herokuapp.com/


### 7. Haz alguna modificación a tu aplicación en node.js para Heroku, sin olvidar añadir los tests para la nueva funcionalidad, y configura el despliegue automático a Heroku usando Snap CI o alguno de los otros servicios, como Codeship, mencionados en StackOverflow
Tras realizar varios push a la rama master de mi proyecto he podido comprobar que efectivamente se realiza el despliegue ( se puede ver en el dashboard de la app en heroku)


### 8. Preparar la aplicación con la que se ha venido trabajando hasta este momento para ejecutarse en un PaaS, el que se haya elegido.
Finalmente he configurado mi proyecto para que use una variable de entorno en la que se indica la URI de la base de datos mLab que he instalado haciendo uso de una extensión de heroku. El proyecto esta desplegado en https://infraestructuravirtual.herokuapp.com/


