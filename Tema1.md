# Ejercicios tema 1

### 1. Consultar en el catálogo de alguna tienda de informática el precio de un ordenador tipo servidor y calcular su coste de amortización a cuatro y siete años.


### 2. Usando las tablas de precios de servicios de alojamiento en Internet y de proveedores de servicios en la nube, Comparar el coste durante un año de un ordenador con un procesador estándar (escogerlo de forma que sea el mismo tipo de procesador en los dos vendedores) y con el resto de las características similares (tamaño de disco duro equivalente a transferencia de disco duro) en el caso de que la infraestructura comprada se usa sólo el 1% o el 10% del tiempo.

Para esta comparación he seleccionado dos servidores de 1&1.

|Tipo | RAM | Procesador | Disco duro | Precio|
|:----|:---:|:----------:|:----------:|------:|
|Dedicado|16 GB| 8 Cores | 1500GB|    119,99€/mes|
|Cloud|16 GB|8 Cores| 240GB| 0,181 €/hora|

El servidor dedicado siempre tiene el mismo precio anual, **1439,88€**
En el caso del servidor cloud no ocurre lo mismo ya que teniendo en cuenta
que un año tiene 8760 horas obtenemos los siguientes precios:
- Para el 1% : 8760 horas * 0.01 * 0,181 €/hora = **15,86€**
- Para el 10% : 8760 horas * 0.1 * 0,181 €/hora = **158,56€**

### 3.1. ¿Qué tipo de virtualización usarías en cada caso? Comentar en el foro


### 3.2. Crear un programa simple en cualquier lenguaje interpretado para Linux, empaquetarlo con CDE y probarlo en diferentes distribuciones.


### 4. Comprobar si el procesador o procesadores instalados tienen estos flags. ¿Qué modelo de procesador es? ¿Qué aparece como salida de esa orden?


### 5.1. Comprobar si el núcleo instalado en tu ordenador contiene este módulo del kernel usando la orden kvm-ok.


### 5.2 Instalar un hipervisor para gestionar máquinas virtuales, que más adelante se podrá usar en pruebas y ejercicios.
