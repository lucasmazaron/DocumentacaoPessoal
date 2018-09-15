# Geral dos comandos do django

## Para iniciar um novo projeto:  

```ts
    django-admin startproject myProject
```
---  
## Criar um app:

```ts
  python manage.py startapp myApp
```

!!! question "Qual é a diferença entre um projeto e um app? - Projetos versus aplicações - Encontrado na documentação do django"
     Um app é uma aplicação que faz alguma coisa, exemplo, um sistema de web blog, um banco de dados de registros públicos, ou uma simples aplicação de enquete. Um projeto é uma coleção de configurações e apps para um particular website. Um projeto pode conter múltiplos apps. Um app pode estar em múltiplos projetos.  

!!! info "Para saber mais... "
    * [Django Project - Criando um aplicativo de votação](https://docs.djangoproject.com/pt-br/2.1/intro/tutorial01/#creating-the-polls-app)
---  
## Iniciando servidor desenvolvimento:

```ts
 python manage.py runserver 0:8000
```
O uso do ip/porta é opcional.  

---
## Criando Banco de dados

!!! info "Acesse o link para toda a documentação "
    * [Django Project - Configuração do Banco de Dados](https://docs.djangoproject.com/pt-br/2.1/intro/tutorial02/#database-setup)

Para verificar se houve mudança de models:
```ts
  python manage.py makemigrations
```

Para criar as tabelas do banco:  
```ts
  python manage.py migrate
```

!!! note "Nota"
    O comando migrate verifica a configuração em INSTALLED_APPS e cria qualquer tabela do banco de dados necessária de acordo com as configurações do banco de dados no seu arquivo mysite/settings.py e as migrações que venham com a app (cobriremos isso mais tarde). É mostrado uma mensagem para cada migração que foi aplicada. Se lhe interessar, execute cliente de linha de comando para seu banco de dados e dgite \dt (PostgreSQL), SHOW TABLES; (MySQL), .schema (SQLite), ou SELECT TABLE_NAME FROM USER_TABLES; (Oracle) para mostrar as tabelas mostradas pelo Django.


---
## Criar Super User

```ts
  python manage.py createsuperuser
```
