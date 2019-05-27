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

Adiciona este código en la línea 9 de tu archivo **app.component.html**

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

![](../.gitbook/assets/7.gif)

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

![](../.gitbook/assets/8.gif)

{% hint style="info" %}
**Por si tienes alguna duda. Aquí te explicamos cómo funciona: 👷‍♀️**

**1.** La etiqueta **\*ngFor** es una directiva principal, nos permite crear listas de datos en nuestro HTML sin adicionar más lineas de código. todo se genera dinámicamente según el tamaño de la lista de elementos a mostrar.

**2.** Veremos como se visualizara en pantalla el contenido de **strengths** sin necesidad de escribir una por una en el archivo **app.component.html.**
{% endhint %}

## Paso 5: Personalizo mi tarjeta sin esfuerzo 💅🏼  <a id="paso-2-vamos-a-armar-el-esqueleto"></a>

‌Vamos a hacer que de una lista de opciones solo se nos muestre una.

para esto vamos a usar la directiva NgSwitch.

Adiciona este código en la línea 25 de tu archivo **app.component.html**

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

![](../.gitbook/assets/10.gif)

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
\*\*\*\*
{% endhint %}

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

![](../.gitbook/assets/10.gif)

{% hint style="info" %}
**Por si tienes alguna duda. Aquí te explicamos cómo funciona: 👷‍♀️**

**1.** La etiqueta **\[ngSwitch\]** es una directiva estructural que agrega o no código \(mostrar u ocultar vistas\) cuando la condición coincide con la expresión de cambio.

**2.** Veremos como se visualizara en pantalla el elemento siempre y cuando exista un valor pink expresado en el siguiente código **\*ngSwitchCase="'pink'"**.
{% endhint %}

