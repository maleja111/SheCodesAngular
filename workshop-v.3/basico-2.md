---
description: 'En este desafío vamos a aprender sobre: Interpolación y pipelines.'
---

# Básico \#2 - Trasformando data 🗳🗂

## 💡 Introducción 💡 <a id="paso-1-creemos-nuestra-app-de-angular"></a>

Hora de aplicar lo aprendido, vamos a jugar con HTML, Css y Angular 😎   
Realizaremos una aplicación que nos permita cambiar la manera en la que vemos la información en pantalla.

\*\*\*\*[**¡Aquí puedes encontrar el demo!**](https://angular-transformando-data.stackblitz.io)\*\*\*\*

## Paso 1: **Creemos nuestra App de Angular** 🅰️

Entra a [**www.stackblitz.com**](https://stackblitz.com), y verás algo como esto:

![](https://blobscdn.gitbook.com/v0/b/gitbook-28427.appspot.com/o/assets%2F-LW1Rd6Lo-WMisT20MSI%2F-LfkG9FnieTyrSrzuXpf%2F-LfkL1kfzmm5NbCpp7Bn%2F1.png?alt=media&token=c53de18e-d4ad-429e-a53d-90c4f288eb14)

![](https://blobscdn.gitbook.com/v0/b/gitbook-28427.appspot.com/o/assets%2F-LW1Rd6Lo-WMisT20MSI%2F-LfkG9FnieTyrSrzuXpf%2F-LfkL_8jRYal27_KSvzl%2FScreen%20Shot%202019-05-25%20at%201.56.29%20PM.png?alt=media&token=51d5597c-a0fb-4530-afbf-104ee3c4cc89)

## Paso 2: **Vamos a crear unas variables 🗳**

Ya dominas perfectamente el concepto de que es una variable 🤓vamos a crear las variables que van a contener la información que vamos a mostrar en nuestra aplicación.  
Copiaremos lo siguiente en el archivo **app.component.ts.**

{% code-tabs %}
{% code-tabs-item title="app.component.ts" %}
```typescript
flipCard = false;
today = new Date();
totalBill = 203094.12;
text = 'SHe CoDes AnGulAr';
```
{% endcode-tabs-item %}
{% endcode-tabs %}

Deberías hacer algo así, y tu resultado se deberá ver así:👇

![](../.gitbook/assets/transform-1.gif)

{% hint style="info" %}
**Por si tienes alguna duda. Aquí te explicamos cómo funciona: 👷‍♀️  
  
1.** Vamos a crear una variable llamada`flipCard`para manejar un efecto muy lindo que tendremos de voltear el rectángulo donde pondremos nuestros datos a mostrar, dónde le asignaremos un valor _booleano_ en **false**.  
**2.** Vamos a crear una variable llamada `today,` dónde le asignaremos el valor de una función propia de JavaScript que obtiene la fecha actual.  
**3.** En la variable `totalBill` vamos a almacenar un número con decimales.  
**4.** Y finalmente en la variable `text` vamos a almacenar una cadena de caracteres o también llamado dató string.
{% endhint %}

## Paso 3: **Vamos a construir el esqueleto de nuestra aplicación 💀**

En esta parte vamos a crear la estructura HTML que le dará vida y estructura a la forma en que presentaremos los datos en pantalla.  
En este archivo llamado  **app.component.html** vamos a reemplazar su contenido, por el siguiente código.

{% code-tabs %}
{% code-tabs-item title="app.component.html" %}
```markup
<div>
	<div class="centerTitle">
		<h1>Vamos a cambiar la forma en la que vemos nuestra información en pantalla</h1>
	</div>

	<div>
		<div class="cardContainer">
			<div class="card" [class.flipped]="flipCard" (click)="onClickCard()">
				<div class="front">
					<h3 class="cardTitle">
						¡¡¡ Dame Click !!!
						<!-- TODO: Aquí colocaremos datos sin modificar -->
            </h3>
				</div> <!-- close card front -->

				<div class="back">
					<div class="content">
						<h3 class="cardTitle">
							<!-- TODO: Aquí colocaremos los mismos datos modificados -->
              </h3>
					</div> <!-- close card back content -->
				</div> <!-- close card back -->

			</div> <!-- close card -->
		</div> <!-- close cardContainer -->
	</div>

</div>
```
{% endcode-tabs-item %}
{% endcode-tabs %}

Deberías hacer algo así, y tu resultado se deberá ver así:👇

![](../.gitbook/assets/transform-2.gif)

{% hint style="info" %}
**Por si tienes alguna duda. Aquí te explicamos cómo funciona: 👷‍♀️  
  
1.** En nuestro código HTML tenemos la etiqueta H1, que nos presenta el titulo de la aplicación.  
**2.** Tenemos un `<div>` que nos contiene una clase llamada **"cardContainer"**, aquí meteremos toda la información que queremos mostrar.  
**3.** Dentro de el `<div>` que contiene la clase llamada "**card"**, tenemos unas etiquetas que nunca habíamos visto.  
       **3.1** la primera es **\[class.flipped\]="flipCard"** \(será el responsable de darnos el efecto de girar una tarjeta\), vemos la variable `flipCard` que creamos anteriormente, que funciona así: cuando el valor es true en nuestra estructura HTML se adicionara la clase f**lipped**, solo y solo si, la variable es true, si su valor es false entonces no nos va a adicionar la clase **flipped** en nuestra estructura HTML.  
       **3.2** la segunda es \(click\)="onClickCard\(\)" aquí capturaremos el evento click donde nos mostrará u ocultará la información con la data transformada o sin transformar dependiendo del caso. \(en un siguiente paso veremos que contiene la función\).  
**4.** Ten presente los 2 comentarios que estás viendo que contienen   
**&lt;!-- TODO: Aquí .... --&gt;**  
 porque estas líneas nos servirán de referencia para poner código en un siguiente paso.
{% endhint %}

