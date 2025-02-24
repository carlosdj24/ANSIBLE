# Proyecto Ansible Docker Container

Este repositorio tiene como objetivo automatizar la gestión de contenedores Docker utilizando Ansible.

## Descripción

Este proyecto utiliza el módulo `docker_container` de Ansible para gestionar un contenedor Docker basado en la imagen oficial de `nginx`. El playbook realiza lo siguiente:

1. Asegura que Docker esté instalado en la máquina local.
2. Inicia un contenedor de Nginx.
3. Verifica el estado del contenedor y muestra si está en ejecución.

## Requisitos

- Tener Docker instalado en la máquina local.
- Tener Ansible instalado en tu máquina de control.

## Cómo ejecutar el playbook

1. Clona este repositorio:

   ```bash
   git clone https://github.com/tuusuario/ansible-docker-container.git
   cd ansible-docker-container
