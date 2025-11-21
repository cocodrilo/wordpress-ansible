# WordPress Deployment with Ansible (Curso Ansible)

Este proyecto contiene los playbooks, inventarios y roles necesarios para desplegar una arquitectura WordPress completa utilizando Ansible. Incluye base de datos MySQL/MariaDB, servidores web y un balanceador de carga con HAProxy.

## Estructura del proyecto

.
├── ansible.cfg
├── group_vars/
│   └── all.yml
├── inventario.ini
├── roles/
│   ├── database/
│   │   ├── defaults/main.yml
│   │   ├── handlers/main.yml
│   │   ├── tasks/main.yml
│   │   ├── templates/my.cnf.j2
│   │   ├── vars/main.yml
│   │   ├── meta/main.yml
│   │   ├── files/
│   │   └── tests/
│   ├── loadbalancer/
│   │   ├── defaults/main.yml
│   │   ├── handlers/main.yml
│   │   ├── tasks/main.yml
│   │   ├── templates/haproxy.cfg.j2
│   │   ├── vars/main.yml
│   │   ├── meta/main.yml
│   │   ├── files/
│   │   └── tests/
│   └── webserver/
│       ├── defaults/main.yml
│       ├── handlers/main.yml
│       ├── tasks/main.yml
│       ├── templates/wp-config.php.j2
│       ├── vars/main.yml
│       ├── meta/main.yml
│       ├── files/
│       └── tests/
├── secrets.yml
├── test-db.yml
├── test-lb.yml
└── test-web.yml

## Componentes principales

### 1. Rol **database**
Instala y configura la base de datos para WordPress:
- MariaDB/MySQL
- Configuración del servidor (`my.cnf`)
- Creación de base de datos y usuario
- Handlers para reinicios
- Variables específicas en `vars/main.yml`

### 2. Rol **webserver**
Despliega WordPress y configura Apache o Nginx:
- Descarga y despliegue del código WordPress
- Plantilla `wp-config.php.j2` con claves y conexiones
- Permisos correctos para el servidor web
- Archivos estáticos opcionales en `files/`

### 3. Rol **loadbalancer**
Balanceador de carga con HAProxy:
- Plantilla completa `haproxy.cfg.j2`
- Handlers para recargar servicio
- Variables ajustables en `vars/main.yml`
