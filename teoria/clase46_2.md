# Librería, Biblioteca o Módulo

Es posible que tengamos la necesidad de crear ficheros de JS con funciones, clases o incluso objetos que usemos con frecuencia para cuestiones específicas. Esta es la idea de librería (biblioteca o módulo) 

Vamos a ver las herramientas que nos proporciona JavasScript a nivel de Front para realizar estas tareas: 

## Import 

Se usa para incluír dentro de un script en JavaScript una clase, función, variable, constante...etc

Vamos algunos ejemplos y su significado

```js
import defaultExport from "module-name"; //Elemento por defecto
import * as name from "module-name"; //Todo el módulo 
import { export } from "module-name"; //Un elemento concreto
import { export as alias } from "module-name"; //Un elemento con un alias
import { export1 , export2 } from "module-name"; //Varios elementos 
import "module-name"; //Importa y ejecuta el módulo completo

```

Hay que tener en cuenta que **import** trabaja en conjunto con **export**, si no hemos exportado los elementos, no podremos importarlos.

Más información: [import](https://developer.mozilla.org/es/docs/Web/JavaScript/Reference/Statements/import)

## export 

Es la palabra reservada que indica que un elemento (clase, función, variable, constante...etc) es importable desde el exterior.

Existen dos tipos diferentes de exportación , nombrada y por defecto. Se pueden tener varias exportaciones nombradas por módulo pero sólo una exportación por defecto.

Veamos algunos ejemplos y su significado: 

```js
export { myFunction }; //Por nombre: La función debe estar previamente implementada
export const foo = Math.sqrt(2); //Constante
export default function() {}; //Función por defecto 
export default Class {}; //Clase por defecto

```

Ejemplo con default: 

```js

// en el archivo saludo.js
var saludo = "Hola";
export default saludo; 

// en el archivo script.js. Podemos usar otro nombre por ser la exportación por defecto.

import saludar from './saludo.js' 
console.log(saludar); // Hola

```

Importar y exportar por defecto

```js

import mod from 'mod';

export default mod;

```

Más ejemplos: 

- export 

```js
// module "my-module.js"
function cube(x) {
  return x * x * x;
}
const foo = Math.PI + Math.SQRT2;
var graph = {
    options:{
        color:'white',
        thickness:'2px'
    },
    draw: function(){
        console.log('From graph draw function');
    }
}
export { cube, foo, graph };

```
- import

```js

//You should use this script in html with the type module ,
//eg ''<script type="module" src="demo.js"></script>",
//open the page in a httpserver,otherwise there will be a CORS policy error.
//script demo.js

import { cube, foo, graph } from 'my-module';
graph.options = {
    color:'blue',
    thickness:'3px'
};
graph.draw();
console.log(cube(3)); // 27
console.log(foo);    // 4.555806215962888

```

Por defecto: 

- export 
```js
// module "my-module.js"
export default function cube(x) {
  return x * x * x;
}
```
- import

```js
import cube from 'my-module';
console.log(cube(3)); // 27

```

Más información: [export](https://developer.mozilla.org/es/docs/Web/JavaScript/Reference/Statements/export)
