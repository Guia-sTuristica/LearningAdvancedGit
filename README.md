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
    git reset --hard es paracido git checkout -- .
    gut restore --stage file => sacerlo eliminado del stage



## git mv, Cambiar el nombre  y eliminar archivo mediante git
    git mv "nombredelarchivoactual" "nombrenuevo" =>Cambio de nombre    y nos aparece una R, realizando git status tenemos el rename
    ya esta el cambio ahora realizamos un git commit -m "comentario"
    git rm nombredelarchivo=> Eliminar archivo aun si hacemos un git status todavia aparece esta en el staged y realizamos un commit

## git mv, Cambiar el nombre  y eliminar archivo fuera de git
    cuando cambiamos el nombre de un archivo fuera de git (fuera de los comando por consola), git no le dara seguimiento de este archivo
    aparece un U, para git se creo un nuevo archivo el anterio desaperecio vemos informacion de un git status
    D historia/superman.historia.md => tengo una eliminado de un archivo es peligroso si tenemos informacion es importante por que perdemos 
    todas las historias de cambios de este archivo
    ?? historia/superman.md => nuevo archivo
    podemos dar un git add . => y nos informacion que el archivo original lo tiene el nuevo archivo d enombre cambiado solo si aparece una R
    si hacemos un git reset --hard "hash" nos recuperar el ultimo cambio de nombre
    Eliminamos un archivo  => se elimina el archivo

## Ignorando arhivo que nos deseamos
    .gitignore => esta en la raiz del proyecto especifiamos los directorio que no le de seguimiento

## Ramas Uniones Merge y Conflictos
    las ramas nos ayudan si queremos poner nuevas funcionalidas o puede ser descartado es una linea de tiempo aparte
    Merge => 3 posibles escenearios fast-foward, qu se dispara cuando git detecta cuando en la rama principal no hay cambios
    Uniones automaticas => git detecta que en la rama principal, que la rama secunda desconece, git detecta si no hay conflictos y lo agrega 
    Merge Manual => git no puede resolver de forma automatica y lo hace manual y cuando resuelva ese conflicto git crea un commit nuevo

### MERGE FAST-FORWARD
    git branch "nombre de rama" =>crea una nueva rama cuando 
    git branch => nos indica la rama donde estamos 
    git checkout "nombre de rama" => se mueve a la rama indicada    
    git merge 
       Para unir la ramas tenemos que estar parado en la rama para traaer los cambios de la otra rama en este caso
        git branch main luego => git merge y se ejecuta Fast-forward
        git logro identificar todos los cambios
        
        apunta a la rama main y villanos
             villanos.md  Flash reverso - RobertFox (HEAD -> main, rama-villanos)
        La rama existira aun
        es conveniento que  la borremos
        git branch -d rama-villanos
        git branch -d rama-villanos -f => de maneraa forzada eliminamos la rama por que los commit no se van a pasar a la rama principal

### MERGE AUTOMATICAS
    git checkout -b rama-villanos => crea la rama y nos movemos a la rama
        realiamoz modificacion de la bio de superman ahora comiteamos, estos commit se encuentra en la rrama villanos
    y no forma de la rama main
    * 7c61b5b - (39 seconds ago) Borramos datos que no necesitamos de superman - RobertFox (HEAD -> main)
    | * cf1141b - (5 minutes ago) Notas en villanos - RobertFox (rama-villanos)
    | * e47f613 - (5 minutes ago) agregamos a doomsday - RobertFox
    |/
    unimos la rama al master tenemos que estar en l rama en la cual espera los cambios de otra rama 

### MERGE: uniones con conflictos
    Cuando git no puede hacar de manera automatica el fast-forward y se han hecho modificacion en la misma linea
    menseaje de conflicto=>CONFLICT (content): Merge conflict
    nos indica que ha aparecido un conflicto y hay que comitear el resultado 
    tenemos que elegir que cambio necesitamos 
    al puls git s vemos que tnemo UU y tenemos que resolver este conflicto con git commit -am ""
    una vez comiteado resolvemos este conflicto

## TAGS , etiquetas
     Son usados para marcar versiones referencia de un commite a un estado el proyecto en ese punto especificos o realese o aplicativo de nuestro programas puede ser palabras o numeros
    git tag nombredeltag ?> creamos un tag
    git tag -d nombredeltag ?> elimina el tag
    git tag -a v1.0.0  -m "version 1.0.0 lista" => creamos la version crea el tag del ulti mo commit
        v1=> version mayor cambios de version , 0 => version menor cierta funcionalidad => 0 => tipo de bug que tiene que ser resuelte

    como poner un tag a un commit especifico => git tag -a v0.1.0 hashquequermosdelcommit -m "Version alpha, 
    git show v0.1.0 => si queremos ver mas informacion de un tag en especifico

## STASH 
     el proceso que toma el estado desordenado de nuestro directorio de trabajo y lo almacena en una pila de cambios incompletos que podemos volver a aplicar más adelante. Podemos crear, actualizar o eliminar los cambios temporales personalizados
     Si queremos guardar nuestro trabajo incompleto sin comprometerlos, usaremos el comando=> git stash
     git stash list
        muestra todos los stats

    git stash pop
    podemos restablecer los cambios guardados simplemente usando el siguiente comando:
    si queremos ver nuestro git log 
    nos muestra todos los commits pero no muestra el statsh porque ya lo tengo volcado
    y podemos hacer nuestro commit
