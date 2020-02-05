---
description: "En este ejercicio nos vamos a divertir aprendiendo sobre Formularios de tipo Template-driven en Angular.io \U0001F4DD"
---

# Intermedio \#2: Crea un formulario de contacto ✉️

## 💡 Introducción 💡

En este desafío vamos a mostrar de forma muy creativa datos que tú mismo vas a ingresar en un formulario de contacto, la cual es una funcionalidad básica de las páginas web. 📬

\*\*\*\*[**¡Aquí puedes encontrar el demo!**](https://angular-contacto-template-driven-form.stackblitz.io)\*\*\*\*

## Paso 1: **Creemos nuestra App de Angular** 🅰️

Entra a [**www.stackblitz.com**](https://stackblitz.com), y verás algo como esto:

![](../.gitbook/assets/1.png)

![](../.gitbook/assets/screen-shot-2019-05-25-at-1.56.29-pm.png)

## Paso 2: **Vamos a la estructura** básica **HTML 💀**

Vamos a adicionar la estructura básica que va a tener nuestro formulario para que tengamos mucho mas claro como vamos a visualizar nuestros datos.  
Reemplazaremos el contenido del archivo **app.component.html** y adicionaremos lo siguiente:

{% code title="app.component.html" %}
```markup
<div class="center">

	<div class="card">
		<div class="additional">
			<div class="user-card">
				<div class="level center">
					She Codes Angular
				</div>
        <div class="logo-container">
          <div class="logo">
              <img src="https://pbs.twimg.com/profile_images/1106680001368346625/uKM4e-br_400x400.png">
          </div>
        </div>
				<div class="points center">
					@SheCodesAngular
				</div>
				
			</div>
			<div class="more-info">
      <!-- TODO: Aquí adicionaremos nuestro formulario -->
			</div>
		</div>
		<div class="general more-info">
    <!-- TODO: Aquí adicionaremos el resultado de los datos que ingresemos al formulario -->
		</div>
	</div>
</div>
```
{% endcode %}

Deberías hacer algo así, y tu resultado se deberá ver así:👇

![](../.gitbook/assets/screen-shot-2019-11-04-at-5.31.48-pm.png)

## Paso 3: **Dale personalidad y color a nuestra aplicación 🎨**

Vamos a hacer algo diferente esta vez, siempre dejamos la estructura CSS para el final, pero en esta ocasión vamos a dejarla lista y nos enfocaremos en la lógica de nuestro formulario de contacto.  
Reemplazaremos el contenido del archivo **styles.css** y adicionaremos lo siguiente:

{% code title="styles.css" %}
```css
/* Add application styles & imports to this file! */
@import url('https://fonts.googleapis.com/css?family=Abel');

html, body {
  background: #FCEEB5;
  font-family: Abel, Arial, Verdana, sans-serif;
}

.center {
  position: absolute;
  top: 50%;
  left: 50%;
  -webkit-transform: translate(-50%, -50%);
}

.logo-container {
    left: 29px;
    position: absolute;
    top: 75px;
}

.logo-container img {
    width: 85%;
    height: auto;
    border-radius: 50%;
}

.card {
  width: 450px;
  height: 250px;
  background-color: #fff;
  background: linear-gradient(#f8f8f8, #fff);
  box-shadow: 0 8px 16px -8px rgba(0,0,0,0.4);
  border-radius: 6px;
  overflow: hidden;
  position: relative;
  margin: 1.5rem;
}

.card h1 {
  text-align: center;
}

.card .additional {
  position: absolute;
  width: 150px;
  height: 100%;
  background: linear-gradient(#dE685E, #EE786E);
  transition: width 0.4s;
  overflow: hidden;
  z-index: 2;
}

.card:hover .additional {
  width: 100%;
  border-radius: 0 5px 5px 0;
}

.card .additional .user-card {
  width: 150px;
  height: 100%;
  position: relative;
  float: left;
}

.card .additional .user-card::after {
  content: "";
  display: block;
  position: absolute;
  top: 10%;
  right: -2px;
  height: 80%;
  border-left: 2px solid rgba(0,0,0,0.025);
}

.card .additional .user-card .level,
.card .additional .user-card .points {
  top: 15%;
  color: #fff;
  font-size: 0.75em;
  font-weight: bold;
  background: rgba(0,0,0,0.15);
  padding: 0.125rem 0.75rem;
  border-radius: 100px;
  white-space: nowrap;
}

.card .additional .user-card .points {
  top: 85%;
}

.card .additional .more-info {
  width: 300px;
  float: left;
  position: absolute;
  left: 150px;
  height: 100%;
}

.card .additional .more-info h1 {
  color: #fff;
  margin-bottom: 0;
}

.card .additional .coords {
  margin: 0 1rem;
  color: #fff;
  font-size: 1rem;
}

.card .additional .coords .strong {
  font-weight:bold;
}

.card .general {
  width: 300px;
  height: 100%;
  position: absolute;
  top: 0;
  right: 0;
  z-index: 1;
  box-sizing: border-box;
  padding: 1rem;
  padding-top: 0;
}

.card .general .more {
  position: absolute;
  bottom: 1rem;
  right: 1rem;
  font-size: 0.9em;
}

.margin-left {
  margin-left: 40px;
}
```
{% endcode %}

Deberías hacer algo así, y tu resultado se deberá ver así:👇

![](../.gitbook/assets/screen-shot-2019-11-04-at-5.40.49-pm.png)

## Paso 3: **Aprendamos a hacer un formulario en Angular.io 📝🅰️**

Ya tienes la estructura básica, hora nos concentraremos en la creación de un formulario, este formulario tendrá 3 campos, un campo para ingresar tu nombre, otro para ingresar tu correo electrónico y un campo para ingresar un mensaje.  
  
Adicionaremos el siguiente contenido reemplazando la línea de comentario `<!-- TODO: Aquí adicionaremos nuestro formulario -->`  en el archivo **app.component.html.**

{% code title="app.component.html" %}
```markup
<form #contactForm="ngForm" (ngSubmit)="onSubmit(contactForm.value)">
  <div class="form-group">
    <input type="text" placeholder="What is your name?"  clas="form-control" name="name" [(ngModel)]="name" required/>
  </div>
  <div class="form-group">
    <input name="emailaddress" placeholder="What is your email?*" class="form-control" type="email" name="email" [(ngModel)]="email" required/>
  </div>
  <div class="form-group">
    <textarea rows="4" cols="40" placeholder="Please enter your message*" class="form-control" name="message" [(ngModel)]="message" required></textarea>
  </div>
  <button type="submit" class="btn btn-primary" [disabled]="!contactForm.valid">Submit</button>
</form>
```
{% endcode %}

Deberías hacer algo así, y tu resultado se deberá ver así **cuando pases el mouse sobre la aplicación**:👇

![](../.gitbook/assets/screen-shot-2019-11-04-at-5.59.03-pm.png)

{% hint style="info" %}
**Por si tienes alguna duda. Aquí te explicamos cómo funciona: 👷‍♀️  
  
1.** En Angular.io existen 2 tipos de Formularios [Template-driven](https://angular.io/guide/forms#template-driven-forms) y [Reactive Forms](https://angular.io/guide/reactive-forms#reactive-forms), en esta oportunidad trabajaremos con los formularios tipo [Template-driven](https://angular.io/guide/forms#template-driven-forms). su diferencia radica en el tipo de aplicaciones que necesites crear, para formularios simples y sin lógica personalizadas, esta es tu mejor opción, cuando necesitas validaciones personalizadas o creación de campos que aparezcan dinámicamente [Reactive Forms](https://angular.io/guide/reactive-forms#reactive-forms) es tu mejor opción.  
**2.** En nuestro código HTML tenemos una nueva etiqueta`form`que contendrá nuestro [formulario](https://www.w3schools.com/html/html_forms.asp).  
**3.** En nuestro código HTML tenemos`contactForm="ngForm"`, que es la referencia a nuestro formulario, en Angular se llama Template reference, y básicamente nos ayuda a potenciar una simple etiqueta HTML `form` con todo el poder que tienen Angular para ofrecernos. el `NgForm` le da propiedades como validación o  poner el campo como requerido y muchísimas más funcionalidades con lógica sin necesidad de tanto código.  
**4.** En nuestro código HTML tenemos `(ngSubmit)="onSubmit(contactForm.value):`Con él`(ngSubmit)` estamos usando un evento para hacer acceder a nuestra función `onSubmit()` que va a contener la información de los valores `contactForm.value` que son nuestros datos del formulario en el momento que le demos click a el botón de guardar los datos del formulario. \(aun que no los estemos guardando en ninguna base de datos realmente\)  
**5.** En nuestro código HTML tenemos una nueva etiqueta `input` esta etiqueta nos ayudara a ingresar información a nuestro formulario, en nuestro caso, los campos name y email tienen la etiqueta [input](https://www.w3schools.com/tags/tag_input.asp) que nos permitirá tener control sobre la información ingresada.  
**6.** En nuestro código HTML tenemos una nueva etiqueta `textarea` esta etiqueta nos ayuda ingresando información a nuestro formulario que podría ser de más de una línea, se usa generalmente para párrafos. Nosotros lo usamos para el campo message [textarea](https://www.w3schools.com/tags/tag_textarea.asp).  
**7.** En nuestro código HTML tenemos una nueva etiqueta `required` esta etiqueta es lógica de los formularios de Angular.io tipo **template-driven**, al incluir esta etiqueta le estamos diciendo a angular que ese campo es un campo requerido y que lo necesitamos lleno para el correcto envío de información cuando presionemos el botón guardar.  
**8.** En nuestro código HTML tenemos una nueva etiqueta `placeholder`  será la encargada de poner un texto dentro del campo \(input, o textarea\) cuando este vacío, se usa para especificar una pista breve que describe el valor que esperamos que ingrese el usuario.  
**9.** En nuestro código HTML tenemos una nueva etiqueta `button` que define un botón en el que se puede hacer clic.
{% endhint %}

{% hint style="warning" %}
**En el paso 4 explicaremos:**

{% code title="app.component.html" %}
```markup
[disabled]
[(ngModel)]
```
{% endcode %}
{% endhint %}

## Paso 4: Vamos a visualizar los datos **👀**

Ya aprendiste a hacer un formulario 🎉, ahora vamos a comprender cómo ver esa información.  
  
Adicionaremos el siguiente contenido reemplazando la línea de comentario `<!-- TODO: Aquí adicionaremos el resultado de los datos que ingresemos al formulario -->`  en el archivo **app.component.html.**

{% code title="app.component.html" %}
```markup
<h1>Result Contact us</h1>
<div class="coords">
 <span class="strong">Name: </span>
 <span>{{contactForm.value.name}}</span>
</div>
<div class="coords">
 <span class="strong">Email: </span>
 <span>{{contactForm.value.email}}</span>
</div>
<div class="coords">
 <span class="strong">Message: </span>
 <span>{{contactForm.value.message}}</span>
</div>
<span class="more">Mouse over the card for more info</span>
```
{% endcode %}

![](../.gitbook/assets/screen-shot-2019-11-04-at-7.53.20-pm.png)

{% hint style="info" %}
**Por si tienes alguna duda. Aquí te explicamos cómo funciona: 👷‍♀️  
  
1.** Recuerdas que en el paso anterior teníamos en nuestro HTML:

{% code title="app.component.html" %}
```markup
#contactForm="ngForm"
```
{% endcode %}

Bueno, `contactForm` es nuestra referencia a nuestro formulario, entonces gracias a que es un Angular template-driven form, podemos usar la referencia al contenido de sus campos sin adicionar variables o código adicional en nuestro archivo .ts, directamente desde nuestro HTML podemos acceder a ella.  
**2.** Por lo explicado en el paso anterior, podemos hacer un binding \(una visualización de variable\) usando nuestros conocidos {{}} y nuestro `contactForm` de referencia, haciendo muy fácil mostrar el nombre, que ingresamos de la siguiente manera:

{% code title="app.component.html" %}
```markup
{{contactForm.value.name}}
```
{% endcode %}

Lo mismo lo hacemos con los demás campos:

{% code title="app.component.html" %}
```markup
{{contactForm.value.email}}
{{contactForm.value.message}}
```
{% endcode %}

**3.** Recuerdas la etiqueta `[(ngModel)]="name"` en nuestro código HTML, esto, combinado con los puntos 1 y 2, hacen la magia del binding \(una visualización de variable\), cuando usamos **\[\(ngModel\)\]** es dos vías de binding, en inglés, two-way data binding para asignar el nombre, incluso podemos crear una variable con el mismo nombre "name" y asignarle un valor por defecto para cuando cargue nuestro formulario.  
**4.** Recuerdas la etiqueta \[disabled\] del punto:

{% code title="app.component.html" %}
```markup
[disabled]="!contactForm.valid"
```
{% endcode %}

**contactForm.valid**: Es el uso de la referencia del template-driven form para acceder a las propiedades, lo que declaramos como nuestro contactForm puede acceder a la propiedad que le dice si es valid. Lo que lo hace valido o invalido es que cuando adicionamos la etiqueta **required** en el paso 3, le estamos diciendo a nuestro formulario que hasta que ese campo no este lleno, el formulario no sera válido, por lo tanto, debe tener el contenido de los 3 campos de nuestro formulario.   
**\[disabled\]**: Le estamos indicando que cuando la condición interna no se cumpla, me des habilite el botón, vamos a inhabilitar el botón, mientras el formulario no sea valido.
{% endhint %}

## Paso 5: Vamos a "guardar" datos **💾**

Podemos ver todas las ventajas que tiene [Template-driven](https://angular.io/guide/forms#template-driven-forms) y vamos a ver las pocas lineas de código que vamos a necesitar para guardar nuestros datos.  
  
Copiaremos lo siguiente en el archivo **app.component.ts.**

{% code title="app.component.ts" %}
```typescript
onSubmit(value: any){  
    console.log('Save: ', value);
}
```
{% endcode %}

Deberías hacer algo así, y tu resultado se deberá ver así:👇

![](../.gitbook/assets/screen-shot-2019-11-04-at-11.17.48-pm.png)

{% hint style="info" %}
**Por si tienes alguna duda. Aquí te explicamos cómo funciona: 👷‍♀️  
  
1.** Recuerdas que en el paso 3 te contamos sobre el botón para guardar nuestro formulario, bueno, necesitamos crear una función que va a recibir toda la información que ingresemos en él. la llamamos `onSubmit` y adicionamos la función console.log para ver los datos que queremos "almacenar" en consola.
{% endhint %}

🎉 ¡**LO LOGRASTE!** 🎉

{% hint style="info" %}
\*\*\*\*[**Aquí**](https://stackblitz.com/edit/angular-contacto-template-driven-form) puedes encontrar el ejercicio resuelto.
{% endhint %}

## 😎 Tu Misión 😎

Con lo que aprendiste en el ejercicio de hoy, crea un nuevo botón que te permita llenar la información en el formulario con solo un clic, \(aquí un pastelito\),:

* Deberás tener 3 variables, una name, otra email y otra message.
* Deberás crear una función que responda al evento del botón llenando los valores de las variables.

  Esta adición es para retar tu curiosidad, podrías proponer la solución que tú quieras. 

{% hint style="success" %}
Has completado **Crea un formulario de contacto ✉️** ahora vamos para nuestro siguiente desafío **👇**
{% endhint %}

{% hint style="info" %}
**Nota:**

Si necesitas ayuda con este ejercicio puedes contactar a:

Alejandra Giraldo  
Twitter: @maleja111  
Correo: magiraldodevelop@gmail.com
{% endhint %}

