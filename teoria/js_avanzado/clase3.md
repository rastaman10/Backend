![logotipo de The Bridge](https://user-images.githubusercontent.com/27650532/77754601-e8365180-702b-11ea-8bed-5bc14a43f869.png  "logotipo de The Bridge")


# [Bootcamp Web Developer Full Stack](https://www.thebridge.tech/bootcamps/bootcamp-fullstack-developer/)
### JS, ES6, Node.js, Frontend, Backend, Express, React, MERN, testing, DevOps

## Clase 3

### GitHub: Trabajar en equipo

### Hacer Pull Request
Los usuarios realizan sus modificaciones en el respositorio local. Cuando han terminado crean
un **`pull request`** y lo envían al repositorio. Sus cambios deben ser aprobados
por el administrador

![img](../../assets/js_avanzado/clase3/pullrequest.png)

- [how-to-make-your-first-pull-request](https://www.freecodecamp.org/news/how-to-make-your-first-pull-request-on-github-3/)
- [tutorial-simple-primer-pr-pull-request](https://blog.desdelinux.net/tutorial-simple-primer-pr-pull-request/)


### Actualizar un Fork

![img](../../assets/js_avanzado/clase3/update_fork.png)

- [how-to-update-a-fork-in-git](https://medium.com/@sahoosunilkumar/how-to-update-a-fork-in-git-95a7daadc14e)
- [collaborating-with-issues-and-pull-requests](https://docs.github.com/en/github/collaborating-with-issues-and-pull-requests/syncing-a-fork/)


## TALLER: `Git y GitHub` - Trabajar en equipo en un proyecto - Diámica con Owner + Forks

En equipos de 3 personas vamos a aprender a trabajar en equipo con GitHub para:
- Subir cambios a un proyecto
- Hacer Pull Requests
- Actualizar Fork
- Rechazar PR y comentar cambios

![img](../../assets/js_avanzado/clase3/prmeme.jpg)

Para ejercitar el uso de **`Git y GitHub`** en equipo el grupo deberá realizar un proyecto simple que consistirá en:

- Construir en `HTML` un formulario simple con los campos *usuario* y *contraseña* y un botón de envío. 

- Dar estilos con `CSS` a dicho formulario para que la interacción con él sea agradable y sencilla (tener en cuenta accesibilidad y usabilidad).

- Validar con `JavaScript` el nombre de *usuario* y *contraseña*. Para ello se almacenará en el fichero un array de al menos 3 objetos con las propiedades *usuario* y *contraseña*. 

- Añadir una pequeña descripción del proyecto en el fichero `README.md`

### Flujo de trabajo con Git y GitHub. Fork y branches

1. Un integrante del grupo (Owner) deberá crear un repositorio en Github. Creará en la rama `main` la estructura base del proyecto. Esta estructura estará compuesta de al menos: un fichero HTML, un fichero CSS, un fichero JS, las carpetas que consideren necesarias para que el proyecto esté correctamente organizado. 

2. El Owner creará en su repo la rama `develop`, sobre la que se recibirán los cambios. **No volveremos a tocar la rama `main`**. 

3. Sus compañero/s se harán Fork del repositorio.

4. Cada integrante se clonará su Fork en local. Una vez definidas las tareas que realizará cada integrante del equipo, deberán moverse a la rama `develop` y sacar una `nueva rama`. Las ramas deben tener **el nombre de la funcionalidad** en la que se está trabajando. 

5. Cada integrante trabajará en su rama y cuando termine una parte pusheará a su correspondiente fork los `commits`. (*recordar que los commits pueden hacerse en local las veces que sean necesarias y luego subir todos los cambios de una sola vez al repositorio remoto. También tener en cuenta que puede que algún integrante del equipo necesite al menos una parte del trabajo de otro. En ese caso puede que sea necesario hacer push antes de tener la tarea 100% terminada*).


6. Tras hacer los cambios, se hará push al repositorio Fork de GitHub con la rama nueva. Después "Pull Request" al repo original de la rama nueva a Develop del repo original. `rama_nueva(fork) -> develop(owner)`. (recordad no tocar `main`)

7. El resto de integrantes tienen que actualizar sus forks, dado que el repo original ha cambiado, tanto en `local` como en `remoto`. 

8. El Owner del repo *revisará el código de los compañeros y dejará comentarios* si los considera necesarios. Si en alguna **`PR`** surgen **conflictos**, deberán resolverlos juntos para estar seguros de que el código siga funcionando. Cuando esté todo listo y revisado, se mergearán las actualizaciones en `develop`.

9. Cuando se termine el trabajo en una rama individual y se haya mergeado correctamente en `develop` se deberá borrar la rama individual tanto del repositorio local como del repositorio Fork en GitHub. 


📌 [**Buscador de comandos de Git**](https://gitexplorer.com/) 📌

**Y recuerda...**

![In case of fire](../../assets/js_avanzado/clase3/fire.png)







