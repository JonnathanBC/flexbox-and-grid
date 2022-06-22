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
    Porque si los estamos en row y le damos un flex start seria de izq a der, pero si estamos en column seria de arriba hacia abajo, igual si estamos en row y flex-end seria de der a izq, si estamos en columna seria de abajo hacia arriba siempre alineara en el eje principal pudiendo ser row o column, si estamos en row y center seria del centro para los lados y si estamos en column y center seria del centro hacias arriba y abajo.

    -justify-content.- Este tiene los valores de:
      -flex-start.- que es el por defecto que tiene es como un float: left, alinea desde la izq a der
      -flex-end.- es como un float: right, alinea desde la der a izq
      -center.- Alinea al centro, alinea desde el centro para afuera
      -space-between.- Coloca espacios entre items, osea va a ignorar las orillas de la caja contendora y el espacio que sobra lo va a repartir entre los elementos interno (hijos), osea los alinea desde las orillas y ocupa todo el espacion segun el contenido separado por espacios izq a der

      -space-around.-  Es similiar al space-between solo que este si considera las orillas, sin embargo las orillas van a ser a la mitad de los elementos interno, es decir, da unos margenes a los lados y desde ahi comienza a alinerar de izq a dre, ojo solo da el espacion proporcional a un elemento

      -space-evenly.- Le da el mismo valor a las orillas a los elementos internos.

  ALINEACION DEL CROSS AXIS (align-items y align-content).- Nos srive para alinear el eje cross, el vertical o dependiendo puede ser x o y.

  align-items.- Este alinea los hijos independientemente es decir segun el numero de filas que tenemos, en cambio el justify-content alinea en conjunto es decir se lleva todas la filas o columnas, el valor por defecto es strech pero tenemos los sig valores:
    -flex-start.- Respecto de y la alineacino es arriba
    -flex-end.- Respecto de y la alineacion es abajo
    -center.- Respecto de y la alineacino es en el centro
    -stretch.- Por defecto los hijos en una caja flexbox en el eje transversal, se van a estirar al tamaño del conetnedor padre.

    -baseline.- Define cual es la linea imaginaria base de todo el texto, es decir, tenemos una 3 cajas y estas cajas tienen texto dentro, esta propiedad nos hace que los textos este a la misma altura en linea.

  align-content.- Este es parecido al justify-content con la diff que este funciona para el eje cross pero este si alinea todo en conjunto no independientemente. Este no funciona cuando tenemos el valor de no wrap, funcionara con el cuandop tenemos el wrap porque trabaja por grupo. Align content no funciona cuando esta en una sola linea. es decir cuando el flex-wrap: no wrap ahi no funciona. Siempre que no funcione estiraminetos, ventrados, valores de ancho al 100% al usar el strecth debemos de siempre revisar si si los hijos tienen algun valor de height o width dependiendo si es row o column si direccion.Teniendo en cuenta que row obecede a height ennhijos y el column al width.
    -flex-start.-
    -flex-end.-
    -center.-
    -stretch.-
    -space-between.-
    -space-around.-
    -space-evenly.-

*PROPIEDADES QUE VAN A LOS HIJOS.-
  -FLUJO DE CRECIMIENTO.-
    -flex-grow.- por defecto es 0, cuando la caja flexbox tiene espacio sobrante los hijos podran hacer uso de ese espacio sobrante, flex-grow es la habilidad p factor de crecer no acepta valores negativos (-1 -2 etc). Se reparte todo el espacio de manera proporcional iguales a los elementos hijos.
    
    calculos: Si tenemos 3 elementos y un contenedor con acho de 1000px y los hijos con un ancho de 100px serian los calculos de la sig manera:
    si le damos un flex-grow: 1 todos mediran 333.333 divide de manera proporcional.
    si le damos un flex:grow: 1, y al elemento 2 un flex-grow: 2, pues tenemos el primer y tercer elemento con 1 y el segundo con 2, el calculo seria de todo el sobrante que tenemos, de 1000 tenemos 3 elemntos de 100 pues sobra 700px en el contenedor esos 700px se dividen para 4 en este caso, porque, porque tenemos 3 elementos pero uno de ellos es dos seria item 1(1) + item2 (2) + item(3)(1) = 4, los 700 se divide para 4 nos daria un valor de 175px y le tenemos que sumar el valor de 100px que tiene cada caja seria 175 + 100 = 275 para los item que tienen el flex-grow: 1 y para calcular del iitem 2 con el flex-grow: 2 a esos 275 tenemos que sumarle 175 porque es lo que obtenemos del resultado de la division de 700 para 4 275+175 = 450, entonces item 1 tiene 275 item2 tiene 450 y el item 3 tiene 275.

    Otro ejm.
    contendor de ancho 1000 e items de ancho 100, el item 1 flex-grow: 1, item 2 flex-grow: 3, item: 3 flex-grow: 2, igual sumamos los flex-grow que tiene cada item 1 + 3 +2 = 6, 6 se divide para 700 que es sobrante nos da 116.66, se suma los 100 que tiene cada item de ancho 116.66 + 1000 = 216.666 aqui ya el item1 tiene 216.666, luego el item dos tiene grow de 3 le tenemos que sumar a los 216.66 2 veces el resultado de la division de el sobrante con los ocupantes que seria 116.66 + 116.66 + 216.66 = 449,98, el item 2 ya tiene el valor de 449,98, e igual para el ultimo item como tiene el grow de dos le tenemos que suma 1 vez 116.66 + 216.66 = 333,32 enotces quedaria de la sig manera 
    item 1 flex-grow: 1 => 216.66
    item 2 flex-grow: 3 => 449.98 => 450
    item 3 flex-grow: 1 => 333.32

    //Ejemplo css del ultimo ejercicio
    container {
      width: 1000px
    }

    .item {
      ...code
      width: 100px
      flex-grow: 1
    }

    .item:nth-child(2) {
      flex-grow: 3;
    }

    .item:nth-child(3) {
      flex-grow: 2;
    }

    FACTOR DE REDUCCION.-
      -flex-shrink.- por defecto es 1, Cuando la caja flexbox NO tenga espacio sobrante, es la habilidad o el factor de encogerse e igual no se aceptan valores negativos.
      Es decir lo elementos si tenemos una caja al 100% y los hijos que tienen el flex-shrink: 1 que es su valor por dfecto esto se van encogiendo si hacemos mas pequeña la pantalla del navegador, llega a un punto donde no caben mas y se empiezan ha hacer como "responsivos", y si tenemos en 0 el valor pues pirden la "responsividad" y nos genera ya la barra de scroll abajo. Funciona igual que el flex-grow solo que este es al contrario reduce igual se reducen con calculos no exactamente a la mitad en relacion al container padre.

      //CALCULO.-
      Tenemos una caja al 100% de witdh, y 3 hijos con 79.78 de width, el primer hijo con el flex-shrink: 1, el 2do hijo con el flex-shrink:2 y el 3er con el flex-shrink: 1
      Se calcula en base al contenedor, es decir, lo que mide cada hijo 79.78 * el numero de hijos 3 = 239,34 aqui no hay problema pero en el hipotetico caso que el contenedor mida 220, restamos los 239.34 - 220 = 19.34, entonces cada hijo se reducira 19.34, entonces el valor que tenemos de resta osea lo que cada hijo debe reducirse pues tenemos que dividir para los hijos que son teniendo en cuenta el flex-shrink, osea el 1 tiene 1, el 2 tiene 2, y el 3 tiene 1 osea sumamos los flex-shrink y nos daruia 4 entonces tenemos que dividir eso para 4 (19.34 / 4 = 4.835) entonces el hijo 1 y 3 que son flex-shrink: 1 tiene el valor de reduccio de 4.835. Para calcular el que tiene flex-dshrink: 2 seria el 4.835 multiplicado por 2 (4.835 * 2 = 9.67). Ya teniendo estos calculos al valor inicial debemos restarles estos valor 

      Cuando el padre mide 220px
      hijo 1 => 79.78 - 4.835 = 74.945 => 75
      hijo 2 => 79.78 - (4.835 * 2 = 9.67) = 70.11  
      hijo 3 => 79.78 - 4.835 = 74.945 => 75

      Asi se hace el calculo de eso. Segun los hijos que tengan el flex-shrink: 1 2 3 etc.

    -flex-basis.- por defecto es auto, es el tamaño del elemento hijo dentro de la linea de la caja flexbox, si la caja flexbox tiene una direccion de fila, flex-basis representa el width(ancho), si la caja esta en columna flex-basis representa el height(alto). Cuando tenemos una propiedad flex-basis y la direccion en row ignorabcompletamente la propiedad width asi tenga poir cascada mas valor lo ignora por completo asi le pongamos en width de 500px y u flex-basis: 100 siempre se quedara con el valor de 100px dado en el baisis. e igual cuando la direccion es column solo que en el height

    Tenemos unn atajo que nos ahorra escribir los flex-grow o flex-shrink o flex-basis se llama flex, y van en ese orden, el valor primero es el de grow, el segundo es el del shrink y el tercero en el basisi:
    flex: 0 1 300px.

      ORDEN Y ALINEACION DE HIJOS (order y align-self).-
        order.- Nosotro podemos invertir el orden de los elementos, esta propiedad orden nos va a controlar el orden, osea representa el orden que tendran los elementos hijos en la cja flexbox su valor por defecto es 0 y se aceptan valores negativos o positivos, un valor menor siempre ira antes que un valor mayor.

        Esto funciona cuando nosotros damos un orden a los elementos hijos de los hijos, es decir, si le damos al item un orden de 0 todo lo de item tendra un mismo orden, pero si al item en su segundo hijo le damos un orden de 1 se ira al final y si le colocamos - 1 se ira al inicio ejm:
        En el hipotetico caso que tengamos 5 item con la clase item pues los 4 items tendra el order de 0 y como vemos en el ejm de abajo tenemos el 2 elemento osea item2 este se pasara al funal y tendremos lo sig
        item 1 - item-3 - item-4 - item-5 - item-2

        y si le pasamos a un orden de -1 pues quedaria asi
        item-2 - item 1 - item-3 - item-4 - item-5

        .item {
          order: 0
        }

        .item:nth-child(2) {
          flex-grow: 3; */
          flex-shrink: 2; */
          order: 1;
        }

        align-self.- Es la propiedad de los hijos, esto nos sirve cuando queremos que un elemento tenga una alineacion distinta al resto de hermanos o hijos. Su valor por defecto es stretche igual toma los mismo valores que align-items flex-start flex-end etc etc.Este sobre escribe el valor que tenga align-items. COmo su nombre lo dice alineate tu mismo, funciona o se ve cambios cuando en el mismo ejem del order el damos un align-.self al tercer item de los 5 pues este si se moveria:

        .item:nth-child(3) {
          flex-grow: 2;
          align-self: flex-start;
        }
        El tercer elemento se alineara arriba solo ese.