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





