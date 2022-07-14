¡Importante! Primero siempre hacer un "git status" con eso se sabe mucho

**********************************************************************************************************

contenido separado por *

- procedimiento  pruebas gitignore       / referencias

- los proceso para subir al github  hc-mic29 / odoo-dev-templ
                                               ==============
- por ej. como cambiar a un diferente branch (version) del repositorio source (src)

- varios marcadores no investigado de preguntas surgidas a lo largo del aprendizaje de git

**********************************************************************************************************

procedimiento que encontré buena práctica para ver que pasa con cambios relacionados la archivo gitignore

probando / agregando algo a gitignore

https://git-scm.com/docs/gitignore

escribo cambios en gitinore:
git status    veo lo que sale aunque contenido de carpetas vacias no salen

git add .

git status      veo más detalles que al solo cambiar gitignore 

no me gusta el resultado

git rm -r --cached .

https://stackoverflow.com/questions/2545602/how-to-git-ignore-subfolders-subdirectories
git status también sugiere el uso del comando:
    (usa "git rm --cached <archivo>..." para sacar del área de stage)

si hay errores como lo indica el mismo programa

git rm -rf --cached . ha funcionado bien aunque no entiendo todo del mensaje 

cambios en gitignore y de nuevo hasta el git add . final y el git commit -m "mensaje" o git commit -a
y en el editor que asoma escribir lo que necesite

referencias adicionales:
https://stackoverflow.com/questions/6794717/git-ignore-certain-files-in-sub-directories-but-not-all

.gitignore excluye carpeta pero incluye subcarpeta específica
https://qastack.mx/programming/5533050/gitignore-exclude-folder-but-include-specific-subfolder

    Nota
    El seguimiento /*es significativo:

        El patrón dir/excluye un directorio llamado diry (implícitamente) todo debajo de él.
        Con dir/, Git nunca mirará nada debajo diry, por lo tanto, nunca aplicará ninguno de los patrones de "no excluir" a nada debajo dir.
        El patrón dir/*no dice nada sobre dirsí mismo; simplemente excluye todo debajo dir. Con dir/*, Git procesará el contenido directo de dir, dando a otros patrones la oportunidad de "excluir" un poco del contenido ( !dir/sub/).


.gitignore examples to ignore files, folder & pattern | GoLinuxCloud
https://www.golinuxcloud.com/gitignore-examples/

url adicionales sin leer detalladamente
https://git.dokry.com/gitignore-para-todos-los-files-en-carpetas-y-subcarpetas.html

**********************************************************************************************************

hecho ésto apra subirlo a github

git checkout -b test_gitignore
git remote add test git@github.com:hc-mic29/odoo-dev-templ.git
git fetch test                                                          <-- todavía no se mucho sobre ésto
warning: no hay commits comunes                                 pero es para algo cunaod existe ya algo en el 
                                                                repositorio remoto
remote: Enumerating objects: 24, done.
remote: Counting objects: 100% (24/24), done.
remote: Compressing objects: 100% (13/13), done.
remote: Total 24 (delta 4), reused 19 (delta 4), pack-reused 0
Desempaquetando objetos: 100% (24/24), 2.92 KiB | 597.00 KiB/s, listo.
Desde github.com:hc-mic29/odoo-dev-templ
 * [nueva rama]      main       -> test/main
 * [nueva rama]      master     -> test/master


michael@ssdquark:~/Git/prueba_odoo_templ$ git branch -r
  test/main
  test/master
michael@ssdquark:~/Git/prueba_odoo_templ$ git branch -avv
  master              ba15911 probando patterns de gitignore
* test_gitignore      ba15911 probando patterns de gitignore
  remotes/test/main   1cfdd78 Add files via upload
  remotes/test/master 3172255 README de main


michael@ssdquark:~/Git/prueba_odoo_templ$ git branch -u test/master test_gitignore
Rama 'test_gitignore' configurada para hacer seguimiento a la rama remota 'master' de 'test'.
michael@ssdquark:~/Git/prueba_odoo_templ$ git pull
fatal: rehusando fusionar historias no relacionadas
michael@ssdquark:~/Git/prueba_odoo_templ$ git branch -u test/test test_gitignoreerror: la rama de upstream solicitada 'test/test' no existe
ayuda: 
ayuda: Si estás planeando basar tu trabajo en una rama upstream
ayuda: que ya existe en el remoto, tal vez necesites ejecutar
ayuda: "git fetch" para recibirla.
ayuda: 
ayuda: Si estás planeando hacer push a una nueva rama local que
ayuda: va a rastrear a su contraparte remota, tal vez quieras usar
ayuda: "git push -u" para configurar tu upstream predeterminado cuando realices el push.
michael@ssdquark:~/Git/prueba_odoo_templ$ git branch -r
  test/main
  test/master
michael@ssdquark:~/Git/prueba_odoo_templ$ git push -u test/test test_gitignore
fatal: 'test/test' does not appear to be a git repository
fatal: No se pudo leer del repositorio remoto.

Por favor asegúrate de que tengas los permisos de acceso correctos
y que el repositorio exista.
michael@ssdquark:~/Git/prueba_odoo_templ$ git push -u test test_gitignore
Enumerando objetos: 13, listo.
Contando objetos: 100% (13/13), listo.
Compresión delta usando hasta 4 hilos
Comprimiendo objetos: 100% (5/5), listo.
Escribiendo objetos: 100% (13/13), 1.02 KiB | 522.00 KiB/s, listo.
Total 13 (delta 0), reusado 0 (delta 0)
remote: 
remote: Create a pull request for 'test_gitignore' on GitHub by visiting:
remote:      https://github.com/hc-mic29/odoo-dev-templ/pull/new/test_gitignore
remote: 
To github.com:hc-mic29/odoo-dev-templ.git
 * [new branch]      test_gitignore -> test_gitignore
Rama 'test_gitignore' configurada para hacer seguimiento a la rama remota 'test_gitignore' de 'test'.




**********************************************************************************************************
si por ejemplo quiero clonar el repositorio de otra version de una addon odoo oca

cd src/
                                                                   
git clone --branch 14.0 https://github.com/OCA/partner-contact.git src/partner-contact
                                                                    ^crearía un directorio adicional src
que tiene que ser inluido en la config renglón addons-path

git status


https://stackoverflow.com/questions/5736987/how-to-switch-to-a-different-remote-branch-in-git

git branch -r
git branch --all

git checkout remotes/origin/15.0
git checkout -b develop


ésto sería diferente con la versión de odoo porque con depth uno solo "single-brach"


cd src/odoo

git branch --all

* 14.0
  remotes/origin/14.0

TODO: en otra ocasióninvesitag siguientes cuestiones
¿como agragar remotes/origin/15?



**********************************************************************************************************

git remove all remotes and re config at DuckDuckGo
https://duckduckgo.com/?t=ffsb&q=git+remove+all+remotes+and+re+config&ia=web

How to Remove a Git Remote | Linuxize
https://linuxize.com/post/how-to-remove-git-remotes/


git - Repository size limits for GitHub.com - Stack Overflow
https://stackoverflow.com/questions/38768454/repository-size-limits-for-github-com

version control - How can I delete a folder from a git branch? - Stack Overflow
https://stackoverflow.com/questions/69254431/how-can-i-delete-a-folder-from-a-git-branch

version control - Git "revert" current directory - Stack Overflow
https://stackoverflow.com/questions/14125385/git-revert-current-directory

linux - Use "git revert" to back-out a change adding a line? - Stack Overflow
https://stackoverflow.com/questions/10159775/use-git-revert-to-back-out-a-change-adding-a-line

¿Qué es un pull request? - Aprende GIT
https://aprendegit.com/que-es-un-pull-request/

github - Git merge and push - Stack Overflow
https://stackoverflow.com/questions/13597494/git-merge-and-push

Git push rechazó "no avance rápido"
https://qastack.mx/programming/20467179/git-push-rejected-non-fast-forward

git - Updating a local repository with changes from a GitHub repository - Stack Overflow
https://stackoverflow.com/questions/1443210/updating-a-local-repository-with-changes-from-a-github-repository

git - Difference between file in local repository and origin - Stack Overflow
https://stackoverflow.com/questions/21101572/difference-between-file-in-local-repository-and-origin

Git - git-checkout Documentation
https://git-scm.com/docs/git-checkout/en

How to Create a Remote Branch in Git
https://www.w3docs.com/snippets/git/how-to-create-a-remote-branch-in-git.html

git error: src refspec Odoo14EC-dev no concuerda con ninguno at DuckDuckGo
https://duckduckgo.com/?t=ffsb&q=git+error%3A+src+refspec+Odoo14EC-dev+no+concuerda+con+ninguno&ia=web

Message 'src refspec master does not match any' when pushing commits in Git - Stack Overflow
https://stackoverflow.com/questions/4181861/message-src-refspec-master-does-not-match-any-when-pushing-commits-in-git


