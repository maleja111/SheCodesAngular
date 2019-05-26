---
description: >-
  Además de utilizar conocimiento de ejercicios pasados ¡vamos a usar
  formularios!
---

# Intermedio 1: Toma nota 📝

## 💡 Introducción 💡

Ya hemos utilizado funciones muy divertidas de Angular, ahora vamos a utilizar un formulario para crear una pequeña lista de notas [**¡Aquí puedes encontrar el demo!**](https://stackblitz.com/edit/angular-toma-lista)\*\*\*\*

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

{% hint style="info" %}
\*\*\*\*
{% endhint %}

