---
description: >-
  En este reto aprendamos sobre directivas. Una directiva se representa como un
  atributo en una etiqueta HTML; *ngIf, *ngFor o *ngSwitch son algunas y le
  adiciona un comportamiento definido.
---

# Básico 2: Creando mi perfil 👤

## 💡 Introducción 💡

¡Que divertido fue aprender a usar imagenes de gatos!  
¡ahora vayamos por la creación de nuestro propio perfil!  

¿Te gustaría crear la base de lo que podría ser tu propio perfil en tu aplicación web? Vamos a crear un perfil, que muestre u oculte información según nuestros propios datos, así podremos personalizarlo ¡como más nos guste! [**¡Aquí puedes encontrar el demo!**](https://stackblitz.com/edit/angular-mi-perfil)\*\*\*\*

## Paso 1: **Creemos nuestra App de Angular** ⭐️

Entra a **www.stackblitz.com**, y verás algo como esto:

![](../.gitbook/assets/1.png)

![](../.gitbook/assets/screen-shot-2019-05-25-at-1.56.29-pm.png)

## Paso 2: **Vamos a armar el esqueleto 💀👤**

Vamos a crear el entorno de nuestra aplicación. Para ello iremos al archivo **app.component.html** y borramos todo el contenido para adicionar lo siguiente:

{% code-tabs %}
{% code-tabs-item title="app.component.html" %}
```markup
<div class="card">
  <div class="profile-picture">
    <div class="profile-picture-outer-radius"></div>
  </div>
  
  <div class="infobox">
    <p class="infobox-username" *ngIf="name">{{name}}</p>
  </div>
  <div class="floating-action-button"> + </div>
</div>
```
{% endcode-tabs-item %}
{% endcode-tabs %}

Deberías hacer algo así, y tu resultado se deberá ver así:👇

![](../.gitbook/assets/6.gif)

{% hint style="info" %}
**Por si tienes alguna duda. Aquí te explicamos cómo funciona: 👷‍♀️**

**1.** La etiqueta **\*ngIf** es una directiva que incluye una condición basada en el valor de una variable que la contiene. Cuando la expresión se evalúa como verdadera, Angular realiza la visualización de la porción de código, y cuando es falsa o nula, Angular realiza la **NO** visualización de la porción de código.
{% endhint %}

## Paso 3: Reforcemos el concepto de \*ngIf 🤓 <a id="paso-2-vamos-a-armar-el-esqueleto"></a>

‌Vamos a suponer que deseamos filtrar la información que vamos a mostrar en nuestro perfil. ¿Cómo podremos lograr eso?

Adiciona este código en la línea 8 de tu archivo **app.component.html**

{% code-tabs %}
{% code-tabs-item title="app.component.html" %}
```markup
<div class="">
  <p class="align-left" *ngIf="following > 100">Following:</p><p class="align-right">{{following}}</p>  
</div>

<div class="clear-float" *ngIf="following > 700">
  <p class="align-left">Followers:</p><p class="align-right">{{followers}}</p>  
</div>
```
{% endcode-tabs-item %}
{% endcode-tabs %}

Deberías hacer algo así, y tu resultado se deberá ver así:👇​

![](../.gitbook/assets/13.gif)

{% hint style="info" %}
**Por si tienes alguna duda. Aquí te explicamos cómo funciona: 👷‍♀️**

**1.** La etiqueta **\*ngIf** también nos permite realizar operaciones lógicas, tanto así, que podemos hacer que una condición haga que se visualice o no los datos.   
  
Si el número de following es mayor a 100 podré ver esta información, de lo contrario se ocultarán.   
Si el número de followers es mayor a 700 podré ver esta información, de lo contrario se ocultarán.
{% endhint %}

## Paso 4: Datos y más datos sin codificar tanto 🧙🏻‍♀️ <a id="paso-2-vamos-a-armar-el-esqueleto"></a>

‌Vamos a suponer que deseamos filtrar la información que vamos a mostrar en nuestro perfil. ¿Cómo podremos lograr eso?

Adiciona este código en la línea 16 de tu archivo **app.component.html**

{% code-tabs %}
{% code-tabs-item title="app.component.html" %}
```markup
<div class="clear-float" *ngFor="let strength of strengths">
    <p class="align-left">{{strength.text}}</p><p class="align-right">{{strength.level}}</p>  
</div>
```
{% endcode-tabs-item %}
{% endcode-tabs %}

Deberías hacer algo así, y tu resultado se deberá ver así:👇​

![](../.gitbook/assets/14.gif)

{% hint style="info" %}
**Por si tienes alguna duda. Aquí te explicamos cómo funciona: 👷‍♀️**

**1.** La etiqueta **\*ngFor** es una directiva principal, nos permite crear listas de datos en nuestro HTML sin adicionar más lineas de código. todo se genera dinámicamente según el tamaño de la lista de elementos a mostrar.

**2.** Veremos como se visualizara en pantalla el contenido de **strengths** sin necesidad de escribir una por una en el archivo **app.component.html.**
{% endhint %}

## Paso 5: Personalizo mi tarjeta sin esfuerzo 💅🏼  <a id="paso-2-vamos-a-armar-el-esqueleto"></a>

‌Vamos a hacer que de una lista de opciones solo se nos muestre una.

para esto vamos a usar la directiva NgSwitch.

Adiciona este código en la línea 20 de tu archivo **app.component.html**

{% code-tabs %}
{% code-tabs-item title="app.component.html" %}
```markup
<div class="clear-float" *ngFor="let person of people" [ngSwitch]="person.color">
  <div *ngSwitchCase="'pink'" [style.color]="person.color">
    <p class="align-left">{{person.name}}</p><p class="align-right">{{person.color}}</p>
  </div>
</div>
```
{% endcode-tabs-item %}
{% endcode-tabs %}

Deberías hacer algo así, y tu resultado se deberá ver así:👇​

![](../.gitbook/assets/15.gif)

{% hint style="info" %}
**Por si tienes alguna duda. Aquí te explicamos cómo funciona: 👷‍♀️**

**1.** La etiqueta **\[ngSwitch\]** es una directiva estructural que agrega o no código \(mostrar u ocultar vistas\) cuando la condición coincide con la expresión de cambio.

**2.** Veremos como se visualizara en pantalla el elemento siempre y cuando exista un valor pink expresado en el siguiente código **\*ngSwitchCase="'pink'"**.
{% endhint %}

## Paso 6: Vamos a adicionar la lógica 🧠  <a id="paso-2-vamos-a-armar-el-esqueleto"></a>

Ahora vamos a modificar el archivo **app.component.ts**, ****en ****este vamos a adicionar la declaración de variables que vimos en el archivo **app.component.html**.  
En este archivo vamos a reemplazar su contenido, vamos a reemplazar el actual código por este:

{% code-tabs %}
{% code-tabs-item title="app.component.ts" %}
```typescript
import { Component } from '@angular/core';

@Component({
  selector: 'my-app',
  templateUrl: './app.component.html',
  styleUrls: ['./app.component.css']
})
export class AppComponent {
  name = 'Alejandra Giraldo';
  following = 5001;
  followers = 10002;

  strengths = [{ text: 'English', level: 'Basic' }, { text: 'HTML', level: 'High' }, { text: 'Testing', level: 'Low' }];

  people = [
    {
      "name": "Vanessa M.",
      "age": 16,
      "color": 'red'
    },
    {
      "name": "Carlos Angulo",
      "age": 25,
      "color": 'green'
    },
    {
      "name": "Maleja",
      "age": 21,
      "color": 'pink'
    }
  ];

}

```
{% endcode-tabs-item %}
{% endcode-tabs %}

Deberías hacer algo así, y tu resultado se deberá ver así:👇

![](../.gitbook/assets/11.gif)

{% hint style="info" %}
**Por si tienes alguna duda. Aquí te explicamos cómo funciona: 👷‍♀️**

**1.** Realizamos la declaración de variables para:  
**name:** línea 9 donde le asignamos un valor tipo string.  
**following:** línea 10 donde le asignamos un valor tipo entero.  
**followers:** línea 11 donde le asignamos un valor tipo entero.  
**strengths**: línea 13 donde le asignamos un valor tipo objeto, donde almacenamos la lista de fortalezas a visualizar en el perfil.  
**people:** línea 15 donde le asignamos un valor tipo objeto, donde almacenamos la lista de mejores amigos de tu perfil.
{% endhint %}

## Paso Final: Personaliza tu perfil 🎨 <a id="paso-final-personaliza-tu-aplicacion"></a>

¡Vamos a hacer que nuestro perfil tenga color agregando CSS!   
¿recuerdas las clases que usamos en nuestro **app.component.html**?   
¡llego el tiempo de usarlas!   
Reemplaza el contenido de **app.component.css** con éste:

{% code-tabs %}
{% code-tabs-item title="app.component.css" %}
```css
body {
  background: #ededed; 
  font-family: "Century Gothic", CenturyGothic, Geneva, AppleGothic, sans-serif;
  user-select: none;
}

.card {
  width: 300px;
  height: 550px;
  margin: 0 auto;
  background: #22313F;
  border-radius: 4px;
  box-shadow: 6px 6px 6px rgba(0, 0, 0, 0.25);
}

.profile-cover-container {
  background-size: cover;
  width: 100%;
  height: 175x;
  overflow: hidden;
  float: left;
}
.profile-cover-container img {
  width: 100%;
  height: auto;
  border-top-right-radius: 4px;
  border-top-left-radius: 4px;
  z-index: 0;
}

.cover-overlay {
  z-index: 1;
  border-top-right-radius: 35%;
  border-top-left-radius: 35%;
  margin-top: -50px;
  width: 100%;
  height: 60px;
  background: #22313F;
  position: relative;
}

.profile-picture {
  background-image: url("https://pbs.twimg.com/profile_images/1057449615841214466/KXT83JRQ_400x400.jpg");
  background-size: cover;
  top: 65px;
  width: 150px;
  height: 150px;
  border-radius: 50%;
  margin: auto;
  display: block;
  z-index: 1;
  border: 1px solid #949599;
  position: relative;
}

.profile-picture-outer-radius {
  width: 158px;
  height: 157px;
  top: -5px;
  left: -5px;
  border-radius: 50%;
  border: 1px solid #949599;
  position: absolute;
}

.infobox {
  margin: 80px 25px;
  color: #949599;;
}
.infobox p {
  margin-top: 10px;
  margin-bottom: 0;
}
.infobox-username {
  font-size: 1.5em;
  text-align: center;
  color: white;
}

.align-left {
  float: left;
  text-align: left;
}

.align-right {
  float: right;
  text-align: right;
}

.clear-float {
  clear: both;
}

.floating-action-button {
  height: 50px;
  width: 50px;
  border-radius: 50%;
  background: #35B4E1;
  background: -webkit-radial-gradient(#35B4E1, #18B984); 
  background: -o-radial-gradient(#35B4E1, #18B984);
  background: -moz-radial-gradient(#35B4E1, #18B984);
  background: radial-gradient(#35B4E1, #18B984);
  box-shadow: 2px 2px 6px rgba(0, 0, 0, 0.25);
  cursor: pointer;
  font-size: 2.5em;
  color: white;
  text-align: center;
  position: relative;
  float: right;
  right: 27px;
}
.floating-action-button:hover {
  background: #18b984;
  background: -webkit-linear-gradient(#18B984, #35B4E1); 
  background: -o-linear-gradient(#18B984, #35B4E1);
  background: -moz-linear-gradient(#18B984, #35B4E1);
  background: linear-gradient(#18B984, #35B4E1);
  box-shadow: 4px 4px 6px rgba(0, 0, 0, 0.25);
}
```
{% endcode-tabs-item %}
{% endcode-tabs %}

Deberías hacer algo así, y tu resultado se deberá ver así:👇

![](../.gitbook/assets/12.gif)

## 😎 Tu Misión 😎 <a id="tu-mision"></a>

Parece que nuestra aplicación está lista excepto por un pequeño detalle 😵. Debería de poder agregar elementos con información como correo electrónico y profesión.

⭐️ Utiliza lo que ya conoces como: **data** [**binding**](https://alligator.io/angular/data-binding-angular/)**,** las diferentes directivas y variables para adicionar mas campos en nuestra tarjeta.‌ y ¡personaliza con tu foto, datos y colores favoritos!

**💪💪**¡¡Felicitaciones!! ¡Llegaste muy lejos! **💪💪**‌

{% hint style="info" %}
**Nota:**

Si necesitas en casa y necesitas ayuda con este ejercicio puedes contactar a:

Alejandra Giraldo  
Twitter: @maleja111  
Correo: magiraldodevelop@gmail.com
{% endhint %}

