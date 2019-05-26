---
description: >-
  En este reto aprendamos sobre directivas. Una directiva se representa como un
  atributo en una etiqueta HTML; *ngIf, *ngFor, *ngSwitch son algunas y le
  adiciona un comportamiento definido.
---

# Básico 2: Directives \|\| pipes

## 💡 Introducción 💡

¡Que divertido fue aprender a usar imagenes de gatos!  
ahora vayamos por... [**¡Aquí puedes encontrar el demo!**](https://stackblitz.com/edit/angular-toma-lista)\*\*\*\*

## Paso 1: **Creemos nuestra App de Angular** ⭐️

Entra a **www.stackblitz.com**, y verás algo como esto:

![](../.gitbook/assets/1.png)

![](../.gitbook/assets/screen-shot-2019-05-25-at-1.56.29-pm.png)

## Paso 2: **Añadamos un título ✍️**

Vamos a crear el entorno de nuestra aplicación. Para ello iremos al archivo **app.component.html** y borramos todo el contenido para adicionar lo siguiente:

{% code-tabs %}
{% code-tabs-item title="app.component.html" %}
```markup
<div>
	<div>
		<div>
          <h1>Tienes #<span class='highlight'>{{items.length}}</span>
            elementos en la lista.
          </h1>
      </div>
    </div>
</div>
```
{% endcode-tabs-item %}
{% endcode-tabs %}

Deberías ver algo así: 👇

![](../.gitbook/assets/ejer1.gif)

## 

