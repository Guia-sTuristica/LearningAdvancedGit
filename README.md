## Git Intro
    en git si viene con dos menos viene una palabra completa
    git --version
    git --help => nos da la ayuda de los comandos
    git config --global user.email => configuraciones de git
    git config --global user.name => configuraciones de git para el repositorio
    git config --global -e => si queremos corregir la configuracion

## Git Add, status, reset
    git add . => añade todos los cambios
    git add text.x => solo añade el cambio del archivo text.x
    git add js/*.js => se añade la carpeta js con todos los archivo con extension js
    git status => informa el estado del repositorio, si esta en verde por que se han 
    aceptado con el add, si estan en rojo por que no estan añadido
    git status --short => hace un resumen muy condesado del status
    git reset nombreArchivo.x =>ese archivo no es parte del estado
    git commit -m "texto de lo comprometido=>nos mostrar los archivo que estan comprometido
    git commit -am => añade los cambios y pone el comentario comprometido

## git log
    git log => nos muestra lo que se ha comiteado con id de cada commitq
    git log --oneline => nos muestra la forma corta del commit
    git log --oneline --decorate --all --graph =>
    git config core.autocrlf true => es básicamente una interpretación de un carácter.

## GIT Recuperar cambios
    cuando no se puede realizar ctrl + z
    git checkout -- . =>le dice a git reconstruye el proyecto como estaba hecho el ultimo commmit con cambios 
    si se eliminaria alguna carpeta tambien lo construye, si se crea un nuevo archivo este comando no quitas
    ese cambio

## GIT Branch      
    git branch => nos dice que rama estamos trabajando es el lugar de estar trabajando, al realizarlo
        nos muestra donde nos ubicamos con un asterisco
    git branch -m master main =>cambiar el nombre de la rama, el incoveniente   no se esta pactando de manera global
    de nuevos repositorio que si queremos iniciliar 
    git config --global init.defaultBranch main => con esto cambiamos de manera global que se inicia el git
    git config --global -e => lo podemos comprobar y tambien podemos editar variables o alias
    

## .gitkeep
    nos dice que mantenga esta carpeta, tenemos añadire la carpeta uploadas
    si queremos un directorio vacio no lo añade, tan solo si se añade archivo,
    el directorio uploads, es importante cuando el usuario añade archivo si no existe

## Alias
    git config --global alias.s "status --short"  => va hacer un status  --short ejecutamos git s
    creamos un alias de git log
    git config --global alias.lg "log --graph --abbrev-commit --decorate --format=format:'%C(bold blue)%h%C(reset) - %C(bold green)(%ar)%C(reset) %C(white)%s%C(reset) %C(dim white)- %an%C(reset)%C(bold yellow)%d%C(reset)' --all"

## Comprobacion como estaba antes y como esta ahora
    git diff=> diff --git a/README.md b/README.md, nos indica con el que es la version anterior y b es la version actual
    cuanto viene en "+" son los que estan pendiente de añadir, si lo agregan no va aparecer la diferencia por que esta agregado
    esta comparando los cambios que no esta en el staged
    git diff --staged =>
## Actualizar mensaje del commit y revertir commits, git reset 
    git commit --amend -m "Mensaje actualizado" => esto se cambia para el ultimo commit
    git commit --amend=> podemos hacer muchos cambios y podemos cambiar el texto del commit
    git reset --soft HEAD^ "Mensaje actualizado" => Modficacion que sea parte del ultimo commit, podemos poner commit anteriore
    "HEAD^4", podemo ver el commit git log y vemo que el ultimo comit no esta y podemos añadir los datos que si queremos, hay que tener 
    cuidado mejor que hagan el amend para modficar 
    git reset --soft "hash del git" => vemos lamodficiacion que hay lo sacaquemos del staged y modemos hacer el nuevo commit y almacenar los cambios
    git reset --mixed "hash del git"=>saca todo del staged y locambios listo para volver añadir, nos aparece U untrack, no teenomos los comit subsiguientes
    si pone git reset -- => seria mixed por defecto
    git reset --hard "hash" => es destructivo va dejar como estaba antes del punto y acide sucesivamente 
    si esto ocurre por error esta es la soluccion git no pierde nada
    git reflog => vemostodos los commit cada una de staos hast son todas la modificaicones
    git reset --hard "hash" => regresar el commit donde nos intersa y se reconstruye todo el proyecto



## Cambiar el nombre  y eliminar archivo