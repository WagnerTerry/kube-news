# Projeto kube-news

### Objetivo
O projeto Kube-news é uma aplicação escrita em NodeJS e tem como objetivo ser uma aplicação de exemplo pra trabalhar com o uso de containers.

### Configuração
Pra configurar a aplicação, é preciso ter um banco de dados Postgre e pra definir o acesso ao banco, configure as variáveis de ambiente abaixo:

DB_DATABASE => Nome do banco de dados que vai ser usado.

DB_USERNAME => Usuário do banco de dados.

DB_PASSWORD => Senha do usuário do banco de dados.

DB_HOST => Endereço do banco de dados.

## Comandos Docker

 - docker container run <nome-container> -> Executar/buscar um container
 - docker container run --name <meucontainer> hello-world -> Executa e nomeia um container
 - docker container ls -> exibe as container ativas
 - docker container ls -a -> exibe todas as container abertas e fechadas
 - docker image ls -> exibe as imagens dos comtaineres instalados
 - docker exec -it <id container> /bin/bash -> Executar modo iterativo, nesse caso do nginx
 - docker container run -d -p 8080:8080 kube-news -> executar docker / -d > daemon , rodar em background e -p > porta
 - docker container logs <id container> -> exibe o log do container, ótimo para debugar.
 - docker logs <id container> -> log do container
 - docker container -rm -f <id container> -> remover um container
 - docker container run -d -p 5432:5432 -e POSTGRES_PASSWORD=root -e POSTGRES_USER=kubenews -e POSTGRES_DB=kubenews postgres -> Cria um container com a imagem do postgres e adiciona as variaveis de ambiente
 - docker image prune -> remover container/lixos
 - docker tag <nome do repositorio> <nome de usuario no docker hub>/tag - tag-versão. Ex: docker tag kube-news fabricioteste/kube-news:v1 -> Renomear uma imagem para subir no docker hub
 - docker login -> Autenticação no docker hub
 - docker push <nome do repositorio>:<tag> -> Sobe para o docker hub o container criado. Ex. docker push fabricioteste/kube-news:v1
 - docker-compose up -d -> Rodar o docker compose
 - docker-compose down -> derruba todos os containeres
 - docker network create kube-news-net -> Fazer a integração com os containeres do projeto
 - docker network ls -> Exibe as conexões network
 - container run -d -p 5432:5432 -e POSTGRES_PASSWORD=root -e POSTGRES_USER=kubenews -e POSTGRES_DB=kubenews --network kube-news-net --name postgres postgres -> exemplo de network
 - docker container run -d -p 8080:8080 -e DB_DATABASE=kubenews -e DB_USERNAME=kubenews -e DB_PASSWORD=root -e DB_HOST=postgres --network kube-news-net wagnerterry/kube-news:v1
 - docker volume create postgres-vol -> Volume gerenciado pelo docker // evita de perder os dados, caso encerre um banco de dados/container
 - docker volume ls
 - docker container run -d -p 5432:5432 -e POSTGRES_PASSWORD=root -e POSTGRES_USER=kubenews -e POSTGRES_DB=kubenews --network kube-news-net --name postgres -v postgres-vol:/var/lib/postgresql/data postgres -> Mapear volume
 - docker inspect kube-news_postgres-vol -> Verificar dados de um volume específico


 ## Dockerfile
 - Cria imagem de um container

 ## Docker Compose
 - É para criar container

 ## Exemplo de criação de uma imagem usando Dockerfile
 FROM ubuntu
 RUN apt update
 RUN apt install curl -y

 comando: docker build -t ubuntu-curl -f Dockerfile
 nome da imagem: ubuntu-curl
