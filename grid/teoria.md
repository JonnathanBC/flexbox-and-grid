!!! GRID CSS !!!.- Con grid por fin tenemos un sistema bidireccional osea que podemos tener columnas y filas para maquetar al mismo tiempo a diff de flexbox que es unidireccional porque tenemos bien filas o columnas pero no las dos.
Flexbox es para alinear los elementos internos de un componente de UI.
A grid css lo empezaron  a soportar en 2017. En grid tambien tenemos algunos conceptos a entender por ejm:

-Grid Container (Contenedor Padre).- Al que se le aplica el display: grid
-Grid Items (Elementos Hijos).- Estos son como nuestras celdas.
-Grid Lines (Lineas de Cuadricula).- Son la lineas divisiorias entre columnas por ejm si tenemos una grid de 5 * 5 las lineas de cuadricula seran de 6 * 6.

-Grid Track (Pistas de Cuadricula).-Es como toda una fila o toda una columna.
-Grid Cell (Celda de Cuadricula).- Interseccion entre columan y fila cada rectangulo
-Grid Area (Area Cuadricula).- Son area cuadriculares pueden ser rectangulos o cuadrados perfectos, es como la combinacion de celdas, lo que no se vale formar son figuras irregulares solo cuadrada o rectangular

!!! GRID EXPLICITA !!!.- Hay varias maneras de definir una grid, la mas elemental es una grid explicita se llama asi porque como su nombre explicitamente vamos a definir el número de filas y columnas que queremos que nuestra grid tenga ejm:

  .grid-explicit {
    display: grid; //Display 
    grid-template-rows: 2rem 20vh 30%; numero de filas
    grid-template-columns: 50% 100px 1fr; numero de columnas
  }
    Tenemos varias formas de definir esto tenemos el valor de repeat que recibe dos parametro, el numero de filas o columnas y el segundo el tamaño ejm:

    /* Grid de 5 columns * 4 rows */
    grid-template-columns: repeat(5, 20%);
    grid-template-rows: repeat(4, auto); Con este valor de auto le estamos diciendo que las filas se adpten al contenido de cada columna porque si le damos fijo y tenemos un texto largo este llega a su maximo y se desborda el texto o contenido. Generalmente el tamaño de la filas depende del contenido que tiene nuestros elementos. Tambien en vez de trabajar con porcentajes podemos trabajar con la fraccion que seria el espacio sobrante es el 100% del contenedor ejm:

    grid-template-columns: repeat(5, 1fr);
    grid-template-rows: repeat(4, 1fr); Esto es igual al ejm de arriba.
    El valor de repeat odempodemos usar siempre y cuando las filas sean unidas por ejm
    grid-template-columns: 20% repeat(2, 30%) 20%; aqui quiero que las dos columnas de la mitad tengan 30 ahi si vale el repeat no podemos colocar el repeat por ejm a las de 20 porque esta una de 20 yt solo hasta el final la otro no esta seguida la aplica para filas o columnas.
    Tambein podemos dar espaciado entre las celdas, existe una propiedad antes llamada grid-gap, para espaciodo entre filas existia un grid-row-gap y para las columnas grid-column-gap antes se llamaban asi, ahora se llama gap que viene a suplantar estas ya obsoletas propiedades anteriores

  !!! POSICIONAMIENTO EN GRID LINES !!!.- Podemos nosotros hacer que un elemento se posicione en una determinada coordenada por asi decirlo en determinada celda de la cuadricula que hemos definido y lo podemos lograr de dif formas ejm:

  Posiciona segun las grid lines.
    .grid-explicit .item:nth-child(10) {
      color: red;
      grid-row-start: 2; 
      grid-row-end: 3;
      grid-column-start: 2;
      grid-column-end: 3;

      /*Atajo para las propiedades de arriba */
      grid-row: 2 / 3;
      grid-column: 3 / 4;
    }
    Podemos tambien dar a una celda dos espacios ejm:
    grid-row: 2 / 3;
    grid-column: 3 / 5; Le damos dos espacios o combinacion de celdas

    Tenemos tambien otro atajo, que seria el atajo de las propiedades grid-row y grid-column, donde primero van los valores de grid-row-start grid-row-end y grid-column-start y grid-column-end
    grid-area: 2 / 3 / 3 / 5;

    Podemos tambien posicionar con la palabra span esto trabaja en posiciones osea le decimos que ocupe 2 posiciones para abajo y 3 para el lado
    .grid-explicit .item:nth-child(12) {
      color: yellow;
      grid-row: span 2; /* en fila ocupa dos espacios osea para abajo */
      grid-column: span 3; /* en columna ocupa dos espacios osea para los lados */
    }
  Una buena práctica si empezamos a alinear los elementos debemos de alinear todos, porque si dejamos que grid lo posicione segun su lagoritmo nos pueden quedar espacios o incluso desaparece el contenido de esa grid.

  !!! POSICIONAMIENTO CON GRID LINE NOMBRADOS !!!.- Podemos dar nombres explicitos a las grid lines, los nombres como buena practica deben ser semanticos osea con sentido comun ejm :

    .grid-line-names {
      display: grid;
      /* Grid 3c * 3r auto */
      grid-template-columns: repeat(3, 1fr);
      grid-template-rows: repeat(3, 1fr);
      grid-template-columns: [linea-c1] 1fr [linea-c2] 1fr [linea-c3] 1fr [linea-c4];
      grid-template-rows: [linea-r1] auto [linea-r2] auto [linea-r3] auto [linea-r4];

      Debemos de darnos en cuenta que la ultima grid linea no tiene que llevar fraccion o valor en px porque es la ultima si no se rompe la grid. Y le colocamos en auto al grid template rows para que tome el ancho segun el contenido si no se rompe la maquetacion de la grid.
    }

    .grid-line-names .item:nth-child(3) {
      color: cyan;
      grid-row: linea-r3 / linea-r4;
      grid-column: linea-c1 / linea-c4;
    }

    Cuando usamos los grid lines nos podemos usar grid-area el atajo de grid-row y grid-column en la técnica de los nombres.

  !!! POSICIONAMIENTO CON GRID AREAS !!!.- Nos ayuda a dar nombres de areas tambien donde es mas semantico y una mejor practica de usar este tipo de posicionamientos ya sean con nombres de areas o posicionamiento en lineas sin nombre pero porque si vemos cuando emepzamos a posicionar y a nombrar las lineas es muy engorroso y se llena de nombres nuestro css y es una mejor practica hacerlo con grid areas nombradas en este ejm vamos a realizar una maquetacion típica de una header, side, content y footer y vamos a poder apreciar la técnica esta de posicionamiento con grid areas nombradas porque ya al area de header le podemos dar le nombre del area a header y sería mas semántico ejm en el index.html.

    .grid-areas {
      display: grid;
      /* Grid 2c * 3r */
      grid-template-columns: 1fr 200px;
      grid-template-rows: 100px 1fr 60px;
      grid-template-areas: 
        "header  header"
        "content sidebar"
        "footer  footer";
    }

    .header {
      grid-area: header;
    }

    .content {
      grid-area: content;
    }

    .sidebar {
      grid-area: sidebar;
    }
    Realizamos primero la definicon de las columnas y areas, luego con el grid-template-areas estmos definiendo como primer valor en las comillas "nombre-area referencia", luego a las clases header que colocamos en le html le tenemos que dar el nombre con la propiedad grid-area: nombre-del-area, tiene que ser el mismo nombre que definimos arriba entonces asi haría caso a la maquetación, como vemos header ocupa dos espacios porque es header header, en el content sidebar ocupa dos espacios tambien pero un espacio es para el content y el otro para sidebar y el footer es igual que el header.
    Si queremos agragr una nueva fila basta con añadir en la defincion de la grid y al nombrar las areas seguirles dando los espacio que va a ocupar es decir esto grid-template-areas: 
        "header  header"
        "content sidebar"
        "content sidebar"
        "etc etc"
        "footer  footer"; esta propiedad se seuira modificando segun lo que queremos lograr.
    Otro ejm que se puede dar es que en un sidebar como lo estamos ejemplificando ahora necesite que de los dos espacios que tiene ocupe solo uno osea el espacio en fila tambien lo podemos lograr con el nombre de area pero le damos el nombre del area y el valor de punto ejm "content ." asi solo tomara un espacio  en fila.

  !!! GRID IMPLÍCITA GRIDS DE BLOQUE Y DE LINEA !!!.- Es como que tenemos una grid de 4c * 3 pero si tenemos 19 items enotnces no abaraca del item 13 al 19, entonces nosotros podemos hacer que la grid siga creciendosegun los elementos que tenga asi tenga una definicion en este ejm de 4c * 3r,pero esas columnas no tendran el mismo tamaño que le demos a las filas y siempre debemos de crear las grid si queremos fijas debemos de fijarnos siempre al tamao del cotenedor padre y cuando y los items que no entra en la grid pues se iran acomodando y al tamaño del contenedor padre y si ya no caben pues estos se desbordan y esto items van a tener el valor automatico es decir a los items que le coloquemos mas contenido y esta desbordado se acomoda segun lo que necesite.

    .grid-implicit {
      /* Grid de 4c * 3r */
      display: grid;
      grid-template-columns: repeat(4, 1fr);
      grid-template-rows: repeat(3, 200px); /* Altura de los items hace referencia los rows. */
    }

    Tenemos esta propiedad de display: inline-grid; por naturaleza inline lo que haces es ocupar solo el espacio requerido horizontalmente, este hace que todo el containerse pase a la izq osea la incio de la pantalla, entonces solo ocupara  los 80vh que tenemos en nuestro container por eso se alinea a la derecha, cuando nosotros usamos un display: inline sea grid o flex no podemos aplicar margenes laterales

    Esto del inline grid nos puede servir cuando nosotros queremos tener 3 grid en linea una ya sea para un referecncia de libros, otro de juegos y otro de comida por ejm entonces las 3 se posicionar en linea una alado de la otra.
    .grid-implicit {
      /* Grid de 4c * 3r */
      width: 40%;
      display: grid;
      display: inline-grid;
      grid-template-columns: repeat(4, 1fr);
      grid-template-rows: repeat(3, 200px); /* Altura de los items hace referencia los rows. */
    }
    Cuando usamos display: grid este se comporta en bloque osea para abajo cada grid , y cuando aplicamos el modelo inline-grid este toma en linea osea horizontalmente cada grid.

  !!! FLUJO DE LA GRID !!!.- Por defecto el comportamiento de grid es que se vayan generando filas, pero tambien podemos invertir el flujo, osea que primero se generen columns.
  Lo podemos hacer con la propiedad gird-auto-flow po defecto su valor en row:
  .grid-flow {
    display: grid;
    /* Grid 5c*4r */
    grid-template-columns: repeat(5, 1fr);
    grid-template-rows: repeat(3, 150px);
    grid-auto-flow: row;
    grid-auto-rows: auto;
    grid-auto-columns: auto;
  }
  Pero también tiene mas valores: grid-auto-flow: ;
    -column.- Osea primero crea las columnas y afectara el diseño de la grid.
    Revisar documentacion para los otros valores

    Tambein tenemos una propiedad que es grid-auto-rows: y su valor por defecto es auto, esta esntra cuando la grid explicta se van generando mas items en la grid, esta nos va a determinar que los items que no entren en la grid que definimos sean auto osea el tamaño que deben de tomar el resto de items que no caben y toman todo el espacio disponible. Podemos tambien modificar el auto por medidas absoluta sosea en pixeles y ese sera el valor que tomara acad elemento sobrante en la grid. Esta prop se usa cuando el valor de el flujo de la grid sea row grid-auto-flow: row.

    Tambien tenemos una propiedad llamada grid-auto-columns: le damos un valor que queremos esto se usa cuamdo el valor de del flujo de la grid sea column grid-auto-flow: column

  !!! FLUJO DENSO DE LA GRID !!!.- Cuando nosotros queremos pareovchar el espacio que dejan algunas cajas de la grid cuando por ejm le damos un espacio de 3 y 3 pero solo tenemos dos este genera otra row como e flujo de la grid entonces quedaria hueco, para poder aprovechar dicho espacio podemos agregar la propiedad grid-auto-flow con el valor de row dense ejm:

    .grid-flow-dense {
      display: grid;
      /* Grid 5c*4r */
      grid-template-columns: repeat(5, 1fr);
      grid-template-rows: repeat(4, 200px);
      grid-auto-flow: row dense;
      }

    Al elemento 9 le quedaban dos espacios en fila y queremos que tenga 3 entonces este se baja automaticamente y nos queda espacio para es lo solucionamos con el grid-auto-flow: row dense
    .grid-flow-dense .item:nth-child(9) {
      color: cyan;
      grid-row: span 3;
      grid-column: span 3;
    }

    Esto lo que hace es que los elementos que estan despues de lo que se movio o ocupo si tienen espacio estos suben y se colocan ahi, en este caso el item 10 e item 11 subieron a esos espacios que dejo el item 9 que movimos.
    E igual esto sirve para columna ejm 
    grid-auto-flow: column reverse;

    Si el valor del grid-auto-flow es row eso significa que la grid va a respetar el número exolicito que hayamos definido de columnas y si necesita genera mas segun el acomodo que hagamos va a generar mas filas implicitamente, osea dinamicamente si tenemos de 5 columnas siempre seran 5 pero filas mil, en cmabio cuando tenemos grid-auto-flow en column pues respeta las filas y genera mas columnas.

  !!! Grid Layers celdas en capa (Superposicion).-Son los elementos que estan mas al fondo o mas al frente.
  Vamos ha hacer un ejm de que tenemos una grid 4*4 pero tenemos una caja mas que queremos que aparezca adelante de todos osea la grid de 4 detras y ese elemento adelante.

  !!! ORDEN GRID ITEMS (PROPIEDADES A LOS HIJOS)!!!.- Funcoina igual que la teoria de felxbox von respecto de como alinear y ordenar los elementos con la propiedad order, la que nos permite cambiar el orden de los elementos siendo 0 su valor por defecto que seria el orden normal de izq a der, igual acepta numero positivos y negativos siendo el numero mas pequeño osea los negativos van al inicio, minetras mas grande el numero mas al final 
  order: 0 normal por defecto
  order: 1 va al sig espacio
  order: 2 lo posiciona al final
  order: -1 Menor a 0 osea, se pondra primero.
  Este orden siguiendo el flujo de la grid ya sea en columna o fila.

  !!! ALINEACION DE GRID ITEMS (PROPIEDADES A LOS HIJOS).-
  Casi siempre se trabaja con px en el  grid-template-rows
  .grid-align {
    display: grid;
    /* Grid 3c * 2r */
    grid-template-columns: repeat(3, 1fr);
    grid-template-rows: repeat(2, 200px);
    justify-items: stretch;
    align-items: stretch;
  }

  Tenemos esta propiedad aqui justify-items: stretch que su valor por defecto es stretch y asi segun los valores cambiara la manera de posicionarse los hijos tenemos center, start etc, este justify trabaja en x, siempre alineara en base o respetco a sucelda y ocupa el ancho que necesita nomas no todo por ejm si le podemos start pues se alinea a la izq pero deja un espacio a la der en este caso la fila es de 200px por ejm podiria ocupar 150px y deja 50px por ejemplificar.
    stretch.- Es por defecto como parace de prima carga.
    start.- Se alinea al inico osea a la izq pero solo ocupa lo que necesita el resto deja libre.
    end.- Se alinea al fin osea a la der/ pero solo ocupa lo que necesita el resto deja libre.
    center.- Lo centra, pero solo ocupa lo que necesita el resto deja libre.
    baseline.- Depende el taaño de la tipografia.

    Respecto de y para alinear seria de usar la propiedad align-items: por defecto siendo stretch y con los mismo valores de justofy-items si no que este centra en el cross y horizontal.
    start.- Se alinea arriba
    end.- Se alinea abajo
    center.- Lo centra
    stretch.- Valor por defecto.

    En cambio si queremos alinear un solo elemento podemos sin que rompa la maqueta el retso de elementos lo ponemos usar las propiedades justify-self y align-self en este caso vamos a mover el elemnto 4 arriba a la izq ejm :

    .grid-align .item:nth-child(4) {
      justify-self: start;
      align-self: start;
    }

  !!! ALINEACION DE GRID TRACKS !!!.- Es una alineacion por decirlo de una manera por bloque, osea todas las filas o todas la columnas.
  Tenemos las propiedades de justify-content que alinea los tracks en la grid en el horizontal con los sig valores :
    start.- Alinea al inicio osea a la izq pero ocupa todo porque en en bloque en fila o columnap por defecto
    end;.- Alinea al final osea a la derecha pero ocupa todo porque en en bloque en fila o columna
    center.- Alinea al centro en bloque.
    space-between.- Da espacio entre bloques pero desde el margen 0 para la izq osea sin considerar las orillas.
    space-around.- Da espacio entre bloques contando los margenes, le da como un padding de ahi los alinea.
    space-evenly.- Da el mismo espacio entre elemento y orillas.

  Tenemos tambien align-content que este alinea los los tracks de la grid en el eje vertical (Y) con los sig valores:
    start.- Alinea arriba osea al margen top
    end.- Alinea abajo osea al margen end
    center.- Centra todo.
    space-between  //Igual que los valores de justify.-content si no que el align-content va al eje Y
    space-around //Igual que los valores de justify.-content si no que el align-content va al eje Y
    space-evenly //Igual que los valores de justify.-content si no que el align-content va al eje Y

  !!! TAMAÑOS MAXIMOS Y MÍNIMOS DE GRID TRACKS !!!.- Tenemos una funcoin minmax que nos permite tener maximos y mínimos tamañospara cada uno de los trackks de la grid dependiendo en donde estos declarando la funcion siendo en row o columns. Teniendo en cuenta que si nosotros respetamos el flujo de la grid en filas respeta el numero de columnas dado osea este es fijo siempre, pero si es en columna este respeta el numero de filas dado es fijo y las columnas son la que se generan segun necesite.

  .grid-min-max {
    display: grid;
    /* Grid 4c * ?r, Osea genera las filas segun necesita lo podemos usar en un scroll infinito. */
    grid-template-columns: repeat(4, 1fr);
    grid-template-columns: repeat(4, minmax(100px, 200px));
    }
    El minmax recibe dos valores primero el minimo y segundo el maximo se puede usar cualquier medida px, fr, rem, em etc etc. En este ejm aqui si se reduce los items pero como le pusimos 200px como maximo pues hasta los 200 px crecera.
    Hay 2 valores que se le pueden asignar al min max, min-content y max-content, esto depende del minimo o maximo contenido que tengan la columna ejm :

    grid-template-columns: repeat(4, minmax(min-content, 200px));

    Lo podemos usar al reves tambien, Siempre sera 100 px el minimo pero el maximo le dimos min-content entonces el maximo sera el minimo contenido de la columna.
    grid-template-columns: repeat(4, minmax(100px, min-content));
    
    Tambien tenemos max-conten
    grid-template-columns: repeat(4, minmax(100px, max-content));
    Lo podemos invertir tambien
    grid-template-columns: repeat(4, minmax(max-content, 100px));

    Esto tiene siempre afectacion a los tracks completos como filas y columnas toda la fila o toda la columna.
    Pero debemos de tener cuidado al usar esto invertido porque puede ser que el valor mínimo sea mas grande que el máximo que le damos etonces queda en comflicto y le da el valor minimo mas alto.





