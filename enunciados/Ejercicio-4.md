<<<<<<< HEAD
1. Buscar ficheros .log que tengan 30 dias del directorio ``/var/log`` y luego mostrar lo que ha salido
 
2. Búsqueda recursiva desde la ruta ``/`` aquellos que tengan más de 100 megas

3. Partiendo de este playbook, y aunque ya sabemos que no se haría de esta manera, estionar los posibles errores si no tenemos alguna de las distribuciones. (no busco condicionales, sino bloques, etc)
=======
# Ejercicios bucles

1. Queremos mostrar los ficheros con `ls /`, `ls -a /`, `ls -la /` de aquellos nodos que sean Ubuntu.
>>>>>>> 630ea2f7bfd0a25b5037f7a25d4f775f5687394f

2. Escribir una tarea que copie la lista de ficheros JSON que se acompaña desde `/home/usuario/json` a `/tmp/jsons`.

<<<<<<< HEAD
4. Utilizando una estructura wait_for, esperar a que un fichero (elegid el nombre y la ubicación o por ejemplo bloqueo.lock) de la máquina remota deje de existir en esa máquina remota. Cuando salga del wait_for, que haga una tarea que muestre un mensaje. Para eliminar ese fichero de la máquina remota, podéis hacerlo de forma manual o como queráis.

5. ¿Y si ahora lo quisiéramos como condición previa para ejecutar unas tareas cualquiera? Por ejemplo tomar algunas tareas de algún ejercicio que sólo se ejecuten si previamente se ha eliminado ese fichero bloqueo.lock 
=======

>>>>>>> 630ea2f7bfd0a25b5037f7a25d4f775f5687394f

3. Ahora sí que sí vamos a instalar Nginx. Para ello tenemos que realizar las siguientes tareas:
	- Instalar el propio Nginx con su apt update y todo.
	- Permitir el paso a través de cortafuegos. Para ello, debemos escoger entre Nginx Full, Nginx HTTP, Nginx HTTPS.
	- Verificar el status del cortafuegos. Capturar la salida para nos muestre que todo ha ido bien.
	- Verificar que el servicio está funcionando.

4. Crear una tarea que, dada una lista de usuarios y una lista de grupos como los anteriores, los combine todos contra todos creando el usuario y el grupo. 


    Grupos:
   - usuarios
   - admin
   - desarrollo
   - testing
   - produccion

    Usuarios:
    - Pedro
    - Juan
    - Maria
    - Ana
    - Antonio
    - Marta
    - Jose

5. Ahora queremos ser más específicos y crear los usuarios con estas especificaciones:

| Usuarios | Grupos a los que pertenece     | Expira la cuenta | uid  | Crear Clave SSH |
|----------|--------------------------------|-------------------|------|-----------------|
| Pedro    | admin, usuarios, produccion    | no                | 1040 | si, rsa 2048    |
| Juan     | usuarios, desarrollo           | no                | 1041 | no              |
| Maria    | usuarios, desarrollo           | no                | 1042 | no              |
| Ana      | testing, produccion           | no                | 1043 | si, rsa 2048    |
| Antonio  | usuarios, testing              | no                | 1044 | no              |
| Marta    | usuarios, produccion           | no                | 1045 | no              |
| Jose     | admin, usuarios, desarrollo    | no                | 1046 | si, rsa 2048    |
| Invitado1| usuarios                        | si                | -    | no              |
| Invitado2| usuarios                        | si                | -    | no              |
