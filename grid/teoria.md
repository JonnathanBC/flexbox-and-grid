!!! GRID CSS !!!.- Con grid por fin tenemos un sistema bidireccional osea que podemos tener columnas y filas para maquetar al mismo tiempo a diff de flexbox que es unidireccional porque tenemos bien filas o columnas pero no las dos.
Flexbox es para alinear los elementos internos de un componente de UI.
A grid css lo empezaron  a soportar en 2017. En grid tambien tenemos algunos conceptos a entender por ejm:

-Grid Container (Contenedor Padre).- Al que se le aplica el display: grid
-Grid Items (Elementos Hijos).- Estos son como nuestras celdas.
-Grid Lines (Lineas de Cuadricula).- Son la lineas divisiorias entre columnas por ejm si tenemos una grid de 5 * 5 las lineas de cuadricula seran de 6 * 6.

-Grid Track (Pistas de Cuadricula).-Es como toda una fila o toda una columna.
-Grid Cell (Celda de Cuadricula).- Interseccion entre columan y fila cada rectangulo
-Grid Area (Area Cuadricula).- Son area cuadriculares pueden ser rectangulos o cuadrados perfectos, es como la combinacion de celdas, lo que no se vale formar son figuras irregulares solo cuadrada o rectangular

GRID EXPLICITA.- Hay varias maneras de definir una grid, la mas elemental es una grid explicita se llama asi porque como su nombre explicitamente vamos a definir el número de filas y columnas que queremos que nuestra grid tenga ejm:

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

  POSICIONAMIENTO EN GRID LINES.- Podemos nosotros hacer que un elemento se posicione en una determinada coordenada por asi decirlo en determinada celda de la cuadricula que hemos definido y lo podemos lograr de dif formas ejm:

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

  POSICIONAMIENTO CON GRID LINE NOMBRADOS.- Podemos dar nombres explicitos a las grid lines, los nombres como buena practica deben ser semanticos osea con sentido comun ejm :

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

