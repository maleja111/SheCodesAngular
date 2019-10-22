---
description: "En este nivel, vamos a aprender ¿Qué es JavaScript \U0001F913?, ¿Para que sirve? y ¿Cómo podemos sacarle el mejor provecho a este lenguaje?."
---

# Primeros pasos: JavaScript

## 💡 Introducción 💡

JavaScript \(JS\) es un lenguaje de programación que le ha otorgado rapidez y efectos atractivos a las páginas web, mediante su uso combinado junto a HTML, CSS y otros lenguajes.   
Hoy vamos a conocer aspectos generales pero muy útiles de forma dinámica. 🎮

![JavaScript Logo](../.gitbook/assets/image%20%281%29.png)

\*\*\*\*[**¡Aquí puedes encontrar el demo!**](https://angular-catparty.stackblitz.io/)\*\*\*\*

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
  
**2.** Vemos una palabra nueva llamada **this**, ¿Qué es **this**?`this`es una palabra reservada de JavaScript \(palabra reservada significa que no puedes crear una variable que este escrita exactamente igual\), se hace referencia al objeto, que contiene el método donde se invoca.  
En este caso`this.dias`hace referencia a la variable `dias` que  acabamos de crear y \[0\] hace referencia a la posición del array que queremos seleccionar, la primero seria el 0 con lunes, 1 con martes, 2 con miércoles y así sucesivamente.  
  
**3.** La misma referencia de`this` se hace en la variable `personalInfo` aquí, los objetos están conformados por una estructura`{llave: valor},` donde llave será la referencia para acceder al contenido, es por eso que cuando escribimos `this.personalInfo.apellido`, el resultado es `"Giraldo"`, porque estamos accediendo a la llave`apellido`de nuestra variable`personalInfo.`
{% endhint %}

## Paso 2: ¿Qué es una variable? **🗄** <a id="paso-2-que-es-una-variable"></a>

Una variable es un espacio de almacenamiento, aquí podemos guardar cualquier tipo de dato que te puedas imaginar, como una cadena de caracteres, un valor numérico o estructuras un poco más específicas. Adiciona este código en tu archivo **app.component.ts**Add fileJavaScript exit: ⌘↩

```text
  // Vamos a crear una serie de variables de diferentes tipos  // Numérico  iva = 16;        // Variable tipo entero  total = 234.65;  // Variable tipo decimal​  // Cadenas de texto, tambien se les dicen String  mensaje = 'Bienvenid@ a She Codes Angular';  nombreCompleto = 'Alejandra Giraldo';​  // Arrays - Arreglos  dias = ['Lunes', 'Martes', 'Miércoles', 'Jueves', 'Viernes', 'Sábado', 'Domingo'];  diaSeleccionado = this.dias[0];    // diaSeleccionado = 'Lunes'​    // Object - Objetos  personalInfo = {'nombre': 'Alejandra', 'apellido': 'Giraldo', 'cedula': 123456};  soloApellido = this.personalInfo.apellido;    // soloApellido = 'Giraldo'​  // Boolean - Booleanos  estoyAprendiendo = true;  meGustanLosVegetales = false;
```

‌

Deberías hacer algo así, y tu resultado se deberá ver así:👇

