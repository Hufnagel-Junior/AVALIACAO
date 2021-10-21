# Configuração do Container Nginx

1. Exposição de porta:

80

2. Volume:

Aplicação: htdocs -> /var/www/html

Logs: nginx/logs -> /var/log/nginx

Virtual Host: nginx/sites -> /etc/nginx/conf.d

3. Virtual Host

Criação do vhost modelo http://api.dev (vhost modificável)

# Postgresql
Nessa etapa sera criado o Postgresql que é usado no Banco de Dados

1. A porta que sera usada:
5432

2. Volume:

Aplicação: postgresql/data -> /var/lib/postgresql/data

3. Configuração para conexão

POSTGRES_DB = default

POSTGRES_USER = default

POSTGRES_PASSWORD = secret

POSTGRES_PORT = 5432

# Passo a Passo

I. Clone o repositório
Para clonar o Repositorio do Git realize o seguinte comando:

git clone https://github.com/Hufnagel-Junior/AVALIACAO.git

II. É necessario acessar a pasta AVALIACAO em seguida copiar o arquivo env-example para .env.

cp env-example .env

III. Inicie seu container:

docker-compose up -d

IV. Adicione os domínios no arquivo de hosts do windows.

127.0.0.1 localhost

127.0.0.1 api.dev

VI. Abra no navegador

http://localhost

http://api.dev

6. Acessar o shell do container:

winpty docker exec -it nginx bash

winpty docker exec -it postgresql bash

VII. Acessar o banco de dados dentro do container Postgresql

psql default default

VIII. Comandos básicos para utilizar o banco de dados

\l;

CREATE DATABASE teste;

\connect teste;

\dt;

CREATE TABLE pessoa (id serial primary key, nome varchar(60) not null);

INSERT INTO pessoa(nome) VALUES ('junior');

INSERT INTO pessoa(nome) VALUES ('vanessa');

INSERT INTO pessoa(nome) VALUES ('amanda');

INSERT INTO pessoa(nome) VALUES ('tulio');
