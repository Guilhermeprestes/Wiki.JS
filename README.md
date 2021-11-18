# Wiki.JS
Implementação do Sistema de documentação Wiki.JS

## Requisitos 
1 Servidor para Banco de dados <br>
1 Servidor para Wiki.JS

> Neste caso estamos utilizando um servidor com UBUNTU SERVER

## Banco de Dados MySQL

Dentro da console do MySQL, vamos criar o banco de dados com o nome wiki, um
usuário e uma senha, com permissão para acessar seu próprio banco:

```bash MySQL
mysql> create database wiki character set utf8 collate utf8_bin;
mysql> create user wikijs@IP_SERVER-WIKI identified by 'wikipw';
mysql> grant all privileges on wiki.* to wikijs@IP_SERVER-WIKI;
mysql> quit;
```

## Instalar o Node.JS

```bash MySQL
sudo apt install nodejs
sudo apt install npm
nodejs -v
```
## Instalar a Wiki.JS

Baixe a versão mais recente do Wiki.js:

```bash
  wget https://github.com/Requarks/wiki/releases/download/2.5.219/wiki-js.tar.gz
  ```
  
 Extraia o pacote para o destino final de sua escolha:
 
 ```bash
 mkdir wiki
tar xzf wiki-js.tar.gz -C ./wiki
cd ./wiki
 ```
 Renomeie o arquivo de configuração de amostra para config.yml:
 
  ```bash
  mv config.sample.yml config.yml
 ```
 Edite o arquivo de configuração e preencha seu banco de dados e configurações de porta:
 
  ```bash
vim config.yml 
```
> db: <br>
  type: mysql <br>
  host: localhost <br>
  port: 3306 <br>
  user: wikijs <br>
  pass: wikipw <br>
  db: wiki <br>
  
  


 
