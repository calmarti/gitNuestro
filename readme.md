# Práctica de Git

## Respuestas al Ejercicio 1

### Ivan Martínez Calcaño


**¿Qué comando utilizaste en el paso 11?**
git reset --hard HEAD~1 
**¿Por qué?**
Para deshacer el último commit regresando un commit hacia atrás en el grafo, 
perdiendo (descartando) además los cambios realizados en el working copy. 

Alternativamente, podríamos hacer: git reset HEAD~1 y luego git restore git-nuestro.md
 y obtendríamos el mismo resultado. 

**¿Qué comando o comandos utilizaste en el paso 12?** 
git reflog y después: git reset --hard <id del commit>  
**¿Por qué?**
1. git reflog: 
Para obtener el id del commit que habíamos creado. 
Para ello busco en el log la línea donde aparece 'HEAD@{1}', la cual 
registra el commit anterior al último comando ejecutado.
2. git reset --hard <id del commit>  
**¿Por qué?**
Para mover el puntero HEAD (y el puntero de la rama 'styled) al commit que habíamos creado 
(rehacer el commit) y recuperar los cambios en el working copy

**El merge del paso 13, ¿Causó algún conflicto?** 
No. 
**¿Por qué?**
Al hacer el merge Git arroja el mensaje 'Already up to date'. 
Mi interpretación del mensaje es que como la rama 'styled' ya contiene 
al commit inicial de 'master', con un merge de 'master' no hay nada nuevo que absorber. 
Por tanto, no hay conflicto.  

**El merge del paso 19, ¿Causó algún conflicto?**
Sí. 
**¿Por qué?**
Porque el fichero git-nuestro.md de la rama 'styled' difiere
del fichero git-nuestro.md de la rama 'htmlify' en múltiples líneas. 

**El merge del paso 21, ¿Causó algún conflicto?** 
No. 
**¿Por qué?**
Porque al ser un grafo de tipo lista el commit de la rama 
'master' ya está contenido en la rama 'styled'. Por tanto, 
el merge fue de tipo fast-forward que, como vimos en clase, 
es un tipo de merge que por su propia naturaleza no genera 
conflicto.   

**¿Qué comando o comandos utilizaste en el paso 25?**
git log --graph --pretty=oneline

**El merge del paso 26, ¿Podría ser fast forward?** 
Sí.
**¿Por qué?**
Porque como la rama 'title' fue creada en el último commit de la rama 'master',
aquella contiene a todos los commits de 'master'. Esto significa
que esta parte del grafo es de tipo lista. Por tanto, un merge
fast-forward también era posible.  

**¿Qué comando o comandos utilizaste en el paso 27?**
1. git log --pretty=oneline --graph
Con este comando puedo identificar visualmente cual fue el commit 
anterior de la rama 'master' antes de hacer el merge. Una vez
identificado ya tengo su id.  

2. git reset <id commit anterior>
Con este comando el puntero HEAD y el puntero de la rama 'master' regresan
al commit previo al merge sin que el working copy pierda los 
cambios producidos por el merge. 

**¿Qué comando o comandos utilizaste en el paso 28?**

git restore git-nuestro.md
Con este comando descarto los cambios en el working copy
que habían sido producidos por el merge, y que aún 
permanecían ahí a pesar de haber deshecho el merge.  

**¿Qué comando o comandos utilizaste en el paso 29?**
1. git branch
para asegurarme que no estoy en la rama que quiero eliminar
2. git branch -D title:
Para eliminar la rama title de manera forzada

**¿Qué comando o comandos utilizaste en el paso 30?**
1. git reflog
Para obtener el id del commit 'inalcanzable', o sea, el del merge donde
master absorbió a 'title'

2. git reset --hard <id del commit donde se hizo el merge deshecho> 
Para rehacer el merge (el puntero HEAD y de 'master' regresan al commit
donde se realizó el merge que habíamos deshecho y se restauran los cambios 
en el working copy). 

**¿Qué comando o comandos usaste en el paso 32?**
1. git reflog:
Para ubicar el commit inicial y su id
2. git reset <id del commit inicial>
Para deshacer todos los commits
 y regresar al commit inicial (sin tocar el working copy)

**¿Qué comando o comandos usaste en el punto 33?**
1. git reflog:
Para obtener el id del commit donde se hizo el merge no-ff de 'title' en 'master':
2. git reset <id del commit>:
Para rehacer la historia de commits desde el inicial hasta el último 
(sin tocar el working copy) 
3. git log --graph --pretty=oneline:
Para comprobar que hemos restaurado la historia de commits de 'master'
4. nano git-nuestro.md
Para comprobar que el fichero en working copy refleja todos los cambios
hechos a lo largo del ejercicio. 






