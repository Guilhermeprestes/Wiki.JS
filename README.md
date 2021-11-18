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
mysql> create user wiki@IP_SERVER-WIKI identified by 'wikipw';
mysql> grant all privileges on wiki.* to wiki@IP_SERVER-WIKI;
mysql> quit;
```

## Instalar o Node.JS

```bash MySQL
sudo apt install nodejs
sudo apt install npm
nodejs -v
```
