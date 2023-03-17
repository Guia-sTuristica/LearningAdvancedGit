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
    si vemos en nuestra cabecera => (HEAD -> main) es nuestro local
    (origin/main) => es nustro repositorio remoto puede de estar adelante o atras
    (origin/main) si esta atras y nuestro (Head -> main) adeltnte nostros estamos adelantado
    si fuera alrevez nuestro repositorio esta adelanto y nuestro local atrasado

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
    `git config --global alias.lg "log --graph --abbrev-commit --decorate --format=format:'%C(bold blue)%h%C(reset)
    - %C(bold green)(%ar)%C(reset) %C(white)%s%C(reset) %C(dim white)- %an%C(reset)%C(bold yellow)%d%C(reset)' --all"`

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
    podemos restablecer los cambios guardados y borra el stash simplemente usando el siguiente comando:
    si queremos ver nuestro git log 
    nos muestra todos los commits pero no muestra el stash porque ya lo tengo volcado
    y podemos hacer nuestro commit
    Si queremos mantener esos cambios en el alijo, en lugar de usar git stash pop
    borrando el git stash => git stash clear
    Si queremos mantener esos cambios en el alijo, en lugar de usar git stash pop, usaremos git stash apply
    y podemos hacer nuestro commit y el stash ya desaparece
    toda la informacion que tenemos los stash => git stash list --stat
     gitsi ya no necesitamos ese alijo que realizamos, lo eliminamos con el siguiente comando especificado con la identificación del alijo, y lo eliminará del área de almacenamiento. El comando para eliminar el alijo en particular es el siguiente:
    => git stash drop <stash_id>
    ver informacion de un stash => git stash show <stash_id>
    git stash save "nombre del stash" => guardamos un stash con un nombre
    stash@{0} => el ultimio que se añadio en el stah
    recuperar el stash respectivo
    git stash apply stash@{2}

## REBASE
    Sirve para ordenar commits
    corregir commits
    unir commits
    separar commits
    debes estar en la rama secundaria q
    git rebase main=> loq ue realizara que los commit que tnemos en la rama secundaria se posicionara en los ultimos
    sin perderse ningun cambio
    lugo podemos situarnos en la rama main realizamos un merge y nos dara un fast forward
### REBASE SQUASH
    el rebase iteractiva consejo debe ser en el local, aun cuando no se hace push 
    git rebase -i HEAD => hace referencia al ultimo commit 
    git rebase -i HEAD~2 => hace referencia la cantidade commit que nos puede interesar
        squash => es tomar dos cosas y se fucionen juntas una ves dentro viendo los commit que necesitamos por el rebase
            utilizamos "s" hashid  y el anterio ponemos "p" quitando los valore que se llaman pick
            luego nos movera otra pantalla nos dira que un commit de dos comits y nos informa si quermeos que se llama el nombre
            de commit que nos interesa y guardamos
            example llegara haci=> git rebase -i HEAD~2:
            pick 0962319 añadiendo informacion de rebase
            pick 0631cab info rebase
            solucion cogemos solo dos la p y s
            p 0962319 añadiendo informacion de rebase
            s b5d840f info rebase
    debes estar en la rama secundaria 
    git rebase main=> loq ue realizara que los commit que tnemos en la rama secundaria se posicionara en los ultimos
    sin perderse ningun cambio
    lugo podemos situarnos en la rama main realizamos un merge y nos dara un fast forward

## REBASE REWORD
    Actualiza los nombres de los commits que queremaos entramos a al rebase interactivo y cogemos los ultimos
	git rebase -i HEAD~2
	example añadimos la r
	r 0962319 añadiendo informacion de rebase
	r a5c3203 info rebase

	luego nos muestra una pantalla en la cual podmeos cambiar el nombre del commit y lo cambiamos

## REBASE EDIT
    podemos hacer commit diferentes por archivos
    revertir los cambios solo por archivos
	git checkout -- README.md

   si hacemos commit de dos archivo y nos damos cuenta que queremos separar los archivo 
    por distintos commit hacemos lo siguiente
    puede ser un rebase iteractivo mostranod la cantidad de commit
    git rebase -i HEAD~3
    Ppoenemos el caracte e o edit

    nos muestra una un rebase manual
    git status, nos muestra ahora un rebase iterativo
    hacemos un git reset del ultimo commit => git reset HEAD^
    nos baja del stage de los dos archivo modificacods
    ahora si podemos añadir el archivo que queramos
    git add  nombre de arhivo
    hacemos el commit

    y luego agregamos el archiov que queremos 

    hacer un git lg vemos que el main esta debajo del git head
    por que aun estamos en el rebase iteractivo
    ejecutamos para que termine el rebase iteractivo => git rebase  --continue 
## PUSH TAGS
    subir los tags => git push --tags
    releases y tagas=> diferencia 
    git push -u origin => cuando hacemos otra vez git push ya no no es necesario por que
    lo estamos guardando
    git remote -v => nos indica el origen del git


## WARNING -PULLING WITHOUT  RECONCILE STRATEGY
  `Nos indica que estrategia va aplicar a la hora de unir nuestro repositorios en remoto y local 
  git config --global pull.rebase false solo usa el # merge
  vgit config --global pull.rebase true solo usa el # rebase
  git config --global pull.ff only solo usa el # fast-forward only, normalmente se usa 
  `
  git config --global pull.ff only => lo usamos
  comprobacion del commit

## GIT PULL REBASE
   git config pull.rebase true => es una configuracion de manera global cuando tenemos 
	conflicto y podemos resolverlo
   al hacer un git pull nos indica que estamos en un git pull rebase
   si hacemos un git branch
   si nos encontramos con estamos en medio de un rebase tenemos que terminarlo antes 
	 de hacer cualquier tipo de trabajo
   *(no branch, rabasing main)
   si hay conflicto elegimos y guardamos los cambios
	hacemos un nuevo commit
	realizamos un git status vamos a ver estamose n un git rebase interactivo
	vemos que ya lo tenemos en el stage con el commit realizad
	git commit --amed => podemos abortar los cambios
	git rebase  --continue => se actualiza de manera exitosa
	realizamos hasta git push => se hace la uniont

	hacemos git pull si da un erro realizar un nuevo commit



## GIT PUSH [REJECTED]
     cuando el push da fallo	
	nos dice que fue rechazado porque hay una referencia este repositotiro remoto que no tenemos
	de manera local	.
	nos pide que hagamos git pull antes de hacer pushing

    ! [rejected]        main -> main (fetch first)
    error: failed to push some refs to 'https://github.com/robertfox11/LearningAdvancedGit.git'
    hint: Updates were rejected because the remote contains work that you do
    hint: not have locally. This is usually caused by another repository pushing
    hint: to the same ref. You may want to first integrate the remote changes
    hint: (e.g., 'git pull ...') before pushing again.
    hint: See the 'Note about fast-forwards' in 'git push --help' for details.

	hacemos un git pull

	si hay conflictos, lo solucionamos y vemos que podemos elegitr una vez elegido
	realizamos un commit 
	realizamo ahora un push 
    
## INTERFAZ DE GIT HUB
  Podemos tomar todo el proyecto con FORK => 	HACE UNA COPIA O CLONE COMPLETO A MI CUENTA DE GITHUB
  LA estrella  => se marca de favorito
  pestaña de watch => pendiente de novedades y commit nuevo a al repositorio que estamos viendo o seguimiento d eun proyecto 
  Code=> tenemos el codigo
  en el branch=> vemos las versiones  o ramas creada que se utilizar en react
  issues => Es problemas o sugerencia cualquier pregunta que podemos realizar
  Pullrequest => revisa el codigo cambio de un repositorio que no nos pertenece	
  Actions=> cuando algo sucede en el repositorio puede de ser un deploy proceso automaticas mediantes acciones procesos automaticos
  Projects => manejar projecto suficientemente maduro para salir a produccion
  Wiki => propia documentacion del proyecto documentacion oficial para que puedan ver el usuario final
  Security => cuantas personas puede utilizar el proyecto de securit
  Insights => ayuda a la gente para saber cuanto esta trabajando en el proyecto, ver muchas estadisticas de commits la frecuencia   comunidad cuantas veces sea push 

## **ISSUES**  
    Creacion de preguntas 
    Creacion de vesrion checkeado
    - [x] v1
    - [ ] v2
   **_Buscando un archivo Github_**
   en la funcionalidad **GoToFile** => busca archivos , tambien e **GoToLine** va a la linea del archivo
   **Copy path** => copia el path del archivo ("ruta")
   **Copy permalink** => llegamos ala version archivo en este punto del tiempo

## Raw, blames, history
    raw => nos muestra el archivo de texto
    Blame => nos dice los cambio que ha sufrido desde la creacion y quien lo ha modificado
    history => nos muestra el historial
## **Creando un nuevo archivo en Git hub**
    pull request=> es una rama que se desprendio en un punto del tiempo de la rama principal
    para unir la rama, nos sirve hacer un analisis previo antes de hacer un merge, tiene que ser revisada por 
    alguien antes de unirla al main, tiene que cumplir el standard de calidad antes de hacer el merge
    creamos un nuevo archivo y proponer un nuevo archivo, dice proponer por que puede ser rechazada
    una vez que hemos puesto nuestro comentario damos al boton pullrequest
    podemos comentar o puede comentar el que tiene mas conocimiento del proyecto pude recharzar o tambien comentar
    para juntarlo tenemos que hacer un merge commit 
    **_Squash_** =>voy a tomar estos cambio y lo fusinare con el ultimo commit realizado 
    **Create Merge pull request** =>   commit adicional que se hace una adicion, podemos borrar esta rama si no la necesitamos

## **git fetch**
    Actualizar la referencia en mi repsoitorio local del remoto ahora apunta al main
    El head main estar apuntando a otro commit 
    podemos hacer un git pull
    En git hub podemo poner comentarios e

## Fork, Clone y Colaboraciones
    Repositorio publico no somo colaboradores podemos hacer git clone sin ningun problema, pero no podemos hacer push 
    ¿Pero como queremos colaborar?
    Entra el concepto de un Fork, tomar el respositorio original y tener acceso el respositorio, es como una rama adicional
    puede ser unida ahi entra el pull request y asi podemos contribuir
    Damos a click en fork y luego aparece nuestro perfil para asi poder clonarlo
    copiamos el git y lo clonamos en nuestra carpeta que queramos
    un git clone "repositorio" y vemos con un git log
    y ya esta lo tenemos

## **GIT PULL Request**
    Una vez que tengamos el repositorio podemos modificar algun archivo y darle commit
    una vez hecho vamos a darle un boton donde dice Contribute, aparece un boton "Open pull Request"
    en git hub nos da informacion donde podemos realizar el pull request podemos darle un commentario
    y creamos el pull request 
    Ahora ya no podemos continuar por que el otro usuario tiene que aceptar o rechazar el pull
    request
    El administrador del repositor y puede comentar sobre estos cambio al que realizo el pull request
    y puede tambien resolve esta conversacion si se le ha comentado
    **_Squash an merger_** para aceptar los cambios en filechanged en este boton podemos ver los cambios
    y en el boton reviewChanges podemos revertir los cambios endamos a request_change

## Vemos todas las ramas
    git branch -a
    eliminamos ramas => primero estamos en el main o nuestra rama
    git remote prune origin => revisa la ramas del remoto que no existe, y las limpia si la rama 
    ya es unidad hay que borrarla
    git branch => vemos de  manera local => git branch -d "rama"
    ACtualizar la rama de manera local tambien borrar la rama del respositorio
    git push origin:"rama" => eliminamos la rama de manera remota
    podemos crear una rama apartir de una version en github

## Milestone & ISSUES & COLABORADORES   
    Issues, Para comentar y comunicarse por el miembro de trabajo o realizar preguntas
    Para que reconozca github y responde r aun issues  por el commit 
    es  => "Fixes "el numero del issues" #numero y lo cierra el issues github
    Issues Templates, Reportar bug, un feature,custom template, seguimiento en damos en el boton propose y creamos
    luego al crear un issues nos da  la option el reportar bug que hemos definido , nos un template de codigo 
    Tambien podemos crear un template personalizados en custom templates    
    **Labels** => en issues, tenemos muchas etiquetas personalizables, para que sirve
    Cramos un nuevo issues y en labels tomamos la etiqueta que queremos  y en nuestro issues tenemos la etiquetas
    Añadir automaticamente un labels => antes de darle a propose editamos el template y asignamos un label y aquin se lo asiganmos
    Milestone, es un agrupador de issues "https://docs.github.com/en/issues/tracking-your-work-with-issues/about-issues"
    podemos poner la fecha para que se cumpla la fecha contenido 
    Colaboradores => en managge access, agregamos la  el nombre de git que necesitamos para que colabore con nosotros el puede acceder atodos, podemos tambien eliminar el colaborador, si quiere que se nuevo dueño de este repositorio 
    en configuraciones => tranferir repository poenemos el nuevo nombre  y el ombre del repositorio

  
## WiKi
    Sirve Cuando necesiten que el proyecto un proceso de instalacion o documentacion oficial de nuestro repositorio
    con stilos de mardow con los estilos que nos da github, tambien podemos crear paginas
    con enlaces que nos lleva a esa pagina en el boton de enlace podemos especificar el texto y la pagina que se creo
    anteriormente
    Podemos realizar una navegacion con todos los enlaces que podemos en nuestro navegador

## Proyectos en GITHUB
    Es un administrado de proyectos
    hay dos formas de verlo board de forma tradicional tambien con jira de forma tradicional
    tambien esta table 
    tareas qeu tambien son issues, asignar persona para asiganr trabajo esta vez seleccionamos board
    en tabla  o boarda podemos crear estas opciones
        En title => podemos poner el nombre del proyecto, podemos hacer clic en el enlace y hacer un issues, seleccionamos
        el proyecto para cual crear el issues, estan enlazado con un respositorio
        assignees => a quien vamos asignar la tarea
        status => el estado de la tarea, tambien se puede personalizar los estados en editar campos
        en "+" => Podemos crear una nueva columna para poder tambien revisar los commit el pull request  con las columnas 
        creadas
    
    En el projects podemos crear un link asignamos el project y va aparecer las opciones tambien tiene otros beneficios
    como asignar issues o issues ya creados

## GITHUB PAGES
    Es un hosting gratuito de github=> tiene html, css, javascript
    Hay para nuestro proyecto y tambhien para usuario
    => esta es la ruta web por perfil de github=> https://robertfox11.github.io/ "aun no hay pagina"
    Creamos un sitio web personaklizados =>
    **Creacion de sitio web** => creamos un repositorio llamado => robertfox11.github.io
    ahora vamos a settings buscamos la opcion pages, elegimos el sources
    **Para tu proyecto**
    Una carpeta especifica para desplegar github pages => creamos una rama web
    el directorio se llama docs => es un nombr especial tiene archivo css, js, html 
    mergeamos a la rama nueva
    vamos settings => para que la carpeta sea un sitio web no hay que seleccionar un temaa podemos seleccionar la rama que queramos
    nos va decir que folder neesitamos para desplegar en el web docs es utilziado para este tipo de despliegue

## Insights
    Informacion estadisticas, trafico de red, ver cambios de rama, fork quienes a realizado, etc

## Organizacion y Equipos
    Es una forma agrupada de compartir el trabajo, puede ver el repositorio de distintos proyectos
    En el boton de "+" a lado del perfil podemo crear organizacion 
    En esta parte hay 3 opciones a elegir free, team, enterprise
    creamos el nombre de la organizacion => esto crea un repositorio de un url en particular
    completamos con un email valido, cuenta personal  o de negocio verificar cuenta
    next
    Ahora nos pide miembro a nuestra organizacion => una vez que esta añadido como miembro les envia un email

## Transferencia el dominion de un repositorio a una organizacion
    Tenemos que tener el nombre de la organizacion entramos en la organizacion 
    podemos crear respositorio en nuestra organizacion, trambien crear proyectos
    estos proyecto tiene alcance de manera global de los repositorio que tenemos 
    **Ejemplo**
    entramos en nuestro repositorio y vamos ajustes y vamos a transferir y elegimos la organizacion que queramos
    si tenmos mas eligimos una y escribimos nuestro nombre de respositorio le damos aceptar
    y nos aperece en nuestro repositor que tenemos en nuestra organizacion 
    **Teams: Equipos de trabajo**
    En la organizacion vamos a teams, podemos crear Equipo o diferente equipos
    podemos ponerlo secreta o visible, si es secreta a los miembros de la organizacion nos lo va aparee
    creamos un teams
    los temas puede tener otros equipos que sepuede crear en teams
    y tambien miembros en cada teams
    en cada teams podemo añadir repositorios que haya agregado en la organizacion principal y pone por defecto solo lectura
    **Repositorio y privelgios a nuestra organización**
    Podemos cambiar los previlegios, hay un perfil admin podemos manejar issues requesta manejarlo y cerrarlo y 
    poner la opcion de mantenimineto
    **Autenticaciones de los miembros**
    los miembros podemos poner el usuario public y se puede desde a fuera que este usuario 
    pertenece a esta organizacio, podemos quitarlo pouede ser colaborador externo
    
    
