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

## **No olvides, que cuando termines el ejercicio debes borrar esas variables, para que personas en internet no usen tu cuenta sin tu autorización o roben tu información.**

## Paso 5: **Crea un servicio de autenticación**

La mejor manera de administrar y coordinar las tareas necesarias para la autenticación del usuario es crear un servicio reutilizable. Con el servicio en su lugar, podrá llamar a sus métodos a través de su aplicación. Se puede crear una instancia del objeto WebAuth de auth0.js en el servicio **AuthService.ts.**

{% code-tabs %}
{% code-tabs-item title="AuthService.ts" %}
```typescript
import { Injectable } from "@angular/core";
import * as auth0 from "auth0-js";
import { environment } from "../../environments/environment";
import { Router } from "@angular/router";

(window as any).global = window;

@Injectable()
export class AuthService {
  auth0 = new auth0.WebAuth({
    // the following three lines MUST be updated
    domain: environment.domain, // TODO '<YOUR_AUTH0_DOMAIN>'
    audience: environment.audience, // TODO: https://<YOUR_AUTH0_DOMAIN>/userinfo
    clientID: environment.clientID, // TODO: '<YOUR_AUTH0_CLIENT_ID>'
    redirectUri: environment.redirectUri,
    responseType: "id_token",
    scope: "openid profile"
  });

  constructor(public router: Router) {}

  public login(): void {
    this.auth0.authorize();
  }

  public handleAuthentication(): void {
    this.auth0.parseHash((err, authResult) => {
      if (authResult && authResult.accessToken && authResult.idToken) {
        window.location.hash = "";
        this.setSession(authResult);
        this.router.navigate(["/"]);
      } else if (err) {
        this.router.navigate(["/"]);
        console.log(err);
        alert("Error: ${err.error}. Check the console for further details.");
      }
    });
  }

  private setSession(authResult): void {
    // Set the time that the Access Token will expire at
    const expiresAt = JSON.stringify(
      authResult.expiresIn * 1000 + new Date().getTime()
    );

    // If there is a value on the scope param from the authResult,
    // use it to set scopes in the session for the user. Otherwise
    // use the scopes as requested. If no scopes were requested,
    // set it to nothing
    const scopes = authResult.scope || this.requestedScopes || "";

    localStorage.setItem("access_token", authResult.accessToken);
    localStorage.setItem("id_token", authResult.idToken);
    localStorage.setItem("expires_at", expiresAt);
    localStorage.setItem("scopes", JSON.stringify(scopes));
  }

  public logout(): void {
    // Remove tokens and expiry time from localStorage
    localStorage.removeItem("access_token");
    localStorage.removeItem("id_token");
    localStorage.removeItem("expires_at");
    localStorage.removeItem("scopes");
    // Go back to the home route
    this.router.navigate(["/"]);
  }

  public isAuthenticated(): boolean {
    // Check whether the current time is past the
    // Access Token's expiry time
    const expiresAt = JSON.parse(localStorage.getItem("expires_at"));
    return new Date().getTime() < expiresAt;
  }

  public userHasScopes(scopes: Array<string>): boolean {
    const grantedScopes = JSON.parse(localStorage.getItem("scopes")).split(" ");
    return scopes.every(scope => grantedScopes.includes(scope));
  }
}

```
{% endcode-tabs-item %}
{% endcode-tabs %}

![](../.gitbook/assets/screen-shot-2019-11-05-at-9.20.41-am.png)

{% hint style="info" %}
**Por si tienes alguna duda. Aquí te explicamos cómo funciona: 👷‍♀️  
  
1.** En `auth0.WebAuth(` estamos asignando las variables de configuración que creamos en el paso anterior.  
**2.** El servicio incluye varios métodos para manejar la autenticación. **login:** las llamadas autorizan desde auth0.js que inicia el inicio de sesión universal.   
**handleAuthentication:** busca un resultado de autenticación en el hash de URL y lo procesa con el método parseHash de auth0.js.  
**setSession:** establece el token de acceso del usuario, el token de identificación y la hora en que caducará el token de acceso cerrar sesión: elimina los tokens del usuario del almacenamiento del navegador.  
**isAuthenticated:** verifica sí el tiempo de vencimiento del token de acceso ha pasado.

```text
El servicio incluye varios métodos para manejar la autenticación.

login: las llamadas autorizan desde auth0.js que inicia el inicio de sesión universal
handleAuthentication: busca un resultado de autenticación en el hash de URL y lo procesa con el método parseHash de auth0.js
setSession: establece el token de acceso del usuario, el token de identificación y la hora en que caducará el token de acceso
cerrar sesión: elimina los tokens del usuario del almacenamiento del navegador
isAuthenticated: verifica si el tiempo de vencimiento del token de acceso ha pasado
```
{% endhint %}

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

