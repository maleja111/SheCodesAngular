---
description: "Cuando creamos una aplicación una de las partes más importantes es la autenticación dado que deseamos que sea segura y podamos proteger los datos de los usuarios, aprendamos juntos como hacerlo \U0001F510"
---

# Avanzado \#2 Autenticación básica con Auth0 🔒

## 💡 Introducción 💡

En este desafío vamos a aprender a tener una autenticación con [Auth0](https://auth0.com/) y las ventajas de usarla.  
En un mundo donde casi tod@s usan la misma contraseña para todo, la fecha de su cumpleaños, el nombre de su mascota, entre otras malas prácticas para protección de datos, te estás asegurando de cuidar la información de manera simple. 🔐

\*\*\*\*[**¡Aquí puedes encontrar un demo!**](https://shorturl.at/byCW0)\*\*\*\*

## Paso 1: **Creemos nuestra App de Angular** 🅰️ <a id="paso-1-creemos-nuestra-app-de-angular"></a>

Entra a [**www.stackblitz.com**](https://stackblitz.com/), y verás algo como esto:

![](https://blobscdn.gitbook.com/v0/b/gitbook-28427.appspot.com/o/assets%2F-LW1Rd6Lo-WMisT20MSI%2F-LfkG9FnieTyrSrzuXpf%2F-LfkL1kfzmm5NbCpp7Bn%2F1.png?alt=media&token=c53de18e-d4ad-429e-a53d-90c4f288eb14)

![](https://blobscdn.gitbook.com/v0/b/gitbook-28427.appspot.com/o/assets%2F-LW1Rd6Lo-WMisT20MSI%2F-LfkG9FnieTyrSrzuXpf%2F-LfkL_8jRYal27_KSvzl%2FScreen%20Shot%202019-05-25%20at%201.56.29%20PM.png?alt=media&token=51d5597c-a0fb-4530-afbf-104ee3c4cc89)

## Paso 2: **Vamos a crear una cuenta en Auth0** 

Esta cuenta es totalmente gratuita, Auth0 se encargará de la autenticación de los usuarios por nosotros, ellos tienen unos servicios, llamados API donde tú los llamas y según la información que le envíes él te responderá si es el usuario correcto, también nos realizará procesos de autenticación de terceros como Google o recordar contraseña, se asegurará que no sea un correo maligno que le este haciendo peticiones cuando intenta recordar la contraseña y que no están tratando de atacar tu aplicación, asiendo así, un inicio de sesión muy seguro.  
  
Entra a [**https://auth0.com/**](https://auth0.com/), y crearas una cuenta así:

![](../.gitbook/assets/screen-shot-2019-11-05-at-12.19.31-am.png)

![](../.gitbook/assets/screen-shot-2019-11-05-at-12.20.26-am.png)

Podrás crear una cuenta con un usuario y contraseña o con una cuenta que ya tengas anteriormente por un tercero.  
Yo usare la de Google para este ejemplo.

![](../.gitbook/assets/screen-shot-2019-11-05-at-12.26.11-am.png)

Cuando ya ingreses a tu cuenta, podrás ver una plataforma de manejo de tus aplicaciones e inicios de sesión en ella, puedes sacar estadísticas, hacer grupos por roles y permisos, decir a que usuario les va a otorgar ciertos accesos y a cuales no. ¡Y mucho más!

![](../.gitbook/assets/screen-shot-2019-11-05-at-12.39.51-am.png)

Al darle click en **+ Create Application** creamos una nueva instancia para manejar el inicio de sesión de nuestra aplicación.  
Y seleccionamos **Single Page Web Application** como el tipo de autenticación que vamos a usar.

![](../.gitbook/assets/screen-shot-2019-11-05-at-12.42.54-am%20%281%29.png)

Curando ya tengamos nuestra nueva instancia, Auth0 nos va a proveer de un client ID que usaremos para todos los llamados a su API.

![](../.gitbook/assets/screen-shot-2019-11-05-at-7.13.46-am.png)

Vamos a tomar la URL de nuestra aplicación que nos genera [https://stackblitz.com/](https://stackblitz.com/) y vamos a usarla para que Auth0 sepa que cuando hagamos un llamado a su API desde nuestra aplicación, nos responda con la configuración que esperamos al respecto.

![](../.gitbook/assets/screen-shot-2019-11-05-at-7.29.03-am.png)

Esta es la ubicación de la URL de nuestra aplicación en [https://stackblitz.com/](https://stackblitz.com/)  
Guarda los cambios y estas listo para usarla.

## Paso 3: **Vamos insertar la funcionalidad para hacer llamados a funcionalidades externas como una API y adicionaremos router.**

Ya aprendiste como adicionar router, ahora vamos a adicionar la funcionalidad  HTTP Client Module en nuestro  `app.module.ts`  y  luego hacemos su llamado a desde `imports`

```typescript
import { HttpClientModule } from '@angular/common/http';
```

![](../.gitbook/assets/screen-shot-2019-11-05-at-7.44.10-am.png)

```typescript
import { RouterModule } from '@angular/router';
```

![](../.gitbook/assets/screen-shot-2019-11-05-at-9.16.45-am.png)

## Paso 4: **Adicionar las variables de configuración**

En este archivo vamos a sacar las variables necesarias para manejar nuestra aplicación, esta va a ser la información que le entregaremos a la API de Auth0 y con ella nos identificaremos.  
vamos a crear un archivo llamado donde las pondremos  **auth0-variables.ts**

{% code-tabs %}
{% code-tabs-item title="auth0-variables.ts" %}
```typescript
interface AuthConfig {
  clientID: string;
  domain: string;
  audience: string;
  redirectUri: string;
}

export const AUTH_CONFIG: AuthConfig = {
  clientID: '',// TODO: '<YOUR_AUTH0_CLIENT_ID>'
  domain: '', // TODO '<YOUR_AUTH0_DOMAIN>'
  audience: '', // TODO: https://<YOUR_AUTH0_DOMAIN>/userinfo
  redirectUri: "https://angular-basic-with-auth0.stackblitz.io/callback",
};
```
{% endcode-tabs-item %}
{% endcode-tabs %}

![](../.gitbook/assets/screen-shot-2019-11-05-at-8.53.40-am.png)

## **No olvides, que cuando termines el ejercicio debes borrar esas variables, para que personas en internet no usen tu cuenta sin tu autorización.**

## Paso 5: **Crea un servicio de autenticación**

La mejor manera de administrar y coordinar las tareas necesarias para la autenticación del usuario es crear un servicio reutilizable. Con el servicio en su lugar, podrá llamar a sus métodos a través de su aplicación. Se puede crear una instancia del objeto WebAuth de auth0.js en el servicio **AuthService.ts.**

```typescript
import { HttpClientModule } from '@angular/common/http';
```

![](../.gitbook/assets/screen-shot-2019-11-05-at-7.44.10-am.png)

##  Paso 3: **Vamos a crear nuestra clase Callback**

![](../.gitbook/assets/screen-shot-2019-11-05-at-7.44.10-am.png)

Para manejar la ruta de devolución de llamada \([http: // localhost: 3000 / callback](https://angular-basic-with-auth0.stackblitz.io/callback)\), definamos este componente, cree un nuevo archivo llamado **callback.ts** dentro del directorio src/App e inserte el siguiente código:

{% code-tabs %}
{% code-tabs-item title="app.component.html" %}
```markup
<div class="center">

	<div class="card">
		<div class="additional">
			<div class=
```
{% endcode-tabs-item %}
{% endcode-tabs %}

>

  
Yo usare la de Google para este ejemplo.

Entra a [**www.stackblitz.com**](https://stackblitz.com), y verás algo como esto:

![](../.gitbook/assets/1.png)

![](../.gitbook/assets/screen-shot-2019-05-25-at-1.56.29-pm.png)

## Paso 2: **Vamos a la estructura** básica **HTML 💀**

Vamos a adicionar la estructura básica que va a tener nuestro formulario para que tengamos mucho mas claro como vamos a visualizar nuestros datos.  
Reemplazaremos el contenido del archivo **app.component.html** y adicionaremos lo siguiente:

