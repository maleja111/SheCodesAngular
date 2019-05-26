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

**1.** La etiqueta **form** \(linea 2\) es una etiqueta de HTML que representa un formulario. En este formulario contiene los diferentes campos y botones que lleguemos a necesitar.  
  
**2.** La etiqueta **\(ngSubmit\)="save\(\)"** : **ngSubmit** es usada para manejar el envío de la información del formulario. **save\(\):** es usado para indicar al archivo **app.component.ts** cual es la función a la que se va a hacer referencia cuando se envíe información del formulario.  
  
**3.** El elemento **{{}}**  es una forma de comunicar nuestro[componente](https://platzi.com/tutoriales/1153-angular/1619-que-son-los-componentes-en-angular/).   
De esta manera el **app.component.ts**, se comunica con **app.component.html,** y ****el **\|\|** dentro ****del ****elemento es una condición "o" que nos va a mostrar el número cero mientras no exista datos en las variables.  
  
**4.** El elemento [**class**](https://css-tricks.com/almanac/selectors/c/class/)**=""** nos va a ayudar a definir los estilos de nuestra aplicación \(no solo tiene esa utilidad, pero la usaremos para eso en el ejercicio de hoy\).  
  
 **5.** El elemento **\***[**ngIf**](https://angular.io/api/common/NgIf)**=** nos va a ayudar a ocultar o mostrar elementos, depende de la variable que tengamos asignada dentro del **\*ngIf=**, en este caso tenemos la variable **showBtnStart** donde la asignaremos en el **app.component.ts** más adelante. 
{% endhint %}

\*\*\*\*

