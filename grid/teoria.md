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

