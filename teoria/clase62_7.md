
# Soluciones cambio

## Promoción Septiembre 2022

```js

function inicializarEfectivo(c500, c200, c100, c50, c20, c10, c5, c2, c1, c05, c02, c01, c005, c002, c001) {

    return [c500, c200, c100, c50, c20, c10, c5, c2, c1, c05, c02, c01, c005, c002, c001, 0];
}

function calcularTotal(efectivo, billetesMonedas) {
    //var total = 0;
    //efectivo.push(0); //le añadimos el 0 a la ultima casilla del array de efectivo en vez de declarar otra variable
    efectivo[efectivo.length - 1] = 0
    for (let i = 0; i < efectivo.length - 1; i++) {
        //total = total + efectivo[i] * billetesMonedas[i];         // varias formas de hacer lo mismo
        //total += efectivo[i] * billetesMonedas[i];
        efectivo[efectivo.length - 1] += efectivo[i] * billetesMonedas[i];
    }

    //[efectivo.length - 1] esto representa la ultima casilla del array, simplemente la seleccionamos
    efectivo[efectivo.length - 1] = Math.round((efectivo[efectivo.length - 1] + Number.EPSILON) * 100) / 100; //para redondear a dos decimales
    //efectivo.push(total);

    return efectivo;
}
function actualizarCaja(caja, pago) {
    for (let i = 0; i < caja.length; i++) {
        if (pago[i] > 0) {
            caja[i] += pago[i]
        }
    }
    return caja
}
var caja = inicializarEfectivo(1, 5, 0, 1, 4, 8, 2, 5, 4, 0, 0, 1, 2, 3, 1);
const billetesMonedas = [500, 200, 100, 50, 20, 10, 5, 2, 1, 0.5, 0.2, 0.1, 0.05, 0.02, 0.01];
caja = calcularTotal(caja, billetesMonedas);

// alert(caja);

var precio = 500.40;
var pago = inicializarEfectivo(4, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0);
pago = calcularTotal(pago, billetesMonedas);


//alert(pago);
if (pago[pago.length - 1] - precio == 0) { //Me dan el importe exacto
    alert('Importe exacto');
    caja = actualizarCaja(caja, pago)
    // alert(caja)
} else { //El importe no está exacto 
    // alert(pago[pago.length - 1] - precio);
    var devolver = pago[pago.length - 1] - precio
    if (devolver > caja[caja.length - 1]) { //No hay cambio en la caja
        alert("No tenemos cambio")
    } else {//Hay cambio aparentemente y se empieza a devolver
        var cambio = inicializarEfectivo(0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0)
        let i = 0;
        while (devolver > 0 && i < caja.length - 1) {
            if (caja[i] * billetesMonedas[i] >= devolver) { //Hay más que lo que tenemos que devolver
                cambio[i] = Math.floor(devolver / billetesMonedas[i]);
                caja[i] -= cambio[i]
                devolver -= cambio[i] * billetesMonedas[i];
            } else { //Hay menos 
                cambio[i] = caja[i];
                caja[i] = 0;
                devolver -= cambio[i] * billetesMonedas[i];
            }
            caja = calcularTotal(caja, billetesMonedas);
            cambio = calcularTotal(cambio, billetesMonedas);
            i++
        }
        if(devolver > 0){ //No disponemos de monedas o billetes para devolver
            alert("No podemos devolverte, disculpa las molestias")
        }else{ //Hemos devuelto
            for(let i = 0; i < caja.length-1;i++){
                if(pago[i]!=0){
                    caja[i]+=pago[i];
                }
            }
            caja = calcularTotal(caja, billetesMonedas);
            alert("Caja: " + caja);
            alert("Cambio: " + cambio);
        }
        
    }
}

```

## Promocion Abril 2022

```js

//pos 0 = 500; y ultima casilla importe total

let caja = [0, 0, 0, 1, 4, 8, 2, 5, 4, 0, 0, 1, 2, 3, 1, 0.0];

const precioArticulo = 1050;

let pago = [2, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0.0];

let devolucion = [0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0.0];

function dineroTotal(dinero) {
  for (let i = 0; i < dinero.length - 1; i++) {
    if (dinero[i] != 0) {
      switch (i) {
        case 0:
          dinero[dinero.length - 1] = 500 * dinero[i];
          break;
        case 1:
          dinero[dinero.length - 1] += 200 * dinero[i];
          break;
        case 2:
          dinero[dinero.length - 1] += 100 * dinero[i];
          break;
        case 3:
          dinero[dinero.length - 1] += 50 * dinero[i];
          break;
        case 4:
          dinero[dinero.length - 1] += 20 * dinero[i];
          break;
        case 5:
          dinero[dinero.length - 1] += 10 * dinero[i];
          break;
        case 6:
          dinero[dinero.length - 1] += 5 * dinero[i];
          break;
        case 7:
          dinero[dinero.length - 1] += 2 * dinero[i];
          break;
        case 8:
          dinero[dinero.length - 1] += 1 * dinero[i];
          break;
        case 9:
          dinero[dinero.length - 1] += 0.5 * dinero[i];
          break;
        case 10:
          dinero[dinero.length - 1] += 0.2 * dinero[i];
          break;
        case 11:
          dinero[dinero.length - 1] += 0.1 * dinero[i];
          break;
        case 12:
          dinero[dinero.length - 1] += 0.05 * dinero[i];
          break;
        case 13:
          dinero[dinero.length - 1] += 0.02 * dinero[i];
          break;
        case 14:
          dinero[dinero.length - 1] += 0.01 * dinero[i];
          break;
      }
    }
  }
  dinero[dinero.length - 1] = dinero[dinero.length - 1].toFixed(2);
}
dineroTotal(pago);
dineroTotal(caja);
// console.log(pago);
// console.log(caja);
function mostrarDinero(dinero) {
  let mostrar = "";
  for (let i = 0; i < dinero.length - 1; i++) {
    if (dinero[i] != 0) {
      switch (i) {
        case 0:
          mostrar += "Hay " + dinero[i] + " billetes de 500 \n";
          break;
        case 1:
          mostrar += "Hay " + dinero[i] + " billetes de 200 \n";
          break;
        case 2:
          mostrar += "Hay " + dinero[i] + " billetes de 100 \n";
          break;
        case 3:
          mostrar += "Hay " + dinero[i] + " billetes de 50 \n";
          break;
        case 4:
          mostrar += "Hay " + dinero[i] + " billetes de 20 \n";
          break;
        case 5:
          mostrar += "Hay " + dinero[i] + " billetes de 10 \n";
          break;
        case 6:
          mostrar += "Hay " + dinero[i] + " billetes de 5 \n";
          break;
        case 7:
          mostrar += "Hay " + dinero[i] + " monedas de 2 \n";
          break;
        case 8:
          mostrar += "Hay " + dinero[i] + " monedas de 1 \n";
          break;
        case 9:
          mostrar += "Hay " + dinero[i] + " monedas de 0.5 \n";
          break;
        case 10:
          mostrar += "Hay " + dinero[i] + " monedas de 0.2 \n";
          break;
        case 11:
          mostrar += "Hay " + dinero[i] + " monedas de 0.1 \n";
          break;
        case 12:
          mostrar += "Hay " + dinero[i] + " monedas de 0.05 \n";
          break;
        case 13:
          mostrar += "Hay " + dinero[i] + " monedas de 0.02 \n";
          break;
        case 14:
          mostrar += "Hay " + dinero[i] + " monedas de 0.01 \n";
          break;
      }
    }
  }
  if (mostrar == "") {
    mostrar = "Su cambio es 0";
  }
  alert(mostrar);
}
function rangoDevolucion(importeDevolucion) {
  if (importeDevolucion >= 500) {
    return 0;
  } else if (importeDevolucion >= 200) {
    return 1;
  } else if (importeDevolucion >= 100) {
    return 2;
  } else if (importeDevolucion >= 50) {
    return 3;
  } else if (importeDevolucion >= 20) {
    return 4;
  } else if (importeDevolucion >= 10) {
    return 5;
  } else if (importeDevolucion >= 5) {
    return 6;
  } else if (importeDevolucion >= 2) {
    return 7;
  } else if (importeDevolucion >= 1) {
    return 8;
  } else if (importeDevolucion >= 0.5) {
    return 9;
  } else if (importeDevolucion >= 0.2) {
    return 10;
  } else if (importeDevolucion >= 0.1) {
    return 11;
  } else if (importeDevolucion >= 0.05) {
    return 12;
  } else if (importeDevolucion >= 0.02) {
    return 13;
  } else if (importeDevolucion >= 0.01) {
    return 14;
  }
}
function valorPosicion(posicion) {
  switch (posicion) {
    case 0:
      return 500;
      break;
    case 1:
      return 200;
      break;
    case 2:
      return 100;
      break;
    case 3:
      return 50;
      break;
    case 4:
      return 20;
      break;
    case 5:
      return 10;
      break;
    case 6:
      return 5;
      break;
    case 7:
      return 2;
      break;
    case 8:
      return 1;
      break;
    case 9:
      return 0.5;
      break;
    case 10:
      return 0.2;
      break;
    case 11:
      return 0.1;
      break;
    case 12:
      return 0.05;
      break;
    case 13:
      return 0.02;
      break;
    case 14:
      return 0.01;
      break;
  }
}
devolucion[devolucion.length - 1] = pago[pago.length - 1] - precioArticulo;
devolucion[devolucion.length - 1] = devolucion[devolucion.length - 1].toFixed(2);
console.log(devolucion[devolucion.length - 1])
console.log(caja[caja.length - 1])
if (devolucion[devolucion.length - 1] == 0) {
  console.log("Gracias, vuelva pronto ");
  mostrarDinero(devolucion);
} else {
  if (devolucion[devolucion.length - 1] > caja[caja.length - 1]) {
    console.log("Me faltan pelas");
  } else {
    if (pago[pago.length - 1] < precioArticulo) {
      console.log("Importe insuficiente");
    } else {
      for (
        let i = rangoDevolucion(devolucion[devolucion.length - 1]);
        i < caja.length - 1;
        i++
      ) {
        if (caja[i] != 0) {
          let valorPosicion1 = valorPosicion(i);
          if (caja[i] * valorPosicion1 >= devolucion[devolucion.length - 1]) {
            let cantidad = Math.floor(
              devolucion[devolucion.length - 1] / valorPosicion1
            );
            devolucion[devolucion.length - 1] -= valorPosicion1 * cantidad;
            devolucion[devolucion.length - 1] =
              devolucion[devolucion.length - 1].toFixed(2);
            caja[i] -= cantidad;
            devolucion[i] = cantidad;
            console.log("cantidad " + cantidad);
            console.log("devolucion " + devolucion);
            console.log("caja " + caja);
            console.log("valorPosicion1 " + valorPosicion1);
          }
        }
      }
      mostrarDinero(devolucion);
    }
  }
}

```

## Noviembre 2021

```js 

    const contarDinero = (...valores) => {
        let dinero = [["500", "200", "100", "50", "20", "10", "5", "2", "1",
            "0.50", "0.20", "0.10", "0.05", "0.02", "0.01"], valores];
        return dinero;
    }
    const calcularTotal = function (caja) {
        const keys = caja[0];
        const values = caja[1];
        let total = 0;
        for (let i = 0; i < keys.length; i++) {
            total += (Number(keys[i]) * values[i]);
            // console.log(total);
        }
        caja[0].push("total")
        caja[1].push(Math.round(total * 100) / 100);
        return caja;
    }
    function vaciarCaja(caja) {
        const values = caja[1];
        for (let i = 0; i < values.length; i++) {
            values[i] = 0;
            // console.log(caja[keys[i]]);
        }
        return caja;
    }
    function mostrarCambio(dinero) {
        let cadenaCambio = "Devolución: \n";
        const keys = dinero[0];
        const values = dinero[1];
        for (let i = 0; i < keys.length; i++) {
            cadenaCambio += `${keys[i]}: ${values[i]} \n`;
        }
        alert(cadenaCambio);
    }
    function primerElemento(parteEntera, dinero) {
        // const values = dinero[1];
        const keys = dinero[0];
        // console.log(parteEntera);
        let i = 0;
        let encontrado = false;
        while (i < keys.length && !encontrado) {
            if (keys[i] <= parteEntera) {
                encontrado = true;
            }
            i++;
        }
        return i - 1;
    }
    function inicializarCambio(cambio, posicion) {
        for (let i = 0; i < posicion; i++) {
            cambio[1][i] = 0;
        }
        return cambio;
    }
    function recopilarCambio(devolver, caja, cambio, posicion) {
        if (devolver >= caja[0][posicion]) {
            // console.log("Entro aquí");
            // console.log("caja[0][posicion]: ", caja[0][posicion]);
            var parte1 = Math.floor(devolver / Number(caja[0][posicion]));
            // console.log("parte1: ", parte1);
            // console.log("caja[1][posicion]: ", caja[1][posicion]);
            if (parte1 <= caja[1][posicion]) {
                caja[1][posicion] = caja[1][posicion] - parte1;
                cambio[1][posicion] = (parte1);
                devolver = devolver - Number(parte1 * caja[0][posicion]);
                console.log(caja[0][posicion]);
            } else {
                if (caja[1][posicion] > 0) {
                    cambio[1][posicion] = (caja[1][posicion]);
                    devolver = devolver - Number(caja[0][posicion]) * caja[1][posicion];
                    caja[1][posicion] = 0;
                }
                // console.log(caja[0][posicion]);
            }
        }
        devolver = Math.round(devolver * 100) / 100
        // console.log("devolver: ", devolver);
        return [devolver, caja, cambio];
    }
    let caja = contarDinero(0, 0, 0, 1, 4, 8, 2, 5, 4, 0, 0, 1, 2, 3, 1);
    // console.log(caja);
    let pago = contarDinero(0, 0, 0, 0, 2, 1, 0, 0, 1, 2, 6, 0, 0, 1, 0);
    caja = calcularTotal(caja);
    pago = calcularTotal(pago);
    let precio = 32.95;
    let cambio = [[], []];
    let devolver = pago[1][pago[1].length - 1] - precio;
    devolver = Math.round(devolver * 100) / 100
    if (devolver > caja[1][caja[1].length - 1]) {
        alert("No disponemos de cambio para tu compra, gracias y hasta luego");
    } else {
        if (devolver == caja[1][caja[1].length - 1]) {
            cambio[0] = caja[0].slice();
            cambio[1] = caja[1].slice();
            caja = vaciarCaja(caja);
            mostrarCambio(cambio);
        } else {
            let posicion = (primerElemento(devolver, caja));
            cambio = [["500", "200", "100", "50", "20", "10", "5", "2", "1",
                "0.50", "0.20", "0.10", "0.05", "0.02", "0.01"], []];
            inicializarCambio(cambio, cambio[0].length);
            // function recopilarCambio(devolver, caja, cambio, posicion) {
            for (let i = posicion; i < caja[1].length - 1; i++) {
                [devolver, caja, cambio] = recopilarCambio(devolver, caja, cambio, i);
            }
            mostrarCambio(cambio);
            // console.log(devolver);
            // console.log(caja);
            // console.log(cambio);
        }
    }
    // TE FALTA DINERO
    // NO HAY CAMBIO

```
