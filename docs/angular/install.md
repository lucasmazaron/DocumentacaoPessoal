# Instalação Angular Cli e dependências

!!! warning "Atenção!"
    NO LINUX, SEMPRE UTILIZAR O *SUDO* OU ENTÃO CORRIGIR AS PERMISSÕES DO NPM

### NodeJS
* Para Instalar o Node no Linux:  
```ts
  sudo apt-get update
  sudo apt-get install nodejs npm
```
* Ou então baixar pelo próprio site do NODE.  
* Para Testar a versão do node:  
 `node -v`  

### Angular Cli
* Para Instalação no Linux:
```ts
    sudo npm install -g @angular/cli
```
* O `-g` indica que o pacote será instalada de forma **Global**. Para poder ser usado em todos os pontos do *SO*, não só em uma pasta  
* O `@angular/cli` é o nome do pacote
* Para testar se foi instalado a versão corretamente:
* `ng -v` Deverá imprimir "ANGULAR CLI" no Terminal com a lista das versões logo a baixo.  

!!! important "Importante"
    Sempre que baixar um novo projeto do git, utilizar npm install para baixar as dependências.
