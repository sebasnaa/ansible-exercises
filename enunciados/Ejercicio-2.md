# Ejercicios módulos


1. Comprimir el directorio /apps/tomcat en formato gz (Pista: módulo archive)

    ```yaml
    - name: comprimir un directorio
      hosts: nodo1
      tasks:
      - name: comprimir el contenido de /apps/tomcat
        archive:
          path: /apps/tomcat
          dest: /apps/tomcat.tar.gz
          format: gz
    ```
    - Usando variables
    ```yaml
    - name: comprimir un directorio
      hosts: nodo1
      vars:
        ruta: /apps/tomcat
        destino: /apps/tomcat.tar.gz
        formato: gz 
      tasks:
      - name: comprimir el contenido de /apps/tomcat
        archive:
          path: "{{ ruta }}"
          dest: "{{ destino }}"
          format: "{{ formato }}"
    ```	
2. Comprimir todos los archivos de la carpeta /apps/tomcat/logs y de la carpeta /var/log/tomcat/  Excluir aquellos que tengan la palabra access y sean de extensión .txt

    ```yaml
    - name: comprimir archivos con exclusion
      hosts: nodo1
      tasks:
      - name: comprimir el contenido de /apps/tomcat
        archive:
          path: 
          - /apps/tomcat/logs/*
          - /var/log/tomcat/*
          dest: /apps/tomcat/ficherolog.tar.bz2
          format: bz2
          exclude_path:
          - /apps/tomcat/logs/*access*.txt
          - /var/log/tomcat/*access*.txt
    ```
3. Instalar paquetes .deb (Pista, módulo apt)
    ```yaml
    - name: Instalar paquetes .deb
      hosts: nodo1
      tasks:
      - name: instalar con deb en local
        apt:
          deb: /home/usuario/paquete_mio.deb

      - name: instalar con deb desde internet
        apt:
          deb: https://artifacts.elastic.co/downloads/beats/filebeat/filebeat-7.17.2-amd64.deb
    ```


4. Limpiar dependencias y la cache (Crear un fichero de tareas para luego importarlo con import_task) (Pista: Módulo apt)

    - limpia_fija_yda_esplendor.yml

      ```yaml
      - name: Remove useless packages from the cache
        apt:
          autoclean: yes

      - name: Remove dependencies that are no longer required
        apt:
          autoremove: yes
      ```
    - limpiar.yml

      ```yaml
      - name: limpieza profunda
        hosts: nodo1
        tasks:
          - name: limpiar
            import_task: limpia_fija_yda_esplendor.yml
      ```