# Usar la imagen oficial de Nginx como base
FROM nginx:latest

# Copiar la configuración personalizada de Nginx
COPY conf.d/default.conf /etc/nginx/conf.d/default.conf

# Copiar los archivos HTML
COPY html /usr/share/nginx/html

# Exponer el puerto 80
EXPOSE 80

# Comando por defecto para iniciar Nginx
CMD ["nginx", "-g", "daemon off;"]
