# **PyMySQL - Cliente MySQL em Python Puro**
Exemplo didático de cliente MySQL usando Python puro com a biblioteca PyMySQL, com banco MySQL rodando em container Docker.  

## Descrição
Este projeto exemplifica a conexão e manipulação de dados em um banco MySQL com Python puro. São demonstradas operações básicas:

## Criação de tabela

*Inserção de registros (com diferentes formas de placeholders)*

*Consulta (SELECT) com filtro*

*Atualização (UPDATE)*

*Exclusão (DELETE)*

O banco MySQL está configurado para rodar via Docker, facilitando o setup.

## Pré-requisitos
*Docker e Docker Compose instalados*

*Python 3.x instalado*

*Conhecimento básico de terminal/comandos*

## Configuração do Docker MySQL
Na raiz do projeto, há um arquivo **docker-compose.yml** com a configuração do MySQL 8:
```
version: '4.2'
services:
  mysql_206:
    env_file:
      - .env
    container_name: mysql_206
    hostname: mysql_206
    image: mysql:8
    restart: always
    command:
      - --authentication-policy=mysql_native_password
      - --character-set-server=utf8mb4
      - --collation-server=utf8mb4_unicode_ci
      - --innodb_force_recovery=0
    volumes:
      - ./mysql_206:/var/lib/mysql
    ports:
      - 3307:3306
    environment:
      TZ: America/Sao_Paulo
```  
## Como subir o container MySQL
**1. Crie um arquivo .env com suas credenciais MySQL:**
```
MYSQL_ROOT_PASSWORD='senha'
MYSQL_DATABASE='base_de_dados'
MYSQL_USER='usuario'
MYSQL_PASSWORD='senha'
MYSQL_HOST='localhost'
```  
**2. No terminal, dentro da pasta do projeto, execute:**
```
docker-compose up -d
```   
**3. O MySQL ficará acessível na porta 3307 do seu computador.**  

# Configuração do ambiente Python
**1. Crie um ambiente virtual (opcional, mas recomendado):**
```
python -m venv venv
```
#### Linux/macOS
```
source venv/bin/activate   
```
#### Windows
```
venv\Scripts\activate      
```
**2. Instale as dependências:**
```
pip install pymysql python-dotenv
```

# Uso
**1. Verifique se o container MySQL está rodando (docker ps).**

**2. Verifique se o arquivo .env está configurado corretamente.**

**3. Execute o script Python:**
```
python main.py
```
Ele fará todas as operações de criação, inserção, consulta, atualização e exclusão no banco.  

# Funcionamento do script
- Conecta ao MySQL usando credenciais do .env

- Cria a tabela customers (id, nome, idade) se não existir

- Limpa a tabela para começar do zero

- Insere registros usando diferentes tipos de placeholders e formatos de dados:

  - Tupla simples
  - Dicionário
  - Tupla de dicionários
  - Tupla de tuplas

- Consulta registros filtrados pelo campo id

- Apaga um registro específico

- Atualiza um registro e imprime o resultado
