![logotipo de The Bridge](https://user-images.githubusercontent.com/27650532/77754601-e8365180-702b-11ea-8bed-5bc14a43f869.png "logotipo de The Bridge")

# [Bootcamp Web Developer Full Stack](https://www.thebridge.tech/bootcamps/bootcamp-fullstack-developer/)

### JS, ES6, Node.js, Frontend, Backend, Express, React, MERN, testing, DevOps

## Clase 12

### Más sobre Offline: HTML5: Service Workers

### Offline: Usando Service Workers

![img](../../assets/js_avanzado/clase12/service-worker.png)

- [Service workers, servicios web más allá del navegador](https://www.arsys.es/blog/programacion/service-worker/)
- [Service Workers registrados en nuestro navegador chrome://serviceworker-internals/](chrome://serviceworker-internals/)
- [MDN | Service Workers MDN API](https://developer.mozilla.org/es/docs/Web/API/Service_Worker_API)
- [Introducción a los Service Workers](https://developers.google.com/web/fundamentals/primers/service-workers?hl=es)
- [PWA: Conceptos básicos sobre Service Workers - el abismo de null](https://elabismodenull.wordpress.com/2017/11/17/pwa-conceptos-basicos-sobre-service-workers/)

¿Recuerdas Web Workers?
> Un service worker es una secuencia de comandos ejecutados por el navegador en segundo plano. Se trata de un fichero JavaScript que continúa ejecutándose aunque el sitio web se cierre.

**Características**
- No se puede directamente al DOM, sino que se comunica con las páginas que controla mediante la interfaz PostMessage.
- Al ser un proxy de red programable, permite controlar el modo en que se manejan las solicitudes de red de la página.
- Capaces de mantener información mediante la API de IndexedDB.
- Pueden implementar diferentes sistemas de cacheo.

**Lo que necesitamos tener**
- Soporte del navegador
- Uso de HTTPS. Necesitaremos configurar HTTPS en el servidor

***Usos**
- Realizar tareas de cacheo de información. 
- Podemos tener un sistema por donde recibir notificaciones Push. 
- Permite sincronizar datos en segundo plano. Por si *cae la conexión*, para no dejar colgado al usuario.
- Permite instalar y actualizar nuestra aplicación. 

```javascript
// Ejemplo - registro de Service Worker
if ('serviceWorker' in navigator) {
   window.addEventListener('load', function() {
     navigator.serviceWorker.register('/miServiceWorker.js').then(function(registration) {
       // Si es exitoso
       console.log('Service Worker registrado correctamente');
     }, function(err) {
       // Si falla
       console.log('SW fallo', err);
     });
   });
 }
```


### HTML5:PWA
![img](../../assets/js_avanzado/clase12/pwa.png)
![img](../../assets/js_avanzado/clase12/pwa-hero.jpg)

**Documentación**
- [Progressive Web Apps by Google Developers](https://developers.google.com/web/progressive-web-apps/)

**Recursos**
- [Awesome PWA](https://github.com/hemanth/awesome-pwa)
- [PWA Builder - comprueba cómo de PWA es tu app](http://www.pwabuilder.com/generator)
- [Introducing Pokedex.org: a progressive webapp for Pokémon fans](http://www.pocketjavascript.com/blog/2015/11/23/introducing-pokedex-org)
- [GitBook | @jdonsan: Desarrolla Progressive Web Apps](https://jdonsan.gitbooks.io/desarrolla-progressive-web-apps/content/)
- [el.abismo = de[null] | Serie PWA](https://elabismodenull.wordpress.com/category/series/serie-pwa/)

Checklist de PWA
- [Checklist de PWA](https://developers.google.com/web/progressive-web-apps/checklist)

### Ejemplos/Tutoriales PWA
- [how-to-build-a-pwa-with-html-css-and-vanillajs](https://dev.to/faisaljebali/how-to-build-a-pwa-with-html-css-and-vanillajs-3lf7)
- [build-a-pwa-from-scratch-with-html-css-and-javascript](https://www.freecodecamp.org/news/build-a-pwa-from-scratch-with-html-css-and-javascript/)
- [New Progressive Web App training now available](https://web.dev/new-pwa-training/)
- [build-a-simple-first-progressive-web-app-pwa](https://thanhtungvo.medium.com/build-a-simple-first-progressive-web-app-pwa-a7342173470b)
- [pwa-going-offline](https://developers.google.com/codelabs/pwa-training/pwa03--going-offline#0)
- [the-progressive-web-apps-guide-youve-been-looking-for](https://betterprogramming.pub/the-progressive-web-apps-guide-youve-been-looking-for-5ae3fa2cea83)


![img](../../assets/js_avanzado/clase12/pwa_meme.jpg)




