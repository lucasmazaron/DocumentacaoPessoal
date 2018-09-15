# Geral dos Arquivos Angular CLI  
## Packages.json

!!! note "Nota"
    Arquivo de configuração da aplicação. Contém todas as dependências

## WebPack

!!! note "Nota"
    Biblioteca em java script responsável por criar os bundles da aplicação.

    * polyfills - Série de scripts que você adiciona para aumentar compatibilidade com browsers antigos;  
    * main - Scripts da aplicação;  
    * styles - Stilos dentro da aplicação;  
    * vendor - Scripts de terceiros;  
    * inline - carregar webpack.  

## `src\polyfills.ts`

!!! note "Nota"
    Incluir scripts para dar suporte a novas funcionalidades a browsers antigos  

## app.module.ts

```typescript
  @NgModule({
    declarations: [MyFirstComponent], //Todos os componentes da aplicação
    imports: [],      // Imports de dependências
    providers: [],
    bootstrap: []})   // Qual é o componente responsável por fazer o bootstrap da aplicação
```
!!! note "Nota"
    **@NgModule** -> Decorator.  
    Utilizado para aplicar metadados em uma classe/atributo/metodo/argumento de um metodo`  
