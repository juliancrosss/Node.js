# Node.js

##Ejecucion

*Ejecutando Node.js en (CLI) command-line-interface*

    $ node
    
    >console.log("Hello, world!");
    Hello world
    >undefined
    
*Podemos ejecutar node.js desde un archivo en nuestro directorio de nuestro equipo*

        console.log(Hello, Wolrd!); //file.js
        
        $ node file.js
        Hello, Wolrd!
        
*Para salir de (CLI) command-line-interface Ctrl+D o Ctrl+C*

#Configurando y usar NODE PACKAGE MANAGER "npm"

*Podemos nosotros solamente llegar lejos usando las caracteristicas del lenguaje y functiones basicas. La mayoría de las plataformas de programación tienen un sistema que le permite descargar, instalar y administrar módulos de terceros. En Node, tenemos el Administrador paquetes Node Package Manager (NPM).*

*NPM son tres cosas. Un repositorio de paquetes de terceros, una manera para manegar paquetes instalados en nuestro computador, y un standard para definir dependencias en otros paquetes. NPM ofrece un servicio de registro público que contiene todos los paquetes que los programadores publican en npm. NPM también proporciona la linea de comandos "Terminal", para descargar, instalar y manejar estos paquetes. También puede utilizar el formato de descriptor de paquete estándar para especificar qué módulos de terceros su módulo o aplicación depende.*

*Usted no necesita saber acerca del npm para empezar a utilizar Node, pero será necesario una vez que usted desea utilizar módulos de terceros*

##Usando NPM para install, actualizar y densistalar paquetes

*NPM es un poderoso gestor de paquetes y se puede utilizar de muchas maneras. npm mantiene un repositorio centralizado de módulos públicos*

*NGP tiene dos modos principales de operación: globales y locales*

*Estos dos modos de cambiar de directorio de destino para almacenar los paquetes y tienen profundas implicaciones para la forma en carga módulos de Node*

*El modo local es el modo por defecto de funcionamiento en NPM. En este modo,NPM funciona en el nivel de directorio local, nunca hace cambios en todo el sistema*

*El modo global es más adecuado para la instalación de módulos que siempre deben estar disponibles a nivel mundial, como los que proporcionan utilidades de línea de comandos y que no sean utilizados directamente por las aplicaciones.*

##El modo Global

*Si instaló Node usando el directorio por defecto, mientras que en el modo global,npm instala los paquetes en /usr/local/lib/node_modules.*

        /usr/local/ lib/node_modules/sax:
        $ npm install -g sax
        
##El modo local 

*El local modo es por defecto  funcionamiento en NPM y el recomendado en el mecanismo de resolucion de dependencias.En este modo NPM instala todo dentro del directorio actual*

        /home/user/apps/my_app, NPM usara /home/user/apps/my_app/node_modules
        
##Instalando un Modulo

*Use el siguiente comando, puede descargar e instalar la ultima version del paquete.*

        $ npm install <package name>

*Ejemplo*

        $ npm install sax
        //Podemos especificar la version del modulo a instalar
        $ npm install <package name>@<version spec>
        $ npm install sax@0.2.5
        
##Desinstalando Modulos

*La siguiente linea de comando NPM  trata para buscar y desinstalar el paquete*

        $ npm uninstall <package name>
        //Eliminar globalmente un paquete
        $ npm uninstall -g <package name>

##Actualizando un paquete

*Podemos actualizar un paquete de la siguiente manera*

        $ npm update <package name>
        //Global
        $ npm update –g <package name>

#Usando Archivos Ejecutables

*es posible que un módulo incluye uno o más les ejecutable. NPM instala archivos ejecutables dentro de /usr/local/bin. este PATh es el defeult para la ejecucion de archivos binarios*

*Si usted instalo un paquete localmente, NPM instala cualquier ejecutable dentro de ./node_modules/.bin directorio*

##Resolviendo Dependencias

*NPM no solo instala los paquetes que usted requiere tambien instala los paquetes que esos paquetes dependen de el, por ejemplo si usted solicita instalar un paquete A y este paquete depende en B y C. Node extraera los paquetes B y C y los instalara dentro
./node_modules/A/ node_modules.*

Por ejemplo si usted localmente instalo el paquete nano

        $ npm install nano
        
Salida de NPM

        nano@0.9.3 ./node_modules/nano
        ├── underscore@1.1.7
        └── request@2.1.1
        
*Esto muestra que el paquete nano depende  en underscore y request paquetes e indica cual version de estos paquetes fueron instalados. Si usted observa dentro del directorio ./node_modules/nano/ node_modules , usted vera estos paquetes instalados*

        $ ls node_modules/nano/node_modules 
        request underscore
        
#Usando package.json para definir dependencias

*Cuando creamos un Node aplicacion, podemos tambien incluir un archivo packege.json en el root. el archivo package.json es donde podemos definir algo de metadata en la aplicacion. tal como nombre, autores, repositorios, contactos, y asi. Este tambien donde deberiamos especificar extrañas dependencias.*

*Ejemplo*

        
       {
         "name" : "MyApp",
         "version" : "1.0.0",
         "dependencies" : {
           "sax" : "0.3.x",
           "nano" : "*",
           "request" : ">0.2.0"
         }
        }
        
*Despues en root de la aplicacion, escribimos:*

        $ npm install
        
*NPM analizara las dependencias y el node_modules y automaticamente descargara e instalara cualquier paquete faltante.*

*Podemos actualizar localmente paquetes instalados*

        $ npm update

*Resumen*

* instalacion de Node
* instalacion y uso de Node Package Manager
* usar npm para instalar, desinstalar paquetes de terceros
* podemos usar package.json junto con npm para manegar paquetes de terceros o dependencias
* 

#Introduccion a Node

*Programación dirigida por eventos es un estilo de programación por lo que el flujo de ejecución está determinada por los eventos. Eventos son manegadores por controladores de eventos o callback eventos. Un Evento callback es una funccion que es invocado cuando algo significante sucede- tal como cuando el resultado de un query de una  base de datos es disponible o cuando el usuario clickea un boton.*

*Considere como un query a una base de datos es completada en tipica programacion de  I/O.*

        result = query('SELECT * FROM posts WHERE id = 1');
        do_something_with(result);
        
*Este query requiere que el actual hilo o proceso espere hasta la base de datos finialice el proceso.*

*en un Event-Driven system, este query deberia realizarse de esta manera:*

        query_finished = function(result){
            do_something_with(result);
        }
        query('SELECT * FROM posts WHERE id = 1', query_finished);
        
*Aqui estamos definiendo que sucedera cuando el query es finalizado y almacenando en esa funccion llamada query_finished. Entonces estamos pasando esa funccion como un argumento a la query. Cuando finaliza , la consulta involcara a la funcion  query_finished, en lugar de un simple retruno de resultado*

*Este estilo de programacion, por lo cual en lugar de usar un valor de retorno definimos funciones que son llamadas por el sistema cuando un interesante evento ocurre- es llamado event-driven o asynchronous programming "programacion asincronica". Esta es una de la definiciones de las carateristicas de Node. Este estilo de programacion significa el proceso actual no bloqueara cuando este haciendo un I/O operaciones. Sin embargo, varias I/O operaciones pueden ocurrir en paralelo. y cada respectivo callback function sera invocada cuando la operacion finalice.*

*El event-driven programming estilo esta acompañado por un event loop. un event loop es una contruccion que principalmente realiza dos funcciones en un continuo loop-event detection y event handler triggering, el event loop debe determinar el evento callback y invocarlo.*

*Este Event loop es justo un hilo ejecutandose dentro de un proceso, el cual significa que cuando un event sucede, el event handler puede ejecutarse sin interrupion. esto significa lo siguiente:*

* Hay al menos un event handler ejecutandose en un momento dado.
* cualquier event handler se ejecutara para la terminacion sin comenzado una interupcion
* 

*Esto permite a los programadores para relajarse el sincronico requerimientos y no tener que preocuparse sobre los concurrentes hilos de ejecucion cambiando para compartir el estado de memoria*



