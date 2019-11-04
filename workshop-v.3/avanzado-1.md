---
description: "En Angular existen dos formas de crear formularios una llamada Template Driven y otra llamada Reactive Forms, en este desafío te enseñaremos como crear un formulario Reactivo o Reactive Form \U0001F609"
---

# ✨Avanzado \#1 - Formularios Reactivos✨

## 💡 Introducción 💡

En este desafío crearemos un formulario de contacto aplicando algunos conceptos básicos de Angular, los cuales hemos aprendido en los desafíos anteriores y aprenderemos algunos nuevos a través de este desafío 🤙

**¡**[**Aquí puedes encontrar el demo**](https://contact-form1.stackblitz.io)**!**

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
<h1>📝 Formulario de Contacto 📝</h1>
```
{% endcode-tabs-item %}
{% endcode-tabs %}

Deberías ver algo así: 👇

![T&#xED;tulo del Formulario](../.gitbook/assets/screen-shot-2019-11-03-at-11.12.35-pm.png)

## Paso 3: Añadamos algunos campos de texto

Creemos un componente form y en el añadiremos algunos campos de texto para nuestro formulario.

En la carpeta app daremos clic derecho, seleccionamos la opción Angular Generator y seleccionamos component, le asignaremos el nombre form.

![Componente Form](../.gitbook/assets/screen-shot-2019-11-03-at-11.17.48-pm.png)

En nuestro nuevo componente vamos a crear un campo de texto para el nombre, teléfono, país de origen, fecha de nacimiento y correo.

Incluiremos este componente form en nuestro app component.

![A&#xF1;adimos los campos](../.gitbook/assets/screen-shot-2019-11-03-at-11.25.14-pm.png)

## Paso 4: Volvamos nuestro formulario reactivo

En el **app.module.ts** debemos incluir el modulo **ReactiveFormsModule.**

```typescript
import { ReactiveFormsModule } from '@angular/forms';
```

Lo incluimos en los imports del @NgModule.

```typescript
imports: [BrowserModule, ReactiveFormsModule]
```

