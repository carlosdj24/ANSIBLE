# Estudio del Módulo `docker_container` en Ansible

## 1.- Nombre del módulo: `docker_container`

### Descripción

El módulo `docker_container` de Ansible permite gestionar contenedores Docker de manera automatizada. Con este módulo, puedes crear, eliminar, reiniciar, detener y administrar contenedores Docker desde tus playbooks de Ansible. Es ideal para la automatización de tareas en entornos que utilizan contenedores, y simplifica la administración de aplicaciones contenidas.

---

## 2.- Ejemplos de funcionamiento

### Ejemplo 1: Crear un contenedor Docker

En este playbook crearemos un contenedor Docker que ejecute una imagen de `nginx`.

#### Archivo: `crear_contenedor_nginx.yaml`

```yaml
- name: Crear un contenedor Docker con Nginx
  hosts: localhost  # Reemplazar con el nombre del host o grupo de hosts
  become: true  # Permite ejecutar el playbook con permisos de superusuario
  tasks:
    - name: Crear y ejecutar el contenedor Nginx
      community.docker.docker_container:
        name: nginx_contenedor
        image: nginx
        state: started
        restart_policy: always
        published_ports:
          - "80:80"
```
#### Comando para ejecutar el Playbook
```Bash

ansible-playbook crear_contenedor_nginx.yaml
Verificación (En el cliente)
```
```Bash

docker ps
Si el contenedor está corriendo, aparecerá en la lista.
```
### Ejemplo 2: Detener un contenedor Docker
Este playbook detendrá el contenedor nginx_contenedor.

### Archivo: detener_contenedor_nginx.yaml
```YAML

- name: Detener el contenedor Docker Nginx
  hosts: localhost  # Reemplazar con el nombre del host o grupo de hosts
  become: true  # Permite ejecutar el playbook con permisos de superusuario
  tasks:
    - name: Detener el contenedor Nginx
      community.docker.docker_container:
        name: nginx_contenedor
        state: stopped
```
### Comando para ejecutar el Playbook
```Bash

ansible-playbook detener_contenedor_nginx.yaml
Verificación (En el cliente)
```
```Bash

docker ps -a
```
El contenedor debería aparecer detenido.

### Ejemplo 3: Eliminar un contenedor Docker
En este playbook eliminaremos el contenedor nginx_contenedor.

Archivo: eliminar_contenedor_nginx.yaml
```YAML

- name: Eliminar el contenedor Docker Nginx
  hosts: localhost  # Reemplazar con el nombre del host o grupo de hosts
  become: true  # Permite ejecutar el playbook con permisos de superusuario
  tasks:
    - name: Eliminar el contenedor Nginx
      community.docker.docker_container:
        name: nginx_contenedor
        state: absent
```
### Comando para ejecutar el Playbook
```Bash

ansible-playbook eliminar_contenedor_nginx.yaml
Verificación (En el cliente)
```
```Bash

docker ps -a
El contenedor debería haber sido eliminado.
```
## 3.- Referencias
Documentación oficial de Ansible sobre el módulo docker_container
Guía oficial de Ansible
Repositorio de Ansible Docker Collection
<!-- end list -->
