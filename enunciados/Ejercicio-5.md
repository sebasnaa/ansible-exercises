# Ejercicios bucles

1. Crear una lista web_service que contenga los elementos: httpd y vsftpd y crear una tarea que pregunte si el servicio está iniciado, recorriendo esos elementos con un bucle.

    ```yaml
    - name: comprar si el servicio está ok
    hosts: nodo1
    vars:
        web_service:
        - httpd
        - vsftpd
    tasks:
        - name: al lio
        service:
            name: "{{ item }}"
            state: started 
        loop: "{{ web_service }}"
    ```

2. Queremos comprimir los archivos del directorio ``/home/usuario/tomcat/logs`` que
tengan extensión ``.log``, ``.out`` y ``.txt`` (se puede usar o no regex)

    ```yaml
    - name: buscar y encontrar
    hosts: nodo1
    tasks:
        - name: Primero encontrar
        find:
            paths: /home/usuario/tomcat/logs
            patterns: '*.log,*.out,*.txt'
        register: salida

        - name: comprimir
        archive:
            remove: yes
            path : "{{ item.path }}"
            dest : "{{ item.path }}.bz2"
            format: bz2
        loop: "{{ salida.files }}"
    ``` 



3. Descomprimir archivos de un usuario llamado weblogic, de un fichero llamado:
server-jre-8u191-linux-x64.tar.gz al directorio ``/opt/oracle``

    ```yaml
    - name: buscar y encontrar
    hosts: nodo1
    tasks:
    - name: descomprimo
        unarchive:
        src: /home/usuario/tomcat/logs/otromio.out.bz2
        dest: /home/usuario/tomcat/logs
        remote_src: yes
    ```

4. Validar que los paquetes están instalados. (Pista modulo package_facts)

    ```yaml
    - name: buscar y encontrar
    hosts: nodo1
    tasks:
        - name: Gather the package facts
        package_facts:
            manager: auto

        - name: Print the package facts
        debug:
            var: ansible_facts.packages

        - name: Check whether a package called foobar is installed
        debug:
            msg: "{{ item }} está instalado"
        when: '"{{ item }}" in ansible_facts.packages'
        loop:
            - apache2
            - vim
            - nginx
            - filebeat 
    ```

5. Buscar ficheros .log que tengan 30 dias del directorio ``/var/log``y luego mostrar lo que ha salido
 

6. Búsqueda recursiva desde la ruta ``/`` aquellos que tengan más de 100 megas (Pista: módulo find)

 
7. Buscar con Regex en la ruta ``/var/log``, aquellos ficheros que empiecen por una letra minúcula entre la a y la z, tengan un guion bajo y después 8 numeros y que tengan extensión ``.log`` (además, que tengan más de 100 megas)

    ```yaml
    - name: buscar por vejez y tamaño
    hosts: nodo1
    tasks:
        - name: buscar
        find:
            path: /home/usuario/
            size: 10k
            age: 10d
            recurse: yes
        register: salida
        - name: imprime
        debug:
            var: "{{salida.path}}"
    ```

