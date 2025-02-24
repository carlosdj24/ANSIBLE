# ANSIBLE

![ansible](/ansible1.png)

# **Estudio del Módulo `docker_container` en Ansible**  

## **1.- Nombre del módulo: `docker_container`**  

### **Descripción**  
El módulo `docker_container` de Ansible se utiliza para gestionar contenedores Docker en un sistema. Permite crear, iniciar, detener, eliminar y configurar contenedores de Docker, facilitando la administración de aplicaciones y servicios que se ejecutan en contenedores. Es muy útil para la automatización de la gestión de contenedores en entornos de servidores y en la integración de Docker en flujos de trabajo de DevOps.

---

## **2.- Ejemplos de funcionamiento**  

### **Ejemplo 1: Crear y ejecutar un contenedor Docker con Nginx**  
En este playbook crearemos y ejecutaremos un contenedor Docker utilizando la imagen `nginx:latest`, exponiendo el puerto 80 del contenedor al puerto 8080 del host.

#### **Archivo:** `crear_contenedor_nginx.yml`
```yaml
---
- name: Crear y ejecutar un contenedor Docker con Nginx
  hosts: localhost  # Se ejecuta en el host local
  become: true  # Permite ejecutar el playbook con permisos de superusuario
  tasks:
    - name: Crear el contenedor Nginx
      docker_container:
        name: nginx_container
        image: nginx:latest
        state: started
        restart_policy: always
        exposed_ports:
          - "80"
        published_ports:
          - "8080:80"
