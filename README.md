# ejerciciosjavascript_46-52

## 046 Escriba un ejercicio de JavaScript para obtener la extensión de un nombre de archivo.

Utilizo la funion .lastIndexOf(".") para obtener el último . de la cadena
y posterioremente la función .substring(posicion) para que me devuelva un substring desde el último punto encontrado.


```javascript
    var posicionultimopunto = pathfichero.lastIndexOf(".");
    var resultado = pathfichero.substring(posicionultimopunto + 1);
   ```

##  047 Escriba un programa JavaScript para comprobar si todos los dígitos de un número dado son iguales o no.

Con la expresión regular   /^\d+$/;  verifico que la entrada sea numérico

y despues con un bucle compruebo si el primer caracter es igual al resto
en caso de que un ya no lo sea, salgo del bucle con un break

si llego al final del bucle es que todos son iguales

```javascript

var numero = document.getElementById("entrada").value;
var patron = /^\d+$/; //Expresión regular para aceptar solo números enteros

if (patron.test(numero)) {    
    
    var caracter = numero.charAt(0);        
    for (var i = 1; i< numero.length; i++) {
        var nuevocaracter = numero.charAt(i);
        if (caracter != nuevocaracter)
        {
            resultado="NO";
                    break;
        }
    }
    
}else {
alert("el valor del número debe ser entero positivo");
numero.focus();
return (false);
}
document.getElementById("divresultado").innerText ="Los digitos "+ resultado + " son todos iguales";
  ```  

##   048 Escriba un programa de JavaScript para encontrar la cantidad de elementos que se presentan en ambos arreglos dados

Para crearme los arrays utilizo las funciones Math.round( (Math.random () * 100)) para definirme la longitud de cada array y posterioremente lo relleno con un bucle que vaya desde 1 hasta esa longitud
rellenandolo con push arraynumeros1.push (Math.round( (Math.random () * 100)));



presento el array y su longitud  arraynumeros1.length


```javascript
{
let arraynumeros1 = new Array();
let n1 = Math.round( (Math.random () * 100));

for (let i=0;i< n1; i ++){
arraynumeros1.push (Math.round( (Math.random () * 100)));
}

document.getElementById("divresultado").innerText="";

document.getElementById("divresultado").innerHTML="Array 1: <br>" + arraynumeros1;
document.getElementById("divresultado").innerHTML+="<br>";
document.getElementById("divresultado").innerHTML+="Elementos de Array 1: " + arraynumeros1.length;
}    
 ```  

 ##   049 Escriba un programa JavaScript para simplificar una ruta absoluta dada para un archivo en estilo Unix.

 Entiendo por simplificar una ruta absoluta de unix en ir poniendo por que carpetas me voy moviendo

 he utilizado lastIndexof("/") y substring para ir recortando el path
 y lo he metido en un bucle hasta que lasindeof("/")== -1

En una practica posterior similar utilizaré la funcion split

```javascript
 const myfuncion = function ()
{
    
    const ruta = "/var/log/mysql/error.log";

    let str =ruta;

    document.getElementById("divresultado").innerHTML= str + "<br>";;

    let posicionultimopunto =  str.lastIndexOf("/") ;
    do {
    posicionultimopunto =  str.lastIndexOf("/") ;
    
    
    document.getElementById("divresultado").innerHTML+=str.substring(posicionultimopunto + 1) + "<br>";
    
    str = str.substring(0,posicionultimopunto );
        
    } while (str!="" && posicionultimopunto >0);

}  
 ```          


  ##  050 Escriba un programa JavaScript para ordenar las cadenas de una matriz dada de cadenas en el orden de longitudes crecientes. Nota: No cambie el orden si las longitudes de dos cadenas son iguales.

  Javascript tiene el metodo sort para ordenar arrays
  al cual le puedes pasar por argumento una función que espeficique como lo quieres ordenar
  
  ```javascript
  arraycadenas.sort(function(a, b){return a.length-b.length});
   ``` 


##  051 Escriba un programa JavaScript para romper la dirección de una URL y poner su parte en una matriz. Nota: estructura de la URL: //.org [/] y es posible que no haya parte en la dirección.


Este es similar al ejercicio 49 pero en este caso utilizo url1.split("/")
Esta funcion me devuelve en una matriz todos los elementos de una cadena separado por el parametro
para terminar utilzo  matriz.splice(0, 0, url.substr(0, url.indexOf("://") + 3)); para que me inserte el protocolo en la primera posición del elemento 

```javascript
    const myfuncion = function (valor) {
    let url = document.getElementById("txturl").value;
    let matriz = new Array();
    let url1 = url.substr(url.indexOf("://") + 3, url.length);
    matriz = url1.split("/");
    if (url.indexOf("://") != -1)
        matriz.splice(0, 0, url.substr(0, url.indexOf("://") + 3));
    /* visualizacion */
    for (i = 0; i < matriz.length; i++) {
        let li = document.createElement("li");
        li.innerText = matriz[i];
        document.getElementById("lista").appendChild(li);
    }
}
``` 

## 052 Escriba un programa JavaScript para encontrar el número entero máximo n tal que 1 + 2 + ... + n <= un número entero dado


En este caso he utilizado una función recursiva se va llamando con valor + 1
y la condición de salida es que el sumatorio sea mayor que el numero dado

``` javascript
var elemento = Math.round(Math.random() * 1000);
var suma=0;
let elementos = new Array();

const myfuncion = function     ( valor)
{
    elementos.push(valor);
    suma = suma + (valor +1) ;

    if ( suma  <= elemento)
    {
        
        valor++;
        myfuncion (valor);
    }
    else
        { 
        document.getElementById("divresultado").innerHTML= "Número base: " +elemento  + "<br>";
        document.getElementById("divresultado").innerHTML+= elementos + "<br>"; 
            
            document.getElementById("divresultado").innerHTML+="Número Máximo: " + valor + "<br>"; 
            
        }
}
```

## 053 Escriba un programa JavaScript para calcular la suma de cubos de todos los enteros desde 1 hasta un entero dado.


Similar al ejerccio anterior
una funcion recursiva que le paso por parametro el valor + 1
voy incrementado el sumatorio con el cubo del elemento
y la salida es cuando llegue el parametro al numero dado

``` javascript
var elemento =  Math.round(Math.random() * 20) ;
var suma=0;
let elementos = new Array();
       
const myfuncion = function     ( valor)
{
    /* inicializo si la suma = 0*/
    if (suma==0) {
       elementos = [];
        elemento =  Math.round(Math.random() * 20) 
    }         
    let cubo = valor*valor*valor;
    elementos.push(cubo);
    suma = suma + cubo ;
    if ( valor  < elemento){
        valor++;
        myfuncion (valor);
    }
    else
    { 
        document.getElementById("divresultado").innerHTML= "Número base: " +elemento  + "<br>";
        document.getElementById("divresultado").innerHTML+= "cubos: " + elementos + "<br>"; 
        document.getElementById("divresultado").innerHTML+="Número Máximo: " + suma + "<br>"; 
    suma=0;
    }
}
``` 
