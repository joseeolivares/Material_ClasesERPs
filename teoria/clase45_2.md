# Excepciones 
Las excepciones son erroes en ejecución, es decir, son cuestiones que no puede controlar un compilador o un intérprete (en el caso de Javascript los intérpretes que hemos visto son el navegador y Node).

Estos errores se producen al procesar las sentencias y no impiden que se ejecuten sentencias anteriores.

La forma más sencilla de manejarlas es usando **try-catch-finally**.

**Veamos un ejemplo:**

```javascript

    /*function f(){
    console.log('Hola');
    }*/
    try{
        f();
    }catch{
        console.log('Se ha producido una excepción');
    }finally{
        console.log('El finally se ejecuta sí o sí');
    }

```
Prueba el ejemplo dejando **f** comentada y luego descomentada y hablemos de las conclusiones que debemos sacar.

## try
Bloque de código en el que implementamos el "código a intentar", pero no podemos usar un try sin al menos un catch (podemos tener más de uno si contemplamos la posibilidad de que se produzcan errores diferentes y queremos que el comportamiento de la aplicación sea diferente en cada caso) o al menos un finally.

**La sintaxis es la siguiente:**

```javascript

    try {
        try_statements
    }

```
**Esto por sí sólo no funciona, como hemos comentado**



## catch
Bloque de código que se ejecuta si se produce una excepción. Se encarga de capturarla y actuar en consecuencia.

**La sintaxis es la siguiente:**
```javascript

    try {
        try_statements
    }
    catch (exception_var) {
        catch_statements
    }


```

```
    try_statements: 
        Las sentencias que serán ejecutadas.
    catch_statements: 
        Sentencias que se ejecutan si una excepción se produce en el bloque try.
    exception_var: 
        Identificador que contiene un objeto de excepcion asociado a la cláusula catch, para poder trabajar con él.

```


## finally
Bloque de código que se ejecuta en todos los casos, no es obligatorio. Las sentencias incluídas en el **finally** se van a ejecutar tanto si se puede ejecutar el código del **try**, como si se ejecuta el código de cualquiera de los **catch**. Además es un único bloque, como sucede con el **try**.

**La sintaxis es la siguiente:**

```javascript

    try {
        try_statements
    }
    [catch (exception_var) { 
        catch_statements
    }]
    [finally {
        finally_statements
    }]


```


```
    try_statements: 
        Las sentencias que serán ejecutadas.
    catch_statements: 
        Sentencias que se ejecutan si una excepción se produce en el bloque try.
    exception_var: 
        Identificador que contiene un objeto de excepcion asociado a la cláusula catch, para poder trabajar con él.
    finally_statements: 
        Sentencias que se ejecutan después de que se completa la declaración try . Estas sentencias se ejecutan independientemente de si una excepcion fue lanzada o capturada.

```

### Ampliemos un poco la información y veamos más detalles: 

La sentencia **try** consiste en un bloque try que contiene una o más sentencias. **Las llaves {} se deben utilizar siempre, incluso para una bloques de una sola sentencia. Al menos un bloque catch o un bloque finally debe estar presente**. Esto nos da tres formas posibles para la sentencia try:

```
    try...catch
    try...finally
    try...catch...finally
```

Un bloque **catch** contiene sentencias que especifican **qué hacer si una excepción es lanzada en el bloque try**. Si cualquier sentencia dentro del bloque try (o en una funcion llamada desde dentro del bloque try) lanza una excepción, el control cambia inmediatamente al bloque catch . **Si no se lanza ninguna excepcion en el bloque try, el bloque catch se omite**.

La bloque **finally** se ejecuta despues del bloque try y el/los bloque(s) catch hayan finalizado su ejecución. **Éste bloque siempre se ejecuta**, independientemente de si una excepción fue lanzada o capturada.

**Se puede anidar una o más sentencias try. Si una sentencia try interna no tiene una bloque catch, se ejecuta el bloque catch de la sentencia try que la encierra.**

## throw
Esto nos permite lanzar excepciones propias, que pueden ser sentencias simples, objetos, resultados de funciones...etc

**Veamos algunos ejemplos simples:**

```javascript

    try {
        throw 'Error creado por Davinia';
    } catch (e) {
        console.log('Se ha producido una excepción: ' + e);
    } finally {
        console.log('El finally se ejecuta sí o sí');
    }

```

```javascript 

    try {
        throw { toString: function () { return "Error creado por Davinia desde una función anónima";} };
    } catch (e) {
        console.log('Se ha producido una excepción: ' + e);
    } finally {
        console.log('El finally se ejecuta sí o sí');
    } 

```

```javascript

    try {
        function f() { 
            return "Error creado por Davinia desde una función"; 
        };
        throw { toString: f };
    } catch (e) {
        console.log('Se ha producido una excepción: ' + e);
    } finally {
        console.log('El finally se ejecuta sí o sí');
    }

```

También se puede preguntar por la excepción producida y manejarla de manera diferente en cada caso.

**Veamos un ejemplo:**

```javascript

    try {
        f();
    } catch (e) {
        if (e instanceof ReferenceError) {
            console.log('Se ha producido una excepción: '+ e);
        }
    } finally {
        console.log('El finally se ejecuta sí o sí');
    }

```

