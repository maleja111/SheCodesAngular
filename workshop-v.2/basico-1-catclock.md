---
description: >-
  Es la hora de la acción ⏰. Crearemos una  alarma gatuna para despertar a
  nuestro gatito y que esté listo para la acción.
---

# Básico \#1: CatParty😺

## 💡 Introducción 💡

En este desafío haremos algo divertido aplicando conceptos básicos de Angular, los cuales  iremos describiendo a medida que realicemos cada uno de los pasos descritos abajo.  

\*\*\*\*[**¡Aquí puedes encontrar el demo!**](https://angular-catparty.stackblitz.io/)\*\*\*\*

¿Estás list@?

**Es hora de la Acción!!! 😝**

## Paso 1: **Creemos nuestra App de Angular** ⭐️

Primero iremos a el inicio de **Stackbliz** y crearemos una App de Angular.

![Vamos al inicio de Stackblitz y damos click en el bot&#xF3;n.](../.gitbook/assets/screen-shot-2019-05-25-at-10.41.44-pm.png)

![Seleccionamos la opci&#xF3;n de Angular](../.gitbook/assets/screen-shot-2019-05-25-at-10.48.40-pm.png)

![Ver&#xE1;s algo como esto &#x1F446;](../.gitbook/assets/screen-shot-2019-05-25-at-10.52.23-pm.png)

Seleccionamos el texto  del archivo **app.component.html**, lo borramos \(presionando la tecla delete de tu compu 💻\) y guardamos los cambios, seleccionando en la parte superior la opción de 'Save' 💾

![](../.gitbook/assets/webp.net-gifmaker-1.gif)

## Paso 2: **Añadamos un título** 🏁

Iremos al archivo **app.component.html** y vamos a usar unas etiquetas o tags de HTML para poner un titulo.

Copiaremos lo siguiente en el archivo **app.component.html** 

{% code title="app.component.html" %}
```markup
<h1>CatClock 😼</h1>
```
{% endcode %}

Deberías ver algo así: 👇

![A&#xF1;adimos el t&#xED;tulo a nuestra App](../.gitbook/assets/screen-shot-2019-05-25-at-11.05.04-pm.png)

{% hint style="info" %}
**¿Qué es una etiqueta?**👇

Las etiquetas o tags son la forma de escribir código HTML, es la semántica del HTML. Son fragmentos de texto rodeados por corchetes angulares `< >,` que tienen funciones y usos específicos, existen muchas etiquetas como **&lt;div&gt;&lt;/div&gt;**, **&lt;p&gt;&lt;/p&gt;**, ****entre otras.

**&lt;h1&gt;:** Es una etiqueta para los títulos

**&lt;img&gt;**: Es una etiqueta para imágenes
{% endhint %}

## Paso 3: **Añadamos una imagen de un gatito** 🖼️

Debajo de nuestro titulo en el archivo **app.component.html**, ****vamos a añadir la etiqueta para las imágenes, con una imagen de un gatito.

Copiaremos lo siguiente en el archivo **app.component.html** 

{% code title="app.component.html" %}
```markup
<h1>CatClock 😼</h1>

<img id="catImage" src="https://s3.amazonaws.com/media.skillcrush.com/skillcrush/wp-content/uploads/2016/08/normalTime.jpg" alt="CatClock">
```
{% endcode %}

Verás algo así: 👇

![As&#xED; puedes cualquier imagen en tu html](../.gitbook/assets/screen-shot-2019-05-25-at-11.17.29-pm.png)

## Paso 4: **Añadamos un texto dinámico** 📝

Vamos a usar un término en Angular llamado **Interpolación** \(conocida en inglés como "string interpolation"\),  nos permite desplegar algo declarado en código en nuestra vista o HTML. Crearemos una variable llamada "**party**" en el archivo **app.component.ts**.

Podemos reemplazar la variable que estaba creada llamada **name** y la renombramos a **party** en el archivo **app.component.ts** dentro del **export class AppComponent** y lo demas no lo borramos.

Le quitamos el valor de **'Angular'** y le pondremos **'Party'**

{% code title="app.component.ts" %}
```typescript
export class AppComponent  {
  party = 'Party';
}
```
{% endcode %}

Verás algo así: 👇

![](../.gitbook/assets/webp.net-gifmaker-3.gif)

Ahora añadamos nuestra variable a nuestro título en el archivo **app.component.html**.

{% hint style="info" %}
**¿Qué es una variable?** es como un caja, \(donde puedes poner cosas 🎁\). Ésta almacenará lo que nosotros queramos, textos, números, etc **👍**
{% endhint %}

Para usar la interpolación se usan dos llaves **{{ }}** dobles.

{% code title="app.component.html" %}
```markup
<h1>CatClock 😼 {{party}} </h1>

<img id="catImage" src="https://s3.amazonaws.com/media.skillcrush.com/skillcrush/wp-content/uploads/2016/08/normalTime.jpg" alt="CatClock">
```
{% endcode %}

## Paso 5: **Crearemos una imagen dinámica**  🖌️

Sabemos cómo crear texto dinámico, ahora vamos a crear una imagen dinámica.

Para ello copiaremos la url de la imagen que esta en el 'src' y la pondremos en una nueva variable.

Crearemos una variable llamada **urlImage** y pondremos la url copiada allí.

En el archivo **app.component.ts** ve hasta la línea 8, donde encontraras el **export class AppComponent** y añade dentro de el, debajo de la variable **party**, ****la variable de urlImage, no borres lo demás, te debe quedar algo así en el **export class AppComponent**: ****👇

{% code title="app.component.ts" %}
```typescript
export class AppComponent  {
  party = 'Party';
  urlImage = 'https://s3.amazonaws.com/media.skillcrush.com/skillcrush/wp-content/uploads/2016/08/normalTime.jpg';
}
```
{% endcode %}

Luego en el archivo  **app.component.html** borraremos del src la url de la imagen y pondremos en su lugar el nombre de la nueva variable entre llaves dobles. 

Quedaría algo así: 👇

{% code title="app.component.html" %}
```markup
<h1>CatClock 😼 {{party}} </h1>

<img id="catImage" src={{urlImage}} alt="CatClock">
```
{% endcode %}

![Creamos nuestra imagen din&#xE1;mica](../.gitbook/assets/webp.net-gifmaker-4.gif)

## Paso 6: **Remplacemos nuestra imagen con algo de lógica** 🧠

Ahora lo que haremos es que cuando reemplacemos el texto de nuestra imagen en el código, esta cambiará.

Para ellos usaremos algo de lógica, colocaremos un **if** \(nos sirve para preguntar\) en nuestro archivo **app.component.ts**, donde preguntaremos si el texto de la variable **party** es igual a 'Party' si esto se cumple se mostrará una nueva imagen. 

Copia debajo la variable **urlImage** el siguiente código:

{% code title="app.component.ts" %}
```typescript
export class AppComponent  {
  party = 'Party';
  urlImage = 'https://s3.amazonaws.com/media.skillcrush.com/skillcrush/wp-content/uploads/2016/08/normalTime.jpg';
  
  constructor() {
    if(this.party === 'Party'){
      this.urlImage = 'https://s3.amazonaws.com/media.skillcrush.com/skillcrush/wp-content/uploads/2016/08/partyTime.jpg';
    }
  }
}
```
{% endcode %}

![](../.gitbook/assets/webp.net-gifmaker-5.gif)

Si reemplazas el texto la variable **party**, podrás ver la imagen inicial. Con el valor 'Party' veras los gatos saltando.

¡Felicitaciones hemos terminado el primer desafío!

🎉 ¡**LO LOGRASTE!** 🎉

{% hint style="info" %}
\*\*\*\*[**Aquí**](https://stackblitz.com/edit/angular-catparty) puedes encontrar el ejercicio resuelto.
{% endhint %}

## 😎 Tu Misión Especial 😎

Parece que nuestra aplicación está lista pero debemos editar el texto desde la lógica 😵. 

⭐️ Se podría poner un botón que al darle click nos cambie el texto, pero esto te lo dejamos de tarea ****⭐️

A medida que vas desarrollando los demás desafíos aprenderás como añadir un botón que al presionarlo pueda realizar este cambio, o puedes poner un campo de texto o idearte tu propia solución.

Esta adición es para retar tu curiosidad, podrías proponer la solución que tu quieras. 

{% hint style="success" %}
Has completado el **desafío \#1**, ahora vamos a el **desafío \#2 👇**
{% endhint %}

{% hint style="info" %}
**Nota:**

Si necesitas mentoría con este ejercicio puedes contactar a:

Vanessa M. Aristizabal  
Twitter: @vanessamarely  
Correo: vanessamarely@gmail.com
{% endhint %}

