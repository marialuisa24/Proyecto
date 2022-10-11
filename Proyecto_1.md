# **Introduccion al Git**

 ## **Indice**

1. ### ¿Que es Git?
2. ### Características
3. ### Órdenes básicas
4. ### Flujo de trabajo
5. ### Software que los usa como base

<br>
<hr>
<br>


## **Contenido**

1. ### **¿Que es Git?**
<br>
Git es un software de control de versiones diseñado por Linus Torvalds, pensando en la eficiencia, la confiabilidad y compatibilidad del mantenimiento de versiones de aplicaciones cuando estas tienen un gran número de archivos de código fuente. Su propósito es llevar registro de los cambios en archivos de computadora incluyendo coordinar el trabajo que varias personas realizan sobre archivos compartidos en un repositorio de código.

![](GIT.png)

<br>
<br>

2. ### **Características**
<br>

Entre las características más relevantes se encuentran:

 - Fuerte apoyo al desarrollo no lineal, por ende rapidez en la gestión de ramas y mezclado de diferentes versiones. Git incluye herramientas específicas para navegar y visualizar un historial de desarrollo no lineal. Una presunción fundamental en Git, es que un cambio será fusionado mucho más frecuentemente de lo que se escribe originalmente, conforme se pasa entre varios programadores que lo revisan.

 - Gestión distribuida. Al igual que Darcs, BitKeeper, Mercurial, SVK, Bazaar y Monotone, Git le da a cada programador una copia local del historial del desarrollo entero, y los cambios se propagan entre los repositorios locales. Los cambios se importan como ramas adicionales y pueden ser fusionados en la misma manera que se hace con la rama local.

 - Los almacenes de información pueden publicarse por HTTP, FTP, rsync o mediante un protocolo nativo, ya sea a través de una conexión TCP/IP simple o a través de cifrado SSH. Git también puede emular servidores CVS, lo que habilita el uso de clientes CVS pre-existentes y módulos IDE para CVS pre-existentes en el acceso de repositorios Git.

 - Los repositorios Subversion y svk se pueden usar directamente con git-svn.
Gestión eficiente de proyectos grandes, dada la rapidez de gestión de diferencias entre archivos, entre otras mejoras de optimización de velocidad de ejecución.
Todas las versiones previas a un cambio determinado, implican la notificación de un cambio posterior en cualquiera de ellas a ese cambio (denominado autenticación criptográfica de historial). Esto existía en Monotone.

 - Resulta algo más caro trabajar con ficheros concretos frente a proyectos, eso diferencia el trabajo frente a CVS, que trabaja con base en cambios de fichero, pero mejora el trabajo con afectaciones de código que concurren en operaciones similares en varios archivos.

<br>
<br>

3. ### **Órdenes básicas**
<br>

 - **git init:**

Esto crea un subdirectorio nuevo llamado .git, el cual contiene todos los archivos necesarios del repositorio – un esqueleto de un repositorio de Git. Todavía no hay nada en tu proyecto que esté bajo seguimiento.

 - **git fetch:**

Descarga los cambios realizados en el repositorio remoto.

 - **git merge <nombre_rama>:**

Impacta en la rama en la que te encuentras parado, los cambios realizados en la rama “nombre_rama”.

 - **git pull:**

Unifica los comandos fetch y merge en un único comando.

 - **git commit -m "<mensaje>":**

Confirma los cambios realizados. El “mensaje” generalmente se usa para asociar al commit una breve descripción de los cambios realizados.

 - **git push origin <nombre_rama>:**

Sube la rama “nombre_rama” al servidor remoto.

 - **git status:**

Muestra el estado actual de la rama, como los cambios que hay sin commitear.

 - **git add <nombre_archivo>:**

Comienza a trackear el archivo “nombre_archivo”.

 - **git checkout -b <nombre_rama_nueva>:**

Crea una rama a partir de la que te encuentres parado con el nombre “nombre_rama_nueva”, y luego salta sobre la rama nueva, por lo que quedas parado en esta última.

 - **git checkout -t origin/<nombre_rama>:**

Si existe una rama remota de nombre “nombre_rama”, al ejecutar este comando se crea una rama local con el nombre “nombre_rama” para hacer un seguimiento de la rama remota con el mismo nombre.

 - **git branch:**

Lista todas las ramas locales.

 - **git branch -a:**

Lista todas las ramas locales y remotas.

 - **git branch -d <nombre_rama>:**

Elimina la rama local con el nombre “nombre_rama”.

 - **git push origin <nombre_rama>:**

Commitea los cambios desde el branch local origin al branch “nombre_rama”.

 - **git remote prune origin:**

Actualiza tu repositorio remoto en caso de que algún otro desarrollador haya eliminado alguna rama remota.

 - **git reset --hard HEAD:**

Elimina los cambios realizados que aún no se hayan hecho commit.

 - **git revert <hash_commit>:**

Revierte el commit realizado, identificado por el “hash_commit”.

<br>
<br>

4. ### **Flujo de trabajo**
<br>

 - Git-Flow

Creado en 2010 por Vincent Driessen.​ Es el flujo de trabajo más conocido. Está pensado para aquellos proyectos que tienen entregables y ciclos de desarrollo bien definidos. ​Está basado en dos grandes ramas con infinito tiempo de vida (ramas master y develop) y varias ramas de apoyo, unas orientadas al desarrollo de nuevas funcionalidades (ramas feature-*), otras al arreglo de errores (hotfix-*) y otras orientadas a la preparación de nuevas versiones de producción (ramas release-*). La herramienta gitflow facilita la automatización de las tareas implicadas en este flujo de trabajo.

 - Master

Es la rama principal. Contiene el repositorio que se encuentra publicado en producción, por lo que debe estar siempre estable.

 - Development

Es una rama sacada de Master. Es la rama de integración, todas las nuevas funcionalidades se deben integrar en esta rama. Luego que se realice la integración y se corrijan los errores (en caso de haber alguno), es decir que la rama se encuentre estable, se puede hacer un merge de development sobre la rama Master.

 - Features

Cada nueva funcionalidad se debe realizar en una rama nueva, específica para esa funcionalidad. Estas se deben sacar de Development. Una vez que la funcionalidad esté desarrollada, se hace un merge de la rama sobre Development, donde se integrará con las demás funcionalidades.

 - Hotfix

Son errores de software que surgen en producción, por lo que se deben arreglar y publicar de forma urgente. Es por ello, que son ramas sacadas de Master. Una vez corregido el error, se debe hacer una unificación de la rama sobre Master. Al final, para que no quede desactualizada, se debe realizar la unificación de Master sobre Development.

 - Release
 
Las ramas de release apoyan la preparación de nuevas versiones de producción. Para ellos se arreglan muchos errores menores y se preparan adecuadamente los metadatos. Se suelen originar de la rama develop y deben fusionarse en las ramas master y develop.
<br>
<br>

5. ### **Software que los usa como base**
<br>
<br>

Git se ha usado como software base sobre el que se han desarrollado otros proyectos

 - Gerrit. Aplicación web que permite la revisión de código en equipo para la aprobación o rechazo de modificaciones. Consiste de un repositorio Git que actúa como intermediario entre los gits de los desarrolladores y el repositorio Git que usa la integración continua. Los desarrolladores en lugar de enviar el código al sistema de integración continua lo envían al repositorio Gerrit donde se han establecido político.

 - Las plataformas de forja son plataformas web que ofrecen servicios que permiten el desarrollo colaborativo de software. Uno de los servicios básicos ofrecidos es poder crear repositorios de software en un sistema de control de versiones concreto. El sistema de control de versiones más utilizado es Git. Ejemplos de estos servicios son GitLab, Bitbucket y GitHub. Se han desarrollado varias soluciones que permiten crear automáticamente forjas software como por ejemplo Gogs, Gitea, RhodeCode Community Edition o las versiones de plataformas ofrecidas por GitHub (GitHub Enterprise), Gitlab (GitLab CE y GitLab EE) y Bitbucket.

 - SparkleShare. Es un cliente de código abierto que permite usar repositorios Git como servicios de alojamiento de archivos, permitiendo la sincronización de archivos y colaboración en la nube de forma similar a Dropbox. Los repositorios Git pueden estar en una máquina Linux, generalmente creados con la aplicación Dazzle [2] o en repositorios git alojados en la nube usando servicios como GitLab, GitHub, Bitbucket o NotABug [3].

 - git-crypt. Herramienta de git que permite hacer cifrado de forma completamente transparente. Cuando se hace un git push los ficheros marcados para cifrar se cifren automáticamenteno. Análogamente se hará cuando se hace un git pull. De esta forma podemos tener un repositorio que tenga parte de sus archivos cifrados y otra parte sin cifrar. El cifrado se puede realizar con claves de cifrado simétrico (con GPG) o asimétrico.

 - Herramientas, como gitflow [4], que facilitan la automatización de las tareas implicadas en cierto/s flujo/s de trabajo.

 