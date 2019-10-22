---
description: "En este nivel, vamos a aprender ¿Qué es JavaScript \U0001F913?, ¿Para que sirve? y ¿Cómo podemos sacarle el mejor provecho a este lenguaje?."
---

# Primeros pasos: JavaScript

## 💡 Introducción 💡

JavaScript \(JS\) es un lenguaje de programación que le ha otorgado rapidez y efectos atractivos a las páginas web, mediante su uso combinado junto a HTML, CSS y otros lenguajes.   
Hoy vamos a conocer aspectos generales pero muy útiles de forma dinámica. 🎮

![JavaScript Logo](../.gitbook/assets/image%20%281%29.png)

\*\*\*\*[**¡Aquí puedes encontrar el demo!**](https://angular-conoce-javascript.stackblitz.io)\*\*\*\*

## Paso 1: **Creemos nuestra App de Angular** ⭐️

Entra a [**www.stackblitz.com**](www.stackblitz.com), y verás algo como esto:

![](../.gitbook/assets/1.png)

![](../.gitbook/assets/screen-shot-2019-05-25-at-1.56.29-pm.png)

## Paso 2: ¿Qué es una variable? **🗄**

Una variable es un espacio de almacenamiento, aquí podemos guardar cualquier tipo de dato que te puedas imaginar, como una cadena de caracteres, un valor numérico o estructuras un poco más específicas.  
Adiciona este código en tu archivo **app.component.ts**

{% code-tabs %}
{% code-tabs-item title="app.component.ts" %}
```javascript
  // Vamos a crear una serie de variables de diferentes tipos
  // Numérico
  iva = 16;        // Variable tipo entero
  total = 234.65;  // Variable tipo decimal

  // Cadenas de texto, tambien se les dicen String
  mensaje = 'Bienvenid@ a She Codes Angular';
  nombreCompleto = 'Alejandra Giraldo';

  // Arrays - Arreglos
  dias = ['Lunes', 'Martes', 'Miércoles', 'Jueves', 'Viernes', 'Sábado', 'Domingo'];
  diaSeleccionado = this.dias[0];    // diaSeleccionado = 'Lunes'

  // Object - Objetos
  personalInfo = {'nombre': 'Alejandra', 'apellido': 'Giraldo', 'cedula': 123456};
  soloApellido = this.personalInfo.apellido;    // soloApellido = 'Giraldo'

  // Boolean - Booleanos
  estoyAprendiendo = true;
  meGustanLosVegetales = false;
```
{% endcode-tabs-item %}
{% endcode-tabs %}

Deberías hacer algo así, y tu resultado se deberá ver así:👇

![](../.gitbook/assets/variables-1.gif)

{% hint style="info" %}
**Por si tienes alguna duda. Aquí te explicamos cómo funciona: 👷‍♀️**

**1.** Nos podemos dar cuenta que cuando abrimos el archivo **app.component.ts** que ya existe una variable name, y es de tipo string.  
  
**2.** Vemos una palabra nueva llamada **this**, ¿Qué es **this**?`this`es una palabra reservada de JavaScript \(palabra reservada significa que no puedes crear una variable que este escrita exactamente igual a "**this**"\), se hace referencia al elemento que contiene el método donde se invoca.  
En este caso`this.dias`hace referencia a la variable `dias` que  acabamos de crear y \[0\] hace referencia a la posición del array que queremos seleccionar, el primer elemento del array seria el 0 con el texto _lunes_, el segundo seria 1 con el texto _martes_, el tercero seria 2 con el texto _miércoles_ y así sucesivamente.  
  
**3.** También usamos la referencia de`this`en la variable `personalInfo` aquí, los objetos están conformados por una estructura`{llave: valor},` donde llave será la referencia para acceder al contenido, es por eso que cuando escribimos `this.personalInfo.apellido`, el resultado es `"Giraldo"`, porque estamos accediendo a la llave`apellido`de nuestra variable`personalInfo.` Ensaya usando `this.personalInfo.cedula` ¡ y descubre que pasa!  
  
**4.** También te abras podido dar cuenta, que en un archivo con extensión **.TS** puedes hacer comentarios dentro de tu código, usando **`//`** o **/**_**\*  texto \***_**/** si quieres utilizar más de una línea comentada, por ejemplo

{% code-tabs %}
{% code-tabs-item title="app.component.ts" %}
```javascript
/* estas 
son varias 
líneas comentadas */
```
{% endcode-tabs-item %}
{% endcode-tabs %}

Esto es muy útil cuando trabajas en equipos y deseas dejar una nota, o simplemente porque deseas recordar que es lo que hace tu código.
{% endhint %}



## Paso 3: ¿**Cómo podemos ver el contenido de una variable? 👀**

Que lindo conocer todas las posibilidades de almacenamiento de datos que podemos tener con JavaScript 🥳 .  
Ahora vamos a utilizar **los** conocimientos que aprendiste en el ejercicio anterior sobre HTML y descubriremos como Angular nos permite ver variables de manera muy simple.  
Adiciona este código en tu archivo **app.component.html**

{% code-tabs %}
{% code-tabs-item title="app.component.html" %}
```markup
<p>
  Vamos a ver la variable iva: {{ iva }}
</p>
<p>
  Vamos a ver la variable total: {{ total }}
</p>
<p>
  Vamos a ver la variable mensaje: {{ mensaje }}
</p>
<p>
  Vamos a ver la variable nombreCompleto: {{ nombreCompleto }}
</p>
<p>
  Vamos a ver la variable dias: {{ dias }}
</p>
<p>
  Vamos a ver la variable diaSeleccionado: {{ diaSeleccionado }}
</p>
<p>
  Vamos a ver la variable personalInfo: {{ personalInfo }}
</p>
<p>
  Vamos a ver la variable soloApellido: {{ soloApellido }}
</p>

<p>
  Vamos a ver la variable estoyAprendiendo: {{ estoyAprendiendo }}
</p>
<p>
  Vamos a ver la variable meGustanLosVegetales: {{ meGustanLosVegetales }}
</p>
```
{% endcode-tabs-item %}
{% endcode-tabs %}

Deberías hacer algo así, y tu resultado se deberá ver así:👇

![](../.gitbook/assets/variables-2.gif)

{% hint style="info" %}
**Por si tienes alguna duda. Aquí te explicamos cómo funciona: 👷‍♀️  
  
1.** Este es un conocimiento de Angular 🅰️💖:  
 Acabaste de ver que en el archivo con extensión **.html** tiene algo nuevo, tiene un par de llaves dobles **{{ }}**, el uso de estas llaves se le llama interpolación, su nombre en inglés es "interpolation", es un mecanismo de Angular para ver en una **template** \(nuestro archivo app.component.html\) una variable.
{% endhint %}

## Paso 4: ¿Qué es una función? 🤔 <a id="paso-2-que-es-una-variable"></a>

Cuando se desarrolla una aplicación, es muy habitual utilizar una y otra vez las mismas instrucciones. Por eso una función se utiliza para agrupar las indicaciones que necesitamos para realizar una tarea concreta y que se puedan reutilizar fácilmente.  
Vamos a reemplazar nuestras variables anteriores del archivo **app.component.ts** por este código:

{% code-tabs %}
{% code-tabs-item title="app.component.ts" %}
```javascript
variable = '';

guardemosUnValorEnUnaVariable(valor) {
  this.variable = valor;
}
```
{% endcode-tabs-item %}
{% endcode-tabs %}

Deberías hacer algo así, y tu resultado se deberá ver así:👇

![](../.gitbook/assets/variable-3.gif)

Vamos a reemplazar ****el contenido del archivo **app.component.html** por este código:

{% code-tabs %}
{% code-tabs-item title="app.component.html" %}
```markup
<p>
  Vamos a ver la variable variable: {{ variable }}
</p>
```
{% endcode-tabs-item %}
{% endcode-tabs %}

Deberías hacer algo así, y tu resultado se deberá ver así:👇

![](../.gitbook/assets/variable-5.gif)

## Paso 5: Aprendamos que es If y que es else ✅ <a id="paso-2-que-es-una-variable"></a>

Esta es la estructura más utilizada en JavaScript y en la mayoría de lenguajes de programación. La usamos para tomar decisiones, vamos a ver un ejemplo de su escritura y su uso.  
Adiciona este código en tu archivo **app.component.ts**

{% code-tabs %}
{% code-tabs-item title="app.component.ts" %}
```javascript
mostrarMensajeEnVariable = true;

ngOnInit() {
  this.queMensajeMostrar();
}

queMensajeMostrar() {
  if (this.mostrarMensajeEnVariable == true) {
    this.guardemosUnValorEnUnaVariable(
      "El valor de la condición es igual a true 👍"
    );
  } else {
    this.guardemosUnValorEnUnaVariable(
      "El valor de la condición es diferente a true!, 👎"
    );
  }
}
```
{% endcode-tabs-item %}
{% endcode-tabs %}

Deberías hacer algo así, y tu resultado se deberá ver así:👇

![](../.gitbook/assets/variable-6.gif)

{% hint style="info" %}
**Por si tienes alguna duda. Aquí te explicamos cómo funciona: 👷‍♀️  
  
1.** Este es un conocimiento de Angular 🅰️💖:  
Acabaste de ver la función `ngOnInit(),`esta es propia de Angular y tiene la particularidad de ser la primer función en ejecutarse cuando cargamos nuestro componente; **ngOnInit\(\)** es la primer función que será llamada y dentro de ella encontramos el llamado a la función `queMensajeMostrar()`, haciendo esto, podremos garantizar que se ejecute apenas inicie nuestra aplicación.

**2.** **if** `this.mostrarMensajeEnVariable == true`, entonces nos mostrará un mensaje especifico, si no, **else**, tendremos un mensaje diferente.
{% endhint %}

🎉 ¡**LO LOGRASTE!** 🎉

{% hint style="info" %}
\*\*\*\*[**Aquí**](https://stackblitz.com/edit/angular-conoce-javascript) puedes encontrar el ejercicio resuelto.
{% endhint %}

## 😎 Tu Misión 😎

Con lo que aprendiste en **Primeros Pasos: Html 📝 & CSS 🎨,** ponle personalidad a tu aplicación 🎨👩‍🎨. 

Esta adición es para retar tu curiosidad, podrías proponer la solución que tu quieras. 

{% hint style="success" %}
Has completado los **Primeros pasos: JavaScript**, ahora vamos para nuestro primer desafío **👇**
{% endhint %}

