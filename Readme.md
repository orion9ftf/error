### Errores y soluciones:

***Error rvm***

```shell
Error running '__rvm_make -j8',
please read /Users/usuario/.rvm/log/1648737556_ruby-2.5.3/make.log

There has been an error while running make. Halting the installation.
```


Solución:

```shell
$ export warnflags=-Wno-error=implicit-function-declaration

$ rvm install 2.5.3
```

Solución problema:

rvm problem

```
$ rvm use 3.0.0

RVM is not a function, selecting rubies with 'rvm use ...' will not work.

You need to change your terminal emulator preferences to allow login shell.
Sometimes it is required to use `/bin/bash --login` as the command.
Please visit https://rvm.io/integration/gnome-terminal/ for an example.
```

Solutions: 

```shell
$ source $HOME/.rvm/scripts/rvm
$ rvm use 3.0.0
```


```shell
Running: __rvm_make -j8
```

```shell
$ RUBY_CONFIGURE_OPTS="--disable-dtrace" rvm install 2.6.8
```

***Instalar rails***

```shell
$ brew install shared-mime-info
```


Al dar el comando de arriba aparece esto: 
****

A CA file has been bootstrapped using certificates from the system
keychain. To add additional certificates, place .pem files in
  /opt/homebrew/etc/openssl@3/certs

and run
  /opt/homebrew/opt/openssl@3/bin/c_rehash

openssl@3 is keg-only, which means it was not symlinked into /opt/homebrew,
because macOS provides LibreSSL.

If you need to have openssl@3 first in your PATH, run:
  echo 'export PATH="/opt/homebrew/opt/openssl@3/bin:$PATH"' >> ~/.zshrc

For compilers to find openssl@3 you may need to set:
  export LDFLAGS="-L/opt/homebrew/opt/openssl@3/lib"
  export CPPFLAGS="-I/opt/homebrew/opt/openssl@3/include"

For pkg-config to find openssl@3 you may need to set:
  export PKG_CONFIG_PATH="/opt/homebrew/opt/openssl@3/lib/pkgconfig"
****

Luego 

```shell
$ gem install rails -v 6.0.0
```



**********************************************************************

***Listar rails***

```shell
$ gem list | grep rails
```


***Instalar Rails***

```shell
$ gem install rails -v5.2.3
```

*******************************************************************************

### Variables de Entorno Linux - MacOS

> Quedan almacenadas en el equipo.

> En nuestro proyecto solo llamamos una referencia a esa variable.

> Son variables globales del sistema operativo y las podemos utilizar con cualquier aplicación que se use desde el terminal (ejemplo: rails s)

***¿Cómo se define una variable de entorno?***

```shell
export  NOMBRE_VARIABLE=VALOR_VARIABLE
```

***Otras opciones:***

Ejemplos:

1.- .env (debemos crear un archivo llamado .env, y este pasarlo a .gitignore para que al momento de subir el proyecto a un repositorio, ignore ese archivo y lo que contiene dentro).

2.- .gitignore

```
#Ignore bundler config.
/ .bundle

#Ignore the default SWLite database.
/db/*.sqlite3
```

Mostrar los archivos ocultos: `$ ls -a`
 
O listar los archivos ocultos con `$ ls -la`

Archivos ocultos que podemos utilizar (se cargan junto con la terminal al ser utilizada, ya que utiliza ciertas dependencias del sistema):

***Linux:***

```shell
.bashrc
.profile
```

***Mac:***

```shell
.bash_profile (recomendada)
.bashrc
```

***¿Cómo abrir un archivo oculto?***

***Linux:***

```shell
$ nano .profile
$ code .profile
```

1.- Crear la variable de entorno en uno de los archivos ocultos ya mencionados.

2.- Cargar las variables en la terminal.
 
- Primero cerrar esa terminal, para que se carguen en una nueva sesión. Y abrir un nuevo terminal para que estén disponibles.
 
- Comprobar si se encuentra disponible: 
 
`$ printenv PASSWORD_KEY`

* Esto debiera retornar el valor de la variable

* Otra manera de hacerlo, es recargar el archivo .profile con $ source .profile

Cada vez que abramos un terminal es una sesión diferente.

Quedan guardadas en los archivos disponibles del terminal (o levantar un servidor).

> En mi código debo llamar a esa variable:

En Rails se llama con la palabra reservada `ENV[]`, que viene del archivo environments .

***Ejemplo:*** tengo un usuario y su password:

```rb
Config.omniauth :facebook, ENV[‘USER_CLIENT’], ENV[‘PASSWORD_KEY’]
```

> Cuando se levante nuevamente el servidor, va a ir a buscar en el entorno donde se está ejecutando el servidor.


### Para que nuestras credenciales funcionen en entorno de Producción y no solo en entorno de Desarrollo, podemos setear esas credenciales y pasarelas a Heroku.

> A Heroku le podemos preguntar por una variable y obtener su valor con:

```shell
$ heroku config:get NOMBRE_DE_LA_VARIABLE
```

O sestear una variable con:

```shell
$ heroku config:set CLIENT_KEY=cbcbudssjsisnxn6447bysyx
```

***Ver las variables en Heroku:***

1.- Heroku

2.- Settings

3.- Config Vars | Reveal Config Vars

4.- También se pueden sestear desde Heroku, pero es mejor hacerlo en la terminal.


***Linux:***
```shell
nano .profile
source .profile
printenv CLIENT
```

Llamar a todas las variables de entorno que comiencen con un nombre en particular:
 
Primero cargar el archivo con `$ source .profile`

Y luego `$ printenv | grep CLIENT`

***MacOS:***

```shell
nano .bash_profile
source .bash_profile
printenv CLIENT_KEY
```

Llamar a todas las variables de entorno que comiencen con un nombre en particular:
 
Primero cargar el archivo con `$ source .bash_profile`
Y luego `$ printenv | grep CLIENT`



****************************************************************************************

### Editar navegador por defecto en VSCODE:

1.- Preferencias

2.- Configuración

3.- Extensiones

4.- Live Server config

5.- Editar en settings.json
 
> tiene que quedar así:

```json
{
    "workbench.iconTheme": "material-icon-theme",
    "liveServer.settings.CustomBrowser": "chrome",
    "liveServer.settings.donotShowInfoMsg": true,
    "security.workspace.trust.untrustedFiles": "open",
    "[html]": {
        "editor.defaultFormatter": "esbenp.prettier-vscode"
    },
    "window.zoomLevel": 1
}
```


******************************************************************************************

### INSTALAR BREW:

1.- $ echo 'eval $(/opt/homebrew/bin/brew shellenv)' >> /Users/“user”/.zprofile

2.- eval $(/opt/homebrew/bin/brew shellenv)

3.- brew help


### Heroku install:
$ brew tap heroku/brew && brew install heroku


### Rails:

```shell
$ rails routes —expanded
$  rails db:migration create_articles
```

```rb
t.string :title
t.text :description
```

```shell
errors:
> articles.errors.full_messages
```
*****************************************************

### Font-size

1em = 16px
40px / 16 (1em) = 2.5em

Viewport es el tamaño de la ventana del navegador. 1vw = 1% del ancho de la ventana gráfica. Si la ventana gráfica tiene 50 cm de ancho, 1vw es 0,5 cm.

Background-image options:

```
1.- background-image: url(“imagen.png”);
2.- background-image: url(./assets/img/imagen.png);
3.- background-image: url(https://www…etc);
4.- background-image: url(assets/img/imagen.png);
5.- background-image: url(imagen.png);
6.- background-image: url(“/assets/img/imagen.png”);
```



Copiar la ssh.pub de windows: clip < ~/.ssh/id_rsa.pub
Copiar la ssh en Mac pbcopy < ~/.ssh/id_rsa.pub
Copiar la ssh en linux(primero descargar una pequeña app que nos ayuda a copiar la ssh): sudo apt install xclip | luego copia este comando, ayuda a copiar la ssh para pegarla en el repositorio GitHub: xclip -sel clip < ~/.ssh/id_rsa.pub




