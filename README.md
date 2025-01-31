
# Proyecto Nginx con CI/CD

Este proyecto configura un servidor web utilizando Nginx ejecutados en un contenedor Docker. El despliegue se realiza de manera automática utilizando GitHub Actions (CI/CD), y se gestiona con Docker Compose.

## Estructura del Proyecto

La estructura del proyecto es la siguiente:

```
nginx/
├── docker-compose.yml          # Configuración de los contenedores Docker
├── nginx/
│   ├── conf.d/
│   │   └── default.conf        # Configuración de Nginx
│   └── html/
│       └── index.html          # Página HTML básica de Nginx
├── .github/
│   └── workflows/
│       └── deploy.yml          # Configuración del pipeline de CI/CD
└── README.md                   # Documentación del proyecto
```

## Requisitos

- Docker
- Docker Compose
- GitHub account

## Pasos para Desplegar el Proyecto

1. **Configurar GitHub Actions**:
   - Crea un nuevo repositorio en GitHub y sube este proyecto.
   - Configura los secretos en GitHub:
     - `DOCKER_USERNAME`: Tu nombre de usuario de Docker Hub.
     - `DOCKER_PASSWORD`: Tu contraseña de Docker Hub.
     - `SSH_PRIVATE_KEY`: Tu clave privada SSH para acceder a tu VPS.
  
2. **Configurar el VPS**:
   - **Asegúrate de que Docker y Docker Compose estén instalados en tu VPS**. Este paso solo se realiza una vez. 
     - En el VPS, instala Docker y Docker Compose siguiendo las instrucciones correspondientes para tu sistema operativo.
   
3. **Automatización del Despliegue**:
   - **GitHub Actions** se encarga de todo el proceso automáticamente:
     1. Cuando haces un push a la rama principal del repositorio en GitHub, el workflow de CI/CD se activa.
     2. El workflow construye las imágenes Docker y las sube automáticamente a Docker Hub.
     3. Luego, el workflow se conecta automáticamente a tu VPS usando SSH y ejecuta los siguientes comandos:
        - `git pull` para obtener los últimos cambios.
        - `docker-compose up -d` para actualizar los contenedores con la nueva imagen.
   
   ¡No es necesario que ejecutes manualmente nada en el VPS!

## Acceder al Servidor

Una vez que los contenedores estén en ejecución, puedes acceder al servidor Nginx a través de la IP pública de tu VPS. En tu navegador, abre:

```
http://<IP-DE-TU-VPS>
```

Verás la página de bienvenida de Nginx.

---

## Configuración de Nginx

El archivo de configuración de Nginx se encuentra en `nginx/conf.d/default.conf`. Este archivo define el servidor y el puerto en el que escucha Nginx, así como el directorio raíz de los archivos HTML.

