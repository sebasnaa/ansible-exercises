1. Buscar ficheros .log que tengan 30 dias del directorio ``/var/log``
y luego mostrar lo que ha salido
 
2. Búsqueda recursiva desde la ruta ``/`` aquellos que tengan más de 100 megas

3. Partiendo de este playbook, y aunque ya sabemos que no se haría de esta manera, gestionar los posibles errores si no tenemos alguna
de las distribuciones. (no busco condicionales, sino bloques, etc)

    ```yaml
    - name: ejercicio
    hosts: all
    tasks:
        - name: instala en ubuntu
        apt:
            name: git
            state: present
        - name: instala en centos
        yum: 
            name: git
            state: present
    ```

4. Utilizando una estructura wait_for, esperar a que un fichero (elegid el nombre y la ubicación o por ejemplo bloqueo.lock) de la máquina 
remota deje de existir en esa máquina remota. Cuando salga del wait_for, que haga una tarea que muestre un mensaje. Para eliminar ese fichero 
de la máquina remota, podéis hacerlo de forma manual o como queráis.

5. ¿Y si ahora lo quisiéramos como condición previa para ejecutar unas tareas cualquiera? Por ejemplo tomar algunas tareas de algún ejercicio
que sólo se ejecuten si previamente se ha eliminado ese fichero bloqueo.lock 

6. Crear un fichero: ``missecretos.yml`` que albergue unas variables llamadas miuser y micontra, cifrarlo con ansible-vault, y después llamarlo
desde un playbook que tenga una tarea que muestre el valor de miuser y micontra

7. Realizar la instalación del rol de mysql cifrando ese fichero de la contraseña: ``vars/main.yml``

8. Escoger algún otro rol de ansible galaxy y lanzarlo en vuestras máquinas. Elegid alguno que os lo ponga facil en los requerimientos. 