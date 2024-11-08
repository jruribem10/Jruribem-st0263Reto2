# Reto 2 - Despliegue de LMS Moodle en Clúster de Alta Disponibilidad en Kubernetes

### Participantes
- **Jaime Uribe**  
  Correo: [jruribem@eafit.edu.co](mailto:jruribem@eafit.edu.co)
- **Juan Pablo Duque**  
  Correo: [jpduquep@eafit.edu.co](mailto:jpduquep@eafit.edu.co)

### Profesor
- Álvaro Ospina
- Correo: [aospina.edu.co](mailto:aospina@eafit.edu.co)

---

## 1. Descripción del Proyecto

Este reto consiste en desplegar un LMS Moodle en un clúster de alta disponibilidad en Kubernetes autoescalado en la nube. El despliegue incluye la configuración de un dominio propio y un certificado SSL.

En este proyecto se emplea **NGINX** como balanceador de carga (LB) en la capa de aplicación de Moodle. Además, se utilizan dos servidores adicionales:
- **DBServer**: servidor de base de datos, que puede ejecutarse en Docker (recomendado) o de forma nativa.
- **FileServer**: servidor de archivos, que implementa un NFSServer para la gestión de archivos.

### 1.1 Aspectos Cumplidos

- Despliegue de Drupal.
- Configuración del balanceador de carga con NGINX.
- Despliegue de base de datos MySQL.
- Configuración de NFS mediante EFS de AWS, con la creación de dos sistemas de archivos.

### 1.2 Aspectos No Cumplidos

- Replicación de los nodos de Drupal.
- Configuración de dominio SSL.

---

## 2. Información General

La arquitectura de este despliegue se basa en la replicación de pods con imágenes de distintos componentes de software, los cuales operan en conjunto para asegurar la alta disponibilidad de la aplicación.

Se generaron **n** réplicas del CMS (Drupal) y **m** réplicas del balanceador de carga. Gracias a los mecanismos de replicación de datos proporcionados por EFS, se asegura la consistencia de la información almacenada en el sistema.

### 2.2 Lenguaje Utilizado

Se utilizó **YAML** para definir los servicios necesarios, incluyendo la configuración de la base de datos, el balanceador de carga y la instalación de Drupal.

---

## 3. Desafíos

Durante el desarrollo del proyecto se presentaron varios desafíos:

1. **Conexión de Drupal**: Problemas iniciales al conectar Drupal con la base de datos y el sistema EFS.
2. **Configuración Independiente de Nodos**: Los nodos desplegados operaban de forma independiente, sin compartir la misma configuración.
3. **Escalado de Balanceador de Carga**: Se presentaron problemas de configuración del balanceador de carga (LB) al aumentar el número de nodos, lo que ocasionó errores de escalabilidad en algunas réplicas.

---

Este repositorio contiene los archivos de configuración y las instrucciones necesarias para la implementación y despliegue del sistema en Kubernetes.
---
![image](https://github.com/user-attachments/assets/a0aeab88-2dfa-4929-b739-ef2d73df245a)
---
## Servicios
![image](https://github.com/user-attachments/assets/d7ed791c-4665-4f3c-ab81-9b94ad641fa2)

---
![image](https://github.com/user-attachments/assets/caf475d3-07b4-4ed3-9712-a2f4a75f68e7)

---



