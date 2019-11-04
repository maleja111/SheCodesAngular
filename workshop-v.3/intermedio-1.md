---
description: >-
  Angular posee un concepto llamado Routing o Enrutamiento en español, este nos
  permite navegar en nuestra aplicación y en este desafío aprenderemos como
  hacerlo
---

# 📬Intermedio \#1 - Enrutamiento 📬

## 💡 Introducción 💡

En este desafío haremos algo divertido aplicando el concepto de enrutamiento, en cada uno de los pasos iremos abordando algunos conceptos de Angular, y crearemos nuestra nueva aplicación, que para este desafío haremos nuestra página personal o portafolio 😉.

**¡**[**Aquí puedes encontrar el demo**](https://routing-challenge1.stackblitz.io)**!**

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
<h1>My App 😉</h1>
```
{% endcode-tabs-item %}
{% endcode-tabs %}

![A&#xF1;adiendo el t&#xED;tulo](../.gitbook/assets/screen-shot-2019-11-03-at-3.57.50-pm.png)

Este paso es muy sencillo y ya lo hemos realizado en pasos anteriores, entonces le pondremos una clase a nuestro título y algo de estilos e incluso podemos incluirle una tipografía a nuestra aplicación.

Para la fuente puedes usar cualquier tipografía de google como la siguiente e importarla en el archivo styles.css y aplicar la fuente a todos los elementos, así:

{% code-tabs %}
{% code-tabs-item title="styles.css" %}
```css
/* Add application styles & imports to this file! */
@import url('https://fonts.googleapis.com/css?family=Open+Sans&display=swap');
* {
  font-family: 'Open Sans', sans-serif;
}
```
{% endcode-tabs-item %}
{% endcode-tabs %}

O puedes usar alguna otra del catalogo:

[https://fonts.google.com/](https://fonts.google.com/)

A nuestro título, lo pondremos dentro de la etiqueta header y le añadiremos un atributo clase. Como este es el nivel intermedio y ya sabes como poner algunos elementos, entonces no te mostraremos como poner la etiqueta o el color en el paso a paso.

##  Paso 3: Crearemos varios componentes 💪

Angular esta compuesto por varios **componentes**. En nuestra aplicación base existe un componente **App**, en él hemos estado añadiendo las diferentes instrucciones de los diferentes desafíos.

Cuando visitas una página Web, puedes observar que ella tiene muchas secciones como información de una empresa/producto, detalles de servicios, información de contacto entre otras. En este paso crearemos varios componentes, que serán donde iremos a colocar cada una de las secciones de nuestra página.

Dando clic derecho sobre la carpeta App, se desplegará un menu, en el seleccionaremos la opción **Angular Generator** y luego seleccionamos componente.

![Creando un componente](../.gitbook/assets/screen-shot-2019-11-03-at-4.24.32-pm.png)

Nos aparece un campo de texto donde colocaremos el nombre para nuestro componente.

![Incluimos el nombre de nuestro componente](../.gitbook/assets/screen-shot-2019-11-03-at-4.29.06-pm.png)

Le colocaremos el nombre home y presionamos enter y se nos creará nuestro nuevo componente.

![Componente Home](../.gitbook/assets/screen-shot-2019-11-03-at-4.32.56-pm.png)

Repetiremos el mismo paso para la creación del componente para crear otros 3 nuevos componentes, los llamaremos about, skills y contact.

Nuestra carpeta app, lucirá así:

![Nuestros nuevos componentes](../.gitbook/assets/screen-shot-2019-11-03-at-4.37.20-pm.png)

## Paso 4: Añadiendo un Menu 📋

Añadamos un componente para crear nuestro menu en el.

Entonces seguimos los pasos anteriores y crearemos nuestro componente menu.

![Componente Menu](../.gitbook/assets/screen-shot-2019-11-03-at-6.25.42-pm.png)

En el archivo **menu.component.html** vamos a poner la etiqueta &lt;nav&gt; donde pondremos cada uno de los links que nos llevarán a cada componente. Esos links los pondremos en una lista.

![Lista de links](../.gitbook/assets/ezgif.com-gif-maker-12.gif)

Nuestra lista se verá parecida al siguiente código, pero en la vista o **HTML** aún  no veremos nuestra lista hasta que la incluyamos en nuestro componente  App. 

{% code-tabs %}
{% code-tabs-item title="menu.component.html" %}
```markup
<nav>
  <ul>
    <li><a>About</a></li>
    <li><a>Skills</a></li>
    <li><a>Contact</a></li>
  </ul>
</nav>
```
{% endcode-tabs-item %}
{% endcode-tabs %}

En el archivo **app.component.ts** existe una línea donde encuentras el '**selector**' y ese es el que se debe añadir en el **app.component.html**

Copia el selector y añádelo como etiqueta en la vista del componente App.

![A&#xF1;adiendo el menu en el App ](../.gitbook/assets/ezgif.com-gif-maker-13.gif)

Ahora debemos unir cada uno de los links a los respectivos componentes.

## Paso 5: Uniendo los componentes a sus links 🕹️

Vamos a crear un modulo para controlar todas nuestras rutas.

En la carpeta **app**, vamos a dar clic derecho y en la opción Angular Generator, seleccionaremos Module

![Modulo Routing](../.gitbook/assets/ezgif.com-gif-maker-14.gif)

En nuestro nuevo archivo vamos a incluir las rutas y para ello debemos importar el RouterModule  e incluir en los import la colección de nuestras rutas.

* Incluimos el import

```typescript
import { RouterModule } from '@angular/router';
```

* en los import colocaremos la colección usando el forRoot.

```typescript
RouterModule.forRoot([
      { path: 'about', component: AboutComponent },
      { path: 'contact', component: ContactComponent },
      { path: 'home', component: HomeComponent },
      { path: 'skills', component: SkillsComponent },
      { path: '**', redirectTo: 'home' }
    ])
```

* Debemos también importar los componentes que estamos mencionando en la colección de rutas, para que no salga error en nuestra aplicación.

```typescript
import { AboutComponent } from '../about/about.component';
import { ContactComponent } from '../contact/contact.component';
import { HomeComponent } from '../home/home.component';
import { SkillsComponent } from '../skills/skills.component';
```

* Debemos incluir también nuestros componentes en los declarations.

```typescript
declarations: [ AboutComponent, ContactComponent, HomeComponent, SkillsComponent]
```

![Routing Module](../.gitbook/assets/screen-shot-2019-11-03-at-9.14.00-pm.png)

También podemos crear una variable donde almacenemos la colección de nuestras rutas y la pondremos en nuestro forRoot, pero esta es solo otra alternativa.

{% code-tabs %}
{% code-tabs-item title="routing.module.ts" %}
```typescript
import { NgModule } from '@angular/core';
import { CommonModule } from '@angular/common';
import { RouterModule } from '@angular/router';
import { AboutComponent } from '../about/about.component';
import { ContactComponent } from '../contact/contact.component';
import { HomeComponent } from '../home/home.component';
import { SkillsComponent } from '../skills/skills.component';

@NgModule({
  imports: [
    CommonModule,
    RouterModule.forRoot([
      { path: 'about', component: AboutComponent },
      { path: 'contact', component: ContactComponent },
      { path: 'home', component: HomeComponent },
      { path: 'skills', component: SkillsComponent },
      { path: '**', redirectTo: 'home' }
    ])
  ],
  declarations: [ AboutComponent, ContactComponent, HomeComponent, SkillsComponent]
}) 
export class RoutingModule { }
```
{% endcode-tabs-item %}
{% endcode-tabs %}

* Aún no hemos incluido el archivo routing.module en nuestro app, para esto en el archivo **app.module.ts**, importamos nuestro archivo **routing.module.ts**

{% code-tabs %}
{% code-tabs-item title="app.module.ts" %}
```typescript
import { RoutingModule } from './routing/routing.module';
```
{% endcode-tabs-item %}
{% endcode-tabs %}

Incluimos en la colección de imports nuestro '**RoutingModule**'

```typescript
imports:      [ BrowserModule, FormsModule, RoutingModule ],
```

En nuestro **app.module.ts** aparecen importados los componentes que ya incluimos en el **routing.module.ts**, entonces lo que haremos es borrar los que ya están en el routing. Nuestro **app.module.ts** quedará así:

{% code-tabs %}
{% code-tabs-item title="app.module.ts" %}
```typescript
import { NgModule } from '@angular/core';
import { BrowserModule } from '@angular/platform-browser';
import { FormsModule } from '@angular/forms';

import { AppComponent } from './app.component';
import { MenuComponent } from './menu/menu.component';

import { RoutingModule } from './routing/routing.module';

@NgModule({
  imports:      [ BrowserModule, FormsModule, RoutingModule ],
  declarations: [ AppComponent, MenuComponent ],
  bootstrap:    [ AppComponent ]
})
export class AppModule { }

```
{% endcode-tabs-item %}
{% endcode-tabs %}

* Nos falta incluir estas rutas que creamos de nuestros componentes en el menu que incluimos y usar la etiqueta &lt;router-outlet&gt; que nos ayudará a mostrar el contenido de nuestros componentes

En nuestro **app.component.html** vamos a incluir nuestra etiqueta &lt;router-outlet&gt; &lt;/router-outlet&gt;, dentro de estas etiquetas se va a mostrar todo el contenido de nuestros componentes.

{% code-tabs %}
{% code-tabs-item title="app.component.html" %}
```markup
<header class="header">
  <h1>My App 😉</h1>
</header>
<app-menu></app-menu>
<router-outlet></router-outlet>
```
{% endcode-tabs-item %}
{% endcode-tabs %}

Al incluir nuestra etiqueta saldrá un error parecido al siguiente y es porque nos falta exportar nuestro Modulo de Routing, y para esto es solo que incluyamos el export, en nuestro NgModule, en el **routing.module.ts** así:

{% code-tabs %}
{% code-tabs-item title="routing.module.ts" %}
```typescript

@NgModule({
  imports: [
    CommonModule,
    RouterModule.forRoot([
      { path: 'about', component: AboutComponent },
      { path: 'contact', component: ContactComponent },
      { path: 'home', component: HomeComponent },
      { path: 'skills', component: SkillsComponent },
      { path: '**', redirectTo: 'home' }
    ])
  ],
  declarations: [ AboutComponent, ContactComponent, HomeComponent, SkillsComponent],
  exports: [
    RouterModule,
  ]
}) 

```
{% endcode-tabs-item %}
{% endcode-tabs %}

* Solo falta incluir en nuestros links la ruta de nuestros componentes y para ello vamos a hacer uso de unos atributos que tiene el enrutamiento o Routing, llamados **routerLinkActive** y **routerLink**. En cada uno de nuestros links incluiremos que nuestro link esta activo y le pondremos en el routerLink el path que asignamos en el RouterModule. En el archivo **menu.component.html** añadiremos lo mencionado.

{% code-tabs %}
{% code-tabs-item title="menu.component.html" %}
```markup
<nav>
  <ul>
    <li><a routerLinkActive="active" 
      routerLink="/home">Home</a></li>
    <li><a routerLinkActive="active" 
      routerLink="/about">About</a></li>
    <li><a routerLinkActive="active" 
      routerLink="/skills">Skills</a></li>
    <li><a routerLinkActive="active" 
      routerLink="/contact">Contact</a></li>
  </ul>
</nav>
```
{% endcode-tabs-item %}
{% endcode-tabs %}

![Menu completado exitosamente](../.gitbook/assets/screen-shot-2019-11-03-at-9.59.31-pm.png)

Si damos clic en cada uno de los links podremos ver el contenido de cada componente.

![Probando los links](../.gitbook/assets/ezgif.com-gif-maker-15.gif)

Como puedes notar no hay mucho contenido en nuestros componentes, entonces podemos incluir alguno de contenido en ellos. 

## Paso 6: Añadamos algo de contenido 🤡

En nuestro componente home, podemos incluir algo de texto introductorio a nuestra aplicación, esta aplicación es como tu portafolio. Entonces incluye un texto para darle la bienvenida a tu visitante y algo de contexto de la página. En nuestro **home.component.html** colocaremos las etiquetas y el texto.

{% code-tabs %}
{% code-tabs-item title="home.component.html" %}
```markup
<section>
  <p>Bienvenidos!!</p>
  <p>
  Esta es mi página y en ella incluire mi portafolio, el cual estan todos invitados a conocer.
  </p>
</section>
```
{% endcode-tabs-item %}
{% endcode-tabs %}

En el component about, **about.component.html**,  podemos colocar un título.

{% code-tabs %}
{% code-tabs-item title="about.component.html" %}
```markup
<section>
  <header>
    <h1>Sobre Mí</h1>
  </header>
</section>
```
{% endcode-tabs-item %}
{% endcode-tabs %}

Nuestro portafolio se verá así:

![portafolio en proceso](../.gitbook/assets/ezgif.com-gif-maker-15%20%281%29.gif)



¡Sí has llegado hasta aquí, Felicitaciones!!! 

Estas a un paso de completar este desafío, solo te falta realizar la misión especial 👍

😉

{% hint style="info" %}
\*\*\*\*[**Aquí**](https://stackblitz.com/edit/routing-challenge1) puedes encontrar el ejercicio resuelto.
{% endhint %}

## 😎 Tu Misión Especial 😎

Parece que nuestra aplicación está casi lista 😀. 

👍 Para completarla debes  añadir contenido en los componentes restantes, recuerda que estas construyendo tu portafolio, entonces añade información sobre ti en cada componente y si necesitas ayuda con los estilos o añadiendo el contenido nos puedes pedir ayuda 👍

Si completas tu portafolio y me muestras este desafío completado, te daré un pequeño detalle 😁

{% hint style="success" %}
Has completado el **desafío \#2 de nivel básico**, ahora vamos al **desafío Intermedio \#2 👇**
{% endhint %}

{% hint style="info" %}
**Nota:**

Si necesitas mentoría con este ejercicio puedes contactar a:

Vanessa M. Aristizabal  
Twitter: @vanessamarely  
Correo: vanessamarely@gmail.com
{% endhint %}

