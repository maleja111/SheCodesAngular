---
description: >-
  En este reto aprendamos sobre directivas. Una directiva se representa como un
  atributo en una etiqueta HTML; *ngIf, *ngFor, *ngSwitch son algunas y le
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

## 

