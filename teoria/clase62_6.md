# Soluciones simples ejercicios (Subprogramas y funciones)

## Ejercicio 2.3 

```js
//El parámetro indica la cantidad de caracteres de la secuencia
function ejercicio_2_3(tamSecuencia){ 
    var mostrar = "";
    for (let i = 0; i < tamSecuencia; i++) {
        switch(i%3){
            case 0:
                mostrar = mostrar + '*';
                break;
            case 1:
                mostrar = mostrar + '+';
                break;
            case 2:
                mostrar = mostrar + '_';
                break;
        }
    }
    alert(mostrar);
}

```


## Ejercicio 2.4

```js

//El parámetro indica la cantidad de líneas del triángulo
function ejercicio_2_4(lineas){ 
    var mostrar = "";
    for (let i = 0; i < lineas; i++) {
        for (let j = 0; j <= i; j++) {
            mostrar = mostrar + '*';
        }
        mostrar = mostrar + '\n'; //\n es el salto de línea
        
    }
    alert(mostrar);
}


```
