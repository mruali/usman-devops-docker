# Base Image
FROM php:7.4-apache

# Install system dependencies and libzip
RUN apt-get update && apt-get install -y \
    libzip-dev \
    vim \
    git \
    unzip \
    && apt-get clean

# Install PHP extensions
RUN docker-php-ext-install mysqli pdo pdo_mysql zip

# Enable Apache Modules
RUN a2enmod rewrite

# Set the ServerName to Suppress Apache Warnings
RUN echo "ServerName localhost" >> /etc/apache2/apache2.conf

# Set Proper Permissions for Document Root
WORKDIR /var/www/html

# Copy Application Files into the Container
COPY ./transport /var/www/html

# Set Permissions for the Application Directory
RUN chown -R www-data:www-data /var/www/html \
    && chmod -R 755 /var/www/html

# Expose Port 80
EXPOSE 80

# Start the Apache Server
CMD ["apache2-foreground"]
