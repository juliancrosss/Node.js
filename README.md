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
