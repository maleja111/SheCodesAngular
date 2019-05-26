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

## Paso 3: Hora de poner el formulario **📋**

Vamos a utilizar un formulario con un campo de texto y 2 botones: un botón adicionará el contenido del campo de texto a la lista y el otro botón limpiara la lista para que no contenga nada.

Adiciona este código en la linea 8 de tu archivo **app.component.html**

{% code-tabs %}
{% code-tabs-item title="app.component.html" %}
```markup
<div>
  <form (ngSubmit)="save()">
    <div class="form-group">
      <input class="form-group"
        id="textId"
        type="text"
        placeholder="Adiciona a la lista..."
        required
        minlength="3"
        [(ngModel)]="model.text"
        name="text" />
    </div>
    <button type='submit'>Adiciona a la lista</button>
    <button (click)='clearComplete()' type='button'>Elimina toda la lista</button>
  </form>
  <label class="label">Form Model: {{this.model | json}}</label><br />
  <label class="label">List: {{this.items | json}}</label><br />
</div>
```
{% endcode-tabs-item %}
{% endcode-tabs %}

Deberías hacer algo así, y tu resultado se deberá ver así:👇

![](../.gitbook/assets/2.gif)

{% hint style="info" %}
**Por si tienes alguna duda. Aquí te explicamos cómo funciona: 👷‍♀️**

**1.** La etiqueta **form** es una etiqueta de HTML que representa un formulario. En este formulario contiene los diferentes campos y botones que lleguemos a necesitar.  
  
**2.** La etiqueta **\(ngSubmit\)="save\(\)"**: **ngSubmit** es usada para manejar el envío de la información del formulario. **save\(\):** es usado para indicar al archivo **app.component.ts** cual es la función a la que se va a hacer referencia cuando se envíe información del formulario.

**3.** La etiqueta **input**:   
**class:** Es usada para manejar estilos.   
**id:** Referencia al elemento.   
**type:** El tipo de dato, en este caso texto.   
**placeholder:** Muestra en el campo de texto un mensaje, antes de que el usuario ingrese un valor.   
**required y minlength:** Se utiliza para realizar validaciones.  
**ngModel:** Creas una instancia a [`FormControl`](https://angular.io/api/forms/FormControl) donde se domina el modelo y binds hacia el elemento.  
**name:** Nombre del input.

{% code-tabs %}
{% code-tabs-item title="app.component.html" %}
```markup
<input class="form-group"
        id="textId"
        type="text"
        placeholder="Adiciona a la lista..."
        required
        minlength="3"
        [(ngModel)]="model.text"
        name="text" />
```
{% endcode-tabs-item %}
{% endcode-tabs %}

  
**4.** El elemento **button** es un botón, el primero envía información del formulario.  
Segundo, elimina la lista.  
El primer label nos va a permitir ver el modelo de nuestra aplicación.  
El segundo label nos va a permitir ver como la lista se elimina.

{% code-tabs %}
{% code-tabs-item title="app.component.html" %}
```markup
<button type='submit'>Adiciona a la lista</button>
<button (click)='clearComplete()' type='button'>Elimina toda la lista</button>
//////
<label class="label">Form Model: {{this.model | json}}</label><br />
<label class="label">List: {{this.items | json}}</label><br />
```
{% endcode-tabs-item %}
{% endcode-tabs %}
{% endhint %}



\*\*\*\*

