
## Sección Udemy 10

## import task

4. Limpiar dependencias y la cache (Crear un fichero de tareas para luego importarlo con import_task)

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

## Sección Udemy 11

## Loop

3. Crear una tarea que instale con loop: `curl`, `apt-transport-https`, `ca-certificates`, `software-properties-common`, `glances`, `git` y `vim`.

	3.2. ¿Y si ahora queremos distinguir entre las distintas distribuciones de Linux? (No usar el módulo package) 
		- Primero distínguelas a través de tags.
		- En segundo lugar distínguelas a partir de capturar qué distribución es la del host.