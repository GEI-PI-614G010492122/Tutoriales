# Visual Studio Code Tutorial

En este tutorial vamos a ver cómo configurar Visual Studio Code así como sus principales funcionalidades. Para un mayor aprovechamiento en la asignatura enfocaremos este tutorial a entorno de programación Python. Más específicamente, al finalizar el mismo tendréis configurado un entorno de desarrollo preparado para un proyecto Django con vistas a la práctica a realizar.

## Tabla de contenidos
1. [Comencemos](#desc)
2. [Aspectos generales](#tips)
3. [Extensiones](#ext)
4. [Debugging](#debug)
5. [Sistema control de versiones](#git)
6. [Remote-Containers](#container)
7. [Django](#django)

<a name="desc"></a>
# 1. Comencemos
## Setting up Visual Studio Code
VS Code es un editor de código fuente gratuito y [*open-source*](https://github.com/microsoft/vscode) disponible para Linux, macOS y Windows. A continuación se enlazan las guías de instalación específicas para cada plataforma:
* [macOS](https://code.visualstudio.com/docs/setup/mac)
* [Linux](https://code.visualstudio.com/docs/setup/linux)
* [Windows](https://code.visualstudio.com/docs/setup/windows)
## Interfaz de usuario

La siguiente figura muestra la disposición básica de componentes en VS Code.

<p align="center">
  <img src="https://code.visualstudio.com/assets/docs/getstarted/userinterface/hero.png" alt="Figure 1"/>
</p>


Entre los componentes básicos encontraremos:
* **Activity Bar**. Situada en el borde vertical izquierdo, contiene el explorador de archivos, el administrador de extensiones, un buscador, el administrador de código fuente (e.g. Git), acceso a la herramienta de ejecución y depuración, entre otros. Los elementos de la activity bar podrán aumentar dependiendo de las extensiones que tengamos instaladas.
* **Side Bar**. Situada a la derecha de la activity bar, muestra información de distinta naturaleza dependiendo de la herramienta seleccionada, como podría ser la estructura de directorios de nuestro proyecto.
* **Editor Groups**. Región principal de la herramienta y desde donde editaremos nuestros ficheros fuente. Visual Studio Code permite dividir en celdas verticales y horizontales esta región, de manera que podemos tener distintos ficheros visibles simultáneamente. Para ello bastaría con seleccionar y arrastrar una pestaña por dicha región y el editor ya nos irá marcando las distintas formas en las que podemos ir dividiendo esta vista. Para más información acerca de esta funcionalidad, consultar [side-by-side-editing](https://code.visualstudio.com/docs/getstarted/userinterface#_side-by-side-editing) y [grid-layout](https://code.visualstudio.com/docs/getstarted/userinterface#_grid-editor-layout).
* **Panel**. Situado por defecto debajo del editor, muestra información de salida y de debugging, problemas o warnings de nuestra ejecución y también integra una terminal.
* **Status Bar**. Situada en el borde inferior, resume la información general de nuestro proyecto: rama del repositorio en la que nos encontramos, errores, warnings, etc.

<a name="tips"></a>
# 2. Aspectos generales
La paleta de comandos es el punto de encuentro a todas las funcionalidades de VS Code. Para acceder a la Paleta de Comandos podemos ir a ```Ver > Paleta de comandos``` o usando los atajos de teclado: ⌘P en macOS o Ctrl+P en Linux/Windows. 

Podemos utilizar esta herramienta para buscar por nombre los ficheros que hemos utilizado recientemente, por ejemplo.

<p align="center">
  <img src="https://user-images.githubusercontent.com/38211239/157474152-ec25afba-d3f5-4fa9-b284-8711e4607eef.png" alt="Figure 2"/>
</p>

Una funcionalidad interesante si estamos intercambiando continuamente entre dos ficheros es la combinación Ctrl+P+P (⌘PP).

Sin embargo, la paleta de comandos no es meramente un buscador de archivos, sino que nos ofrece funcionalidades mucho más potentes e interesantes. Si escribimos ```?``` en la ventana emergente podremos ver la lista de "comodines" empleados en VS Code para representar las funcionalidades ofrecidas. Algunas de las opciones más interesantes están representadas por los caracteres: ```@```, ```#```, ```>``` ó ```:```. Vamos a ver cada uno por separado.

<p align="center">
  <img src="https://user-images.githubusercontent.com/38211239/157477862-621181ce-3450-4c94-9fc1-42504cf6d965.png" alt="Figure 2"/>
</p>

* ```@``` : Nos permite buscar un símbolo por nombre en el fichero actual. Lo que VS Code llama símbolo puede ser una variable, una clase, un método, ...

<p align="center">
  <img src="https://user-images.githubusercontent.com/38211239/157477933-f7ad4e80-2e55-4c09-908d-13ba205ea39e.png" alt="Figure 2"/>
</p>

Si añadimos ```:``` después de ```@```, las coincidencias serán agrupadas según su categoría (variables, métodos, clases, etc).

<p align="center">
  <img src="https://user-images.githubusercontent.com/38211239/157479335-6e6b7c61-4598-4b3e-8770-e40bfa79ae3b.png" alt="Figure 2"/>
</p>

* ```#``` : Permite extender la búsqueda de símbolos a otros ficheros del proyecto, no necesariamente el actual (⌘T)

<p align="center">
  <img src="https://user-images.githubusercontent.com/38211239/157479560-d962d349-b002-4524-8398-b76ca3e7637c.png" alt="Figure 2"/>

</p>

* ```:``` : permite ir a una línea concreta del fichero actual (e.g. ```:50``` nos llevaría a la línea número 50)
* ```>``` : Representa la parte central de la Paleta de Comandos y permite mostrar y ejecutar múltiples comandos del editor. Podemos desde ejecutar nuestro proyecto, depurarlo, ejecutar órdenes de nuestro sistema control de versiones (e.g. pull, push, clone, etc), abrir una nueva terminal, hasta cambiar el tema/apariencia de nuestro editor, entre muchísimas otras.

Para mayor información acerca de la paleta de comandos, consultar [command palette](https://code.visualstudio.com/docs/getstarted/userinterface#_command-palette).

<p align="center">
  <img src="https://user-images.githubusercontent.com/38211239/157478066-bcf9a22e-261b-4942-97db-8d97bf0700ea.png" alt="Figure 2"/>
</p>

Un atajo fuera de la paleta de comandos, pero muy útil sobre todo cuando estamos familiarizándonos con un proyecto nuevo y/o ajeno, es el de 'Ir a definición/Go to definition'. Para ello situamos el cursor encima de una definición (puede ser una llamada a método, llamada a clase, llamada a función, etc) y pulsamos ```F12```. En ese momento VS Code nos llevará al lugar donde se ha hecho la declaración del objeto en cuestión.

Para quién quiera profundizar/investigar sobre otros atajos, *edit hacks* o "trucos" que pueden mejorar vuestra productividad, se recomienda consultar: [VS Code tips and tricks](https://code.visualstudio.com/docs/getstarted/tips-and-tricks).

<a name="ext"></a>
# 3. Extensiones

Las funcionalidades que ofrece VS Code out-of-the-box pueden ser extendidas por medio de extensiones o plugins. Esto nos permitirá configurar nuestro editor de código *ad libitum*, incorporando nuevas capas de funcionamiento extra y consiguiendo un comportamiento cercano al de un IDE pero de una forma mucho más ligera, flexible, personalizada y sobre todo, gratuita.

Instalar nuevas extensiones es muy sencillo. Bastaría con seleccionar la pestaña de "Extensiones" en la Activity Bar, que nos llevará al MarketPlace donde podremos buscar por nombre la extensión deseada e instalarla.

<p align="center">
  <img src="https://user-images.githubusercontent.com/38211239/157483945-773ac0b5-193b-40b6-8851-0465cf2f690a.png" alt="Figure 2"/>


Algunas de las extensiones recomendadas para esta asignatura son:
* [Python](https://marketplace.visualstudio.com/items?itemName=ms-python.python) (versión oficial de Microsoft)
* [Jupyter](https://marketplace.visualstudio.com/items?itemName=ms-toolsai.jupyter) (versión oficial de Microsoft)
* [Pylance](https://marketplace.visualstudio.com/items?itemName=ms-python.vscode-pylance) (versión oficial de Microsoft)
* [Remote - WSL](https://marketplace.visualstudio.com/items?itemName=ms-vscode-remote.remote-wsl) (para usuarios de Windows. Versión oficial de Microsoft)
* [Docker](https://marketplace.visualstudio.com/items?itemName=ms-azuretools.vscode-docker) (versión oficial de Microsoft)
* [Remote - Containers](https://marketplace.visualstudio.com/items?itemName=ms-vscode-remote.remote-containers) (versión oficial de Microsoft)
* [HTML snippets](https://marketplace.visualstudio.com/items?itemName=abusaidm.html-snippets)
* [Django](https://marketplace.visualstudio.com/items?itemName=batisteo.vscode-django).

En relación con la extensión de Python, en caso de tener múltiples intérpretes instalados, deberemos seleccionar en la parte inferior del editor la versión del mismo que deseamos utilizar.

  
<p align="center">
  <img src="https://user-images.githubusercontent.com/38211239/159157560-78dc441c-9e66-4ce9-ade6-7f298bfe4729.png" alt="Figure 2"/>


Otras extensiones de propósito general que pueden ser interesantes:
* [Bracket Pair Colorizer](https://marketplace.visualstudio.com/items?itemName=CoenraadS.bracket-pair-colorizer)
* [Git History](https://marketplace.visualstudio.com/items?itemName=donjayamanne.githistory)
* [Better Comments](https://marketplace.visualstudio.com/items?itemName=aaron-bond.better-comments)
* [Code Spell Checker](https://marketplace.visualstudio.com/items?itemName=streetsidesoftware.code-spell-checker)
* [Prettier - Code formatter](https://marketplace.visualstudio.com/items?itemName=esbenp.prettier-vscode)
* [Rewrap](https://marketplace.visualstudio.com/items?itemName=stkb.rewrap)

Se recomienda que, antes de instalar una extensión, se lea la descripción asociada y las funcionalidades que ofrece, se valore su necesidad y, en caso de instalarla, se configure tal y como se indica, si procede. En general, la mayoría de extensiones nos proporcionan un comportamiento por defecto sin necesidad de realizar una configuración específica. Sin embargo, casi todas ellas pueden configurarse para obtener un comportamiento más adaptado a nuestras necesidades.

<a name="debug"></a>
# 4. Debugging

Como hemos mencionado anteriormente, podemos encontrar un acceso directo al depurador de VS Code en la Activity Bar lateral.
El primer paso para poder debuggear nuestro código es crear un archivo ```launch.json``` que configure nuestro entorno de depuración.

<p align="center">
  <img src="https://user-images.githubusercontent.com/38211239/157497614-94858087-5516-4f02-b83c-eb8ee6d66762.png" alt="Figure 2"/>
</p>

En caso de no tener un fichero ```launch.json``` creado, VS Code ofrece una serie de plantillas de configuración básicas para distintos lenguajes/librerías/herramientas. En este caso, vamos a seleccionar una plantilla básica para Python. No obstante, como podemos ver en la siguiente figura, también tenemos la posibilidad de generar una plantilla para una aplicación Django. Veremos esta opción más adelante.

<p align="center">
  <img src="https://user-images.githubusercontent.com/38211239/157497690-1cd2ec65-df46-448b-b5fc-e03fd3df6a56.png" alt="Figure 2"/>
</p>

Existen diversos parámetros de configuración adicionales que pueden resultar de especial utilidad en nuestro entorno de trabajo dependiendo de nuestras necesidades. Podéis encontrar un listado de estos parámetros en: [additional configurations](https://code.visualstudio.com/docs/python/debugging#_additional-configurations).

<p align="center">
  <img src="https://user-images.githubusercontent.com/38211239/157497773-d061e403-563b-437a-9fff-e1b19e3e862a.png" alt="Figure 2"/>
</p>

Para comenzar el proceso de depuración, el primer paso sería definir los puntos de ruptura, pinchando en la parte izquierda de la línea en cuestión, de manera que aparezca un punto rojo que corrobore la selección hecha. A continuación, pinchamos en el símbolo "Play" situado en la parte superior de la Side Bar (```F5```). Nótese que debemos de tener seleccionada la plantilla de configuración que hemos creado previamente en el desplegable que está a la derecha del símbolo "Play" mencionado.

En este instante, aparecerá una pequeña barra de herramientas sobre el *Editor Group* que nos permitirá, de izquierda a derecha: continuar nuestra ejecución hasta el siguiente punto de ruptura (Continue), depurar paso a paso por procedimientos (step over), depurar paso a paso por instrucciones (step into), salir de la depuración (step Out), reiniciar la depuración (restart) y pausar la depuración (stop). Este funcionamiento es común a cualquier otra herramienta de depuración en IDE/editor de código que hayáis utilizado.

<p align="center">
  <img src="https://user-images.githubusercontent.com/38211239/159155302-d61b045d-7c34-4ddb-b70c-1a955fa5a676.png" alt="Figure 2"/>
</p>

Cuando la ejecución del código llegue a uno de los puntos de ruptura establecidos previamente, la Side Bar mostrará el estado de las variables definidas hasta ese momento en nuestro programa.

Existe la posibilidad de ver la evolución de una variable específica escribiendo su nombre en el bloque "Inspección" que podemos encontrar en la Side Bar (```Inspección > Agregar expresion```).

<p align="center">
  <img src="https://user-images.githubusercontent.com/38211239/159155322-86ab5b9b-62f2-4453-b4e8-94bbf07e9fbf.png" alt="Figure 2"/>
</p>



También podremos configurar un punto de ruptura para que tenga un comportamiento distinto al por defecto. Esto puede ser interesante, por ejemplo, si queremos que el punto de ruptura definido no pare la ejecución del programa y simplemente escriba un log. Podremos ver dicho log en la "Consola de depuración", dentro del Panel de VS Code. Para ello hacemos click con el botón derecho sobre el punto de ruptura y seleccionamos ```Editar punto de interrupción > Mensaje de registro```. En el input text que nos aparece escribiríamos el mensaje que queremos imprimir, pudiendo imprimir el contenido de variables mediante la notación ```{variable}```.

<p align="center">
  <img src="https://user-images.githubusercontent.com/38211239/157497911-4275eacc-320d-40d4-b0d4-8ff529b71ded.png" alt="Figure 2"/>
</p>

También podremos configurar un punto de ruptura para que solo se pare la ejecución de nuestro programa cuando se cumpla una determinada condición ```Editar punto de interrupción > Expresión```. Por ejemplo, cuando una variable tenga asignado un valor concreto.

<p align="center">
  <img src="https://user-images.githubusercontent.com/38211239/157497967-a29a8859-0107-4e4f-b4f6-9c6f88041173.png" alt="Figure 2"/>
</p>

También existe la posibilidad de configurar el depurador para que detecte y muestre las partes del código en las que se haya producido una excepción. Para ello tenemos que seleccionar el checkbox asociado ```Raised Exceptions``` dentro del grupo "Puntos de Interrupción" situado en la Side Bar (en la parte inferior).

<p align="center">
  <img src="https://user-images.githubusercontent.com/38211239/159155326-9af4b404-faf9-4d41-97fd-cd511605e664.png" alt="Figure 2"/>
</p>


<a name="GIT"></a>
# 5. Sistema control de versiones

VS Code integra por defecto el Source Control Management (SCM) e incluye soporte a Git out-of-the-box.

Así, podremos inicializar un repositorio nuevo dentro del proyecto en el que nos encontramos en caso de que aún no lo hayamos hecho.

<p align="center">
  <img src="https://user-images.githubusercontent.com/38211239/159155479-d6b889d1-d237-4480-85b8-e5bc01a7de2e.png" alt="Figure 2"/>
</p>



Para hacer un commit, la dinámica es muy sencilla. Pinchamos sobre el símbolo ```+``` encima de aquellos ficheros que queramos incluir y damos un mensaje al commit. Una vez incluido un fichero podrá volver a ser eliminado del commit pinchando sobre el símbolo ```-```.

<p align="center">
  <img src="https://user-images.githubusercontent.com/38211239/159155513-2d65cc44-f3ef-41a4-9d1b-ec1f6f69157b.png" alt="Figure 2"/>
</p>

Una vez añadidos todos los ficheros que queremos, pinchamos sobre "Confirmar" para realizar el commit.


![git4](https://user-images.githubusercontent.com/38211239/157498103-893f9a3c-ece0-43be-8d4a-51c4c4c75d78.png)

Veremos que nuestro commit aparece en el bloque "COMMITS" de la side bar.

<p align="center">
  <img src="https://user-images.githubusercontent.com/38211239/159155659-aa80f7db-ff5a-4d81-b152-ed847171618b.png" alt="Figure 2"/>
</p>


Para hacer el commit público (hasta ahora sólo está en local), debemos hacer un push. Para ello pinchamos sobre el icono con una nube que aparece dentro del bloque COMMITS "Publish main to GitHub". Recordad que si no existe el repositorio en GitHub, primero debéis crearlo y ejecutar ```git remote add origin git@github.com:LopezCastroRoberto/finalexample.git``` para asociar vuestra rama main/master con el origin.


<p align="center">
  <img src="https://user-images.githubusercontent.com/38211239/159155684-1b022256-bff8-4d9d-a0c1-e66f479eed91.png" alt="Figure 2"/>
</p>


En este punto, si hacéis un cambio en local y pincháis sobre el fichero modificado (letra "M" de "Modified" a la derecha del fichero) podréis ver resaltadas las diferencias con respecto al último commit en el Edit Group.

![git8](https://user-images.githubusercontent.com/38211239/157498191-fb6f0f92-fa50-4ba8-a08c-8893014c1053.png)


Cualquier otra funcionalidad de Git (pull, clone, etc) puede encontrarse escribiendo su nombre en la Paleta de Comandos (e.g. Git: pull) o en los tres puntos situados a la derecha del bloque "CONTROL DE CÓDIGO FUENTE".
![git9](https://user-images.githubusercontent.com/38211239/157498205-6863663b-ab2c-46b3-8bd0-d8d362fabde8.png)


