!!! FLEXBOX !!!.-
En Julio del 2009, ahi es que se comienza ha hablar de flexbox, y no es hasta los años finales del año 2012 cuando en los primeros navegadores Chrome, Firefox se empieza a implementar el modulo de flexbox, gracias a este modulo de maquetacion es que podemos hacer diseños y prpruestas muy interesantes.

Flexbox es un sistema unidimencional, es decir, que vamos a tener filas o columnas pero no las dos al mismo tiempo, si nos filas no pueden ser columnas, si no columnas no podemos tener filas. 
Flexbox tiene varias propiedades unas son aplicadas a elemento padre y otras a los elementos hijos, mas o menos son unas 11 propiedades que hay que entender:

1)display.- Con display tenemos 2 valores, este display se agregar siempre al padre al container padre:
  -flex.- Lo que hace esta prop es que le comportamiento por default de los hijos de una caja flexbox se van a alinear y la direccion por defecto es horizontal en fila. Importante es una caja flexible que trabaja en bloque, es decir, si tenemos dos contenedores y colocamos display: flex se coloca uno debajo del otro porque al ser de bloque este ocupa todo el ancho disponible
  container1
  container2

  -inline-flex.- Es una caja flexible que trabaja inline osea los alinea en la misma linea cualquier contenedor, si tenemos dos conetendor y colocamos un display: inline.flex estos se van a alinear en la misma linea, al ser de linea este ocupa todo el ancho disponibleque necesite su contenido osea el ancho que ocupen sus elementos hijos
  container1 container2