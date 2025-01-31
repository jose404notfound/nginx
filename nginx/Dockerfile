# Usamos la imagen base de Nginx
FROM nginx:latest

# Copiar los archivos de configuración personalizados
COPY ./conf.d /etc/nginx/conf.d
COPY ./html /usr/share/nginx/html

# Exponer el puerto 80
EXPOSE 80
