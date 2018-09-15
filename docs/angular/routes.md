# Rotas

!!! note "Nota"
    Os exemplos utilizados são baseados no meat-app que se encontra no github/cod3rcursos. São anotações do decorrer do curso.

 Para marcar como area dinâmica no template, utilizar `<router-outlet></router-outlet>`.  
 Dessa forma, a aplicação mudará o componente conforme as rotas.  
 Para que isso funcione, devemos mapear cada componente nas rotas.  
 As rotas são basicamente um array que possuem o caminho para cada componente.  
 `Rotas aceitam parâmetros, utilizando a sintax :nomeparam`

**Exemplo:**  

``` typescript
  export const ROUTES: Route = [

    { path: '', component: RestaurantsComponent },
    { path: 'restaurant/:id', component: RestaurantsComponent },
    { path: 'about', component: AboutComponent }
  ]
```
Em seguida, você precisa indicar que rotas serão usadas no módulo através da função `forRoot` no módulo raíz:  

```typescript
  @NgModule({
    declaration: [...],
    imports: [..., RouterModule.forRoot(ROUTES)],
  })

  export class AppModule {
    ...
  }
```  
Ou `forChild` nos outros modulos...  
======= Implementar anotações forChild

Como que eu consigo navegar? Como os caminhos são acionados?  

* O Modulo de routeamento disponibiliza uma diretiva chamada `routerLink=` onde podemos passar um caminho a ser acionado ou, um conjunto de parâmetros.  

```html
  <!-- no template de algum componente -->
  <a routerLink="/restaurants">Restaurantes</a>

  <!-- ou -->
  <a [routerLink]="['/restaurants']">Restaurantes</a>

  <!-- passando parâmetro -->
  <a [routerLink]="['/restaurants', restaurant.id]">Restaurantes</a>
```

## routerLinkActive  

!!! question "Como Controlar o estilo dos links ativos ou não ativos?"
    O modulo de routeamento disponibiliza uma diretiva `routerLinkActive=""`. Essa diretiva serve para mudar o estilo caso a rota abaixo do elemento esteja ativa.  
    Não é obrigatório o uso no elemento que estiver com o routerLink. Você pode utilizar em elementos parents.  

```html
                   <!-- active é a classe do css -->
  <li routerLinkActive="active"><a href="#">Restaurantes</a></li>
```
