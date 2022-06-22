!!! FLEXBOX !!!.- css-tricks.com/snippets/css/a-guide-to-flexbox/
En Julio del 2009, ahi es que se comienza ha hablar de flexbox, y no es hasta los años finales del año 2012 cuando en los primeros navegadores Chrome, Firefox se empieza a implementar el modulo de flexbox, gracias a este modulo de maquetacion es que podemos hacer diseños y prpruestas muy interesantes.

Terminologia basica.-
Vamo a tener nuestro contenedor o mas conocido como flex container, los elementos hijos comunmente llamados flex item, y vamos a tener dos ejes el eje principal llamado main axis (eje x horizontal), y el eje transversal cross axis (eje y vertical), aunque existe una propiedad de css que nos permite cambiar y colocar el cross axis como principa, y el main axis como secundario o transversal

Flexbox es un sistema unidimencional, es decir, que vamos a tener filas o columnas pero no las dos al mismo tiempo, si nos filas no pueden ser columnas, si no columnas no podemos tener filas. 
Flexbox tiene varias propiedades unas son aplicadas a elemento padre y otras a los elementos hijos, mas o menos son unas 11 propiedades que hay que entender:

*PROPIEDADES QUE VAN AL PADRE:

  1)display.- Con display tenemos 2 valores, este display se agregar siempre al padre al container padre:
    -flex.- Lo que hace esta prop es que le comportamiento por default de los hijos de una caja flexbox se van a alinear y la direccion por defecto es horizontal en fila. Importante es una caja flexible que trabaja en bloque, es decir, si tenemos dos contenedores y colocamos display: flex se coloca uno debajo del otro porque al ser de bloque este ocupa todo el ancho disponible
    container1
    container2

    -inline-flex.- Es una caja flexible que trabaja inline osea los alinea en la misma linea cualquier contenedor, si tenemos dos conetendor y colocamos un display: inline.flex estos se van a alinear en la misma linea, al ser de linea este ocupa todo el ancho disponibleque necesite su contenido osea el ancho que ocupen sus elementos hijos
    container1 container2

  2)flex-direction.- Propiedad se agrega al padre siempre y de esta tenemos 4 valores por defecto:
    -row.- Va en fila de inicio a fin (izq a der) row es el valor por defecto asi no se haya escrito la prop de direccion
    -row-reverse.- invierte la fila de fin a inicio (der a izq)
    -column.- Va en columna inicia de arriba hacia abajo
    -column-reverse.- invierte la columna inicia de abajo hacia arriba.

  3)flex-wrap.- Esta propiedad nos dice si los elementos se van a alinear en una sola fila, porque este toma en cuenta el ancho que tengan los hijos. teniendo en cuenta que cuando damos el flex estos por defecto los hijos se ira colocando en linea sin importar el ancho seguiran siempre al infinito. Tenemos tambien algunos valores:
    -nowrap.- Este valor es por defecto, pues es por que no toma el ancho de los hijos y los coloca siempre en linea hasta el infinito, este cuando ya nos se pueden achicar mas lo hijos este genera la barra de scroll lateral por lo que nunca perder su direccion inline.
    Si nosotros tenemos propiedades de medida en alto o ancho este nowrap las ignara por completo, siempre tomara su 100% del contenido infinito, porque el espacio  se va encogiendo

    container {
      display: flex;
      flex-direction: row;
      flex-wrap: nowrap;
    }

    item {
      width: 20%
    }
    Como vemos en este ejm el no wrap lo ignora por completo y tomara todo el ancho infiinito

    -wrap.- Va a envolver los hijos, este si va a conciderar el tamaño de los hijos entonces cuando llegue a limite y el hijo no cabe en la misma linea entonces este lo colocara debajo y va a generar varias filas, es decir pierde su inline hasta el tamaña de la caja padre.
    Nota cuando tenemos la direccion en row en fila los element y el flexdirection en wrap, cuando es una fila este toamara el valor del width para su "grid", si tenemos en columna pues toma el height para su "grid"

    -wrap-reverse.- hace lo mismo que el wrap si no que de fin a incio (de der a izq)
    Todo esto que hemos visto del flex-direction y del flex-wrap es lo que se conoce como el flujo de la caja, es decir como se van a comportar dentro los elementos hijos, para esto tenemos como un atajo para estas dos porpiedades que es el flex-flow: flex.direction_valor flex-wrap_valor, el primer valor seria para la direccion y el segundo para el wrap ejm:
    flex-flow: row wrap

    Siempre en css los estilos son en cascada, es decir el ultimo declarado ese tomara como valor siempre.

    ALINEACION DEL MAIN AXIS.- Tenemos 3 elementos que nos permitira alinearlos y como distribuirlos dentro de dicha caja flexbox. Teniendo en cuenta por defecto el eje principal es horizontal, pero tambien como podemos cambiar con el flex-direction sea row seria horixontal principal si colocamos colomn y seria el principal, osea la alineacion en eje principal depende del eje principal que le hayamos dado con el flex-direction y la alineacion lo hara en base al espacio sobrante que quede en la caja padre.
    Porque si los estamos en row y le damos un flex start seria de izq a der, pero si estamos en column seria de arriba hacia abajo, igual si estamos en row y flex-end seria de der a izq, si estamos en columna seria de abajo hacia arriba siempre alineara en el eje principal pudiendo ser row o column, si estamos en row y center seria del centro para los lados y si estamos en column y center seria del centro hacias arriba y abajo

    -justify-content.- Este tiene los valores de:
      -flex-start.- que es el por defecto que tiene es como un float: left, alinea desde la izq a der
      -flex-end.- es como un float: right, alinea desde la der a izq
      -center.- Alinea al centro, alinea desde el centro para afuera
      -space-between.- Coloca espacios entre items, osea va a ignorar las orillas de la caja contendora y el espacio que sobra lo va a repartir entre los elementos interno (hijos), osea los alinea desde las orillas y ocupa todo el espacion segun el contenido separado por espacios izq a der

      -space-around.-  Es similiar al space-between solo que este si considera las orillas, sin embargo las orillas van a ser a la mitad de los elementos interno, es decir, da unos margenes a los lados y desde ahi comienza a alinerar de izq a dre, ojo solo da el espacion proporcional a un elemento

      -space-evenly.- Le da el mismo valor a las orillas a los elementos internos.

