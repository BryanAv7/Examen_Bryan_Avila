# Usar Debian como imagen base
FROM debian:bullseye

# Configurar variables de entorno
ENV DEBIAN_FRONTEND=noninteractive

# Instalar dependencias necesarias
RUN apt-get update && apt-get install -y \
    curl \
    gnupg \
    apache2 \
    && curl -fsSL https://deb.nodesource.com/setup_18.x | bash - \
    && apt-get install -y nodejs \
    && npm install -g @angular/cli

# Crear directorio de trabajo en el contenedor
WORKDIR /var/www/angular-docker-app

# Copiar package.json y package-lock.json para instalar dependencias
COPY package*.json ./

# Instalar dependencias de Angular
RUN npm install

# Copiar el resto del código fuente al contenedor
COPY . .

# Construir la aplicación Angular para producción
RUN npm run build -- --output-path=/var/www/html --base-href=/

# Configurar Apache para servir archivos estáticos
COPY nginx.conf /etc/apache2/sites-available/000-default.conf
RUN a2enmod rewrite

# Exponer el puerto 80
EXPOSE 80

# Comando por defecto para iniciar Apache
CMD ["apache2ctl", "-D", "FOREGROUND"]
