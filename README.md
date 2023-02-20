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
    git status => informa el estado del repositorio, si esta en verde por que se han 
    aceptado con el add, si estan en rojo por que no estan añadido
    git reset nombreArchivo.x =>ese archivo no es parte del estado
    git commit -m "texto de lo comprometido=>nos mostrar los archivo que estan comprometido
