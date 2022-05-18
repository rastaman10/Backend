![logotipo de The Bridge](https://user-images.githubusercontent.com/27650532/77754601-e8365180-702b-11ea-8bed-5bc14a43f869.png "logotipo de The Bridge")

# [Bootcamp Web Developer Full Stack](https://www.thebridge.tech/bootcamps/bootcamp-fullstack-developer/)

### JS, ES6, Node.js, Frontend, Backend, Express, React, MERN, testing, DevOps

## Clase 13

### Más herramientas de auditoría para Web Developers

### PageSpeed

![Logo](../../assets/js_avanzado/clase13/pagespeed.png)

- [¿Qué es PageSpeed?](https://www.wpdoctor.es/pagespeed-que-es-y-como-usarlo/)
- [PageSpeed](https://developers.google.com/speed/pagespeed/insights/)

### Lighthouse

![img](../../assets/js_avanzado/clase13/lighthouse.png)

- [Extensión de Chrome](https://chrome.google.com/webstore/detail/lighthouse/blipmdconlkpinefehnmjammfjpmpbjk?hl=es)

### Más APIs de HTML5

![Chart](../../assets/js_avanzado/clase13/html5.jpg)

Listado completo
- [javascript-api-html5](https://www.digitallearning.es/blog/javascript-api-html5/)
- [15-apis-de-html5]( https://www.htmlcinco.com/15-apis-de-html5/)

Overview sobre algunas de las más importantes
- [Eventos online y offline](https://developer.mozilla.org/es/docs/Web/API/NavigatorOnLine/Eventos_online_y_offline)

Offline: Comprobación de conexión
```javascript
if (window.navigator.onLine) {
    const detalles = `<h1>Hay conexión a Internet!!</h1>
    <h3>Detalles del browser:</h3>
    <p>CodeName: ${navigator.appCodeName}</p>
    <p>Nombre: ${navigator.appName}</p>
    <p>¿Versión?: ${navigator.appVersion}</p>
    <p>Cookies?: ${navigator.cookieEnabled}</p>
    <p>Lenguaje?: ${navigator.language}</p>
    <p>Plataforma: ${navigator.platform}</p>
    <p>User-agent header: ${navigator.userAgent}</p>`;
    document.body.innerHTML = detalles;

} else {
    document.body.innerHTML = "<h1>No hay conexión!!</h1>"
    console.warn("Sorry, no hay conexión a Internet!");
}	
```
Offline: Verificando conexión con eventos
```javascript
window.addEventListener("offline", () => {
    console.warn("Te has desconectado!")
});

window.addEventListener("online", () => {
    console.info("Te has conectado!")
});
```
- [Offline Storage](https://www.hongkiat.com/blog/html5-offline-storage/)
- [Web Workers](https://www.w3schools.com/html/html5_webworkers.asp)
- [File System](https://www.javascripture.com/File)

### Extensiones para Web Developers en Visual Studio


![img](../../assets/js_avanzado/clase13/visualstudio.jpg)

- [top-vs-code-extensions-for-web-developers](https://www.elegantthemes.com/blog/wordpress/top-vs-code-extensions-for-web-developers)
- [15-best-visual-studio-code-extensions-for-web-developers](https://www.syncfusion.com/blogs/post/15-best-visual-studio-code-extensions-for-web-developers.aspx)

