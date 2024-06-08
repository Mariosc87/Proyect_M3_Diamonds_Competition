# PROYECTO COMPETICIÓN PRECIO DE DIAMANTES

## ¿Quien quiere participar en un juego para aproximarte al valor de miles de diamantes random?

Con este proyecto lo que se pretende es que tu puedas intentar averigual el valor de unos diamantes, simplemente con un dataset que contiene once columnas de informacion y más de cuarenta mil filas de diamantes. Tu debes averiguar el precio de estos, simplemente con el tratamiento de los datos.

![Image](img/diamantes.jpg)

El proyecto se encuentra aún en su fase Beta. Aún se sigue mejorando para poder acercarnos mas al precio real de estos diamantes.

## Índice

* Título e imagen de portada

* Estado del proyecto

* Índice

* Descripción del proyecto
  
* Conclusion

* Acceso al proyecto

* Tecnologías utilizadas

* Personas-Desarrolladores del Proyecto

* Contribuciones

### Descripcion del proyecto.

Para realizar este proyecto lo que he tenido que hacer para empezar, crear una conexión con el archivo .db, elijo para ello sqlite3. Cargo y convierto los datos de cada tabla en diferentes DataFrames y cierro la conexión.

Lo siguiente que realizo es unir estos dataframes en una sola tabla con la ayuda de la funcion pd.merge(). Y la guardo en un csv.

Ya tengo todos los datos que necesito en una tabla, por lo que el siguiente paso sería crear dos notebook diferente uno de entrenamiento y otro de test.

En el notebook de entrenamiento cargo el csv de train y con pandas visualizo los datos que tengo. 11 columnas y más de 40000 filas.

Lo primero es hacer una limpiez de datos, este dataset afortunadamente no tiene ni un solo nulo en ninguna fila. Por lo que me voy directamente a tratar las columnas categóricas del dataset, y son cuatro: city, color, cut y clarity. Tengo que pasar estas cuatro columnas a números y finalmente con el metodo que mejor resultado obtengo es con el "Label Encoding". Con el label encoding tras tatar los datos mucho decido eliminar la columna city. Los datos de las otras columnas establezco números aleatorios para darles valor numérico. Con el "Hot encoding" consigo resultados muy parecidos pero peores, por lo que lo desecho.

Ahora lo que quiero tratar son las columnas numéricas, sin tocar la columna "price". Son estas: carat, depth, table, x, y, z. Hago "Scaling" con los datos de estas columnas y para mi sorpresa, los resultados fueron perores con el tratamiento de scaling que sin el tratamiento de estos datos.

Me creo la variable "X" que la asigno todas las columnas a excepción de "price" y también creo la variable "y" que le asigno el target, es decir, la columna "price" y entreno los datos, obteniendo valores para x_train, x_test, y_train e y_test pero sólo del 80% del total.

Y es hora de elegir el modelo, el mio será "RANDOM FOREST", tras probar diferentes modelos e intentar otros que no logre hacer, fue el que mejor resultado me dio.

Y guardo el modelo con la librería pickle.

Ahora abrimos ahora el notebook de Test y cargamos el csv de test. Copiamos todo el tratamiento de datos del notebook de Train y abrimos el modelo que hemos guardado.

Tenemos que realizar la predicción de los datos, cargando el modelo guardado y haciendo la prediccion sobre el dataframe al que le hemos tratado los datos. Con esto creamos un array de numpy y lo transformamos en un dataset. Nombramos la columna creada del array con el nombre de "price" (tiene que ser el mismo nombre al target) y creamos tambien una columna id que simplemente sea la posición de la fila en la tabla.

Esto lo guardamos en un csv y este sera el que comparemos en la submission y nos diga la diferencia de dolares que nos da.

### Conclusión.

En mi caso mi conclusión es que el complicarme con el tratamiento de datos sólo me ha dado problemas y no he conseguido nada con ello. Lo más simple es lo que a mi me ha funcionado.

### Acceso al proyecto.

* Clona este repositorio en tu máquina local.
* Navega al directorio del proyecto.
* Y modifica los datos a tu antojo.
* La estructura ya esta creada.
* O comprueba el modelo que esta hecho aqui.

### Requisitos del sistema.

* Python 3.x instalado en tu sistema.

* Conexión a internet para la recuperación de datos en tiempo real.

### Personas_Desarrollador del proyecto y Licencia.

El desarrollador de este proyecto es Mario S C.

Este proyecto está bajo la Licencia MIT.

### Contribuciones.

Las contribuciones son bienvenidas. Si deseas mejorar la aplicación, por favor:

* 1- Haz un fork del repositorio.

* 2- Y crea un pull request en el repositorio original.
