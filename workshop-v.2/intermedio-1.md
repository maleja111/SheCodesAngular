---
description: >-
  Además de utilizar conocimiento de ejercicios pasados ¡Vamos a usar
  formularios!
---

# Intermedio \#1: Lista de Tareas 📝

## 💡 Introducción 💡

Ya hemos utilizado funciones muy divertidas de Angular, ahora vamos a utilizar un formulario para crear una pequeña lista de notas [**¡Aquí puedes encontrar el demo!**](https://stackblitz.com/edit/angular-toma-lista)\*\*\*\*

## Paso 1: **Creemos nuestra App de Angular** ⭐️

Entra a **www.stackblitz.com**, y verás algo como esto:

![](../.gitbook/assets/1.png)

![](../.gitbook/assets/screen-shot-2019-05-25-at-1.56.29-pm.png)

## Paso 2: **Añadamos un título ✍️**

Vamos a crear el entorno de nuestra aplicación. Para ello iremos al archivo **app.component.html** y borramos todo el contenido para adicionar lo siguiente:

{% code title="app.component.html" %}
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
{% endcode %}

Deberías ver algo así: 👇

![](../.gitbook/assets/ejer1.gif)

## Paso 3: Hora de poner el formulario **📋**

Vamos a utilizar un formulario con un campo de texto y 2 botones: un botón adicionará el contenido del campo de texto a la lista y el otro botón limpiará la lista para que no contenga nada.

Adiciona este código en la línea 8 de tu archivo **app.component.html**

{% code title="app.component.html" %}
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
{% endcode %}

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

{% code title="app.component.html" %}
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
{% endcode %}

  
**4.** El elemento **button** es un botón, el primero envía información del formulario.  
Segundo, elimina la lista.  
El primer label nos va a permitir ver el modelo de nuestra aplicación.  
El segundo label nos va a permitir ver como la lista se elimina.

{% code title="app.component.html" %}
```markup
<button type='submit'>Adiciona a la lista</button>
<button (click)='clearComplete()' type='button'>Elimina toda la lista</button>
//////
<label class="label">Form Model: {{this.model | json}}</label><br />
<label class="label">List: {{this.items | json}}</label><br />
```
{% endcode %}
{% endhint %}

## Paso 4: Adicionemos lógica para el formulario 🧪 **📋**

Ahora vamos a modificar el archivo **app.component.ts**, ****en ****este vamos a adicionar la declaración de variables que vimos en el archivo **app.component.html** y además vamos a agregar unas funciones.  
En este archivo vamos a reemplazar su contenido, por el siguiente código:

{% code title="app.component.ts" %}
```typescript
import { Component } from '@angular/core';


@Component({
  selector: 'my-app',
  templateUrl: './app.component.html',
  styleUrls: ['./app.component.css']
})
export class AppComponent {
  model = {};
  items = [];


  ngOnInit() {
  }

  save() {
    if (this.model.text !== '') {
      this.items.unshift({ 'text': this.model['text'], 'complete': false });
      this.model['text'] = '';
    }
  }

  clearComplete() {
    this.items = [];
  }
}
```
{% endcode %}

Deberías hacer algo así, y tu resultado se deberá ver así:👇

![](../.gitbook/assets/3.gif)

{% hint style="info" %}
**Por si tienes alguna duda. Aquí te explicamos cómo funciona: 👷‍♀️**

**1.** En la línea 10 y 11, se declaran las variables: **model** y **items**.  
  
**2.** La función **save\(\)**, línea 17, es la encargada de enviar los datos del formulario a lista.  
  
**3. Dentro de la función save\(\):** Línea 18 valida que el input tenga texto.  
La línea 19 me adiciona un elemento a una lista.  
La línea 20 me limpia el input.  
  
**4.** La función **clearComplete\(\)**, línea 24, es la encargada de eliminar los datos de la lista, es por eso que se limpia la variable.
{% endhint %}

## Paso 5: Creemos un espacio para ver las listas **📝👀**

Ahora vamos a modificar el archivo **app.component.html**, ****en ****este vamos a adicionar el código para ver nuestra lista.  
Adiciona este código en la línea 26 de tu archivo **app.component.html**

{% code title="app.component.html" %}
```markup
<div *ngIf="items.length > 0" class="mt-20">
  <div *ngFor="let item of items" class="individual">
    <div class="list-items">
      <div class="items">
        <input type="checkbox" id="check1"/>
        <label for="check1">
        <div><i class="fa fa-check"></i></div> {{item.text || 'Add some thing'}}
        </label>
      </div>
    </div>
  </div>
</div>
```
{% endcode %}

Deberías hacer algo así, y tu resultado se deberá ver así:👇

![](../.gitbook/assets/4.gif)

{% hint style="info" %}
**Por si tienes alguna duda. Aquí te explicamos cómo funciona: 👷‍♀️  
  
1**. El elemento _**\***_**ngIf=** __nos va a ayudar a ocultar o mostrar elementos, depende de la variable que tengamos asignada dentro del **ngIf=**, en este caso tenemos la siguiente lógica, si la variable **items.length** \(el número de elementos de la lista\) es mayor a 0 entonces muestre la lista.  
  
**2.** **\*ngFor** es una directiva en Angular, nos permite presentar una lista de elementos en pantalla de una forma sencilla. Su sintaxis consiste en inicializar una variable que la podemos llamar **item**, que será el elemento que nos irá mostrando de la lista  items.  
  
3.**{{item.text \|\| 'Add some thing'}}** Aquí indico si deseo que muestre el mensaje o un mensaje por defecto, si text no llega a tener texto.
{% endhint %}

## Paso Final: Personaliza tu aplicación 👩🏻‍🎨

¡Vamos a hacer que nuestra lista tenga color agregando CSS!   
¿Recuerdas las clases que usamos en nuestro **app.component.html**? ¡Llegó el tiempo de usarlas!   
Reemplaza el contenido de **app.component.css** con éste:

{% code title="app.component.css" %}
```css
* {
  font-family: 'Gloria Hallelujah', cursive;
}
/* Title */
h1 {
  color: #a4499a;
  font-size: 26px;
  font-weight: bold;
  margin-bottom: 10px;
}
/* Title Number */
h1 span.highlight {
  color: #4220da;
}
form {
  width: 300px;
  white-space: nowrap;
  display: grid;
}
#textId {
  width: 98%;
}
.label {
  color: #7f6859;
  font-weight: bold;
  background-color: #e8e8e8;
  width: 300px;
  font-size: 15px;
  font-family: Arial,Helvetica,sans-serif;
}
input {
  border-radius: 15px;
}
button{
  padding: 2px 0px;
  background: #d075c1;
  border-radius: 15px;
  border: 0;
  color: #fff;
  font-size: 12px;
  font-weight: bold;
  cursor: pointer;
  margin: 3px 0px;
}
.list-items {
  background-color: #789872;
  border-bottom: 3px solid #88b1a77a;
}
.items {
  color: #fff;
  font-size: 18px;
  display: inline-flex;
}

.mt-20 {
  margin-top: 20px;
}
```
{% endcode %}

Deberías hacer algo así, y tu resultado se deberá ver así:👇

![](../.gitbook/assets/5.gif)

## 😎 Tu Misión 😎

Parece que nuestra aplicación está lista excepto por un pequeño detalle 😵. Debería de poder eliminar un elemento de la lista cuando esta esté terminada.

⭐️ Utiliza lo que ya conoces como: **data** [**binding**](https://alligator.io/angular/data-binding-angular/)**,**  llamado de funciones y evento clic en botones para lograr este objetivo.

**💪💪**¡¡Felicitaciones!! ¡Llegaste muy lejos! **💪💪**

{% hint style="info" %}
**Nota:**

Si necesitas ayuda con este ejercicio puedes contactar a:

Alejandra Giraldo  
Twitter: @maleja111  
Correo: magiraldodevelop@gmail.com
{% endhint %}

