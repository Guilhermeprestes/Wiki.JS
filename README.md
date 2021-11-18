# Wiki.JS
Implementação do Sistema de documentação Wiki.JS no UBUNTU Server

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
curl -fsSL https://deb.nodesource.com/setup_16.x | sudo -E bash -
sudo apt-get install -y nodejs
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
  
 Execute Wiki.js
 
  ```bash
node server
```
Espere até ser convidado para abrir a página de configuração no seu navegador.
Conclua o assistente de configuração para finalizar a instalação.

## Executar como serviço

Crie um novo arquivo chamado wiki.servicedentro do diretório /etc/systemd/system

  ```bash
vim /etc/systemd/system/wiki.service
```
Cole o seguinte conteúdo (presumindo que seu wiki esteja instalado em /var/wiki):

  ```bash
[Unit]
Description=Wiki.js
After=network.target

[Service]
Type=simple
ExecStart=/usr/bin/node server
Restart=always

User=root
Environment=NODE_ENV=production
WorkingDirectory=/var/wiki

[Install]
WantedBy=multi-user.target
```
Salve o arquivo de serviço 

Recarregue o systemd:

  ```bash
 systemctl daemon-reload
```
Execute o serviço:

  ```bash
systemctl start wiki
```

Habilite o serviço na inicialização do sistema.

  ```bash
 systemctl enable wiki
```









 
