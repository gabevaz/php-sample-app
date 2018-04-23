
O Banco de dados é um componente Stateful, ou seja possui persistência de dados, estes normalmente são armazenados em:

```sh
/var/lib/mysql
```

Para rodar a imagem o banco de dados pode usar tanto Dockerfile ou Mount points

## Criar DOCKERFILE
Depois de já ter o Docker instalado em sua máquina, é necessario criar na pasta do seu projeto o arquivo Dockerfile, abrir em um editor de texto e passar o seguinte código:

```sh
## para indicar qual imagem estou usando
FROM mysql:latest

## criar o banco na hora que startar o container
COPY ./demo.sql /docker-entrypoint-initdb.d/

```

## Inicializar Banco

Para inicializar o banco usa-se o comando abaixo que irá passar o nome do banco, no caso chamado demo, o my_sql_allow_empty_password que permite o uso de senhas vazias (no caso, yes), --name que indica o nome do container, no caso backend e por ultimoa imagem que irá rodar e sua versão

```sh
docker run -d -e MYSQL_DATABASE='demo' -e MYSQL_ALLOW_EMPTY_PASSWORD='yes' --name backend db:0.0.1
```

## Visualizar o Log do container

Para olhar o log do container que está rodando usa-se:

```sh
docker logs NOME_DO_CONTAINER
```

no caso,

```sh
docker logs backend
```

## Executar comando dentro do container

Para executar um comando dentro de um container que já está rodando, no caso o 'backend' e entrar no banco de dados

```sh
docker exec -ti backend mysql -u root -p
```

## Juntar frontend e backend

Para juntar o frontend e backend usa-se o seguinte comando:

```sh
docker run -d -p 80:80 --name frontend --link backend frontend:0.0.1
```

Acima temos que rodar o front, depois expor o conteúdo na porta 80:80, dar um nome (frontend), linkar ele com o container de backend, falando que eles tem que se comunicar entre si e por ultimo indicar o nome da imagem e sua versão.


