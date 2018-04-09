#pegar o PHP
FROM php:7.2-apache

#enable mysqli para conectar o banco de dados
RUN docker-php-ext-install mysqli

#document root
WORKDIR /var/www/html/

#copiar todos os arquivos do diretorio para o workdir
#pode fazer assim também : COPY . . 
#o segundo ponto se referencia ao workdir
COPY . /var/www/html/


