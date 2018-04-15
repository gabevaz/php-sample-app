## Criar DOCKERFILE
Depois de já ter o Docker instalado em sua máquina, é necessario criar na pasta do seu projeto o arquivo Dockerfile, abrir em um editor de texto e passar o seguinte código:

```sh
#para pegar o PHP
FROM php:7.2-apache

#enable mysqli para conectar o banco de dados
RUN docker-php-ext-install mysqli

#document root (raíz do documento)
WORKDIR /var/www/html/

#copiar todos os arquivos do diretorio para o workdir
#pode fazer assim também : COPY . . 
#o segundo ponto se referencia ao workdir
COPY . /var/www/html/

```
## Criar um container
Para executar um container utilize o comando run com o nome da imagem que vá utilizar para a criação:

```sh
docker run nome_da_imagem
```

Porém ele criará o container e este irá morrer, para manter o container conectado basta adicionar 'bash' no final do comando

## Listando containers
Cada vez que você executa o comando run, o Docker vai criar um novo container do zero e armazenar para utilização futura. Você não deve ficar utilizando o comando run toda hora, por isso para listar os containers existentes usa-se 'ps'

```sh
docker ps
```

## Rodar containers Docker já criados

```sh
docker start nome_do_container
```

O comando start só funciona com containers, por isso é obrigatório rodar o comando run pelo menos uma vez.
O container será iniciado e permanecerá rodando em segundo plano até o comando stop ser rodado.

## Acessar containers Docker que já estão rodando
Para acessar containers que já estão rodando usa-se o comando 'attach'
```sh
docker attach nome_do_container
```



