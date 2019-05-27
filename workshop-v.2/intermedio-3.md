# Intermedio 3: Forms and Services

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

## 😎 Tu Misión 😎

Parece que nuestra aplicación está lista excepto por un pequeño detalle 😵. Debería de poder eliminar un elemento de la lista cuando este terminada

⭐️ Utiliza lo que ya conoces como: **data** [**binding**](https://alligator.io/angular/data-binding-angular/)**,**  llamado de funciones y evento clic en botones para lograr este objetivo.

**💪💪**¡¡Felicitaciones!! ¡Llegaste muy lejos! **💪💪**

## 🎉 ¡**LO LOGRASTE!** 🎉

{% hint style="info" %}
**Nota:**

Si necesitas en casa y necesitas ayuda con este ejercicio puedes contactar a:

Alejandra Giraldo  
Twitter: @maleja111  
Correo: magiraldodevelop@gmail.com
{% endhint %}

