---
description: >-
  En este desafío aprenderemos conceptos básicos de Angular y un poco sobre
  directivas
---

# 👮 Básico \#1 - Directivas👮

## 💡 Introducción 💡

En este desafío haremos algo divertido aplicando conceptos básicos de Angular, en especial sobre directivas, los cuales  iremos describiendo a medida que realicemos cada uno de los pasos descritos abajo.  

**¡**[**Aquí puedes encontrar el demo**](https://buttons-emojis.stackblitz.io)**!**

¿Estás list@?

**Es hora de la Acción!!! 😝**

## Paso 1: **Creemos nuestra App de Angular** ⭐️

Primero iremos a el inicio de **Stackbliz** y crearemos una App de Angular.

![Vamos al inicio de Stackblitz y damos click en el bot&#xF3;n.](../.gitbook/assets/screen-shot-2019-05-25-at-10.41.44-pm.png)

![Seleccionamos la opci&#xF3;n de Angular](../.gitbook/assets/screen-shot-2019-05-25-at-10.48.40-pm.png)

![Ver&#xE1;s algo como esto &#x1F446;](../.gitbook/assets/screen-shot-2019-05-25-at-10.52.23-pm.png)

En la parte izquierda donde dice "Files", seleccionaremos el archivo llamado **app.component.html**. 

Dentro del archivo seleccionamos su texto,  lo borramos \(presionando la tecla delete de tu compu 💻\) y guardamos los cambios, seleccionando en la parte superior la opción de '**Save**' 💾 o la tecla rápida **cmd** + **S** o en windows **Ctrl** + **S.** 

![](../.gitbook/assets/webp.net-gifmaker-1.gif)

## Paso 2: **Añadamos un título** 🏁

En el mismo archivo **app.component.html,** vamos a usar unas etiquetas o tags de **HTML** para poner un título.

Copiaremos lo siguiente en el archivo **app.component.html** 

{% code-tabs %}
{% code-tabs-item title="app.component.html" %}
```markup
<h1>🤪 Emoji 🤪</h1>
```
{% endcode-tabs-item %}
{% endcode-tabs %}

Deberías ver algo así: 👇

![A&#xF1;adamos un t&#xED;tulo](../.gitbook/assets/screen-shot-2019-11-03-at-10.03.11-am.png)

{% hint style="info" %}
**¿Qué es una etiqueta?**👇

Como lo vimos anteriormente, las etiquetas o tags son la forma de escribir código HTML, es la semántica del HTML. Son fragmentos de texto rodeados por corchetes angulares `< >,` que tienen funciones y usos específicos, existen muchas etiquetas como **&lt;div&gt;&lt;/div&gt;**, **&lt;p&gt;&lt;/p&gt;**, ****entre otras.

**&lt;h1&gt;:** Es una etiqueta para los títulos más grandes
{% endhint %}

Existe un concepto en Angular que se llama la **interpolación**, la cual nos permite mostrar lo que definamos en la lógica, puede ser un titulo y mostrarlo en la vista o **HTML**.

Así que usaremos la interpolación para nuestro título.

En el archivo **app.component.ts**, vas a encontrar varias líneas de código, como el siguiente:

![app.component.ts](../.gitbook/assets/screen-shot-2019-11-03-at-12.08.41-pm.png)

Nuestro código lo pondremos dentro de las llaves que inician en la línea 8. Entonces modificaremos la variable **name** y le pondremos **title** y dentro de las comillas pondremos el texto que colocamos en nuestras etiquetas &lt;h1&gt;&lt;/h1&gt;. Así:

{% code-tabs %}
{% code-tabs-item title="app.component.ts" %}
```typescript
import { Component } from '@angular/core';

@Component({
  selector: 'my-app',
  templateUrl: './app.component.html',
  styleUrls: [ './app.component.css' ]
})
export class AppComponent  {
  title = '🤪 Emoji 🤪';
}
```
{% endcode-tabs-item %}
{% endcode-tabs %}

 

En el archivo de **app.component.html** dentro de las etiquetas &lt;h1&gt;&lt;/h1&gt; pondremos nuestra variable definida. Así:

{% code-tabs %}
{% code-tabs-item title="app.component.html" %}
```markup
<h1>{{title}}</h1>
```
{% endcode-tabs-item %}
{% endcode-tabs %}

![Usando la interpolaci&#xF3;n](../.gitbook/assets/ezgif.com-gif-maker.gif)

## Paso 3: **Añadamos un botón** 🆒

En nuestra vista o **HTML** incluiremos no solo uno sino varios botones y en lugar de poner dentro de ellos texto, pondremos emojis.

Entonces manos a la obra 😀.

En nuestro **app.component.html** añadiremos las etiquetas de un botón, &lt;button&gt;&lt;/button&gt; y repetiremos esta línea 3 veces y dentro de ella pondremos diferentes emojis.

{% code-tabs %}
{% code-tabs-item title="app.component.html" %}
```markup
<h1>{{title}}</h1>
<button></button>
```
{% endcode-tabs-item %}
{% endcode-tabs %}

![A&#xF1;adamos nuestros botones](../.gitbook/assets/ezgif.com-gif-maker-1.gif)

Nuestro **app.component.html** quedaría así:

{% code-tabs %}
{% code-tabs-item title="app.component.html" %}
```markup
<h1>{{title}}</h1>
<button>😀</button>
<button>😢</button>
<button>🤪</button>
```
{% endcode-tabs-item %}
{% endcode-tabs %}

## Paso 4: Pongamos algunas Directivas

Las Directivas son unas instrucciones que nos permiten añadir ciertos comportamientos a nuestra vista. Comportamientos como mostrar u ocultar el código. nos permite recorrer una colección de datos, entre otros.

Entonces usaremos nuestros botones para que al darles clic nos muestre una imagen que represente el emoji de nuestro botón, y al dar clic nuevamente sobre el mismo botón la oculte. Seguiremos los siguientes pasos:

* Crearemos 3 variables llamadas: **happy**, **sad**, **crazy** y a todas les asignaremos el valor de false. Estas variables las pondremos debajo de nuestra variable title en nuestro **app.component.ts**.

{% hint style="info" %}
**Te recuerdo ¿Qué es una variable?** es como un caja, \(donde puedes poner cosas 🎁\). Ésta almacenará lo que nosotros queramos, textos, números, etc **👍**
{% endhint %}

{% code-tabs %}
{% code-tabs-item title="app.component.ts" %}
```typescript
import { Component } from '@angular/core';

@Component({
  selector: 'my-app',
  templateUrl: './app.component.html',
  styleUrls: [ './app.component.css' ]
})
export class AppComponent  {
  title = '🤪 Emoji 🤪';
  happy= false;
  sad= false;
  crazy= false;
}

```
{% endcode-tabs-item %}
{% endcode-tabs %}

* Como queremos que al darle clic a nuestros botones este muestre o oculte una imagen, entonces debemos de añadirle a cada uno el evento clic \(Este hace referencia a un concepto que se llama **Event Binding**\).

{% hint style="info" %}
**Event Binding.** Ella nos permite agregar eventos a nuestra vista. En este caso utilizamos el evento de **Click**, pero pueden ser muchos tipos: **\(keyup\)**, **\(change\)**, **\(resize\)**, etc  💻
{% endhint %}

Entonces a nuestras etiquetas le  añadiremos el click, y le asignaremos a cada botón la variable que creamos respectiva a cada botón, pero para cambiar ese valor de **false**, le pondremos a cada una de nuestras variables el signo de admiración **!**, esto lo que hace es negar nuestra variable.  Si nuestra variable tenia un valor de **true**, al darle clic esta se negara, significa que se convertirá en **false**. Si nuestra variable tenia asignado un **false**, al darle clic se negará en otras palabras se convertirá en **true**. 

![A&#xF1;adiendo el click](../.gitbook/assets/ezgif.com-gif-maker-7.gif)

{% code-tabs %}
{% code-tabs-item title="app.component.html" %}
```markup
<h1>{{title}}</h1>
<button (click)="happy=!happy">😀</button>
<button (click)="sad=!sad">😢</button>
<button (click)="crazy=!crazy">🤪</button>
```
{% endcode-tabs-item %}
{% endcode-tabs %}

Si damos clic en cada botón, visualmente no notaremos el cambio, así que es hora de poner nuestras imágenes.

* Colocaremos nuestras imágenes, para esto pondremos dentro de una etiqueta &lt;section&gt;, la etiqueta &lt;img&gt; \(puedes usar la imagen que desees\), como son tres botones pondremos 3 &lt;section&gt;. Ubiquemos nuestras etiquetas debajo de cada etiqueta &lt;button&gt;&lt;/button&gt;. Así:

![Coloquemos nuestra &amp;lt;section&amp;gt; debajo de cada bot&#xF3;n](../.gitbook/assets/ezgif.com-gif-maker-8.gif)

El código que aparece en la imagen es el siguiente:

{% code-tabs %}
{% code-tabs-item title="app.component.html" %}
```markup
<h1>{{title}}</h1>
<button (click)="happy=!happy">😀</button>
<section>
  <img title="Happy" src="https://i.pinimg.com/originals/f2/ce/c9/f2cec98f06e8f66ff0bcfb2ffdb413eb.jpg" />
</section>
<button (click)="sad=!sad">😢</button>
<button (click)="crazy=!crazy">🤪</button>
```
{% endcode-tabs-item %}
{% endcode-tabs %}

* Dupliquemos el código de &lt;section&gt; para los otros dos botones y le cambiamos el title de la imagen y el src.

Duplicado queda así:

{% code-tabs %}
{% code-tabs-item title="app.component.html" %}
```markup
<h1>{{title}}</h1>
<button (click)="happy=!happy">😀</button>
<section>
  <img title="Happy" src="https://i.pinimg.com/originals/f2/ce/c9/f2cec98f06e8f66ff0bcfb2ffdb413eb.jpg" />
</section>
<button (click)="sad=!sad">😢</button>
<section>
  <img title="Happy" src="https://i.pinimg.com/originals/f2/ce/c9/f2cec98f06e8f66ff0bcfb2ffdb413eb.jpg" />
</section>
<button (click)="crazy=!crazy">🤪</button>
<section>
  <img title="Happy" src="https://i.pinimg.com/originals/f2/ce/c9/f2cec98f06e8f66ff0bcfb2ffdb413eb.jpg" />
</section>
```
{% endcode-tabs-item %}
{% endcode-tabs %}

 Si cambiamos los title y el src, nos queda así:

![Coloquemos los otros &amp;lt;section&amp;gt;](../.gitbook/assets/ezgif.com-gif-maker-9.gif)

Tu código debería quedar similar al siguiente, pero con las imágenes que hayas agregado de tu preferencia.

{% code-tabs %}
{% code-tabs-item title="app.component.html" %}
```markup
<h1>{{title}}</h1>
<button (click)="happy=!happy">😀</button>
<section>
  <img title="Happy" src="https://i.pinimg.com/originals/f2/ce/c9/f2cec98f06e8f66ff0bcfb2ffdb413eb.jpg" />
</section>
<button (click)="sad=!sad">😢</button>
<section>
  <img title="Sad" src="https://hips.hearstapps.com/hmg-prod.s3.amazonaws.com/images/sad-dog-1537347496.jpg?resize=480:*" />
</section>
<button (click)="crazy=!crazy">🤪</button>
<section>
  <img title="Crazy" src="https://townsquare.media/site/757/files/2014/08/names.jpg" />
</section>
```
{% endcode-tabs-item %}
{% endcode-tabs %}

* Ahora que tenemos nuestras imágenes vamos a añadir la directiva encargada de ocultar y mostrar el contenido. 

Para ello en cada &lt;section&gt; incluiremos el **\*ngIf**, esta directiva se encarga de ocultar o mostrar algo de acuerdo a la variable o función de la cual deseemos que se evalué algo.

Nosotros deseamos evaluar que si nuestras variables: **happy, sad, crazy** son verdaderas nos muestre la imagen que representa cada botón.

Para esa evaluación añadiremos en cada etiqueta nuestra directiva así:

```markup
<section *ngIf="happy">
```

Entonces por cada &lt;section&gt; incluiremos un **\*ngIf** con su variable.

![Coloquemos la directiva \*ngIf](../.gitbook/assets/ezgif.com-gif-maker-10.gif)

Como muestra la imagen anterior, al añadir nuestra directiva se irá ocultando la imagen.

Si damos clic sobre cada botón mostrará y ocultara nuestra imagen.

![Probando el evento click](../.gitbook/assets/ezgif.com-gif-maker-11.gif)



¡Felicitaciones hemos terminado el primer desafío básico!

🎉 ¡**LO LOGRASTE!** 🎉

{% hint style="info" %}
\*\*\*\*[**Aquí** ](https://stackblitz.com/edit/buttons-emojis)puedes encontrar el ejercicio resuelto.
{% endhint %}

## 😎 Tu Misión Especial 😎

Parece que nuestra aplicación está lista 😀. 

⭐️ Como vez la aplicación no luce tan bonita, entonces tu misión especial es ponerle algunos estilos para que luzca super cool!! ****⭐️

{% hint style="success" %}
Has completado el **desafío \#1 de nivel básico**, ahora vamos al **desafío básico \#2 👇**
{% endhint %}

{% hint style="info" %}
**Nota:**

Si necesitas mentoría con este ejercicio puedes contactar a:

Vanessa M. Aristizabal  
Twitter: @vanessamarely  
Correo: vanessamarely@gmail.com
{% endhint %}

